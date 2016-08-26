# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # box setting
  config.vm.hostname = "vagrant-dev-host"
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "private_network", ip: "192.168.10.10"
  config.vm.network "forwarded_port", guest: 5000, host: 5000, auto_correct: true
  config.vm.synced_folder "./src", "/home/vagrant/src", create: true

  # virtualbox provider
  config.vm.provider "virtualbox" do |vb|
    vb.name = "Vagrant Development Box"
    vb.memory = "1024"
  end

  # install docker on vm
  # config.vm.provision "docker"

  # install required software, dependencies and configurations
  # on the virtual machine using a provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision/playbook.yml"
  end
end
