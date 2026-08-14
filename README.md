# Home-Lab

# 🛡️ Windows SOC Analyst Home Lab

A hands-on cybersecurity home lab designed to develop practical SOC Analyst skills through Windows security monitoring, log analysis, detection engineering and incident investigation.

---

## 🎯 Objectives

The goal of this project is to build an isolated SOC environment where I can:

- Configure and harden a Windows endpoint
- Generate realistic security telemetry
- Analyse Windows Event Logs
- Use Sysmon for enhanced endpoint visibility
- Forward logs to a SIEM
- Create detection rules
- Investigate suspicious activity
- Document security incidents
- Develop practical SOC Analyst skills

---

## 🏗️ Lab Architecture

```text
Host Machine
     │
     ▼
Oracle VirtualBox
     │
     ▼
Windows 11 SOC Endpoint
     │
     ├── Windows Event Logs
     ├── Windows Security Auditing
     ├── Sysmon
     └── Security Telemetry
              │
              ▼
             SIEM
              │
              ▼
      Detection & Investigation
```

---

## 🛠️ Technologies

- Windows 11
- Oracle VirtualBox
- Windows Event Viewer
- Windows Security Auditing
- Sysmon
- PowerShell
- SIEM
- MITRE ATT&CK
- Git
- GitHub

---
## 📂 Project Structure

| Directory                  | Purpose                               |
| -------------------------- | ------------------------------------- |
| `01-virtual-machine-setup` | Windows VM creation and configuration |
| `02-windows-hardening`     | Windows security configuration        |
| `03-windows-logging`       | Windows auditing and event logging    |
| `04-sysmon`                | Sysmon installation and configuration |
| `05-siem`                  | SIEM configuration and log ingestion  |
| `06-detection-engineering` | Detection rules and queries           |
| `07-investigations`        | SOC-style incident investigations     |
| `08-attack-scenarios`      | Controlled security testing           |

---

## 📊 Project Progress

| Stage                 | Status      |
| --------------------- | ----------  |
| Virtual Machine Setup | ✅ Complete |
| Windows Installation  | ✅ Complete |
| Windows Updates       | ✅ Complete |
| Guest Additions       | ✅ Complete |
| Baseline Snapshot     | ✅ Complete |
| Windows Hardening     | ⏳ Upcoming |
| Security Logging      | ⏳ Upcoming |
| Sysmon                | ⏳ Upcoming |
| SIEM                  | ⏳ Upcoming |
| Detection Engineering | ⏳ Upcoming |
| SOC Investigations    | ⏳ Upcoming |

---

## 🔎 Investigations

Future investigations will document:

Suspicious PowerShell activity
Failed authentication attempts
Suspicious process execution
Account activity
Persistence techniques
Network activity
Privilege escalation
Other security events

Each investigation will include:

Alert
Initial triage
Evidence
Timeline
Investigation
MITRE ATT&CK mapping
Findings
Recommended response
Lessons learned

--- 

## 🧠 Skills Demonstrated

This project demonstrates practical experience with:

Windows administration
Security monitoring
Log analysis
Endpoint telemetry
SIEM
Detection engineering
Incident response
Threat detection
MITRE ATT&CK
PowerShell
Technical documentation

---

## ⚠️ Disclaimer

This project is designed for educational and defensive cybersecurity purposes.

All security testing is performed within an isolated virtual environment controlled by me.
