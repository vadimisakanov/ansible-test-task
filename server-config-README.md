`server-config.yaml` playbook, main playbook for the project

## Implements the task:

Prepare the OS using Ansible

Using Ansible, implement the ability to perform the following actions (and repeat them on other servers in the future):
– Implement the procedure of encrypting the second disk in the system (where there is no root partition) (partition name should be specified in the inventory).
Implement a procedure to encrypt the partition that is present on the disk next to the root partition.
– Disabling C-state for all available
– Switching CPU operation from power-saving mode to more productive mode.
– Rename the active network interface to "net0". Display information about the renamed interface during the playbook
– At the end of the playbook execution, a list of CPUs should be displayed, as well as information about Intel Hyper-Threading (AMD multithreading).