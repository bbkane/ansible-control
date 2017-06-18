This is a Vagrant Ansible control box because it's not supported on Windows

## Install

- Install prereqs (Windows 7):
  - Virtualbox 5.0.40
  - Vagrant 1.8.7

- `vagrant up`

## Current TODO
- Make a playbook for the host so I can bootstrap
  - I need:
    - Git
    - Vim
    - My Vim config
- Then I need to push the file with Vagrant and run the playbook

## TODO

- Set up synced folder for ansible projects (probably won't fix)
- Update docs with the shared stuff (vagrant 1.9.3 and vbox 5.1.18)
- Merge the two Vagrantfiles
