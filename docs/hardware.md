# Hardware Inventory

## Purpose

This document records the physical hardware used by the Home Server. The objective is to maintain an accurate inventory, understand current capacity limits, and support future upgrade decisions.

## Current Configuration

| Component | Specification | Operational Role |
|---|---|---|
| Processor | Intel Core i5-2400 @ 3.10 GHz | Docker workloads, Python automation, Linux services |
| CPU Architecture | 4 cores / 4 threads | Small-scale self-hosted services |
| Memory | Approximately 6 GB RAM | Operating system, Docker containers, automation processes |
| Storage | Approximately 224 GB SSD | Debian system, Docker volumes, project files |
| Network Adapter | Intel 82579LM Gigabit Ethernet | Wired LAN connectivity |
| Graphics | Integrated Intel graphics | Console and basic system display |
| Operating System | Debian 13 | Server operating system |

## Workload Profile

The current hardware is designed for low-to-medium workloads:

- Python automation projects.
- Docker containers with controlled resource usage.
- SSH administration.
- Secure remote access through Tailscale.
- Small operational file storage.
- Technical experimentation with Linux, networking, and monitoring.

## Capacity Considerations

The Intel Core i5-2400 is sufficient for the current Home Server scope. The primary limitation is memory capacity, especially when running multiple Docker containers, monitoring tools, or future virtualization workloads.

## Upgrade Priorities

| Priority | Improvement | Reason |
|---|---|---|
| High | Upgrade RAM to at least 16 GB | Improve Docker capacity and enable additional services |
| High | Add a second drive for backups | Reduce risk of data loss from a single storage device |
| Medium | Add a larger SSD or HDD | Support backup retention and file storage growth |
| Medium | Add UPS protection | Maintain safe shutdown capability during power outages |
| Low | Evaluate Proxmox | Consider only after increasing RAM and storage capacity |

## Maintenance Notes

- Monitor disk health periodically.
- Keep the server clean and ensure adequate airflow.
- Verify available storage capacity before deploying new services.
- Review CPU and memory usage after adding Docker containers.
- Document all hardware changes in this file.

## Security Note

This repository intentionally excludes serial numbers, MAC addresses, real IP addresses, credentials, and internal network details.


