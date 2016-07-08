fabkit
======

Fabric-based Provisioning Toolkit for Linux and MacOSX

[![wercker status](https://app.wercker.com/status/f2cd44bd90931f136e21ad448a25d240/m "wercker status")](https://app.wercker.com/project/bykey/f2cd44bd90931f136e21ad448a25d240)
[![](https://imagelayers.io/badge/dceoy/dev:latest.svg)](https://imagelayers.io/?images=dceoy/dev:latest 'Get your own badge on imagelayers.io')

Requirements
------------

Python 2.x, Fabric, and python-yaml are required on a client.

```sh
# Ubuntu
$ sudo apt-get -y install fabric python-yaml

# CentOS
$ sudo yum -y install fabric python-yaml

# Fedora
$ sudo dnf -y install fabric python-yaml

# MacOSX
$ sudo /usr/bin/easy_install pip
$ sudo pip install -U fabric pyyaml
```

Usage
-----

```sh
$ fab -u [user name] -h [host address] <command>[:arg1,arg2]
```

| Command                           | Description                       | Platform                       |
|:----------------------------------|:----------------------------------|:-------------------------------|
| flow                              | Set up a development server       | Fedora, CentOS, Ubuntu, MacOSX |
| dev.setup_system                  | Install packages for system       | Fedora, CentOS, Ubuntu         |
| dev.setup_with_rpm(:yml)          | Install packages using dnf or yum | Fedora, CentOS                 |
| dev.setup_with_deb(:yml)          | Install packages using apt-get    | Ubuntu                         |
| dev.setup_with_brew(:yml)         | Install packages using homebrew   | MacOSX                         |
| dev.setup_py(:ver,yml)            | Set up Python 2 or 3 using pyenv  | Fedora, CentOS, Ubuntu, MacOSX |
| dev.setup_rb(:ver,yml)            | Set up Ruby using rbenv           | Fedora, CentOS, Ubuntu, MacOSX |
| dev.setup_go(:yml)                | Set up Go                         | Fedora, CentOS, Ubuntu, MacOSX |
| dev.setup_r(:yml)                 | Set up R                          | Fedora, CentOS, Ubuntu, MacOSX |
| dev.setup_cli                     | Set up Zsh and Vim                | Fedora, CentOS, Ubuntu, MacOSX |
| dev.setup_zsh(:zshrc)             | Set up Zsh                        | Fedora, CentOS, Ubuntu, MacOSX |
| dev.setup_vim(:vimrc)             | Set up Vim                        | Fedora, CentOS, Ubuntu, MacOSX |
| docker.run_nginx_autoindex(:port) | Run Nginx on Docker               | Fedora, CentOS, Ubuntu         |
| docker.run_rstudio_server(:port)  | Run RStudio Server on Docker      | Fedora, CentOS, Ubuntu         |
| local.config_git(:user,email)     | Set global options of Git         | Fedora, CentOS, Ubuntu, MacOSX |
| local.enable_nopass_sudo          | Enable sudo without password      | Fedora, CentOS                 |

- `flow` and `dev.setup_system` install the packages written at `config/*.yml`.
- () are optional arguments.
- `yml` are yaml files (default: `config/*.yml`).
- `ver` are versions of Python or Ruby (integer).
- `zshrc` and `vimrc` are run scripts (default: `template/_.*rc`).
- `docker.run_nginx_autoindex` run [dceoy/docker-nginx-autoindex](https://github.com/dceoy/docker-nginx-autoindex) making a home directory available at `/` of Nginx (default port: 80).
- `docker.run_rstudio_server` run [dceoy/docker-rstudio-server](https://github.com/dceoy/docker-rstudio-server) sharing a home directory (default port: 8787).
- Commands can use configurations in `~/.ssh/config`. (e.g., certificates, host names, and user names)

Example
-------

Several arguments are optional.

```sh
$ git clone https://github.com/dceoy/fabkit.git
$ cd fabkit
$ fab d   # equal to "fab -u ${USER} -H localhost dev"
```
