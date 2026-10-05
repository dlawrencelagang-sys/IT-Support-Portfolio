# Active Directory Home Lab

## Objective
Set up a working Active Directory domain in a home lab and practice the day-to-day tasks a helpdesk technician handles: user management, password resets, account unlocks, onboarding/offboarding, shared folder permissions, and Group Policy.

## Environment
- Host: Oracle VirtualBox
- Domain Controller: Windows Server 2022 (DL-DC-01)
- Client: Windows 11
- Domain name: dltech.com

## Setup

### 1. Server VM
![VM settings](images/01-vm-settings.png)

### 2. Static IP configuration
![Static IP](images/02-static-ip.png)

### 3. Installing the Active Directory Domain Services role
![AD DS role install](images/03-adds-install.png)

### 4. Promoting the server to a domain controller
Created a new forest with the root domain dltech.com.
![Domain controller promotion](images/04-dc-promotion.png)

### 5. Creating OUs, users, and a security group
Created OUs for IT, HR, and Sales, added test users, and created a security group (IT-Staff) inside the IT OU.
![OU structure](images/05-ou-structure.png)
![IT-Staff group members](images/06-itstaff-members.png)

### 6. Preparing and joining the client to the domain
Pointed the client's DNS to the domain controller's IP, then joined the client to dltech.com.
![Client DNS setting](images/07-client-dns.png)
![Joining the domain](images/08-domain-join.png)
![Domain join confirmation](images/09-domain-join-success.png)

## Scenarios Practiced

### Scenario 1: Password reset
- **Problem:** User forgot their password and can't log in.
- **Troubleshooting:** Located the user in Active Directory Users and Computers.
- **Resolution:** Reset the password and required a change at next logon.

![Password reset](images/10-password-reset.png)
![Login prompt for new password](images/11-new-password-prompt.png)

### Scenario 2: Account unlock
- **Problem:** User (Bruce Wayne) locked out after multiple failed login attempts.
- **Troubleshooting:** Checked the account status in ADUC and confirmed it was locked.
- **Resolution:** Unlocked the account.

![Locked account](images/12-locked-account.png)
![Unlock account](images/13-unlock-account.png)
![Successful login after unlock](images/14-login-after-unlock.png)

### Scenario 3: New hire setup
- **Problem:** New employee (Theresa Lisbon) needs an account and access to HR resources.
- **Resolution:** Created the user in the HR OU and added her to the HR-Staff security group.

![New user creation](images/15-new-user.png)
![Added to HR-Staff group](images/16-hrstaff-members.png)

### Scenario 4: Offboarding
- **Problem:** Employee (Bruce Wayne) has left the company and needs access removed.
- **Resolution:** Disabled the account and moved it to a dedicated Disabled Users OU.

![Account moved to Disabled Users OU](images/17-disabled-ou.png)
![Failed login attempt](images/18-disabled-login-fail.png)

### Scenario 5: Shared folder permissions
- **Problem:** Each department needs a shared folder that only their team can access.
- **Resolution:** Created a shared "DL-Tech Folder" with department subfolders, granted access to each OU's security group, and mapped it as a network drive on the client.

![Folder permissions](images/19-folder-permissions.png)
![Mapped drive - access granted](images/20-mapped-drive-access.png)

### Scenario 6: Group Policy - Desktop wallpaper
- **Goal:** Push a standard desktop wallpaper to domain clients using Group Policy.
- **Resolution:** Created a GPO with the wallpaper setting and linked it to the domain/OU, then confirmed it applied on the client.

![GPO wallpaper setting](images/21-gpo-wallpaper-editor.png)
![Wallpaper applied on client](images/22-gpo-wallpaper-result.png)

## What I Learned
- How OUs and security groups serve different purposes: OUs organize and apply policy, groups control access.
- The day-to-day tasks a helpdesk technician handles in Active Directory: password resets, unlocks, onboarding, and offboarding.
- How DNS has to be configured correctly on a client before it can find and join a domain.
- How Group Policy pushes settings to clients without touching each machine manually.
