# Ansible Role: Valkey

Installs and configures Valkey server

## Requirements

- Ubuntu server

## Initial version does the following

- Finds out Docker gateway IP address e.g. `172.17.0.1`
- Install `valkey` package with APT
- Creates override configuration file in `/etc/valkey/conf.d/overrides.conf`
- Adds Docker gateway IP to `bind` setting
- Sets `protected-mode` to `no` >> NOTE that is when you have firewalled access to your server!!

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
