# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

#VM settings
MYSQL_IP = "172.28.128.10"
MYSQL_MEMORY_MB  = "6144" #6g

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/focal64"  # https://app.vagrantup.com/ubuntu/
  config.vm.define "mysql" do |mysql|
    mysql.vm.provider "virtualbox" do |vb|
      vb.memory = MYSQL_MEMORY_MB
    end
    mysql.vm.network :forwarded_port, guest: 3306, host: 3306
    mysql.vm.provision :shell, :path => "install.sh"
    mysql.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777", "fmode=666"]
    mysql.vm.network "private_network", ip: MYSQL_IP
  end
end
