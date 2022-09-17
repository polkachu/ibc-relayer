# IBC-Relayer Ansible Setup

## Design Philosophy

1. Support both hermes and rly
1. Make config file extensible by DRY principle

## Guide

First copy it to your own inventory file so you can customize it to suit your needs:

```bash
cp inventory.sample inventory
```

### rly installation

```bash
ansible-playbook main_rly_install.yml
```

### Hermes installation

```bash
ansible-playbook main_hermes_install.yml
```

### Hermes deployment

You will want to maintain your own `mainnet.toml.j2` file in the `hermes_config` playbook

```bash
ansible-playbook main_hermes_config.yml -e "target=mainnet"
```
