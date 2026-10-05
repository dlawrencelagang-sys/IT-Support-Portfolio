# Action1 Patch Management Lab

## Objective
Set up Action1 in a home lab to practice patch management: installing agents, deploying agents across a domain, viewing vulnerabilities (CVEs), and deploying missing updates with a controlled reboot.

## Environment
- Action1 (free tier)
- Windows Server 2022 domain controller (DL-DC-01, domain dltech.com)
- Windows 11 client (Desktop-01, user Bruce Wayne)

## Setup

### 1. Manual agent install on the DC
Downloaded the Windows agent (.MSI) from the Action1 console and installed it on the domain controller.

![Action1 console - Install Agent page](images/01-install-agent-dc.png)
![Agent setup wizard completed on the DC](images/02-agent-installed-dc.png)

### 2. Agent Deployer
Set up the Action1 Deployer, a service that queries Active Directory and automatically deploys the agent to domain computers, so agents don't have to be installed one machine at a time.

![Download and install Deployer step](images/03-deployer-setup.png)
![Deployer installer running on the DC with a domain service account](images/04-deployer-install-progress.png)
![Check Status - successfully connected to DL-DC-01.dltech.com](images/05-deployer-connected.png)
![Deployment Scope settings - all computers in dltech.com, DL-DC-01 excluded](images/06-deployer-scope-settings.png)

### 3. Client auto-enrollment
I did not install anything by hand on the Windows 11 client. Once the Deployer was running, Desktop-01 appeared in Action1 on its own and the Agent Deployment page showed 2 agents deployed.

![Agent Deployment status - Deployer running, 2 agents deployed](images/07-client-auto-enrolled.png)
![Endpoints list - Desktop-01 and DL-DC-01 both connected](images/08-both-endpoints-enrolled.png)

## Scenarios Practiced

### Vulnerability review
Viewed the vulnerabilities (CVEs) Action1 detected on each endpoint, along with the affected software and remediation status.

![Vulnerabilities - Desktop-01](images/09-vulnerabilities-client.png)
![Vulnerabilities - DL-DC-01](images/10-vulnerabilities-dc.png)

### Deploying updates - client (Desktop-01)
Reviewed the missing updates, selected them, configured the deployment, and scheduled it.

![Missing updates on Desktop-01 (8 selected)](images/11-missing-updates-client.png)
![Selected updates and reboot options](images/12-deploy-updates-select-client.png)
![Schedule - run now, 24-hour completion deadline](images/13-deploy-schedule-client.png)

Reboot options were set to reboot automatically only if required, with a custom message and a 2-minute timeout so logged-on users can save their work.

### Deploying updates - domain controller (DL-DC-01)
Repeated the process on the domain controller with its own set of missing updates.

![Missing updates on DL-DC-01 (4 selected)](images/14-missing-updates-dc.png)
![Selected updates and reboot options](images/15-deploy-updates-dc-settings.png)

### Monitoring the deployment
Tracked both deployments in Automation History while they ran, then confirmed the DC deployment finished. The DC then showed the custom reboot message to the logged-in user before restarting.

![Automation History - both deployments running](images/16-downloading-both.png)
![Automation History - DC deployment completed](images/17-deployment-completed.png)
![Reboot prompt with custom maintenance message on the DC](images/18-reboot-confirmation.png)

## What I Learned
- How to install the Action1 agent manually and how to use the Deployer Agent to roll it out automatically across a domain.
- How to view the vulnerabilities (CVEs) Action1 detects on each endpoint and see which software is affected.
- How to select missing updates, set reboot behavior with a custom user message, schedule the deployment, and monitor it in Automation History.
