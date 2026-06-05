## Sysmon Installation and Log collection

## Objective
Install Sysmon on Windows 11 machine endpoint visibility and collect detailed telemerty. the logs provide visibility into process, network, conections, and system activity, supporting future detection, threat hunting, and incident response.

## Skills Demonestrated.




# Sysmon Installation

## Download Sysmon

Download Sysmon from Microsoft Sysinternals.

## Download Configuration File

Download the SwiftOnSecurity Sysmon configuration file and save it as:

```powershell
C:\Users\zaina\Downloads\Sysmon\sysmonconfig.xml
```

## Install Sysmon

Open PowerShell as Administrator and run:

```powershell
.\Sysmon64.exe -accepteula -i sysmonconfig.xml
```
---
<img width="1149" height="466" alt="image" src="https://github.com/user-attachments/assets/494c2a11-fb7d-4d75-8e99-5550cc05bb07" />

---


### Verification

Open Event Viewer and navigate to:

```text
Applications and Services Logs
└── Microsoft
    └── Windows
        └── Sysmon
            └── Operational
```

Verify that Sysmon is generating events such as:

- Event ID 1 - Process Creation
- Event ID 13 - Registry Value Set
- Event ID 22 - DNS Query

<img width="1209" height="593" alt="image" src="https://github.com/user-attachments/assets/1bf483fb-cc6f-40f1-99fb-9b3fa22e32e1" />

---

# Investigation Scenario

## Scenario

A user launches PowerShell.

The goal is to determine:

- Who launched the process
- When it was launched
- What process started it
- What activity occurred afterward

---

# Event ID 1 - Process Creation

## Description

Event ID 1 records process creation activity.

## Investigation

The log entry showed that:

- `powershell.exe` was executed
- The execution time was recorded
- Parent process information was available
- User account information was available

## Why It Matters

This event helps analysts determine:

- Which user launched a process
- When the process was executed
- Which process started it
- What command-line arguments were used

---
<img width="1041" height="638" alt="image" src="https://github.com/user-attachments/assets/f0842a4f-5660-48ac-9128-bc89300aae89" />
<img width="1104" height="704" alt="image" src="https://github.com/user-attachments/assets/0821d2d5-71b7-4a94-8063-ea2700a82313" />
<img width="910" height="597" alt="image" src="https://github.com/user-attachments/assets/3d6fd227-5a2b-45e8-ad72-a451fca73cee" />

---
# Event ID 3 - Network Connection

## Description

Event ID 3 records outbound network connections initiated by a process.

## Investigation

PowerShell established an HTTPS connection.

### Findings

| Time | Event ID | Observation |
|--------|--------|-------------|
| 6:06 PM | 3 | HTTPS connection established |

## Why It Matters

This event can help identify:

- External connections
- Destination IP addresses
- Destination ports
- Potential command-and-control communication
---
<img width="901" height="571" alt="Screenshot 2026-06-04 180334" src="https://github.com/user-attachments/assets/04b8cda6-f659-4eca-96dd-40c21f2e2f01" />

---

# Event ID 8 - Create Remote Thread

## Description

Event ID 8 records remote thread creation activity between processes.

## Investigation

The event involved:

```text
dwm.exe
```

Desktop Window Manager (`dwm.exe`) is responsible for rendering the Windows graphical interface.

## Assessment

Based on the observed behavior, this activity appeared to be normal operating system activity and was not considered suspicious.

---
<img width="900" height="601" alt="Screenshot 2026-06-04 181353" src="https://github.com/user-attachments/assets/9627eba0-4869-459b-81e5-d14985d752f9" />

---
# Event ID 11 - File Created

## Description

Event ID 11 records file creation activity.

## Investigation

PowerShell created a temporary file named:

```text
__PSScriptPolicyTest
```

### Findings

| Time | Event ID | Process | Observation |
|--------|--------|---------|-------------|
| 6:05 PM | 11 | powershell.exe | Temporary file created |

## Assessment

PowerShell commonly creates this file when checking script execution policies during startup.

---
<img width="903" height="595" alt="Screenshot 2026-06-04 181615" src="https://github.com/user-attachments/assets/aea16116-1fc6-474e-8c87-69158f7815c5" />

---

# Event ID 13 - Registry Value Set

## Description

Event ID 13 records registry modifications.

## Investigation

The event showed a registry value being created under the RunOnce registry key.

## Assessment

The modification was performed by the Microsoft Edge installer and appeared to be legitimate software installation activity. 

---
<img width="903" height="497" alt="image" src="https://github.com/user-attachments/assets/138cb5b3-16e2-4147-9c0a-2a3eef221a21" /> 

---
# Event ID 22 - DNS Query

## Description

Event ID 22 records DNS requests performed by processes.

## Investigation

The process:

```text
lsass.exe
```

performed a DNS lookup for:

```text
homelab.com
```

### Findings

| Time | Event ID | Process | Query |
|--------|--------|---------|--------|
| 6:01 PM | 22 | lsass.exe | homelab.com |

## Assessment

LSASS was attempting to locate a domain controller for the Active Directory domain.

---
<img width="881" height="484" alt="image" src="https://github.com/user-attachments/assets/bf9b351e-e589-4ba1-bff7-17e0f48f51f6" />




