# Ansible Role: Certbot (for Let's Encrypt)

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-certbot.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-certbot)

Installs Certbot (for Let's Encrypt) for RHEL/CentOS or Debian/Ubuntu.

## Requirements

Certbot requires Git to be installed. You can install Git using the `geerlingguy.git` role.

## Role Variables

    certbot_repo: https://github.com/certbot/certbot.git
    certbot_version: master
    certbot_keep_updated: yes

Certbot code repository options. This role clones the agent from the configured repo, then makes the `certbot-auto` script executable.

    certbot_dir: /opt/certbot

The directory inside which Certbot will be cloned.

## Dependencies

None.

## Example Playbook

    - hosts: servers
      roles:
        - geerlingguy.letsencrypt

After installation, you can create certificates using the `certbot-auto` script, which by default is installed inside the configured `certbot_dir`, so by default, `/opt/certbot/certbot-auto`. Here are some example commands to configure certificates with Certbot:

    # Automatically add certs for all Apache virtualhosts (use with caution!).
    /opt/certbot/certbot-auto --apache
    
    # Generate certs, but don't modify Apache configuration (safer).
    /opt/certbot/certbot-auto --apache certonly

To set up renewals, you should run the following command periodically (e.g. once or twice per day):

    /opt/certbot/certbot-auto renew --quiet --no-self-upgrade

You can test the auto-renewal (without actually renewing the cert) with the command:

    /opt/certbot/certbot-auto renew --dry-run

See full documentation and options on the [Certbot website](https://certbot.eff.org/).

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/).
