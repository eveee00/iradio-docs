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