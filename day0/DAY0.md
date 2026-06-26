# Day 0 — Project Kickoff: Architecture & Planning

## 📋 Project Goals

Build a realistic enterprise infrastructure environment inside VMware Workstation that demonstrates:

- Windows Server administration (AD, DNS, DHCP, DFS, IIS, NLB)
- Linux integration (Domain Join, Docker, Samba, Nginx)
- Network security (OPNsense firewall, Suricata IDS)
- Monitoring & ITSM (Zabbix, GLPI)
- High availability (AD replication, DHCP failover, NLB)
- Security validation (Kali Linux attack simulation)

## 🎯 Scope

### Identity & Directory
- Active Directory Domain Services (atlas.internal)
- DNS (Forward/Reverse Zones)
- DHCP (Multi-scope configuration)
- OU Structure & Group Policy
- Domain-joined workstations

### Networking & Security
- Multi-NIC OPNsense firewall
- Network segmentation (6 networks)
- Suricata IDS/IPS
- Inter-network firewall rules
- DMZ isolation

### Linux & Containers
- Ubuntu domain join (SSSD/Realmd)
- Docker Engine
- Zabbix monitoring
- GLPI ITSM/Helpdesk
- Samba file services
- Nginx reverse proxy

### High Availability
- Active Directory replication
- DNS replication
- DHCP failover
- IIS NLB cluster

### Security Validation
- Kali Linux attack simulation
- Reconnaissance (Nmap, Enum4Linux)
- Exploitation (Responder, Kerberoasting)
- Detection (Suricata alerts)

## 🏗️ Architecture Decisions

### Multi-NIC vs VLAN Tagging

**Decision:** Multi-NIC architecture (no VLAN tagging)

**Rationale:**
- Simpler VMware networking setup
- More reliable packet capture for Suricata IDS
- Better performance for isolated networks
- No VLAN tag misconfiguration risks
- Easier troubleshooting

### DMZ Separation

**Decision:** Dedicated DMZ server (CAS-DMZ-01)

**Rationale:**
- Keeps public services isolated from internal infrastructure
- Nginx reverse proxy acts as single entry point
- No direct access to Domain Controllers from DMZ
- Better security posture

### Phased Dynamic Boot Strategy

**Decision:** Only power on VMs required for current scenario

**Rationale:**
- Limited RAM (32GB total)
- Faster testing cycles
- Focused validation
- Avoid unnecessary resource consumption

## 📊 Hardware Constraints

| Component | Specification |
|-----------|---------------|
| Host Machine | 32 GB RAM, 8-core CPU |
| Hypervisor | VMware Workstation 17 Pro |
| Storage | 200GB+ SSD (Thin Provisioned) |
| Max VMs Running | 3 simultaneous |

### Phased Boot Scenarios

| Scenario | VMs Running | RAM Used |
|----------|-------------|----------|
| AD / DNS / GPO | DC-01 + IT-WS1 | ~10GB |
| Linux Integration | DC-01 + SRV-LIN01 | ~12GB |
| Firewall / Segmentation | FW-01 + LIN01 + IT-WS1 | ~14GB |
| HA Replication | DC-01 + DC-02 + IT-WS1 | ~16GB |
| Attack Simulation | LIN01 + Kali + HR-WS1 | ~14GB |

## 🧪 Validation Strategy

Each day includes:

- ✅ Configuration steps documented
- ✅ Validation commands executed
- ✅ Screenshots captured
- ✅ Lessons learned documented
- ✅ GitHub updates pushed
- ✅ LinkedIn post published

## 📚 Documentation

- [Architecture Overview](../docs/Architecture-Overview.pdf)
- [Network Design](../docs/Network-Design.pdf)
- [Active Directory Design](../docs/Active-Directory-Design.pdf)
- [Security Architecture](../docs/Security-Architecture.pdf)
- [Project Roadmap](../docs/Project-Roadmap.pdf)

---

**Day 0 Complete — Design Phase Finished**
