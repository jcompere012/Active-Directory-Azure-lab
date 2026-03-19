# AD Build Runbook — NexaCore Technologies
**Domain:** nexacore.local  
**DC:** DC-01 | 10.0.1.10  
**Built by:** J. Compere  
**Date:** March 2026

---

## Phase 1 — Azure Infrastructure

### Resource Group
- Name: NexaCore-RG
- Region: East US 2

### Virtual Network
- Name: NexaCore-VNet
- Address space: 10.0.0.0/16
- Subnet: Corporate-Subnet (10.0.1.0/24)

### DC-01 Virtual Machine
- OS: Windows Server 2022 Datacenter
- Size: Standard_B2s
- Private IP: 10.0.1.10 (static)
- NSG: RDP inbound restricted to admin IP

### Client-01 Virtual Machine
- OS: Windows 11 Pro
- Size: Standard_B2s
- DNS pointed to: 10.0.1.10
- Domain joined via: netdom command

---

## Phase 2 — AD DS Installation

1. Installed AD DS and DNS roles via Server Manager
2. Promoted DC-01 to domain controller
3. Created new forest: nexacore.local
4. NetBIOS name: NEXACORE
5. Forest/Domain functional level: Windows Server 2016
6. DSRM password configured and stored securely

---

## Phase 3 — OU Structure

Created the following hierarchy in ADUC:

nexacore.local
└── NexaCore
    ├── IT (Users, Computers, Groups)
    ├── Finance (Users, Computers, Groups)
    ├── HR (Users, Computers, Groups)
    ├── Sales (Users, Computers, Groups)
    ├── Operations (Users, Computers, Groups)
    ├── Legal (Users, Computers, Groups)
    ├── Admin Accounts
    ├── ServiceAccounts
    └── Servers

---

## Phase 4 — Domain Join

- Verified DNS resolution: nslookup nexacore.local → 10.0.1.10
- Tested port connectivity: 88, 135, 389, 445 all open
- Domain joined CLIENT-01 using netdom command
- Moved computer object to NexaCore → IT → Computers OU

### Issue encountered
Windows 11 GUI credential dialog failed with error 0x2407
even with correct credentials and Domain Admin account.

### Resolution
Used netdom join command via elevated Command Prompt:
netdom join CLIENT-01 /domain:nexacore.local 
/userd:Administrator /passwordd:*

---

## Phase 5 — GPO Configuration

- Created 7 GPOs total
- Base Security Policy linked at domain root
- Department policies linked to respective OUs
- Verified application via gpresult /r on CLIENT-01

---

## Notes
- Always use adm-username accounts for admin tasks
- svc-backup account has non-expiring password
- Default Administrator password stored in secure vault