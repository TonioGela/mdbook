# How to setup a server as a time-machine backup

### Get a static IP in your network

`192.168.0.99` will be your static ip, while `192.168.0.1` is your home router ip.

```
$ sudo nmcli connection show
NAME                UUID                                  TYPE      DEVICE 
Wired connection 1  91d78f79-c7cf-32fc-8a91-bc3d587a2461  ethernet  enp0s3 
virbr0              b5402c70-eb3d-4a45-a7ad-43e1652798b1  bridge    virbr0
```

```
$ sudo nmcli connection modify 91d78f79-c7cf-32fc-8a91-bc3d587a2461 IPv4.method  manual
$ sudo nmcli connection modify 91d78f79-c7cf-32fc-8a91-bc3d587a2461 IPv4.address 192.168.0.99/24
$ sudo nmcli connection modify 91d78f79-c7cf-32fc-8a91-bc3d587a2461 IPv4.gateway 192.168.0.1
$ sudo nmcli connection modify 91d78f79-c7cf-32fc-8a91-bc3d587a2461 IPv4.dns     192.168.0.1
```

```
$ sudo nmcli connection down 91d78f79-c7cf-32fc-8a91-bc3d587a2461
$ sudo nmcli connection up 91d78f79-c7cf-32fc-8a91-bc3d587a2461
```

```
$ ping www.google.com
```

### Install Netatalk and Avahi

```
$ dnf install -y netatalk avahi
```

Assign timemachine to the right user
```
$ chown timemachine:timemachine /timemachine
```

```
$ vi /etc/netatalk/afp.conf
[Name of the Time Machine Volume in Time Machine]
path = /timemachine
time machine = yes
valid users = timemachine // assuming this is you user
```

You can repeat the configuration up here for multiple volumes

```
$ systemctl enable --now netatalk avahi-daemon
```

### Add firewall rules 

```
$ firewall-cmd --permanent --add-port={548,5353,49152,52883}/{tcp,udp}
$ firewall-cmd --reload
```

### Prevent lid turning off the server
```
$ sudo vi /etc/systemd/logind.conf
HandleLidSwitch=ignore
```
