
## CAN (socketCAN)

`sudo apt-get install can-utils`

`ip link show`

```
can0: <NOARP,ECHO> mtu 16 qdisc noop state DOWN mode DEFAULT group default qlen 10
link/can 
```

```
sudo ip link set can0 up type can bitrate 500000
```
