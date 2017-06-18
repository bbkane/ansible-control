This is a Vagrant Ansible control box because it's not supported on Windows

## Install

- Install prereqs (Windows 7):
  - Virtualbox 5.0.40
  - Vagrant 1.8.7

- `vagrant up`

## Test

`ansible -i hosts -k -m ping all`

## TODO
- Set up synced folder for ansible projects (probably won't fix)
- Use SSH keys instead of passwords so I don't have to use `-k`
