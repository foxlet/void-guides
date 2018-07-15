Setting Up QEMU Tun/Tap using NetworkManager
============================================

# Make the Bridge
```
nmcli connection add type bridge \
    ifname br1 con-name furbridge
```

# Attach Bridge to Ethernet
```
nmcli connection add type bridge-slave \
    ifname enp37s0 con-name furinternal master br1
```

# Make the Tun/Tap
```
nmcli connection add type tun \
    ifname tap0 con-name foxtap0 \
    mode tap owner `id -u`
```

# Attach Tun/Tap to Bridge
```
nmcli connection mod foxtap0 connection.slave-type bridge \
    connection.master br1
```
