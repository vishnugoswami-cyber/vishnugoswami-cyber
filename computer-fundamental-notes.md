# Tech Fundamentals — Study Notes

---

## Table of Contents
1. [Inside a Computer System](#1-inside-a-computer-system)
2. [What Happens When We Press the Start Button](#2-what-happens-when-we-press-the-start-button)
3. [Computer Types](#3-computer-types)
4. [Virtualization](#4-virtualization)
5. [Virtual Machines & Containers](#5-virtual-machines--containers)
6. [Cloud Computing](#6-cloud-computing)
7. [Major Cloud Vendors](#7-major-cloud-vendors)
8. [Client-Server Basics](#8-client-server-basics)

---

## 1. Inside a Computer System

Each part has its own job, and together they make the computer work.

**The building blocks are:**

| Component | Role |
|-----------|------|
| Motherboard | The Skeleton and Nerves |
| RAM | Short-term Memory |
| PSU | Heart and Lungs |
| HDD + SDD | Long-term Memory |
| GPU | Visual Cortex |
| CPU | The Brains |

---

## 2. What Happens When We Press the Start Button?

Below are the steps a computer system goes through before it shows you a working interface.

**Flow:**
> Press Power Button → Firmware Starts → POST → Select Boot Device → Start Bootloader

### Step 1 — Press the Power Button
When we press the power button on our computer system, a signal is sent to the PSU to allow power to flow.

### Step 2 — Firmware Starts
A computer system contains firmware that allows all its components to start up. The central system that manages this is called the **Unified Extensible Firmware Interface (UEFI)**.

> **NOTE:** We will often see the term **BIOS** mentioned instead of UEFI. BIOS does the same thing as UEFI but has mainly been replaced by UEFI.

### Step 3 — Power-On Self Test (POST)
One of the routines that the UEFI loads is the Power-On Self Test, which tests if every required component is present, configured correctly, and functioning.

### Step 4 — Select Boot Device
The UEFI holds an ordered list which prioritizes which device to look first for the boot-up routine for the Operating System.

### Step 5 — Initiate Bootloader
On the selected boot device, the bootloader is initiated. This bootloader transfers the Operating System from the selected boot device to the Random Access Memory. Once the OS is transferred, the UEFI gives control over the different components to the OS.

---

## 3. Computer Types

Four types of computers that often look similar but serve very different purposes.

| Computer Type | Screen & Keyboard | Main Purpose |
|---------------|:-----------------:|--------------|
| Laptop | Yes | Portable everyday computing |
| Desktop | Yes | Sustained performance at a fixed location |
| Workstation | Yes | Precision and reliability for professional tasks |
| Server | No | Providing services to many users over a network |

The most powerful computer most people own fits in their pocket, but millions more hide inside everyday objects — doors, lamps, coffee machines.

### Embedded & Special-Purpose Computers

| Type | What it is | Examples |
|------|-----------|---------|
| Smartphone | Pocket-sized computer optimized for battery life and connectivity | iPhones, Android phones |
| Tablet | Touch-first computer with a larger screen | iPad, drawing tablet |
| IoT Devices | Network-connected device with a single purpose | Thermostat, smart doorbell, fitness tracker |
| Embedded Computer | Computer built into another device | Coffee maker controller, automatic door sensor, lamp dimmer chip |

---

## 4. Virtualization

Before virtualization, the rule of thumb in IT was:

> **"One Server = One Application"**

In the early days, digital services were run on physical machines, and each machine typically had a single, clear purpose — such as hosting a website or storing data. This meant separate physical servers for each service. The problems were obvious:

- High Cost
- Low Utilization
- Slow Development
- Hard to Scale

### The Solution

Virtualization introduced a new idea:

> **"What if multiple applications could share the same physical server safely?"**

A **hypervisor** was introduced to act as a referee between virtual machines — allowing each virtual computer to behave independently, like a physical computer.

### The Building Analogy

| Element | Represents |
|---------|-----------|
| The building | The physical server |
| The apartments | Virtual machines |
| The tenants | Applications or operating systems |
| The building manager | The hypervisor |

Each virtual computer, known as a **Virtual Machine (VM)**, acts as an independent system with its own operating system, apps, and settings — even though they all share the same physical hardware underneath.

### Types of Hypervisors

- **Type 1 Hypervisor** — Runs directly on the physical hardware. Fast, efficient, and ideal for servers and professional environments.
- **Type 2 Hypervisor** — Runs within an existing operating system. Easier to install and ideal for learning, testing, or small setups.

---

## 5. Virtual Machines & Containers

| | Virtual Machine (VM) | Container |
|-|---------------------|-----------|
| **What it is** | A virtual computer created by the hypervisor | A lightweight, isolated environment that runs a single application |
| **Includes** | Its own full operating system | Only the app and its dependencies |
| **Size** | Heavier | Lightweight |
| **Best for** | Running different operating systems | Running multiple instances of an application |

---

## 6. Cloud Computing

Cloud computing is the delivery of computing services — servers, storage, databases, networking, software — over the internet.

### Benefits of Cloud Computing

- **Scalability** — Scale resources up or down based on demand
- **On-demand Self-Service** — Provision resources without human intervention
- **Pay Only for What You Use** — Cost-efficient consumption model
- **Security** — Built-in security tools and compliance features
- **High Availability** — Services remain accessible even during failures
- **Global Access** — Access from anywhere in the world

### Types of Cloud

| Type | Best Used By |
|------|-------------|
| **Public Cloud** | Startups and global applications |
| **Private Cloud** | Banks, healthcare, and government organizations |
| **Hybrid Cloud** | E-commerce platforms and enterprises |

### Cloud Service Models

#### IaaS — Infrastructure as a Service
You rent basic computing resources such as virtual servers, storage, and networking. You manage the operating system and your application; the provider manages the physical hardware.

#### PaaS — Platform as a Service
The cloud provider manages the infrastructure and the operating system. You focus only on building, deploying, and running your application.

#### SaaS — Software as a Service
You use a complete application over the internet. The provider manages everything, and you access the software through a browser or app (e.g., Gmail, Zoom).

---

## 7. Major Cloud Vendors

There are several cloud vendors offering a variety of services. **Amazon Web Services (AWS)** is the industry leader, with the most extensive offerings and global reach.

Other well-known providers include:

- **Microsoft Azure**
- **Google Cloud Platform (GCP)**
- **Alibaba Cloud**
- **IBM Cloud**
- **Oracle Cloud**

---

## 8. Client-Server Basics

Multiple organizations around the world started with the idea of interconnecting their systems to facilitate information exchange and resource sharing regardless of distance. Networks such as ARPANET, CYCLADES, and NSFNET paved the way for the modern internet.

- The **browser** is the client — it requests the webpage.
- The **server** is the system that serves it.

### Protocol
A protocol defines how a client can communicate with a server. This definition includes:
- Which commands the client and server understand
- How a request is structured
- What syntax is used
- What response should be given to which type of request
- What response to give to faulty requests

### Port
A port identifies a specific service running on a system. When a client wants to access a service on a server, it must connect using the correct port.

### DNS — Domain Name Service
When you enter the name of a website, DNS resolves it to the server's IP address location. These location coordinates are called an **Internet Protocol (IP) address** in computer terms.

### HTTP(S)
**Hypertext Transfer Protocol (Secure)** — abbreviated as HTTPS — is a stateless client-server protocol used for the World Wide Web. Stateless means each request is processed independently, without the server retaining information about previous requests.

### HTTP Methods (Commands)
There are 9 core HTTP methods defined in the main HTTP specifications (also called RFC documents):

| Method | Purpose |
|--------|---------|
| **GET** | Retrieve a resource from a web server |
| **POST** | Send data to create a new resource |
| **PUT** | Replace an existing resource |
| **PATCH** | Partially update an existing resource |
| **DELETE** | Remove a resource |
| **HEAD** | Same as GET but returns headers only |
| **OPTIONS** | Describes communication options for a resource |
| **CONNECT** | Establishes a tunnel to the server |
| **TRACE** | Performs a message loop-back test |

---

*Notes compiled from handwritten study notes — Computer Fundamentals, Virtualization, Cloud Computing & Client-Server Basics.*
