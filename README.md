**# fintech-dual-core-campus-network-day23**

FinTech Corporate Campus Network – Dual-Core Redundancy, MHSRP, LACP EtherChannel, OSPF, VLAN Segmentation and Load Sharing | Cisco Packet Tracer
Project Overview

This project demonstrates a FinTech Corporate Campus Network designed in Cisco Packet Tracer with a focus on high availability, gateway redundancy, load sharing, Layer 3 routing, VLAN segmentation, and link aggregation.
The design addresses a real-world business requirement where a single core-switch failure must not bring down the entire office network.

Lab
**Day 23 – FinTech Corporate Campus: Dual-Core Redundancy & Load Balancing**

**🎯 Client Requirement:**

The client, Mr. Tariq – Head of FinTech Operations, required:
Complete core-switch redundancy
Gateway redundancy
Active-Active load sharing
VLAN 10 traffic primarily handled by Core-SW1
VLAN 20 traffic primarily handled by Core-SW2
Automatic failover when one core switch fails
Redundant connectivity between the campus and Edge Router
Higher bandwidth through EtherChannel
Fast internal routing convergence
Scalable and production-oriented network architecture

**🏗️ Network Topology**

**The network contains:**
Core-SW1 – Cisco 3560 Multilayer Switch

Core-SW2 – Cisco 3560 Multilayer Switch

Acc-SW1 – Cisco 2960 Access Switch

Edge-R1 – Cisco 2811/2911 Gateway Router

Cloud/Server – External/Cloud connectivity

VLAN 10 – Operations

VLAN 20 – Developers

VLAN 99 – Management

Topology Design
![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/1ccceb09-ceeb-4091-aeb6-69c78449fd1b.jpg)

**Redundancy Design**

**1. Dual Core Switches**

Two multilayer core switches are deployed instead of one.



If one core switch fails, the second core switch can continue forwarding traffic.

**Dual Connections to Edge-R1**

![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/982f7650-f774-4588-8f72-6f40ca8f235e.jpg)

Both core switches have independent Layer 3 transit connections to the Edge Router.

This removes the single core-to-edge path dependency.

**3. Core-to-Core Layer 3 EtherChannel**
 ![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/1a5feb3a-c812-4158-a204-403423d8bc4d.jpg)
 
Core-SW1 and Core-SW2 use a Layer 3 LACP EtherChannel as their high-speed cross-link.

Core-SW1
 
Core-SW2

**The logical Port-Channel provides:**

Link aggregation

Redundancy

Higher available bandwidth

Fast communication between the core switches

LACP mode: active

**Note: mode active is an LACP negotiation mode. mode on is a static EtherChannel and is not LACP.**

**4. Layer 2 LACP to Access Switch**

![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/5234f6b1-0016-4dea-b2c5-903afde6d681.jpg)

Acc-SW1 has redundant Layer 2 connections to both core switches.


These are configured as Layer 2 trunk EtherChannels using LACP.

LACP mode: active

 IP Addressing Scheme
Network
Purpose
Subnet
VLAN 10
Operations
10.10.10.0/24
VLAN 20
Developers
10.10.20.0/24
VLAN 99
Management
10.10.99.0/24
Core-SW1 ↔️ Edge-R1
Primary Transit
10.10.0.0/30
Core-SW2 ↔️ Edge-R1
Secondary Transit
10.10.0.4/30
Core-SW1 ↔️ Core-SW2
L3 Cross-Link
10.10.0.8/30
Virtual Gateway Addresses
VLAN
Virtual Gateway
VLAN 10
10.10.10.1
VLAN 20
10.10.20.1
VLAN 99
10.10.99.1
🏷️ VLAN Plan
VLAN ID
VLAN Name
Network
Purpose
10
Operations
10.10.10.0/24
Core Business Users
20
Developers
10.10.20.0/24
Software & DevOps Team
99
Management
10.10.99.0/24
Network & IT Management
🔁 MHSRP / HSRP Active-Active Load Sharing
Multiple HSRP groups are used so that both core switches can participate in forwarding traffic.
VLAN 10
Virtual Gateway: 10.10.10.1
Active:          Core-SW1
Standby:         Core-SW2
VLAN 20
Virtual Gateway: 10.10.20.1
Active:          Core-SW2
Standby:         Core-SW1
This provides active-active gateway utilization across the VLANs.
If Core-SW1 fails, Core-SW2 can take over VLAN 10.
If Core-SW2 fails, Core-SW1 can take over VLAN 20.
🚀 OSPF Dynamic Routing
OSPF Area 0 is used for dynamic Layer 3 routing between the core switches and Edge-R1.
OSPF provides:
Dynamic route exchange
Automatic route learning
Redundant paths
Fast convergence
Scalable routing
Reduced manual static-route configuration
Useful OSPF Verification
show ip ospf neighbor
show ip route
show ip ospf interface
🔗 EtherChannel / LACP Design
Connection
Layer
Technology
Recommended Mode
Core-SW1 ↔️ Core-SW2
Layer 3
LACP EtherChannel
active
Core-SW1 ↔️ Acc-SW1
Layer 2
LACP EtherChannel
active
Core-SW2 ↔️ Acc-SW1
Layer 2
LACP EtherChannel
active
Verification
show etherchannel summary
show interfaces port-channel
show interfaces trunk
🔐 Security & Availability Benefits
VLAN Segmentation
Different departments are logically separated using VLANs.
Benefits:
Reduced broadcast domains
Better traffic organization
Improved access control
Easier policy implementation
High Availability
Redundancy is provided through:
Dual multilayer core switches
Dual core-to-edge links
LACP EtherChannel
MHSRP/HSRP
OSPF dynamic routing
Business Continuity
The design reduces the impact of:
Core-switch failure
Individual link failure
Gateway failure
Routing-path failure
🔄 Traffic Flow
Normal VLAN 10 traffic:
PC – VLAN 10
      ↓
Acc-SW1
      ↓
L2 LACP EtherChannel
      ↓
Core-SW1
      ↓
OSPF
      ↓
Edge-R1
      ↓
External Network / Cloud
Normal VLAN 20 traffic:
PC – VLAN 20
      ↓
Acc-SW1
      ↓
L2 LACP EtherChannel
      ↓
Core-SW2
      ↓
OSPF
      ↓
Edge-R1
      ↓
External Network / Cloud
