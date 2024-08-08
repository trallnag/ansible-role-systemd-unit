# Ansible Role `trallnag.systemd_unit` <!-- omit from toc -->

Role that set ups a systemd unit. Depending on the configuration, the role will
take care of reloading the daemon, verifying the unit file, activating it, and
restarting it.

Available on
[Ansible Galaxy](https://galaxy.ansible.com/ui/standalone/roles/trallnag/systemd_unit).

## Table of Contents <!-- omit from toc -->

- [Requirements](#requirements)
- [Role Parameters](#role-parameters)
- [Project Status](#project-status)
- [Contributing](#contributing)
- [Licensing](#licensing)

## Requirements

Some tasks require root privileges. Privilege escalation is performed with
explicit `become: true` statements.

## Role Parameters

See [`meta/argument_specs.yml`](meta/argument_specs.yml).

```yaml
systemd_unit_name:
  type: str
  required: true
  description: >-
    Full name of the systemd unit. For example "rclone-sync.timer".

systemd_unit_content:
  type: str
  required: true
  description: >-
    The systemd unit itself. For example the content of the "rclone-sync.timer"
    file.

systemd_unit_activate:
  type: bool
  required: false
  default: false
  description: >-
    Should the unit be activated? Activation means: Unmask, enable, s and
    restart if already active.

systemd_unit_restart:
  type: bool
  required: false
  default: false
  description: >-
    Should the unit be restarted if it was already active and the uni file
    itself did not change? For example useful to trigger restart if script
    changed that is executed by service.

systemd_unit_running_check:
  type: str
  required: false
  default: false
  description: >-
    Should a `systemctl is-active` be performed at the end of the rol ensure
    unit is running?

systemd_unit_running_check_delay:
  type: str
  required: false
  default: "0"
  description: >-
    Time in seconds to wait before performing check to see if unit is running at
    end of role. Only relevant if `systemd_unit_running_ch is set to `true`.
    Decimals (as string) supported. Pause only done if unit enabled, started, or
    restarted by role.
```

## Project Status

Maintained and actively used.

## Contributing

Contributions are welcome. Please refer to [`CONTRIBUTING.md`](CONTRIBUTING).

Consult [`DEVELOPMENT.md`](DEVELOPMENT.md) for guidance regarding development.

Read [`RELEASE.md`](RELEASE.md) for details about the release process.

## Licensing

This work is licensed under the
[Apache License](https://choosealicense.com/licenses/apache-2.0) (Apache-2.0), a
permissive license whose main conditions require preservation of copyright and
license notices. See [`LICENSE`](LICENSE) for the license text.

This work comes with an explicit [`NOTICE`](NOTICE) file containing additional
legal notices and information.
