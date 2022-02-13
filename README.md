nodenv
========

Role for installing [nodenv](https://github.com/nodenv/nodenv).

TODO
------------

- Add `system` install
- Add the ability to use a proxy for installation

Requirements
------------

none

Role Variables
--------------

Default variables are:

```yaml
nodenv:
  version: v1.4.0
  default_nodejs: 16.14.0
  nodejs:
    - version: '16.14.0'

nodenv_clean_up: false

nodenv_repo: 'https://github.com/nodenv/nodenv.git'

nodenv_plugins:
  - { name: 'nodenv-vars', repo: 'https://github.com/nodenv/nodenv-vars.git', version: 'master' }
  - { name: 'node-build', repo: 'https://github.com/nodenv/node-build.git', version: 'master' }
  - { name: 'nodenv-default-packages', repo: 'https://github.com/nodenv/nodenv-default-packages.git', version: 'master' }
  - { name: 'nodenv-update', repo: 'https://github.com/nodenv/nodenv-update.git', version: 'master' }

nodenv_root: "~/.nodenv"

nodenv_users: [ ]

nodenv_extra_depends: [ ]
nodenv_apt_packages:
  - build-essential
  - git
  - libcurl4-openssl-dev
  - libffi-dev
  - libreadline-dev
  - libssl-dev
  - libxml2-dev
  - libxslt1-dev
  - zlib1g-dev
```

Description:

- ` nodenv.version ` - Version of `nodenv` to
  install ([nodenv releases page](https://github.com/nodenv/nodenv/releases))
- ` nodenv.default_nodejs ` - Which Nodejs version to be set as global rbenv ruby.
- ` nodenv.nodejs ` - Versions of Nodejs to install. E.g. `[ {version: '16.14.0'},{version: '17.5.0'} ]`
- ` nodenv_clean_up ` - Delete all Nodejs versions not listed in the `nodenv.nodejs`. Default value is `false`
- ` nodenv_repo ` - Repository with source code of `nodenv` to install
- ` nodenv_plugins ` - Array of Hashes with information about plugins to install
- ` nodenv_root ` - Install path
- ` nodenv_users ` - Array of usernames for multiuser install. User must be present in the system
- ` nodenv_extra_depends` - Array of extra system packages to install before compiling Nodejs
- ` nodenv_tmpdir ` - A temporary directory path used for artifacts when installing Nodejs. Defaults to
  system's `$TMPDIR`

Example:

```yaml
- hosts: localhost
  gather_facts: true
  vars:
    nodenv:
      version: v1.4.0
      default_nodejs: 16.14.0
      nodejs:
        - version: 16.14.0
      nodenv_users:
        - appuser
  roles:
    - role: nodenv
```

Dependencies
------------

none

License
-------

MIT

Author Information
------------------

[YouSysAdmin](http://github.com/YouSysAdmin)
