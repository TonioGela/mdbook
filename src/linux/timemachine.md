## TimeMachine on CasaOs

Taken from:
- https://github.com/IceWhaleTech/CasaOS/issues/1030
- https://mxnr.net/time-machine-on-zimaboard/amp/
- https://wiki.samba.org/index.php/Configure_Samba_to_Work_Better_with_Mac_OS_X

1) `ssh casaos@casaos.local`
2) `sudo useradd toniogela`
3) `sudo smbpasswd -a toniogela`
4) `cd /mnt/diskname && sudo mkdir timemachine`
5) `sudo chown toniogela:toniogela timemachine`
6) `sudo apt install samba-vfs-modules`
7) `sudo vi /etc/samba/smb.conf`

Add under `[global]`
```
   min protocol = SMB2
   ea support = yes
   vfs objects = fruit streams_xattr
   fruit:metadata = stream
   fruit:model = TimeCapsule
   fruit:posix_rename = yes
   fruit:veto_appledouble = no
   fruit:nfs_aces = no
   fruit:wipe_intentionally_left_blank_rfork = yes
   fruit:delete_empty_adfiles = yes
```

Create this (but maybe it's useless):
```
[share]
   spotlight backend = elasticsearch
```

Then foreach user (here's `toniogela`) create at bottom:

```
[Time Machine name you will see under MacOs]
   comment = TTime Machine name you will see under MacOs
   path = /mnt/diskname/timemachine
   browseable = yes
   writeable = yes
   guest ok = no
   read only = no
   fruit:time machine = yes
   valid users = toniogela
   durable handles = yes
   kernel oplocks = no
   kernel share modes = no
   posix locking = no
   ea support = yes
   inherit acls = yes
```

reboot and you should be done
