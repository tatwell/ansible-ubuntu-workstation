# Ansible Ubuntu Workstation
Ansible playbook designed to quickly deploy a new Ubuntu workstation.

This was based largely on https://github.com/Benoth/ansible-ubuntu. If you're building your own, I'd recommend starting there.


## Requirements
- Git
- Ansible 2+ (automatically installed from [Ansible offical PPA](https://launchpad.net/~ansible/+archive/ubuntu/ansible) with the provided install.sh script)


## Installation
1. First, install Git and Ansible using the install script :
```
sudo apt-get install git
git clone https://github.com/tatwell/ansible-ubuntu-workstation.git
cd ansible-ubuntu-workstation
./install.sh
```

2. Review and customize the playbook `ansible-desktop.yml`
3. Update settings in `group_vars/all.yml`.


## Usage
To run the playbook:

    ansible-playbook ansible-desktop.yml --ask-become-pass


## Manual Steps
After running the playbook, I still need to do the following tasks manually:

- Reload the shell to enable updates:

        source ~/.bashrc
        source /etc/profile

- Create default user postgresql database:

        createdb

        # Now you should be able to connect to postgres.
        psql

- On Jenkins server, add Python installations for the [Shining Panda plugin](https://wiki.jenkins-ci.org/display/JENKINS/ShiningPanda+Plugin):
  - Manage Jenkins > Global Tool Configuration > Python installations
  - Input following settings:
    - Name: `Jenkins-Pyenv-Python-2.7.8`
    - Home or executable: `/var/lib/jenkins/pyenv/versions/2.7.8/bin/python2`
  - Push **Add Python** button.

- As `jenkins` user, update password settings in `/var/lib/jenkins/.env/local-wiki.env`.

- Configure backups:
  - System Settings > Backups > Install
  - Configure settings (menu on left of settings dialog)
  - Turn on backups (toggle switch in upper right of dialog to ON)
  - For an automated approach, see [these roles in Galaxy](https://galaxy.ansible.com/list#/roles?page=1&page_size=10&autocomplete=duplicity&order=-download_count,name).

- Move existing VirtualBox VMs:
  - See this thread: https://superuser.com/q/633431
  - If you get an error copying VM files because they are too large, see [this article](http://www.wikihow.com/Format-a-USB-Flash-Drive-in-Ubuntu).
  - After copying and adding VM, update shared folder under Settings.

- tmux
  - To install plugins: `tmux` > CTRL-B > I


## Roles

See `ansible-desktop.yml` for the roles used by this playbook. A summary of many roles can be found at:

- https://github.com/Benoth/ansible-ubuntu#roles-included
