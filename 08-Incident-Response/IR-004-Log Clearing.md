
#  Incident Report: Audit Log Clearing Activity

> **Status:** Closed  
> **Severity:** High  
> **Category:** Defense Evasion / Log Manipulation  
> **Analyst:** Zainab Abdulhasan

---

##  Alert

Windows Security logs were cleared from the system.

---

##  Investigation

| Field | Details |
|---|---|
| Event ID | `1102` |
| Event Name | Audit Log Cleared |
| User Account | `DESKTOP1\zaina` |
| Log Source | Windows Security Log |
| Computer | `DESKTOP1.homelab.com` |

---

##  Evidence

### Windows Security Event ID 1102

<img width="932" height="559" alt="image" src="https://github.com/user-attachments/assets/b91c6525-5564-41a7-8aa7-64e5c34cf1cf" />

The Security log recorded that the audit log was cleared.




## Incident Response

## Investigation

4624 - Successful Logon
4625 - Failed Logon
4720 - User Created
4732 - Added to Administrators
4688 - Process Creation

Security, Application, System logs were cleared. No other endpoints were affected.
---

## Preserve Evidence
Evidence was preserved by exporting Security, Sysmon, and PowerShell logs and capturing active processes and network connections prior to remediation.


<img width="1067" height="571" alt="Screenshot 2026-06-05 101445" src="https://github.com/user-attachments/assets/c7cd3279-2c51-4bcc-aa30-b6e560bb3051" />

---



## Containment

Disable affected account
Remove administrative privileges
Isolate affected system

---
<img width="1216" height="438" alt="image" src="https://github.com/user-attachments/assets/3109104b-71ec-44c1-8ca8-7c631d155c48" />

---

**Account Responsible**

```text
DESKTOP1\zaina



