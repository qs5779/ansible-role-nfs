Role Name
=========

Role to install nfs client and/or nfs server.

Requirements
------------

None

Role Variables
--------------

Default variables

```yaml
nfs_export_root: /exports
nfs_exports:
  - data
  - documents
nfs_export_opts:
  - rw
  - no_root_squash
  - no_subtree_check
  - crossmnt
  - fsid=0
```

Example of required user supplied variables

```yaml
nfs_access_list:
  - 192.168.1.0/24
  - 2607:f8b0:4008:804::/64
```
The above variables result in the following /etc/exports file.

```sh
#
# Ansible managed
#
/exports -rw,no_root_squash,no_subtree_check,crossmnt,fsid=0 192.168.1.0/24 2607:f8b0:4008:804::/64
```

Dependencies
------------

None

Example Playbook
----------------

```yaml
  - hosts: servers
    vars:
      nfs_access_list:
        - 192.168.1.0/24
        - 2607:f8b0:4008:804::/64
    roles:
        - qs5779.nfs
```

License
-------

MIT

Installation
------------

I will not upload this role to ansible galaxy until I develop automated tests.
To install the role from github, create a reqirements.yml file with the following contents:

```yaml
---
# for examples see https://docs.ansible.com/ansible/latest/galaxy/user_guide.html#installing-multiple-roles-from-a-file
# from GitHub
- name: qs5779.nfs
  src: https://github.com/qs5779/ansible-role-nfs
  version: main
...
```

Then run:

```sh
ansible-galaxy install -r requirements.yml
```

Author Information
------------------

Quien Sabe https://www.quiensabe.org
