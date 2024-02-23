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

  - hosts: servers
    vars:
      nfs_access_list:
        - 192.168.1.0/24
        - 2607:f8b0:4008:804::/64
    roles:
        - { role: qs5779.nfs }

License
-------

MIT

Author Information
------------------

Quien Sabe https://www.quiensabe.org
