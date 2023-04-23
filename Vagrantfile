# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.define "master" do |master|
    master.vm.network "public_network", ip: "192.168.0.70"
    master.vm.provider "virtualbox" do |vb|
      vb.memory = 4096
      vb.cpus = 4 
    end
  end

  config.vm.define "worker-1" do |worker01|
    worker01.vm.network "public_network", ip: "192.168.0.71"
    worker01.vm.provider "virtualbox" do |vb|
      vb.memory = 4096
      vb.cpus = 4 
    end
  end

  config.vm.define "worker-2" do |worker02|
    worker02.vm.network "public_network", ip: "192.168.0.72"
    worker02.vm.provider "virtualbox" do |vb|
      vb.memory = 4096
      vb.cpus = 4 
    end
end
end
