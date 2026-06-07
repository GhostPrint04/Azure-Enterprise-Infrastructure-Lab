# Azure Interprise Infraestructure Lab
Enterprise Azure infrastructure lab featuring Windows and Linux virtual machines, virtual networking, DHCP, DNS, RDP, SSH, NSGs, packet analysis with Wireshark, and PowerShell-based troubleshooting in a cloud environment.

Overview

Designed and administered a cloud-based Azure environment consisting of Windows and Linux virtual machines, virtual networking components, remote management services, and network troubleshooting workflows. Performed system administration tasks, validated network services, analyzed packet captures, and documented troubleshooting procedures using industry-standard tools.
   
## Technologies Used

| Category | Technologies |
|-----------|-------------|
| Cloud Infrastructure | [Microsoft Azure](https://azure.microsoft.com), Azure Resource Groups, Virtual Machines, Virtual Networks |
| Operating Systems | Windows Server, Windows 11, Ubuntu Linux |
| Networking | [TCP/IP](https://learn.microsoft.com), [DNS](https://learn.microsoft.com), [DHCP](https://learn.microsoft.com), NSGs |
| Remote Access | [RDP](https://learn.microsoft.com), [SSH](https://www.openssh.com) |
| Administration & Troubleshooting | [PowerShell](https://learn.microsoft.com/powershell), [Wireshark](https://www.wireshark.org) |

Key Activities

* Deployed and Configured Windows and Linux Virtual Machines.
* Managed Network Connectivity and Virtual Network Resources.
* Performed DHCP Lease Renewal and IP Configuration Validation.
* Captured and Analyzed DNS, TCP, UDP, SSH, and RDP Traffic Using Wireshark.
* Validated Remote Connectivity Through SSH and Remote Desktop Protocol.
* Investigated Connectivity Interruptions and Verified Recovery Procedures.
* Documented Troubleshooting Processes and Packet-level Analysis.

### Resource Group Components

![Resource Group](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Resource%20Group.png?raw=true)

Deployed and managed Windows and Linux virtual machines within Microsoft Azure. Configured cloud resources, validated system availability, and established the foundation required for remote administration, network analysis, and infrastructure troubleshooting activities.

## Virtual Network Configuration

![Virtual network](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Virtual%20Network.png?raw=true)

## Creating VM's
### - Window 11 VM Deployment
![Creating window-vm2](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Creating%20window-vm2.png?raw=true)
### - Linux VM Deployment
![Creating linux-vm2](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Creating%20linux-vm2.png?raw=true)
![VM's](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Deployment%20VM's.png?raw=true)
Windows 11 and Ubuntu Server 22.04 LTS were selected to simulate a mixed-operating-system enterprise environment. Windows 11 was used for remote administration and user-based tasks, while Ubuntu Server provided a Linux platform for SSH connectivity, command-line administration, and network troubleshooting exercises.

## Virtual Machine's
### Status

![Linux status](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Linux%20status.png?raw=true)

![Linux & Windows running](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Linux%20&%20window%20running.png?raw=true)

This is a represetantion of the actual Status of both virtual Machine's running successfully, made it on Microsoft Azure.

## ICMPv4 Traffic Filtering with Azure NSG

A continuous ping was initiated from the Windows VM to the Ubuntu VM while monitoring traffic in Wireshark. An inbound Deny ICMPv4 rule was created in the Azure Network Security Group (NSG) with a priority of 290, ensuring the rule was evaluated before broader allow rules. Once applied, ICMPv4 traffic was successfully blocked, resulting in request timeouts and the absence of Echo Replies in Wireshark. After removing the rule, connectivity was restored and ICMPv4 Echo Replies resumed, confirming successful traffic filtering and restoration.

Skills Demonstrated: Azure NSG Management, ICMPv4 Analysis, Wireshark Packet Capture, Network Security, Connectivity Troubleshooting.

![ICMP disable & enabled traffic NSG](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/ICMP%20disable%20&%20enabled%20traffic%20NSG.png?raw=true)


## Secure Shell (SSH) Connectivity
### Secure Remote Administration
![SSH connection and network traffic analysis](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/SSH%20connection%20and%20Network%20Traffic%20Analysis.png?raw=true)

Established a secure SSH connection from a Windows workstation capturing "SSH" traffic from Ubuntu Linux virtual machine to wireshark using PowerShell. Authenticated successfully with the username and password configured during the Azure virtual machine deployment. Executed administrative commands including "whoami", "hostname", "touch", "ls", "id", and "uname -a" to validate user access, system identity, file operations, and operating system information. Simultaneously captured SSHv2 traffic in Wireshark to verify encrypted communication between the client and Linux server.

## DHCP Lease Renewal

### DHCP Lease Assignment Analysis
During the DHCP lease renewal process, the active Remote Desktop (RDP) session was temporarily interrupted as the virtual machine released and renewed its network configuration. Observed the automatic reconnection process after the DHCP lease was reassigned and verified successful restoration of remote access. This exercise demonstrated practical troubleshooting of network-related connectivity interruptions, validated the relationship between DHCP operations and Remote Desktop services, and reinforced core system administration skills such as remote server management, network configuration validation, and infrastructure troubleshooting within a Microsoft Azure environment.

![DHCP release & renew results](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/DHCP%20release%20&%20renew%20results.png?raw=true)

Created a custom batch file (dhcp.bat) in C:\ProgramData containing ipconfig /release and ipconfig /renew commands. Used PowerShell to verify the script's presence and execute it, generating DHCP lease activity while capturing packets in Wireshark. Analyzed the DHCP Discover, Offer, Request, and ACK (ACKNOWLEDGE) process and confirmed successful assignment of IP addressing, subnet mask, default gateway, and DNS configuration. This lab demonstrates PowerShell administration, basic automation, packet analysis and network troubleshooting in Azure.

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

This lab demonstrates hands-on experience with DHCP lease renewal, PowerShell administration, packet analysis using Wireshark, and network troubleshooting in an Azure virtual machine environment.

## TCP Traffic Analysis
### TCP Session Analysis (Port 3389)

![TCP 3389 release & renew](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/TCP%203389%20-%20release%20&%20renew.png?raw=true)

Captured and analyzed TCP traffic associated with an active Remote Desktop (RDP) session using Wireshark. Observed ACK (ACKNOWLEDGE) packets confirming successful communication between endpoints and RST (RESET) packets generated during a DHCP lease renewal, causing the RDP session to reconnect. This analysis demonstrated how TCP manages session acknowledgment, connection termination, and connectivity recovery during network changes.

## DNS Query Responses

### DNS Resolution Verification

![DNS Results - release & renew](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/DNS%20results%20-%20release%20&%20renew.png?raw=true)

Monitored DNS queries and responses in Wireshark to validate name resolution processes. Analyzed request/response behavior and identified how client systems locate resources across the network.

## DNS Packet Inspection

### DNS Traffic Inspection

![UDP & TCP results & renew](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/UDP%20&%20TCP%20results%20-%20release%20&%20renew.png?raw=true)

Performed DNS packet analysis using Wireshark by capturing and analyzing traffic on UDP/TCP port 53. Reviewed DNS queries, response records, and hostname resolution activity to validate DNS functionality, troubleshoot connectivity, and confirm successful communication between client systems and DNS services.
RDP Connectivity Issue

Remote Desktop Troubleshooting

Investigated a Remote Desktop session interruption and reviewed reconnection attempts. Demonstrated understanding of remote access troubleshooting and network connectivity validation.

## Script Creation

Administrative Script Development

Developed a reusable network troubleshooting script for DHCP operations. Demonstrated basic scripting skills to streamline common support and network administration tasks.

## Skills Demonstrated: Wireshark, PowerShell, DHCP, DNS, TCP/IP, UDP, RDP Troubleshooting, Network Packet Analysis, Windows Administration, Network Diagnostics, Root Cause Analysis.


