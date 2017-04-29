This is a Vagrant Ansible control box because it's not supported on Windows

## Install

- Install prereqs (Windows links):
  - [http://download.virtualbox.org/virtualbox/5.1.20/VirtualBox-5.1.20-114628-Win.exe](VirtualBox)
  - Virtualbox Extensions? Not sure this is needed. Trying without it.
  - [https://releases.hashicorp.com/vagrant/1.9.4/vagrant_1.9.4.msi](Vagrant)
    - This release has problems (https://github.com/mitchellh/vagrant/issues/8520) , but 1.9.3 doesn't seem to so I"m using that

## TODO
- Set up synced folder for ansible projects

- Update docs with the shared stuff (vagrant 1.9.3 and vbox 5.1.18)
- Work on ansible projects
- Merge the two Vagrantfiles