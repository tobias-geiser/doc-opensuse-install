# Partitions

4GB EFI
~GB OS

# Full Disk Encryption

# Install Rescue System
To install a rescue system on the disk we will copy the initrd and linux kernel from the installation media.

```
sudo mount /dev/vda1 /boot/efi/
sudo mkdir /boot/efi/opensuse-rescue

sudo mount -o loop /path/to/your-file.iso /mnt

sudo cp /mnt/boot/x86_64/loader/initrd /boot/efi/opensuse-rescue
sudo cp /mnt/boot/x86_64/loader/linux /boot/efi/opensuse-rescue

sudo umount /mnt
```

create a new loader entry in /boot/efi/loader/entries/
e.g opensuse-rescue.conf
```
# Boot Loader Specification type#1 entry
title      openSUSE Tumbleweed Rescue
sort-key   rescue
options    splash=silent quiet rescue=1 showopts
linux      /opensuse-rescue/linux
initrd     /opensuse-rescue/initrd
```


# Configure Zypper

Change installRecommens to "no"

```
[solver]

## Install soft dependencies (recommended packages)
##
## CAUTION: The system wide default for all libzypp based applications (zypper,
## yast, pk,..) is defined in  /etc/zypp/zypp.conf(solver.onlyRequires)  and it
## will per default install recommended packages. It is NOT RECOMMENDED to define
## this value here for zypper exclusively, unless you are very certain that you
## want zypper to behave different than other libzypp based packagemanagement software
## on your system.
##
## Valid values: boolean
## Default value: follow zypp.conf(solver.onlyRequires)
##
installRecommends = no
```


# Install Packages

```
sudo zypper in git systemd-zram-service hyprland ghostty thunar nushell fzf chromium hyprpaper hypridle hyprlock
```
