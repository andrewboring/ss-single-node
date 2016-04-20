# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.network "private_network", type: "dhcp"
  config.vm.hostname = "ssnode1"


  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = "1024"
    #unless File.exist?(disk1)
    #  vb.customize ['createmedium', '--filename', disk1, '--size', 1024]
    #end
    vb.customize ['storagectl', :id, '--name', 'SATA', '--add', 'sata', '--controller', 'IntelAHCI', '--portcount', 3]
    vb.customize ['createmedium', 'disk', '--filename', './disk1.vdi', '--size', 1024]
    vb.customize ['storageattach', :id, '--storagectl', 'SATA', '--port', 0, '--device', 0, '--type', 'hdd', '--medium', './disk1.vdi']
    vb.customize ['createmedium', 'disk', '--filename', './disk2.vdi', '--size', 1024]
    vb.customize ['storageattach', :id, '--storagectl', 'SATA', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', './disk2.vdi']
    vb.customize ['createmedium', 'disk', '--filename', './disk3.vdi', '--size', 1024]
    vb.customize ['storageattach', :id, '--storagectl', 'SATA', '--port', 2, '--device', 0, '--type', 'hdd', '--medium', './disk3.vdi']
  end

  config.vm.provision "shell", inline: <<-SHELL
      yum -y update 
      yum -y install net-tools
  SHELL


end
