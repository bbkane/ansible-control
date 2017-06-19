# Ansible Control

This is a Vagrant/Virtualbox set of scripts for experimenting with Ansible in a disposable/recreatable environment.

## Install

Vagrant is very finicky software, but these versions seem to work for this
setup, while newer versions don't. When the newer versions have the bugs ironed
out, I hope to upgrade these links.

- Install prereqs (Windows 7):
  - [Virtualbox 5.0.40](https://www.virtualbox.org/wiki/Download_Old_Builds_5_0)
  - [Vagrant 1.8.7](https://releases.hashicorp.com/vagrant/1.8.7/)

- Download (or clone this repo).

- `cd <directory of this repo>`

- `vagrant up`

That will build two boxes- `ansible-control` and `target`. `ansible-control`
has Ansible installed, this repo on it, and some other light provisioning (see
[./ansible_control.yaml](ansible_control.yaml) ). `target1` is a blank slate.

- From Windows, SSH  to `127.0.0.1` port `2222` with username `vagrant` and password `vagrant`
- From `ansible-control`, ssh to `target1` with username `vagrant` and password
  `vagrant` to add the key to the `known_hosts` list.

## Test

`ansible -i hosts -k -m ping all`

## Use

Now you should be able to start writing playbooks and testing them against `target1`.

## TODO
- Set up synced folder for ansible projects (probably won't fix)
- Use SSH keys instead of passwords so I don't have to use `-k`
