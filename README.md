# Bitwardenrs

[![Build Status](https://travis-ci.com/dmaes/ansible-role-bitwardenrs.svg?branch=master)](https://travis-ci.com/dmaes/ansible-role-bitwardenrs)

Builds, installs and configures [Bitwarden_RS](https://github.com/dani-garcia/bitwarden_rs) (without Docker).

Currently, only sqlite3 backend is supported.
Also, not all configuration can be done via role variables yet.

*Only tested on Debian 10 and CentOS 8*

## Requirements
* Requirements for the [unarchive](https://docs.ansible.com/ansible/latest/modules/unarchive_module.html)-module
* Requirements for the [package](https://docs.ansible.com/ansible/latest/modules/package_module.html)-module
* Systemd
* SQLite3
* wget or curl

## Role Variables
| Variable | Description | Default value |
| --- | --- | --- |
| `bitwardenrs_directory` | Where to install Bitwarden_RS | `/opt/bitwarden_rs` |
| `bitwardenrs_version` | Which version to install | `1.16.3` |
| `bitwardenrs_webvault` | Install the patched webvault | `true` |
| `bitwardenrs_webvault_version` | Version of the webvault to install | `2.15.1` |
| `bitwardenrs_config` | Key-value environment variables for the Bitwarden_RS `.env` file | `{ DOMAIN: "https://{{ ansible.fqdn }}/" }` |

## Example Playbook
```yaml
- hosts: servers
  roles:
    - dmaes.bitwardenrs
```

## License
MIT
