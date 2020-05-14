# Ansible role: RIPE RPKI services

Install and configure [RIPE RPKI validator and RTR server](https://github.com/RIPE-NCC/rpki-validator-3) on Debian/Ubuntu servers.

## Requirements

None.

## Role Variables

Additional info you can find in `defaults/main.yml`:

### Variables for rpki-validator-3

```
RPKIvalidator: {
    deploy: false
    port: 8080
    address: localhost
}
```

    deploy: false

If set true to install and configure rpki-validator-3 service.

    port: 8080

Port which service is listen for.

    address: localhost

Listen ip address for service.

### Variables for rpki-rtr-server

```
RTRserver: {
    deploy: true
    port: 8081
    address: localhost
    RTRport: 8282
    RTRaddress: 0.0.0.0
}
```

     deploy: true

Set true to install and configure rpki-rtr server.

    port: 8081

Port which listen by rpki-rtr-server, statistics allowed on this port.

    address: localhost

IP address which listen by rpki-rtr-server, statistics allowed on this port.

    RTRport: 8282

Port at which RTR session is created.

    RTRaddress: 0.0.0.0

IP address for RTR session.

_Note: If you use `hash_behaviour=replace` in your ansible.cnf, you need to replace all variables or only needed parameters, otherwice variable will be overwriten._

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: rpkiserver
      vars:
        RPKIvalidator:
          deploy: true
          port: 8080
          host: 0.0.0.0
        RTRserver:
          deploy: true
          port: 8081
          host: 0.0.0.0
          RTRport: 8282
          RTRhost: 0.0.0.0

      roles:
         - role: romchi.ripe_rpki

Author Information
------------------

* [Roman Bulakh <bulah.roman@gmail.com>](https://github.com/romchi)
