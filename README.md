[![GitHub license](https://img.shields.io/github/license/PDOK/status_role)](https://github.com/PDOK/status_role/blob/main/LICENSE)
[![GitHub release](https://img.shields.io/github/release/PDOK/status_role.svg)](https://github.com/PDOK/status_role/releases)

# status_role

This role adds status information about deployed resources to the provided custom resource.

## Requirements

This role uses the k8s_info module.
This requires: 
- python >= 2.7
- openshift >= 0.6 
- PyYAML >= 3.11

This role uses the operator_sdk.util.k8s_status module
This requires:
- operator_sdk.util collection

This role uses the community.general.json_query filter
This requires:
- community.general collection
- jmespath

## Role Variables

- status_objects: a list of kubernetes objects which includes exactly 1 deployment.
- resource: the custom resource needed to make sure that always an ownerRefernce exists on a configmap.

## Example Playbook

    - hosts: servers
      include_role:
        name: status_roles
      vars:
        resource: "{{ _apiverison_kind }}"
        status_objects:
          - "{{ deployment }}"
          - "{{ configmap }}"
          - "{{ service }}"
          - "{{ autoscaler }}"
