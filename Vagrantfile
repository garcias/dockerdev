# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip: "10.0.1.222"
  config.ssh.forward_agent = true
  config.vm.provider :virtualbox do |v|
    v.name = "dockerdev"
    v.memory = 1024
  end
  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    sudo apt-get update -qq
    sudo apt-get install software-properties-common
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt-get update -qq
    sudo apt-get install -y docker-ce
    sudo usermod -aG docker ${USER}
  SHELL

end
