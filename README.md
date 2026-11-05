# Mother-of-All-Self-Hosting Ansible playbook

[![Support room on Matrix](https://img.shields.io/matrix/mash-playbook:devture.com.svg?label=%23mash-playbook%3Adevture.com&logo=matrix&style=for-the-badge&server_fqdn=matrix.devture.com&fetchMode=summary)](https://matrixrooms.info/room/mash-playbook:devture.com) [![donate](https://liberapay.com/assets/widgets/donate.svg)](https://liberapay.com/mother-of-all-self-hosting/donate) [![REUSE status](https://api.reuse.software/badge/github.com/mother-of-all-self-hosting/mash-playbook)](https://api.reuse.software/info/github.com/mother-of-all-self-hosting/mash-playbook)

**MASH** (**M**other-of-**A**ll-**S**elf-**H**osting) is an [Ansible](https://www.ansible.com/) playbook that helps you self-host [more than 250 services](docs/supported-services.md) as [Docker](https://www.docker.com/) containers on your own server.

By running services in containers, we can have a predictable and up-to-date setup, across multiple supported distros and CPU architectures.

[Installation](docs/README.md) (upgrades) and some maintenance tasks are automated using [Ansible](https://www.ansible.com/) (refer to [our Ansible guide](docs/ansible.md)).

## ✨ Why MASH?

- **One playbook, one config file.** All your services are configured in a single `vars.yml` file. Trying out a new service usually takes a few lines.
- **Shared pieces are set up for you.** A [Traefik](components/traefik/README.md) reverse proxy with automatic HTTPS certificates, a [Postgres](components/postgres/README.md) database server and an [email relay](components/exim_relay/README.md) are installed once and shared by all your services.
- **Easy upgrades.** Update the playbook and run it again to [upgrade all services](docs/maintenance-upgrading-services.md).
- **Simpler backups.** All services keep their data in one place on the server and share one Postgres server, so [one backup setup](components/backup_borg/README.md) covers them all.
- **Your setup is just configuration.** Keep your `vars.yml` in version control and re-run the playbook to set up the same services on another server.

## ✔ Supported services

Some of the services you can install:

- **Files and photos**: [Nextcloud](components/nextcloud/README.md), [Immich](components/immich/README.md), [Syncthing](components/syncthing/README.md), [Copyparty](components/copyparty/README.md)
- **Media**: [Jellyfin](components/jellyfin/README.md), [Navidrome](components/navidrome/README.md), [audiobookshelf](components/audiobookshelf/README.md), [PeerTube](components/peertube/README.md)
- **Passwords and sign-in**: [Vaultwarden](components/vaultwarden/README.md), [authentik](components/authentik/README.md), [Keycloak](components/keycloak/README.md), [Authelia](components/authelia/README.md)
- **Documents and notes**: [Paperless-ngx](components/paperless/README.md), [Collabora Online](components/collabora_online/README.md), [Outline](components/outline/README.md), [BookStack](components/bookstack/README.md)
- **Code**: [Forgejo](components/forgejo/README.md), [Gitea](components/gitea/README.md), [GitLab](components/gitlab/README.md), [Woodpecker CI](components/woodpecker_ci_server/README.md)
- **Communication**: [Jitsi](components/jitsi/README.md), [GoToSocial](components/gotosocial/README.md), [Mumble](components/mumble/README.md), [ntfy](components/ntfy/README.md)
- **Networking and monitoring**: [Headscale](components/headscale/README.md), [WireGuard Easy](components/wg_easy/README.md), [AdGuard Home](components/adguard_home/README.md), [Uptime Kuma](components/uptime_kuma/README.md), [Prometheus](components/prometheus/README.md), [Grafana](components/grafana/README.md)

Refer to the [full list of supported services](docs/supported-services.md). We keep adding support for more [FOSS](https://en.wikipedia.org/wiki/Free_and_open-source_software).

## 🚀 Getting started

Follow the [installation guide](docs/README.md), starting with the [prerequisites](docs/prerequisites.md). We recommend starting with a few services: you can add or remove services later by re-running the playbook.

Once the playbook is set up, adding a service usually takes two lines in your `vars.yml` file:

```yaml
jellyfin_enabled: true
jellyfin_hostname: jellyfin.example.com
```

Then run the playbook again:

```sh
just install-all
```

## 🆕 Changes

This playbook evolves over time, sometimes with backward-incompatible changes.

When updating the playbook, refer to [the changelog](CHANGELOG.md) to catch up with what's new.

## 🆘 Support

- Matrix room: [#mash-playbook:devture.com](https://matrixrooms.info/room/mash-playbook:devture.com). To join Matrix, [use a public server](https://app.element.io) like `matrix.org` or self-host Matrix yourself using the related [matrix-docker-ansible-deploy](https://github.com/spantaleev/matrix-docker-ansible-deploy) Ansible playbook

- GitHub issues: [mother-of-all-self-hosting/mash-playbook/issues](https://github.com/mother-of-all-self-hosting/mash-playbook/issues)

## 🤝 Related

- [matrix-docker-ansible-deploy](https://github.com/spantaleev/matrix-docker-ansible-deploy): a sister playbook for running a [Matrix](https://matrix.org) server. MASH can install services on the same server (refer to [this page](docs/setting-up-services-on-mdad-server.md)).

## ❓ What's with the name?

Our goal is to create a large Ansible playbook which can be your all-in-one-toolkit for self-hosting services in a clean and reliable way.

We like the MASH acronym, and [mashing](https://en.wikipedia.org/wiki/Mashing) is popular in the alcohol brewing industry. The result of all that mash is an enjoyable (at least by some) product.

Then, there's mixing and mashing stuff, which is also what this Ansible playbook is all about - you can mix and mash various pieces of software to create the self-hosted stack of your dreams!
