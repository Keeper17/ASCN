# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

#Notes
#user name for VMs is created as vagrant

#<vagrant box add bento/ubuntu-20.04> to add OS image to internal repository
#<vagrant up> to start VMs (run at the same folder where this file is, or pass file as argument)
#<vagrant halt> to stop VMs
#<vagrant destroy> to remove VMs

#You should only need change the first two/three variables in this file

#Variables
Number_VMs = 1 #number VMs to launch
IP_RANGE= "192.168.56" #Change me if needed!
PUBLIC_KEY_PATH = "~/.ssh/id_rsa.pub" #Change me if needed!
READ_PUBLIC_KEY = File.read(File.expand_path(PUBLIC_KEY_PATH)).strip

#Provisioning VM - New!
PROVISION_VM = false                 #Change me if needed!
PROVISION_VM_IP = "192.168.56.10"   #Change me if needed!
PRIVATE_KEY_PATH = "~/.ssh/id_rsa"  #Change me if needed!

Vagrant.configure("2") do |config|

 config.vm.box = "bento/ubuntu-20.04"

 config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.cpus = 1
  end

  #(1..Number_VMs).each do |i|
  #  config.vm.define "server#{i}" do |node|
  #    node.vm.hostname = "VM#{i}"
  #    node.vm.network :private_network, ip: "#{IP_RANGE}.#{100+i}"
  #  end
  #end

    config.vm.define "server2" do |node|
      node.vm.hostname = "VM2"
      node.vm.network :private_network, ip: "#{IP_RANGE}.#{102}"
    end

 config.vm.provision "shell", inline: <<-SHELL
        echo "#{READ_PUBLIC_KEY}" >> /home/vagrant/.ssh/authorized_keys
        sed -i 's/#PubkeyAuthentication yes/PubkeyAuthentication yes/g' /etc/ssh/sshd_config
        sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/g' /etc/ssh/sshd_config
        systemctl restart sshd
        #apt update
        #apt-get install -y vim
        #apt-get upgrade -y
        #apt-get update -y
        #apt install python pip -y
        #curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-411.0.0-linux-x86.tar.gz
        #tar -xf google-cloud-cli-411.0.0-linux-x86.tar.gz
        #./google-cloud-sdk/install.sh -q
        #apt-get install ansible


      SHELL


end
