Date: Sept 30, 2026
VM: OWASP Broken Web Apps - 10.0.2.4
My Host: Kali Linux

 The Problem
I was trying to open 10.0.2.4 in Firefox but I kept getting:
The proxy server is refusing connections,
I had set manual proxy to 127.0.0.1:8080 for BurpSuite.

What I Learned
When Firefox is set to manual proxy, it tries to send EVERY site through Burp, including my local lab VMs. If Burp is not running, it fails.

The Solution
1. Firefox > Settings > Network Settings > Manual Proxy
2. Look for the box: "No proxy for"
3. I added: localhost, 127.0.0.1, 10.0.2.4
4. Saved and refreshed. The OWASP page loaded instantly.


Key Takeaway
Always add your lab IPs to "No proxy for" when using BurpSuite, or switch proxy off when not intercepting.


Next Step
Start first OWASP BWA challenges and try basic SQL Injection payload ' OR '1'='1
