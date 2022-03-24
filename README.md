# Ansible AVD TOI labs

This repository contains lab and exercise to support Arista AVD & CVP TOI.

## Disclaimer

All this content is linked to a TOI and cannot be used outside of a specific training environment.

To get access to training environment, please contact your Arista Networks representative.

## Repository Content

### Arista Ansible AVD collection labs

- Lab related to [arista.avd.eos_cli_config_gen](labfiles/ansible-avd-toi/arista.avd/eos-cli-config-gen-lab)
- Lab related to [arista.avd.eos_designs](labfiles/ansible-avd-toi/arista.avd/eos-designs-lab)

### Arista Ansible CV collection labs

- Ansible CV [module overview](labfiles/ansible-avd-toi/arista.cvp/arista.cvp-overview)
- [Manage configlets](labfiles/ansible-avd-toi/arista.cvp/arista.cvp-cv-configlets) in Cloudvision
- [Manage containers](labfiles/ansible-avd-toi/arista.cvp/arista.cvp-cv-containers) in Cloudvision
- [Play with devices](labfiles/ansible-avd-toi/arista.cvp/arista.cvp-cv-device) in Cloudvision

## Getting started

```bash
# Clone repository
git clone https://github.com/titom73/ansible-avd-cvp-toi.git
cd ansible-avd-cvp

# Update Cloudvision password in inventory
sed -r 's/ansible_password: arista/ansible_password: <PUT YOUR PASSWORD HERE>/g' arista.cvp/inventory.yml
```

## License

Published under Apache2 license
