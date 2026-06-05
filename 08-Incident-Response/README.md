#  Incident Report: PowerShell Activity Investigation

> **Status:** Closed  
> **Severity:** Low  
> **Category:** Endpoint / Sysmon  
> **Analyst:** Zainab Abdulhasan  

---

##  Alert

PowerShell execution detected on the endpoint.

---

##  Investigation

| Field | Details |
|---|---|
| Event ID | 1 - Process Creation |
| Process | `powershell.exe` |
| Parent Process | `explorer.exe` |
| User | `DESKTOP1\zaina` |
| Log Source | `Microsoft-Windows-Sysmon/Operational` |

## 📸 Evidence

### Sysmon Event ID 1 - Process Creation

<img width="873" height="480" alt="Screenshot 2026-06-04 190145" src="https://github.com/user-attachments/assets/14054e27-ae2a-47ad-a5fc-5076ceb00b9a" />

**Observed Commands**
<img width="1011" height="490" alt="image" src="https://github.com/user-attachments/assets/45c0c30f-2a80-4d67-a8be-d4cdaf523d1d" />
<img width="929" height="442" alt="image" src="https://github.com/user-attachments/assets/f3aa3e3d-cdba-46d4-8df4-02b5fb161d51" />
<img width="982" height="447" alt="image" src="https://github.com/user-attachments/assets/7a40d5d7-1492-4697-9872-d267985d1a8c" />
```powershell
Get-Process
Get-Service
Invoke-WebRequest

