# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "phusion/ubuntu-14.04-amd64"
  config.vm.network :private_network, ip: '10.0.0.10'

  MY_TCP_PORTS = {
    "4000" => 4000, # Jekyll
    "8080" => 8080, # Web dev
  }
  
  MY_TCP_PORTS.each do |guest, host|
    config.vm.network "forwarded_port", guest: "#{guest}", host:"#{host}", protocol: "tcp", auto_correct: true
  end
  
  config.nfs.map_uid = Process.uid
  config.nfs.map_gid = Process.gid
  config.vm.synced_folder "/Users/carlos/Code", "/home/vagrant/Code", nfs: true
  
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