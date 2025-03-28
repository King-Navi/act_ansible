#-*- mode: ruby -*-
#vi: set ft=ruby

Vagrant.configure("2") do |config|
    config.vm.box= "generic/ubuntu2004"
    config.vm.network "forwarded_port", guest: 3031, host: 9091 
    config.vm.synced_folder ".", "/vagrant"

    # Configuración del proveedor (VirtualBox)
    config.vm.provider "virtualbox" do |vb| 
        vb.memory = "4096" 
        vb.name = "Ubuntu2004" 
    end 
    config.vm.provision "ansible_local" do |a|
        a.verbose = "v"
        a.playbook = "playbook.yaml"
    end
end