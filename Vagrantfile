#!/usr/bin/ruby
#coding:utf-8

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  
  config.vm.network :private_network, ip: "192.168.33.100"

  config.vm.network "forwarded_port", guest: 8080, host: 8080
    
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/vagrant.yml"
    ansible.inventory_path = "ansible/hosts"
    ansible.limit = "all"
    ansible.install = true
  end
end

