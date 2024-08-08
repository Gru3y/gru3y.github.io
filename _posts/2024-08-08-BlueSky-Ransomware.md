---
title: "[CD] BlueSky Ransomware"
date: 2024-08-08
categories: [Writeups, CyberDefenders]
tags: [CyberDefenders, Writeup, Wireshark, Network Miner, PCAP, Splunk]
---

# Scenario
As a cybersecurity analyst on SecureTech's Incident Response Team, you're tackling an urgent case involving a high-profile corporation that suspects a sophisticated cyber attack on its network. The corporation, which manages critical data across various industries, has experienced a ransomware attack, leading to the encryption of files and an immediate need for expert assistance to mitigate the damages and investigate the breach.

Your role in the team is to conduct a detailed analysis of the evidence to determine the extent and nature of the attack. Your objective is to identify the tactics, techniques, and procedures (TTPs) used by the threat actor to help your client contain the threat and restore the integrity of their network.

***

# Questions

**Q:** Knowing the source IP of the attack allows security teams to respond to potential threats quickly. Can you identify the source IP responsible for potential port scanning activity? <br />
**A:** 87.96.21.84 <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q1-1.png" alt="BlueSky Ransomware">

***

**Q:** During the investigation, it's essential to determine the account targeted by the attacker. Can you identify the targeted account username? <br />
**A:** sa <br />

***

**Q:** We need to determine if the attacker succeeded in gaining access. Can you provide the correct password discovered by the attacker? <br />
**A:** cyb3rd3f3nd3r$ <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q3-1.png" alt="BlueSky Ransomware">
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q3-2.png" alt="BlueSky Ransomware">

***

**Q:** Attackers often change some settings to facilitate lateral movement within a network. What setting did the attacker enable to control the target host further and execute further commands? <br />
**A:** xp_cmdshell <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q4-1.png" alt="BlueSky Ransomware">

***

**Q:** Process injection is often used by attackers to escalate privileges within a system. What process did the attacker inject the C2 into to gain administrative privileges? <br />
**A:** winlogon.exe <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q5-1.png" alt="BlueSky Ransomware">
<p>An analysis of the evtx file indicates a lot of logs related to the use of powershell (EventCodes in the top are 600 and 400), and from this we will start looking for the infected process. We will start looking by Event ID 400, which indicates to us that powershell has started running. The first log with ID: 400 indicates that winlogon.exe started powershell controlled by Metasploit.</p>
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q5-2.png" alt="BlueSky Ransomware">
 
***

**Q:** Following privilege escalation, the attacker attempted to download a file. Can you identify the URL of this file downloaded? <br />
**A:** http://87.96.21.84/checking.ps1 <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q6-1.png" alt="BlueSky Ransomware">

***

**Q:** Understanding which group Security Identifier (SID) the malicious script checks to verify the current user's privileges can provide insights into the attacker's intentions. Can you provide the specific Group SID that is being checked? <br />
**A:** S-1-5-32-544 <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q7-1.png" alt="BlueSky Ransomware">

***

**Q:** Windows Defender plays a critical role in defending against cyber threats. If an attacker disables it, the system becomes more vulnerable to further attacks. What are the registry keys used by the attacker to disable Windows Defender functionalities? Provide them in the same order found. <br />
**A:** DisableAntiSpyware,DisableRoutinelyTakingAction,DisableRealtimeMonitoring,SubmitSamplesConsent,SpynetReporting <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q8-1.png" alt="BlueSky Ransomware">

***

**Q:** Can you determine the URL of the second file downloaded by the attacker? <br />
**A:** http://87.96.21.84/del.ps1 <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q9-1.png" alt="BlueSky Ransomware">

***

**Q:** Identifying malicious tasks and understanding how they were used for persistence helps in fortifying defenses against future attacks. What's the full name of the task created by the attacker to maintain persistence? <br />
**A:** \Microsoft\Windows\MUI\LPupdate <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q10-1.png" alt="BlueSky Ransomware">

***

**Q:** According to your analysis of the second malicious file, what is the MITRE ID of the tactic the file aims to achieve? <br />
**A:** TA0005 <br />

***

**Q:** What's the invoked PowerShell script used by the attacker for dumping credentials? <br />
**A:** Invoke-PowerDump.ps1 <br />

***

**Q:** Understanding which credentials have been compromised is essential for assessing the extent of the data breach. What's the name of the saved text file containing the dumped credentials?  <br />
**A:** hashes.txt <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q13-1.png" alt="BlueSky Ransomware">

***

**Q:** Knowing the hosts targeted during the attacker's reconnaissance phase, the security team can prioritize their remediation efforts on these specific hosts. What's the name of the text file containing the discovered hosts? <br />
**A:** extracted_hosts.txt <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q14-1.png" alt="BlueSky Ransomware">

***

**Q:** After hash dumping, the attacker attempted to deploy ransomware on the compromised host, spreading it to the rest of the network through previous lateral movement activities using SMB. You’re provided with the ransomware sample for further analysis. By performing behavioral analysis, what’s the name of the ransom note file? <br />
**A:** # DECRYPT FILES BLUESKY # <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q15-1.png" alt="BlueSky Ransomware">
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q15-2.png" alt="BlueSky Ransomware">
<https://app.any.run/tasks/205e5c98-78ee-41aa-b850-b86388efae29/>



***

**Q:** In some cases, decryption tools are available for specific ransomware families. Identifying the family name can lead to a potential decryption solution. What's the name of this ransomware family? <br />
**A:** Conti <br />
<img src="/assets/img/BlueSky-Ransomware/BlueSky-Ransomware-q16-1.png" alt="BlueSky Ransomware">

***