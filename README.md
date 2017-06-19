# Ansible Control

This is a Vagrant/Virtualbox set of scripts for experimenting with Ansible in a disposable/recreatable environment.

## Install

Vagrant is very finicky software, but these versions seem to work for this
setup, while newer versions don't. When the newer versions have the bugs ironed
out, I hope to upgrade these links.

- Install prereqs (Windows 7):
  - [Virtualbox 5.0.40](https://www.virtualbox.org/wiki/Download_Old_Builds_5_0).
    It looks like the latest version of Virtualbox is also work (5.1.22)
  - [Vagrant 1.8.7](https://releases.hashicorp.com/vagrant/1.8.7/)

- Download (or clone this repo).

- `cd <directory of this repo>`

- `vagrant up`

That will build two boxes- `ansible-control` and `target`. `ansible-control`
has Ansible installed, this repo on it, and some other light provisioning (see
[./ansible_control.yaml](ansible_control.yaml) ). `target1` is a blank slate.
It will take quite a while to download, import, and provision the boxes, so get
a coffee.

If you get a VirtualBox error, try it again and then try uninstalling your
Virtualbox and updating to a newer version. Maybe that will help.

- From Windows, SSH  to `127.0.0.1` port `2222` with username `vagrant` and password `vagrant`
- From `ansible-control`, ssh to `target1` with username `vagrant` and password
  `vagrant` to add the key to the `known_hosts` list.
- type `exit` to exit `target1`
- type `cd ~/ansible_control` to change directories to where your ansible files are.

## Test

`ansible -i hosts -k -m ping all`

## Use

Now you should be able to start writing playbooks and testing them against `target1` (and `ansible-control` if you want)

## Learn

- [Ansible](http://docs.ansible.com/ansible/index.html)
- Vim
  - Vim is a text editor that I use to write playbooks. To go through the
    tutorial, type `vimtutor` in the console.
- [Linux](http://linuxcommand.org/learning_the_shell.php) - this is just a link
  to a tutorial I found online. There are others, and randomly googling is
  helpful here too. If you need help for a specific command, type `man
  <command>` to pull up the manual. If you don't know the command, type `man -k
  <keyword>` to search the man pages. Googling is generally faster though.

## Saving your work outside the VM

Virtualbox and Vagrant offer ways to sync folders, but I haven't been able to
get any of them to work reliably on Windows. Instead I use a git repo to save my
work.

## Shut down

When you're done for the day, type `vagrant halt` from Windows to kill the
VM. Type `vagrant up` to restart it.

## Destroy

If you screw something up or you want to start over, make sure your work is
saved and type `vagrant destroy` to destroy the VM. To create a new one, type
`vagrant up` again.

## TODO
- Set up synced folder for ansible projects (probably won't fix)
- Use SSH keys instead of passwords so I don't have to use `-k`
