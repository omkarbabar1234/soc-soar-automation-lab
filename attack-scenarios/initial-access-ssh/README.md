# 🔐 Initial Access via SSH Brute Force Attack

## 📌 Overview
This scenario simulates an SSH brute-force attack against a Linux server and demonstrates how a SOC detects suspicious authentication activity and triggers an automated response using SIEM and SOAR 🚨🤖.

---
## 🧪 Attack Simulation
- A VMware-based lab was set up with **Kali Linux (attacker)** and **Ubuntu Linux (target).**
- From the Kali Linux machine, an SSH brute-force attack was launched against the Ubuntu server using Hydra.
- Multiple failed SSH authentication attempts were generated in a short time window.
- A successful SSH login occurred after repeated attempts, simulating unauthorized initial access.
 
---
## 🔍 Detection Logic
- The Ubuntu system generates authentication logs in `/var/log/auth.log`.
- Multiple failed SSH login attempts from the same source IP are detected within a short time window.
- The SIEM parses SSH failure events and identifies a brute-force pattern based on frequency and repetition.
- Once the threshold is crossed, an SSH brute-force alert is generated with source IP, targeted user, and timestamps.

---
## 🤖 Automated Response
- The SOAR workflow is triggered automatically when the SSH brute-force alert is generated.
- The source IP address is validated and enriched for reputation.
- The malicious IP is temporarily blocked on the target system to prevent further access attempts.
- The action is logged for analyst review and auditing.

---
## 🧠 Analyst Conclusion
This activity was confirmed as a brute-force attempt targeting SSH services. The automated response successfully reduced attacker dwell time and prevented further unauthorized access. This scenario demonstrates how SOC teams can combine detection, correlation, and automation to handle common initial access attacks efficiently.

