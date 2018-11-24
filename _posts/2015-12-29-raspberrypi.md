---
layout: post
title:  "raspberrypi 설정"
date:   2015-12-29
---

라즈베리 파이 

설치
------------------
1. vim,htop
2. samba
3. pptpd(vpn 서버)
4. nfs
5. transmission-daemon(https://gist.github.com/i9yang/59475caffb6fcdeb9430ef8e9da0647f)
6. jq(json 파싱)
7. ntfs-3g(ntfs)

fstab
------------------
1. /dev/sda1       /media/usb      ext4    defaults        0       0


mount -t cifs //192.168.0.8/500G/NVIDIA_SHIELD /srv/shield -o user=i9yang,pass=kj-venus-bunt,iocharset=utf8,file_mode=0777,dir_mode=0777,vers=1.0
