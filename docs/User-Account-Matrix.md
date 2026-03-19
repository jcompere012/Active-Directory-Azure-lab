# User Account Matrix — NexaCore Technologies
**Domain:** nexacore.local  
**Total accounts:** 23 (19 users + 4 admin accounts)

---

## Standard User Accounts

### IT Department
| Full Name | Username | Title | OU Path | Group |
|-----------|----------|-------|---------|-------|
| Alex Torres | atorres | IT Manager | NexaCore/IT/Users | GRP-IT |
| Brian Nguyen | bnguyen | Systems Administrator | NexaCore/IT/Users | GRP-IT |
| Carlos Patel | cpatel | Help Desk Technician | NexaCore/IT/Users | GRP-IT |
| Diana Kim | dkim | Network Engineer | NexaCore/IT/Users | GRP-IT |

### Finance Department
| Full Name | Username | Title | OU Path | Group |
|-----------|----------|-------|---------|-------|
| Sandra Williams | swilliams | Finance Manager | NexaCore/Finance/Users | GRP-Finance |
| Tom Brown | tbrown | Accountant | NexaCore/Finance/Users | GRP-Finance |
| Uma Davis | udavis | Financial Analyst | NexaCore/Finance/Users | GRP-Finance |

### HR Department
| Full Name | Username | Title | OU Path | Group |
|-----------|----------|-------|---------|-------|
| Laura Garcia | lgarcia | HR Manager | NexaCore/HR/Users | GRP-HR |
| Mike Wilson | mwilson | HR Specialist | NexaCore/HR/Users | GRP-HR |
| Nina Moore | nmoore | Recruiter | NexaCore/HR/Users | GRP-HR |

### Sales Department
| Full Name | Username | Title | OU Path | Group |
|-----------|----------|-------|---------|-------|
| Ryan Johnson | rjohnson | Sales Manager | NexaCore/Sales/Users | GRP-Sales |
| Emily Martinez | emartinez | Account Executive | NexaCore/Sales/Users | GRP-Sales |
| Frank Anderson | fanderson | Sales Representative | NexaCore/Sales/Users | GRP-Sales |
| Grace Thomas | gthomas | Sales Representative | NexaCore/Sales/Users | GRP-Sales |

### Operations Department
| Full Name | Username | Title | OU Path | Group |
|-----------|----------|-------|---------|-------|
| Henry Jackson | hjackson | Operations Manager | NexaCore/Operations/Users | GRP-Operations |
| Iris White | iwhite | Operations Analyst | NexaCore/Operations/Users | GRP-Operations |
| James Harris | jharris | Logistics Coordinator | NexaCore/Operations/Users | GRP-Operations |

### Legal Department
| Full Name | Username | Title | OU Path | Group |
|-----------|----------|-------|---------|-------|
| Karen Lewis | klewis | Legal Counsel | NexaCore/Legal/Users | GRP-Legal |
| Oscar Clark | oclark | Paralegal | NexaCore/Legal/Users | GRP-Legal |

---

## Admin Accounts
| Username | Full Name | OU Path | Group Membership | Purpose |
|----------|-----------|---------|-----------------|---------|
| adm-atorres | ADM - Alex Torres | Admin Accounts | Domain Admins | Full domain admin |
| adm-bnguyen | ADM - Brian Nguyen | Admin Accounts | Server Operators | Server management |
| adm-cpatel | ADM - Carlos Patel | Admin Accounts | Server Operators | Server management |
| adm-dkim | ADM - Diana Kim | Admin Accounts | Server Operators | Server management |

---

## Service Accounts
| Username | OU Path | Password Expires | Purpose |
|----------|---------|-----------------|---------|
| svc-backup | ServiceAccounts | Never | Backup operations (Veeam) |

---

## Account Policy (applied via Base Security GPO)
- Password minimum length: 12 characters
- Complexity required: Yes
- Max password age: 90 days
- Lockout threshold: 5 attempts
- Lockout duration: 30 minutes

---

## Naming Conventions
| Account type | Format | Example |
|-------------|--------|---------|
| Standard users | first initial + last name | atorres |
| Admin accounts | adm- + username | adm-atorres |
| Service accounts | svc- + function | svc-backup |
| Security groups | GRP- + department | GRP-IT |