ansible-role-userli
==================

[![Build Status](https://travis-ci.org/systemli/ansible-role-userli.svg?branch=master)](https://travis-ci.org/systemli/ansible-role-userli)

This role installs Userli, a web application to (self-) manage email users
and encrypt their mailboxes. Find more information at
https://systemli.github.io/userli/.

Requirements
------------

  * composer
  * PHP >= 7.3
  * php-apcu
  * php-curl
  * php-gd
  * php-mbstring
  * php-mysql / php-pgsql
  * php-xml
  * php-zip
  * php-ctype
  * php-intl
  * MariaDB/MySQL/PostgreSQL/SQLite

Role Variables
--------------

Add files to `translations` or `userli/translations` to override the default strings
and their translations.

See `defaults/main.yml` for available role variables.

Dependencies
------------

There are no fixed dependencies, but you need PHP, a webserver and a database.
See `molecule/default/prepare.yml` for an example setup.

Example Playbook
----------------

See `molecule/default/playbook.yml` for an example playbook.

Tests
-----

Run local tests with

    molecule test

Requires Molecule, Vagrant and `python-vagrant` to be installed.

License
-------

GPLv3

Author Information
------------------

https://www.systemli.org
