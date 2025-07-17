[![status](https://img.shields.io/badge/status-active-brightgreen)](#project-status)
[![release](https://img.shields.io/github/v/release/trallnag/ansible-role-systemd-unit)](https://github.com/trallnag/ansible-role-systemd-unit/releases)
[![ci](https://img.shields.io/github/actions/workflow/status/trallnag/ansible-role-systemd-unit/ci.yaml?label=ci)](https://github.com/trallnag/ansible-role-systemd-unit/actions/workflows/ci.yaml)
[![release](https://img.shields.io/github/actions/workflow/status/trallnag/ansible-role-systemd-unit/release.yaml?label=release)](https://github.com/trallnag/ansible-role-systemd-unit/actions/workflows/release.yaml)

# Ansible Role `trallnag.systemd_unit`

Role that set ups a systemd unit. Depending on the configuration, the role will
take care of reloading the daemon, verifying the unit file, activating it, and
restarting it.

Available on
[Ansible Galaxy](https://galaxy.ansible.com/ui/standalone/roles/trallnag/systemd_unit).

## Requirements

Some tasks require root privileges. Privilege escalation is performed with
explicit `become: true` statements.

## Role parameters

See [`meta/argument_specs.yml`](./meta/argument_specs.yml).

```yaml
systemd_unit__name:
  type: str
  required: true
  description: >-
    Full name of the systemd unit. For example "rclone-sync.timer".

systemd_unit__content:
  type: str
  required: true
  description: >-
    The systemd unit itself. For example the content of the "rclone-sync.timer"
    file.

systemd_unit__activate:
  type: bool
  required: false
  default: false
  description: >-
    Should the unit be activated? Activation means: Unmask, enable, s and
    restart if already active.

systemd_unit__restart:
  type: bool
  required: false
  default: false
  description: >-
    Should the unit be restarted if it was already active and the uni file
    itself did not change? For example useful to trigger restart if script
    changed that is executed by service.

systemd_unit__running_check:
  type: str
  required: false
  default: false
  description: >-
    Should a `systemctl is-active` be performed at the end of the rol ensure
    unit is running?

systemd_unit__running_check_delay:
  type: str
  required: false
  default: "0"
  description: >-
    Time in seconds to wait before performing check to see if unit is running at
    end of role. Only relevant if `systemd_unit_running_ch is set to `true`.
    Decimals (as string) supported. Pause only done if unit enabled, started, or
    restarted by role.
```

## Project status

The project is maintained by me, [Tim](https://github.com/trallnag), and I am
interested in keeping it alive as I am actively using it.

## Versioning

The project follows [Semantic Versioning](https://semver.org/).

## Contributing

Contributions are welcome. Please refer to [`CONTRIBUTE.md`](./CONTRIBUTE.md).

## Licensing

This work is licensed under the
[ISC license](https://en.wikipedia.org/wiki/ISC_license). See
[`LICENSE`](./LICENSE) for the license text.

## Template

This project is based on the following
[Copier](https://copier.readthedocs.io/en/stable/) template:
<https://github.com/trallnag/copier-template-ansible-role>.
