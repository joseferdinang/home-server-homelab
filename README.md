# Home Server / Home Lab

[![Linux](https://img.shields.io/badge/Linux-Debian_13-A81D33?style=flat-square&logo=debian&logoColor=white)](https://www.debian.org/)
[![Docker](https://img.shields.io/badge/Docker-Containerized_Services-2496ED?style=flat-square&logo=docker&logoColor=white)](https://www.docker.com/)
[![Python](https://img.shields.io/badge/Python-Automation-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Status](https://img.shields.io/badge/Status-Active-success?style=flat-square)](#)

## Overview

This repository documents my Home Server / Home Lab project, designed to strengthen practical skills in Linux administration, Docker, Python automation, networking, secure remote access, and technical documentation.

The server supports Python projects, containerized services, a small operational file storage environment, and continuous learning in infrastructure and data-oriented automation.

## Objectives

- Run Python automation projects.
- Deploy and manage Docker containers.
- Provide secure remote administration through SSH.
- Enable private remote access through Tailscale.
- Document configurations, incidents, improvements, and operational procedures.
- Optimize energy use while maintaining stable services.
- Build a technical portfolio focused on infrastructure and data.

## Architecture

```text
                           Internet
                              |
                    Secure remote access
                         Tailscale VPN
                              |
                    Router / Firewall LAN
                              |
                    192.168.1.X/24
                              |
                    +------------------+
                    | Home Server      |
                    | Debian 13        |
                    | Intel Core i5    |
                    | Docker / Python  |
                    +------------------+
                     |       |       |
                     |       |       |
                   SSH    Docker    Storage
                     |       |       |
            Administration  Automation  Operational
               and support   projects    files
```

## Hardware

| Component | Specification |
|---|---|
| Processor | Intel Core i5-2400 |
| CPU | 4 cores / 4 threads |
| Memory | Approximately 6 GB RAM |
| Storage | SSD, approximately 224 GB |
| Network | Gigabit Ethernet |
| Graphics | Integrated Intel graphics |
| Operating system | Debian 13 |

## Services

| Service | Purpose | Status |
|---|---|---|
| Debian 13 | Base operating system | Active |
| Docker Engine | Container execution | Active |
| Docker Compose | Reproducible service deployments | Active |
| SSH | Secure remote administration | Active |
| Tailscale | Private remote connectivity | In validation |
| Python | Automation and data processing | Active |
| Seguricon Contabilidad | Python-based Docker automation project | Active |
| Local storage | Operational files and backups | In progress |

## Docker Project

The server runs a Python automation project using Docker.

```text
seguricon-contabilidad/
├── main.py
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
├── handlers/
├── tests/
├── data/
└── credentials/
```

Sensitive folders and files must never be uploaded to GitHub.

```gitignore
.env
credentials/
data/
*.log
__pycache__/
venv/
```

## Energy Efficiency Strategy

This Home Server uses older hardware, so efficient and stable operation is a priority.

Current and planned measures:

- Dedicated AMD graphics card removed to reduce power consumption.
- Integrated Intel graphics used instead of a dedicated GPU.
- Energy profiles evaluated with TLP.
- Power consumption reviewed with PowerTOP.
- Unnecessary startup services disabled.
- Docker used to isolate and simplify service management.
- Periodic monitoring of CPU, memory, storage, and container usage.

Recommended verification commands:

```bash
sudo powertop
sudo tlp-stat -s
uptime
free -h
df -h
docker stats
systemctl --type=service --state=running
```

## Security Principles

- SSH access should use key-based authentication.
- Direct root access through SSH should remain disabled.
- Remote access should use Tailscale instead of exposing unnecessary services.
- Passwords, API tokens, private keys, and business data must remain outside the repository.
- Operating system and Docker images should be updated regularly.
- Important configurations should be backed up and tested.

Example SSH hardening settings:

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
AllowUsers YOUR_LINUX_USER
```

## Roadmap

- [ ] Document server network topology.
- [ ] Validate Tailscale remote access.
- [ ] Implement automated encrypted backups.
- [ ] Add uptime and resource monitoring.
- [ ] Configure alerts for storage, temperature, and service failures.
- [ ] Create incident response notes.
- [ ] Add automated tests for Python projects.
- [ ] Implement GitHub Actions for code validation.
- [ ] Evaluate Proxmox after future hardware upgrades.

## Author

José Alfredo Ferdinand Gallardo  
Analista de Sistemas TI | Linux, Docker, Python, SQL y Análisis de Datos
