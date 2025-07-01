# Ansible Role: Valkey

[![CI](https://github.com/back-2-95/ansible-role-valkey/actions/workflows/ci.yml/badge.svg)](https://github.com/back-2-95/ansible-role-valkey/actions/workflows/ci.yml)

Installs and configures Valkey server

## Requirements

- Ubuntu server

## The initial version does the following

- Finds out Docker gateway IP address e.g. `172.17.0.1`
- Install `valkey` package with APT
- Creates override configuration file in `/etc/valkey/conf.d/overrides.conf`
- Adds Docker gateway IP to `bind` setting
- Sets `protected-mode` to `no` >> NOTE that is when you have firewalled access to your server!!

## Dependencies

None.

## Require this role

Add the following to your requirements.yml:

```yaml
---
roles:
  - name: back-2-95.valkey
    src: https://github.com/back-2-95/ansible-role-valkey
    version: main
    scm: git
```

## Example Playbook

```yaml
- hosts: all
  roles:
    - back-2-95.valkey
```

## On the server:

Validate current values with `valkey-cli`:

```console
valkey-cli CONFIG GET port
1) "port"
2) "6379"
```

```console
valkey-cli CONFIG GET protected-mode
1) "protected-mode"
2) "no"
```

```console
valkey-cli CONFIG GET bind
1) "bind"
2) "127.0.0.1 172.17.0.1"
```

## License

MIT
