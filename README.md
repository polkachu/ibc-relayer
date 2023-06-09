# IBC-Relayer Ansible Setup

## Design Philosophy

1. Support hermes, rly and hyperspace installation
1. Support hermes abd rly configuration, although we are transitioning to rly so rly will receive more continuous support
1. Make config file extensible by DRY principle

## Guide

First copy it to your own inventory file so you can customize it to suit your needs:

```bash
cp inventory.sample inventory
```

### Hermes installation

```bash
ansible-playbook main_hermes_install.yml
```

### rly installation

```bash
ansible-playbook main_rly_install.yml
```

### Hyperspace installation

```bash
ansible-playbook main_hyperspace_install.yml
```

### Hermes deployment

You will need to specify `key_name`, `memo` and a list of target ips in the inventory file. Examples are provided in the sample file.

```bash
ansible-playbook main_hermes_config.yml -e "target=mainnet"
ansible-playbook main_hermes_config.yml -e "target=testnet"
```

### rly deployment

[TBD] You will need to specify `key_name`, `memo` and a list of target ips in the inventory file. Examples are provided in the sample file.

```bash
ansible-playbook main_rly_config.yml -e "target=mainnet"
ansible-playbook main_rly_config.yml -e "target=testnet"
```

### Some useful commands for self

`{host="hq",unit="hermes_mainnet.service"} |~"dst_chain.*insufficient funds"`

`{host="hq",unit="hermes_mainnet.service"}  |~"ERROR.*dst_chain" !~"redundant" !="mismatch" !=" timed out" !="crescent" !="not valid"`
