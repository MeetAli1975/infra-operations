# Infrastructure Operations (`infra-operations`)

Ansible-based infrastructure operations and configuration management for Linux nodes hosted on Proxmox VE.

## Infrastructure Nodes

| Node | Operating System | IP Address | Ansible Group |
|---|---|---|---|
| aether | Omarchy (Arch Linux-based) | 192.168.1.203 | aether |
| devops-forge | Rocky Linux 9.8 | 192.168.1.202 | forge |
| devops-peer | Rocky Linux 9.8 | 192.168.1.201 | peer |

Aether is the Ansible control node and uses a local connection. Forge and Peer are managed through SSH.

## Infrastructure Services

- Ansible configuration management
- SSH key-based remote administration
- NFSv4 shared storage
- Persistent NFS mounts
- Firewalld and systemd service management
- Git-based infrastructure change control

## NFS Architecture

- Server: devops-forge (192.168.1.202)
- Export: /srv/shared-services
- Clients: aether and devops-peer
- Mount point: /mnt/shared-services
- Authorized subnet: 192.168.1.0/24

## Usage

```bash
ansible all -m ping -i inventory/hosts.ini
ansible-playbook -i inventory/hosts.ini playbooks/system-baseline.yml
ansible-playbook -i inventory/hosts.ini playbooks/forge-baseline.yml
ansible-playbook -i inventory/hosts.ini playbooks/forge-configuration.yml --check --ask-become-pass
ansible-playbook -i inventory/hosts.ini playbooks/aether-nfs-client.yml --check --ask-become-pass

```

## Version Control

Infrastructure changes are tracked in Git and synchronized with GitHub.
