# Energy Optimization

## Objective

This document records the measures applied to reduce energy consumption and improve operational efficiency in the Home Server.

The objective is to maintain a stable Linux environment for Docker, Python automation, SSH administration, and storage tasks while minimizing unnecessary power usage.

## Baseline Context

The Home Server is built on an Intel Core i5-2400 platform. Because this is older hardware, power efficiency is an important operational consideration.

The server is intended to remain available for long periods, making energy optimization relevant for both cost control and hardware longevity.

## Implemented Measures

### Dedicated GPU Removal

A dedicated AMD Radeon graphics card was removed from the server.

This change reduces idle power consumption, heat generation, and unnecessary hardware complexity. The server now relies on integrated Intel graphics for local console access.

### TLP Power Management

TLP is used to review and apply Linux power management settings.

Recommended validation command:

```bash
sudo tlp-stat -s
```

### PowerTOP Analysis

PowerTOP is used to identify power consumption patterns and available system tunings.

Recommended commands:

```bash
sudo powertop
sudo powertop --csv=powertop-report.csv
```

The CSV report can be used later to compare power-related metrics over time.

### Service Management

Only required services should remain enabled at startup.

Useful commands:

```bash
systemctl --type=service --state=running
systemctl list-unit-files --state=enabled
```

Unused services should be reviewed before disabling them to avoid affecting Docker, SSH, networking, or storage operations.

## Monitoring Checklist

| Area | Command or Tool | Review Frequency |
|---|---|---|
| CPU and load | `uptime` | Weekly |
| Memory usage | `free -h` | Weekly |
| Storage capacity | `df -h` | Weekly |
| Docker resources | `docker stats` | After deploying services |
| Power tunings | `sudo powertop` | Monthly |
| TLP status | `sudo tlp-stat -s` | Monthly |
| Running services | `systemctl --type=service --state=running` | Monthly |

## Future Improvements

-- [ ] Record idle power consumption in watts.
- [ ] Compare consumption before and after optimization measures.
- [ ] Create a scheduled health report for CPU, RAM, disk, and Docker containers.
- [ ] Evaluate BIOS power-saving settings.
- [ ] Add temperature monitoring.
- [ ] Add UPS protection for safe shutdown during power outages.
- [ ] Define energy consumption thresholds for future upgrades.

## Technical Notes

Energy optimization must not compromise security, backups, SSH availability, Docker services, or network connectivity.

Any change to power settings should be documented and validated after implementation.
