# Ansible Home Lab — Command Reference

## SSH Setup

```bash
# Generate a key (once, per purpose — use separate keys for lab vs production)
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519

# Copy a key to a target host
ssh-copy-id -o IdentitiesOnly=yes -i ~/.ssh/id_ed25519.pub debian@<ip>

# Test connection
ssh debian@<ip>
```

## Ansible — Basic Commands

```bash
# Check version / install info
ansible --version

# Ping all hosts in inventory
ansible all -i inventory.ini -m ping

# Ping a single host
ansible home -i inventory.ini -m ping

# Dry run (note: unreliable for tasks depending on earlier install tasks)
ansible-playbook -i inventory.ini baseline.yml --check

# Run against one host only
ansible-playbook -i inventory.ini baseline.yml --limit lab
```
