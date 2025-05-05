# arch
Arch Linux Installation Guide

Using iwctl to connect to wifi:

Let's check Connection:
```ping www.google.com```

Let's use iwctl:
```iwctl```
```device list```
```adapter ADAPTERNAME set-property Powered on```
```station wlan0 scan```
```station wlan0 get-networks```
```station wlan0 connect wifi-name```
```station wlan0 show```

```ping www.google.com```
