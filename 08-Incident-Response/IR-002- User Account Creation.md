# Incident Assessment

## Severity

🟡 Medium

## Analysis

A new local account named **attacker** was created by user **zaina** using the Windows `net.exe` utility.

While this activity was performed intentionally within the lab environment, unauthorized account creation is commonly associated with persistence techniques used by threat actors after gaining access to a system.

Creating additional user accounts can allow attackers to maintain access even if the original compromised account is disabled.

---

# Event ID 4720 - User Account Created

## Description

Event ID 4720 records the creation of a new local user account.

## Investigation

The Security Log revealed that a new account was created.

### Findings

| Field | Value |
|---------|---------|
| Event ID | 4720 |
| Created Account | attacker |
| Created By | zaina |
| Computer | DESKTOP1.homelab.com |
| Time | 6/4/2026 8:29:30 PM |

### Evidence

The Security Log showed:

```text
Created Account:
attacker

Created By:
zaina
```
<img width="976" height="466" alt="Screenshot 2026-06-04 203221" src="https://github.com/user-attachments/assets/865d9f9c-53d4-4b34-a776-066630e1d8f6" />


---

# Event ID 1 - Process Creation

## Description

Sysmon Event ID 1 records process creation activity.

## Investigation

To determine how the account was created, Sysmon logs were reviewed.

The following command was identified:

```cmd
net user attacker Password123! /add
```

### Findings

| Field | Value |
|---------|---------|
| Process | net.exe |
| User | zaina |
| Command | net user attacker Password123! /add |
| Time | 6/4/2026 8:29:30 PM |

### Evidence

The Sysmon Process Creation event recorded:

```cmd
"C:\WINDOWS\system32\net.exe" user attacker Password123! /add
```

This confirms that the account was created manually through the Windows command line utility.

<img width="984" height="466" alt="Screenshot 2026-06-04 203105" src="https://github.com/user-attachments/assets/1f4da96c-b176-4716-8095-6653c719e269" />

---

# Timeline

| Time | Event ID | Description |
|---------|---------|---------|
| 8:29:30 PM | 1 | net.exe executed |
| 8:29:30 PM | 4720 | User account created |
| 8:29:30 PM | Correlated | Account creation confirmed |

---

