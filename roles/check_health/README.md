Check Health
=========

Check Elasticsearch Cluster health. Can be used between rolling updates steps and after cluster bootstrap

Requirements
------------

Elasticsearch cluster reachable

Role Variables
--------------

| Variable                 | Required | Default                                                                  | Comments                                        |
| ------------------------ | -------- | ------------------------------------------------------------------------ | ----------------------------------------------- |
| `es_api_scheme`                | No | `http`                                                     | http or https |
| `es_api_host`                | No | `localhost`                                                  | ES node's fqdn to query should be reachable from the ansible_host used to run this role |
| `es_api_port`                | No | `9200`                                                       | ES node's port |
| `es_api_uri`                | No | `{{ es_api_scheme }}://{{ es_api_host }}:{{ es_api_port }}    | ES URI |
| `es_api_cluster_health`                | No | `_cluster/health`                                  | ES Cluster health api |
| `es_api_cluster_nodes`                | No | `_nodes`                                            | ES Cluster nodes api |
| `es_api_basic_auth_username`                | No | `'elastic'`                                   | ES User to use when auth is enabled |
| `es_api_basic_auth_password`                | No | `'changeme'`                                  | ES Password to use when auth is enabled |
| `es_rolling_update`                | No | `no`                                                   | Rolling update mode : check relocating shards and wait for the cluster status to be green before continue |

Example Playbook
----------------

```yaml
- hosts: localhost
  connection: local
  roles:
  - role: klusters.elasticsearch.check_health
```

License
-------

MIT
