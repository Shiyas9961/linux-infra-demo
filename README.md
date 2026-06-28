# Alpine DevOps Setup

Ansible automation for preparing an Alpine Linux VirtualBox VM for DevOps practice.

## Features

- Installs common Linux tools
- Installs Python and pip
- Installs Docker and Docker Compose
- Enables SSH
- Configures sudo access
- Adds user to Docker group

## VM Requirement

Alpine VM should have a static host-only IP, for example:

```bash
192.168.56.101