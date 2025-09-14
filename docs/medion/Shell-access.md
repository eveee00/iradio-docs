---
title: (MD) Shell access
layout: default
parent: MD Radio
nav_order: 1
---


## Shell access

Telnet is present on my device since it wasn't updated.

```
$ telnet [ip]
Trying 192.168.178.194...
Connected to 192.168.178.194.
Escape character is '^]'.

(none) login: root
Password: password


BusyBox v1.15.2 (2014-05-05 11:57:25 CST) built-in shell (ash)
Enter 'help' for a list of built-in commands.

# cat /proc/cpuinfo
Processor       : ARM926EJ-S rev 5 (v5l)
BogoMIPS        : 119.60
Features        : swp half thumb fastmult edsp java 
CPU implementer : 0x41
CPU architecture: 5TEJ
CPU variant     : 0x0
CPU part        : 0x926
CPU revision    : 5

Hardware        : W55FA93
Revision        : 0000
Serial          : 0000000000000000
# exit
Connection closed by foreign host.
```

# Adding SSH

If you don't like telnet, you can add temporary SSH access _without_ flashing a modified binary.

_Note: this method still requires telnet and it will not persist after a reboot. but it is an alternative to modding the firmware._

- Download DropBear from [here](https://bitfab.org/dropbear-static-builds/) (get the arm static .tgz)
- [Get it onto the radio.](http://docs.eveee00.xyz/docs/medion/fw-etc/files/up-and-download.html) (I recommend putting it into /bin)
- Make it executeable:

```sh
chmod +x ./dropbearmulti
```

- Create `/.ssh/authorized_keys` (Yes, password auth is broken (at least for me))

```sh
mkdir /.ssh
cd /.ssh
echo "YOUR_PUBLIC_KEY" > authorized_keys
```

- Start DropBear

```sh
dropbearmulti dropbear -R -s
```
_Note: yes, I'm also disabling password auth here alltogether, but this doesn't have to do with it not working_

- Connect

```
$ ssh root@[IP]
[1461] Sep 14 01:43:35 wtmp_write: problem writing /dev/null/wtmp: Not a directory


BusyBox v1.15.2 (2014-05-05 11:57:25 CST) built-in shell (ash)
Enter 'help' for a list of built-in commands.

# ls
UIData   data     flash    mplayer  sbin     usr
attach   dev      linuxrc  proc     sys      var
bin      etc      mnt      root     tmp

```

- (OPTIONAL) Kill telnetd

You can kill telnetd if you only want ssh

```sh
killall telnetd
```

