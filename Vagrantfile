# -*- mode: ruby -*-
# vi: set ft=ruby :
require 'berkshelf/vagrant'
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "logstash"
  config.berkshelf.enabled = true

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  # Example for VirtualBox:
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
   config.vm.provision "chef_solo" do |chef|
     chef.add_recipe "redisio::install"
     chef.add_recipe "redisio::enable"
     chef.add_recipe "nginx::default"
     chef.add_recipe "elasticsearch::default"
     chef.add_recipe "elasticsearch::nginx"
     chef.add_recipe "logstash::default"
     #chef.add_recipe "logstash::agent"
     #chef.add_recipe "logstash::server"
     #chef.add_recipe "logstash::index_cleaner"
     chef.add_recipe "kibana::nginx"
     chef.add_recipe "riemann::default"
   end
end
