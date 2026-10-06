# 🛡 Windows Event Log Investigation: Threat Triage & Forensic Analysis

## 📌 Executive Summary
As part of defensive security operations (SOC), monitoring and analyzing Windows Security Event Logs is critical for detecting unauthorized access, privilege escalation, and persistence mechanisms. This project investigates simulated security events on a Windows endpoint, focusing on identifying failed logons, successful authentications, and suspicious account creation.
🛠️ Tools & Environment
Operating System: Windows 10 / 11

Investigation Tool: Windows Event Viewer (Security Log)

Key Event IDs Targeted:

4625: An account failed to log on (Brute Force Indicator)

4624: An account was successfully logged on

4720: A user account was created (Persistence Indicator)

🔍 Investigation Steps & Findings
1. Detecting Failed Logons (Event ID 4625)
Objective: Identify potential brute-force or unauthorized access attempts.

Analysis: Filtered Windows Security logs for Event ID 4625. The logs successfully captured unauthorized authentication attempts.

📸 Evidence / Screenshot:
<img width="959" height="500" alt="event-4625-failed-logon" src="https://github.com/user-attachments/assets/58853ba8-af4e-4dd6-af67-f8c103d2641c" />


2. Tracking Successful Access (Event ID 4624)
Objective: Monitor successful logon events to correlate with suspicious activities.

Analysis: Filtered logs for Event ID 4624 to review valid system and user sessions.

📸 Evidence / Screenshot:
<img width="960" height="503" alt="event-4624-successful-logon" src="https://github.com/user-attachments/assets/5145bccc-dbfd-46e8-b3c9-0d62f622acbe" />


3. Identifying Persistence Mechanism - Account Creation (Event ID 4720)
Objective: Detect unauthorized privilege escalation or backdoor creation by attackers.

Analysis: Filtered logs for Event ID 4720, which highlights the creation of a new local user account (TestUser123). This is a classic indicator of persistence used by threat actors to maintain access.

📸 Evidence / Screenshot:
<img width="955" height="504" alt="event-4720-user-creation" src="https://github.com/user-attachments/assets/a91d13b1-3c0e-4342-8b79-bb88fc89f6fe" />


🚀 Indicators of Compromise (IOCs)
Suspicious Username Created: TestUser123

Target System: Local Endpoint

Key Log Categories: Windows Security Auditing

💡 Remediation & Recommendations
Account Auditing: Regularly audit local and domain user accounts for unauthorized creations.

Brute-Force Mitigation: Implement Account Lockout Policies and Multi-Factor Authentication (MFA).

SIEM Integration: Forward Windows Security Event Logs to a centralized SIEM (like Splunk or ELK) for real-time alerting.
