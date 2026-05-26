# 🏠 Personal Homelab Infrastructure & Cluster Tracker

Welcome to my homelab repository. This space serves as the blueprint, hardware documentation, and tracking archive for my self-hosted home server network and testing clusters. 

I build and maintain this setup to host independent services, manage my own data securely, and experiment with backend infrastructure.

---

## 📅 Project Timeline & Milestone Logs

| Date | Phase | Focus & Milestones |
| :--- | :--- | :--- |
| **Dec 21, 2025** | Planning | Research phase. Spent most of the time sourcing and acquiring hardware components. |
| **Dec 24, 2025** | Network Setup | Sourced network hardware; started mapping and building the local network structure. |
| **Apr 09, 2026** | Core Assembly | All hardware arrived. Started physical assembly of the main server and secondary nodes. |
| **May 26, 2026** | Documentation | Current Phase. Starting full system tracking and mapping out the repository documentation. |

---

## 🛠️ Compute Hardware Architecture

### 🛡️ The Main Production Node (Main Server)
*This is the core workforce engine running my primary virtualized environments. It is built inside an open-frame case.*

* **CPU:** AMD Ryzen 5 5600G
* **Motherboard:** MSI B450-A Pro Max
* **Memory:** 32GB x1 SAMSUNG UDIMM
* **Storage:** 250GB SATA SSD
* **Power Supply:** Cooler Master 650W (80+ Bronze)
* **Chassis:** Open Frame Case
* **Primary OS Layer:** Proxmox VE (Hypervisor)

### 📈 Proxmox Cluster Backup Nodes
*These secondary machines are integrated into the environment primarily for failover clusters and automated TrueNAS storage backups.*

* **HP ProOne 400 G1:** Intel Core i5-4570T | 12GB RAM | 250GB SATA SSD | Intel HD Graphics 4600
* **Fujitsu Lifebook AH531:** Intel Core i5-2410M | 12GB RAM | 700GB HDD | Intel HD Graphics 3000

### 🧪 The Raspberry Pi Sandbox (Testing Ground Cluster)
*A dedicated 3-node physical cluster running Ubuntu Server Lite. It utilizes Docker Swarm and Kubernetes (K8s) frameworks purely for testing network scaling, Pi-hole redundancy, and Tailscale endpoints.*

* 1x Raspberry Pi 4 Model B (8GB RAM)
* 2x Raspberry Pi 4 Model B (4GB RAM)

---

## 🌐 Networking Hardware

* **Core Router:** TP-Link 300Mbps Multi-Mode Wi-Fi Router (`TL-WR844N`)
* **Switching Layer:** Mercusys 8-Port Gigabit Desktop Switch (`MS108G`)
* **ISP Gateway:** Huawei OptiXstar `EG8145X6-10` *(Configured to bridge mode; has no active use inside the core network)*

---

## ⚙️ Service & Software Ecosystem

### 🌐 Cloud & Tunneling Services (External Connections)
* **Playit.gg:** Premium tunneling service used for seamless server port-forwarding without exposing home public IPs.
* **Cloudflare:** Primary Domain Management, Cloudflare Tunnels, and web application hosting via Cloudflare Pages.
* **Tailscale:** Private Mesh VPN layer used for secure, encrypted remote access to the homelab from any outside device.
* **GitHub / GitLab:** Source control, logic archiving, and workflow pipelines.

### 🐳 Application Architecture & Running Configurations
*The main server runs Proxmox VE. All core services run inside an **Ubuntu Server VM**, handled via isolated Docker containers and supervised through Portainer.*

| Software / Platform | Purpose within the Environment |
| :--- | :--- |
| **AMP Panel (CubeCoders)** | Full-stack Minecraft server administration (Velocity networks, proxy balancing, MySQL backend databases). |
| **Docker & Portainer** | Containerized deployment runtime and visual web UI cluster management dashboard. |
| **Docker Swarm & K8s** | Container orchestration platforms utilized heavily across the Pi testing cluster. |
| **Coolify** | Open-source PaaS used for rapid self-hosted web deployments and database spin-ups. |
| **TrueNAS Core** | Dedicated network-attached storage configuration for system backup points. |
| **Ollama & Open WebUI** | Local, private AI language model deployment interface. |
| **Pi-hole** | Network-wide local DNS management and tracking domain sinkholes. |
| **Jellyfin & qBittorrent** | Media management system paired with an automated client for local media staging. |
| **aaPanel** | Standalone server engine utilized exclusively for a self-hosted local email configuration. |

---

## 📁 GitHub Project Directory Layout

```text
├── Project-picture/         # Visual media directory
│   ├── setup-pic/           # Screenshots and operational captures taken during active setup
│   └── hardware-pic/        # Physical pictures of the servers, components, and frame layout
│
├── Running-service/         # Infrastructure configuration vault
│   ├── website/             # Source files for my personal self-hosted websites
│   └── [Dockerfiles/Stacks] # Standard compose files, environment variables, and stack configurations
│
└── README.md                # Core documentation index
