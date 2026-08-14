# Home-Lab

<img width="1296" height="1184" alt="image" src="https://github.com/user-attachments/assets/4061b45f-b449-44bf-9135-fc3264ab5113" />


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
                    ┌─────────────────────┐
                    │    Host Machine     │
                    │     Windows 11      │
                    └──────────┬──────────┘
                               │
                        Oracle VirtualBox
                               │
                               ▼
                    ┌─────────────────────┐
                    │    SOC-Windows      │
                    │     Windows 11      │
                    │                     │
                    │  Security Logs      │
                    │  Sysmon             │
                    │  Audit Policies     │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │        SIEM         │
                    │                     │
                    │ Log Collection      │
                    │ Detection Rules     │
                    │ Investigation       │
                    └─────────────────────┘
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
