# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.define "app1" do |app|
    app.vm.hostname = "node1"
    app.vm.box = "bento/ubuntu-16.04"
    app.vm.network :public_network, ip: "192.168.0.114"
  end

  config.vm.define "app2" do |app|
    app.vm.hostname = "node2"
    app.vm.box = "bento/ubuntu-16.04"
    app.vm.network :public_network, ip: "192.168.0.115"
  end

  config.vm.define "app3" do |app|
    app.vm.hostname = "node3"
    app.vm.box = "bento/ubuntu-16.04"
    app.vm.network :public_network, ip: "192.168.0.116"
  end

  config.vm.provision "shell", inline: <<-SHELL
     cd /opt
     curl -sSL https://get.docker.com | sh
     apt-get -y install openssh-server
  SHELL

end    
