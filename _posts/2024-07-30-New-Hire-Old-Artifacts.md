---
title: "[THM] New Hire Old Artifacts"
date: 2024-07-29
categories: [Writeups, TryHackMe]
tags: [THM, Writeup, Splunk, SIEM]
---
Scenario: You are a SOC Analyst for an MSSP (managed Security Service Provider) company called TryNotHackMe.

A newly acquired customer (Widget LLC) was recently onboarded with the managed Splunk service. The sensor is live, and all the endpoint events are now visible on TryNotHackMe's end. Widget LLC has some concerns with the endpoints in the Finance Dept, especially an endpoint for a recently hired Financial Analyst. The concern is that there was a period (December 2021) when the endpoint security product was turned off, but an official investigation was never conducted. 

Your manager has tasked you to sift through the events of Widget LLC's Splunk instance to see if there is anything that the customer needs to be alerted on. 

***

# Questions
**Q:** A Web Browser Password Viewer executed on the infected machine. What is the name of the binary? Enter the full path. <br />
**A:** C:\Users\FINANC~1\AppData\Local\Temp\11111.exe
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q1-1.png" alt="New Hire Old Artifacts">
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q1-2.png" alt="New Hire Old Artifacts">

***

**Q:** What is listed as the company name? <br />
**A:** NirSoft <br />
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q2-1.png" alt="New Hire Old Artifacts">

***

**Q:** Another suspicious binary running from the same folder was executed on the workstation. What was the name of the binary? What is listed as its original filename? (format: file.xyz,file.xyz) <br />
**A:** IonicLarge.exe,PalitExplorer.exe
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q3-1.png" alt="New Hire Old Artifacts">
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q3-2.png" alt="New Hire Old Artifacts">

***

**Q:** The binary from the previous question made two outbound connections to a malicious IP address. What was the IP address? Enter the answer in a defang format. <br />
**A:** 2[.]56[.]59[.]42
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q4-1.png" alt="New Hire Old Artifacts">

***

**Q:** The same binary made some change to a registry key. What was the key path? <br />
**A:** HKLM\SOFTWARE\Policies\Microsoft\Windows Defender
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q5-1.png" alt="New Hire Old Artifacts">

***

**Q:** Some processes were killed and the associated binaries were deleted. What were the names of the two binaries? (format: file.xyz,file.xyz) <br />
**A:** WvmIOrcfsuILdX6SNwIRmGOJ.exe,phcIAmLJMAIMSa9j9MpgJo1m.exe
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q6-1.png" alt="New Hire Old Artifacts">

***

**Q:** The attacker ran several commands within a PowerShell session to change the behaviour of Windows Defender. What was the last command executed in the series of similar commands? <br />
**A:** powershell WMIC /NAMESPACE:\\root\Microsoft\Windows\Defender PATH MSFT_MpPreference call Add ThreatIDDefaultAction_Ids=2147737394 ThreatIDDefaultAction_Actions=6 Force=True
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q7-1.png" alt="New Hire Old Artifacts">

***

**Q:** Based on the previous answer, what were the four IDs set by the attacker? Enter the answer in order of execution. (format: 1st,2nd,3rd,4th) <br />
**A:** 2147735503,2147737010,2147737007,2147737394
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q8-1.png" alt="New Hire Old Artifacts">

***

**Q:** Another malicious binary was executed on the infected workstation from another AppData location. What was the full path to the binary? <br />
**A:** C:\Users\Finance01\AppData\Roaming\EasyCalc\EasyCalc.exe
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q9-1.png" alt="New Hire Old Artifacts">

***

**Q:** What were the DLLs that were loaded from the binary from the previous question? Enter the answers in alphabetical order. (format: file1.dll,file2.dll,file3.dll) <br />
**A:** ffmpeg.dll,nw.dll,nw_elf.dll <br />
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q10-1.png" alt="New Hire Old Artifacts"> <br />
<img src="/assets/img/New-hire-old-artifacts/new-hire-old-artifacts-q10-2.png" alt="New Hire Old Artifacts">

***