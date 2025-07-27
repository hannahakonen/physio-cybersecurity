# Cybersecurity Planning, Implementation and Maintaining for a Fictitious Physiotherapy Center Physio

The domain environment including Windows server 2022 and Windows 10 workstations is simulated in VMware with virtual machines and the vulnerabilities are scanned with a Kali Linux machine. 

The company has introduction and appointment [web pages](https://github.com/hannahakonen/physio-web-pages/tree/main). 

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

Different encryption methods were compared and the encryption methods needed for the customer environment were mapped and planned: 
- Bitlocker protection for workstations
- HTTPS/TLS protection for communication on appointment pages
- VPN for remote processing of customer data
- S/MIME for email encryption
- Bitwarden for password protection
- Node.js' bcrypt library for password hashing
- Windows Hello for MFA 

As a case example, the implementation of Bitlocker as a GPO was planned and started. 

As a separate practical example, the OpenStego encryption task of the Testout Security Pro course was done.

## Managing Cybersecurity Risks

Cybersecurity risks are managed, for example, by monitoring the network and scanning for vulnerabilities with various programs. The project combined these by observing Nmap scans with Wireshark. 

### Monitoring the Information Network Using Various Analysis Tools

A lightweight network monitoring plan was created (Appendix 4a) and the network traffic of the workstation (Appendix 4b) and [the web application](https://github.com/hannahakonen/physio-web-pages/tree/main) running on it (Appendix 4c) was analyzed using Wireshark. At the same time, scans were performed on the workstation using Nmap on a Kali Linux machine. The results of the version scan are presented in full in Appendix 4d. Nmap scans and, for example, the database connections of the Physio web application to the MongoDB Atlas service were detected using Wireshark.

In addition, login attempts were already examined in Appendix 2 by modifying the Default Domain Conrollers Policy GPO to implement a check of both successful and unsuccessful domain logins and by viewing logins in the Server Manager Event Viewer console (Windows Logs > Security).

### Scanning for Vulnerabilities of the Network

The Kali Linux machine's Nmap was used to scan for possible open network connections on the workstation while analyzing with Wireshark and found the IP addresses, open ports and Windows operating system in use (Appendix 4b) as well as the Node.js Express framework used in [the web application](https://github.com/hannahakonen/physio-web-pages/tree/main) (Appendix 4c, 4d).

Based on the network monitoring plan, a vulnerability scan was carried out on the server with Nessus Essentials (Appendix 5b). The Nessus scan reports are presented in Appendices 5c-f (5e too large file, not included in the Github material).

The investigation of database injection vulnerabilities in the Physio web application was started with Burp Suite (Appendix 5h).

### Verifying the Vulnerabilities of the Systems

A summary (Appendix 6) of the results and reports of the Nmap and Nessus Essentials vulnerability scans from the previous sections (Appendices 4b-d, 5b) was made here.

Nmap was used only to scan the workstation with and without [the web application](https://github.com/hannahakonen/physio-web-pages/tree/main). Nessus was used also to scan the server. The vulnerabilities detected by Nmap and Nessus were consistent.

### Making Development Suggestions to Improve Cybersecurity

Development suggestions for improving information security based on vulnerability scans (Nmap, Nessus Essentials) are presented in Appendix 6. 

- Support for medium-strength SSL encryption found on port 443 of the server must be removed. 
- The outdated SSL certificate must be renewed and support for old TSL versions must be removed.
- The old SMB version found on port 445 of the workstation must be handled and SMB login must be forced.
- [The web application](https://github.com/hannahakonen/physio-web-pages/tree/main) must implement the Helmet.js middleware of the Express framework, which protects Express-based applications by setting http headers correctly. The code must also block unwanted http methods, force HTTPS, and set the response header related to the content protection policy to deny. Injection vulnerabilities in the NoSQL database must still be investigated.

## Promoting Cybersecurity solutions

### Knowing Laws, Regulations and Other Official Regulations Related to Information Security and Data Protection

The company processes healthcare customer and patient data, the laws and regulations of which are presented in Appendix 7. In Finland these include:

- the Act on the Processing of Customer Data in Social and Healthcare Services (703/2023)
- the EU General Data Protection Regulation (2016/679, GDPR)
- the Data Protection Act (1050/2018)
- the Act on Healthcare Professionals (559/1994)

In addition, Chapter 38 of the Criminal Code (39/1889) “Crimes related to information technology” defines data breaches, unauthorized use of data and crimes against information systems, and the Act on Electronic Identification and Trust Services (533/2016) regulates strong electronic identification.

According to the Customer Data Act, a healthcare service provider must register as a user of Kanta services if customer data is processed in an electronic customer or patient information system. Physio is obliged, among other things, to use an information system that meets the essential requirements and to prepare a data security plan. 

In accordance with the GDPR, Physio must also make a public data protection statement that explains what data is collected and why, how long the data is stored, and a description of the rights of the data subject.

### Illustrating Cyber Threats and Corresponding Risks

The most common and critical security threats today and the risks they pose to the client company were explained and described with brief examples (Appendix 8).

According to the Cybersecurity Center's Small Business Cybersecurity Guide, the most common cyber threats are phishing, malware, and ransomware.

ChatGPT also lists malware (e.g. ransomware), phishing, username and password breaches, insider threats, failure to manage updates and vulnerabilities, and security risks in IoT devices.

In the OWASP Foundation's 2021 Top 10 list, the most common web application security risks were broken access control, cryptographic flaws, injections, insecure design, and incorrect security settings.

For Physio, the risk with various threats is that customer and patient data could end up in the wrong hands, resulting in sanctions, reputational damage, and operational disruptions.

### Following Information Security Guidelines in The Work Duties

A short and concise preliminary information security guide was implemented for the client company (Appendix 9).

### Instructing in Cybersecurity or Data Protection Matters

A Security Guidance PowerPoint presentation was made on three small cybersecurity issues to consider in practical work for the company's employees: phishing emails, email encryption in Outlook, and implementing Bitwarden (Appendix 10).
