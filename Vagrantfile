# -*- mode: ruby -*-

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provision "shell", path: "scripts/bootstrap.sh"
  config.vm.define "pihole" do |pihole|
    pihole.vm.hostname = "pihole"
    pihole.vm.network "private_network", ip: "192.168.100.50"
    pihole.vm.provider "virtualbox" do |vb|
      vb.name = "pihole"
      vb.cpus = "2"
      vb.memory = "4096"
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end
    pihole.vm.provision "shell", path: "scripts/pihole-provision.sh"
  end
end
