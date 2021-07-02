# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure(2) do |config|

	# Uncomment to provision all machines
	# config.vm.provision "shell", path: "bootstrap.sh"

	config.vm.box = "generic/ubuntu1804"

	# Master VM
	config.vm.define "hashistack" do |hashistack|
		hashistack.vm.hostname = "hashistack"
		hashistack.vm.network "private_network", ip: "10.20.30.100"
		hashistack.vm.provider "virtualbox" do |v|
			v.name = "hashistack"
			v.memory = 2048
			v.cpus = 2
		end

		# Uncomment to provision master machine only
		# hashistack.vm.provision "shell", path: "bootstrap_master.sh"
	end

	# Support VMs
	SupportNodeCount = 1

	(1..SupportNodeCount).each do |i|

		config.vm.define "hashistack#{i}" do |hashistack|

			hashistack.vm.hostname = "hashistack#{i}"
			hashistack.vm.network "private_network", ip: "10.20.30.10#{i}"
			hashistack.vm.provider "virtualbox" do |v|
				v.name = "hashistack#{i}"
				v.memory = 1024
				v.cpus = 1
			end

			# Uncomment to provision support machines only
			# hashistack.vm.provision "shell", path: "bootstrap_support.sh"

		end

	end

end