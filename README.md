Dumpall role for Ansible
========

[![Ansible Galaxy Role](https://img.shields.io/badge/Ansible%20Role-mrjk.dumpall-blue.svg?style=flat-square)](https://galaxy.ansible.com/detail#/role/6960)

Dump all remote variables and (optionally) copy the result to a destination on the host. This role is Ansible 2.0 compatible.

Based on the excellent work by [Lester Wade](https://coderwall.com/p/13lh6w), and the very nice implementation of [f500](https://github.com/f500/ansible-dumpall). This version basically fixes some minor bugs, and avoid file name collision.

Requirements
------------

None.

Installation
------------

Via Ansible Galaxy:
    ansible-galaxy install mrjk/ansible-role-dumpall


Role Variables
--------------

    dumpall_flat_mode: yes
    dumpall_guest_destination: "/tmp/ansible/dump/{{ inventory_hostname }}"
    dumpall_host_destination: "/tmp/ansible/dump/{{ inventory_hostname }}"

Example Playbook
-------------------------

Example without a host_destination will result in a dumpfile /tmp/ansible.all on the guest:

    - hosts: servers
      roles:
         - dumpall

Example with a host_destination will result in a dumpfile /examine/ansible.all on the host machine:
(the dumpfile on the guest is removed)

    - hosts: servers
      roles:
         - role: dumpall
           dumpall_host_destination: /tmp/my_prj


If you also set the flat_mode to false, the local filename will be the entire path of the guest_destination,
prepended by the hostname of the current play. See the Ansible _fetch_ module for more information.

License
-------

LGPL

Author Information
------------------

mrjk, jeznet.org

Jasper N. Brouwer, jasper@nerdsweide.nl

Ramon de la Fuente, ramon@delafuente.nl


