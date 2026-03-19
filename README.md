# Active-Directory-Azure-lab
Enterprise Active Directory lab built on Azure Cloud - Nexacore Technologies


# Active Directory Enterprise Lab — Azure Cloud
### NexaCore Technologies | nexacore.local

A fully functional enterprise-grade Active Directory environment 
built on Microsoft Azure, simulating a real-world corporate 
IT infrastructure for a managed services company.

---

## Project Overview

| Detail | Value |
|--------|-------|
| Company | NexaCore Technologies |
| Domain | nexacore.local |
| Location | Tampa, FL (simulated) |
| Cloud Platform | Microsoft Azure |
| DC OS | Windows Server 2022 Datacenter |
| Client OS | Windows 11 Pro |
| Total Users | 19 |
| Departments | 6 |

---

## Architecture

- **Azure Resource Group:** NexaCore-RG
- **Virtual Network:** NexaCore-VNet (10.0.0.0/16)
- **Subnet:** Corporate-Subnet (10.0.1.0/24)
- **Domain Controller:** DC-01 (10.0.1.10 — static)
- **Client VM:** CLIENT-01 (domain joined)
- **NSG:** RDP locked to admin IP only

---

## Organizational Structure
```
nexacore.local
└── NexaCore
    ├── IT          (4 users)
    ├── Finance     (3 users)
    ├── HR          (3 users)
    ├── Sales       (4 users)
    ├── Operations  (3 users)
    ├── Legal       (2 users)
    ├── Admin Accounts
    ├── ServiceAccounts
    └── Servers
```

---

## Key Configurations

### Active Directory
- Forest/Domain functional level: Windows Server 2016
- Full OU hierarchy with Users, Computers, Groups sub-OUs
- 19 domain user accounts across 6 departments
- 6 department security groups (GRP-IT, GRP-Finance, etc.)
- Separate admin accounts for IT staff (adm-username format)
- Service account for backup operations (svc-backup)

### Group Policy Objects
| GPO | Scope | Key Settings |
|-----|-------|--------------|
| NexaCore - Base Security Policy | Domain | Password complexity, lockout policy |
| NexaCore - IT Policy | IT OU | RDP access, elevated rights |
| NexaCore - Finance Policy | Finance OU | USB disabled, audit logging |
| NexaCore - HR Policy | HR OU | USB disabled, Control Panel restricted |
| NexaCore - Sales Policy | Sales OU | Screen lock, screensaver policy |
| NexaCore - Legal Policy | Legal OU | USB disabled, full audit trail |

### Security Hardening
- NSG rules restricting RDP to admin IP only
- Account lockout after 5 failed attempts
- Minimum 12-character password requirement
- Separate privileged admin accounts for IT staff
- Service accounts with non-expiring passwords isolated in dedicated OU

---

## Skills Demonstrated

- Azure Virtual Network and VM deployment
- Active Directory Domain Services installation and configuration
- DNS configuration for internal domain resolution
- OU design following enterprise best practices
- Group Policy design and implementation
- Security group management
- Role-based access control (RBAC) concepts
- Network Security Group configuration
- Domain join troubleshooting
- Windows Server 2022 administration

---

## Documentation

- [AD Build Runbook](docs/AD-Build-Runbook.md)
- [GPO Configuration Guide](docs/GPO-Configuration.md)
- [User Account Matrix](docs/User-Account-Matrix.md)
- [Troubleshooting Log](docs/Troubleshooting-Log.md)

---

## Screenshots

See the `/screenshots` folder for:
- Azure resource group and VNet configuration
- ADUC showing full OU hierarchy
- GPO links per department
- Successful domain join confirmation
- Domain user login on CLIENT-01
- gpresult output confirming GPO application
