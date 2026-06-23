# Public Cloud Enterprise Lab: Automated Windows Server Core, Active Directory, & Identity Management Pipeline

## Project Overview
This repository documents the end-to-end architectural deployment of an enterprise-grade **Windows Server 2022 Datacenter (Server Core)** infrastructure inside **Microsoft Azure**. 

To maximize operational efficiency, reduce the attack surface, and emulate modern DevOps/SysAdmin data center practices, the entire infrastructure was provisioned and configured **exclusively via the command line (PowerShell & SConfig)**, completely bypassing standard graphical user interfaces (GUIs). 

Additionally, this lab demonstrates automated identity lifecycle management by leveraging programmatic scripting pipelines to stand up a brand-new directory forest and batch-provision enterprise user objects.

---

## Technical Competencies Demonstrated
* **Cloud Infrastructure as a Service (IaaS):** Provisioned resilient cloud compute instances, managed trial resource allocation, and configured explicit Network Security Group (NSG) firewall rules.
* **Systems Optimization (Server Core):** Implemented a specialized `[smalldisk]` Server Core footprint, optimizing storage boundaries down to 64 GB and running a live enterprise directory database on minimal hardware metrics (1 GB RAM / 2 vCPUs).
* **Command-Line & Shell Administration:** Conducted 100% of host renaming, operating system configurations, and directory service operations using terminal environments.
* **Directory Services Architecture:** Engineered a secure, isolated Active Directory Forest root infrastructure from the ground up, initializing database schema, schema enforcement, and integrated DNS zones.
* **Identity & Access Management (IAM) Automation:** Designed and executed a robust configuration loop utilizing structured PowerShell objects to safely automate enterprise user provisioning pipelines.

---

## Deep-Dive Deployment Documentation

### Phase 1: Cloud Infrastructure Provisioning (Azure IaaS)
1. Navigated the **Microsoft Azure** portal to provision a clean compute instance using resource-optimized parameters.
2. Formulated and deployed a Virtual Machine utilizing the following specifications:
    * **Virtual Machine Name:** `WinServer-Core-01`
    * **Hardware Tier:** `Standard_B2ats_v2` (2 vCPUs, 1 GB RAM — Free Services Eligible)
    * **Operating System Image:** `[smalldisk] Windows Server 2022 Datacenter: Azure Edition Core - x64 Gen2`
    * **Firewall / Network Security Group:** Locked down access parameters to the instance via explicit **RDP (Port 3389)** inbound binding for secure remote administration.

### Phase 2: Host Standardization & NetBIOS Refactoring (SConfig)
Upon establishing a secure remote terminal session via Microsoft Remote Desktop from macOS, the default `SConfig` (Server Configuration) text engine was utilized to standardize the base operating system before deployment:
1. Executed option `2` (Computer Name transformation).
2. Converted the volatile, randomized Azure host string to a structured corporate scheme: `WinServer-01`.
3. Initiated a programmatic system reboot to clear the NetBIOS naming cache and apply architectural shifts.

### Phase 3: Active Directory Domain Services (AD DS) Automation
Following the system restart, the server was accessed via native PowerShell to build out the directory backbone of the organization.

#### 1. Binary Feature Package Extraction
Executed the following cmdlet to query Microsoft Update repositories, downloading and extracting all core Active Directory binaries and corresponding deployment automation tools:
```powershell
Install-WindowsFeature -Name AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName "securitylab.local"
New-ADOrganizationalUnit -Name "Staff" -Path "DC=securitylab,DC=local"
# Define target enterprise user identities using custom object arrays
$Users = @(
    [PSCustomObject]@{FirstName="John"; LastName="Doe"; Username="jdoe"},
    [PSCustomObject]@{FirstName="Jane"; LastName="Smith"; Username="jsmith"}
)

# Enforce secure baseline default credentials
$SecurePassword = ConvertTo-SecureString "InitialP@ss2026!" -AsPlainText -Force

# Execute logical configuration loop to provision and inject accounts into the directory database
foreach ($User in $Users) {
    New-ADUser -Name "$($User.FirstName) $($User.LastName)" `
               -GivenName $User.FirstName `
               -Surname $User.LastName `
               -SamAccountName $User.Username `
               -UserPrincipalName "$($User.Username)@securitylab.local" `
               -Path "OU=Staff,DC=securitylab,DC=local" `
               -AccountPassword $SecurePassword `
               -ChangePasswordAtLogon $true `
               -Enabled $true
}
Get-ADUser -Filter * -SearchBase "OU=Staff,DC=securitylab,DC=local" | Select-Object Name, SamAccountName, Enabled

