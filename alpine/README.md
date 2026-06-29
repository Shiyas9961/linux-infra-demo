# Alpine Linux DevOps Automation

This directory contains Ansible playbooks and roles to configure an Alpine Linux virtual machine for a DevOps lab environment.

The automation prepares a lightweight Alpine installation with commonly used Linux utilities and Docker.

## Folder Structure

```text
alpine/
├── ansible.cfg
├── inventories/
│   └── lab/
│       ├── hosts.ini
│       └── group_vars/
│           └── all.yml
├── playbooks/
│   └── setup.yml
├── roles/
│   ├── common/
│   ├── docker/
│   └── security/
└── README.md
```

## Features

### Common Role

Installs commonly used Linux utilities.

Packages include:

- bash
- curl
- wget
- git
- vim
- nano
- htop
- tree
- openssh
- sudo
- ca-certificates
- shadow
- iproute2
- net-tools
- bind-tools
- rsync
- tar
- gzip
- unzip
- tzdata

Also performs:

- Configure official Alpine repositories
- Update package index
- Configure timezone

---

### Docker Role

Installs Docker from the official Alpine repositories.

Configuration includes:

- Docker Engine
- Docker CLI
- Docker Compose
- Docker service enabled
- Docker service started
- Automation user added to the Docker group

---

### Security Role

Configures basic system access.

Includes:

- Passwordless sudo (optional)
- SSH service enabled
- SSH service started
- Automation user added to the wheel group

---

## Requirements

Target Machine

- Alpine Linux 3.20+
- Python 3
- OpenSSH Server
- Passwordless sudo (recommended)

Controller Machine

- Ansible 2.16+
- SSH Key Authentication

---

## Inventory

Example:

```ini
[alpine]
alpine-vm ansible_host=192.168.56.101 ansible_user=ansible ansible_ssh_private_key_file=~/.ssh/proxmox-server
```

---

## Verify Connection

```bash
ansible alpine -m ping
```

Expected output:

```text
alpine-vm | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

---

## Run Automation

```bash
ansible-playbook playbooks/setup.yml
```

---

## Verify Docker

```bash
docker --version
docker compose version
docker run hello-world
```

---

## Verify Services

```bash
rc-service docker status
rc-service sshd status
```

---

## Notes

- Uses the Alpine package manager (`apk`).
- Uses OpenRC instead of systemd.
- Intended for lightweight container hosts and Linux administration practice.
- GitHub Actions self-hosted runners are **not officially supported** on Alpine because they depend on glibc, while Alpine uses musl libc.

---

## Future Enhancements

This automation will be extended with:

- Nginx
- Kubernetes
- Monitoring Stack
- Security Hardening
- Reverse Proxy
- Container Registry Integration

## License

MIT License