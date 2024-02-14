# Ansible Playbook

You can make your own playbook with just one command


## Usage

```
In this path (provision/roles/create_playbook/vars) Two variables are set:
ansible_root: </path/to/provision>
project_name: <your project name>

You need to change the value of (ansible_root) to your desired path where ansible is located.
```
## How to run

```bash
$ ansible-playbook create_playbook.yml -e project_name="myapp"
```