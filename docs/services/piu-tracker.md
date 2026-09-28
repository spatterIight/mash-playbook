<!--
SPDX-FileCopyrightText: 2020 - 2024 MDAD project contributors
SPDX-FileCopyrightText: 2020 - 2024 Slavi Pantaleev
SPDX-FileCopyrightText: 2024 - 2026 Suguru Hirahara
SPDX-FileCopyrightText: 2026 spatterlight

SPDX-License-Identifier: AGPL-3.0-or-later
-->

# pump-it-up-tracker

The playbook can install and configure [pump-it-up-tracker](https://github.com/spatterIight/pump-it-up-tracker) for you.

pump-it-up-tracker is a read-only web application for personal tracking of [Pump It Up](https://www.piugame.com/) scores, which you log as Ansible variables.

See the project's [documentation](https://github.com/spatterIight/pump-it-up-tracker#readme) to learn what pump-it-up-tracker does and why it might be useful to you.

For details about configuring the [Ansible role for pump-it-up-tracker](https://github.com/spatterIight/ansible-role-piu-tracker), you can check them via:

- 🌐 [the role's documentation](https://github.com/spatterIight/ansible-role-piu-tracker/blob/main/docs/configuring-piu-tracker.md) online
- 📁 `roles/galaxy/piu_tracker/docs/configuring-piu-tracker.md` locally, if you have [fetched the Ansible roles](../installing.md)

## Dependencies

This service requires the following other services:

- [Traefik](traefik.md) reverse-proxy server

## Configuration

To enable this service, add the following configuration to your `vars.yml` file and re-run the [installation](../installing.md) process:

```yaml
########################################################################
#                                                                      #
# piu-tracker                                                          #
#                                                                      #
########################################################################

piu_tracker_enabled: true

piu_tracker_hostname: piu.example.com

########################################################################
#                                                                      #
# /piu-tracker                                                         #
#                                                                      #
########################################################################
```

### Adding your scores

Scores are logged as entries in `piu_tracker_scores`, one per result screen. See [this section](https://github.com/spatterIight/ansible-role-piu-tracker/blob/main/docs/configuring-piu-tracker.md#add-your-scores) on the role's documentation for details.

## Usage

After running the command for installation, pump-it-up-tracker becomes available at the URL specified with `piu_tracker_hostname`. With the configuration above, the service is hosted at `https://piu.example.com`.

To log new scores, add them to `piu_tracker_scores` and re-run the installation process.

## Troubleshooting

See [this section](https://github.com/spatterIight/ansible-role-piu-tracker/blob/main/docs/configuring-piu-tracker.md#troubleshooting) on the role's documentation for details.
