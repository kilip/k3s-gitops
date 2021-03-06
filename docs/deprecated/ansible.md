# Ansible

Various playbooks to help integrate or destroy your k3s cluster

## Provision playbook

> **Caution:** This playbook will provision your operating systems to be most compatible with Kubernetes

```bash
env ANSIBLE_CONFIG=ansible/ansible.cfg ansible-playbook \
  -i ansible/inventory \
  ansible/main.yml --ask-become-pass
```

## Ping Cluster

```bash
env ANSIBLE_CONFIG=ansible/ansible.cfg ansible \
  -i ansible/inventory k3s_cluster -m ping
```

## Reboot cluster

```bash
env ANSIBLE_CONFIG=ansible/ansible.cfg ansible -b \
      all -i ansible/inventory -m shell -a "/sbin/shutdown -r now"
```

:warning: Caution Dangerzone Below :warning:

## Teardown k3s cluster playbook

> **Caution:** This playbook will complete destroy your k3s Cluster

```bash
env ANSIBLE_CONFIG=ansible/ansible.cfg ansible-playbook \
  -i ansible/inventory \
  ansible/teardown-k3s.yml --ask-become-pass
```

## Teardown rook-ceph playbook

> **Caution:** This playbook will complete destroy your ceph cluster and delete all data

```bash
env ANSIBLE_CONFIG=ansible/ansible.cfg ansible-playbook \
  -i ansible/inventory \
  ansible/teardown-rook-ceph.yml --ask-become-pass
```


