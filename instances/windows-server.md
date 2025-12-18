---
icon: windows
---

# Windows Server

The Windows Server in the Learnova platform functions as the **centralized user and policy management server**. It is responsible for domain control, user authentication, Group Policy enforcement, and client integration within the Learnova educational environment.

### Network Configuration

The Windows Server has been configured with a **static IP address** to ensure stability and consistent domain services.

* IP Address: _192.168.16.3_
* DNS Server: _127.0.0.1_
* Network Mode: Internal / LAN

Client machines obtain their IP addresses automatically via **DHCP from the router**, allowing seamless network connectivity without manual IP configuration on each client device.

### Active Directory Domain Services (AD DS)

#### Forest and Domain Setup

The Active Directory Domain Services role has been installed and configured with the following domain structure:

* **Forest Name:** `gpo.learnova.edu`
* **Domain Type:** Single forest, single domain
* **Domain Controller:** Windows Server (Primary DC)

This configuration allows centralized identity management and Group Policy enforcement across all Learnova clients.

### Organizational Units (OU) Structure

To separate policy management and administrative control, two main Organizational Units (OU) were created:

| OU Name          | Description                    |
| ---------------- | ------------------------------ |
| Learnova Staff   | Contains staff user accounts   |
| Learnova Student | Contains student user accounts |

### User Account

Domain user accounts that  have been created:

| Username | Role    | OU Placement     |
| -------- | ------- | ---------------- |
| catur    | Staff   | Learnova Staff   |
| amelia   | Student | Learnova Student |

### Group Policy Object (GPO) Configuration

Group Policy Objects (GPO) have been configured and linked to the respective Organizational Units to enforce different rules and restrictions based on user roles.

* GPOs are linked at the **OU level**
* Policies are applied automatically when users log in to domain-joined client machines
* Staff and students receive **different policy sets**

### GPO Application Table

<table><thead><tr><th width="244.57421875">OU</th><th>GPO Name</th></tr></thead><tbody><tr><td>Student and Staff</td><td>Disable Control Panel &#x26; Settings</td></tr><tr><td>Student and Staff</td><td>Disable Command Prompt</td></tr><tr><td>Student and Staff</td><td>Disable Regedit</td></tr><tr><td>Student and Staff</td><td>Auto Lock / Auto Logoff After Idle</td></tr><tr><td>Student and Staff</td><td>Disable Powershell</td></tr><tr><td>Student</td><td>Disable USB Storage</td></tr><tr><td>Student</td><td>Disable Software Installation</td></tr><tr><td>Student</td><td>Create Student Folder in C:\</td></tr><tr><td>Staff</td><td>Create Staff Folder in C:\</td></tr></tbody></table>

### Client Configuration

Client computers are configured as follows:

* IP Addressing: **Automatic (DHCP from Router)**
* DNS Resolution: Provided by Windows Server (Domain Controller)
* Domain Join: Clients are joined to `gpo.learnova.edu`

This setup allows clients to automatically receive IP addresses and domain policies without manual network configuration.
