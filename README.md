# 🛠️ IT Administrator Portfolio

Welcome to my **IT Administrator Portfolio** — a collection of hands-on Windows Server and enterprise infrastructure labs designed to build and demonstrate real-world **system administration** skills.

This repo focuses on the responsibilities typically handled by **Junior SysAdmins**, **IT Administrators**, and **Infrastructure Support Technicians**, including:

- Group Policy design  
- DNS and DHCP server administration  
- File server permissions (NTFS + Share)  
- AGDLP security models  
- Backups and shadow copies  
- Software deployment  
- Windows Server management and troubleshooting  

Each lab is documented using the same structured workflow as my Help Desk portfolio:  
**problem → technical steps → verification → evidence**.

---

## 📁 Labs | Road Map (In Progress)

| Lab # | Title | Description |
|------|--------|-------------|
| 1 | [GPO Management & Deployment](./lab1-gpo-management) | Create and apply Group Policy Objects for password policies, desktop settings, login scripts, and system hardening. |
| 2 | [DNS Server Configuration](./lab2-dns-configuration) | Configure host (A) records, CNAMEs, reverse lookup zones, conditional forwarders, and perform DNS troubleshooting. |
| 3 | [DHCP Server Setup](./lab3-dhcp-setup) | Configure DHCP scopes, reservations, exclusion ranges, and test client IP assignments. |
| 4 | [File Server Permissions (NTFS + Share)](./lab4-file-server-permissions) | Build a file server with proper NTFS permissions, share settings, and access verification steps. |
| 5 | [AGDLP Security Groups](./lab5-agdlp-security-groups) | Implement Microsoft's AGDLP permission model using global, domain local, and nested security groups. |
| 6 | [Shadow Copies & Restore](./lab6-shadow-copies-restore) | Enable shadow copies, delete test files, and perform user-driven file restoration. |
| 7 | [Backup & Recovery Basics](./lab7-backup-and-recovery) | Configure Windows Server backup, run incremental backups, and perform file/volume recovery. |
| 8 | [Software Deployment via GPO](./lab8-software-deployment-gpo) | Deploy MSI-based software packages across domain computers using Group Policy. |

---

## 🧠 Skills Demonstrated

- **Active Directory Administration**  
  - OUs, GPOs, security groups, login scripts  
  - AGDLP enterprise permission model  

- **Windows Server Roles**  
  - DNS (A/CNAME/Reverse, forwarders)  
  - DHCP (scopes, reservations, exclusions)  
  - File Services (NTFS/Share permissions)  
  - Volume Shadow Copies  
  - Windows Server Backup  

- **Enterprise Workflows**  
  - Change management documentation  
  - Role-based access control (RBAC)  
  - Software deployment lifecycle  
  - Access troubleshooting & verification  

- **Networking & Infrastructure**  
  - DNS resolution and testing  
  - DHCP lease assignment  
  - Firewall ports and service dependencies  

- **Tools & Scripting**  
  - PowerShell for server administration  
  - GPUpdate, GPResult, nslookup, ipconfig  
  - Server Manager & Administrative Tools  

---

## 🏗️ Server Environment Overview

All labs use a custom Windows Server environment built in UTM:

- **Windows Server 2025 Domain Controller**  
  - Active Directory Domain Services  
  - DNS + DHCP  
  - Group Policy Management  
  - File Server Resource Manager (FSRM) *(upcoming)*  

- **Windows 11 Client VMs**  
  - Domain-joined  
  - Used for testing GPO, permissions, and deployments  

This environment mirrors a **small business / enterprise starter infrastructure**, providing realistic system administration experience.

---

## 📚 IT Admin Learning Path

This repo is part of my long-term path toward becoming a **System Administrator**.

### Currently Studying:
- Windows Server administration  
- Network services (DNS, DHCP, SMB, LDAP)  
- Microsoft security model (GPO, AGDLP, RBAC)  

### Certifications:
- **CompTIA Network+** *(preparing)*  
- **CompTIA Security+** *(next goal)*  
- Future: **Microsoft Certified: Windows Server Hybrid Administrator Associate**

---

## 🧾 About

This portfolio builds on the foundation set by my:

- **UCLA Extension Cybersecurity Certificate**  
- **Help Desk Portfolio** (Windows support & troubleshooting)  
- **SOC Labs** (Sysmon, WEF, Splunk, event analysis)

The goal of this repository is to demonstrate **practical Windows Server administration**, using structured, evidence-driven documentation similar to real-world IT operations.

---

Created by **Luis Chris Mejia**  
**Repository:** https://github.com/ChrisCyberTech/it-admin-portfolio
