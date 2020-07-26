# Eth2 ansible collection

This is an experimental Ansible collection of roles and playbooks to use for testnets.

It is NOT RECOMMENDED to use this in mainnet, as security was not the primary focus of this.
The primary focus is to quickly spin up testnets and automate things that require more care in a mainnet context.

This is a *work in progress* ansible collection. The intention is to eventually publish it, to make it more reusable.
For now, you can git-submodule this repository, and add the `roles` as source for your playbooks.

## Usage

- `machine`: common setup things for a nepublw machine, installing required things for other roles
- `ubuntu`: common ubuntu os settings (TODO: hardening)
- `eth2client`: 
    - defines validator assignments
    - defines validator
    - defines beacon node
    - defines [eth2stats](https://eth2stats.io) setup.
    - Defaults can be configured by picking any of the `defaults` subdirectories:
        - `lighthouse`
        - `nimbus`
        - `prysm`
        - `teku`
- `bootnode`: Discv5 bootnode for eth2 clients
- `deposit_contract`: Deploy testnet deposit contract, optionally with tokens instead of eth.
- `metrics`: Deploy prometheus, grafana, install dashboard and datasources, setup nginx, setup letsencrypt and vhosts.
- `val_tools`: Build deposits, execute deposits. 

The `val_tools` and `deposit_contract` roles assume [`ethereal`](https://github.com/wealdtech/ethereal/) is installed.

## Local testnet provisioning

To start a local testnet provisioning is provided using `vagrant`. Please install `vagrant` first on your local machine.

To setup your own testnet, execute these commands from the root folder of this repository:

```
# Setup and provision virtual machines (requires vagrant to be installed)
vagrant up

# To retry provisioning after the VMs are up, use
vagrant provision
```

## License

MIT, see [`LICENSE`](./LICENSE) file.
