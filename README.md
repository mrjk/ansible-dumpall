Dumpall role for Ansible
========

Dump all remote variables and (optionally) copy the result to a destination on the host.

Based on the excellent work by [Lester Wade](https://coderwall.com/p/13lh6w), and the very nice implementation of [f500](https://github.com/f500/ansible-dumpall). This version basically fixes some minor bugs, and avoid file name collision.

Requirements
------------

None.

Role Variables
--------------

    dumpall_flat_mode: yes
    dumpall_guest_destination: /tmp/ansible.all
    dumpall_host_destination: /tmp/ansible/dump/

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

Jasper N. Brouwer, jasper@nerdsweide.nl

Ramon de la Fuente, ramon@delafuente.nl

MrJK, jeznet.org
