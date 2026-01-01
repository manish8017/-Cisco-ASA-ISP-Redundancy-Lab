# ISP Level Redundancy with Cisco ASA

#Project Overview
This project demonstrates **ISP-level redundancy** using a **Cisco ASA firewall** connected to **two different ISPs
- Primary ISP (ACT – 10 Gbps)
- Backup ISP (BSNL – 5 Gbps)

The design ensures high availability, failover, and continuous internet connectivity for the internal network.

# Topology Description

#Network Diagram
The topology includes:
- Inside LAN
- Cisco ASA Firewall
- Dual ISPs (Primary & Backup)
- External network with a test server (Loopback)


# Devices Used
| Device | Role |
| R1 | Inside LAN Gateway |
| ASA | Firewall & ISP redundancy point |
| R2 | Primary ISP Router (ACT – 10 Gbps) |
| R3 | Backup ISP Router (BSNL – 5 Gbps) |
| R4 | External Router / Internet Simulation |
| Loopback | Test server (8.8.8.8) |


# IP Addressing Scheme

# Inside Network
| Network | Gateway |
| 10.11.11.0/24 | R1 – 10.11.11.1 |

# ASA to ISP Links
| Link | Subnet |
| ASA - ACT (Primary) | 130.12.12.0/24 |
| ASA- BSNL (Backup) | 150.10.10.0/24 |

# ISP to Internet Links
| Link | Subnet |
| ACT - R4 | 124.4.4.0/24 |
| BSNL -R4 | 134.4.4.0/24 |

#External Test Server
- Loopback IP: 8.8.8.8


# Design Logic

- ASA is connected to **two ISPs**
- Primary ISP (ACT)** is preferred due to higher bandwidth
- Backup ISP (BSNL)** is used during primary link failure
- Traffic automatically switches based on route availability
- Provides **fault tolerance and high availability**



#Key Configuration Concepts

#ASA Firewall
- Inside interface connected to LAN
- Two outside interfaces:
  - Outside-Primary (ACT)
  - Outside-Backup (BSNL)
- Default routing prefers ACT
- Backup route via BSNL with higher administrative distance
- Security policies applied at the ASA level

# Routing
- Static routes or SLA-based tracking can be used
- Internet reachability verified via loopback (8.8.8.8)

# Learning Outcomes
Understanding ISP-level redundancy
Dual ISP design using Cisco ASA
Primary / Backup ISP selection
Real-world enterprise firewall design
Network documentation and GitHub portfolio building


