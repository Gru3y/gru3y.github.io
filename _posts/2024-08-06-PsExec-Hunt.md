---
title: "[CD] PsExec Hunt"
date: 2024-08-06
categories: [Writeups, CyberDefenders]
tags: [CyberDefenders, Writeup, Wireshark, PCAP]
---

Scenario:

Our Intrusion Detection System (IDS) has raised an alert, indicating suspicious lateral movement activity involving the use of PsExec. To effectively respond to this incident, your role as a SOC Analyst is to analyze the captured network traffic stored in a PCAP file.

# Questions

**Q:** In order to effectively trace the attacker's activities within our network, can you determine the IP address of the machine where the attacker initially gained access? <br />
**A:** 10.0.0.130 <br />
<img src="/assets/img/PsExec-Hunt/PsExec-Hunt-q1-1.png" alt="PsExec Hunt">

***

**Q:** To fully comprehend the extent of the breach, can you determine the machine's hostname to which the attacker first pivoted? <br />
**A:** sales-pc <br />
<img src="/assets/img/PsExec-Hunt/PsExec-Hunt-q2-1.png" alt="PsExec Hunt">

***

**Q:** After identifying the initial entry point, it's crucial to understand how far the attacker has moved laterally within our network. Knowing the username of the account the attacker used for authentication will give us insights into the extent of the breach. What is the username utilized by the attacker for authentication? <br />
**A:** ssales <br />
<img src="/assets/img/PsExec-Hunt/PsExec-Hunt-q3-1.png" alt="PsExec Hunt">

***

**Q:** After figuring out how the attacker moved within our network, we need to know what they did on the target machine. What's the name of the service executable the attacker set up on the target? <br />
**A:** PSEXESVC.EXE <br />
<img src="/assets/img/PsExec-Hunt/PsExec-Hunt-q4-1.png" alt="PsExec Hunt">

***

**Q:** We need to know how the attacker installed the service on the compromised machine to understand the attacker's lateral movement tactics. This can help identify other affected systems. Which network share was used by PsExec to install the service on the target machine? <br />
**A:** ADMIN$ <br />
<img src="/assets/img/PsExec-Hunt/PsExec-Hunt-q5-1.png" alt="PsExec Hunt">

***

**Q:** We must identify the network share used to communicate between the two machines. Which network share did PsExec use for communication? <br />
**A:** IPC$ <br />
<img src="/assets/img/PsExec-Hunt/PsExec-Hunt-q6-1.png" alt="PsExec Hunt">

***

**Q:** Now that we have a clearer picture of the attacker's activities on the compromised machine, it's important to identify any further lateral movement. What is the machine's hostname to which the attacker attempted to pivot within our network? <br />
**A:** MARKETING-PC <br />
<img src="/assets/img/PsExec-Hunt/PsExec-Hunt-q7-1.png" alt="PsExec Hunt">

***