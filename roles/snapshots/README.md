Snapshots Elasticsearch
=========

Create snapshots and snapshots repository

Requirements
------------

Elasticsearch cluster reachable

Role Variables
--------------

```yaml
es_api_scheme: "http"
es_api_host: "localhost"
es_api_port: 9200
es_api_uri: "{{ es_api_scheme }}://{{ es_api_host }}:{{ es_api_port }}"
es_api_snapshots: "_snapshot"
es_api_basic_auth_username: 'elastic'
es_api_basic_auth_password: 'changeme'

es_validate_certs: no
es_create_repositories: yes

es_repositories:
  - name: "fs_default_name"
    type: "fs"
    settings:
      location: "/my_fs_backup_location"
      compress: "true"
      chunk_size: null
      max_restore_bytes_per_sec: "40mb"
      max_snapshot_bytes_per_sec: "40mb"
      readonly: "false"
es_create_snapshots: no

es_snapshots_to_create:
  - name: <fs-snapshot-{now/d}>
    repository: "fs_default_name"
    settings:
      indices: ["*"]
      ignore_unavailable: "true"
      include_global_state: "false"
      metadata:
        taken_by: "me"
        taken_because: "i wanted to"

es_restore_snapshots: no

es_snapshots_to_restore: []
```

Example Playbook
----------------

```yaml
- hosts: localhost
  connection: local
  roles:
  - role: klusters.elasticsearch.snapshots
```


License
-------

MIT

Author Information
------------------

http://fathallah.fr
