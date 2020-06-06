# tumbumer.sshd

Managing openssh-server configuration.

## Role Variables

### General (optional)

| var | default | choices | description |
|---|---|---|---|
| tumbumer_sshd_update_config | false | false, true | Update /etc/ssh/sshd_config and restart ssh service |
| tumbumer_sshd_host_key_action | | create, update | Action for ssh host key |
| tumbumer_sshd_address | | | sshd ipv4 address |
| tumbumer_sshd_port | 22 | | sshd ipv4 port |
| tumbumer_sshd_private_key | | | Host private key, required if tumbumer_sshd_host_key_action == "update" |
| tumbumer_sshd_public_key | | | Host public key, required if tumbumer_sshd_host_key_action == "update" |

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
  - tumbumer_sshd_private_key: "-----BEGIN OPENSSH PRIVATE KEY-----..." 
  - tumbumer_sshd_public_key: "ssh-ed25519 XXX..."
  roles:
  - tumbumer.sshd
```

## License

Apache-2.0
