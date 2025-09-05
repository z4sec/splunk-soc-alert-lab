# Splunk SOC Alert Lab

## Overview
This project simulates a Security Operations Center (SOC) environment using Splunk on a Windows server. It configures alerts for five Windows event IDs (1102, 4625, 4688, 4720+4726, 2003) to detect potential security incidents, visualized in a classic Splunk dashboard. Built in a home lab, it showcases SIEM skills essential for a SOC analyst role.

## Lab Setup
- **Platform**: Windows (Splunk server).
- **Tool**: Splunk Enterprise for log ingestion, alert creation, and dashboard visualization.
- **Data Source**: Windows event logs (Security, System, Firewall).

## Alerts and Events
The following table summarizes the configured alerts, their purpose, and why they matter in a SOC context:

| Event ID | Purpose | Why It Matters |
|----------|---------|---------------|
| 1102 | Detects security log clearing | Indicates an attacker hiding their tracks (e.g., malware, privilege escalation). |
| 4625 | Monitors failed login attempts | Signals potential brute-force or credential guessing attacks. |
| 4688 | Tracks process creation (e.g., cmd.exe, powershell.exe) | Detects malicious processes or reconnaissance activity. |
| 4720+4726 | Detects user account creation/deletion | Indicates privilege escalation or attacker cleanup. |
| 2003 | Monitors firewall ON/OFF changes | Reveals configuration changes that could enable attacks. |

### Event ID 1102: Security Log Cleared
- **Alert Configuration**: Triggers on `EventCode=1102` in Windows Security logs.
- **Screenshots**:
  - ![Index Search](EVENT%20%3D%201102%20Security%20Log%20Clear%20Detetction/1-%20index-search.png)
  - ![Search Result](EVENT%20%3D%201102%20Security%20Log%20Clear%20Detetction/2-%20search-result.png)
  - ![Edit Alert](EVENT%20%3D%201102%20Security%20Log%20Clear%20Detetction/3-%20edit-alert.png)
  - ![Alert Saved](EVENT%20%3D%201102%20Security%20Log%20Clear%20Detetction/4-%20alert-saved.png)
  - ![Alert Triggered](EVENT%20%3D%201102%20Security%20Log%20Clear%20Detetction/5-%20alert-triggered.png)
  - Full folder: [EVENT = 1102 Security Log Clear Detetction](EVENT%20%3D%201102%20Security%20Log%20Clear%20Detetction/)

### Event ID 4625: Failed Login Attempts
- **Alert Configuration**: Triggers on `EventCode=4625` with a threshold (e.g., 5 failed attempts in 5 minutes).
- **Screenshots**:
  - ![Index Search](EVENT%20%3D%204625%20Failed%20login%20alert/1-%20index-search.png)
  - ![Search Result](EVENT%20%3D%204625%20Failed%20login%20alert/2-%20search%20result.png)
  - ![Edit Alert](EVENT%20%3D%204625%20Failed%20login%20alert/3-%20edit%20alert.png)
  - ![Alert Saved](EVENT%20%3D%204625%20Failed%20login%20alert/4-%20alert%20saved.png)
  - ![Alert Triggered](EVENT%20%3D%204625%20Failed%20login%20alert/5-%20alert%20triggered.png)
  - Full folder: [EVENT = 4625 Failed login alert](EVENT%20%3D%204625%20Failed%20login%20alert/)

### Event ID 4688: Powershell or CMD Activity
- **Alert Configuration**: Triggers on `EventCode=4688` for specific or unusual processes.
- **Screenshots**:
  - ![Index Search](EVENT%20%3D%204688%20Powershell%20or%20cmd%20activity/1-%20index%20search.png)
  - ![Edit Alert](EVENT%20%3D%204688%20Powershell%20or%20cmd%20activity/2-%20edit%20alert.png)
  - ![Alert Saved](EVENT%20%3D%204688%20Powershell%20or%20cmd%20activity/3-%20alert%20saved.png)
  - ![Alert Triggered](EVENT%20%3D%204688%20Powershell%20or%20cmd%20activity/4-%20alert%20triggered.png)
  - Full folder: [EVENT = 4688 Powershell or cmd activity](EVENT%20%3D%204688%20Powershell%20or%20cmd%20activity/)

### Event IDs 4720+4726: User Account Created/Deleted
- **Alert Configuration**: Triggers on `EventCode=4720` or `EventCode=4726`.
- **Screenshots**:
  - ![Index Search](EVENT%20%3D%204720%2B4726%20User%20account%20created%20%26%20deleted/1-%20index%20search.png)
  - ![Search Result](EVENT%20%3D%204720%2B4726%20User%20account%20created%20%26%20deleted/2-%20search%20result.png)
  - ![Edit Alert](EVENT%20%3D%204720%2B4726%20User%20account%20created%20%26%20deleted/3-%20edit%20alert.png)
  - ![Alert Saved](EVENT%20%3D%204720%2B4726%20User%20account%20created%20%26%20deleted/4-%20alert%20saved.png)
  - ![Alert Triggered](EVENT%20%3D%204720%2B4726%20User%20account%20created%20%26%20deleted/5-%20alert%20triggered.png)
  - Full folder: [EVENT = 4720+4726 User account created & deleted](EVENT%20%3D%204720%2B4726%20User%20account%20created%20%26%20deleted/)

### Event ID 2003: Firewall ON/OFF
- **Alert Configuration**: Triggers on `EventCode=2003` for firewall configuration changes.
- **Screenshots**:
  - ![Index Search](EVENT%20%3D2003%20Firewall%20ON-OFF/1-%20index%20search.png)
  - ![Edit Alert](EVENT%20%3D2003%20Firewall%20ON-OFF/2-%20edit%20alert.png)
  - ![Alert Saved](EVENT%20%3D2003%20Firewall%20ON-OFF/3-%20alert%20saved.png)
  - ![Alert Triggered](EVENT%20%3D2003%20Firewall%20ON-OFF/4-%20alert%20triggered.png)
  - Full folder: [EVENT =2003 Firewall ON-OFF](EVENT%20%3D2003%20Firewall%20ON-OFF/)

## Dashboard
A classic Splunk dashboard combines all alerts for real-time monitoring, with tables and charts for each event ID.
- Screenshots:
  - ![Created Dashboard](Created%20Dashboard.png)
  - ![Dashboard Monitoring](Dashboard%20Monitoring.png)

## How to Replicate
1. Install Splunk Enterprise on a Windows machine.
2. Configure Splunk to ingest Windows event logs (Security, System, Firewall).
3. Create alerts for Event IDs 1102, 4625, 4688, 4720, 4726, and 2003 with thresholds.
4. Build a dashboard using Splunk’s editor or XML.
5. Test by generating events (e.g., failed logins, process creation).

## Screenshots
Each event ID folder contains 4-5 screenshots showing:
- Raw event logs in Splunk.
- Alert configuration settings.
- Triggered alerts.
Browse screenshots for all images.

## Future Improvements
- Integrate Snort IDS/IPS for network monitoring.
- Add Wireshark for packet analysis.
- Automate alert triage with Python/Bash scripts.
- Map alerts to MITRE ATT&CK framework.

## Contact
LinkedIn: [Zeeshan Alam](https://www.linkedin.com/in/zeeshan-alam-073102246)  
This project showcases my SOC analyst skills in SIEM, log analysis, and dashboard creation.
