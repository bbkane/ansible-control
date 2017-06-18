# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "bento/centos-7.3"
  # Disable the default synced folder because it's too much trouble to set up
  config.vm.synced_folder '.', '/vagrant', disabled: true

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
  end

  config.vm.define :ansible_control, primary: true do |ansible_control|
    ansible_control.vm.network :private_network, ip: "10.0.0.10"
    ansible_control.vm.hostname = "ansible-control"
    ansible_control.vm.provision "shell", inline: <<-SHELL
      yum -y update
      # http://docs.ansible.com/ansible/intro_installation.html#latest-release-via-yum
      yum -y install epel-release
      yum -y install ansible
    SHELL

    ansible_control.vm.provision "file", source: ".", destination: "/home/vagrant/ansible_control"
    ansible_control.vm.provision "shell", privileged: false, inline: "sudo mkdir -p /vagrant"

    ansible_control.vm.provision "ansible_local" do |ansible|
      # ansible-playbook run from here
      ansible.provisioning_path = "/home/vagrant/ansible_control"
      ansible.playbook = "ansible_control.yaml"
      ansible.verbose = true
      ansible.inventory_path = "hosts"
      ansible.limit = "ansible-control"
    end
  end

  config.vm.define :target1 do |target1|
    target1.vm.network :private_network, ip: "10.0.0.11"
    target1.vm.hostname = "target1"
  end
end
