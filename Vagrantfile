# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.become = true
    ansible.groups = {
     "mgmt" => ["mgmt01"],
     "meta" => ["meta01"],
     "storage" => ["storage01"],
     "clients" => ["client01"],
     "all_groups:children" => ["mgmt", "meta", "storage", "clients"]
    }
  end

  config.vm.provider "libvirt" do |lv|
    vb.memory = "1024"
  end

  config.vm.define "mgmt01" do |config|
    config.vm.hostname = "mgmt01"
    config.vm.network "private_network", ip: "192.168.122.10"
  end

  config.vm.define "meta01" do |config|
    config.vm.hostname = "meta01"
    config.vm.network "private_network", ip: "192.168.122.20"
  end

  config.vm.define "storage01" do |config|
    config.vm.hostname = "storage01"
    config.vm.network "private_network", ip: "192.168.122.30"
  end

  config.vm.define "client01" do |config|
    config.vm.hostname = "client01"
    config.vm.network "private_network", ip: "192.168.122.40"
  end

end
