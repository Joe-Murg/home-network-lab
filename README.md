# Multi-Subnet Home Network Lab

## Overview
This project simulates a small home/office network using Cisco Packet Tracer.  
It includes two separate subnets connected via a router, allowing devices on different networks to communicate.

The lab focuses on building a working network, testing connectivity, and troubleshooting common configuration issues.

---

## Network Topology

The network consists of:

- 1 Router (Cisco 1941)
- 2 Switches (2960)
- Subnet 1: 3 devices (2 PCs + 1 laptop)
- Subnet 2: 2 PCs

- Subnet 1: `192.168.1.0/24`
- Subnet 2: `192.168.2.0/24`

Devices in each subnet connect to a switch, which connects to the router.

---

## IP Addressing

### Subnet 1 (192.168.1.0/24)
| Device   | IP Address     | Gateway        |
|----------|---------------|----------------|
| PC0      | 192.168.1.10  | 192.168.1.1    |
| PC1      | 192.168.1.11  | 192.168.1.1    |
| Laptop0  | 192.168.1.12  | 192.168.1.1    |

### Subnet 2 (192.168.2.0/24)
| Device | IP Address     | Gateway        |
|--------|---------------|----------------|
| PC2    | 192.168.2.10  | 192.168.2.1    |
| PC3    | 192.168.2.11  | 192.168.2.1    |

---

## Router Configuration

```text
enable
configure terminal

interface g0/0
ip address 192.168.1.1 255.255.255.0
no shutdown

interface g0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
