# VYZLAB-Multi-Server-Virtual-Infrastructure
A comprehensive enterprise-grade virtual network featuring redundant Active Directory services, segregated DMZ web hosting, and a robust file-sharing architecture with disaster recovery capabilities.

## 🚀 Infrastructure Overview

This project simulates a production-ready corporate network managed by a **pfSense firewall**. It emphasizes the **"Always-On"** philosophy by utilizing dual Domain Controllers and automated backup strategies.

### Core Technical Pillars

- **High Availability (HA)**  
  Dual Domain Controllers (`DC-01`, `DC-02`) with cross-replicated Active Directory and split-scope/redundant DHCP.

- **Network Security**  
  Three-interface firewall setup (`WAN`, `LAN`, `DMZ`) to isolate public-facing web services from internal corporate data.

- **Storage & Recovery**  
  Centralized File Server (`FS`) utilizing Shadow Copies for versioning and Windows Server Backup for disaster recovery.

- **Service Segregation**  
  Dedicated Web Server (`WS`) placed within a DMZ to mitigate risk to the internal domain.

## 🛠 Features & Implementation Details

### Identity & Network Services

- **Redundant AD DS**  
  Configured a secondary Domain Controller to ensure authentication remains available if `DC-01` fails.

- **DHCP Failover**  
  Established DHCP on both controllers to prevent a single point of failure for client IP addressing.

### Data Protection Strategy

- **Shadow Copies**  
  Enabled on the File Server to allow users to restore previous versions of files without IT intervention.

- **Windows Server Backup**  
  Configured scheduled backups to a dedicated virtual disk to simulate offsite/secondary storage recovery.

### DMZ Configuration

- **Security Hardening**  
  The Web Server (`WS-01`) is isolated in the DMZ.

- **Firewall Rules**  
  Implemented strict pfSense rules allowing only HTTP/HTTPS traffic from the WAN, while blocking the DMZ from initiating connections into the LAN.

## 📝 Future Improvements

- **Site-to-Site Extension**  
  Migrating a portion of this infrastructure to a second physical host via P2P Ethernet.

- **Linux Integration**  
  Joining Ubuntu-based servers to the existing Windows Domain using SSSD.
