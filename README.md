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

1. Dual Core Switches
Two multilayer core switches are deployed instead of one.


If one core switch fails, the second core switch can continue forwarding traffic.
2. Dual Connections to Edge-R1
Both core switches have independent Layer 3 transit connections to the Edge Router.
Core-SW1 -------- Edge-R1
Core-SW2 -------- Edge-R1
This removes the single core-to-edge path dependency.
3. Core-to-Core Layer 3 EtherChannel
Core-SW1 and Core-SW2 use a Layer 3 LACP EtherChannel as their high-speed cross-link.
Core-SW1
   ║
   ║  L3 EtherChannel
   ║  LACP
   ║
Core-SW2
The logical Port-Channel provides:
Link aggregation
Redundancy
Higher available bandwidth
Fast communication between the core switches
LACP mode: active
Note: mode active is an LACP negotiation mode. mode on is a static EtherChannel and is not LACP.
4. Layer 2 LACP to Access Switch
Acc-SW1 has redundant Layer 2 connections to both core switches.
Core-SW1 ═════ Acc-SW1
Core-SW2 ═════ Acc-SW1
These are configured as Layer 2 trunk EtherChannels using LACP.
LACP mode: active
