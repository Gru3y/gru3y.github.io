---
title: "[CD] Web Investigation"
date: 2024-08-10
categories: [Writeups, CyberDefenders]
tags: [CyberDefenders, Writeup, Wireshark, PCAP]
---

Scenario:

You are a cybersecurity analyst working in the Security Operations Center (SOC) of BookWorld, an expansive online bookstore renowned for its vast selection of literature. BookWorld prides itself on providing a seamless and secure shopping experience for book enthusiasts around the globe. Recently, you've been tasked with reinforcing the company's cybersecurity posture, monitoring network traffic, and ensuring that the digital environment remains safe from threats.

Late one evening, an automated alert is triggered by an unusual spike in database queries and server resource usage, indicating potential malicious activity. This anomaly raises concerns about the integrity of BookWorld's customer data and internal systems, prompting an immediate and thorough investigation.

As the lead analyst on this case, you are required to analyze the network traffic to uncover the nature of the suspicious activity. Your objectives include identifying the attack vector, assessing the scope of any potential data breach, and determining if the attacker gained further access to BookWorld's internal systems.

# Questions

**Q:** By knowing the attacker's IP, we can analyze all logs and actions related to that IP and determine the extent of the attack, the duration of the attack, and the techniques used. Can you provide the attacker's IP? <br />
**A:** 111.224.250.131 <br />
<img src="/assets/img/Web-Investigation/Web-Investigation-q1-1.png" alt="Web Investigation">

***

**Q:** If the geographical origin of an IP address is known to be from a region that has no business or expected traffic with our network, this can be an indicator of a targeted attack. Can you determine the origin city of the attacker? <br />
**A:** Shijiazhuang <br />
<img src="/assets/img/Web-Investigation/Web-Investigation-q2-1.png" alt="Web Investigation">

***

**Q:** Identifying the exploited script allows security teams to understand exactly which vulnerability was used in the attack. This knowledge is critical for finding the appropriate patch or workaround to close the security gap and prevent future exploitation. Can you provide the vulnerable script name? <br />
**A:** search.php <br />
<img src="/assets/img/Web-Investigation/Web-Investigation-q3-1.png" alt="Web Investigation">

***

**Q:** Establishing the timeline of an attack, starting from the initial exploitation attempt, What's the complete request URI of the first SQLi attempt by the attacker? <br />
**A:** /search.php?search=book%20and%201=1;%20--%20- <br />
<img src="/assets/img/Web-Investigation/Web-Investigation-q4-1.png" alt="Web Investigation">

***

**Q:** Can you provide the complete request URI that was used to read the web server available databases? <br />
**A:** /search.php?search=book%27%20UNION%20ALL%20SELECT%20NULL%2CCONCAT%280x7178766271%2CJSON_ARRAYAGG%28CONCAT_WS%280x7a76676a636b%2Cschema_name%29%29%2C0x7176706a71%29%20FROM%20INFORMATION_SCHEMA.SCHEMATA--%20- <br />
<img src="/assets/img/Web-Investigation/Web-Investigation-q5-1.png" alt="Web Investigation">

***

**Q:** Assessing the impact of the breach and data access is crucial, including the potential harm to the organization's reputation. What's the table name containing the website users data? <br />
**A:** customers <br />
<img src="/assets/img/Web-Investigation/Web-Investigation-q6-1.png" alt="Web Investigation">

***

**Q:** The website directories hidden from the public could serve as an unauthorized access point or contain sensitive functionalities not intended for public access. Can you provide name of the directory discovered by the attacker? <br />
**A:** /admin/ <br />
<img src="/assets/img/Web-Investigation/Web-Investigation-q7-1.png" alt="Web Investigation">

***

**Q:** Knowing which credentials were used allows us to determine the extent of account compromise. What's the credentials used by the attacker for logging in? <br />
**A:** admin:admin123! <br />
<img src="/assets/img/Web-Investigation/Web-Investigation-q8-1.png" alt="Web Investigation">
<img src="/assets/img/Web-Investigation/Web-Investigation-q8-2.png" alt="Web Investigation">

***

**Q:** We need to determine if the attacker gained further access or control on our web server. What's the name of the malicious script uploaded by the attacker? <br />
**A:** NVri2vhp.php <br />
<img src="/assets/img/Web-Investigation/Web-Investigation-q9-1.png" alt="Web Investigation">

***