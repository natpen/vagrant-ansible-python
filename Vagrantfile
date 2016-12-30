# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

NAME = "project-name"

Vagrant.require_version ">= 1.7.0"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.ssh.insert_key = false
  config.vm.hostname = NAME

  config.vm.provider :virtualbox do |v|
    # v.name = "project-name"
    v.memory = 256
    v.cpus = 1
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.network :private_network, ip: "192.168.33.55"
  # Set the name of the VM. See: http://stackoverflow.com/a/17864388/100134
  config.vm.define NAME do |t|
  end

  # config.vm.network :forwarded_port, guest: 5000, host: 5001

  config.vm.synced_folder "../project-name", "/project-name"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/site.yml"
  end
end
