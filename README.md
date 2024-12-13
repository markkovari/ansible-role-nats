# NATS Ansible Role

> [!CAUTION]
> This role is still in development and not yet ready for production use yet.
> It probably will work for some use cases, but some of them are lacking or not yet implemented.

Feel free to open an issue or a pull request if you have any suggestions or improvements.

[![ci](https://github.com/markkovari/ansible-role-nats/actions/workflows/ci.yaml/badge.svg)](https://github.com/markkovari/ansible-role-nats/actions/workflows/ci.yaml)

NATS.io is a simple, secure, and high-performance open source messaging system for cloud-native applications, IoT messaging, and microservices architectures.
This Ansible role installs it and then provide its configuration.

> [!INFO]
> Currently creating the credentials file is manual and requires a bit of modification to the file. This _might_ be automated in the future.
## Creds file creation steps

1. install the [nsc tool](https://docs.nats.io/using-nats/nats-tools/nsc)
1. create a new operator account
```console
nsc add operator {{MyOperator}}
```
1. Find the operator account in the `~/.nkeys/{{MyOperator}}/` directory
1. Copy the `{{MyOperator}}.creds` file to the root of the project
1. Create a resolver file `{{MyOperator}}.res` with the following content
1. Create a new user account
```console
nsc add user {{MyUser}}
```
1. Create a resolver file `{{MyUser}}.conf` with the following content
```console
nsc generate config --nats-resolver > {{resolver.conf}}
```
where `{{resolver.conf}}` is the file created in the previous step, called the same as `nats_resolver_file_path_source` in the `defaults/main.yaml` file.
1. modify the file to target a jwt folder, which exists (should be created by ansible later)


Be careful not to commit the file, it contains sensitive information.
Use gitignore/ansible-vault/sops to protect the file.

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
