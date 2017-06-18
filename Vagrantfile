# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "bento/centos-7.3"
  # Disable the default synced folder because it's too much trouble to set up
  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
  end

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  config.vm.define :ansible_control, primary: true do |ansible_control|
    ansible_control.vm.network :private_network, ip: "10.0.0.10"
    ansible_control.vm.hostname = "ansible-control"
    ansible_control.vm.provision "shell", inline: <<-SHELL
      yum -y update
      # http://docs.ansible.com/ansible/intro_installation.html#latest-release-via-yum
      yum -y install epel-release
      yum -y install ansible
    SHELL
    ansible_control.vm.provision "file", source: "./ansible_control.yaml", destination: "/tmp/ansible_control.yaml"
    ansible_control.vm.provision "shell", privileged: false, inline: "sudo mkdir -p /vagrant"
    ansible_control.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "/tmp/ansible_control.yaml"
    end
  end

  config.vm.define :target1 do |target1|
    target1.vm.network :private_network, ip: "10.0.0.11"
    target1.vm.hostname = "target1"
  end

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # This requires the VirtualBox Guest Additions and the kernal module
  # To make this work, Use VirtualBox 5.1.18 (NOT 5.1.20) and vagrant-vbguest
  # config.vm.synced_folder "../ansible_playbooks", "/home/vagrant/ansible_playbooks"

  # config.vbguest.auto_update = false
end
