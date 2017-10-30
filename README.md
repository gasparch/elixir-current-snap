
# Purpose 

This repository contains scripts to automate task of building -current version of Elixir and trying it out along with regular Elixir installation.

All build process is done in VM in order not to contaminate host system with development packages.

Elixir build into snap in order to allow clean install/uninstall of testing versions.

# Prerequisites

 - recent version of Vagrant
 - snapd installed on the system

# Builging snap

 To build or rebuild package simply run `vagrant up` in current directory.
 Output of the build will be in `snap/elixir-current_1.6_amd64.snap` file.

# Installing snap

 To install snap package use following command: 

 ```
 sudo snap install --dangerous --classic snap/elixir-current_1.6_amd64.snap
 ```

 Please note that it uses classical confinement in ordet to give mix access to
 git and other locally installed tools. This means it is not isolated in snap
 directory, but can access all your system information.

 `--dangerous` allows installation of unsigned snaps.
