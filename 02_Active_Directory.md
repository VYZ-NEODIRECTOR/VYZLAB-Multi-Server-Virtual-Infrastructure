# Active Directory & Identity Management

The domain **VYZLAB.local** is structured to reflect a professional corporate hierarchy with scalability and security in mind.

## Custom OU Structure

The domain uses a centralized **VYZLAB** parent OU with the following sub-units:

### VYZ-Admins
- High-level administrative accounts
- Example:
  - `VYZ-NEODIRECTOR`

### VYZ-Users
Organized by department for granular policy enforcement:

- **IT**
  - Roboute Guilliman
- **HR**
  - John Wick
- **Finance**
  - Daenarys Targaryen

### VYZ-Servers
- Member servers:
  - `VYZLAB-FS-01`
  - `VYZLAB-WS-01`

### VYZ-Workstations
- Client machines:
  - `VYZLAB-CLT-01`

## Domain High Availability

### Replication
- `VYZLAB-DC-02` operates as a secondary Domain Controller
- Ensures directory availability during maintenance or failure

### Directory Resilience
- **Active Directory Recycle Bin** enabled on `DC-01`
- Allows instant restoration of deleted AD objects without downtime
