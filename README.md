![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-orange)
![Samba](https://img.shields.io/badge/Samba-AD--DC-blue)
![Kerberos](https://img.shields.io/badge/Kerberos-Authentication-red)
![Documentation](https://img.shields.io/badge/Documentation-Professional-lightgrey)

# Samba-Active-Directory-Domain-Controller
Real‑World Identity Infrastructure Project — Deploying an Enterprise‑Grade Domain Controller on Linux

**Overview:**  
This project documents how I deployed a fully functional Active Directory Domain Controller using Samba, DNS, and Kerberos on Ubuntu Server. The goal was to recreate the core identity services used in enterprise environments — authentication, DNS resolution, user management, and Kerberos ticketing — without relying on Windows Server.  
This scenario demonstrates my ability to configure identity infrastructure, troubleshoot service dependencies, validate authentication flows, and document technical work clearly.

**🛠️ Technologies Used:**  
- **Ubuntu Server 22.04 LTS**  
- **Samba 4** (Active Directory Domain Controller)  
- **Kerberos** (`kinit`, `klist`)  
- **DNS** (SRV Records, A Records, Internal Resolution)  
- **Systemd** (Service Management)  
- **Linux Command Line Tools**  
- **Identity & Access Management Concepts**  
- **Troubleshooting & Root Cause Analysis**  
- **Documentation & Communication**

**Background:**  
Active Directory is the backbone of authentication and identity management in most enterprise environments. Instead of using Windows Server, I deployed a Linux‑based AD Domain Controller using Samba — an open‑source implementation of Microsoft’s AD protocols.  

This required configuring:  
- Domain provisioning  
- DNS integration  
- Kerberos authentication  
- User creation  
- Service validation  
- Hostname and network identity  

This project simulates what a Systems Administrator or IT Support Engineer would do when deploying or maintaining identity infrastructure.

**Symptoms / Verification Points:**  

DNS Functionality  
- A‑record resolution  
- SRV records for LDAP and Kerberos  
- Internal domain name resolution  

Kerberos Authentication  
- Ticket creation using `kinit`  
- Ticket validation using `klist`  

Samba AD DC Service  
- Service startup  
- Systemd status  
- Log output  

User Management  
- Creating a domain user  
- Listing all domain users  
- Verifying user presence in the AD database  

**Provisioning the Domain:**  
I used Samba’s provisioning tool to create the domain, configure DNS, and generate Kerberos settings:

```
sudo samba-tool domain provision --use-rfc2307 --interactive
```

This step created:  
- The AD database  
- DNS zone files  
- Kerberos configuration  
- Domain schema  
- Administrator account  

**Investigation:**  

1. **DNS Verification**  
I confirmed that DNS was correctly resolving domain services:  
```
host -t A christian.local
host -t SRV _ldap._tcp.christian.local
```

2. **Kerberos Ticketing**  
I authenticated as the domain administrator:  
```
kinit administrator
klist
```
This confirmed that Kerberos was issuing valid tickets — a critical part of AD authentication.

3. **User Creation**  
I created a test domain user:  
```
sudo samba-tool user create testuser
sudo samba-tool user list
```
Seeing “user testuser added successfully” confirmed that the AD database was functioning properly.

**Root Cause:**  
Unlike Windows Server, Samba AD DC requires manual configuration of:  
- DNS  
- Kerberos  
- Hostname identity  
- System services  
- Domain provisioning  

This project forced me to understand how identity systems actually work under the hood, not just how to click through a GUI.  

I gained hands‑on experience with:  
- Authentication flows  
- DNS dependencies  
- Kerberos ticketing  
- Directory services  
- Linux service management  

These are the same components used in real enterprise identity environments.

**Resolution:**  
By the end of the project:  
- The Samba AD DC was fully deployed  
- DNS and Kerberos were functioning correctly  
- Domain users could be created and managed  
- Authentication was validated with Kerberos tickets  
- All services were stable and persistent across reboots  

This resulted in a complete, production‑style identity environment running entirely on Linux.

**Outcome:**  
- Successful deployment of a Linux‑based AD Domain Controller  
- Verified DNS and Kerberos functionality  
- Created and managed domain users  
- Validated authentication using Kerberos tickets  
- Gained real‑world identity infrastructure experience  

**Skills Demonstrated:**  
- Linux server administration  
- Active Directory concepts  
- Identity & Access Management (IAM)  
- DNS architecture & troubleshooting  
- Kerberos authentication  
- Samba AD DC configuration  
- Systemd service management  
- Root cause analysis  
- Clear communication  
- Professional documentation
