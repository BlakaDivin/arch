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

Once you are connected we can begin with installation :)

-> Boot on any Arch Linux ISO <-

If you're using a French Keyboard: ```loadkeys fr```

```cfdisk /dev/nvme0n1```

1. 1G (EFI System)
2. 70G+ (Linux File System)
3. 8G+ (Linux Swap)

Let's check the disks: ```lsblk```


