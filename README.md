# palava-ansible

## Get Started

- Install ansible (prefer newer ansible versions which are python 3 compatible)
- Copy `ansible.cfg.example` to `ansible.cfg`

## Deploy: Palava Production System

Please note: Replace <ENVIRONMENT> with either **production** or **staging** in the commands below

### Signal tower

- `ansible-playbook -i environments/<ENVIRONMENT>/inventory.yml playbooks/install_signaltower.yml`

### Palava Web

- `ansible-galaxy collection install community.general` (node)
- `ansible-playbook -i environments/<ENVIRONMENT>/inventory.yml playbooks/install_palava_web.yml`

## Deploy: Monitoring (Optional)

Requirements: jmespath (deployer host), unzip (target host)

### Grafana

- `ansible-galaxy install cloudalchemy.grafana`
- `ansible-playbook -i environments/monitoring/inventory.yml playbooks/install_grafana.yml`

### Prometheus

- `ansible-galaxy install cloudalchemy.prometheus`
- `ansible-playbook -i environments/monitoring/inventory.yml playbooks/install_prometheus.yml`
