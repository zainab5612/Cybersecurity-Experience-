# Incident Report: Privilege Escalation Through Administrative Group Membership

> **Status:** Closed  
> **Severity:** High  
> **Category:** Privilege Escalation / Account Management  
> **Analyst:** Zainab Abdulhasan

---

##  Alert

A user account was added to the local Administrators group on a Windows endpoint.

---

##  Investigation

| Field | Details |
|---|---|
| Event ID | `4732` |
| Event Name | A member was added to a security-enabled local group |
| Account Added | `DESKTOP1\attacker` |
| Group Modified | `BUILTIN\Administrators` |
| Action Performed By | `DESKTOP1\zaina` |
| Log Source | Windows Security Log |
| Computer | `DESKTOP1.homelab.com` |

---

##  Evidence

### Windows Security Event ID 4732

<img width="927" height="477" alt="image" src="https://github.com/user-attachments/assets/072d34cb-a8c4-4eda-950d-e3b63d67bd04" />

---

##  Findings

- The account `DESKTOP1\attacker` was added to the local `Administrators` group.
- Administrative privileges were successfully granted.
- The action was performed by `DESKTOP1\zaina`.
- Event ID `4732` confirmed the group membership change.
- This activity was generated in a lab environment for detection and investigation practice.

---

##  Impact

Adding a user to the local Administrators group gives that account elevated privileges on the endpoint.

This could allow the account to:

- Install or remove software
- Change system settings
- Manage users and groups
- Access protected files
- Disable security controls

---

##  MITRE ATT&CK Mapping

| Technique ID | Technique Name |
|---|---|
| `T1078` | Valid Accounts |
| `T1098` | Account Manipulation |

---

##  Conclusion

The account `DESKTOP1\attacker` was successfully added to the local Administrators group. This activity represents privilege escalation because the account gained administrative access on the system.

**Final Classification:** Privilege Escalation Activity - Lab Generated

--



## Response Action

### Containment

- Identified the unauthorized account added to the Administrators group.
- Verified the account's recent activity and login history.
- Confirmed whether the action was approved or unauthorized.

### Account Activity Investigation

The Security log was reviewed for login activity associated with the account `attacker`.

Relevant events reviewed:

- Event ID 4624 (Successful Logon)
- Event ID 4625 (Failed Logon)
- Event ID 4688 / Sysmon Event ID 1 (Process Creation)

No additional suspicious activity was identified beyond the administrative group membership change generated during the lab exercise.



### Remediation

- Removed the account from the local Administrators group.
- Reviewed account activity for unauthorized actions.
- Verified no additional privileged accounts were created.
- If the activity had been unauthorized, a password reset would have been performed to preve
<img width="1235" height="493" alt="image" src="https://github.com/user-attachments/assets/cc5d8d8f-cb91-471a-8e94-f788e6f94d01" />





### Recovery

- Monitored the endpoint for additional suspicious activity.
- Confirmed administrative access was restored to approved users only.
- Documented findings and lessons learned.

<img width="1003" height="530" alt="image" src="https://github.com/user-attachments/assets/9f223d92-11bd-48d8-923a-9b7fe267284e" />






<img width="994" height="535" alt="image" src="https://github.com/user-attachments/assets/699033d4-a9c6-4c38-b826-884753a665c1" />
