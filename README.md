# ansible-role-easywall

The Ansible role installs [easywall](https://github.com/jpylypiw/easywall) - the webinterface for the iptables firewall.

## Requirements

The role requires the following operating system versions:

- Debian > 9
- Ubuntu > 18.04

## Role Variables

```yaml
# install variable to check if the webinterface should be installed.
webinterface: true

# variables to set the easywall username and password using the ansible role
easywall_username: ""
easywall_password: ""

# Set to true to ensure other firewall management software is disabled.
firewall_disable_firewalld: true
firewall_disable_ufw: true

# set ssl certificate options
ssl_cert_path: ""
ssl_key_path: ""
```

## Dependencies

No dependencies to other roles available. Only standard modules are used.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
---
- name: "install easywall firewall management on the system"
  hosts: "linux"
  gather_facts: true
  become: true
  tasks:
    # you should install ssl certificates here - for example let's encrypt

    - name: "use the ansible-role-easywall role"
      include_role:
        name: ansible-role-easywall
      vars:
        webinterface: true
        easywall_username: "{{ vault_easywall_username }}"
        easywall_password: "{{ vault_easywall_password }}"
        ssl_cert_path: "/etc/ssl/certs/certificate.pem"
        ssl_key_path: "/etc/ssl/private/privatekey.pem"
```

## License

GPL 3.0+

## Author Information

Jochen Pylypiw <12394156+jpylypiw@users.noreply.github.com>
