# 🔐 Initial Access via SSH Brute Force Attack

## 📌 Overview
This scenario simulates an SSH brute-force attack against a Linux server and demonstrates how a SOC detects suspicious authentication activity and triggers an automated response using SIEM and SOAR 🚨🤖.

---
## 🧪 Attack Simulation
- An attacker attempts multiple SSH login attempts using different username and password combinations.
- Repeated authentication failures are generated in the Linux SSH logs.
- A successful SSH login is achieved after several failed attempts, indicating a brute-force attack.

---
## 🔍 Detection Logic
- The SIEM monitors Linux authentication logs (`/var/log/auth.log`).
- Multiple failed SSH login attempts from the same source IP are detected within a short time window.
- A correlation rule flags the activity as a potential SSH brute-force attack.
- The alert is enriched with source IP, username, and timestamp details.

---
## 🤖 Automated Response
- The SOAR workflow is triggered automatically when the SSH brute-force alert is generated.
- The source IP address is validated and enriched for reputation.
- The malicious IP is temporarily blocked on the target system to prevent further access attempts.
- The action is logged for analyst review and auditing.

---
## 🧠 Analyst Conclusion
This activity was confirmed as a brute-force attempt targeting SSH services. The automated response successfully reduced attacker dwell time and prevented further unauthorized access. This scenario demonstrates how SOC teams can combine detection, correlation, and automation to handle common initial access attacks efficiently.
