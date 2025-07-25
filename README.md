# Cybersecurity Planning, Implementation and Maintaining for a Fictitious Physiotherapy Center Physio

The domain environment including Windows server 2022 and Windows 10 workstations is simulated in VMware with virtual machines and the vulnerabilities are scanned with a Kali Linux machine. 

The company has introduction and appointment web pages (see repository physio-web-pages). 

The company processes customers' health data, which requires understanding and guidance on laws related to cybersecurity.

The project report (physio-cybersecurity) and the appendices (1-10) are written in Finnish and can be found in the doc folder. 

The (unfinished) summary in English can be found below.

## Using Cyber Threat Management and Protection Measures

### Protecting Devices with Updates and Software (Appendix 1)

The Windows workstation was updated via Windows Update. 
The Device Manager was checked to see if any devices needed a driver update. 
The Communication Port (COM1) drivers were updated by automatically searching for drivers. 
New versions of the firmware were searched for on the manufacturer's website. 
The router was updated. 
Windows protection was ensured to be up to date. 
App & Browser Control was enabled.
A full scan was performed in the Virus & threat Protection settings. 
The Windows Firewall was configured with a few rules.

### Managing Workstations with Management Tools (Appendix 2)

Windows workstation management in a domain environment was implemented using Windows server management consoles, group policies (GPO) and Powershell. 
The following management consoles were used: Server Manager, ADUC, ADDS, FSRM, DHCP, DNS Manager, Event Viewer, GPMC, Windows Server Backup and Print Management. 
GPO was used to implement, for example, password length settings, daily updates of workstations and department-specific public folders. 
Powershell was used to practice automating tasks (searching for users by name, searching for users in a specific OU, adding a user).

### Comparing and Selecting Encryption Methods (Appendix 3)

Different encryption methods were compared and the encryption methods needed for the customer environment were mapped and planned: Bitlocker protection for workstations, HTTPS/TLS protection for communication on appointment pages, VPN for remote processing of customer data, S/MIME for email encryption, Bitwarden for password protection, Node.js' bcrypt library for password hashing and Windows Hello for MFA. 
As a case example, the implementation of Bitlocker as a GPO was planned and started. 
As a separate practical example, the OpenStego encryption task of the Testout Security Pro course was done.

## Managing Cybersecurity Risks

Cybersecurity risks are managed, for example, by monitoring the network and scanning for vulnerabilities with various programs. 
The project combined these by observing Nmap scans with Wireshark. 
A lightweight network monitoring plan was created (Appendix 4a). 
The physio-web-pages application was launched on the workstation and its traffic and vulnerabilities were examined.

### Monitoring the Information Network Using Various Analysis Tools
### Scanning for Vulnerabilities of the Network
### Verifying the Vulnerabilities of the Systems
### Making Development Proposals to Improve Cybersecurity

## Promoting Cybersecurity solutions

### Knowing Laws, Regulations and Other Official Regulations Related to Information Security and Data Protection
### Illustrating Cyber Threats and Corresponding Risks
### Following Information Security Guidelines in The Work Duties

A short and concise preliminary information security guide was made.

### Instructing in Cybersecurity or Data Protection Matters



