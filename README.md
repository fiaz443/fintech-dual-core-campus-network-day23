# fintech-dual-core-campus-network-day23
FinTech Corporate Campus Network – Dual-Core Redundancy, MHSRP, LACP EtherChannel, OSPF, VLAN Segmentation and Load Sharing | Cisco Packet Tracer
Project Overview
This project demonstrates a FinTech Corporate Campus Network designed in Cisco Packet Tracer with a focus on high availability, gateway redundancy, load sharing, Layer 3 routing, VLAN segmentation, and link aggregation.
The design addresses a real-world business requirement where a single core-switch failure must not bring down the entire office network.
Lab
Day 23 – FinTech Corporate Campus: Dual-Core Redundancy & Load Balancing
🎯 Client Requirement
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
🏗️ Network Topology
The network contains:
Core-SW1 – Cisco 3560 Multilayer Switch
Core-SW2 – Cisco 3560 Multilayer Switch
Acc-SW1 – Cisco 2960 Access Switch
Edge-R1 – Cisco 2811/2911 Gateway Router
Cloud/Server – External/Cloud connectivity
VLAN 10 – Operations
VLAN 20 – Developers
VLAN 99 – Management
Topology Design
