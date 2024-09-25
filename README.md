# pf_ring

Installs the PF_RING Kernel module

Hint: for the sake of mistakes PF_RING is written as pfring (lower letter, no underline) where it is possible...


Example Playbook:
```
- hosts: all
  become: true
  vars: 
    pfring_install_mode: apt
  roles:
    - pfring
```


## pfring_install_mode
`pfring_install_mode: source|apt`

`source` fetches pf_ring from git and compiles the kernel (yes just the kernel module for this specific kernel)

`apt`use os package. be aware of the version

## pfring_version

`pfring_version: 8.2.0|latest`

e.g. GIT Tag. ignored when apt is used

## pfring_loader
only relevant with `pfring_install_mode: source`

`pfring_loader: classic`

`classic` is the slickest and easiest way via /etc/modules-load/

Use the shipped `systemd` start script. this is easy but might lead to errors. The fake systemctl scripts doesn't report the right status if the module crashes etc..
