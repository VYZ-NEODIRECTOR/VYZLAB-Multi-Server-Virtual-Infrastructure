# Infrastructure Services

## File Server (VYZLAB-FS-01)

Provides centralized and resilient file storage.

### Storage Resilience
- **Shadow Copies** enabled
- Users can self-restore previous file versions

### Data Backup
- **Windows Server Backup** configured
- Backups target a secondary virtual disk for disaster recovery

## DMZ Web Server (VYZLAB-WS-01)

A dedicated web server isolated within the DMZ.

- **Network Segment:** DMZ (`10.2.2.0/24`)
- **Assigned IP:** `10.2.2.10`
- **Service:** Internet Information Services (IIS)
- **Purpose:** Hosts the corporate intranet

### Security Controls
- LAN-to-DMZ access permitted via pfSense
- Server is blocked from initiating unauthorized internal connections
