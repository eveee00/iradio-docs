---
title: File exchange
layout: default
nav_order: 4
---
You can get files from and to the radio by using FTP.

## Getting files from the radio
In this example, I am uploading a file from /UIData to my server:

```
# ftpput -v -u USERNAME -p PASSWORD FTPSERVER a /UIData/connection_1.bin 
Connecting to FTPSERVER (FTPSERVER:21)
ftpput: cmd (null) (null)
ftpput: cmd USER USERNAME
ftpput: cmd PASS PASSWORD
ftpput: cmd TYPE I (null)
ftpput: cmd PASV (null)
ftpput: cmd STOR a
ftpput: cmd (null) (null)
ftpput: cmd QUIT (null)
# 
```

## Uploading files to the radio

*Do note that any uploaded files will get wiped upon reboot. This is because the filesystem is a CPIO image that is mounted to RAM*

*This doesn't apply to the /flash directory, since a JFFS2 FS is mounted there.*

```
# ftpget -v -u USERNAME -p PASSWORD FTPSERVER /tmp/test/bonzi.png pic/bonzi.png
Connecting to FTPSERVER (FTPSERVER:21)
ftpget: cmd (null) (null)
ftpget: cmd USER USERNAME
ftpget: cmd PASS PASSWORD
ftpget: cmd TYPE I (null)
ftpget: cmd PASV (null)
ftpget: cmd SIZE pic/bonzi.png
ftpget: cmd RETR pic/bonzi.png
ftpget: cmd (null) (null)
ftpget: cmd QUIT (null)
# ls /tmp/test          
bonzi.png
# 
```