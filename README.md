# ansible-role-userli

[![Integration](https://github.com/systemli/ansible-role-userli/actions/workflows/main.yml/badge.svg)](https://github.com/systemli/ansible-role-userli/actions/workflows/main.yml)

This role installs Userli, a web application to (self-) manage email users
and encrypt their mailboxes. Find more information at
<https://systemli.github.io/userli/>.

## Requirements

* composer
* PHP >= 8.4
* php-apcu (optional)
* php-curl
* php-gd
* php-mbstring
* php-mysql
* php-opcache
* php-xml
* php-zip
* php-ctype
* php-intl
* php-redis (optional, for Redis cache)
* MariaDB/MySQL on the same host

The role only supports MariaDB/MySQL. It manages the database and the database
user through the local socket `/run/mysqld/mysqld.sock`.

## Deployment

The role pins a Userli version in `userli_version`. To install Userli for the
first time or to deploy a new version, run the role with `userli_update`:

```shell
ansible-playbook userli.yml -e userli_update=true
```

This stops the webserver and the background services, clears and warms up the
cache, runs the database migrations and starts everything again.

If the installed version differs from `userli_version` and `userli_update` is
not set, the role fails before changing anything.

## Role Variables

Add files to `translations` or `userli/translations` to override the default strings
and their translations.

See `defaults/main.yml` for available role variables.

With `userli_prometheus_textfile_collector_enabled`, the role installs a
systemd timer that writes metrics for the node exporter textfile collector. It
installs `moreutils` for `sponge`.

## Dependencies

There are no fixed dependencies, but you need PHP, a webserver and a database.
See `molecule/default/prepare.yml` for an example setup.

## Example Playbook

See `molecule/default/converge.yml` for an example playbook.

## Tests

For developing and testing the role we use Github Actions, Molecule, and Docker.

Run local tests with:

```shell
molecule test
```

## License

GPLv3

## Author Information

<https://www.systemli.org>
