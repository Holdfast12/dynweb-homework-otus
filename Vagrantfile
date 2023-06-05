# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|

    config.vm.box_check_update = false
    config.vm.synced_folder "/home/michael/dnf_cache", "/var/cache/dnf/"
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  
    config.vm.define "DynamicWeb" do |vmconfig| 
      vmconfig.vm.box = 'almalinux/9'
      vmconfig.vm.hostname = 'DynamicWeb'

      vmconfig.vm.network "forwarded_port", guest: 8083, host: 8083
      vmconfig.vm.network "forwarded_port", guest: 8081, host: 8081
      vmconfig.vm.network "forwarded_port", guest: 8082, host: 8082
      vmconfig.vm.provider "virtualbox" do |vbx|
        vbx.memory = "2048"
        vbx.cpus = "2"
        vbx.customize ["modifyvm", :id, '--audio', 'none']
      end
    end
  
  end
