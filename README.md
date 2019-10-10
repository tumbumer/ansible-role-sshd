# tumbumer.sshd

Managing openssh-server configuration.

## Requirements (for localhost)

* [Vault](https://www.vaultproject.io)
* [hvac python library](https://pypi.org/project/hvac)

## Role Variables

### General (optional)

var | default | choices | description
---|---|---|---
tumbumer_sshd_update_config | false | false, true | Update /etc/ssh/sshd_config and restart ssh service
tumbumer_sshd_host_key_action | | create, update | Action for ssh host key
tumbumer_sshd_address | 0.0.0.0 | | sshd ipv4 address
tumbumer_sshd_port | 22 | | sshd ipv4 port

### Vault (required when tumbumer_sshd_host_key_action == update)

var | default | description
---|---|---|---
tumbumer_sshd_vault_url | <http://127.0.0.1:8200> | URL to vault service
tumbumer_sshd_vault_role_id | | Role id for a vault AppRole auth
tumbumer_sshd_vault_secret_id | empty string | Secret id for a vault AppRole auth
tumbumer_sshd_vault_private_key | | Path to private key, e.g. kv/ssh:privateKey
tumbumer_sshd_vault_public_key | | Path to public key, e.g. kv/ssh:publicKey

## Dependencies

None.

## Example Playbook

```yaml
---
- hosts: all
  vars:
  - tumbumer_sshd_update_config: true
  - tumbumer_sshd_host_key_action: update
  - tumbumer_sshd_address: "{{ ansible_default_ipv4.address }}"
  - tumbumer_sshd_port: 22
  - tumbumer_sshd_vault_role_id: some role id
  - tumbumer_sshd_vault_secret_id: some secret id
  - tumbumer_sshd_vault_private_key: kv/sshHost:privateKey
  - tumbumer_sshd_vault_public_key: kv/sshHost:publicKey
  roles:
  - tumbumer.sshd
```

## License

Apache-2.0
