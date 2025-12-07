# Lab 5 – AGDLP Security Groups

## Objective
Implement Microsoft's AGDLP permissions model using Global Groups (GG), Domain Local Groups (DL), and NTFS permissions to control access to shared departmental folders.

AGDLP = **Accounts → Global → Domain Local → Permissions**

---

## Step 1 — Create Department Folders
On **DC01**, create:

```
C:\Shares\HR
C:\Shares\IT
```

**Screenshot:**  
![01](screenshots/01_shares_folder_structure.png)

---

## Step 2 — Create Global Groups (G)
In **Company → Groups**, create these GLOBAL SECURITY groups:

- HR-GG  
- IT-GG  

**Screenshot:**  
![02](screenshots/02_global_groups_created.png)

---

## Step 3 — Create Domain Local Groups (DL)
In the same OU, create these DOMAIN LOCAL SECURITY groups:

**HR:**
- HR-DL-Read
- HR-DL-Modify

**IT:**
- IT-DL-Read
- IT-DL-Modify

**Screenshot:**  
![03](screenshots/03_domain_local_groups_created.png)

---

## Step 4 — Create Test Users (A = Accounts)
Create:

**HR user:** Amanda HR  
**IT user:** Ivan IT  

**Screenshots:**  
![04](screenshots/04_create_amanda_user.png)  
![05](screenshots/05_create_ivan_user.png)

---

## Step 5 — Add Users to Global Groups (A → G)
- Add *Amanda HR* → **HR-GG**  
- Add *Ivan IT* → **IT-GG**

**Screenshots:**  
![08](screenshots/08_hr_gg_amanda_member.png)  
![09](screenshots/09_it_gg_ivan_member.png)

---

## Step 6 — Nest Global Groups into Domain Local Groups (G → DL)

### HR
- HR-GG → HR-DL-Read  
- HR-GG → HR-DL-Modify  

### IT
- IT-GG → IT-DL-Read  
- IT-GG → IT-DL-Modify  

**Screenshots:**  
![10](screenshots/10_hr_dl_modify_contains_hr_gg.png)  
![10b](screenshots/10b_hr_dl_read_contains_hr_gg.png)  
![11](screenshots/11_it_dl_modify_contains_it_gg.png)  
![11b](screenshots/11b_it_dl_read_contains_it_gg.png)

---

## Step 7 — Configure NTFS Permissions (DL → P)

### HR Folder NTFS Permissions
- HR-DL-Modify → Modify  
- HR-DL-Read → Read  

**Screenshot:**  
![12](screenshots/12_hr_folder_ntfs_permissions.png)

---

### IT Folder NTFS Permissions
- IT-DL-Modify → Modify  
- IT-DL-Read → Read  

**Screenshot:**  
![13](screenshots/13_it_folder_ntfs_permissions.png)

---

## Step 8 — Share the `C:\Shares` Folder
Share name: **Shares**

Share permissions:
- Everyone → Full Control

**Screenshot:**  
![14](screenshots/14_shares_folder_shared.png)

---

## Step 9 — Test Access from Workstation01

### HR User: Amanda HR
Tests:
- Should be able to create/modify in **HR**
- Should be denied access to **IT**

**Screenshot:**  
![15](screenshots/15_amanda_hr_access_test.png)

---

### IT User: Ivan IT
Tests:
- Should be able to create/modify in **IT**
- Should be denied access to **HR**

**Screenshot:**  
![16](screenshots/16_ivan_hr_access_denied.png)

---

## Conclusion
This lab successfully demonstrates Microsoft’s AGDLP model:

**Accounts → Global Groups → Domain Local Groups → Permissions**

- Department access is controlled cleanly  
- No direct user assignments  
- Easily scalable for enterprise environments  
