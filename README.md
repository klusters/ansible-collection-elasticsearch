# Ansible Collection - klusters.elasticsearch
[Inspired by ericsysmin.system](https://galaxy.ansible.com/ericsysmin/system)

Ansible collection that holds roles, that can be used with Elasticsearch Clusters. 

## Roles

| Role      | Build Status                                                                                                                                                                                                                                                        | Documentation                                                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
|  check_elasticsearch   | ![klusters.elasticsearch.check_health](https://github.com/klusters/ansible-collection-elasticsearch/workflows/klusters.elasticsearch.check_health/badge.svg)          | [Documentation](https://github.com/klusters/ansible-collection-elasticsearch/tree/master/roles/etc_hosts)    |

## Usage

You can find specific to each role within the "Documentation" link for each role. However, most should be in this format:

Install this ansible collection :
```bash
ansible-galaxy collection install klusters.elasticsearch
```

Write a playbook file *playbook_name.yml* :

```yaml
---
- hosts: localhost

  tasks:
    - include_role:
        name: klusters.elasticsearch.<role_name>
```

Run *playbook_name.yml* :
```bash
ansible-playbook playbook_name.yml
```

## Testing

Testing is done through GitHub Actions, and can be tested locally as well.

To be able to test locally:
- install docker & molecule 
- run molecule test

For example, on MacOS:
```bash
pip install molecule[docker]
```

Each workflow pertains to a single role, and can be launched locally using the following command:

```bash
molecule test -s <role_name>
```
