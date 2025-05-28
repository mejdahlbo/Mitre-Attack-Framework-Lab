# Mitre Att&ck Framework Lab

## Forewords and Feedback
This is a write-up of my **MITRE ATT&CK Framework Lab**

Feel free to drop any feedback or point out anything I might’ve missed! I’m all about learning from others and my own mistakes. I really appreciate you taking the time to check out my project!

## What is the MITRE ATT&CK Framework?
Imagine we have a big **playbook** that lists all the tricks and tactics that hackers use to break into computer systems and do bad stuff. That’s the **MITRE ATT&CK Framework**.

-   **MITRE** = a nonprofit organisation that helps governments and companies with security
-   **ATT&CK** = **Adversarial Tactics, Techniques, and Common Knowledge**

Link to the MITRE ATT&CK <a href="https://attack.mitre.org">Page</a>

![Mitre Attack](https://github.com/user-attachments/assets/b6a4a56c-a005-475a-acf7-b2baa12ea023)

## How It Works — Think Like a Burglar
Let’s say a burglar wants to break into a house:

-   **Tactics** = **Why** they do something (like “break in,” “hide,” “steal”)
-   **Techniques** = **How** they do it (like “pick a lock,” “use a disguise,” “climb through a window”)
-   **Sub-techniques** = **More detail** (like picking a deadbolt specifically)
-   **Procedures** = **Real-world examples** of these tricks being used

**MITRE ATT&CK** takes this same idea and applies it to **cyber attacks** on computers and networks.


## Why Is It Useful?
For us cyber defenders like **SOC analysts** or **Blue Teams**, the **MITRE ATT&CK Framework** helps with:

-   **Understanding how hackers operate**
-   **Spotting early signs of an attack**
-   **Creating better defences**
-   **Building detection rules (like in Splunk, SIEMs, etc.)**

## Real-World Scenario
A client experienced a ransomware attack a couple months ago and the incident response (IR) team had identified the initial entry point. It was determined that a malicious PDF document had been delivered via phishing and executed on January 1st, 2023. The threat actor leveraged "living off the land" binaries to install additional malware, created scheduled tasks for persistence, and searched for additional hosts via nslookup. They also created a new domain account with domain administrative privileges, which was used to disable antivirus and was observed connecting to other machines via Remote Desktop Protocol (RDP), eventually compromising the domain controller. Furthermore, the new domain account created a file named "1.7z," and there is evidence of large outbound traffic towards [transfer.sh](http://transfer.sh/) indicating likely successful exfiltration. Subsequently, a ransomware binary was deployed rendering critical hosts inaccessible.

## Task
Our task is now to use the MITRE ATT&CK framework to mark our findings and which techniques were used.

## Our Findings Marked in BOLD
A client experienced a **ransomware** attack a couple months ago and the incident response (IR) team had identified the initial entry point. It was determined that a **malicious PDF document** had been delivered via **phishing** and executed on January 1st, 2023. The threat actor leveraged "**living off the land**" binaries to install additional malware, created **scheduled tasks** for persistence, and **searched for additional hosts via nslookup**. They also **created a new domain account with domain administrative privileges**, which was used to **disable antivirus** and was observed **connecting to other machines via Remote Desktop Protocol (RDP)**, eventually compromising the domain controller. Furthermore, the **new domain account created a file named "1.7z"** and there is evidence of **large outbound traffic towards [transfer.sh](http://transfer.sh/)** indicating likely successful exfiltration. Subsequently, a ransomware binary was deployed **rendering critical hosts inaccessible**.

## Techniques Used
|Tactic|Technique|Example|
|--|--|-- |
|**Initial Access**|Phising|Received phishing email with malicious PDF|
|**Execution**|1-User Execution 2-Command & Scripting Interpreter|User executed the malicious PDF allowing the attacker to have access to the environment and use LOLBINS (Living-off-the-land binaries)
|**Persistence**| 1-Scheduled Task/Job 2-Create Account |Created a scheduled task & new user
|**Privilege Escalation**| Valid Accounts |Created new user with administrative privileges
|**Defence Evasion**| Impair Defence |Admin account disabled AV
|**Discovery**| Network Service Discovery |Discovered hosts using nslookup
|**Lateral Movement**| Remote Services |Threat actor utilised RDP to move around laterally
|**Collection**| Archive Collected Data |1.7z was found during the incident indicating likely archived data
|**Exfiltration**| Exfiltration Over Web Service |Large outbound traffic towards [transfer.sh](http://transfer.sh/) was observed
|**Impact**| Data Encrypted for Impact |Ransomware binary was deployed



## Changelog
