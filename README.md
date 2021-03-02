# Ansible role to deploy Mattermost server docker

[![](https://img.shields.io/badge/licence-AGPL--3-blue.svg)](http://www.gnu.org/licenses/agpl "License: AGPL-3")

This role allows you to deploy Mattermost docker with associated Postgres DB and postfix relay.
This role also embeds automatic backups towards swift storage every day (with one full backup every week and retention of 3 full backups) using duplicity based on [Tecnativa docker image](https://hub.docker.com/r/tecnativa/duplicity). See [Ansible docker odoo role](https://github.com/lefilament/ansible_role_odoo_docker/blob/master/files/Dockerfile-backup) for building that docker image.

Prior to running this role, you would need to have docker installed on your server and a traefik proxy (which is the purpose of [this role](https://github.com/lefilament/ansible_role_docker_server))

In order to use this role, you would need to define the following variables for your server (in hostvars for instance) - Only the names of the variables are provided below (not the values) for these used by this role to properly configure everything, you may copy this file directly in hostvars and set the variable although we could only encourage you to use an Ansible vault and refer vault variables from there:

```json
## Ansible configuration for connecting to remote host
# IP address of server
ansible_host: 
# User to be used on server (to which Ansible server public key has been provided)
ansible_user: 
# Encryped password (for elevating rights / sudo)
ansible_become_pass: 
# Server SSHD port
ansible_port: 

## Mattermost configuration
# Mattermost URL (only sub.domain without https:// in front)
mm_url:
# Mattermost DB
mm_db_name: 
mm_db_user: 
mm_db_pass: 

## Backup Swift Storage configuration
swift_username:
swift_password:
swift_authurl:
swift_authversion:
swift_tenantname:
swift_tenantid:
swift_regionname:

```

# Credits

## Contributors

* Remi Cazenave <remi-filament>


## Maintainer

[![](https://le-filament.com/img/logo-lefilament.png)](https://le-filament.com "Le Filament")

This role is maintained by Le Filament
