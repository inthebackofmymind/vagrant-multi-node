# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.define "app1" do |app|
    app.vm.hostname = "orc-app1.dev"
    app.vm.box = "geerlingguy/centos7"
    app.vm.network :private_network, ip: "192.168.60.4"
    app.vm.network "forwarded_port", guest: 443, host: 4341 
  end

  config.vm.define "app2" do |app|
    app.vm.hostname = "orc-app2.dev"
    app.vm.box = "geerlingguy/centos7"
    app.vm.network :private_network, ip: "192.168.60.5"
    app.vm.network "forwarded_port", guest: 443, host: 4342 
  end

  config.vm.define "db" do |db|
    db.vm.hostname = "orc-db.dev"
    db.vm.box = "geerlingguy/centos7"
    db.vm.network :private_network, ip: "192.168.60.6"
    db.vm.network "forwarded_port", guest: 80, host: 8080
    db.vm.network "forwarded_port", guest: 443, host: 4343 
  end
end    
