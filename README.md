# Arch Linux Installation Guide

Using iwctl to connect to wifi:

Let's check Connection:
```ping www.google.com```

Let's use iwctl:
```iwctl```\
```device list```\
```adapter ADAPTER-NAME set-property Powered on```\
```station wlan0 scan```\
```station wlan0 get-networks```\
```station wlan0 connect WIFI-NAME```\
```station wlan0 show```

```ping www.google.com```

## Once you are connected we can begin with installation :)

-> Boot on a fresh Arch Linux ISO <-

If you're using a French Keyboard: ```loadkeys fr```

```cfdisk /dev/nvme0n1```

1. 1G (EFI System)
2. 70G+ (Linux File System)
3. 8G+ (Linux Swap)

Let's check the disks: ```lsblk```

## Let's format the disks

```mkfs.fat -F 32 /dev/nvme0n1p1```\
```mkfs.ext4 /dev/nvme0n1p2```\
```mkswap /dev/nvme0n1p3```\
```swapon /dev/nvme0n1p3```

## Let's mount the disks

```mount /dev/nvme0n1p2 /mnt```\
```mount --mkdir /dev/nvme0n1p1 /mnt/boot```

Let's check the disks once more: ```lsblk```

## Let's create a file system

```pacstrap /mnt base linux linux-headers linux-firmware base-devel nano```

## Let's make Fstab

```genfstab -U /mnt >> /mnt/etc/fstab```

## Let's Chroot

```arch-chroot /mnt```

## Let's Set Timezone

```ln -sf /usr/share/zoneinfo/Europe/Paris /etc/localtime```

View all timezone within this directory: /usr/share/zoneinfo/

## Let's sync the clock

```hwclock --systohc```

## Let's set locales

```nano /etc/locale.gen```

Then uncomment your locale (Example: fr_FR.UTF-8 UTF-8)

```locale-gen```

## Let's set a hostname

```nano /etc/hostname```

Write a hostname, example: archlinux

## Let's install network components

```pacman -S networkmanager wpa_supplicant wireless_tools```\
```systemctl enable NetworkManager```

## Let's install CPU ucode

```pacman -S amd-ucode``` (or pacman -S intel-ucode)

## Let's install a few tools

```pacman -S htop neofetch```

## Let's install bootloader

```pacman -S grub efibootmgr```\
```grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB```\
```grub-mkconfig -o /boot/grub/grub.cfg```

## Let's give root a password

```passwd```

## Let's add a new user

(Replace 'Blaka Div' with full username and Div with name)

```useradd -m -g wheel -c 'Blaka Div' -s /bin/bash Div```

## Let's change our new user password

```passwd Div```

## Let's add our user to sudoers

```export EDITOR=nano```\
```visudo```

Uncomment the line under: #Uncomment to allow members of group wheel to execute any command

## Let's install Gnome

```pacman -S gnome gnome-extra```

## Let's enable gdm

```sudo systemctl enable gdm```

## Let's leave the chroot

```exit```\
```umount -R /mnt```\
```reboot```

Once you reboot you can do theses optional steps:

## Let's fix French Keyboard

```localectl set-x11-keymap fr```

## Let's fix Your touchpad 
```gsettings set org.gnome.desktop.peripherals.touchpad click-method areas```

THE END. Now it is time to enjoy Arch Linux ;)







