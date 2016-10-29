# Overview

This project provides Ansible playbooks for setting up the social enterprise directory. It assumes install on an Ubuntu server.

# Preparing Ansible

On your controller machine:
1. Install ansible
2. Install role dependencies required for social enterprise directory

  `ansible-galaxy install -r role_dependencies.yml`

# Configure hosts

Using the `hosts` file provided in this repo as an example, setup your local ansible hosts file at `/etc/ansible/hosts`

* [backend_servers] : list the servers you want to use as backend for social enterprise directory

# Executing Playbooks

To setup backend servers for the social enterprise directory, use the following playbook:

  `ansible-playbook playbooks/se-dir-backend-playbook.yml`
