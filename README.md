# Ansible playbook for deploy k8s cluster

- kube 1.34 etc version
- HA cluster
- calico, etc
- containerd, etc
- nodelocaldns
- VIP for kubeapi server

```bash
python3 -m venv venv
venv/bin/pip3 install "ansible-core<2.17"

venv/bin/ansible-galaxy collection install community.general
venv/bin/ansible-galaxy collection install ansible.posix
```

## Params

- [inventory](./hosts.yaml).
- [Cluster params](./group_vars/kube_cluster.yml).

### Install

```bash
ansible-playbook install-cluster.yaml -b --user=<user> --ask-become-pass
# ansible-playbook install-cluster.yaml -b --user=root
```

### HA

```bash
ansible-playbook setup-ha-kubeapi-server.yaml -b --user=<user> --ask-become-pass
```

## Works
- Install single master cluster
- Install multi master cluster
- reset cluster
- setup HA kubeapi server extend edit kubelet.conf and configmaps

## Need more testing
- Upgrade cluster