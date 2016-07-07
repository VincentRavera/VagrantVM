# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

$script = <<SCRIPT
    echo 'Init - install docker'
    sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
    echo 'deb https://apt.dockerproject.org/repo ubuntu-trusty main' | sudo tee /etc/apt/sources.list.d/docker.list
    sudo apt-get update
    sudo apt-get install -y docker-engine
    sudo usermod -aG docker vagrant
    sudo apt-get install -y ranger
    echo 'END SCRIPT'
SCRIPT


Vagrant.configure(2) do |config|

  config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "1"]
  end

  config.vm.box = "ubuntu/trusty64"
  config.vm.network "private_network", ip: "192.168.50.10"
  config.vm.hostname = "test"
  config.vm.provision "shell", inline: $script
end
