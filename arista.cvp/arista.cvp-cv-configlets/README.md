# LAB 03 - Manage Configlet on Cloudvision.

## About

Create, Update and Delete configlets on CloudVision.

## Execute lab

__1. Review configlet vars__

```shell
$ cat group_vars/CVP.yml

---
CVP_CONFIGLETS:
  TRAINING-01: "alias a{{ 999 | random }} show version"
  TRAINING-02: "alias a{{ 999 | random }} show version"
```

__2. Create 2 new configlets on CloudVision server.__

```shell
$ ansible-playbook playbook.configlet.yml
```

__3. Optional: Add a new configlet from file__

Create configlet with content of file [configlet.txt](configlet.txt)

Edit [CVP.yml](group_vars/CVP.yml) file

```
$ vim group_vars/CVP.yml
```

And update content with

```yaml
---
CVP_CONFIGLETS:
  TRAINING-01: "alias a{{ 999 | random }} show version"
  TRAINING-02: "alias a{{ 999 | random }} show version"
  TRAINING-03: "{{lookup('file', '../configlet.txt')}}"
```

Run playbook and check on CloudVision

__4. Remove configlets TRAINING-* from CloudVision__

Edit playbook to change `state` in `arista.cvp.cv_configlet_v3` to `absent`

```yaml
- name: "Configure configlet on {{inventory_hostname}}"
  arista.cvp.cv_configlet_v3:
    configlets: "{{CVP_CONFIGLETS}}"
    state: absent
  register: CVP_CONFIGLET_RESULT
```

Run playbook and check on CloudVision
