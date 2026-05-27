# 🏠 My Homelab 

Welcome to my homelab repository this is hardware documentation, and archive for my home server network.

---

## 📅 Project Timeline

| Date | Phase | info |
| :--- | :--- | :--- |
| **Dec 21, 2025** | Planning | Spent most of the time geting my hand on hardware. |
| **Dec 24, 2025** | Network Setup | network hardware; started building local network structure. |
| **Apr 09, 2026** | Main Setup | All hardware arrived. Started building main server and secondary nodes. |
| **May 26, 2026** | Documentation | Current Phase. mapping out the repository documentation. |

## 🚀 Future Goals

### 🌐 Networking
* Install a **10GB SFP+ card** in Ryzen server.
* Upgrade to a new, fully managed network switch.
* dedicated Mini PC running **OPNsense** or **pfSense** as the main server router.

### 💻 Compute & Clustering
* Build a **second Ryzen server node** to expand cluster.
* Rebuild Proxmox cluster into a better bigger cluster:
  > * Ryzen Server 1 *(Completed)*
  > * Ryzen Server 2 *(Planned)*
  > * Mini PC Node 1 *(Planned)*
  > * Mini PC Node 2 *(Planned)*
* dedicated physical **TrueNAS server** build.
* KVM for all node.
* install Ryzen server with a **dedicated GPU** run **Ollama** and AI workloads.

---

## 🛠️ Compute Hardware

### Main Node (Main Server)
*This is the main server.*

* **CPU:** AMD Ryzen 5 5600G
* **Motherboard:** MSI B450-A Pro Max
* **Memory:** 32GB x1 SAMSUNG UDIMM
* **Storage:** 250GB SATA SSD
* **Power Supply:** Cooler Master 650W (80+ Bronze)
* **Chassis:** Open Frame Case
* **Primary OS Layer:** Proxmox VE (Hypervisor)

### Proxmox Cluster Backup Nodes
*These are backup clusters and automated TrueNAS storage backups.*

* **HP ProOne 400 G1:** Intel Core i5-4570T | 12GB RAM | 250GB SATA SSD | Intel HD Graphics 4600
* **Fujitsu Lifebook AH531:** Intel Core i5-2410M | 12GB RAM | 700GB HDD | Intel HD Graphics 3000

### Raspberry Pi Testing Cluster

* 1x Raspberry Pi 4 Model B (8GB RAM)
* 2x Raspberry Pi 4 Model B (4GB RAM)

---

## 🌐 Networking Hardware

* **main Router:** TP-Link 300Mbps Multi-Mode Wi-Fi Router (`TL-WR844N`)
* **Switching hub:** Mercusys 8-Port Gigabit Desktop Switch (`MS108G`)
* **ISP router:** Huawei OptiXstar `EG8145X6-10` *(Configured to bridge mode; has no active use inside the core network)*

---

## ⚙️ Service & Software i use 

###  Cloud & Tunneling (External Connections)
* **Playit.gg:** Premium tunneling service used for server port-forwarding without exposing home public IPs.
* **Cloudflare:** Domain Management, Cloudflare Tunnels, Cloudflare Pages.
* **Tailscale:** Private VPN layer used for remote access to the homelab from any outside network.
* **GitHub / GitLab:** Source , archiving.

| Software / Platform | info |
| :--- | :--- |
| **AMP Panel (CubeCoders)** | Full-stack Minecraft server (Velocity networks, MySQL backend databases). |
| **Docker & Portainer** | Container deployment and visual web UI dashboard. |
| **Docker Swarm & K8s** | Container for Pi testing cluster. |
| **Coolify** | Open-source self-hosted web deployments and databass. |
| **TrueNAS Core** | network-attached storage for system backup points. |
| **Ollama & Open WebUI** | Local, private AI language model and interface. |
| **Pi-hole** | Network-local DNS management and tracking domain. |
| **Jellyfin & qBittorrent** | Media server system. |
| **aaPanel** | server engine for a self-hosted local email server. |


---
## Cluster Configurations

### Network Diagram
```text
┌──────────────────────────────┐
│  Huawei OptiXstar (Bridge)   │  [ISP Input]
└──────────────┬───────────────┘
               │ (RJ45 Ethernet)
 ┌─────────────▼─────────────┐
 │    TP-Link TL-WR844N      │  [server Router]
 └─────────────┬─────────────┘
               │
 ┌─────────────▼─────────────┐
 │    Mercusys MS108G        │  [8-Port Gigabit Switch]
 └─┬──────┬──────┬──────┬────┘
   │      │      │      │
   │      │      │      └─► [3x Raspberry Pi Testing Cluster]
   │      │      └────────► [Fujitsu Lifebook Backup Node]
   │      └───────────────► [HP ProOne Backup Node]
   └──────────────────────► [Proxmox Ryzen Main Server]

```

## 🖥️ Hypervisor Layout

### 1. Proxmox 3-Node Cluster (Main Stack - 24/7)

#### **Proxmox Ryzen Server (`10.0.0.103`)**
* ── **Ubuntu Server VM 100 (`10.0.0.104`)**
  * 📦 AMP Panel
  * 📦 Playit.gg Connector
  * 📦 Mango SMP Proxy
  * 📦 MySQL Database *(LuckPerms configuration sync)*
* ── **Ubuntu Server VM 101 (`10.0.0.105`)**
  * 📦 Docker / Portainer Core
  * 📦 Coolify Deployment Engine
  * 📦 Ollama Engine + Open WebUI
* ── **Ubuntu Server VM 102 (`10.0.0.106`)**
  * 📦 Docker / Portainer Testing Environment
* ── **TrueNAS VM 103**
  * 📦 Local NAS Storage

#### **Backup Nodes (Emergency backup)**
* **Proxmox Fujitsu Lifebook**
* **Proxmox HP ProOne**

---

### 2. Raspberry Pi Cluster (On-Demand Dev Environment)
*Docker Swarm & K8s; not kept online 24/7.*

* ── **Pi 1 Node**
  * aaPanel *(Mail Server)*
* ── **Pi 2 Node**
  * Pi-hole Backup DNS
  * Tailscale
* ── **Pi 3 Node**
  * worker node


---

## 📁 GitHub Project Layout

```text
├── Project-picture/         # media directory
│   ├── setup-pic/           # Screenshots and pic taken during active setup
│   └── hardware-pic/        # Physical pictures of the servers, components, and layout
│
├── Running-service/         # Infrastructure configuration vault
│   ├── website/             # Source files for my websites
│   └── [Dockerfiles]        # Standard compose files, environment variables, and stack configurations
│
└── README.md                # documentation index
```

---
## Disclaimer & Credits
I did not write some of the Docker Compose configuration used in this project. All credits for the setup and original code go entirely to the original creator. This repository is personal archive and portfolio
