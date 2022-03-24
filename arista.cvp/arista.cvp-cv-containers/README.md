# LAB 04 - Manage Containers on CloudVision.

## About

Create and update containers on CloudVision.

## Execute lab

__1. Review containers vars__

```yaml
$ cat group_vars/CVP.yml

---
CVP_CONTAINERS:
  TRAINING:
    parentContainerName: Tenant
  TRAINING_DC:
    parentContainerName: TRAINING
  TRAINING_LEAFS:
    parentContainerName: TRAINING_DC
  TRAINING_SPINES:
    parentContainerName: TRAINING_DC
```

__2. Create continers__

```shell
$ ansible-playbook playbook.container.yml
```


__3. Optional: Attach TRAINING-01 to TRAINING container__

Edit [CVP.yml](group_vars/CVP.yml) file

```
$ vim group_vars/CVP.yml
```

And update content with

```yaml
---
CVP_CONFIGLETS:
  01TRAINING-alias: "alias a{{ 999 | random }} show version"
  01TRAINING-01: "alias a{{ 999 | random }} show version"

CVP_CONTAINERS:
  TRAINING:
    parentContainerName: Tenant
    configlets:
      - 'TRAINING-01'
  TRAINING_DC:
    parentContainerName: TRAINING
  TRAINING_LEAFS:
    parentContainerName: TRAINING_DC
  TRAINING_SPINES:
    parentContainerName: TRAINING_DC
```

Run playbook and check on CloudVision

> On cloudvision server, cancel task and move back device to its initial container

__4. Remove Container topology__

Edit playbook and change mode to `delete`

```yaml
- name: "Configure containers on {{inventory_hostname}}"
  arista.cvp.cv_container:
    cvp_facts: "{{CVP_FACTS.ansible_facts}}"
    topology: "{{CVP_CONTAINERS}}"
    state: absent
    register: CVP_CONTAINERS_RESULT
```
