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
