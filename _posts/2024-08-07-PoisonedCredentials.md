---
title: "[CD] PoisonedCredentials"
date: 2024-08-07
categories: [Writeups, CyberDefenders]
tags: [CyberDefenders, Writeup, Wireshark, PCAP]
---

Scenario:

Your organization's security team has detected a surge in suspicious network activity. There are concerns that LLMNR (Link-Local Multicast Name Resolution) and NBT-NS (NetBIOS Name Service) poisoning attacks may be occurring within your network. These attacks are known for exploiting these protocols to intercept network traffic and potentially compromise user credentials. Your task is to investigate the network logs and examine captured network traffic.

# Questions

**Q:** In the context of the incident described in the scenario, the attacker initiated their actions by taking advantage of benign network traffic from legitimate machines. Can you identify the specific mistyped query made by the machine with the IP address 192.168.232.162? <br />
**A:** fileshaare
<img src="/assets/img/PoisonedCredentials/PoisonedCredentials-q1-1.png" alt="PoisonedCredentials">

***

**Q:** We are investigating a network security incident. For a thorough investigation, we need to determine the IP address of the rogue machine. What is the IP address of the machine acting as the rogue entity? <br />
**A:** 192.168.232.215
<img src="/assets/img/PoisonedCredentials/PoisonedCredentials-q2-1.png" alt="PoisonedCredentials">

***

**Q:** During our investigation, it's crucial to identify all affected machines. What is the IP address of the second machine that received poisoned responses from the rogue machine? <br />
**A:** 192.168.232.176
<img src="/assets/img/PoisonedCredentials/PoisonedCredentials-q3-1.png" alt="PoisonedCredentials">

***

**Q:** We suspect that user accounts may have been compromised. To assess this, we must determine the username associated with the compromised account. What is the username of the account that the attacker compromised? <br />
**A:** janesmith
<img src="/assets/img/PoisonedCredentials/PoisonedCredentials-q4-1.png" alt="PoisonedCredentials">
<img src="/assets/img/PoisonedCredentials/PoisonedCredentials-q4-2.png" alt="PoisonedCredentials">

***

**Q:** As part of our investigation, we aim to understand the extent of the attacker's activities. What is the hostname of the machine that the attacker accessed via SMB? <br />
**A:** ACCOUNTINGPC
<img src="/assets/img/PoisonedCredentials/PoisonedCredentials-q5-1.png" alt="PoisonedCredentials">

***