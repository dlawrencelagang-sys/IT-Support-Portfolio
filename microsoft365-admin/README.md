# Microsoft 365 Admin Lab

## Objective
Set up and manage a Microsoft 365 tenant in a home lab, practicing the day-to-day admin tasks a helpdesk technician handles: user management, licensing, password resets, MFA, shared mailboxes, groups, and offboarding.

## Environment
- Tenant: Denns IT Lab (DennsITLab.onmicrosoft.com)
- Plan: Microsoft 365 Business Premium (trial)
- Note: Microsoft 365 doesn't use OUs like Active Directory. Users are organized by the Department field, and access/permissions are managed through Groups instead.

## Setup

### 1. Admin center dashboard
![Admin center dashboard](images/01-admin-dashboard.png)

### 2. Creating test users with departments
Created test users, each tagged with a Department field to mirror a real org structure: Bruce Wayne (IT), Tony Stark (IT), Patrick Jane (Sales), Theresa Lisbon (HR).

![Add a user form](images/02-add-user-form.png)
![Active users list](images/03-active-users-list.png)

### 3. Assigning a license
Assigned a Microsoft 365 Business Premium license to Tony Stark.

![License assigned](images/04-license-assigned.png)

## Scenarios Practiced

### Scenario 1: Password reset
- **Problem:** User forgot their password and can't sign in.
- **Resolution:** Reset the password from the admin center.

![Password reset dialog](images/05-password-reset-dialog.png)
![Password reset confirmation](images/06-password-reset-confirmation.png)

### Scenario 2: MFA re-registration
- **Problem:** User needs to set up MFA again (e.g., lost their phone or changed devices).
- **Resolution:** As admin, required Tony to re-register MFA, which cleared his existing methods. Then completed the re-registration flow as the user, setting up Microsoft Authenticator via QR code.

![Admin requires re-register MFA](images/07-mfa-admin-require-reregister.png)
![User prompted to secure account](images/08-mfa-user-secure-account.png)
![Install Microsoft Authenticator](images/09-mfa-install-authenticator.png)
![Scan the QR code](images/10-mfa-scan-qr.png)
![Approve sign-in with number match](images/11-mfa-approve-number.png)
![Authenticator added confirmation](images/12-mfa-authenticator-added.png)

### Scenario 3: Shared mailbox
- **Problem:** IT team needs a shared inbox to receive and respond to support requests.
- **Resolution:** Created a shared mailbox (IT Support) and added Tony as a member, then confirmed Tony could actually access it from Outlook.

![Shared mailbox creation form](images/13-sharedmailbox-create-form.png)
![Shared mailbox created](images/14-sharedmailbox-created.png)
![Adding members to the mailbox](images/15-sharedmailbox-add-members.png)
![Shared mailbox members list](images/16-sharedmailbox-members-list.png)
![Tony opens the shared mailbox](images/sharedmailbox-tony-opens.png)
![Viewing the shared mailbox inbox](images/sharedmailbox-inbox-view.png)

### Scenario 4: Group management
- **Problem:** Each department needs its own group for access and communication.
- **Resolution:** Created a Team/Microsoft 365 group per department: IT-Staff (Bruce, Tony), HR-Staff (Theresa), Sales-Staff (Patrick). All set to Private.

![IT-Staff review](images/17-itstaff-review.png)
![HR-Staff review](images/18-hrstaff-review.png)
![Sales-Staff review](images/19-salesstaff-review.png)
![Active teams and groups list](images/20-active-groups-list.png)

### Scenario 5: License management
- **Problem:** Need to investigate and resolve a user's access issue tied to licensing.
- **Resolution:** Removed Tony's license to observe the effect, confirmed he lost mailbox access, then reassigned the license to restore it.

![License removed](images/21-license-removed.png)
![Outlook error with no license](images/22-outlook-error-no-license.png)
![License reassigned](images/23-license-reassigned.png)

With the license removed, Tony got an error in Outlook and could no longer open his mailbox, which shows how a missing license shows up as an access problem for the user.

### Scenario 6: Offboarding
- **Problem:** Employee needs their account access revoked.
- **Resolution:** Blocked Tony's sign-in and confirmed he could no longer log in.

![Block sign-in toggle](images/24-block-signin-toggle.png)
![Block sign-in confirmation](images/25-block-signin-confirmation.png)
![Failed login after block](images/26-failed-login-blocked.png)

## What I Learned
- Microsoft 365 organizes users by Department and Groups instead of OUs like Active Directory.
- How to reset a user's password from the admin center.
- The full MFA re-registration flow, from both the admin side and the end-user side.
- How to create a shared mailbox, add members to it, and confirm they can open it in Outlook.
- How to create private Teams/Microsoft 365 groups for each department.
- How licenses control access to Microsoft 365 services: removing Tony's license caused an Outlook error until the license was reassigned.
- How blocking sign-in stops a user from logging in without deleting their account.
