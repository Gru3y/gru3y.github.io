---
title: "[THM] PS Eclipse"
date: 2024-07-26
categories: [Writeups, TryHackMe]
tags: [THM, Writeup, Splunk, SIEM]
---
Scenario: You are a SOC Analyst for an MSSP (Managed Security Service Provider) company called TryNotHackMe.

A customer sent an email asking for an analyst to investigate the events that occurred on Keegan's machine on Monday, May 16th, 2022. The client noted that the machine is operational, but some files have a weird file extension. The client is worried that there was a ransomware attempt on Keegan's device. 

Your manager has tasked you to check the events in Splunk to determine what occurred in Keegan's device. 

***

# Questions
**Q:** A suspicious binary was downloaded to the endpoint. What was the name of the binary? <br />
**A:** OUTSTANDING_GUTTER.exe
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q1-1.png" alt="PS Eclipse">

***

**Q:** What is the address the binary was downloaded from? Add http:// to your answer & defang the URL. <br />
**A:** hxxp[://]886e-181-215-214-32[.]ngrok[.]io
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q2-1.png" alt="PS Eclipse">
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q2-2.png" alt="PS Eclipse">
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q2-3.png" alt="PS Eclipse">

***

**Q:** What Windows executable was used to download the suspicious binary? Enter full path. <br />
**A:** C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q3-1.png" alt="PS Eclipse">

***

**Q:** What command was executed to configure the suspicious binary to run with elevated privileges? <br />
**A:** "C:\Windows\system32\schtasks.exe" /Create /TN OUTSTANDING_GUTTER.exe /TR C:\Windows\Temp\COUTSTANDING_GUTTER.exe /SC ONEVENT /EC Application /MO *[System/EventID=777] /RU SYSTEM /f
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q4-1.png" alt="PS Eclipse">

***

**Q:** What permissions will the suspicious binary run as? What was the command to run the binary with elevated privileges? (Format: User + ; + CommandLine) <br />
**A:** NT AUTHORITY\SYSTEM;"C:\Windows\system32\schtasks.exe" /Run /TN OUTSTANDING_GUTTER.exe
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q5-1.png" alt="PS Eclipse">

***

**Q:** The suspicious binary connected to a remote server. What address did it connect to? Add http:// to your answer & defang the URL. <br />
**A:** hxxp[://]9030-181-215-214-32[.]ngrok[.]io <br />
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q6-1.png" alt="PS Eclipse">

***

**Q:** A PowerShell script was downloaded to the same location as the suspicious binary. What was the name of the file? <br />
**A:** script.ps1 <br />
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q7-1.png" alt="PS Eclipse">

***

**Q:** The malicious script was flagged as malicious. What do you think was the actual name of the malicious script? <br />
**A:** BlackSun.ps1
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q8-1.png" alt="PS Eclipse">

***

**Q:** A ransomware note was saved to disk, which can serve as an IOC. What is the full path to which the ransom note was saved? <br />
**A:** C:\Users\keegan\Downloads\vasg6b0wmw029hd\BlackSun_README.txt
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q9-1.png" alt="PS Eclipse">

***

**Q:** The script saved an image file to disk to replace the user's desktop wallpaper, which can also serve as an IOC. What is the full path of the image? <br />
**A:** C:\Users\Public\Pictures\blacksun.jpg
<img src="/assets/img/PS-Eclipse/PS-Eclipse-q10-1.png" alt="PS Eclipse">

***