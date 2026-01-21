# VYZLAB-Multi-Server-Virtual-Infrastructure
A comprehensive, enterprise-grade virtual network featuring **redundant Active Directory services**, a **segregated DMZ web hosting environment**, and a **robust file-sharing architecture** with disaster recovery capabilities.

---

## 🚀 Infrastructure Overview

This project simulates a production-ready corporate network managed by a **pfSense firewall VM**, following the **"Always-On"** philosophy. It leverages dual Domain Controllers for high availability and automated backup strategies to ensure data resilience.

### Core Technical Pillars

- **High Availability (HA)** Dual Domain Controllers (`VYZLAB-DC-01`, `VYZLAB-DC-02`) with cross-replicated Active Directory and split-scope/redundant DHCP for uninterrupted authentication and IP services.

- **Network Security** Three-interface firewall (`WAN`, `LAN`, `DMZ`) isolates public-facing web services from internal corporate resources.

- **Storage & Recovery** Centralized File Server (`VYZLAB-FS-01`) uses **Shadow Copies** for versioning and **Windows Server Backup** for disaster recovery.

- **Service Segregation** Dedicated Web Server (`VYZLAB-WS-01`) resides in the DMZ to protect the internal domain from external threats.

---

## 🛠 Tools & Technology

### Virtualization & Operating Systems
- **VMware Workstation Pro:** Host hypervisor for the virtual environment.
- **pfSense:** FreeBSD-based firewall/router (deployed as a VM).
- **Windows Server 2025:** Primary OS for infrastructure roles.
- **Windows 11 Pro:** Client workstation for domain testing.

### Infrastructure & Services
- **Active Directory (AD DS):** Domain management and authentication.
- **Group Policy (GPMC):** Centralized configuration and security hardening.
- **DHCP:** Automated IP allocation and failover configuration.
- **IIS (Internet Information Services):** Web hosting for the DMZ environment.
- **File Server & SMB:** Centralized storage with NTFS permissions.

### Maintenance & Backup
- **Windows Server Backup:** System state and data recovery.
- **Active Directory Tools:** Management of OUs, Users, and Groups.

---

## 🏗 Features & Implementation Details

### Identity & Network Services

- **Redundant Active Directory (AD DS)** Ensures authentication remains available even if `VYZLAB-DC-01` goes offline.

- **DHCP Failover** Both Domain Controllers provide DHCP, eliminating a single point of failure for IP addressing.

### Data Protection Strategy

- **Shadow Copies** Users can restore previous file versions independently without IT intervention.

- **Windows Server Backup** Scheduled backups to a dedicated virtual disk simulate offsite or secondary storage recovery.

### DMZ Configuration

- **Security Hardening** The Web Server (`VYZLAB-WS-01`) is isolated in the DMZ to minimize exposure.

- **Firewall Rules** pfSense rules allow **only HTTP/HTTPS** from the WAN and block the DMZ from initiating connections into the LAN.

---

## 📊 Technical Reference

### IP Address Management
```text
NAME            TYPE    ROLE                IP ADDRESS      MASK            NOTES
pfSense VM      Server  Firewall            192.168.1.x     255.255.255.0   DHCP
                                            10.1.1.1        255.255.255.0   Static
                                            10.2.2.1        255.255.255.0   Static(DMZ)
VYZLAB-DC-01    Server  DC DHCP             10.1.1.10       255.255.255.0   Static
VYZLAB-DC-02    Server  Secondary DC/DHCP   10.1.1.11       255.255.255.0   Static
VYZLAB-FS-01    Server  File Server         10.1.1.12       255.255.255.0   Static
VYZLAB-WS-01    Server  Web Server DMZ      10.2.2.10       255.255.255.0   Static(DMZ)
VYZLAB-CLT-01   Client  Workstation         10.1.1.100      255.255.255.0   DHCP
```
### VM Specification
```text
VM NAME          OS                   vCPU    RAM     STORAGE      ADAPTER
VYZLAB-DC-01     Windows Server 2025  1       2 GB    30 GB        LAN 1
VYZLAB-DC-02     Windows Server 2025  1       2 GB    30 GB        LAN 1
VYZLAB-FS-01     Windows Server 2025  1       2 GB    60 GB,       LAN 1
                                                      40 GB
VYZLAB-WS-01     Windows Server 2025  1       2 GB    30 GB        DMZ
VYZLAB-CLT-01    Windows 11 PRO       1       4 GB    60 GB        LAN 1
