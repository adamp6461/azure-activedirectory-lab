# Azure Active Directory Lab

## Overview

This project demonstrates the deployment and configuration of a Windows Server Active Directory environment hosted in Microsoft Azure. The lab includes virtual machine provisioning, Active Directory Domain Services (AD DS) installation, domain controller promotion, organizational unit creation, and Active Directory validation.

The objective was to simulate a foundational enterprise identity infrastructure using cloud-hosted resources and PowerShell administration.

---

## Technologies Used

- Microsoft Azure
- Windows Server 2022 Datacenter
- Active Directory Domain Services (AD DS)
- PowerShell
- Remote Desktop Protocol (RDP)

---

## Skills Demonstrated

- Azure Virtual Machine Deployment
- Windows Server Administration
- Active Directory Domain Services Installation
- Domain Controller Promotion
- Active Directory Verification
- PowerShell Administration
- Identity Infrastructure Management

---

## Lab Environment

| Component | Configuration |
|------------|---------------|
| Cloud Platform | Microsoft Azure |
| Operating System | Windows Server 2022 Datacenter |
| VM Size | Standard B2ts v2 |
| Domain Name | securitylab.local |
| Server Name | WinServer-01 |
| Management Method | PowerShell |

---

# Screenshots

## 1. Azure Virtual Machine Configuration

Created and configured a Windows Server 2022 virtual machine in Microsoft Azure. The VM was deployed using a free-tier eligible size and configured for Remote Desktop access.

**Screenshot:**

[Step 1 Screenshot]

---

## 2. Virtual Machine Deployment Verification

Validated successful deployment of the Azure virtual machine and confirmed resource creation within the Azure Portal.

# Screenshots

## 1. Azure Virtual Machine Configuration

Created and configured a Windows Server 2022 virtual machine in Microsoft Azure. The VM was deployed using a free-tier eligible size and configured for Remote Desktop access.

![Step 1 - Azure Virtual Machine Configuration](screenshots/Step-1.png)

---

## 2. Virtual Machine Deployment Verification

Validated successful deployment of the Azure virtual machine and confirmed resource creation within the Azure Portal.

![Step 2 - VM Deployment Verification](screenshots/Step-2.png)

---

## 3. Active Directory Domain Services Installation

Installed the Active Directory Domain Services (AD DS) role and promoted the server to a domain controller for the new forest.

```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName "securitylab.local"
```

![Step 3 - AD DS Installation](screenshots/Step-3.png)

---

## 4. Active Directory Validation

Verified successful domain controller promotion and Active Directory functionality using PowerShell.

```powershell
Get-ADForest
```

![Step 4 - Active Directory Validation](screenshots/Step-4.png)

---

## 5. Domain Controller Operational State

Confirmed the server was successfully operating as the domain controller for the newly created Active Directory forest.

![Step 5 - Domain Controller Operational State](screenshots/Step-5.png)
---

## Future Enhancements

- Create Organizational Units (OUs)
- Automate user provisioning via PowerShell
- Implement Group Policy Objects (GPOs)
- Deploy additional domain-joined client systems
- Configure DNS and DHCP services
- Expand into Azure Entra ID integration

---

## Author

**Adam Powell**

Apple Genius | CompTIA Security+ | Jamf 100 Certified

GitHub Repository:
https://github.com/adamp6461/azure-activedirectory-lab
