# Lab 1 – GPO Management & Deployment  
Help Desk / IT Admin Portfolio Lab

This lab demonstrates core Windows Server administration skills using Group Policy Objects (GPOs).  
It includes password policy configuration, desktop restrictions, login scripts, mapped drives, and security hardening settings.  
All GPOs were created and applied in a Windows Server Active Directory environment, then verified on a domain-joined workstation.

---

## **1. Password Policy GPO**

Created **GPO1 – Password Policy** and configured domain password requirements:

- Enforce password history: 10  
- Maximum password age: 30 days  
- Minimum password age: 1 day  
- Minimum password length: 12 characters  
- Password must meet complexity requirements: Enabled  
- Store passwords using reversible encryption: Disabled  

### **Screenshot**
![Password Policy Settings](./screenshots/Lab1-GPO-01_PasswordPolicySettings.png)

---

## **2. Desktop Restrictions GPO**

Created **GPO2 – Desktop Restrictions** to lock down user interface options.

### **Restrictions Applied**
- Hide Control Panel  
- Hide all desktop items  
- Prevent changing desktop background  
- Remove Run menu  
- Prevent changes to Taskbar and Start Menu  

### **Screenshots**
![Control Panel Restriction](./screenshots/Lab1-GPO-02_DesktopRestrictions_ControlPanel.png)

![Desktop Restrictions](./screenshots/Lab1-GPO-03_DesktopRestrictions_DesktopSettings.png)

![Extra Desktop Lockdown](./screenshots/Lab1-GPO-03b_DesktopRestrictions_ExtraDesktopLockdown.png)

![Start Menu Restrictions](./screenshots/Lab1-GPO-04_DesktopRestrictions_StartMenu.png)

---

## **3. Login Script GPO (Drive Mapping)**

Created **GPO3 – Login Script**, placed a batch file in SYSVOL, and configured it to run at logon.

### **Script**
net use H: \DC01\Share /persistent:yes

### **Screenshots**
![Login Script GPO](./screenshots/Lab1-GPO-05_LoginScript_GPO.png)

![Shared Folder Setup](./screenshots/Lab1-GPO-05a_SharedFolder.png)

![Login Script File](./screenshots/Lab1-GPO-05b_LoginScript_File.png)

---

## **4. Security Hardening GPO**

Created **GPO4 – Security Hardening** to apply recommended baseline configurations.

### **Account Policies**
![Guest Disabled](./screenshots/Lab1-GPO-06_SecurityHardening_GuestDisabled.png)

### **CTRL+ALT+DEL Requirement**
![Secure Logon](./screenshots/Lab1-GPO-07_SecurityHardening_CAD.png)

### **UAC Hardening**
![UAC Settings](./screenshots/Lab1-GPO-08_SecurityHardening_UAC.png)

### **SMB Hardening**
![SMB Hardening](./screenshots/Lab1-GPO-09_SecurityHardening_SMB.png)

### **Firewall Node Verification**
![Firewall Verification](./screenshots/Lab1-GPO-10_SecurityHardening_Firewall.png)

---

## **5. Verification on WORKSTATION01**

### **Policy Update**
![gpupdate /force](./screenshots/Lab1-GPO-11_gpupdateForce.png)

### **GPO Application Report**
![gpresult Report](./screenshots/Lab1-GPO-12_gpresultReport.png)

### **Drive Mapping Success**
![Drive Mapping Success](./screenshots/Lab1-GPO-13_DriveMapping_Success.png)

---

## **Conclusion**

This lab demonstrates the ability to:

- Create and manage GPOs  
- Configure password and security policies  
- Apply user interface restrictions  
- Deploy login scripts via SYSVOL  
- Map network drives automatically  
- Perform AD workstation hardening  
- Verify Group Policy application with gpupdate and gpresult  

These are core skills for Help Desk, IT Support, Junior SysAdmin, and SOC Analyst roles.

---