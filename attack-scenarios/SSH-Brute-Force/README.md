# 🔐 Initial Access via SSH Brute Force Attack

## 📌 Overview
This scenario simulates an SSH brute-force attack against a Linux server and demonstrates how a SOC detects suspicious authentication activity, correlates alerts, and notifies analysts using SIEM and SOAR with human-in-the-loop response.

---
## 🧪 Attack Simulation
- A VMware-based lab was set up with **Kali Linux (attacker)** and **Ubuntu Linux (target)**.
- The **Hydra** tool was used from the Kali Linux machine to perform an SSH brute-force attack against the Ubuntu server.
- Multiple failed SSH authentication attempts were generated in a short time window.
- A successful SSH login occurred after repeated attempts, simulating unauthorized initial access.

---
## 🔍 Detection Logic
- The Ubuntu system generates SSH authentication logs in `/var/log/auth.log`.
- These logs are collected and analyzed by **Wazuh**.
- Wazuh detects multiple failed SSH login attempts from the same source IP within a short time window.
- A correlation rule is triggered (for example: SSH authentication failure rule ID) when the defined threshold is exceeded.
- The alert includes source IP, targeted username, timestamps, and severity, indicating a brute-force attack (MITRE ATT&CK: **T1110 – Brute Force**).

---
## 🤖 Automated Response
- When the SSH brute-force alert is generated, it is forwarded to the SOAR platform via webhook.
- The SOAR workflow correlates the alert and creates a case in the case management system for investigation.
- An **email notification is sent to the analyst/security team**, providing details of the attack and affected host.
- No automatic containment is executed at this stage; analyst review and approval are required before any response action
---
## 🧠 Analyst Conclusion
This activity was confirmed as a brute-force attempt targeting SSH services. The automated response successfully reduced attacker dwell time and prevented further unauthorized access. This scenario demonstrates how SOC teams can combine detection, correlation, and automation to handle common initial access attacks efficiently.


