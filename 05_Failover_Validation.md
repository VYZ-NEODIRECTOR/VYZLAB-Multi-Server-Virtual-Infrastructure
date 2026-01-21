# Maintenance & Failover Validation

To verify the **Always-On** design of the VYZLAB infrastructure, the following validation tests are conducted.

## 1. DC Outage Simulation

### Test
- Power down `VYZLAB-DC-01`

### Observation
- `VYZLAB-CLT-01` successfully authenticates using `VYZLAB-DC-02`

### DHCP Persistence
- Secondary DC continues issuing IP leases
- Confirms DHCP failover functionality

## 2. Recovery Testing

### File Recovery
- Delete a test file on `FS-01`
- Restore using the **Windows Server Backup** console

### AD Object Recovery
- Delete a test user account
- Restore via **Active Directory Administrative Center**
  - *Deleted Objects* container
