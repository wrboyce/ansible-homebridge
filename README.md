wrboyce.homebridge
==================

[![Build Status](https://travis-ci.org/wrboyce/ansible-homebridge.svg)](https://travis-ci.org/wrboyce/ansible-homebridge)

Install and configure [Homebridge](https://github.com/nfarina/homebridge).


Role Variables
--------------

`homebridge_plugins` defines the homebridge plugins which should be installed.

Very similar to homebridge, uses the variables `homebridge_name`, `homebridge_username`, `homebridge_port`,
`homebridge_pin`, and `homebridge_description` for basic configuration.

`homebridge_accessories` and `homebridge_platforms` should be the same as with homebridge's configuration,
but in YAML form.

Example Configuration
---------------------

```yml
---
homebridge_plugins:
  - harmonyhub
  - philipshue

homebridge_username: "{{ vault_homebridge_username }}"
homebridge_pin: "{{ vault_homebridge_pin }}"

homebridge_platforms:
  - platform: HarmonyHub
    name: Harmony Hub
  - platform: PhilipsHue
    name: Hue
    ip_address: "{{ vault_homebridge_platforms_philipshue_ipaddress }}"
    username: "{{ vault_homebridge_platforms_philipshue_username }}"
```


Example Playbook
----------------

```yml
- hosts: homebridge-server
  roles:
     - wrboyce.homebridge
```

License
-------

Apache 2.0
