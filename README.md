# Foreman Dynamic Inventory
[![Build Status](https://travis-ci.org/danquack/foreman_dynamic_inv.svg?branch=master)](https://travis-ci.org/danquack/foreman_dynamic_inv)

An ansible role to gather inventory from formen to create hostgroups

## Role Variables
Role variables can be set in play or in vars

1. group_name: host group to return
1. query: foreman query
1. foreman_url: url for foreman (implied https)
1. foreman_username: username for auth with
1. foreman_passwd: password for auth


## Example Playbook
Ping the hosts in the linux hostgroup
```
    - hosts: localhost
      connection: local
      tasks:
        - name: Invoke role looking for all hosts in linux group
          include_role:
            name: ../../foreman_dynamic_inv
          vars:
            query: "hostgroup~+Linux"
            group_name: "linux"
            foreman_url: "foreman.example.com"
            foreman_username: "username"
            foreman_passwd: "passwd"

    - hosts: linux
      tasks:
        - ping:
```

## Contributors
Check out [Github contributors](https://github.com/danquack/foreman_dynamic_inv/graphs/contributors)
