# 🌐 Networking Notes

> A structured study guide covering core networking concepts — OSI Model, LAN Topologies, TCP/IP, Subnetting, VPN, and more.

---

## 📋 Table of Contents

1. [OSI Model](#1-osi-model)
2. [LAN Topologies](#2-lan-topologies)
3. [Packets & Frames (TCP/IP)](#3-packets--frames--tcpip)
4. [Transport, Session, Presentation & Application Layers](#4-transport-session-presentation--application-layers)
5. [Switches & Routers](#5-switches--routers)
6. [Ports 101](#6-ports-101)
7. [ARP & DHCP](#7-arp--dhcp)
8. [Subnetting](#8-subnetting)
9. [VPN Technology & LAN Networking Devices](#9-vpn-technology--lan-networking-devices)

---

## 1. OSI Model

The **OSI Model** (Open Systems Interconnection Model) is an essential model used in networking. This critical model provides a framework dictating how all networked devices will send, receive and interpret data.

At every individual layer that data travels through, specific processes take place, and pieces of information are added to this data — this process is called **encapsulation**.

### The 7 Layers (Top to Bottom)

| # | Layer | Description |
|---|-------|-------------|
| 7 | **Application** | Human-computer interaction layer |
| 6 | **Presentation** | Data formatting and encryption |
| 5 | **Session** | Managing sessions between applications |
| 4 | **Transport** | End-to-end communication, error recovery |
| 3 | **Network** | Routing and logical addressing |
| 2 | **Data Link** | Physical addressing (MAC) |
| 1 | **Physical** | Hardware transmission of raw bits |

---

### Layer 1 — Physical

This layer references the physical components of the hardware used in networking and is the **lowest layer** you will find. Devices use electrical signals to transfer data between each other in a **binary numbering system (1s and 0s)**.

> **Example:** Ethernet cables connecting devices.

---

### Layer 2 — Data Link

The Data Link layer focuses on the **physical addressing** of the transmission. It receives a packet from the Network layer and adds in the **Physical (Media Access Control) MAC address** of the receiving endpoint.

Inside every network-enabled computer is a **Network Interface Card (NIC)** which comes with a unique MAC address to identify it.

---

### Layer 3 — Network

Here the magic of **routing & re-assembly of data** takes place. At this stage of the networking module, these protocols include:
- **OSPF** (Open Shortest Path First)
- **RIP** (Routing Information Protocol)

The factors that decide what route is taken:
- What path is the **shortest**?
- What path is the most **reliable**?
- Which path has the **faster physical connection**?

---

## 2. LAN Topologies

*(Date: 23/04/26)*

In the reference to networking, when we refer to the term "topology", we are actually referring to the **design or look of the network** at hand.

---

### ⭐ Star Topology

The main premise of a star topology is that devices are individually connected via a central networking device such as a **switch or hub**. This topology is the most commonly found today because of its reliability and scalability — despite the cost.

```
        [Device 6]
           |
[Device 1][Device 2]
     \      |      /
   [Device 3]--[Switch/Hub]--[Device 4]
                  |
             [Device 5]
```

- Any information sent to a device in this topology is sent via the central device to which it connects.
- More cabling and dedicated networking equipment is required → more **expensive** than other topologies.
- **Advantages:** Much scalable in nature — easy to add more devices.

---

### 🚌 Bus Topology

This type of connection relies upon a **single connection** which is known as a **backbone cable**.

- All data → travels through single cable → very quickly prone to → **slow and bottleneck**
- This bottleneck → very difficult troubleshooting → difficult to identify which device is experiencing issues with data, all travelling along the same route.

```
[Device 1]  [Device 2]  [Device 3]
    |            |            |
•---+------------+------------+---•  (Backbone Cable)
         |              |
    [Device 4]     [Device 5]
```

---

### 🔁 Ring Topology

The ring topology (also known as **token topology**). Devices such as computers are connected directly to each other to form a **loop**.

- Ring topology works by sending data across the loop until it reaches the destined device, using other devices along the loop to forward the data.
- It will send its own data first before sending data from another device.
- **One direction** for data to travel → easy to troubleshoot any faults that arise.
- ⚠️ This is a **double-edged sword** because it isn't an efficient way of data travelling across a network.

---

## 3. Packets & Frames / TCP/IP

### Packets and Frames

**Packets** and **Frames** are small pieces of data that, when forming together, make a larger piece of information or message.

- A **packet** is a piece of data that is used at Layer 3 of the OSI model, with encapsulating information such as an IP header and payload.
- A **frame**, however, is used at Layer 2 of the OSI model, with encapsulating information such as MAC address, containing additional information such as MAC address.

### TCP/IP (The Four-Way Handshake)

TCP/IP protocol consists of **four layers** and is arguably just a summarised version of the OSI model:

| Layer | TCP/IP |
|-------|--------|
| 4 | Application |
| 3 | Transport |
| 2 | Internet |
| 1 | Network Interface |

TCP guarantees that any data **will** be received on the other end.

TCP packets contain various sections of information known as **headers**. Some crucial headers are:
- Source IP
- Destination port
- Destination IP
- Sequence number
- Checksum
- Flag
- Source port

### Three-Way Handshake

The term given for the process used to establish a connection between two clients using special messages. The three-way handshake communicates using a flag:

1. **SYN** — Initial packet sent by a client during the handshake to initiate a connection and synchronise the two clients.
2. **SYN/ACK** — Sent by a receiving client to acknowledge the synchronisation attempt.
3. **ACK** — The acknowledgement packet can be used by either client or server to acknowledge that a series of messages/packets have been successfully received.
4. **DATA** — Once a connection has been established, data is sent via this flag.
5. **FIN** — Used to cleanly (properly) close the connection after it has been completed.
6. **RST** — This packet abruptly ends all communication. This is used to communicate that there is a problem and data loss is accepted.

### TCP/IP Header Fields

| Field | Description |
|-------|-------------|
| Time to Live (TTL) | Sets an expiry timer for the packet so it doesn't clog up the network |
| Checksum | Ensures data integrity (error checking) |
| Source Address | IP address of the source device |
| Destination Address | IP address of the destination device |
| Headers | Communication between two devices |
| Source Port | Port used by sender |
| Destination Port | Port the data is being sent to |
| Data | The actual content being transmitted |

### UDP/IP

- **UDP** (User Datagram Protocol) — This packet is used to send data quickly, without the need for a connection.
- UDP is **much faster** than TCP.
- UDP does **not** receive a continuous stream from the application layer.
- UDP is useful in situations where there are **small pieces of data being sent**.

---

## 4. Transport, Session, Presentation & Application Layers

### ④ Transport

Transport data is sent plays with what protocol it allows one to send data across a network. It is decided based upon several factors:

- **TCP** — Transmission Control Protocol: This protocol reserves a constant connection between the two devices for the amount of time it takes for the data to be sent and received. TCP is also used for excluding guarantees that data sent from this small chunk in the session layer (Layer 5) has then been received and transmitted in the same order.
- **UDP** — User Datagram Protocol

### ⑤ Session

Once data has been correctly formatted from the presentation layer, the session layer (Layer 6) will begin to create a connection to the other computer that the data is destined for. When a session is successfully created, data is divided into smaller pieces and sent bit by bit. Sessions are unique — data cannot travel over different sessions.

### ⑥ Presentation

This layer acts as a **standardisation** starts to take place. This layer acts as a translator for data to and from the application layer. Security features such as data **encryption** (e.g. HTTPS) take place at this layer.

### ⑦ Application Layer

Application layer is the layer in which protocols and rules are in place to determine how the user should interact with data sent or received. The application layer is the layer the user should interface with data sent or received.

---

## 5. Switches & Routers

### What is a Switch?

Switches are dedicated devices within a network that are designed to **aggregate multiple other devices** such as computers, printers, or any other networking-capable device using Ethernet.

Switches can connect a large number of devices by having ports of **4, 8, 16, 24, 32 and 64** devices to plug into.

```
            Internet
               |
           Router #1
          /          \
    Switch #1      Switch #2
    /  |  \        /  |  \
Devices...        Devices...
```

*Packets of data travel from one device to the next until they have reached their destination.*

---

### What is a Router?

It's a router's job to **connect networks and pass data between them**. It does this by using routing (hence the name "router").

- **Routing** is the label given to the process of data travelling across networks.
- Routing involves creating a path between networks so that this data can be successfully delivered.
- Routing is successful when devices are connected by many paths.

```
[Comp A] ←→ [Router] ←→ [Router] ←→ [Comp B]
               ↕                ↕
            [Router] ←→ [Router]
```

Different protocols will decide what path should be taken:
- What path is the **shortest**?
- What path is the most **reliable**?
- Which path has the **faster medium** (e.g. copper or fibre)?

---

## 6. Ports 101

Ports are an essential point in which data can be exchanged. When a connection has been established, any web data sent or received by a device is assigned by a standard rule. The value will be sent through between 0 and 65535. In computing, ports are a **minimal value** known as a **common port**.

### Common Protocols & Port Numbers

| Port | Protocol | Description |
|------|----------|-------------|
| 21 | **FTP** (File Transfer Protocol) | This protocol is used to pay for, download files from a central server location. |
| 22 | **SSH** (Secure Shell) | This protocol is used to securely login to systems using a client-server model, meaning you can download files from a central location. |
| 80 | **HTTP** (Hyper Text Transfer Protocol) | This protocol powers the World Wide Web (websites). |
| 443 | **HTTPS** (HTTP Secure) | This protocol does the exact same as above, however, is secondary to the security using encryption. |
| 445 | **SMB** (Server Message Block) | This protocol is similar to the FTP, as well as files SMB allows you to share files, well as fully SMB allows printers. |
| 3389 | **RDP** (Remote Desktop Protocol) | This protocol is used to securely login sharing built on a client-server model, meaning you can share data as well as fully SMB allows printers. It's also a means of logging into a system using a visual desktop interface. |

> Any port that is within 0 and 1024 is known as a **common port**.

---

## 7. ARP & DHCP

### Task 3 — ARP (Address Resolution Protocol)

**ARP** is the technology that is responsible for **allowing devices to identify themselves on a network**.

ARP allows a device to associate its **MAC address** with an **IP address** on the network.

#### How Does ARP Work?

ARP (Address Resolution Protocol) sends **two types of messages:**

1. **ARP Request**
2. **ARP Reply**

When an **ARP request** is sent, a message is broadcasted on the network to other devices asking: *"What is the MAC address that owns this IP address?"*

When the other devices receive that message, they will only respond if they own that IP address and will send an **ARP reply** with its MAC address. The requesting device can now remember this mapping and store it in its **ARP cache** for future use.

---

### Task 4 — DHCP (Dynamic Host Configuration Protocol)

**DHCP** automates the assignment of IP addresses on a network.

#### DHCP Process (4-Step Handshake)

```
[System]                              [DHCP Server]
   |                                       |
   |--- DHCP Discover ---------------------->|
   |  "Hey, I'm new here, is there          |
   |   anyone who can give me an IP?"       |
   |                                       |
   |<-- DHCP Offer ----------------------- |
   |            "Hey sure thing,            |
   |             you can have 192.168.1.10" |
   |                                       |
   |--- DHCP Request ---------------------->|
   |  "Yes, that would be brilliant!        |
   |   I'll start using 192.168.1.10"       |
   |                                       |
   |<-- DHCP Ack --------------------------|
   |  "Okay, great. You can use the IP      |
   |   address for the next 24 hours."      |
```

---

## 8. Subnetting

*(Date: 25/04/26 — A Primer on Subnetting)*

> A primer is a small introductory guide.

**Subnetting** is the term given to splitting up a network into smaller, miniature networks within itself.

Subnetting is like deciding who gets what slice and reserving such a slice of a metaphorical cake.

### Subnets use IP addresses in three different ways:

| Type | Purpose | Example |
|------|---------|---------|
| **Network Address** | Identifies the start of the actual network and is used to identify a network's existence. | `192.168.1.0` |
| **Host Address** | An IP address used to identify a device on the subnet. | `192.168.1.100` |
| **Default Gateway** | A special address assigned to a device on the network that is capable of sending information to another network. | `192.168.1.1` or `192.168.1.254` |

### Explanation

- A device with the IP address of **192.168.1.100** will be on the network identified by **192.168.1.0**
- Any data that needs to go to a device that isn't on the same network (i.e. isn't on 192.168.1.0) will be sent to this device (Default Gateway).
- These devices can use any host address but usually use either the **first or last host address** in a network (`.1 or .254`).

### Benefits of Subnetting

- ✅ **Efficiency**
- ✅ **Security**
- ✅ **Full Control**

---

## 9. VPN Technology & LAN Networking Devices

### VPN Technology

| Technology | Description |
|------------|-------------|
| **PPP** | This technology is used by PPTP to allow for authentication and provide encryption of data. This technology is **not** capable of leaving a network by itself (non-routable). |
| **PPTP** | The Point-to-Point Tunnelling Protocol (PPTP) is technology that allows the data from PPP to travel and leave a network. |
| **IPSec** | Internet Protocol Security (IPSec) encrypts data using the existing Internet Protocol (IP) framework. |

---

### LAN Networking Devices

#### What is a Router?
It's a router's job to connect networks and pass data between them. It does this by using routing (hence the name "router"). Routing is the label given to the process of data travelling across a network.
- Creates data path between networks.
- Operates at **Layer 3** of the OSI model.

Different protocols will decide what path should be taken:
- What path is the shortest?
- What path is the most reliable?
- Which path has the faster medium (e.g. copper or fibre)?

#### What is a Switch?
A switch is a dedicated networking device responsible for providing a means of connecting to multiple devices (from 3 to 63) using Ethernet cables.
- Operates at both **Layer 2 and Layer 3** of OSI.

#### VLAN
A technology called **VLAN** (Virtual Local Area Network) allows specific devices within a network to be **virtually split up**.

---

## 📚 Key Terminology Cheat Sheet

| Term | Definition |
|------|-----------|
| **Encapsulation** | The process of adding pieces of information to data at each OSI layer |
| **MAC Address** | A unique physical address used to identify a Network Interface Card |
| **IP Address** | A logical address used to identify a device on a network |
| **Routing** | The process of data travelling across networks |
| **Topology** | The design or layout of a network |
| **ARP Cache** | Storage for IP-to-MAC address mappings on a device |
| **DHCP Lease** | The time period for which an IP address is assigned to a device |
| **Backbone Cable** | The single cable used in a Bus topology |
| **NIC** | Network Interface Card — hardware that connects a device to a network |
| **TTL** | Time to Live — an expiry timer attached to packets |

---

*Notes compiled from classroom study materials. Topics covered: OSI Model, LAN Topologies, TCP/IP, Transport Layer Protocols, Switches & Routers, Ports, ARP, DHCP, Subnetting, and VPN.*
