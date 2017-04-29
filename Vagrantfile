# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "bento/centos-7.3"
  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
  end

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"
  config.vm.network "public_network"

  # this works!
  config.vm.provision "shell", inline: "yum -y update"
  # http://docs.ansible.com/ansible/intro_installation.html#latest-release-via-yum
  config.vm.provision "shell", inline: "yum -y install epel-release" # is this the line causing the 404?
  config.vm.provision "shell", inline: "yum -y install ansible"

  # TODO: test this
  # config.vm.provision "shell" inline: <<-SHELL
  #   yum -y update
  #   # http://docs.ansible.com/ansible/intro_installation.html#latest-release-via-yum
  #   yum -y install epel-release
  #   yum -y install ansible
  # SHELL

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # This requires the VirtualBox Guest Additions and the kernal module
  # To make this work, Use VirtualBox 5.1.18 (NOT 5.1.20) and vagrant-vbguest
  config.vm.synced_folder "../ansible_playbooks", "/home/vagrant/ansible_playbooks"
end