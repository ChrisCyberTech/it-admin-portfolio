# IT Admin Lab 4 – Departmental File Share & NTFS Permissions

This lab covers creating AD security groups, assigning users, building a shared folder structure on DC01, configuring NTFS + Share permissions, and validating access from WORKSTATION01.

---

## 1. Create Department Security Groups (DC01)

### 1.1 Create HR-SG  
![lab4-01-dc01-create-hr-sg](./screenshots/lab4-01-dc01-create-hr-sg.png)

### 1.2 Create Finance-SG  
![lab4-02-dc01-create-finance-sg](./screenshots/lab4-02-dc01-create-finance-sg.png)

### 1.3 Create IT-SG  
![lab4-03-dc01-create-it-sg](./screenshots/lab4-03-dc01-create-it-sg.png)

### 1.4 Create Public-SG  
![lab4-04-dc01-create-public-sg](./screenshots/lab4-04-dc01-create-public-sg.png)

---

## 2. Add Users to Their Department Groups (DC01)

### 2.1 Add HR user to HR-SG  
![lab4-05-dc01-hr-user-added-to-hr-sg](./screenshots/lab4-05-dc01-hr-user-added-to-hr-sg.png)

### 2.2 Add Finance user to Finance-SG  
![lab4-06-dc01-finance-user-added-to-finance-sg](./screenshots/lab4-06-dc01-finance-user-added-to-finance-sg.png)

### 2.3 Add IT user to IT-SG  
![lab4-07-dc01-it-user-added-to-it-sg](./screenshots/lab4-07-dc01-it-user-added-to-it-sg.png)

### 2.4 Add users to Public-SG  
![lab4-08-dc01-user-added-to-public-sg](./screenshots/lab4-08-dc01-user-added-to-public-sg.png)

---

## 3. Create Department Shared Folders (DC01)

### 3.1 Create the root `CompanyShares` folder  
![lab4-09-dc01-create-companyshares-folder](./screenshots/lab4-09-dc01-create-companyshares-folder.png)

### 3.2 Create subfolders: HR, Finance, IT, Public  
![lab4-10-dc01-companyshares-subfolders](./screenshots/lab4-10-dc01-companyshares-subfolders.png)

---

## 4. Configure NTFS Permissions (DC01)

> Goal: Each department folder grants Modify to its department security group, with Administrators and SYSTEM retaining Full Control.

### 4.1 HR folder NTFS permissions  
![lab4-11-dc01-hr-ntfs-permissions](./screenshots/lab4-11-dc01-hr-ntfs-permissions.png)

### 4.2 Finance folder NTFS permissions  
![lab4-12-dc01-finance-ntfs-permissions](./screenshots/lab4-12-dc01-finance-ntfs-permissions.png)

### 4.3 IT folder NTFS permissions  
![lab4-13-dc01-it-ntfs-permissions](./screenshots/lab4-13-dc01-it-ntfs-permissions.png)

### 4.4 Public folder NTFS permissions  
![lab4-14-dc01-public-ntfs-permissions](./screenshots/lab4-14-dc01-public-ntfs-permissions.png)

---

## 5. Configure Share Permissions (DC01)

> Goal: Share each folder with a hidden share name (ending in `$`) and appropriate access for each department group.

### 5.1 HR share permissions (HR$)  
![lab4-15-dc01-hr-share-permissions](./screenshots/lab4-15-dc01-hr-share-permissions.png)

### 5.2 Finance share permissions (Finance$)  
![lab4-16-dc01-finance-share-permissions](./screenshots/lab4-16-dc01-finance-share-permissions.png)

### 5.3 IT share permissions (IT$)  
![lab4-17-dc01-it-share-permissions](./screenshots/lab4-17-dc01-it-share-permissions.png)

### 5.4 Public share permissions (Public)  
![lab4-18-dc01-public-share-permissions](./screenshots/lab4-18-dc01-public-share-permissions.png)

---

## 6. Validate Access from WORKSTATION01

Log onto WORKSTATION01 with different domain users and test each UNC path to confirm that only the correct department can access its folder.

### 6.1 Finance user → `\\DC01\Finance$`  
![ita3-19-workstation01-finance-share-access](./screenshots/ita3-19-workstation01-finance-share-access.png)

### 6.2 HR user (Emily Perez) → `\\DC01\HR$`  
![ita3-20-workstation01-hr-share-access](./screenshots/ita3-20-workstation01-hr-share-access.png)

### 6.3 IT user → `\\DC01\IT$`  
![ita3-21-workstation01-it-share-access](./screenshots/ita3-21-workstation01-it-share-access.png)

### 6.4 HR user denied access to `\\DC01\Public`  
![ita3-22-workstation01-public-share-access-denied](./screenshots/ita3-22-workstation01-public-share-access-denied.png)

---

## 7. Summary

- Department security groups (HR-SG, Finance-SG, IT-SG, Public-SG) were created in Active Directory.
- Users were added to the correct groups based on their department.
- A central `C:\CompanyShares` structure was created with separate HR, Finance, IT, and Public folders.
- NTFS and Share permissions were configured so each department only has access to its own share.
- Access tests from WORKSTATION01 confirmed:
  - HR users can access `\\DC01\HR$`.
  - Finance users can access `\\DC01\Finance$`.
  - IT users can access `\\DC01\IT$`.
  - Access to Public from Emily (HR) is denied in this lab configuration, which matches the intended permissions.







