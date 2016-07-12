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
    sudo apt-get install -y ranger zsh
    sudo git clone git://github.com/robbyrussell/oh-my-zsh.git /home/vagrant/.oh-my-zsh
    sudo chsh -s /bin/zsh
    echo 'Writing in .zshrc file'
    echo "export ZSH=/home/vagrant/.oh-my-zsh" > .zshrc
    echo "ZSH_THEME="bira"" >> .zshrc
    echo "plugins=(git)" >> .zshrc
    echo 'source $ZSH/oh-my-zsh.sh' >> .zshrc
    echo 'Install dockercompose'
    sudo curl -L https://github.com/docker/compose/releases/download/1.8.0-rc2/docker-compose-`uname -s`-`uname -m` | sudo tee /usr/local/bin/docker-compose
    sudo chmod +x /usr/local/bin/docker-compose
    echo 'END SCRIPT'
SCRIPT
#chsh -s /bin/zsh

Vagrant.configure(2) do |config|

  config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", "1024", "--cpus", "1"]
  end

  config.vm.box = "ubuntu/trusty64"
  config.vm.network "private_network", ip: "192.168.50.11"
  config.vm.hostname = "vbuntu"
  config.vm.provision "shell", inline: $script
end
