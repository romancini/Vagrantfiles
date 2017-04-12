# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "akost/linux-mint-17-kde"
  config.vm.box_check_update = false

  config.vm.box_download_insecure = true

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
  end
  
  # configuring hp proxy
  # if Vagrant.has_plugin?("vagrant-proxyconf")
  #    config.proxy.http     = "http://proxy.company.com:8080"
  #    config.proxy.https    = "http://proxy.company.com:8080"
  #    config.proxy.no_proxy = "localhost,127.0.0.1,.159,5."
  # end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    # git installation
    apt-get install -y git
    # docker installation based on https://docs.docker.com/engine/installation/linux/ubuntu/
    ## recommended extra packages for Trusty 14.04
    apt-get install -y linux-image-extra-$(uname -r)
    apt-get install -y linux-image-extra-virtual
    ## packages to allow apt to use a repository over HTTPS
    apt-get install -y apt-transport-https
    apt-get install -y ca-certificates
    apt-get install -y curl
    apt-get install -y software-properties-common
    ## Add Docker’s official GPG key
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    apt-key fingerprint 0EBFCD88
    ## To add the edge repository, add edge after stable on the last line of the command
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu trusty stable"
    ## Install the latest version of Docker
    apt-get update
    apt-get install -y docker-ce
  SHELL
end

