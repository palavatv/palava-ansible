# palava-ansible

## Get Started

- Install ansible (prefer newer ansible versions which are python 3 compatible)
- Copy `ansible.cfg.example` to `ansible.cfg`

## Deploy: Palava Production System

Please note: Replace <ENVIRONMENT> with either **production** or **staging** in the commands below

### Signal tower
- to enable turn:
  - set `palava_signaltower_turn_enabled` to `yes`
  - set `palava_signaltower_turn_secret`
- `ansible-playbook -i environments/<ENVIRONMENT>/inventory.yml playbooks/install_signaltower.yml`

### Palava Web

- `ansible-galaxy collection install community.general` (node)
- `ansible-playbook -i environments/<ENVIRONMENT>/inventory.yml playbooks/install_palava_web.yml`

## Deploy: Monitoring (Optional)

Requirements: jmespath (deployer host), unzip (target host)

Adjust inventory and config variables in `environments/monitoring/group_vars/monitoring/main.yml` before prodceeding.

### Prometheus + Grafana + Alert Manager

- `ansible-galaxy install cloudalchemy.alertmanager`
- `ansible-playbook -i environments/monitoring/inventory.yml playbooks/install_monitoring.yml`