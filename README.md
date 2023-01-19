# IBC-Relayer Ansible Setup

## Design Philosophy

1. Support hermes, rly and hyperspace installation
1. So far, only Hermes configuration is installed since that's the one we use
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

### hyperspace installation

```bash
ansible-playbook main_hyperspace_install.yml
```

### Hermes deployment

Here are two modes to deploy Hermes. For the Scaffolding Mode, you will specify a list of networks in the inventory file. For the Customization Mode, you will maintain your own jinja template.

For both, you will need to specify `key_name`, `memo` and a list of target ips in the inventory file. Examples are provided in the sample file.

```bash
ansible-playbook main_hermes_config.yml -e "target=mainnet"
ansible-playbook main_hermes_config.yml -e "target=testnet"
```

#### Scaffolding Mode

This mode is suitable if you just want to get the relay going quickly among a few networks.

You will fill in the list of networks you want to relay in the `mainnet_networks` or `testnet_networks` variables in the inventory file. The scaffolded config file will relay any channels among these networks.

#### Customization Mode

This mode is suitable when you connect lots of different networks and you want to fine-tune how they connect with each other.

You will leave `mainnet_networks` or `testnet_networks` blank in the inventory file. You will customize the `mainnet.toml.j2` or `testnet.toml.j2` files using our files as the starting point.
