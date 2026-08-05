# Security Baseline

## Objective

This document defines the minimum security baseline for the Home Server.

The goal is to reduce exposure, protect administrative access, prevent accidental disclosure of sensitive information, and maintain a recoverable environment.

## Security Principles

- Use the principle of least privilege.
- Do not expose unnecessary services to the public internet.
- Keep operating system packages and container images updated.
- Store credentials outside public repositories.
- Use secure remote access mechanisms.
- Document security-related changes and incidents.

## Remote Access

### SSH

SSH is used for remote server administration.

Recommended baseline:

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
AllowUsers YOUR_LINUX_USER
```

Administrative access should use SSH keys instead of passwords whenever possible.

Recommended verification commands:

```bash
sudo systemctl status ssh
sudo sshd -T
```

### Tailscale

Tailscale is used or evaluated as the preferred method for remote connectivity.

Benefits:

- Private access without exposing SSH directly to the public internet.
- Encrypted communication between authorized devices.
- Reduced dependency on port forwarding.
- Simplified remote administration.

## Firewall

The server should allow only required services.

Example UFW baseline:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw enable
sudo ufw status verbose
```

Firewall rules must be reviewed before applying changes remotely to avoid losing SSH access.

## Secrets Management

The following files and folders must never be committed to GitHub:

```text
.env
credentials/
data/
*.log
private keys
API tokens
database passwords
backup archives
```

The `.gitignore` file is used to exclude sensitive material from version control.

## Docker Security

- Use official or trusted container images.
- Keep images updated.
- Avoid running containers as root when possible.
- Do not store secrets directly inside Dockerfiles.
- Use environment variables or external secret files excluded by `.gitignore`.
- Review exposed container ports before deployment.

Useful commands:

```bash
docker ps
docker images
docker inspect CONTAINER_NAME
docker compose config
```

## Updates and Patch Management

| Activity | Frequency |
|---|---|
| Review available system updates | Weekly |
| Apply security updates | Weekly or as needed |
| Review Docker image updates | Monthly |
| Review enabled services | Monthly |
| Review firewall rules | Monthly |
| Validate remote access | Monthly |

Recommended commands:

```bash
sudo apt update
apt list --upgradable
docker image ls
```

## Backups and Recovery

Security also requires recoverability.

The Home Server should maintain backups of:

- Important Docker Compose files.
- Service configurations.
- System documentation.
- Automation project code.
- Operational data stored outside this public repository.

Backup files must be encrypted when they contain sensitive information.

## Incident Response Notes

If suspicious activity, service failure, or unauthorized access is detected:

1. Identify the affected service or account.
2. Review relevant logs.
3. Restrict access if necessary.
4. Change exposed credentials or keys.
5. Document the incident and corrective action.
6. Validate that services are operating securely after remediation.

## Repository Safety

This public repository contains documentation and sanitized examples only.

It does not contain real IP addresses, business data, credentials, tokens, SSH keys, Docker secrets, or backup files.
