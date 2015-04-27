# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "phusion/ubuntu-14.04-amd64"

  config.vm.provision :ansible do |ansible|
    ansible.groups = {
      "docker" => ["docker"]
    }
    ansible.playbook = "main.yml"
  end

  config.vm.provider "virtualbox" do |v|
    v.name = "docker"
  end
end
