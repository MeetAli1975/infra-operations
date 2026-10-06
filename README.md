# Infrastructure Operations (`infra-operations`)

Ansible-based operations and configuration management for Linux nodes.

## Nodes
- **aether**: Arch Linux (localhost)
- **forge**: Rocky Linux 9.8 (192.168.1.202)

## Usage
```bash
ansible all -m ping -i inventory/hosts.ini
ansible-playbook -i inventory/hosts.ini playbooks/system-baseline.yml
ansible-playbook -i inventory/hosts.ini playbooks/forge-baseline.yml
ansible-playbook -i inventory/hosts.ini playbooks/forge-configuration.yml --check --ask-become-pass
```
