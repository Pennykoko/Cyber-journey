Day 2 - Network Discovery & Nmap Scans

Date: Sept 29, 2026
Network: NATNetwork - 10.0.2.0/24
Target: Metasploitable 2 - 10.0.2.6


1. Find Live Hosts
I needed to find all active IPs on my lab network.
Command:
`bash
nmap -sn 10.0.2.0/24
*Result I got:*
- 10.0.2.1 (gateway)
- 10.0.2.2 (host)
- 10.0.2.6 (Metasploitable2)
- 10.0.2.5 (OWASP BWA) 
- 10.0.2.15 (my Kali)

  2. Service & Port Scan on Metasploitable
Then I scanned for open ports and services.
Command:
nmap -sV -sC -O 10.0.2.4
*Key ports found:*
- 21/tcp - FTP - vsftpd 2.3.4 (vulnerable)
- 22/tcp - SSH - OpenSSH 4.7
- 23/tcp - Telnet
- 80/tcp - HTTP - Apache
- 139, 445/tcp - SMB - Samba
- 3306/tcp - MySQL
- 5432/tcp - PostgreSQL
- 5900/tcp - VNC
Lesson: Metasploitable is purposely open — it's a playground, not a real network.

3. Vuln Scan
Tried to check for known vulnerabilities.

*Command:*
nmap --script vuln 10.0.2.4
Found:
- FTP allows anonymous login
- SMB vulnerable to MS08-067 (old Windows exploit)
- Apache shows many possible web vulns

What I Learned Today
- `-sn` = ping sweep, just to find live hosts, no port scan
- `-sV` = version detection, `-sC` = default scripts, `-O` = OS detection
- Always scan your own NAT range first so you don't accidentally scan real internet

  Next
Try to exploit one of these: vsftpd 2.3.4 backdoor on port 21
