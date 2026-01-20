# VYZLAB-Multi-Server-Virtual-Infrastructure
A comprehensive, enterprise-grade virtual network featuring **redundant Active Directory services**, a **segregated DMZ web hosting environment**, and a **robust file-sharing architecture** with disaster recovery capabilities.

---

## 🚀 Infrastructure Overview

This project simulates a production-ready corporate network managed by a **pfSense firewall**, following the **"Always-On"** philosophy. It leverages dual Domain Controllers for high availability and automated backup strategies to ensure data resilience.

### Core Technical Pillars

- **High Availability (HA)**  
  Dual Domain Controllers (`VYZLAB-DC-01`, `VYZLAB-DC-02`) with cross-replicated Active Directory and split-scope/redundant DHCP for uninterrupted authentication and IP services.

- **Network Security**  
  Three-interface firewall (`WAN`, `LAN`, `DMZ`) isolates public-facing web services from internal corporate resources.

- **Storage & Recovery**  
  Centralized File Server (`VYZLAB-FS-01`) uses **Shadow Copies** for versioning and **Windows Server Backup** for disaster recovery.

- **Service Segregation**  
  Dedicated Web Server (`VYZLAB-WS-01`) resides in the DMZ to protect the internal domain from external threats.

---

## 🛠 Features & Implementation Details

### Identity & Network Services

- **Redundant Active Directory (AD DS)**  
  Ensures authentication remains available even if `VYZLAB-DC-01` goes offline.

- **DHCP Failover**  
  Both Domain Controllers provide DHCP, eliminating a single point of failure for IP addressing.

### Data Protection Strategy

- **Shadow Copies**  
  Users can restore previous file versions independently without IT intervention.

- **Windows Server Backup**  
  Scheduled backups to a dedicated virtual disk simulate offsite or secondary storage recovery.

### DMZ Configuration

- **Security Hardening**  
  The Web Server (`VYZLAB-WS-01`) is isolated in the DMZ to minimize exposure.

- **Firewall Rules**  
  pfSense rules allow **only HTTP/HTTPS** from the WAN and block the DMZ from initiating connections into the LAN.

---

## 📝 Future Improvements

- **Site-to-Site Extension**  
  Expand part of the infrastructure to a second physical host via P2P Ethernet.

- **Linux Integration**  
  Join Ubuntu-based servers to the Windows Domain using SSSD for cross-platform compatibility.
