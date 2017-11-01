# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
	# The most common configuration options are documented and commented below.
	# For a complete reference, please see the online documentation at
	# https://docs.vagrantup.com.

	# Every Vagrant development environment requires a box. You can search for
	# boxes at https://vagrantcloud.com/search.
	config.vm.box = "ubuntu/xenial64"

	# Share an additional folder to the guest VM. The first argument is
	# the path on the host to the actual folder. The second argument is
	# the path on the guest to mount the folder. And the optional third
	# argument is a set of non-required options.
	config.vm.synced_folder "snap", "/data/snap"

	# Provider-specific configuration so you can fine-tune various
	# backing providers for Vagrant. These expose provider-specific options.
	# Example for VirtualBox:
	#
	config.vm.provider "virtualbox" do |vb|
		# Display the VirtualBox GUI when booting the machine
		vb.gui = false

		# Customize the amount of memory on the VM:
		vb.memory = "2048"
	end
	#
	# View the documentation for the provider you are using for more
	# information on available options.

	# Enable provisioning with a shell script. Additional provisioners such as
	# Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
	# documentation for more information about their specific syntax and use.
	config.vm.provision "shell", inline: <<-SHELL
		apt-get update
		apt-get install -y snapcraft snapd git wget patch rsync make
		apt-get install -y mc
		snap install core
	SHELL

	config.vm.provision "shell", run: 'always', inline: <<-SHELL
		rm -rf /root/snap
		cp -R /data/snap /root/snap
		rm -f /root/snap/elixir*.snap
		cd /root/snap
		snapcraft
		cp /root/snap/elixir-current_dev_amd64.snap /data/snap/elixir-current_dev_amd64.snap
	SHELL
end
