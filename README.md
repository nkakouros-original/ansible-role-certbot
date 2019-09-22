[![Build
Status](https://travis-ci.com/nkakouros-original/ansible-role-certbot.svg?branch=master)](https://travis-ci.com/nkakouros-original/ansible-role-certbot)
[![Galaxy](https://img.shields.io/badge/galaxy-nkakouros.certbot-blue.svg)](https://galaxy.ansible.com/nkakouros/certbot/)

ansible-role-certbot
====================

Installs and configures Certbot (for Let's Encrypt).

Description
-----------

This role will:

- install certbot
- generate certificates
- install a systemd timer to automatically renew them

Requirements
------------

If installing from source, Git is required.

Supported platforms
-------------------

- Ubuntu 14.04
- Ubuntu 16.04
- Debian 8
- Debian 9
- Centos 7

Role Variables
--------------

For a complete variable reference, see the [`defaults/main.yml`](defaults/main.yml) file.

Example Playbook
----------------

    - hosts: servers
      vars:
        certbot_auto_renew_user: your_username_here
        certbot_auto_renew_minute: "20"
        certbot_auto_renew_hour: "5"
      roles:
        - nkakouros.certbot

See other examples in the [molecule/default/](molecule/default/) folder.

License
-------

MIT / BSD

Author Information
------------------

Nikolaos Kakouros (nkak@kth.se)

This role is a fork of https://github.com/geerlingguy/ansible-role-certbot.
