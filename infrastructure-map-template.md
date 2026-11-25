# Infrastructure Map — Blank Template

Fill in one section per server or network component. Duplicate sections as needed. Store credentials in a secrets manager and reference them here by ID only — never plaintext.

---

## 1. Server Inventory

| Field | Value |
| --- | --- |
| Server name / hostname | |
| Asset tag / serial number | |
| Physical location (rack, row, site) | |
| Dell model | |
| CPU | |
| RAM (total / populated) | |
| Storage controllers | |
| Disk configuration (RAID level, sizes) | |
| NIC count and speeds | |
| iDRAC IP address | |
| iDRAC username (ref only) | |
| Admin / OS login (ref only) | |
| OS version | |
| Proxmox version | |
| Node role (cluster member / standalone) | |
| Cluster name | |
| Backup target | |
| Last backup verified | |
| Firmware version (BIOS / iDRAC) | |
| Last firmware update | |
| Warranty / support contract expiry | |
| Notes | |

### Systems Running on This Server

| VM / Container ID | Name | Role | IP Address | OS | Resources (vCPU / RAM / Disk) | Owner | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |

---

## 2. Kubernetes Clusters

| Field | Value |
| --- | --- |
| Cluster name | |
| Version | |
| Control plane nodes (host, IP) | |
| Worker nodes (host, IP) | |
| CNI plugin | |
| Ingress controller | |
| Storage class / provisioner | |
| Namespaces in use | |
| Monitoring stack | |
| Logging stack | |
| Certificate management (e.g. cert-manager) | |
| Last upgrade date | |
| Notes | |

### Key Workloads

| Namespace | Deployment / Service | Purpose | Exposed via (Ingress / NodePort / LB) | TLS cert source | Notes |
| --- | --- | --- | --- | --- | --- |
| | | | | | |
| | | | | | |
| | | | | | |

---

## 3. Docker Hosts (non-Proxmox)

| Field | Value |
| --- | --- |
| Host name / IP | |
| Docker version | |
| Compose files location | |
| Named volumes / bind mounts | |
| Networks in use | |
| Containers running | |
| Image registry used | |
| Notes | |

---

## 4. Network Topology

| Field | Value |
| --- | --- |
| Uplink provider | |
| Uplink router model | |
| Uplink router management IP | |
| Uplink router admin login (ref only) | |
| WAN IP(s) | |
| Permanent IP blocks (CIDR) | |
| Subnet allocations | |
| VLAN IDs and names | |
| Managed switch model(s) | |
| Switch management IPs | |
| Firewall rules summary | |
| NAT configuration | |
| DNS servers (internal / external) | |
| DHCP scope(s) | |
| Notes | |

### Data Flows

| Source | Destination | Port / Protocol | VLAN | Purpose | Notes |
| --- | --- | --- | --- | --- | --- |
| | | | | | |
| | | | | | |
| | | | | | |
| | | | | | |

---

## 5. VoIP System

| Field | Value |
| --- | --- |
| PBX platform / version | |
| SIP trunk provider(s) | |
| Trunk credentials (ref only) | |
| DID number ranges | |
| Extensions in use | |
| Codec(s) | |
| QoS configuration (DSCP / CoS) | |
| Jitter buffer settings | |
| Registration servers | |
| Failover behaviour | |
| Notes | |

---

## 6. Backups & Disaster Recovery

| Field | Value |
| --- | --- |
| Backup tool | |
| Backup schedule | |
| Retention policy | |
| Backup target location(s) | |
| Encryption | |
| Last full restore test date | |
| RTO / RPO targets | |
| Offsite / cloud copy | |
| Notes | |

---

## 7. Monitoring & Alerting

| Field | Value |
| --- | --- |
| Monitoring tool(s) | |
| What is monitored | |
| Alert thresholds | |
| Alert channels (email / SMS / Slack) | |
| Escalation path | |
| Dashboard URL(s) | |
| Log aggregation | |
| Notes | |

---

## 8. External Dependencies

| Dependency | Provider | Purpose | Account / Contract Ref | Expiry / Renewal Date | Notes |
| --- | --- | --- | --- | --- | --- |
| Domain registration(s) | | | | | |
| TLS certificates | | | | | |
| DNS hosting | | | | | |
| Managed services / APIs | | | | | |
| Support contracts | | | | | |
| | | | | | |

---

## 9. Change Log

| Date | Component | Change Description | Changed By |
| --- | --- | --- | --- |
| | | | |
| | | | |
| | | | |

---

*Template version 1. Companion to the interview question set in the network-admin-interview-questions repo. Update this file as the administrator fills it in; consider converting completed sections into Mermaid diagrams for visualisation.*