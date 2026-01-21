# Network Architecture & Security

The infrastructure utilizes a three-tier topology managed by a virtualized **pfSense** appliance, providing strict isolation between the internal domain and public-facing services.

## Segment Configuration

### WAN Interface
- Provides external connectivity via the host network  
- Addressing: `192.168.1.x`

### LAN (`10.1.1.0/24`)
- Hosts core domain infrastructure
- Includes:
  - Domain Controllers
  - File Server
  - Clients

### DMZ (`10.2.2.0/24`)
- Secure perimeter network
- Hosts:
  - Web Server (**VYZLAB-WS-01**)
- Fully isolated from the internal LAN

## Firewall & Routing (pfSense)

- **Gateway:** pfSense VM operates as the primary router at `10.1.1.1`
- **Security Policy:**
  - Web Server is prohibited from initiating connections to the LAN
  - Protects the domain in the event of a DMZ compromise
