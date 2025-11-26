# Lab 6 – Shadow Copies & Restore (FS01)

A hands-on demonstration of how Windows Server uses **Shadow Copies** to restore deleted files from shared folders using the **Previous Versions** feature. This lab simulates a real-world help-desk scenario where a user accidentally deletes a file stored on a company file server.

---

# 📌 Table of Contents
- [Objective](#objective)
- [Lab Topology](#lab-topology)
- [Prerequisites](#prerequisites)
- [Step-by-Step Instructions](#step-by-step-instructions)
  - [Step 1 – Verify Folder Structure](#step-1--verify-folders)
  - [Step 2 – Enable Shadow Copies](#step-2--enable-shadow-copies)
  - [Step 3 – Create a Test File](#step-3--create-test-file)
  - [Step 4 – Delete the Test File](#step-4--delete-test-file)
  - [Step 5 – Restore Using Previous Versions](#step-5--restore-using-previous-versions)
  - [Step 6 – Verify Restoration](#step-6--verify-restoration)
- [Artifacts](#artifacts)
- [Folder Structure](#folder-structure)
- [Real-World Notes](#real-world-notes)
- [Summary](#summary)

---

# 📝 Objective
Demonstrate how to:

- Enable **Shadow Copies** on a Windows Server volume  
- Create and delete a file in a shared directory  
- Restore the deleted file using **Previous Versions**  
- Validate the restoration process  

This replicates how administrators restore files lost by end-users in enterprise environments.

---

# 🖥️ Lab Topology

| Role        | Hostname | OS                  |
|-------------|----------|---------------------|
| File Server | FS01     | Windows Server 2022 |

Only **FS01** is used for this lab.

---

# 📁 Prerequisites

The following folder structure must exist:

C:
└─ CompanyShares
├─ Finance
├─ HR
└─ IT

yaml
Copy code

---

# 🚀 Step-by-Step Instructions

---

## Step 1 – Verify Folder Structure <a name="step-1--verify-folders"></a>

1. On FS01, open **File Explorer**.
2. Navigate to:

C:\CompanyShares

markdown
Copy code

3. Confirm the subfolders **Finance**, **HR**, and **IT** exist.

📸 `FS01-01-companyshares-folders.png`  
```markdown
![FS01-01](screenshots/FS01-01-companyshares-folders.png)
Step 2 – Enable Shadow Copies <a name="step-2--enable-shadow-copies"></a>
Right-click Local Disk (C:) → Properties.

Select the Shadow Copies tab.

Choose *C:* and click Enable.

Configure:

Storage size

Snapshot schedule (optional)

📸 FS01-02-shadowcopies-enabled.png

markdown
Copy code
![FS01-02](screenshots/FS01-02-shadowcopies-enabled.png)
Step 3 – Create Test File <a name="step-3--create-test-file"></a>
Navigate to:

makefile
Copy code
C:\CompanyShares\IT
Right-click → New → Text Document.

Name the file:

nginx
Copy code
TestFile
📸 FS01-03-create-testfile.png

markdown
Copy code
![FS01-03](screenshots/FS01-03-create-testfile.png)
Step 4 – Delete Test File <a name="step-4--delete-test-file"></a>
Right-click TestFile → Delete.

Confirm the folder is empty.

📸 FS01-04-delete-testfile.png

markdown
Copy code
![FS01-04](screenshots/FS01-04-delete-testfile.png)
Step 5 – Restore Using Previous Versions <a name="step-5--restore-using-previous-versions"></a>
Navigate to:

makefile
Copy code
C:\CompanyShares
Right-click IT → Properties → Previous Versions.

Select a shadow copy from before the file was deleted.

Click Restore
or choose Open → manually copy back the file.

📸 FS01-05-previous-versions-window.png

markdown
Copy code
![FS01-05](screenshots/FS01-05-previous-versions-window.png)
📸 FS01-06-restore-confirmation.png

markdown
Copy code
![FS01-06](screenshots/FS01-06-restore-confirmation.png)
Step 6 – Verify Restoration <a name="step-6--verify-restoration"></a>
Return to:

makefile
Copy code
C:\CompanyShares\IT
Confirm TestFile has been successfully restored.

📸 FS01-07-restored-file-verification.png

markdown
Copy code
![FS01-07](screenshots/FS01-07-restored-file-verification.png)
📦 Artifacts
Restored file:
C:\CompanyShares\IT\TestFile

Screenshots included:

FS01-01-companyshares-folders.png

FS01-02-shadowcopies-enabled.png

FS01-03-create-testfile.png

FS01-04-delete-testfile.png

FS01-05-previous-versions-window.png

FS01-06-restore-confirmation.png

FS01-07-restored-file-verification.png
```
📁 Folder Structure
pgsql
Copy code
FS01-ShadowCopies/
│
├── README.md
│
├── screenshots/
│   ├── FS01-01-companyshares-folders.png
│   ├── FS01-02-shadowcopies-enabled.png
│   ├── FS01-03-create-testfile.png
│   ├── FS01-04-delete-testfile.png
│   ├── FS01-05-previous-versions-window.png
│   ├── FS01-06-restore-confirmation.png
│   └── FS01-07-restored-file-verification.png
│
└── artifacts/
    └── (optional restored file placeholder)
🧠 Real-World Notes
Shadow Copies should be enabled on data volumes (D:\Shares), not the OS drive.

They provide fast restore capability with almost no downtime.

Users can self-restore files depending on permissions:

Right-click → Restore previous versions

Shadow Copies store only changed blocks, minimizing storage usage.

They do not replace full server backups (Veeam, Commvault, Azure Backup, etc.).

✅ Summary
This lab demonstrated exactly how IT administrators restore deleted user files on a Windows file server.
Shadow Copies provide a fast and efficient safety net for shared folder environments, reducing help-desk load and improving data protection.

yaml
Copy code
