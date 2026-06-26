# Atlas Enterprise Infrastructure Lab

> A production-inspired enterprise infrastructure laboratory built inside VMware Workstation and documented as a complete engineering diary.

## 📋 Project Overview

This project simulates a modern Windows/Linux enterprise environment while operating under realistic hardware constraints using a phased deployment methodology.

| Attribute | Value |
|-----------|-------|
| **Domain** | atlas.internal |
| **Hypervisor** | VMware Workstation 17 Pro |
| **Total VMs** | 8 |
| **Architecture** | Multi-NIC Segmented Network |
| **Boot Strategy** | Phased Dynamic Boot |

## 🏗️ Architecture



                              INTERNET
                                  │
                                  │
                         ┌────────▼────────┐
                         │   CAS-FW-01     │
                         │   OPNsense      │
                         │  Suricata IDS   │
                         └────────┬────────┘
                                  │
                                  │  Multi-NIC
                                  │
         ┌────────────────────────┼────────────────────────┐
         │                        │                        │
         ▼                        ▼                        ▼
   ┌─────────────┐          ┌─────────────┐          ┌─────────────┐
   │  VLAN 10    │          │  VLAN 20    │          │  VLAN 30    │
   │  MANAGEMENT │          │     HR      │          │     IT      │
   │ 192.168.10  │          │ 192.168.20  │          │ 192.168.30  │
   └──────┬──────┘          └──────┬──────┘          └──────┬──────┘
          │                        │                        │
          ▼                        ▼                        ▼
   ┌─────────────┐          ┌─────────────┐          ┌─────────────┐
   │  DC-01      │          │  HR-WS1     │          │  IT-WS1     │
   │  DC-02      │          │  (meryem)   │          │  (idrissi)  │
   │  SRV-LIN01  │          └─────────────┘          └─────────────┘
   └─────────────┘
                                  │
                                  │
         ┌────────────────────────┼────────────────────────┐
         │                        │                        │
         ▼                        ▼                        ▼
   ┌─────────────┐          ┌─────────────┐          ┌─────────────┐
   │  VLAN 50    │          │  VLAN 60    │          │             │
   │    DMZ      │          │  ATTACKER   │          │             │
   │ 192.168.50  │          │ 192.168.60  │          │             │
   └──────┬──────┘          └──────┬──────┘          └─────────────┘
          │                        │
          ▼                        ▼
   ┌─────────────┐          ┌─────────────┐
   │  DMZ-01     │          │  KALI-01    │
   │  Nginx      │          │  Attacker   │
   │  Proxy      │          └─────────────┘
   └─────────────┘

## 🖥️ Virtual Machines

| Hostname | OS | Role | IP |
|----------|-----|------|-----|
| CAS-FW-01 | OPNsense | Firewall + Suricata | 192.168.1.1 |
| CAS-DC-01 | WS2022 GUI | Primary DC, DNS, DHCP | 192.168.10.10 |
| CAS-DC-02 | WS2022 Core | Secondary DC, DNS | 192.168.10.11 |
| CAS-SRV-LIN01 | Ubuntu 24.04 | Docker (Zabbix, GLPI, Samba) | 192.168.10.30 |
| CAS-DMZ-01 | Ubuntu 24.04 | Nginx Reverse Proxy | 192.168.50.10 |
| CAS-IT-WS1 | Windows 11 | IT Workstation (idrissi) | DHCP (VLAN 30) |
| CAS-HR-WS1 | Windows 11 | HR Workstation (meryem) | DHCP (VLAN 20) |
| CAS-KALI-01 | Kali Linux | Attacker / Pentest | 192.168.99.100 |

## 📊 Network Segmentation

| VLAN | Name | Subnet | Purpose |
|------|------|--------|---------|
| 10 | Management/Servers | 192.168.10.0/24 | Infrastructure Services |
| 20 | HR Production | 192.168.20.0/24 | End Users |
| 30 | IT Operations | 192.168.30.0/24 | Administrators |
| 40 | Finance | 192.168.40.0/24 | Reserved |
| 50 | DMZ | 192.168.50.0/24 | Public Reverse Proxy |
| 99 | Attacker Network | 192.168.99.0/24 | Security Testing |

## 📅 7-Day Roadmap

| Day | Focus | Status |
|-----|-------|--------|
| **Day 0** | Architecture & Planning | ✅ Complete |
| **Day 1** | Active Directory, DNS & DHCP | 🔲 Pending |
| **Day 2** | Group Policy & DFS | 🔲 Pending |
| **Day 3** | Linux Integration & Docker | 🔲 Pending |
| **Day 4** | Firewall & Network Security | 🔲 Pending |
| **Day 5** | Monitoring & ITSM | 🔲 Pending |
| **Day 6** | High Availability & Disaster Recovery | 🔲 Pending |
| **Day 7** | Security Validation & Detection | 🔲 Pending |

## 🛠️ Technology Stack

| Category | Technologies |
|----------|--------------|
| **Identity** | Active Directory, DNS, DHCP, Kerberos |
| **Windows Services** | IIS, WDS, DFS, FSRM, NLB |
| **Linux Services** | Ubuntu, Docker, Nginx, Samba |
| **Monitoring** | Zabbix, Suricata |
| **ITSM** | GLPI |
| **Security** | OPNsense, Kali Linux, BloodHound |

## 🔗 Quick Links

- [Architecture Overview](docs/Architecture-Overview.pdf)
- [Network Design](docs/Network-Design.pdf)
- [Active Directory Design](docs/Active-Directory-Design.pdf)
- [Project Roadmap](docs/Project-Roadmap.pdf)

---

