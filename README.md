# IBC-Relayer Ansible Setup

## Design Philosophy

1. Support both hermes and rly
1. Make config file extensible by DRY principle

## Guide

First copy it to your own inventory file so you can customize it to suit your needs:

```bash
cp inventory.sample inventory
```

To install rly

```bash
ansible-playbook main_rly_install.yml
```

To install Hermes

```bash
ansible-playbook main_hermes_install.yml
```

To install a specific Hermes relayer hub

```bash
ansible-playbook main_hermes_config.yml -e "target=juno"
```
