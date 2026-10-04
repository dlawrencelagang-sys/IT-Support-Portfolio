# Action1 Patch Management Lab

## Objective
Set up Action1 in a home lab to practice patch management: installing agents, deploying agents automatically across a domain, reviewing vulnerabilities, and deploying missing updates.

## Environment
- Action1 (free tier)
- Windows Server 2022 domain controller (DL-DC-01, dltech.com)
- Windows 11 client (Desktop-01, logged in as Bruce Wayne)

## Setup

### 1. Manual agent install on the DC
Installed the Action1 agent directly on the domain controller.

![Install agent on DC](images/01-install-agent-dc.png)
![Agent installed on DC](images/02-agent-installed-dc.png)

### 2. Agent Deployer
Set up Action1 Deployer to automatically discover and install the agent on every computer in the domain, instead of installing it manually on each machine.

![Deployer setup](images/03-deployer-setup.png)
![Deployer installing](images/04-deployer-install-progress.png)
![Deployer connected](images/05-deployer-connected.png)
![Deployment scope settings](images/06-deployer-scope-settings.png)

### 3. Client auto-enrollment
Confirmed the Deployer worked by checking that the Windows 11 client picked up the agent automatically, without installing anything on it by hand.

![Client auto-enrolled](images/07-client-auto-enrolled.png)
![Both endpoints visible](images/08-both-endpoints-enrolled.png)

## Scenarios Practiced

### Vulnerabilities
Reviewed the vulnerabilities (CVEs) found on both endpoints.

![Vulnerabilities - client](images/09-vulnerabilities-client.png)
![Vulnerabilities - DC](images/10-vulnerabilities-dc.png)

### Missing updates - client
Checked which updates were missing on the client, selected the ones to install, and deployed them.

![Missing updates - client](images/11-missing-updates-client.png)
![Deploy settings - client](images/12-deploy-updates-settings-client.png)
![Deploy schedule - client](images/13-deploy-schedule-client.png)
![Downloading updates](images/17-downloading-both.png)
![Reboot confirmation](images/18-reboot-confirmation.png)

Confirmed the full cycle worked: missing updates found, selected, deployed, downloaded, and the machine rebooted automatically with a custom maintenance message.

### Missing updates - DC
Checked missing updates on the domain controller and deployed them the same way.

![Missing updates - DC](images/14-missing-updates-dc.png)
![Deploy settings - DC](images/15-deploy-updates-settings-dc.png)
![Deploy schedule - DC](images/16-deploy-schedule-dc.png)

## What I Learned
- How to install the Action1 agent both manually and automatically across a whole domain using the Deployer.
- How to find and review vulnerabilities on managed endpoints.
- How to find missing updates and deploy them, including setting reboot behavior and a custom message for end users.
