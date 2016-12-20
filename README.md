Role Name
=========

Ansible role for InfluxDB Enterprise

Requirements
------------

None

Role Variables
--------------

The 3 varaibles you need to worry about in terms of operation are the flags for which server components you're working on (data vs. meta vs console).  You pass this in (typically) as role vars and they are:

```yaml
influxdb_is_meta: false
influxdb_is_data: false
influxdb_is_console: false
```

So, use in a playbook may look like this:

```yaml
- name: Deploy InfluxDB Meta Nodes
  hosts: meta
  roles:
    - { role: ansible-role-influxdb-enterprise, influxdb_is_meta: true }
  post_tasks:
    - include: tasks/meta.yml mode="post"

- name: Deploy InfluxDB Data Nodes
  hosts: data
  roles:
    - { role: ansible-role-influxdb-enterprise, influxdb_is_data: true }
  post_tasks:
    - include: tasks/data.yml mode="post"

- name: Deploy InfluxDB Enterprise Console
  hosts: console
  roles:
    - { role: ansible-role-influxdb-enterprise, influxdb_is_console: true }
```

Dependencies
------------

None

License
-------

MIT
