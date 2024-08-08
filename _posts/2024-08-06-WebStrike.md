---
title: "[CD] WebStrike"
date: 2024-08-06
categories: [Writeups, CyberDefenders]
tags: [CyberDefenders, Writeup, Wireshark, PCAP]
---

# Scenario

An anomaly was discovered within our company's intranet as our Development team found an unusual file on one of our web servers. Suspecting potential malicious activity, the network team has prepared a pcap file with critical network traffic for analysis for the security team, and you have been tasked with analyzing the pcap.

***

# Questions

**Q:** Understanding the geographical origin of the attack aids in geo-blocking measures and threat intelligence analysis. What city did the attack originate from? <br />
**A:** Tianjin <br />
<img src="/assets/img/WebStrike/WebStrike-q1-1.png" alt="WebStrike">

***

**Q:** Knowing the attacker's user-agent assists in creating robust filtering rules. What's the attacker's user agent? <br />
**A:** Mozilla/5.0 (X11; Linux x86_64; rv:109.0) Gecko/20100101 Firefox/115.0 <br />
<img src="/assets/img/WebStrike/WebStrike-q2-1.png" alt="WebStrike">

***

**Q:** We need to identify if there were potential vulnerabilities exploited. What's the name of the malicious web shell uploaded? <br />
**A:** image.jpg.php <br />
<img src="/assets/img/WebStrike/WebStrike-q3-1.png" alt="WebStrike">

***

**Q:** Knowing the directory where files uploaded are stored is important for reinforcing defenses against unauthorized access. Which directory is used by the website to store the uploaded files? <br />
**A:** /reviews/uploads/ <br />
<img src="/assets/img/WebStrike/WebStrike-q4-1.png" alt="WebStrike">

***

**Q:** Identifying the port utilized by the web shell helps improve firewall configurations for blocking unauthorized outbound traffic. What port was used by the malicious web shell?  <br />
**A:** 8080 <br />
<img src="/assets/img/WebStrike/WebStrike-q5-1.png" alt="WebStrike">

***

**Q:** Understanding the value of compromised data assists in prioritizing incident response actions. What file was the attacker trying to exfiltrate? <br />
**A:** passwd <br />
<img src="/assets/img/WebStrike/WebStrike-q6-1.png" alt="WebStrike">

***