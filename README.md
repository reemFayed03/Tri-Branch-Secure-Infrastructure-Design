# Enterprise Multi-Site Network Design & Implementation

A comprehensive network infrastructure project featuring dynamic routing, VLAN segmentation, and centralized service management using Cisco Packet Tracer.

## Project Overview
This project demonstrates the design and deployment of a scalable enterprise network connecting three main sites (Management, IT, and HR/Guest branches). The architecture focuses on optimizing IPv4 address space using **VLSM**, ensuring high availability via **OSPF**, and securing the infrastructure with **SSH** and **Extended ACLs**.

## Key Technical Features
* **Hierarchical Subnetting:** Implemented **VLSM** to minimize IP wastage across different departments.
* **Dynamic Routing:** Configured **OSPF (Open Shortest Path First)** for seamless inter-router communication and redundancy.
* **VLAN Segmentation:** Isolated departmental traffic using **Router-on-a-Stick** (Sub-interfaces) to enhance security and reduce broadcast domains.
* **Centralized DHCP Management:** Deployed a central DHCP server with **IP Helper-Address (DHCP Relay)** to provide dynamic addressing across multiple subnets.
* **Network Security:** * Hardened device access using **Enable Secret** and **Console Passwords**.
    * Replaced Telnet with **SSH (v2)** for secure remote management.
    * Applied **Extended Access Control Lists (ACLs)** to restrict Guest access to sensitive internal networks.

## Addressing Plan (VLSM)
|    Department     | Required Hosts |  Subnet ID  | CIDR | Default Gateway |
| :-----------------| :------------- | :---------- | :--- | :-------------- |
|   **Management**  |       30       | 172.16.0.0  | /27  | 172.16.0.1      |
|  **IT & Servers** |       30       | 172.16.0.64 | /27  | 172.16.0.65     |
| **HR Department** |       14       | 172.16.0.96 | /28  | 172.16.0.97     |
| **Guest Network** |       5        | 172.16.0.112| /29  | 172.16.0.113    |



## Topology Architecture
The network consists of:
* **3 Cisco Routers** (R1, R2, R3) connected in a redundant triangle topology.
* **3 Cisco Catalyst Switches** (S1, S2, S3) managing local VLANs.
* **Centralized Services:** DHCP Server located in the IT segment providing IPs globally.



## How to Use
1. Download and install **Cisco Packet Tracer**.
2. Clone this repository or download the `.pkt` file.
3. Open the file to view the live simulation and test connectivity (Ping/Traceroute).

## Security & Access
* **Management Protocol:** SSH v2 only (Telnet disabled).
* **Authentication:** Local User Database & Enable Secret Hashing.
* **Boundary Security:** Extended ACLs applied on the Guest Gateway.

## Challenges & Solutions:

* **Challenge:** Resolving DHCP broadcast issues across different subnets.

* **Solution:** Successfully implemented DHCP Relay (IP Helper-Address) on router sub-interfaces.

---
**Developed with focus on Network Scalability and Security.**
