# GPO Configuration — NexaCore Technologies

---

## NexaCore - Base Security Policy
**Linked to:** nexacore.local (domain root)  
**Applies to:** All users and computers in domain

### Password Policy
| Setting | Value |
|---------|-------|
| Minimum password length | 12 characters |
| Password complexity | Enabled |
| Maximum password age | 90 days |
| Minimum password age | 1 day |
| Password history | 10 passwords remembered |

### Account Lockout Policy
| Setting | Value |
|---------|-------|
| Lockout threshold | 5 invalid attempts |
| Lockout duration | 30 minutes |
| Reset counter after | 30 minutes |

---

## NexaCore - IT Policy
**Linked to:** OU=IT,OU=NexaCore  
**Applies to:** IT department users and computers

### User Rights Assignment
| Setting | Value |
|---------|-------|
| Allow log on through Remote Desktop Services | NEXACORE\GRP-IT, Administrators |
| Allow log on locally | NEXACORE\GRP-IT, Administrators |

**Business justification:** IT staff require RDP access to 
manage and troubleshoot domain-joined machines remotely.

---

## NexaCore - Finance Policy
**Linked to:** OU=Finance,OU=NexaCore  
**Applies to:** Finance department users

### Removable Storage
| Setting | Value |
|---------|-------|
| All Removable Storage classes: Deny all access | Enabled |

### Audit Policy
| Setting | Value |
|---------|-------|
| Audit object access | Success and Failure |
| Audit logon events | Success and Failure |

**Business justification:** Finance handles sensitive financial 
data. USB restriction prevents data exfiltration. Audit logging 
supports compliance requirements.

---

## NexaCore - HR Policy
**Linked to:** OU=HR,OU=NexaCore  
**Applies to:** HR department users

### Removable Storage
| Setting | Value |
|---------|-------|
| All Removable Storage classes: Deny all access | Enabled |

### Control Panel
| Setting | Value |
|---------|-------|
| Prohibit access to Control Panel and PC Settings | Enabled |

**Business justification:** HR handles PII and employee records. 
USB restriction and Control Panel lockdown reduce insider 
threat risk.

---

## NexaCore - Sales Policy
**Linked to:** OU=Sales,OU=NexaCore  
**Applies to:** Sales department users

### Screen Lock
| Setting | Value |
|---------|-------|
| Enable screen saver | Enabled |
| Screen saver timeout | 600 seconds (10 minutes) |
| Password protect screen saver | Enabled |

**Business justification:** Sales staff frequently leave 
desks for client meetings. Auto-lock prevents unauthorized 
access to CRM and client data.

---

## NexaCore - Legal Policy
**Linked to:** OU=Legal,OU=NexaCore  
**Applies to:** Legal department users

### Removable Storage
| Setting | Value |
|---------|-------|
| All Removable Storage classes: Deny all access | Enabled |

### Audit Policy
| Setting | Value |
|---------|-------|
| Audit object access | Success and Failure |
| Audit privilege use | Success and Failure |
| Audit policy change | Success and Failure |

**Business justification:** Legal handles privileged and 
confidential case files. Comprehensive audit trail supports 
regulatory compliance and legal hold requirements.

---

## GPO Verification
Verified all GPOs applying correctly via:
- gpresult /r on CLIENT-01
- Group Policy Results in GPMC
- Settings tab in GPMC showing configured values