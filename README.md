# Ansible Ubuntu Workstation
Ansible playbook designed to quickly deploy a new Ubuntu workstation.

This was based largely on https://github.com/Benoth/ansible-ubuntu. If you're building your own, I'd recommend starting there.


## Requirements
- Git
- Ansible 2+ (automatically installed from [Ansible offical PPA](https://launchpad.net/~ansible/+archive/ubuntu/ansible) with the provided install.sh script)


## Installation
First, install Git and Ansible using the install script :
```
sudo apt-get install git
git clone https://github.com/tatwell/ansible-ubuntu-workstation.git
cd ansible-ubuntu-workstation
./install.sh
```

Then review and customize the playbook `ansible-desktop.yml` and settings in `group_vars/all.yml`.

Finally, to run the playbook:

    ansible-playbook ansible-desktop.yml --ask-become-pass


## Roles

See `ansible-desktop.yml` for the roles used by this playbook. A summary of most roles can be found at:

- https://github.com/Benoth/ansible-ubuntu#roles-included
