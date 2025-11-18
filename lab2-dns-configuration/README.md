# IT Admin Lab 2 — DNS Server Configuration

## Overview
In this lab, I configured Domain Name System (DNS) services on a Windows Server Domain Controller (DC01) and validated name resolution from a domain-joined workstation (Workstation01). The lab covered forward lookup zones, reverse lookup zones, host (A) records, CNAME records, PTR records, conditional forwarders, and DNS troubleshooting.

## Objectives
- Access DNS Manager and verify DNS functionality
- Create and verify A, CNAME, and PTR records
- Configure a reverse lookup zone
- Add a conditional forwarder
- Test DNS resolution from a Windows workstation
- Troubleshoot failed name resolution and validate repair

## Lab Topology

| Device | Role | Hostname | IP Address | OS |
|--------|------|-----------|------------|----|
| Domain Controller | AD DS + DNS | DC01 | 192.168.64.4 | Windows Server |
| Workstation | Domain Client | Workstation01 | 192.168.64.2 | Windows 11 |

Domain FQDN: lab.local

---

## Configuration Steps and Evidence

### Step 1 — Open DNS Manager
![Open DNS Manager](./screenshots/ita2-01-dc01-open-dns-manager.png)

### Step 2 — Forward Lookup Zones
![Forward Lookup Zones](./screenshots/ita2-02-dc01-forward-lookup-zones.png)

### Step 3 — DC01 A Record Properties
![DC01 A Record Properties](./screenshots/ita2-03-dc01-a-record-properties.png)

### Step 4 — Create A Record for Web01
![New A Record - web01](./screenshots/ita2-04-dc01-new-a-record-web01.png)

### Step 5 — Forward Zone Records
![Forward Zone Records](./screenshots/ita2-05-dc01-forward-zone-records.png)

### Step 6 — Create CNAME (www → web01)
![New CNAME Record](./screenshots/ita2-06-dc01-new-cname-www-web01.png)

### Step 7 — CNAME Record Listed
![CNAME Record List](./screenshots/ita2-07-dc01-cname-record-list.png)

### Step 8 — Create Reverse Lookup Zone
![Reverse Lookup Zone](./screenshots/ita2-08-dc01-new-reverse-lookup-zone.png)

### Step 9 — Create PTR Record
![New PTR Record](./screenshots/ita2-09-dc01-new-ptr-record-dc01.png)

### Step 10 — PTR Records Listed
![Reverse PTR Records](./screenshots/ita2-10-dc01-reverse-zone-ptr-records.png)

### Step 11 — Create Conditional Forwarder
![New Conditional Forwarder](./screenshots/ita2-11-dc01-new-conditional-forwarder-example.png)

### Step 12 — Conditional Forwarder Listing
![Conditional Forwarder List](./screenshots/ita2-12-dc01-conditional-forwarder-list.png)

---

## Client-Side Testing

### Step 13 — View DNS Configuration
![Workstation DNS Config](./screenshots/ita2-13-workstation01-ipconfig-all-dns.png)

### Step 14 — Initial DNS Lookup Tests (Issue Identified)
![Initial NSLookup Tests](./screenshots/ita2-14-workstation01-nslookup-tests.png)

### Step 15 — Final DNS Resolution Successful
![DNS Resolution Successful](./screenshots/ita2-15-workstation01-dns-resolution-success.png)

---

## Troubleshooting Summary

| Issue | Root Cause | Resolution |
|--------|------------|-------------|
| web01 failed to resolve | Corrupted/duplicate A + PTR record | Deleted record using dnscmd and recreated clean |
| DNS server name showed incorrectly | PTR conflict | Removed incorrect PTR entry |
| Inconsistent lookup results | Cached stale data | Flushed client and server cache |

Commands used:
ipconfig /flushdns
ipconfig /registerdns
dnscmd /recorddelete lab.local web01 A /f
Clear-DnsServerCache -Force

---

## What I Learned
- How forward and reverse lookup zones work together
- The relationship between A, CNAME, and PTR records
- How conditional forwarders are used for external DNS resolution
- nslookup as a diagnostic tool for DNS
- How cached DNS responses can cause misleading results
- How to correct DNS record corruption in AD-integrated zones

---

## Next Lab
IT Admin Lab 3 — Group Policy (GPO) Configuration and Deployment