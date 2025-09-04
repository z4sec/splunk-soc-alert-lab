Splunk Alerts and Dashboard for SOC Home Lab


A- Overview

This project focuses on creating and visualizing security alerts in Splunk for a home lab SOC environment running on a Windows server. It monitors five key Windows event IDs (1102, 4625, 4688, 4720+4726, 2003) to detect potential security incidents. Alerts are configured in Splunk and combined into a classic dashboard for real-time monitoring.

The lab demonstrates skills in SIEM alert configuration, log analysis, and dashboard creation, essential for a SOC analyst role.


B- Lab Setup

Platform: Windows (Splunk server).

Tool: Splunk Enterprise for log ingestion, alert creation, and dashboard visualization.

Data Source: Windows event logs ingested into Splunk.



C- Alerts and Events

Below are the configured alerts for specific Windows event IDs, including their purpose and significance in a SOC context. Each alert is accompanied by 6-7 screenshots showing log details, alert configurations, and dashboard views.

1. Event ID 1102: Audit Log Cleared

Purpose: Detects when the security event log is cleared, which could indicate an attacker attempting to cover their tracks.

Why It Matters: Unauthorized log clearing is a common tactic to evade detection after malicious activity (e.g., malware or privilege escalation).

Alert Configuration: Triggers when EventCode=1102 is detected in Windows Security logs.

Screenshots -> EVENT = 1102 Security Log Clear Detetction


2. Event ID 4625: Failed Login Attempts

Purpose: Monitors failed login attempts, indicating potential brute-force attacks or credential guessing.

Why It Matters: Multiple failed logins may signal an attacker attempting to gain unauthorized access to a system or account.

Alert Configuration: Triggers on EventCode=4625 with a threshold (e.g., 5 failed attempts in 5 minutes from the same source).

Screenshots -> EVENT = 4625 Failed login alert


3. Event ID 4688: Process Creation

Purpose: Tracks new process creation, helping detect malicious processes or suspicious application execution.

Why It Matters: Attackers often launch processes (e.g., cmd.exe, powershell.exe) to execute malware or perform reconnaissance.

Alert Configuration: Triggers on EventCode=4688 for specific processes or unusual patterns (e.g., unexpected executables).

Screenshots -> EVENT = 4688 Powershell or cmd activity


4. Event IDs 4720+4726: User Account Created/Deleted

Purpose: Detects creation (4720) or deletion (4726) of user accounts, indicating potential privilege escalation or cleanup by an attacker.

Why It Matters: Unauthorized account changes can signal an attacker establishing persistence or removing traces.

Alert Configuration: Triggers on EventCode=4720 or EventCode=4726 in Security logs.

Screenshots -> EVENT = 4720+4726 User account created & deleted


5. Event ID 2003: DNS-Related Event

Purpose: Monitors DNS query anomalies (context-specific; assumed to detect unusual DNS activity).

Why It Matters: DNS events can reveal reconnaissance, data exfiltration, or attacks like DNS amplification (context depends on your setup).

Alert Configuration: Triggers on EventCode=2003 for suspicious patterns (e.g., high query volume or specific domains).

Screenshots -> EVENT =2003 Firewall ON-OFF


D- Splunk Dashboard

A classic Splunk dashboard was created to combine all five alerts for real-time monitoring. It includes:

Screenshots -> Created Dashboard , Dashboard Monitoring


E- How to Replicate


1-Install Splunk Enterprise on a Windows machine.

2-Configure Splunk to ingest Windows event logs (Security, System, DNS logs).

3-Create alerts for Event IDs 1102, 4625, 4688, 4720, 4726, and 2003 with appropriate thresholds.

4-Build a dashboard in Splunk to visualize all alerts (use XML or Splunk’s dashboard editor).

5-Test alerts by generating relevant events (e.g., failed logins, process creation) in the lab.



Note:- Screenshots

Each event ID has a dedicated folder with 6-7 screenshots showing:


Raw event logs in Splunk.

Alert configuration settings.

Dashboard panels for each alert. Browse screenshots/ for all images.




Contact

LinkedIn: www.linkedin.com/in/zeeshan-alam-073102246

This project showcases my ability to configure and visualize security alerts in Splunk for SOC monitoring.
