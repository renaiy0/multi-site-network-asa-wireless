# Telkom Exponential Topology

<div align="center">

![Network Topology](assets-cisc/topology.png)

*Enterprise-scale network infrastructure with 10 interconnected rooms*

[![Cisco Packet Tracer](https://img.shields.io/badge/Cisco-Packet_Tracer-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)](https://www.netacad.com/courses/packet-tracer)
[![In Progress](https://img.shields.io/badge/Status-In_Progress-yellow?style=for-the-badge)](https://github.com)
[![OSPF](https://img.shields.io/badge/Routing-OSPF-green?style=for-the-badge)](https://github.com)

</div>

---

## 📋 Project Overview

A comprehensive enterprise network simulation featuring **10 interconnected rooms** with advanced networking technologies. This project demonstrates the implementation of DHCP, DHCP Relay, OSPF dynamic routing, and wireless connectivity across a large-scale infrastructure. Built with Cisco Packet Tracer, it showcases real-world network design principles including centralized IP management, automatic route discovery, and wireless integration for mobility.

### 🎯 Key Features
- 🏢 **10 Interconnected Rooms** - Large-scale enterprise simulation
- 🌐 **Dynamic Routing** - OSPF implementation for automatic route discovery
- 📡 **Wireless Network** - Multiple access points for seamless connectivity
- 🔄 **DHCP & DHCP Relay** - Centralized IP address management
- 🔐 **Scalable Architecture** - Enterprise-grade network design

## 🏗️ Network Architecture

![Cisco Configuration](assets-cisc/cisco.pkt)

### Topology Structure

The network consists of **10 rooms/segments**, with the primary visible sections being:

```
                        ┌──────────────┐
                        │  MAINROUTER  │
                        │    Se3/0     │
                        └──────┬───────┘
                               │
                ┌──────────────┴──────────────┐
                │                             │
         172.17.1.10                    172.16.1.10
                │                             │
        ┌───────┴────────┐           ┌────────┴───────┐
        │   Router-PT    │           │   Router-PT    │
        │   WH RC Area   │           │  WH&CCNA Area  │
        └───────┬────────┘           └────────┬───────┘
                │                             │
        ┌───────┴────────┐           ┌────────┴────────┐
        │  RUANGAN WH RC │           │  RUANGAN CCNA   │
        │  (Yellow Zone) │           │  (Pink Zone)    │
        └────────────────┘           └─────────┬───────┘
                                              │
                                     ┌────────┴────────┐
                                     │ RUANGAN WAREHOUSE│
                                     │   (Blue Zone)   │
                                     └─────────────────┘
```

### Room Layout

1. **RUANGAN WH RC** (Yellow Zone) - Work-from-Home & Remote Connection Area
2. **RUANGAN CCNA** (Pink Zone) - Main training/office area
3. **RUANGAN WAREHOUSE** (Blue Zone) - Storage and logistics area
4. **Room 4-10** - Additional segments (in progress)

> **Note**: Complete topology documentation for all 10 rooms is being finalized.

## 🖥️ Network Devices

### Core Infrastructure

#### Routers
- **MAINROUTER** - Primary gateway to internet/WAN (Se3/0)
- **Central Router (Se2/0)** - Main distribution router
- **Router-PT WH RC** - Handles WH RC area routing
- **Router-PT WH&CCNA** - Manages CCNA and Warehouse areas

#### Switches
- **Switch 2960-24TT** - Core switch in WH RC area
- **Multiple Distribution Switches** - Connecting all segments

### End Devices by Room

#### RUANGAN WH RC (Yellow Zone)
- 2x Laptop-PT (Laptop0, Laptop1)
- 1x Server-PT (IP: 10.10.10.10)
- 1x Access Point-PT (Access Point2)

#### RUANGAN CCNA (Pink Zone)
- 4x PC-PT (PC1, PC2, PC3, PC4)
- 1x Printer-PT (Printer0)
- 1x Access Point-PT (Access Point0)

#### RUANGAN WAREHOUSE (Blue Zone)
- 2x PC-PT (PC5, PC6)
- 1x Printer-PT (Printer1)
- 1x Access Point-PT (Access Point1)

**Total Estimated Devices**: 50+ endpoints across 10 rooms

## 📊 IP Addressing Scheme

### Subnet Allocation

| Room | Network Address | Gateway | VLAN | Description |
|------|----------------|---------|------|-------------|
| **WH RC** | `172.17.1.0/24` | 172.17.1.1 | - | Remote work area |
| **CCNA** | `172.16.1.0/24` | 172.16.1.1 | - | Training/office |
| **Management** | `10.10.10.0/24` | 10.10.10.1 | - | Server & admin |
| **Warehouse** | `29x.x.x.x/24` | - | - | Storage area |
| **Rooms 4-10** | TBD | TBD | TBD | In progress |

### Key IP Addresses
- **MAINROUTER Se3/0**: Gateway interface
- **Server-PT**: `10.10.10.10`
- **WH RC Router**: `172.17.1.10` ↔ `172.17.1.1`
- **CCNA Router**: `172.16.1.10` ↔ `172.16.1.1`

## 🔧 Implemented Technologies

### 1. DHCP (Dynamic Host Configuration Protocol)
- Automatic IP address assignment
- Centralized IP management across all rooms
- Reduced manual configuration errors
- Dynamic lease management

### 2. DHCP Relay
- Forward DHCP requests across different subnets
- Enable centralized DHCP server for multiple networks
- Optimize network resource utilization
- Support for multi-site deployments

### 3. OSPF (Open Shortest Path First)
- Dynamic routing protocol (Link-state)
- Automatic route discovery and updates
- Fast convergence for network redundancy
- Scalable for large enterprise networks
- Area-based hierarchical design

### 4. Wireless Network
- Multiple Access Points for comprehensive coverage
- Wireless connectivity for mobility
- Support for laptops and mobile devices
- Seamless roaming between access points

## 🚀 Implementation Status

### ✅ Completed
- Basic topology design
- Physical device placement
- Initial IP addressing scheme
- Core router configuration
- Primary room setup (3/10 rooms)

### 🔄 In Progress
- DHCP server configuration
- DHCP relay setup on distribution routers
- OSPF routing implementation
- Wireless network configuration
- Remaining 7 rooms setup
- VLAN segmentation

### 📝 Future Plans
- Complete all 10 rooms deployment
- Inter-room connectivity testing
- VLAN implementation for security
- Access Control Lists (ACL)
- Quality of Service (QoS) configuration
- Network monitoring tools
- Redundancy and failover testing
- Documentation completion

## 🛠️ Configuration Guide

### Prerequisites
- Cisco Packet Tracer 7.x or newer
- Basic networking knowledge
- Understanding of routing protocols
- Familiarity with Cisco IOS commands

### DHCP Server Configuration

```cisco
Router(config)# ip dhcp pool POOL_NAME
Router(dhcp-config)# network 172.17.1.0 255.255.255.0
Router(dhcp-config)# default-router 172.17.1.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit

! Exclude gateway and server IPs
Router(config)# ip dhcp excluded-address 172.17.1.1 172.17.1.10
```

### DHCP Relay Configuration

```cisco
Router(config)# interface FastEthernet0/0
Router(config-if)# ip helper-address 10.10.10.10
Router(config-if)# exit
```

### OSPF Configuration

```cisco
Router(config)# router ospf 1
Router(config-router)# network 172.17.1.0 0.0.0.255 area 0
Router(config-router)# network 172.16.1.0 0.0.0.255 area 0
Router(config-router)# network 10.10.10.0 0.0.0.255 area 0
Router(config-router)# exit
```

### Wireless Access Point Setup

```cisco
! On Access Point
AP(config)# dot11 ssid TELKOM-WIFI
AP(config-ssid)# authentication open
AP(config-ssid)# exit

AP(config)# interface Dot11Radio0
AP(config-if)# ssid TELKOM-WIFI
AP(config-if)# no shutdown
```

## 🧪 Testing & Verification

### Verification Commands

```cisco
! Check DHCP bindings
Router# show ip dhcp binding

! Verify OSPF neighbors
Router# show ip ospf neighbor

! Check routing table
Router# show ip route

! Verify interfaces
Router# show ip interface brief

! Check wireless associations
AP# show dot11 associations
```

### Connectivity Tests

```bash
# From any PC
ping 10.10.10.10          # Test server connectivity
ping 172.17.1.1           # Test gateway
tracert 172.16.1.1        # Trace route to CCNA room
ipconfig /all             # Verify DHCP assignment
```

## 📚 Learning Objectives

This topology is designed to demonstrate:
- Enterprise network design principles
- Multi-site routing protocol implementation
- Centralized DHCP service management
- Wireless network integration
- Network scalability and redundancy
- Hierarchical network architecture
- IP addressing and subnetting
- Inter-VLAN routing (planned)
- Network troubleshooting methodologies

## 🎯 Use Cases

Perfect for learning:
- **Network Administration** - Managing large-scale networks
- **CCNA Certification** - Hands-on practice for exam topics
- **Enterprise IT** - Real-world deployment scenarios
- **Network Design** - Scalable architecture patterns
- **Troubleshooting** - Complex multi-room connectivity issues

```

## 🔍 Troubleshooting

### Common Issues

**DHCP not working**
- ✅ Verify DHCP pool configuration
- ✅ Check DHCP relay (ip helper-address)
- ✅ Ensure no IP conflicts
- ✅ Verify excluded addresses

**OSPF neighbors not forming**
- ✅ Check network statements
- ✅ Verify interface is not passive
- ✅ Confirm matching area IDs
- ✅ Check interface status (up/up)

**Wireless connectivity issues**
- ✅ Verify SSID configuration
- ✅ Check Access Point power
- ✅ Confirm wireless adapter settings
- ✅ Check for channel interference

**Inter-room communication failing**
- ✅ Verify routing table entries
- ✅ Check router interfaces status
- ✅ Test connectivity hop-by-hop
- ✅ Verify ACLs (if configured)

## 👥 Contributors

**renaiy0** - Network Engineer & Project Lead

## 📞 Support

For questions or issues:
- Open an issue on GitHub
- Contact network administrator team
- Check Cisco Packet Tracer documentation

## 📝 License

This project is for educational purposes.

---

<div align="center">

**Status**: 🔧 In Progress (3/10 Rooms Completed)  
**Last Updated**: November 2025  
**Version**: 1.0 - Development Phase

Made with ☕ by renaiy0

</div>
