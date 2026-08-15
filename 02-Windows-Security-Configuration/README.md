# Day 2 — Windows Security Configuration & Event Log Investigation

## 🎯 Objective

The objective of this stage was to establish a basic Windows security baseline and begin investigating Windows Security Event Logs using PowerShell.

The lab was configured to provide a controlled environment for practising SOC analyst tasks such as:

- Verifying Windows Defender status
- Verifying Windows Firewall status
- Checking Windows Security Event Logs
- Investigating authentication events
- Investigating privileged logons
- Generating controlled security events
- Investigating account creation and deletion events

---

## 🖥️ Lab Environment

| Component | Configuration |
|---|---|
| Operating System | Windows 11 Pro |
| Virtualisation | Oracle VirtualBox |
| VM Name | SOC-Windows |
| Memory | 6 GB |
| Processors | 4 |
| Network | NAT |
| PowerShell | Administrator |
| Security Log | Enabled |

---

### 1. PowerShell Environment

PowerShell was opened with administrator privileges to allow security configuration and event log investigation.

![Administrator PowerShell](Screenshots/Admin%20PowerShell%20Open.png)

---

### 2. System Information Baseline

The `systeminfo` command was used to collect information about the Windows environment.

This provided information including:

Windows version and build
System architecture
Processor information
Installed memory
Network configuration
System boot information
Installed Windows hotfixes

---

### 3. Windows Firewall Verification

The Windows Firewall profiles were checked using PowerShell and the command below.

`Get-NetFirewallProfile | Select-Object Name, Enabled, DefaultInboundAction, DefaultOutboundAction`

The results showed that the Domain, Private and Public firewall profiles were enabled.

Security significance

A host-based firewall provides an additional layer of protection by controlling network traffic entering and leaving the system.

For a SOC analyst, firewall status is an important part of establishing a basic endpoint security baseline.

---

### 4. Windows Defender Verification

Microsoft Defender status was checked using the commands below:

`Get-MpComputerStatus | Select-Object AntivirusEnabled, RealTimeProtectionEnabled, AntispywareEnabled, BehaviorMonitorEnabled, IoavProtectionEnabled`

The results confirmed that the main Defender protection features were enabled.

Security significance:

Verifying endpoint protection is an important baseline check when preparing a Windows workstation for security monitoring.

---

### 5. Windows Security Event Log Baseline

The Windows Security Event Log was checked to confirm that logging was enabled and that events were being recorded.

`Get-WinEvent -ListLog Security | Select-Object LogName, IsEnabled, RecordCount`

The Security log was enabled and contained recorded events.

Why this matters:

Security Event Logs provide valuable telemetry for detecting and investigating suspicious activity on Windows systems.

---

### 6. Reviewing Recent Security Events

The most recent Security events were queried using PowerShell.

`Get-WinEvent -LogName Security -MaxEvents 10 |
Select-Object TimeCreated, Id, LevelDisplayName, ProviderName`

This provided a quick overview of recent security activity.

---

### 7. Event ID 4624 — Successful Logon

Event ID 4624 represents a successful logon.

The event was investigated using:

`Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4624} -MaxEvents 1 |
Format-List TimeCreated, Id, ProviderName, Message`

A successful logon event can provide information such as:

Account involved
Logon type
Logon ID
Authentication process
Process responsible for the logon
SOC relevance

Successful logon events can be used to investigate unusual authentication activity, particularly when combined with other events and contextual information.

---

### 8. Event ID 4672 — Special Privileges Assigned

Event ID 4672 was investigated to examine a privileged logon.

`Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4672} -MaxEvents 1 |
Format-List TimeCreated, Id, ProviderName, Message`

The event showed that special privileges were assigned to the SYSTEM account.

SOC relevance

Privileged activity is important to monitor because attackers may attempt to obtain elevated privileges after gaining access to a system.

---

### 9. Controlled Account Creation Test

A test account was deliberately created to generate a known Windows security event.

net user SOC-TestUser "LabTest123!" /add

The resulting Security Event Log was then investigated.

#### Event ID 4720 — User Account Created

Event ID 4720 indicates that a user account was created.

Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4720} -MaxEvents 1 |
Format-List TimeCreated, Id, ProviderName, Message

Investigation findings

The event showed:

Event ID: 4720
Action: User account created
Account: SOC-TestUser
Creating account: Sully
Provider: Microsoft-Windows-Security-Auditing
SOC relevance

Unexpected account creation can be an indicator of suspicious activity.

A SOC analyst could investigate:

Who created the account?
When was it created?
Was the account creation authorised?
What privileges were assigned?
What activity occurred after the account was created?

---

### 10. Controlled Account Deletion Test

The test account was then removed:

net user SOC-TestUser /delete

The resulting Security Event Log was investigated.

#### Event ID 4726 — User Account Deleted

Event ID 4726 indicates that a user account was deleted.

Get-WinEvent -FilterHashtable @{LogName='Security'; Id=4726} -MaxEvents 1 |
Format-List TimeCreated, Id, ProviderName, Message

Investigation findings

The event showed:

Event ID: 4726
Action: User account deleted
Target account: SOC-TestUser
Account performing the action: Sully
Provider: Microsoft-Windows-Security-Auditing

---

## 🔎 Investigation Workflow

This exercise demonstrated a basic SOC investigation workflow:

```
Security Baseline
       ↓
Enable / Verify Security Telemetry
       ↓
Query Windows Security Logs
       ↓
Identify Relevant Event IDs
       ↓
Generate Controlled Security Activity
       ↓
Investigate Resulting Events
       ↓
Document Findings
```
---

## 📊 Event ID Reference

| Event ID | Description                 | Lab Activity                |
| -------- | --------------------------- | --------------------------- |
| 4624     | Successful logon            | Investigated existing event |
| 4672     | Special privileges assigned | Investigated existing event |
| 4720     | User account created        | Generated and investigated  |
| 4726     | User account deleted        | Generated and investigated  |

---

## 🧠 Key Learning Outcomes

By completing this stage, I developed practical experience with:

Windows Security Event Logs
PowerShell event log queries
Windows authentication events
Privileged account activity
User account monitoring
Security telemetry
Host security baselining
Controlled event generation
Basic SOC investigation methodology

This stage provided the foundation for more advanced Windows monitoring and SIEM-based investigation in later stages of the lab.
