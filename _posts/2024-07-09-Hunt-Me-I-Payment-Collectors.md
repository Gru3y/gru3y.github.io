---
title: "[THM] Hunt Me I: Payment Collectors"
date: 2024-07-09
categories: [Writeups, TryHackMe]
tags: [THM, Writeup]
---
On Friday, September 15, 2023, Michael Ascot, a Senior Finance Director from SwiftSpend, was checking his emails in Outlook and came across an email appearing to be from Abotech Waste Management regarding a monthly invoice for their services. Michael actioned this email and downloaded the attachment to his workstation without thinking.

<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-attachment.png" alt="THM-Hunt-Me-I-Payment-Collectors-attachment" style="width:500px;height:500;">

The following week, Michael received another email from his contact at Abotech claiming they were recently hacked and to carefully review any attachments sent by their employees. However, the damage has already been done. Use the attached Elastic instance to hunt for malicious activity on Michael's workstation and within the SwiftSpend domain!

# Questions

**Q:** What was the name of the ZIP attachment that Michael downloaded?<br />
**A:** Invoice_AT_2023-227.zip
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q1.png" alt="THM-Hunt-Me-I-Payment-Collectors-q1">

***

**Q:** What was the contained file that Michael extracted from the attachment?<br />
**A:** Payment_Invoice.pdf.lnk.lnk
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q2.png" alt="THM-Hunt-Me-I-Payment-Collectors-q2">

***

**Q:** What was the name of the command-line process that spawned from the extracted file attachment?<br />
**A:** powershell.exe
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q3-1.png" alt="THM-Hunt-Me-I-Payment-Collectors-q3-1">
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q3-2.png" alt="THM-Hunt-Me-I-Payment-Collectors-q3-2">

***

**Q:** What URL did the attacker use to download a tool to establish a reverse shell connection?<br />
**A:** https://raw.githubusercontent.com/besimorhino/powercat/master/powercat.ps1
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q4.png" alt="THM-Hunt-Me-I-Payment-Collectors-q4">

***

**Q:** What port did the workstation connect to the attacker on?<br />
**A:** 19282
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q5.png" alt="THM-Hunt-Me-I-Payment-Collectors-q5">

***

**Q:** What was the first native Windows binary the attacker ran for system enumeration after obtaining remote access?<br />
**A:** systeminfo.exe
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q6.png" alt="THM-Hunt-Me-I-Payment-Collectors-q6">

***

**Q:** What is the URL of the script that the attacker downloads to enumerate the domain?<br />
**A:** https://raw.githubusercontent.com/PowerShellEmpire/PowerTools/master/PowerView/powerview.ps1
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q7-1.png" alt="THM-Hunt-Me-I-Payment-Collectors-q7-1">
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q7-2.png" alt="THM-Hunt-Me-I-Payment-Collectors-q7-2">

***

**Q:** What was the name of the file share that the attacker mapped to Michael's workstation?<br />
**A:** SSF-FinancialRecords
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q8.png" alt="THM-Hunt-Me-I-Payment-Collectors-q8">

***

**Q:** What directory did the attacker copy the contents of the file share to?<br />
**A:** C:\Users\michael.ascot\downloads\exfiltration

***

**Q:** What was the name of the Excel file the attacker extracted from the file share?<br />
**A:** ClientPortfolioSummary.xlsx
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q10.png" alt="THM-Hunt-Me-I-Payment-Collectors-q10">

***

**Q:** What was the name of the archive file that the attacker created to prepare for exfiltration?<br />
**A:** exfilt8me.zip
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q11.png" alt="THM-Hunt-Me-I-Payment-Collectors-q11">

***

**Q:** What is the MITRE ID of the technique that the attacker used to exfiltrate the data?<br />
**A:** T1048
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q12-1.png" alt="THM-Hunt-Me-I-Payment-Collectors-q12-1">
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q12-2.png" alt="THM-Hunt-Me-I-Payment-Collectors-q12-2">

***

**Q:** What was the domain of the attacker's server that retrieved the exfiltrated data?<br />
**A:** haz4rdw4re.io

***

**Q:** The attacker exfiltrated an additional file from the victim's workstation. What is the flag you receive after reconstructing the file?<br />
**A:** THM{1497321f4f6f059a52dfb124fb16566e}
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q14-1.png" alt="THM-Hunt-Me-I-Payment-Collectors-q14-1">
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q14-2.png" alt="THM-Hunt-Me-I-Payment-Collectors-q14-2">
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q14-3.png" alt="THM-Hunt-Me-I-Payment-Collectors-q14-3">
<img src="/assets/img/THM-Hunt-Me-I-Payment-Collectors-q14-4.png" alt="THM-Hunt-Me-I-Payment-Collectors-q14-4">