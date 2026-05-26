# 🏠 My Homelab 

Welcome to my homelab repository. hardware documentation, and archive for my home server network and testing clusters. 

---

## 📅 Project Timeline

| Date | Phase | info |
| :--- | :--- | :--- |
| **Dec 21, 2025** | Planning | Spent most of the time geting my hand on hardware. |
| **Dec 24, 2025** | Network Setup | network hardware; started building local network structure. |
| **Apr 09, 2026** | Main Setup | All hardware arrived. Started building main server and secondary nodes. |
| **May 26, 2026** | Documentation | Current Phase. mapping out the repository documentation. |

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

### 🧪 Raspberry Pi Testing Cluster
*A dedicated 3-node physical cluster running Ubuntu Server Lite. It utilizes Docker Swarm and Kubernetes (K8s) frameworks purely for testing network scaling, Pi-hole redundancy, and Tailscale endpoints.*

* 1x Raspberry Pi 4 Model B (8GB RAM)
* 2x Raspberry Pi 4 Model B (4GB RAM)

---

## 🌐 Networking Hardware

* **main Router:** TP-Link 300Mbps Multi-Mode Wi-Fi Router (`TL-WR844N`)
* **Switching hub:** Mercusys 8-Port Gigabit Desktop Switch (`MS108G`)
* **ISP router:** Huawei OptiXstar `EG8145X6-10` *(Configured to bridge mode; has no active use inside the core network)*

---

## ⚙️ Service & Software i use 

###  Cloud & Tunneling Services (External Connections)
* **Playit.gg:** Premium tunneling service used for server port-forwarding without exposing home public IPs.
* **Cloudflare:** Domain Management, Cloudflare Tunnels, Cloudflare Pages.
* **Tailscale:** Private VPN layer used for remote access to the homelab from any outside network.
* **GitHub / GitLab:** Source archiving.

### 🐳 Application Architecture & Running Configurations
*The main server runs Proxmox VE. All services run inside an **Ubuntu Server VM**, Docker containers and Portainer.*

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
### Disclaimer & Credits
I did not write some of the Docker Compose configuration used in this project. All credits for the setup and original code go entirely to the original creator. This repository is personal archive and portfolio

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

