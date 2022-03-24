# CloudVision Collection overview

## About

Basic commands to test ansible with a basic installation.

> Prior to run the lab, update [inventory file](./../invengtory.yml) with your CV credentials

## Execute lab

__1. Install `arista.cvp` collection.__

```shell
# Install documentation.
$ ansible-galaxy collection install arista.cvp:==3.3.1

# Display module documentation.
$ ansible-doc arista.cvp.cv_facts_v3
```

__2. Collect facts from CloudVision.__

```shell
$ ansible-playbook playbook.facts.yml
```

__3. Optional: Collect only facts for devices__

Get and display facts of active devices.

```yaml
- name: "Gather CVP facts {{inventory_hostname}}"
    arista.cvp.cv_facts:
      facts:
        - devices
    register: cv_facts
```

__4. Optional: Collect only facts for SPINE devices__

Get and display facts of active devices with spine in their hostname.

```yaml
- name: "Gather CVP facts {{inventory_hostname}}"
    arista.cvp.cv_facts:
      facts:
        - devices
      regexp_filter: .*spine.*
    register: cv_facts
```
