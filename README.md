# Redundant Enterprise Network Infrastructure with Secure Internet Connectivity

A complete enterprise network design and implementation project developed using **Cisco Packet Tracer** as part of my CCNA learning journey.

The project demonstrates how multiple Cisco networking technologies can work together to provide **network segmentation, redundancy, dynamic routing, security, automatic addressing, and Internet connectivity**.

---

## 📌 Project Overview

This project simulates a redundant enterprise network consisting of multiple switches, routers, VLANs, servers, end devices, and a simulated ISP/Internet environment.

The network was designed with a focus on:

* Network segmentation using VLANs
* Redundant default gateways using HSRP
* Dynamic routing using OSPF
* Layer 2 redundancy using Rapid PVST+
* Link redundancy and increased bandwidth using EtherChannel
* Automatic IP addressing using DHCP
* Internet connectivity 
* Traffic filtering using Extended ACLs
* Layer 2 security using Port Security and BPDU Guard
* Guest network isolation
* Network verification and troubleshooting

---

## 🏗️ Network Architecture

The topology contains:

* **3 Routers**

  * R1 – Edge/Internet router
  * R2 – Internal router
  * R3 – Internal redundant router
* **Multiple Cisco switches**
* **Multiple VLANs**
* **Internal servers**
* **Wireless access point and clients**
* **Simulated ISP router**
* **Simulated Internet server**

### VLAN Structure

| VLAN | Name        | Purpose                                |
| ---- | ----------- | -------------------------------------- |
| 10   | Management  | Network management and AP connectivity |
| 20   | Sales       | Sales department                       |
| 30   | Engineering | Engineering department                 |
| 40   | HR          | Human Resources                        |
| 50   | Servers     | Internal servers                       |
| 60   | Guest       | Guest users                            |
| 99   | Native      | Native VLAN for trunks                 |
| 999  | Parking-Lot | Unused/isolated switch ports           |

---

## 🔧 Technologies Implemented

### Layer 2

* VLANs
* 802.1Q Trunking
* Rapid PVST+
* STP Root Bridge Configuration
* EtherChannel
* LACP
* PortFast
* BPDU Guard
* Port Security
* Sticky MAC Addresses
* Native VLAN
* Parking-Lot VLAN

### Layer 3

* Inter-VLAN Routing
* Router-on-a-Stick
* HSRP
* OSPF
* Static Default Routes
* DHCP
* Extended ACLs

### Network Services

* DHCP
* DNS
* HTTP
* Simulated Internet Connectivity

---

## 🔄 Routing and Redundancy

### OSPF

OSPF is used as the dynamic routing protocol between the routers.

The routers form OSPF neighbor relationships and exchange routes for the internal VLAN networks.

The OSPF adjacencies were verified using:

```bash
show ip ospf neighbor
```

All required neighbors reached the:

```text
FULL
```

state.

### HSRP

HSRP provides gateway redundancy for the VLANs.

R2 is configured with a higher HSRP priority and is intended to operate as the **Active** router, while R3 provides redundancy as the **Standby** router.

The HSRP virtual gateway uses the `.1` address in each VLAN.

Example:

```text
R2: 192.168.20.2
R3: 192.168.20.3
HSRP VIP: 192.168.20.1
```

---

## 🌐 Internet Connectivity

Internet connectivity was verified by successfully pinging the simulated Internet server:

```text
8.8.8.8
```

---

## 🔐 Network Security

Several security mechanisms were implemented.

### Port Security

Access ports were configured with:

* Maximum of one MAC address
* Sticky MAC learning
* Restrict violation mode

### PortFast

PortFast was enabled on appropriate access ports to allow end devices to transition quickly to the forwarding state.

### BPDU Guard

BPDU Guard was enabled on PortFast access ports to protect the network from unauthorized switches or unexpected BPDU messages.

### Guest VLAN Isolation

An Extended ACL was configured to prevent the Guest VLAN from accessing the Server VLAN.

```text
Guest VLAN: 192.168.60.0/24
Server VLAN: 192.168.50.0/24
```

The ACL denies traffic from the Guest network toward the Server network while allowing other permitted traffic.

---

## 📡 Wireless Network

An access point was integrated into the enterprise network.

Wireless clients are connected through the configured network and can access permitted internal resources according to the network's VLAN and ACL policies.

---

## 🧪 Verification and Testing

The network was verified using Cisco IOS `show` commands and connectivity tests.

### OSPF Verification

```bash
show ip ospf neighbor
```

Used to verify OSPF neighbor relationships and FULL adjacencies.

### STP Verification

```bash
show spanning-tree
```

Used to verify:

* Root bridge
* Port roles
* Forwarding states
* STP priorities

### EtherChannel Verification

```bash
show etherchannel summary
```

Used to verify the operational EtherChannel and LACP member interfaces.

### Trunk Verification

```bash
show interfaces trunk
```

Used to verify:

* 802.1Q trunking
* Native VLAN
* Allowed VLANs
* Forwarding VLANs

### HSRP Verification

```bash
show standby brief
```

Used to verify the Active/Standby router roles and virtual IP addresses.

### Connectivity Tests

Ping tests were performed to verify:

* Default gateway connectivity
* Inter-VLAN communication
* Server connectivity
* Internet connectivity
* Guest VLAN restrictions

---

## 📁 Repository Contents

```text
CCNA-Enterprise-Network/
│
├── README.md
│
├── Packet_Tracer/
│   └── CCNA_Enterprise_Network.pkt
│
├── Report/
│   └── CCNA_Enterprise_Network.pdf
│
└── Screenshots/
    ├── Topology.png
    ├── OSPF_Verification_for_R1.png
    ├── OSPF_and_HSRP_Verification_for_R2.png
    ├── OSPF_and_HSRP_Verification_for_R3.png
    ├── EtherChannel_and_STP_Verification.png
    ├── Connectivity_Tests.png
    ├── DHCP_Verification.png
    ├── FTP_Server_Verification.png
    └── Facebook_Server_Verification.png


```

---

## ▶️ How to Use

1. Install **Cisco Packet Tracer**.
2. Clone or download this repository.
3. Open the `.pkt` file located in the `Packet_Tracer` folder.
4. Open the required router or switch CLI to inspect the configuration.
5. Use the verification commands listed above to examine the network operation.
6. Perform the included connectivity tests.

---

## 🎯 Project Objectives

The main objectives of this project were to:

* Design an enterprise network topology.
* Implement VLAN-based network segmentation.
* Configure inter-VLAN routing.
* Provide gateway redundancy using HSRP.
* Implement dynamic routing using OSPF.
* Improve Layer 2 redundancy using STP and EtherChannel.
* Provide automatic IP addressing using DHCP.
* Enable Internet access .
* Apply ACL-based traffic filtering.
* Implement basic Layer 2 security.
* Verify and troubleshoot the complete network.

---

## 📚 Learning Outcomes

This project provided practical experience with Cisco networking concepts and demonstrated how individual technologies interact within a complete enterprise network.

It strengthened my understanding of:

* Routing and switching
* VLAN segmentation
* Redundancy and high availability
* Dynamic routing
* Network security
* Address translation
* DHCP and network services
* Cisco IOS configuration
* Network troubleshooting and verification

---

## 👨‍💻 Author

**Kareem Zakaria**

Electronics & Communications Engineering Student

**Cairo University**

---

## 📝 Note

This project was developed for **educational and training purposes** using Cisco Packet Tracer.
