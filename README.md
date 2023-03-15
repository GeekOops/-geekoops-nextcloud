geekoops-nextcloud
==================

Minimalistic role to install Nextcloud (as a system package) on an openSUSE Leap/SLES system.

This role doesn't take care of AppArmor. You might need to disable AppArmor during installation.

Requirements
------------

* [community.general.zypper](https://docs.ansible.com/ansible/latest/collections/community/general/zypper_module.html)
* [Community.Mysql](https://docs.ansible.com/ansible/latest/collections/community/mysql/)

Role Variables
--------------

| Variable | Description | Default |
|----------|-------------|---------|
| `db_configure` | Configure a MariaDB database for NextCloud | `false` |
| `db_name` | Database name to be created | `nextcloud` |
| `db_user` | Database username to be created for NextCloud | `nextcloud` |
| `db_pass` | Password for the database username | `notsecret` |
| `firewall_configure` | Toggle firewall configuration | `true` |
| `firewall_zone` | Firewall zone where to allow traffic to | `public` |

if `db_configure` is set to `true`, then the role will create a MariaDB database for you.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: jellyfish
      roles:
         - role: geekoops-nextcloud
           vars:
             db_configure: true
             db_name: 'nextcloud'
             db_user: 'nextcloud'
             db_pass: 'password123'
             firewall_configure: true
             firewall_zone: 'public'

License
-------

MIT

# Development

## Add githooks

This repository ships pre-commit git hooks that will check the yaml syntax. To configure them do

    git config --local core.hooksPath .githooks/
