
# Ansible Role:  `json_exporter`

This ansible role installs and configure [json_exporter](https://github.com/prometheus-community/json_exporter)


## Requirements & Dependencies

- None

### Operating systems

Tested on

* Arch Linux
* Debian based
    - Debian 10 / 11
    - Ubuntu 20.10
* RedHat based
    - CentOS 8 (**not longer supported**)
    - Alma Linux 8
    - Rocky Linux 8
    - Oracle Linux 8

## Usage

```
json_exporter_version: '0.4.0'

json_exporter_release: {}

json_exporter_system_group: json-exporter
json_exporter_system_user: json-exporter
json_exporter_config_dir: /etc/json_exporter

json_exporter_direct_download: false

json_exporter_logging: {}

json_exporter_web: {}

json_exporter_config: []
```

### `json_exporter_logging`

#### defaults

```yaml
json_exporter_logging:
  level: warn
  format: ""
```


### `json_exporter_web`

#### defaults

```yaml
json_exporter_web:
  listen_address: "127.0.0.1"
  listen_port: "7979"
```


### `json_exporter_config`

#### defaults

```yaml
json_exporter_config: []
```

#### example

```yaml
json_exporter_config:
  - name: example_global_value
    path: "{ .counter }"
    help: Example of a top-level global value scrape in the json
    labels:
      environment: beta # static label
      location: "planet-{.location}"          # dynamic label

  - name: mgob_backup
    type: object
    help: MongoDB Backup
    path: "{}"
    labels:
      environment: DEV      # static label
      id: '{[].plan}'       # dynamic label
    values:
      next_run: "{[].next_run}"
      last_run: "{[].last_run}"
      last_run_status: "{[].last_run_status}"
```


You can also look at the [molecule](molecule/default/group_vars/all) test.


## Contribution

Please read [Contribution](CONTRIBUTING.md)

## Development,  Branches (Git Tags)

The `master` Branch is my *Working Horse* includes the "latest, hot shit" and can be complete broken!

If you want to use something stable, please use a [Tagged Version](https://gitlab.com/bodsch/ansible-promtail/-/tags)!

---

## Author and License

- Bodo Schulz

## License

[Apache](LICENSE)

**FREE SOFTWARE, HELL YEAH!**
