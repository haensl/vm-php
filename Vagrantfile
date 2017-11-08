# -*- mode: ruby -*-
# vi: set ft=ruby :

vmname = "vm-php"

Vagrant.configure("2") do |config|
  config.vm.define vmname
  config.vm.box = "speedlight/jessie-vbguest"
  config.vm.provider "virtualbox" do |virtualbox|
    virtualbox.name = vmname
  end

  # DEV
  config.vm.network "forwarded_port", guest: 80, host: 8080
  # QA
  config.vm.network "forwarded_port", guest: 8081, host: 8081
  # MAILHOG
  config.vm.network "forwarded_port", guest: 8025, host: 8025

  config.vm.post_up_message = "dev:\thttp://localhost:8080\nqa:\t\thttp://localhost:8081\nmailhog:\thttp://localhost:8025"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "VM/site.yml"
    ansible.ask_sudo_pass = "true"
  end
end
