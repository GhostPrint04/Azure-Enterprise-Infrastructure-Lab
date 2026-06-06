# Azure Interprise Infraestructure Lab
Enterprise Azure infrastructure lab featuring Windows and Linux virtual machines, virtual networking, DHCP, DNS, RDP, SSH, NSGs, packet analysis with Wireshark, and PowerShell-based troubleshooting in a cloud environment.

Overview

Designed and administered a cloud-based Azure environment consisting of Windows and Linux virtual machines, virtual networking components, remote management services, and network troubleshooting workflows. Performed system administration tasks, validated network services, analyzed packet captures, and documented troubleshooting procedures using industry-standard tools.

Technologies Used

* Microsoft Azure
* Windows Server
* Ubuntu Linux
* PowerShell
* Wireshark
* RDP
* SSH
* DHCP
* DNS
* TCP/IP
* Network Security Groups (NSGs)

Key Activities

* Deployed and Configured Windows and Linux Virtual Machines.
* Managed Network Connectivity and Virtual Network Resources.
* Performed DHCP Lease Renewal and IP Configuration Validation.
* Captured and Analyzed DNS, TCP, UDP, SSH, and RDP Traffic Using Wireshark.
* Validated Remote Connectivity Through SSH and Remote Desktop Protocol.
* Investigated Connectivity Interruptions and Verified Recovery Procedures.
* Documented Troubleshooting Processes and Packet-level Analysis.

### Resource Group Components

![Resource Group Components](Resource%20group%20component.png)

Deployed and managed Windows and Linux virtual machines within Microsoft Azure. Configured cloud resources, validated system availability, and established the foundation required for remote administration, network analysis, and infrastructure troubleshooting activities.

## Creating VM's 
### (Window 11 & Linux)
![Creating window-vm](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Creating%20windows-vm.png?raw=true)

![Creating linux-vm](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Creating%20linux-vm.png?raw=true)

Windows 11 and Ubuntu Server 22.04 LTS were selected to simulate a mixed-operating-system enterprise environment. Windows 11 was used for remote administration and user-based tasks, while Ubuntu Server provided a Linux platform for SSH connectivity, command-line administration, and network troubleshooting exercises.

## Virtual Machine's
### Status

![Linux & windows VM's running](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/LInux-vm%20private%20ip.%20public%20ip%20&%20running%20status.png?raw=true)

![Linux & Windows VM's running](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/Linux%20&%20Windows%20VM's%20running.png?raw=true)

## TCP Traffic Analysis

### TCP Session Analysis (Port 3389)
![TCP 3389 release & renew](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/TCP%203389%20-%20release%20&%20renew.png?raw=true)

Captured and analyzed TCP traffic associated with an active Remote Desktop (RDP) session using Wireshark. Observed ACK packets confirming successful communication between endpoints and RST packets generated during a DHCP lease renewal, causing the RDP session to reconnect. This analysis demonstrated how TCP manages session acknowledgment, connection termination, and connectivity recovery during network changes.

## DNS Query Responses

### DNS Resolution Verification

![DNS Results - release & renew](https://github.com/GhostPrint04/Azure-Interprise-Infraestructure-Lab/blob/main/DNS%20results%20-%20release%20&%20renew.png?raw=true)

Monitored DNS queries and responses in Wireshark to validate name resolution processes. Analyzed request/response behavior and identified how client systems locate resources across the network.

Captura 3 – DNS Packet Inspection

DNS Traffic Inspection

Captured DNS traffic on UDP port 53 and reviewed query details, response records, and hostname resolution activity. Confirmed proper communication between client and DNS services.

⸻

Captura 4 – DHCP Lease Renewal

DHCP Lease Assignment Analysis

Performed IP release and renewal operations using PowerShell while capturing DHCP traffic in Wireshark. Observed the DHCP Request and DHCP ACK process responsible for assigning network configuration to the client.

⸻

Captura 5 – RDP Connectivity Issue

Remote Desktop Troubleshooting

Investigated a Remote Desktop session interruption and reviewed reconnection attempts. Demonstrated understanding of remote access troubleshooting and network connectivity validation.

⸻

Captura 6 – DHCP Automation Script

PowerShell Network Automation

Created and executed a batch script to automate DHCP release and renewal tasks. Used PowerShell to validate network configuration changes and confirm successful IP assignment.

⸻

Captura 7 – DHCP Renewal Verification

IP Configuration Validation

Verified successful DHCP lease renewal using ipconfig commands. Confirmed IPv4 addressing, subnet mask assignment, gateway configuration, and DNS suffix registration.

⸻

Captura 8 – Script Creation

Administrative Script Development

Developed a reusable network troubleshooting script for DHCP operations. Demonstrated basic scripting skills to streamline common support and network administration tasks.

⸻

Para el README del laboratorio

Puedes cerrar con algo así:

Skills Demonstrated: Wireshark, PowerShell, DHCP, DNS, TCP/IP, UDP, RDP Troubleshooting, Network Packet Analysis, Windows Administration, Network Diagnostics, Root Cause Analysis.


## SSH Connectivity

## DHCP Lease Renewal Analysis

## DNS Resolution Analysis

## TCP Session Analysis

## RDP Troubleshooting

## Video Demonstrations


