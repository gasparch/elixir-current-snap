
# Purpose

This repository contains scripts to automate task of building -current version of Elixir and trying it out along with regular Elixir installation.

All build process is done in VM in order not to contaminate host system with
development packages. Snapcraft installs packages necessary for building in
host environment, which may intervene with normally installed packages.

Elixir build into snap in order to allow clean install/uninstall of testing versions.

Docker is not quite suitable, because it had problems running `snapd` inside it
(in order to install `core` snap), that's why Vagrant is used.

# Prerequisites

 - recent version of Vagrant
 - snapd installed on the system
 - Elixir snap expects latest version of Erlang to be installed on host system

# Builging snap

 To build or rebuild package simply run `vagrant up` in current directory.
 Output of the build will be in `snap/elixir-current_dev_amd64.snap` file.

# Installing snap

 To install snap package use following command:

 ```
 sudo snap install --dangerous --classic snap/elixir-current_dev_amd64.snap
 ```

 Please note that it uses classical confinement in ordet to give `mix` access to
 `git` and other locally installed tools. This means it is not isolated in snap
 directory, but can access all your system information.

 `--dangerous` necessary to allow installation of unsigned snaps.

# Running

 Use there commands (available under `/snap/bin/` path):

 * elixir-current.elixir
 * elixir-current.elixirc
 * elixir-current.iex
 * elixir-current.mix



