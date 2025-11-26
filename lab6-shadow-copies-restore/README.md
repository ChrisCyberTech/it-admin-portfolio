# Lab 6 – Shadow Copies & Restore (FS01)

## Objective

Demonstrate how to use **Shadow Copies** on a Windows file server to restore a deleted file from a shared folder, using the **Previous Versions** feature.

---

## Lab Topology

- **DC01** – Domain Controller for `lab.local` (not directly used in this lab)
- **FS01** – Member file server hosting `C:\CompanyShares`

---

## Machines Used

| Role                | Hostname | OS                          |
|---------------------|----------|-----------------------------|
| Domain Controller   | DC01     | Windows Server 2025         |
| File Server         | FS01     | Windows Server 2022         |

Log on to **FS01** as:

- **Username:** `LAB\Administrator`  
- **Password:** (lab password)

---

## Prerequisites

- FS01 is joined to the `lab.local` domain.
- The folder structure already exists:

```text
C:\
 └─ CompanyShares
     ├─ Finance
     ├─ HR
     └─ IT
High-Level Steps
Review the existing shared folder structure on FS01.

Enable Shadow Copies on the C: volume and configure the schedule.

Create a test file in C:\CompanyShares\IT.

Delete the test file to simulate accidental deletion.

Use Previous Versions (Shadow Copies) to restore the IT folder.

Confirm the test file has been successfully restored.

Step-by-Step Instructions
Step 1 – Verify CompanyShares Folder Structure
On FS01, open File Explorer.

Browse to:

text
Copy code
C:\CompanyShares
Confirm you see the subfolders: Finance, HR, and IT.

📸 Screenshot:
FS01-01-companyshares-folders.png

markdown
Copy code
![FS01-01](screenshots/FS01-01-companyshares-folders.png)
Step 2 – Enable Shadow Copies on C:
In File Explorer, right-click Local Disk (C:) and select Properties.

Go to the Shadow Copies tab.

Select the C:\ volume.

Click Enable (or Settings if already enabled) and confirm the prompt.

Optionally:

Click Settings… to review / configure:

Maximum size for shadow copies.

Schedule for automatic snapshots.

Click OK or Close to return to the Shadow Copies tab.

📸 Screenshot:
FS01-02-shadowcopies-enabled.png

markdown
Copy code
![FS01-02](screenshots/FS01-02-shadowcopies-enabled.png)
Step 3 – Create a Test File in IT
In File Explorer on FS01, go to:

text
Copy code
C:\CompanyShares\IT
Right-click in the blank space → New → Text Document.

Name the file:

text
Copy code
TestFile
(Leave the contents empty for this lab.)

📸 Screenshot:
FS01-03-create-testfile.png

markdown
Copy code
![FS01-03](screenshots/FS01-03-create-testfile.png)
Important: The file must exist before the snapshot you will use for restoration.

Step 4 – Delete the Test File
In the same C:\CompanyShares\IT folder:

Right-click TestFile and choose Delete.

Confirm that the IT folder is now empty.

📸 Screenshot:
FS01-04-delete-testfile.png

markdown
Copy code
![FS01-04](screenshots/FS01-04-delete-testfile.png)
Step 5 – Use Previous Versions to Restore from Shadow Copies
In File Explorer, navigate back to:

text
Copy code
C:\CompanyShares
Right-click the IT folder and select Properties.

Go to the Previous Versions tab.

You should see one or more snapshots listed (created by Shadow Copies).

Select a version from a time before the file was deleted.

Click Restore… and confirm when prompted.

📸 Screenshot (Previous Versions list):
FS01-05-previous-versions-window.png

markdown
Copy code
![FS01-05](screenshots/FS01-05-previous-versions-window.png)
📸 Screenshot (Restore confirmation):
FS01-06-restore-confirmation.png

markdown
Copy code
![FS01-06](screenshots/FS01-06-restore-confirmation.png)
Note: In a production environment, admins often prefer Open → copy specific files instead of restoring an entire folder in place.

Step 6 – Verify the Restored File
After the restore completes, open the IT folder again:

text
Copy code
C:\CompanyShares\IT
Confirm that TestFile has reappeared.

📸 Screenshot:
FS01-07-restored-file-verification.png

markdown
Copy code
![FS01-07](screenshots/FS01-07-restored-file-verification.png)
Artifacts
Restored file:

text
Copy code
C:\CompanyShares\IT\TestFile
Screenshots:

FS01-01-companyshares-folders.png

FS01-02-shadowcopies-enabled.png

FS01-03-create-testfile.png

FS01-04-delete-testfile.png

FS01-05-previous-versions-window.png

FS01-06-restore-confirmation.png

FS01-07-restored-file-verification.png

Real-World Notes
Shadow Copies are typically enabled on data volumes (e.g., D:\Shares) instead of the OS drive.

Users can restore their own files via:

Right-click folder → Restore previous versions.

Shadow Copies are not a replacement for full backups, but they provide:

Fast restores for recently deleted/overwritten files.

Less help-desk load when users can self-service restores.