# GilmanLab Development

This repository contains various configuration files and scripts which are used for developing against GilmanLab.

## Usage

Currently this repository is primarily used to configure macOS with the necessary configurations and programs for
working on glab. It leverages Ansible to make the configuration process repeatable. This is ideal as running the
included playbook will automatically upgrade software on the machine. To run the configuration requires macOS to have
some software already installed. This installation can be automated by running the included bash script:

```bash
$> ./env/mac.sh
```

To begin configuration run the playbook:

```bash
./env/mac.yml
```

Support for additional operating systems will be added in the future.

## Playbook

At a high level, the playbook does the following:

* Copies over the dotfiles to the running users $HOME folder
  * Most of these dotfiles are self-explanatory and are loaded via .bashrc
  * The `.devenv` file is the only one not loaded automatically as it requires a valid Vault token to pull down secrets
* Installs required packages via `brew`
* Installs required packages via `pip`
* Configures SSH
* Installs custom `cluster` script
  * This is an AIO script for bringing up a multi-node k3s cluster via multipass for local development
* Pulls down glab repositories into the default `~/code` directory.