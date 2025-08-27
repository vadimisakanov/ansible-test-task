# ansible-test-task
Test task w Ansible

## Quick start

1/ Configure your server address at `inventory/inventory.ini` and vars in `vars` directory

2/ Run `ansible-playbook server-config.yaml --become --user ubuntu`

3/ You're great!

## Description

Preparing a Linux server: configuring second disk encryption, disabling c-state, switch off CPU powersave mode, set active network interface name, list CPUs

All the tasks described in separate roles, every role called with it's one playbook with the same name + one main role called `server-config.yaml` that calls all the roles at once

Directory structure according to Ansible Best-Practice directory layot https://docs.ansible.com/ansible/2.8/user_guide/playbooks_best_practices.html#directory-layout

## Layout

```
├── README.md                       - this README
Playbooks:
├── cpu-powersave-mode-off.yaml
├── disable-c-state.yaml
├── encrypt-second-disk.yaml
├── playbooks
├── rename-nic.yaml
├── server-config.yaml              - the main playbook
Inventory:
├── inventory
    ├── inventory.ini
Roles:
├── roles
│   ├── cpu-powersave-mode-off
│   ├── disable-s-state
│   ├── encrypt-second-disk
│   └── rename-nic
Variables:
├── vars
    └── main.yaml
```