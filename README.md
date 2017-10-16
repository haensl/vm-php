# VM-PHP

##### PHP project skeleton.

Vagrant box featuring:
- Debian Jessie
- Apache
- MySQL
- PHP 7
- MailHog
- exim4
- development site
- qa site

## Quick Start

1. Fork this repository
2. `cd` into repository folder
3. `vagrant up`

    development: `http://localhost:8080`

    qa: `http://localhost:8081`

    mailhog: `http://localhost:8025`
4. enjoy.

## Requirements

- [Vagrant](https://github.com/hashicorp/vagrant)
- [Ansible](https://github.com/ansible/ansible)

## Customization

This VM setup relies on several Ansible roles which can mostly be adjusted via overriding values in [VM/host_vars/default](VM/host_vars/default). Please visit the respective project for further information:

- [geerlingguy/ansible-role-apache](https://github.com/geerlingguy/ansible-role-apache)
- [geerlingguy/ansible-role-exim](https://github.com/geerlingguy/ansible-role-exim)
- [geerlingguy/ansible-role-mailhog](https://github.com/geerlingguy/ansible-role-mailhog)
- [geerlingguy/ansible-role-mysql](https://github.com/geerlingguy/ansible-role-mysql)
- [geerlingguy/ansible-role-php](https://github.com/geerlingguy/ansible-role-php)

### MySQL

#### Username/password

default: `root // root`

Set `mysql_user`and `mysql_pass` in [VM/host_vars/default](VM/host_vars/default).

#### Database

default: `vm-php`

Set `mysql_db` in [VM/host_vars/default](VM/host_vars/default).

#### Tables

Put your sql statements for initial database setup in [VM/roles/dev-setup/files/tables.sql](VM/roles/dev-setup/files/talbes.sql).

### Apache

#### src/qa directories

default: `app/src // app/dist`

Set `http_root_src` and `http_root_qa` in [VM/host_vars/default](VM/host_vars/default).

#### sites

Site configurations can be adjusted as needed, see [VM/roles/dev-setup/files/dev.conf](VM/roles/dev-setup/files/dev.conf) and [VM/roles/dev-setup/files/qa.conf](VM/roles/dev-setup/files/qa.conf).

#### ports

Ports can be adjusted via [VM/roles/dev-setup/files/ports.conf](VM/roles/dev-setup/files/ports.conf).

## Credits

[Jeff Geerling](https://github.com/geerlingguy) for his awesome Ansible roles.

[Ansible](https://github.com/ansible) for their awesome configuration management tool.

[Hashicorp](https://github.com/hashicorp) for their awesome virtualization managment tool.
