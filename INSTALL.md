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
sudo zypper in btop git systemd-zram-service hyprland hyprland-qtutils hyprcursor ghostty thunar nushell fzf chromium hyprpaper hypridle hyprlock ca-certificates-cacert greetd regreet gtk3-metatheme-adwaita  adwaita-qt6 adwaita-qt5 gtk2-metatheme-adwaita sensors pipewire playerctl brightnessctl bluez upower fastfetch ImageMagick snapper-backup hyprshot rclone gvfs gvfs-backend-samba fprintd fprintd-pam cage

sudo zypper addrepo https://download.opensuse.org/repositories/home:team-vrock:releases/openSUSE_Tumbleweed/home:team-vrock:releases.repo
sudo zypper ref
sudo zypper install eww-bridge

```

# Install Optional Packages
```
sudo zypper in wallpaper-branding-openSUSE
```


# Install Brave Browser
```
sudo zypper addrepo https://brave-browser-rpm-release.s3.brave.com/brave-browser.repo
sudo zypper install brave-browser
```

# Install Visual Studio Code
```
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc &&
echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\nautorefresh=1\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/zypp/repos.d/vscode.repo > /dev/null

sudo zypper install code
```

# Install SoftMaker Office NX
```
sudo zypper install -y curl
curl -fsSL https://softmaker.net/down/install-softmaker-office-nx.sh | sudo bash
```

# Install AI Tools
```
sudo zypper in npm24

# install Codex
sudo npm install -g @openai/codex

# intall github copilot
sudo npm install -g @github/copilot

# install google gemini
sudo npm install  -g @google/gemini-cli

```

# Install Oh-My-Posh
```
curl -s https://ohmyposh.dev/install.sh | bash -s
```

# Install Warp Client (not an openSUSE package)
```
# Add cloudflare-warp.repo
sudo zypper addrepo https://pkg.cloudflareclient.com/cloudflare-warp-ascii.repo

# Update repo
sudo zypper ref

# Install
sudo zypper in cloudflare-warp
```

# Set default graphical target

```
sudo systemctl set-default graphical.target
```


# Install KVM
```
sudo zypper install -t pattern kvm_server kvm_tools
```

# Install docker
```
sudo zypper in docker docker-buildx
```
# Theme
```
gsettings set org.gnome.desktop.interface gtk-theme Adwaita-dark
gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'
```
