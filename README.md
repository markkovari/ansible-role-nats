# NATS Ansible Role

![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/derhuerst/ansible-role-nats/ci.yaml?style=for-the-badge&logo=github)

NATS.io is a simple, secure, and high-performance open source messaging system for cloud-native applications, IoT messaging, and microservices architectures.
This Ansible role installs it and then provide its configuration.

## Installation

```yaml
# requirments.yaml
- src: git@github.com:derhuerst/ansible-role-nats.git
  scm: git
  version: main
  name: nats
```

## Role Variables

[see default variables](defaults/main.yml)

Please note that this Ansible provides a cluster installation of NATS, so you must group your hosts into the cluster and `nats_host_group` specifies the cluster.

## Example Playbook

```yaml
- hosts: some_servers
  roles:
    - nats
```
