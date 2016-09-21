# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provider :virtualbox do |v|
    v.customize ["modifyvm", :id, "--memory", 2048]
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
  SHELL

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "setup.yml"
  end
end
