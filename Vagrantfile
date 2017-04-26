# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "bento/centos-7.3"
  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
  end

  # this works!
  config.vm.provision "shell", inline: "yum -y update"
  # http://docs.ansible.com/ansible/intro_installation.html#latest-release-via-yum
  config.vm.provision "shell", inline: "yum -y install epel-release"
  config.vm.provision "shell", inline: "yum -y install ansible"
end
