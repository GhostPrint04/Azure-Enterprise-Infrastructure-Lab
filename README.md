# Azure Enterprise Infrastructure Lab
Internal documentation for the deployment, configuration, and troubleshooting of a cloudbased Windows and Linux infrastructure hosted on Microsoft Azure. Covers VM provisioning, virtual networking, remote access, and network traffic validation.

![Microsoft Azure](https://img.shields.io/badge/Microsoft_Azure-0089D6?style=for-the-badge&logo=microsoft-azure&logoColor=white)
![Windows Server](https://img.shields.io/badge/Windows_Server-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

<img src="https://upload.wikimedia.org/wikipedia/commons/f/fa/Microsoft_Azure.svg" width="90" align="center"/>

Internal documentation for the deployment...

## Environment Summary

Deployed and managed a mixed Windows and Linux environment on Microsoft Azure, supporting remote access, network connectivity, and endpoint configuration across both platforms. Diagnosed and resolved infrastructure issues including DHCP lease conflicts, RDP session failures and network access control problems, identifying root causes through live packet analysis with Wireshark and implementing fixes via PowerShell automation. Documented all procedures and findings to support repeatable troubleshooting workflows.

| Component | Details |
|----------|---------|
| Platform | Microsoft Azure |
| Resource | Group RG-Network-Lab |
| Windows | VM window-vm — Windows 11 — IP: 10.0.0.5 |
| Linux | VM linux-vm — Ubuntu Server 22.04 LTS — IP: 10.0.0.4 |
| Network | Shared Virtual Network with NSG-controlled subnets |

## Technologies Used

| Category | Technologies |
|-----------|-------------|
| Cloud Infrastructure | [Microsoft Azure](https://azure.microsoft.com), Azure Resource Groups, Virtual Machines, Virtual Networks |
| Operating Systems | Windows Server, Windows 11, Ubuntu Linux |
| Networking | [TCP/IP](https://learn.microsoft.com), [DNS](https://learn.microsoft.com), [DHCP](https://learn.microsoft.com), NSGs |
| Remote Access | [RDP](https://learn.microsoft.com), [SSH](https://www.openssh.com) |
| Administration & Troubleshooting | [PowerShell](https://learn.microsoft.com/powershell), [Wireshark](https://www.wireshark.org) |


| Key Activities |
|----------------|
| Diagnosed and resolved RDP session failures caused by DHCP lease conflicts — traced root cause to TCP RST packets via Wireshark and restored connectivity through PowerShell automation |
| Enforced network access controls by configuring NSG inbound deny rules, blocking ICMPv4 traffic and validating rule priority enforcement at the subnet level |
| Established and validated SSH connectivity from Windows to Ubuntu — confirmed SSHv2 encryption with no plaintext credentials exposed in packet capture |
| Captured and analyzed live network traffic across ICMP, DHCP, DNS, TCP, and RDP protocols using Wireshark during active infrastructure changes | 
| Developed and deployed dhcp.bat automation script to streamline DHCP release and renewal diagnostics on Windows endpoints |
| Documented troubleshooting procedures, packet-level findings, and recovery steps for repeatable IT support workflows| 

### Resource Group Components

![Resource Group](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Resource%20Group.png?raw=true)

Provisioned Windows 11 and Ubuntu Server VMs within a shared Resource Group. Configured cloud resources, validated system availability, and established remote access for both systems prior to production use.

## Virtual Network Configuration

![Virtual network](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Virtual%20Network.png?raw=true)

## VM Provisioning
### Window 11
![Creating window-vm2](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Creating%20window-vm2.png?raw=true)
### Ubuntu Linux
![Creating linux-vm2](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Creating%20linux-vm2.png?raw=true)
![VM's](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Deployment%20VM's.png?raw=true)
Windows 11 and Ubuntu Server 22.04 LTS deployed to support a mixed-OS environment. Windows 11 handles remote desktop administration and user-facing tasks. Ubuntu Server handles SSH-based administration, command-line operations, and network diagnostics.

## Virtual Machine's
### Status

![Linux status](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Linux%20status.png?raw=true)

![Linux & Windows running](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Linux%20&%20window%20running.png?raw=true)

Both VMs confirmed running in Microsoft Azure. Remote connectivity validated via RDP (Windows) and SSH (Ubuntu).

## ICMPv4 Traffic Filtering with Azure NSG

A continuous ping was initiated from the Windows VM to the Ubuntu VM while monitoring traffic in Wireshark. An inbound Deny ICMPv4 rule was created in the Azure Network Security Group (NSG) with a priority of 290, ensuring the rule was evaluated before broader allow rules. Once applied, ICMPv4 traffic was successfully blocked, resulting in request timeouts and the absence of Echo Replies in Wireshark. After removing the rule, connectivity was restored and ICMPv4 Echo Replies resumed, confirming successful traffic filtering and restoration.

Skills Demonstrated: Azure NSG Management, ICMPv4 Analysis, Wireshark Packet Capture, Network Security, Connectivity Troubleshooting.

![ICMP disable & enabled traffic NSG](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/ICMP%20disable%20&%20enabled%20traffic%20NSG.png?raw=true)


## Secure Shell (SSH) Connectivity
### Secure Remote Administration
![SSH connection and network traffic analysis 2](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/SSH%20connection%20and%20Network%20Traffic%20Analysis%202.png?raw=true)

Established a secure SSH connection from a Windows workstation capturing "SSH" traffic from Ubuntu Linux virtual machine to wireshark using PowerShell. Authenticated successfully with the username and password configured during the Azure virtual machine deployment. Executed administrative commands including "whoami", "hostname", "touch", "ls", "id", and "uname -a" to validate user access, system identity, file operations, and operating system information. Simultaneously captured SSHv2 traffic in Wireshark to verify encrypted communication between the client and Linux server.

## DHCP Lease Renewal

### DHCP Lease Assignment Analysis
During the DHCP lease renewal process, the active Remote Desktop (RDP) session was temporarily interrupted as the virtual machine released and renewed its network configuration. Observed the automatic reconnection process after the DHCP lease was reassigned and verified successful restoration of remote access. RDP session dropped during the release phase and automatically restored after lease renewal. Root cause confirmed: DHCP release invalidates active TCP sessions. Behavior documented and expected in Azure VM environments.

![DHCP release & renew results](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/DHCP%20release%20&%20renew%20results.png?raw=true)

Created a custom batch file (dhcp.bat) in C:\ProgramData containing ipconfig /release and ipconfig /renew commands. Used PowerShell to verify the script's presence and execute it, generating DHCP lease activity while capturing packets in Wireshark. Analyzed the DHCP Discover, Offer, Request, and ACK (ACKNOWLEDGE) process and confirmed successful assignment of IP addressing, subnet mask, default gateway, and DNS configuration. 

Verified the complete DHCP lease process, including:

* DHCP Discover
* DHCP Offer
* DHCP Request
* DHCP ACK

Confirmed successful network configuration assignment, including:

* IPv4 Address
* Subnet Mask
* Default Gateway
* DNS Suffix

## TCP Traffic Analysis
### TCP Session Analysis (Port 3389)

![TCP 3389 release & renew](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/TCP%203389%20-%20release%20&%20renew.png?raw=true)

Captured and analyzed TCP traffic associated with an active Remote Desktop (RDP) session using Wireshark. Observed ACK (ACKNOWLEDGE) packets confirming successful communication between endpoints and RST (RESET) packets generated during a DHCP lease renewal, causing the RDP session to reconnect. Root cause confirmed: DHCP release invalidates existing TCP sessions. Session automatically re-established after new IP assignment — expected behavior in Azure VM environments.

## DNS Query Responses

### DNS Resolution Verification

![DNS Results - release & renew](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/DNS%20results%20-%20release%20&%20renew.png?raw=true)

Root cause confirmed: DHCP release invalidates existing TCP sessions. Session automatically re-established after new IP assignment — expected behavior in Azure VM environments.

## DNS Packet Inspection

### DNS Traffic Inspection

![UDP & TCP results & renew](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/UDP%20&%20TCP%20results%20-%20release%20&%20renew.png?raw=true)

Performed DNS packet analysis using Wireshark by capturing and analyzing traffic on UDP/TCP port 53. Reviewed DNS queries, response records, and hostname resolution activity to validate DNS functionality, troubleshoot connectivity, and confirm successful communication between client systems and DNS services.
RDP Connectivity Issue

Remote Desktop Troubleshooting

Investigated a Remote Desktop session interruption and reviewed reconnection attempts. Demonstrated understanding of remote access troubleshooting and network connectivity validation.

## Script Creation

Administrative Script Development

Developed and deployed dhcp.bat to automate IP release and renewal on Windows endpoints. Verified execution via PowerShell. Reusable for DHCP-related diagnostics across the environment.

## Skills

**Cloud & Infrastructure**
`Microsoft Azure` `Virtual Machine Provisioning` `Azure Resource Groups` `Virtual Network Configuration` `Network Security Groups (NSG)` `Subnet Management` `Public & Private IP Management` `Cloud Endpoint Administration`

**Networking & Protocols**
`TCP/IP` `DHCP` `DNS` `ICMP` `SSH` `RDP` `UDP` `NSG Rule Enforcement` `Network Segmentation` `Packet-Level Traffic Analysis` `Protocol Troubleshooting`

**Operating Systems**
`Windows 11` `Ubuntu Server 22.04 LTS` `Cross-Platform Administration` `Remote Desktop Administration` `Linux Command Line`

**Security**
`NSG Inbound/Outbound Rule Management` `SSHv2 Encrypted Communication Validation` `Network Access Control` `Traffic Filtering & Restoration` `Credential Security Verification`

**Tools & Automation**
`Wireshark` `PowerShell` `Batch Scripting` `ipconfig` `Live Packet Capture` `Diagnostic Automation`

**Troubleshooting & Documentation**
`Root Cause Analysis` `DHCP Lease Conflict Resolution` `RDP Session Recovery` `TCP Session Analysis` `Repeatable Workflow Documentation`


