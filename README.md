# NATS Ansible Role

[![ci](https://github.com/markkovari/ansible-role-nats/actions/workflows/ci.yaml/badge.svg)](https://github.com/markkovari/ansible-role-nats/actions/workflows/ci.yaml)

NATS.io is a simple, secure, and high-performance open source messaging system for cloud-native applications, IoT messaging, and microservices architectures.
This Ansible role installs it and then provide its configuration.

## Installation

```yaml
# requirments.yaml
- src: git@github.com:markkovari/ansible-role-nats.git
  scm: git
  version: main
  name: nats
```

## Role Variables

[see default variables](defaults/main.yaml)

> [!TIP]
> With `nats_cluster_enabled: true`, this Ansible role will deploy a [cluster installation of NATS](). You must group your hosts into a group and specify this group in `nats_host_group`.

## Example Playbook

```yaml
- hosts: some_servers
  roles:
    - nats
```
