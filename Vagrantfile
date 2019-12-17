#!/usr/bin/ruby
#coding:utf-8

Vagrant.configure(2) do |config|
  config.vm.box = "bento/amazonlinux-2"
  config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.network "forwarded_port", guest: 22, host: 12222, id: "ssh"
  
  config.vm.provision "export env",
  type: "shell",
  run: "always",
  privileged: true,
  inline: <<-SHELL
      amazon-linux-extras install -y epel
      yum install -y ansible
  SHELL

  config.vm.provision "ansible_local" do |ansible|
    ansible.compatibility_mode = '2.0'
    ansible.become = true
    ansible.limit = "all"
    ansible.playbook = "ansible/vagrant.yml"
    ansible.inventory_path = "ansible/hosts"
    ansible.install = true
  end
end

