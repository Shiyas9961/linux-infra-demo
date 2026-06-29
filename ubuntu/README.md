# Ubuntu DevOps Automation

This directory contains Ansible playbooks and roles to configure an Ubuntu Server for a DevOps lab environment.

The automation prepares a clean Ubuntu installation with commonly used tools and Docker.

## Folder Structure

```text
ubuntu/
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
│   └── docker/
└── README.md
```

## Features

### Common Role

Installs commonly used Linux utilities.

Packages include:

- curl
- wget
- git
- vim
- nano
- unzip
- zip
- tree
- htop
- jq
- net-tools
- iproute2
- dnsutils
- traceroute
- tcpdump
- rsync
- openssh-server
- software-properties-common
- apt-transport-https

Also performs:

- Package update
- Package upgrade
- Timezone configuration
- SSH service enablement

---

### Docker Role

Installs the latest Docker Engine from the official Docker repository.

Includes:

- Docker CE
- Docker CLI
- Containerd
- Docker Buildx
- Docker Compose Plugin

Configuration:

- Docker service enabled
- Docker service started
- Automation user added to docker group

---

## Requirements

Target Machine

- Ubuntu Server 22.04 or newer
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
[ubuntu]
ubuntu-vm ansible_host=192.168.56.102 ansible_user=ansible ansible_ssh_private_key_file=~/.ssh/proxmox-server
```

---

## Verify Connection

```bash
ansible ubuntu -m ping
```

Expected output:

```text
ubuntu-vm | SUCCESS => {
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
systemctl status docker
systemctl status ssh
```

---

## Future Enhancements

This automation will be extended with:

- Kubernetes
- Helm
- Nginx
- GitHub Actions Runner
- Monitoring Stack
- Security Hardening

## License

MIT License