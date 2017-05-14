# Overview

This project provides Ansible playbooks for setting up the social enterprise directory. It assumes install on an Ubuntu server.

# Preparing Ansible

On your controller machine:

1. Install ansible
2. Install role dependencies required for social enterprise directory

  `ansible-galaxy install -r role_dependencies.yml`

3. Set `allow_world_readable_tmpfiles=true` in ansible.cfg

# Configure hosts

Using the `hosts` file provided in this repo as an example, setup your local ansible hosts file at `/etc/ansible/hosts`

* [backend_servers] : list the servers you want to use as backend for social enterprise directory
* [frontend_servers] : list the servers you want to use as frontend for social enterprise directory

# Executing Playbooks

To create backend servers for the social enterprise directory, use the following playbook:

  `ansible-playbook playbooks/se-dir-backend-playbook.yml`

## Finishing Backend installation
  To finish installation for backend, you'll need to configure the secrets:

1.  Session secret
* Add a session secret to config/production.json
```
  "sessionSecret": "Any secret string here"
```

2.  Oauth configuration
* To configure OAuth, create a file called `config/oauth/oauth.json`. The contents should look like:

```
{
  "twitterCallbackURL": "https://<your url>/api/v1/account/login/twitter/callback",
  "facebookCallbackURL": "https://<your url>/api/v1/account/login/facebook/callback",
  "instagramCallbackURL": "https://<your url>/api/v1/account/login/instagram/callback",

  "redirectURLOnSuccessfulLogin": "your URL",

  "twitterConsumerKey" : "your key",
  "twitterConsumerSecret": "your secret",

  "facebookClientId": "your client id",
  "facebookSecret": "your secret",

  "instagramClientId": "your client id",
  "instagramSecret": "your secret "
}
```

3. Restart backend

  `service sedir start`


To create frontend servers for the social enterprise directory, use the following playbook:

  `ansible-playbook playbooks/se-dir-frontend-playbook.yml`

# Executing Playbook on Remote hosts

To execute a playbook on remote host as a user with sudo privileges:

  `ansible-playbook <playbook> --become -u <username> --ask-become-pass --ask-pass`
