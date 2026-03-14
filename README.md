# Multilayer Switch VLAN Routing Lab

## Overview

This project demonstrates the implementation of **VLAN segmentation and Inter-VLAN routing using Cisco multilayer switches** in Cisco Packet Tracer. The lab simulates a small enterprise network where multiple VLANs communicate through a Layer 3 switch.

The objective of this lab is to understand how multilayer switches perform both **Layer 2 switching and Layer 3 routing** to enable communication between different VLAN networks.

---

## Network Topology

The topology consists of:

* 1 Core Multilayer Switch
* 2 Distribution Multilayer Switches
* 3 Access Switches
* 3 End Devices (PCs)

Each PC belongs to a different VLAN and network.



```
/images/network-topology.png
```

---

## Technologies Used

* Cisco Packet Tracer
* VLAN Configuration
* Trunking (802.1Q)
* Inter-VLAN Routing
* Multilayer Switching
* RIP Version 2
* Static IP Addressing

---

## VLAN Configuration

| VLAN ID | Network     | Purpose     |
| ------- | ----------- | ----------- |
| VLAN 10 | 10.1.1.0/24 | PC1 Network |
| VLAN 20 | 10.2.1.0/24 | PC2 Network |
| VLAN 30 | 10.3.1.0/24 | PC3 Network |

---

## IP Addressing

| Device | IP Address | Subnet Mask   | Default Gateway |
| ------ | ---------- | ------------- | --------------- |
| PC1    | 10.1.1.5   | 255.255.255.0 | 10.1.1.250      |
| PC2    | 10.2.1.5   | 255.255.255.0 | 10.2.1.250      |
| PC3    | 10.3.1.5   | 255.255.255.0 | 10.3.1.250      |

Gateway addresses are configured on the **SVI interfaces of the multilayer switch**.

---

## Key Configurations

### VLAN Creation

```
vlan 10
vlan 20
vlan 30
```

### Trunk Configuration

```
interface fa0/1
switchport mode trunk
```

### Inter-VLAN Routing

```
ip routing

interface vlan10
ip address 10.1.1.250 255.255.255.0

interface vlan20
ip address 10.2.1.250 255.255.255.0

interface vlan30
ip address 10.3.1.250 255.255.255.0
```

### RIP Routing

```
router rip
version 2
network 10.0.0.0
no auto-summary
```

---

## Connectivity Testing

Ping tests were performed to verify communication between VLANs.

Example:

```
PC1 > ping 10.2.1.5
PC1 > ping 10.3.1.5
```

Successful replies confirm **Inter-VLAN routing is functioning correctly**.

---

## Project Outcome

* VLAN segmentation successfully implemented
* Trunk links configured between switches
* Inter-VLAN routing enabled through multilayer switching
* PCs in different VLANs can communicate successfully

This lab demonstrates how multilayer switches simplify network design by combining switching and routing capabilities.

---

## Repository Structure

```
multilayer-switch-vlan-lab
│
├── multilayer_vlan_lab.pkt
├── images
│   └── network-topology.png
└── README.md
```

---

## Author

Sandupama Tissera

BSc (Hons) Computer Networks

NSBM Green University

