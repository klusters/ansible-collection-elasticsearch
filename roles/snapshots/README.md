Snapshots Elasticsearch
=========

Create snapshots and snapshots repository

Requirements
------------

Elasticsearch cluster reachable

Role Variables
--------------

```yaml
- es_api_scheme: "http"
- es_api_host: "localhost"
- es_api_port: 9200
- es_api_uri: "{{ es_api_scheme }}://{{ es_api_host }}:{{ es_api_port }}"
- es_api_snapshots: "_snapshot"
- es_api_basic_auth_username: 'elastic'
- es_api_basic_auth_password: 'changeme'

- es_validate_certs: no
- es_create_repository: no

- es_repository_name: "default_name"
- es_repository_type: "fs"
- es_repository_settings:
    location: "my_fs_backup_location"
    compress: "true"
    chunk_size: null
    max_restore_bytes_per_sec: "40mb"
    max_snapshot_bytes_per_sec: "40mb"
    readonly: "false"

- es_create_snapshot: no
- es_snapshot_name: <snapshot-{now/d}>
- es_snapshot_settings:
    indices: ["index_1", "index_2"]
    ignore_unavailable: "true"
    include_global_state: "false"
    metadata:
      taken_by: "me"
      taken_because: "i wanted to"

```

Example Playbook
----------------

```yaml
    - hosts: localhost
      roles:
        - role: role_es_snapshots
```


License
-------

MIT

Author Information
------------------

http://fathallah.fr
