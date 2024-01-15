# Critical RCE Vulnerability Uncovered In Jupiner SRX Firewalls And EX Switches

[Reference from TheHackerNews](https://thehackernews.com/2024/01/critical-rce-vulnerability-uncovered-in.html?_m=3n%2e009a%2e3252%2ene0ao45e79%2e28wa)

- Jupiner Networks has released patches for critical remote code execution (RCE) vulnerability.
- Tracked as CVE-2024-21591, 9.8 on the CVSS scoring system.
- An out-of-bounds write vulnerability in J-Web of Juniper Networks Junos OS SRX Series and EX Series allows an unauthenticated, network-based attacker to cause a Denial-of-Service (DoS) or Remote Code Execution (RCE) and obtain root privileges on the device.
- Caused by use of an insecure function allowing a bad actor to overwrite arbitrary memory.
- The versions that fixed:
  - 20.4R3-S9
  - 21.2R3-S7
  - 21.3R3-S5
  - 21.4R3-S5
  - 22.1R3-S4
  - 22.2R3-S3
  - 22.3R3-S2
  - 22.4R2-S2
  - 22.4R3
  - 23.2R1-S1
  - 23.2R2
  - 23.4R1
  - and later
- As temporary solution until the fixes are deployed, company recommends that users disable J-Web or limit access to trusted hosts.

# Medusa Ransomware On The Rise: From Data Leaks To Multi-Extortion

[Reference from TheHackerNews](https://thehackernews.com/2024/01/medusa-ransomware-on-rise-from-data.html?_m=3n%2e009a%2e3252%2ene0ao45e79%2e28wy)

- The Medusa ransomware threat actors have escalated their operations with the launch of a dedicated dark web data leak site in February 2023 to expose sensitive information from non-compliant victims.
- As part of their multi-extortion strategy, this group will provide victims with multiple options when their data is posted on their leak site, such as time extension, data deletion or download of all the data.
- All of these options have a price tag depending on the organization impacted by this group.
- The group's ransomware attacks begin by exploiting unpatched vulnerabilities in internet-facing assets or applications, along with the hijacking of legitimate accounts; often, they utilize initial access brokers to establish a foothold in order to target networks.
- Medusa's leak site displays information about the organizations, ransom demanded, the amount of time left before the stolen data is released publicly, and the number of views in a bid to exert pressure on the company.
- The actors also offer different choices to the victim, all of which involve some form of extortion to delete or download the pilfered data and seek a time extension to prevent the data from being released.