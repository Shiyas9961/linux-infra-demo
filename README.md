# DevOps Automation

This repository contains Ansible automation for provisioning and configuring Linux virtual machines used in a DevOps lab environment.

Each operating system has its own independent automation so it can be managed, extended, and maintained separately.

## Repository Structure

```text
automation/
├── alpine/
├── ubuntu/
├── .gitignore
└── README.md
```

## Supported Operating Systems

| OS | Status |
|----|--------|
| Alpine Linux | ✅ |
| Ubuntu Server | ✅ |

## Automation Includes

### Alpine

- System update
- Common utilities
- Docker installation
- SSH configuration
- DevOps lab preparation

### Ubuntu

- System update
- Common utilities
- Docker Engine installation
- Docker Compose Plugin
- SSH configuration
- DevOps lab preparation

## Requirements

- Ansible 2.16+
- SSH Access
- Python 3 installed on target host
- Passwordless sudo (recommended)

## Getting Started

Clone the repository:

```bash
git clone https://github.com/<username>/automation.git
cd automation
```

Choose the operating system folder and execute the playbook.

Example:

```bash
cd ubuntu
ansible-playbook playbooks/setup.yml
```

## Future Roadmap

- Kubernetes Automation
- Monitoring Stack
- Nginx Reverse Proxy
- GitHub Runner
- Terraform Integration
- CI/CD Pipelines

## License

MIT License