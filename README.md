# Telkom Exponential Topology

## 📋 Project Description
This project implements a Telkom Exponential network topology currently under development. The topology integrates various modern networking technologies to simulate a medium-scale enterprise infrastructure.

## 🏗️ Network Architecture

### Topology Structure
The topology consists of 3 main segments:

1. **WH RC ROOM** (Yellow Zone)
   - Work-from-Home & Remote Connection Area
   - Wireless connectivity for remote access

2. **CCNA ROOM** (Pink Zone)
   - Main area with multiple PCs and printers
   - VLAN configuration and network management

3. **WAREHOUSE ROOM** (Blue Zone)
   - Warehouse area with PCs and printers
   - Centralized connection to backbone

### Network Devices

#### Routers & Core Devices
- **MAINROUTER**: Primary gateway to internet/WAN
- **Central Router (Se2/0)**: Main distribution router
- **Router-PT WH&CCNA (Se2/0)**: Router for CCNA area
- **Switch 2960-24TT**: Core switch in WH RC area

#### End Devices
**WH RC ROOM:**
- 2x Laptop-PT (Laptop0, Laptop1)
- 1x Server-PT
- 1x Access Point (Access Point2)

**CCNA ROOM:**
- 4x PC-PT (PC2, PC3, PC4, PC1)
- 1x Printer-PT (Printer0)
- 1x Access Point (Access Point0)

**WAREHOUSE ROOM:**
- 2x PC-PT (PC5, PC6)
- 1x Printer-PT (Printer1)
- 1x Access Point (Access Point1)

## 🔧 Implemented Technologies

### 1. **DHCP (Dynamic Host Configuration Protocol)**
- Automatic IP address assignment
- Centralized IP management
- Reduced manual configuration errors

### 2. **DHCP Relay**
- Forward DHCP requests across different subnets
- Enable centralized DHCP server for multiple networks
- Optimize network resource utilization

### 3. **OSPF (Open Shortest Path First)**
- Dynamic routing protocol
- Automatic route discovery and updates
- Fast convergence for network redundancy
- Scalable for enterprise networks

### 4. **Wireless Network**
- Multiple Access Points for area coverage
- Wireless connectivity for mobility
- Support for laptops and mobile devices

## 📊 IP Addressing Scheme

### Subnet Allocation
- **172.17.1.0/24**: WH RC ROOM Network
- **172.16.1.0/24**: CCNA ROOM Network
- **10.10.10.0/24**: Server & Management Network
- **29x.x.x.x**: WAREHOUSE ROOM Network

### Key IP Addresses
- **MAINROUTER Se3/0**: Gateway interface
- **Server-PT**: 10.10.10.10
- **Router Links**:
  - 172.17.1.10 (WH RC side)
  - 172.17.1.1 (Distribution)
  - 172.16.1.10 (CCNA side)
  - 172.16.1.1 (Distribution)

## 🚀 Implementation Status

### ✅ Completed
- Basic topology design
- Physical device placement
- Initial IP addressing

### 🔄 In Progress
- DHCP server configuration
- DHCP relay setup
- OSPF routing implementation
- Wireless network configuration

### 📝 Future Plans
- Testing connectivity between segments
- VLAN implementation
- Security policies (ACL)
- QoS configuration
- Monitoring and troubleshooting tools

## 🛠️ Usage Guide

### Prerequisites
- Cisco Packet Tracer 7.x or newer
- Basic networking knowledge
- Understanding of routing protocols

### Setup Steps
1. Open topology file in Cisco Packet Tracer
2. Verify physical connections between devices
3. Configure DHCP server on router/server
4. Setup DHCP relay on router interfaces
5. Configure OSPF on all routers
6. Setup wireless access points
7. Test connectivity using ping and traceroute

## 📚 Configuration Documentation

### DHCP Server Configuration
```
ip dhcp pool POOL_NAME
network [network-id] [subnet-mask]
default-router [gateway-ip]
dns-server [dns-ip]
```

### DHCP Relay Configuration
```
interface [interface-name]
ip helper-address [dhcp-server-ip]
```

### OSPF Configuration
```
router ospf [process-id]
network [network-id] [wildcard-mask] area [area-id]
```

## 🎯 Learning Objectives

This topology is designed to understand:
- Enterprise network design
- Routing protocol implementation
- DHCP service management
- Wireless integration
- Scalability and redundancy

## 👥 Development Team
Telkom Exponential Topology Project


---

**Status**: 🔧 In Progress  
**Last Updated**: 2025  
**Version**: 1.0 - Development Phase
