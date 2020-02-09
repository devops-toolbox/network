Role Name
=========

network: Network

[![Build Status](https://travis-ci.org/cmihai-ansible/network.svg?branch=master)](https://travis-ci.org/cmihai-ansible/network)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.network](https://galaxy.ansible.com/devopstoolbox.network)

```bash
ansible-galaxy install devopstoolbox.network
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
network_packages_state: present
network_remove_packages: true
network_enable_service: true
network_enable_selinux: true
network_copy_templates: true
network_firewall_configure: true
network_firewall_rules:
  - service: ssh
  - port: 3389
network_users:
  - user: devops
    group: docker
network_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install network on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: network is configured
      import_role:
        name: devopstoolbox.network
      vars:
        network_packages_state: present
        network_remove_packages: true
        network_enable_service: true
        network_enable_selinux: true
        network_copy_templates: true
        network_firewall_configure: true
        network_firewall_rules:
          - service: ssh
          - port: 3389
        network_users:
          - user: devops
            group: docker
        network_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: network
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
