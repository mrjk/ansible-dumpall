Dumpall role for Ansible
========

[![Ansible Galaxy Role](https://img.shields.io/badge/Ansible%20Role-mrjk.dumpall-blue.svg?style=flat-square)](https://galaxy.ansible.com/detail#/role/6960)

Dump all remote variables and (optionally) copy the result to a destination on the host. It is really helpful to have a dump of all variables (because the official documentation lacks of clarity on this point) and it helps a lot to debug your roles/playbooks.  This role is Ansible 2.0 compatible.

Based on the excellent work by [Lester Wade](https://coderwall.com/p/13lh6w), and the very nice implementation of [f500](https://github.com/f500/ansible-dumpall). This version basically fixes some minor bugs, and avoid file name collision.

Requirements
------------

Ansible 1.4 and higher. This is compatible with Ansible 2.0.


Installation
------------

Via Ansible Galaxy:

    ansible-galaxy install mrjk/ansible-role-dumpall


Role Variables
--------------

	dumpall_keep_on_guest: no
	dumpall_keep_on_host: yes
	
    dumpall_guest_destination: "/tmp/ansible/dump/{{ inventory_hostname }}"
    dumpall_host_destination: "/tmp/ansible/dump/{{ inventory_hostname }}"

The dumpall_keep_on_guest and dumpall_keep_on_host variables let you choose where you want to keep the dump file.
The dumpall_guest_destination variable is where the dump file is created on the target. The dumpall_host_destination is where all dumps are retrieved from target.

All variables are mandatory, and they are documented in default/main.yml.

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
		  dumpall_keep_on_guest: yes
          dumpall_host_destination: /tmp/my_prj


License
-------

LGPL

Author Information
------------------

mrjk, jeznet.org

Jasper N. Brouwer, jasper@nerdsweide.nl

Ramon de la Fuente, ramon@delafuente.nl


