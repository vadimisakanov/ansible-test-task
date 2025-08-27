# Basic server configuration
Basic server configuration with Ansible, done for a test task, proudly created with the modern technology

## Quick start
- Configure your server address in `inventory/inventory.ini` and vars in `vars/main.yaml`
- Run `ansible-playbook playbooks/server-config.yaml -i inventory/inventory.ini --become --user ubuntu`
- You're great!

## Description
Preparing a Linux server: configuring second disk encryption, disabling c-state, switch off CPU powersave mode, set active network interface name, list CPUs

All the tasks described in separate roles, every role called with it's one playbook with the same name + one main role called `server-config.yaml` that calls all the roles at once

Directory structure according to Ansible Best-Practice directory layot https://docs.ansible.com/ansible/2.8/user_guide/playbooks_best_practices.html#directory-layout

## Layout
```
├── README.md                       - this README
Playbooks:
├── playbooks
│   ├── cpu-powersave-mode-off.yaml
│   ├── disable-c-state.yaml
│   ├── encrypt-second-disk.yaml
│   ├── list-cpus.yaml
│   ├── rename-nic.yaml
│   └── server-config.yaml         - the main playbook
Inventory:
├── inventory
    ├── inventory.ini
Roles:
├── roles
│   ├── cpu-powersave-mode-off
│   ├── disable-s-state
│   ├── encrypt-second-disk
│   ├── rename-nic
│   └── list-cpus
Variables:
├── vars
    └── main.yaml
```

+ `%playbook-name%-README.md` files with a description for each playbook

## Requirements
- target system with `cryptsetup`, `nmcli`, `cpufrequtils` installed or available in repos
- root privileges (become: yes)

## Role Variables
- `encrypted_partition`: The partition device path to encrypt (must be specified in inventory or overridden)

## Usage
Redefine `encrypted_partition` in `vars/main.yaml` if needed and execute the target playbook like

`ansible-playbook playbooks/server-config.yaml -i inventory/inventory.ini --become --user ubuntu`

`server-config.yaml` is the default playbook that runs all the tasks

Other playbooks run one of the tasks only
