# Infrastructure Monitoring Lab with Prometheus & Grafana

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-E95420?logo=ubuntu&logoColor=white)](https://ubuntu.com/)
[![Prometheus](https://img.shields.io/badge/Prometheus-2.50+-E6522C?logo=prometheus&logoColor=white)](https://prometheus.io/)
[![Grafana](https://img.shields.io/badge/Grafana-10.0+-F46800?logo=grafana&logoColor=white)](https://grafana.com/)

> 

---
<p align="left">
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" alt="Ubuntu" />
  <img src="https://img.shields.io/badge/VirtualBox-183A61?style=for-the-badge&logo=virtualbox&logoColor=white" alt="VirtualBox" />
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" />
  <img src="https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white" alt="Prometheus" />
  <img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white" alt="Grafana" />
  <img src="https://img.shields.io/badge/Linux_Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white" alt="Bash" />
</p>
## 📌 Overview

This project represents a complete, self-contained monitoring laboratory designed to simulate a real-world production environment. As an aspiring DevOps/System Operations professional, I built this lab to bridge the gap between theoretical knowledge and practical implementation of modern observability stacks.

The infrastructure demonstrates competency across multiple critical domains:

- **Virtualization**: Orchestration of guest VMs using Oracle VirtualBox on a Windows host
- **Linux System Administration**: Headless Ubuntu Server 22.04 LTS management via SSH
- **Container Orchestration**: Docker Compose for multi-service application deployment
- **Monitoring & Observability**: End-to-end metrics collection, storage, and visualization pipeline
- **Networking**: Port forwarding, service exposure, and IPv4/IPv6 troubleshooting

---

## 🏗️ Architecture Overview

```text
                               PHYSICAL HOST (Windows 11)
                               ┌──────────────────────────────────┐
                               │  Hardware: Ryzen 7 6800H, 16GB  │
                               │  Terminal: PowerShell / SSH     │
                               │                                  │
                               │  ┌────────────────────────────┐ │
                               │  │    Oracle VM VirtualBox    │ │
                               │  │                            │ │
                               │  │  ┌──────────────────────┐ │ │
                               │  │  │   Ubuntu 22.04 VM    │ │ │
                               │  │  │  2 vCPUs | 4GB RAM  │ │ │
                               │  │  │  25GB Disk          │ │ │
                               │  │  │                      │ │ │
                               │  │  │  ┌───────────────┐  │ │ │
                               │  │  │  │ Docker Engine │  │ │ │
                               │  │  │  │  & Compose    │  │ │ │
                               │  │  │  └───────┬───────┘  │ │ │
                               │  │  │          │          │ │ │
                               │  │  │  ┌───────▼───────┐  │ │ │
                               │  │  │  │  Node       │  │ │ │
                               │  │  │  │  Exporter   │  │ │ │
                               │  │  │  │  :9100      │  │ │ │
                               │  │  │  └───────┬───────┘  │ │ │
                               │  │  │          │          │ │ │
                               │  │  │  ┌───────▼───────┐  │ │ │
                               │  │  │  │  Prometheus  │  │ │ │
                               │  │  │  │  :9090       │──┼─┼─┼─► Host:9090
                               │  │  │  └───────┬───────┘  │ │ │
                               │  │  │          │          │ │ │
                               │  │  │  ┌───────▼───────┐  │ │ │
                               │  │  │  │   Grafana    │  │ │ │
                               │  │  │  │   :3000      │──┼─┼─┼─► Host:3000
                               │  │  │  └───────────────┘  │ │ │
                               │  │  └──────────────────────┘ │ │
                               │  └────────────────────────────┘ │
                               └──────────────────────────────────┘
```
## Screenshots & Verification

<div align="center">

### Real-Time Infrastructure Dashboard (Grafana - ID: 1860)
![Grafana Dashboard](images/grafana-dashboard.png)

<br/>

### Target Discovery & Scraping State (`State: UP`)
![Prometheus Targets](images/prometheus-targets.png)

</div>
## Key Metrics Monitored

| Category | Prometheus Metric | Operational Purpose |
| :--- | :--- | :--- |
| **CPU Utilization** | `node_cpu_seconds_total` | Tracks execution mode distribution (User, System, Idle, I/O Wait) |
| **Memory Allocation** | `node_memory_MemAvailable_bytes` | Monitors actual available memory, cached buffers, and swap activity |
| **Storage & I/O** | `node_disk_io_time_seconds_total` | Evaluates disk read/write latency and root filesystem capacity (`/`) |
| **Network Traffic** | `node_network_receive_bytes_total` | Analyzes ingress and egress throughput across network interfaces |
| **Host Availability** | `node_boot_time_seconds` | Verifies instance uptime, boot integrity, and host health states |
