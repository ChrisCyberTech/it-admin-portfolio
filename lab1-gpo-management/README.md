# Lab 1 – GPO Management & Deployment  
Help Desk / IT Admin Portfolio Lab

This lab demonstrates core Windows Server administration skills using Group Policy Objects (GPOs).  
It includes password policy configuration, desktop restrictions, login scripts, mapped drives, and security hardening settings.  
All GPOs were created and applied in a Windows Server Active Directory environment, then verified on a domain-joined workstation.

All screenshots are stored in the **screenshots** folder.

---

## **1. Password Policy GPO**

Created **GPO1 – Password Policy** and configured domain password requirements:

- Enforce password history: 10  
- Maximum password age: 30 days  
- Minimum password age: 1 day  
- Minimum password length: 12 characters  
- Password must meet complexity requirements: Enabled  
- Store passwords using reversible encryption: Disabled  

**Screenshot:**  
./screenshots/Lab1-GPO-01_PasswordPolicySettings.png

---

## **2. Desktop Restrictions GPO**

Created **GPO2 – Desktop Restrictions** under *User Configuration* to lock down workstation UI.

### Restrictions applied:
- Hide Control Panel  
- Hide all desktop items  
- Prevent changing desktop background  
- Remove Run menu from Start Menu  
- Prevent changes to Taskbar and Start Menu settings

**Screenshots:**  
`./screenshots/Lab1-GPO-02_DesktopRestrictions_ControlPanel.png`  
`./screenshots/Lab1-GPO-03_DesktopRestrictions_DesktopSettings.png`  
`./screenshots/Lab1-GPO-03b_DesktopRestrictions_ExtraDesktopLockdown.png`  
`./screenshots/Lab1-GPO-04_DesktopRestrictions_StartMenu.png`

---

## **3. Login Script GPO (Drive Mapping)**

Created **GPO3 – Login Script**, stored a batch file inside SYSVOL, and configured it to run at user logon.

### Script file:
net use H: \DC01\Share /persistent:yes

### Locations:
- Script stored in: `\\lab.local\SysVol\lab.local\scripts\logon`
- Share path: `\\DC01\Share`

**Screenshots:**  
`./screenshots/Lab1-GPO-05_LoginScript_GPO.png`  
`./screenshots/Lab1-GPO-05a_SharedFolder.png`  
`./screenshots/Lab1-GPO-05b_LoginScript_File.png`

---

## **4. Security Hardening GPO**

Created **GPO4 – Security Hardening** to apply common AD hardening settings.

### Hardening settings applied:

#### **Account Policies**
- Guest account: Disabled

**Screenshot:**  
`./screenshots/Lab1-GPO-06_SecurityHardening_GuestDisabled.png`

#### **Interactive Logon**
- Require CTRL+ALT+DEL: Enabled  
  (Policy: *Interactive logon: Do not require CTRL+ALT+DEL* → Disabled)

**Screenshot:**  
`./screenshots/Lab1-GPO-07_SecurityHardening_CAD.png`

#### **User Account Control (UAC)**
- Run all administrators in Admin Approval Mode: Enabled  
- Elevation prompt behavior for administrators: Prompt for consent  

**Screenshot:**  
`./screenshots/Lab1-GPO-08_SecurityHardening_UAC.png`

#### **SMB / Network Hardening**
- Disable insecure guest logons: Disabled

**Screenshot:**  
`./screenshots/Lab1-GPO-09_SecurityHardening_SMB.png`

#### **Firewall Node Verification**
(Newer Server builds only show the *Advanced Security* console)

**Screenshot:**  
`./screenshots/Lab1-GPO-10_SecurityHardening_Firewall.png`

---

## **5. Verification on WORKSTATION01**

### Applied all policies manually:
gpupdate /force

**Screenshot:**  
`./screenshots/Lab1-GPO-11_gpupdateForce.png`

### Verified applied GPOs:
gpresult /r

Confirmed the following GPOs applied:
- GPO1 – Password Policy  
- GPO2 – Desktop Restrictions  
- GPO3 – Login Script  
- GPO4 – Security Hardening  

**Screenshot:**  
`./screenshots/Lab1-GPO-12_gpresultReport.png`

### Confirmed H: Drive Mapping  
Login script successfully mapped:

H: → \DC01\Share

**Screenshot:**  
`./screenshots/Lab1-GPO-13_DriveMapping_Success.png`

---

## **Conclusion**

This lab demonstrates the ability to:

- Create and manage GPOs  
- Configure password and security policies  
- Apply user interface restrictions  
- Deploy login scripts via SYSVOL  
- Map network drives automatically  
- Perform AD-based workstation hardening  
- Verify Group Policy application with gpupdate and gpresult  

These are core skills required for Help Desk, IT Support, Junior SysAdmin, and SOC Analyst roles.  
Lab completed on a Windows Server domain environment with a domain-joined Windows 11 workstation.

---