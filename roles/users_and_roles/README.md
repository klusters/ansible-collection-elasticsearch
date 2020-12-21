Users and roles Elasticsearch
=========

Manage ES users and roles

Requirements
------------

Elasticsearch cluster reachable

Role Variables
--------------

```yaml
- es_api_scheme: "https"
- es_api_host: "localhost"
- es_api_port: 9200
- es_api_uri: "{{ es_api_scheme }}://{{ es_api_host }}:{{ es_api_port }}"
- es_security_api: '_security'
- es_api_basic_auth_username: 'elastic'
- es_api_basic_auth_password: 'changeme'

- es_validate_certs: no

- es_roles:
    native:
      sample_role_1:
        cluster: []
        indices:
        - names: 'sample-index-1-*'
          privileges:
          - create_index
          - write
      sample_role_2:
        cluster: ['monitor']
        indices:
        - names: 'dummy-index-*'
          privileges:
          - read

- es_users:
    native:
      dummy_user_1:
        password: 'dummy_password_1'
        roles:
        - sample_role_1
      dummy_user_2:
        password: 'dummy_password_2'
        roles:
        - sample_role_2

      metricbeat_collect_es:
        password: 'dummy_password_3'
        roles:
        - remote_monitoring_collector
        - enrich_user

```

Example Playbook
----------------

```yaml
- hosts: localhost
  connection: local
  roles:
  - role: klusters.elasticsearch.users_and_roles
```

License
-------

MIT

Author Information
------------------

http://fathallah.fr
