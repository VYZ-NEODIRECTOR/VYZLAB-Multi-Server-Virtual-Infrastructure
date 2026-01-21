# Network Services & High Availability

## DHCP Failover

Dynamic IP addressing is managed by the Domain Controllers to ensure flexibility and redundancy.

- **Scope Range:** `10.1.1.100 – 10.1.1.200`
- **Failover Mode:** Active failover partnership
- **Servers:**
  - `VYZLAB-DC-01`
  - `VYZLAB-DC-02`

### Client Performance
- `VYZLAB-CLT-01` receives:
  - Automatic IP configuration
  - Redundant DNS settings pointing to both DCs

## DNS Architecture

- **Primary DNS:**  
  - `VYZLAB-DC-01` (`10.1.1.10`)
- **Secondary DNS:**  
  - `VYZLAB-DC-02` (`10.1.1.11`)
