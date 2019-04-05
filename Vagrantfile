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
     "storage" => ["storage01", "storage02"],
     "clients" => ["client01", "client02"],
     "all_groups:children" => ["mgmt", "meta", "storage", "clients"]
    }
  end

  config.vm.provider "libvirt" do |lv|
    lv.memory = "4096"
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

  config.vm.define "storage02" do |config|
    config.vm.hostname = "storage02"
    config.vm.network "private_network", ip: "192.168.122.40"
  end

  config.vm.define "client01" do |config|
    config.vm.hostname = "client01"
    config.vm.network "private_network", ip: "192.168.122.50"
  end

  config.vm.define "client02" do |config|
    config.vm.hostname = "client02"
    config.vm.network "private_network", ip: "192.168.122.60"
  end
end
