docker_mattermost
=================

This role deploys Mattermost on Docker. This role is not maintained anymore.
The main repo for this role is on [Le Filament GitLab](https://sources.le-filament.com/lefilament/ansible-roles/docker_drawio.git)

Requirements
------------

None

Role Variables
--------------

Variables from default directory :
* mm_url: URL on which Mattermost will be listening
* mm_db_name: Database name
* mm_db_user: Database user
* mm_db_pass: Database password
* Mail configuration (optional, if set, a postfix proxy will be deployed, otherwise a mailhog instance will be deployed for blocking e-mails)
  * mailname: domain to which the users belong to
  * mailserver: SMTP server to use for sending e-mails (defaults to smtp.{{ domain }})
  * smtpport: SMTP server port (defaults to 465)
  * smtpuser: SMTP username (defaults to smtpuser)
  * smtppass: SMTP user password (defaults to veryUnsecurePassToBeModified)
* Backups (for backups to be deployed, host needs to be in maintenance_contract group) :
  * swift parameters for 2 object storage instances where backups should be pushed daily
  * mm_backup_pass : Passphrase for encryption of backups


Dependencies
------------

This role requires the following Ansible collection :
* community.docker

This Docker role supposes that Traefik is deployed as an inverseproxy in front of the deployed Dockers.
The following role is used by Le Filament for deploying Traefik : docker_server (https://sources.le-filament.com/lefilament/ansible-roles/docker_server)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: docker_mattermost }
      vars:
         - { mm_url: "mattermost.example.org" }
         - { mm_db_pass: "veryUnsecurePassToBeModified" }

License
-------

AGPL-3

Author Information
------------------

Le Filament (https://le-filament.com)
