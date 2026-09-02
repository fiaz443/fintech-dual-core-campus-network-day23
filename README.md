**# fintech-dual-core-campus-network-day23**

FinTech Corporate Campus Network – Dual-Core Redundancy, MHSRP, LACP EtherChannel, OSPF, VLAN Segmentation and Load Sharing | Cisco Packet Tracer

**Project Overview**

This project demonstrates a FinTech Corporate Campus Network designed in Cisco Packet Tracer with a focus on high availability, gateway redundancy, load sharing, Layer 3 routing, VLAN segmentation, and link aggregation.
The design addresses a real-world business requirement where a single core-switch failure must not bring down the entire office network.

**Lab Information**

**Project:**
FinTech Corporate Campus

**Lab:** Day 23

**Scenario:** Dual-Core Redundancy & Load Balancing

**Platform:** Cisco Packet Tracer

**Core:** Cisco 3560 Multilayer Switches

**Access:** Cisco 2960

**Edge:** Cisco 2811/2911 Router

**Routing Protocol:** OSPF Area 0

**Gateway Redundancy:** MHSRP / HSRP

**Link Aggregation:** LACP EtherChannel

**Day 23 – FinTech Corporate Campus: Dual-Core Redundancy & Load Balancing**

**🎯 Client Requirement:**

**The client, Mr. Tariq – Head of FinTech Operations, required:**

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

![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/40f2be03-8a5e-48ff-acf8-7efd6c97e868.jpg)

**2. Dual Connections to Edge-R1**

Both core switches have independent Layer 3 transit connections to the Edge Router.

This removes the single core-to-edge path dependency.

![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/982f7650-f774-4588-8f72-6f40ca8f235e.jpg)


**3. Core-to-Core Layer 3 EtherChannel**

Core-SW1 and Core-SW2 use a Layer 3 LACP EtherChannel as their high-speed cross-link.

 ![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/1a5feb3a-c812-4158-a204-403423d8bc4d.jpg)
 
**The logical Port-Channel provides:**

Link aggregation

Redundancy

Higher available bandwidth

Fast communication between the core switches

LACP mode: active

**Note: mode active is an LACP negotiation mode. mode on is a static EtherChannel and is not LACP.**

**4. Layer 2 LACP to Access Switch**

Acc-SW1 has redundant Layer 2 connections to both core switches.

![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/5234f6b1-0016-4dea-b2c5-903afde6d681.jpg)

These are configured as Layer 2 trunk EtherChannels using LACP.

LACP mode: active

 **IP Addressing Scheme**

![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/59f2d3eb-ac51-445f-9df7-443220fe32e5.jpg)


**🔐 Security & Availability Benefits**

**VLAN Segmentation**

Different departments are logically separated using VLANs.

Benefits:

Reduced broadcast domains

Better traffic organization

Improved access control

Easier policy implementation

**High Availability**

Redundancy is provided through:

Dual multilayer core switches

Dual core-to-edge links

LACP EtherChannel

MHSRP/HSRP

OSPF dynamic routing

**Business Continuity**

The design reduces the impact of:

Core-switch failure

Individual link failure

Gateway failure

Routing-path failure

**🔄 Traffic Flow**

**Normal VLAN 10 traffic:**

![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/8db22d8f-a47b-4c12-b59b-f8d3ebeb2b54.jpg)

**Normal VLAN 20 traffic:**

![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/76f8a5b9-bd86-477b-99d7-bab8fa48be4e.jpg)

 Verification Checklist
After completing the configuration, verify:

![Network Topology](https://raw.githubusercontent.com/fiaz443/fintech-dual-core-campus-network-day23/main/5d55cae8-76de-4a4b-bfcd-70f7dc4f58c8.jpg)

**Project Outcome:**

This project demonstrates a resilient enterprise network architecture that combines:

**VLAN Segmentation + Layer 3 Switching + LACP + MHSRP/HSRP + OSPF + Dual-Core Redundancy**

The result is a network designed for:

High availability

Gateway redundancy

Active-active load sharing

Link redundancy


Dynamic routing

Scalability

Better business continuity


