# Multi-Subnet Home Network Lab

## Overview
This project simulates a small home/office network using Cisco Packet Tracer.  
It includes two separate subnets connected via a router, allowing devices on different networks to communicate.

The lab focuses on building a working network, testing connectivity, and troubleshooting common configuration issues.

---

## Network Topology
The diagram below shows the full lab setup, including both subnets, switches, and the router connecting them.

![Topology](screenshots/topology.png)

The network consists of:

- 1 Router (Cisco 1941)
- 2 Switches (2960)
- Subnet 1: 3 devices (2 PCs + 1 laptop)
- Subnet 2: 2 PCs

Subnet details:

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

### Example IP Configuration (Subnet 1)
Device configured in Subnet 1 with the correct default gateway:



### Example IP Configuration (Subnet 2)
Device configured in Subnet 2 with the correct default gateway:

![PC2 IP Config](screenshots/PC2-IP-Config.png)

---

## Router Configuration
The router is configured with two interfaces, each acting as the default gateway for its respective subnet.

```bash
enable
configure terminal

interface g0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown

interface g0/1
 ip address 192.168.2.1 255.255.255.0
 no shutdown 
```
 ---

## Connectivity Tests

### Successful Connectivity Between Subnets
Ping test showing successful communication between devices on different subnets.
![Ping Success](screenshots/ping-success.png)

### Failed Ping (Incorrect Default Gateway)
When a device is configured with the wrong default gateway, pings to other subnets fail.

- Issue: Default gateway set incorrectly on PC0.
- Symptom: Ping to 192.168.2.10 fails.

![Ping Failure](screenshots/wrong-gateway-fail.png)

### Fix: Correct Default Gateway
After updating the device to use the correct gateway (192.168.1.1 for Subnet 1), connectivity is restored.

- Action: `PC0 → IP Configuration → Set Default Gateway = 192.168.1.1`
- Result: Successful ping to 192.168.2.10.

![Ping Fixed](screenshots/gateway-fix-success.png)
