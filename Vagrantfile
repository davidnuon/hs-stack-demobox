# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  config.vm.network "forwarded_port", guest: 3030, host: 3030
  config.vm.network "forwarded_port", guest: 1337, host: 1337

  config.vm.synced_folder "src/", "/home/vagrant/src"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-key adv  --keyserver keyserver.ubuntu.com --recv-keys 575159689BEFB442 --force-yes
    echo 'deb http://download.fpcomplete.com/ubuntu trusty main'|sudo tee /etc/apt/sources.list.d/fpco.list

    sudo apt-get update
    sudo apt-get install -y haskell-platform
    sudo apt-get install -y stack
    sudo apt-get install -y git

  SHELL
end
