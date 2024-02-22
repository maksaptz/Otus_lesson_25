# -*- mode: ruby -*-
# vim: set ft=ruby :
#Path to HDD on host

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.box_version = "2004.01"
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024 
    v.cpus = 1
  end
  
  config.vm.define "ipa" do |host|
    host.vm.provider "virtualbox" do |v|
      v.memory = 6054
      v.cpus = 1
    end
    host.vm.hostname = "ipa.otus.lan"
    host.vm.network "private_network",
                     ip: "192.168.50.10",
                     adapter: 2
  end

  config.vm.define "client1" do |host|
    host.vm.hostname = "client1.otus.lan"
    host.vm.network "private_network",
                     ip: "192.168.50.11",
                     adapter: 2
  end

  config.vm.define "client2" do |host|
    host.vm.hostname = "client2.otus.lan"
    host.vm.network "private_network",
                     ip: "192.168.50.12",
                     adapter: 2
    host.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/play.yml"
      ansible.inventory_path = "ansible/hosts"
      ansible.host_key_checking = "false"
      ansible.limit = "all"
    end

  end

end
