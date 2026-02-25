# Ansible playbook for deploy vanila k8s cluster on debian based distributive

![top_history_mistake](./image.png)

- kube 1.35 etc version
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
venv/bin/ansible-galaxy collection install kubernetes.core

```

## Params

- [inventory](./hosts.yaml).
- [Cluster params](./group_vars/kube_cluster.yml).

### Install


```bash
ansible-playbook install-cluster.yml -i inventory/example.hosts.ini -b --user=<user> --ask-become-pass
```

### HA

```bash
ansible-playbook setup-ha-kubeapi-server.yaml -i inventory/example.hosts.ini -b --user=<user> --ask-become-pass
```


## Works
- Install single master cluster
- Install multi master cluster
- reset cluster
- setup HA kubeapi server extend edit kubelet.conf and configmaps

## Need more testing
- Upgrade cluster
