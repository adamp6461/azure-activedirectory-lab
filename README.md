# Active Directory Lab - Azure Domain Controller Deployment

## Overview

This project demonstrates the deployment and administration of a Windows Server Active Directory environment hosted in Microsoft Azure. The lab was designed to simulate enterprise identity management operations while reinforcing Active Directory, PowerShell automation, and cloud infrastructure administration skills.

The environment was deployed using Windows Server Datacenter (Server Core) and configured primarily through PowerShell to reduce reliance on graphical administration tools.

---

## Business Scenario

AP Technology Group, a simulated 250-user organization, required a centralized identity management platform to support user authentication, administrative delegation, and future policy enforcement.

This lab deployed a cloud-hosted Active Directory environment to provide a scalable foundation for user lifecycle management and enterprise systems administration.

---

## Environment

### Cloud Platform

* Microsoft Azure
* Azure Virtual Machine Infrastructure

### Server

* Windows Server Datacenter (Server Core)
* Forest Root Domain Controller

### Domain

```text
securitylab.local
```

---

## Project Objectives

* Deploy a Windows Server instance in Microsoft Azure
* Configure a secure server baseline using PowerShell
* Install Active Directory Domain Services (AD DS)
* Promote a server to a Domain Controller
* Create and manage Organizational Units (OUs)
* Automate user provisioning through PowerShell
* Develop foundational enterprise identity management skills

---

## Technologies Used

* Microsoft Azure
* Windows Server Datacenter (Server Core)
* Active Directory Domain Services (AD DS)
* PowerShell
* Windows Firewall
* DNS
* Azure Virtual Machines
* Organizational Units (OUs)

---

## Implementation

### Server Provisioning

A Windows Server Datacenter virtual machine was deployed within Microsoft Azure using a lightweight Server Core image to minimize resource consumption and reduce attack surface.

### PowerShell Administration

Administrative tasks were performed through PowerShell, including:

* Server renaming
* Network configuration
* Firewall management
* Feature installation
* Active Directory deployment

### Active Directory Deployment

The Active Directory Domain Services role was installed and configured. The server was promoted to a Forest Root Domain Controller for the following domain:

```text
securitylab.local
```

### Organizational Unit Structure

The following Organizational Units were created to simulate an enterprise environment:

```text
SecurityLab.local
│
├── Information Technology
├── Human Resources
├── Finance
├── Sales
├── Marketing
└── Workstations
```

### User Provisioning Automation

PowerShell scripting was used to automate user creation and account activation.

Tasks included:

* User object creation
* Password assignment
* Account enablement
* OU placement
* Batch provisioning through looping structures

---

## PowerShell Examples

### Rename Server

```powershell
Rename-Computer -NewName "DC01" -Restart
```

### Install Active Directory Domain Services

```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```

### Promote Server to Domain Controller

```powershell
Install-ADDSForest `
-DomainName "securitylab.local" `
-InstallDNS `
-Force
```

---

## Skills Demonstrated

* Active Directory Administration
* Microsoft Azure Infrastructure
* Windows Server Management
* PowerShell Automation
* Identity and Access Management (IAM)
* Organizational Unit Design
* User Lifecycle Management
* Infrastructure Deployment
* Systems Administration

---

## Screenshots

### Azure Virtual Machine Deployment

*Coming Soon*

### Active Directory Domain Services Installation

*Coming Soon*

### Organizational Unit Structure

*Coming Soon*

### User Provisioning Automation

*Coming Soon*

---

## Key Takeaways

This lab provided hands-on experience deploying and administering a cloud-hosted Active Directory environment. By leveraging Server Core and PowerShell automation, the project reinforced infrastructure-as-code concepts, administrative scripting, and enterprise identity management practices commonly used in modern IT environments.

---

## Future Enhancements

* Group Policy Object (GPO) Management
* Security Group Administration
* Domain-Joined Client Workstations
* Password Policy Enforcement
* Remote Administration Tools
* PowerShell User Lifecycle Automation
* Active Directory Auditing and Monitoring
