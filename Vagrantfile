#-*- mode: ruby -*-
#vi: set ft=ruby

Vagrant.configure("2") do |config|
    # Primera máquina: Docker
    config.vm.define "docker_vm" do |docker_vm|
        docker_vm.vm.box = "generic/ubuntu2004"
        docker_vm.vm.hostname = "docker-vm"
        docker_vm.vm.network "forwarded_port", guest: 3031, host: 9091
        docker_vm.vm.synced_folder ".", "/vagrant"
    
        docker_vm.vm.provider "virtualbox" do |vb|
          vb.name = "UbuntuDocker"
          vb.memory = 2048
        end
    
        docker_vm.vm.provision "ansible_local" do |a|
          a.verbose = "v"
          a.playbook = "playbook.yaml"
        end
    end

    # Segunda VM - Servidor web con nginx
    config.vm.define "web_vm" do |web_vm|
        web_vm.vm.box = "generic/ubuntu2004"
        web_vm.vm.hostname = "web-vm"
        web_vm.vm.network "forwarded_port", guest: 80, host: 8080
        web_vm.vm.synced_folder ".", "/vagrant"

        web_vm.vm.provider "virtualbox" do |vb|
            vb.name = "UbuntuWeb"
            vb.memory = 1024
        end

        web_vm.vm.provision "ansible_local" do |a|
            a.playbook = "playbook_web.yaml"
        end
    end
end