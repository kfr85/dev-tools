#!/usr/bin/ruby
#coding:utf-8

Vagrant.configure(2) do |config|
  config.vm.box = "bento/amazonlinux-2"
  
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/vagrant.yml"
    ansible.inventory_path = "ansible/hosts"
    ansible.limit = "all"
    ansible.install = true
  end
end

