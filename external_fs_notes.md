# External FS Notes

These are nots about working on getting external fs to work. 


Following the section of [14.10 ifc6410 root fs on external storage])http://releases.linaro.org/14.10/ubuntu/ifc6410)


## Need to install android fs tools

```
sudo apt-get install android-tools-fsutils

sudo apt-get install abootimg
```

```
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ sudo apt-get  install android-tools-fsutils
[sudo] password for tfoote: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  android-tools-fsutils
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 65.6 kB of archives.
After this operation, 493 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main android-tools-fsutils amd64 4.2.2+git20130218-3ubuntu23 [65.6 kB]
Fetched 65.6 kB in 0s (145 kB/s)               
Selecting previously unselected package android-tools-fsutils.
(Reading database ... 470076 files and directories currently installed.)
Preparing to unpack .../android-tools-fsutils_4.2.2+git20130218-3ubuntu23_amd64.deb ...
Unpacking android-tools-fsutils (4.2.2+git20130218-3ubuntu23) ...
Setting up android-tools-fsutils (4.2.2+git20130218-3ubuntu23) ...
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ ls
firmware-ifc6410-20141024-37.img  linaro_1410_boot.img  linaro-trusty-gnome-ifc6410-20141024-37.img
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ simg2img linaro-trusty-gnome-ifc6410-20141024-37.img linaro-trusty-gnome-ifc6410-20141024-37.img.raw
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ ls
firmware-ifc6410-20141024-37.img  linaro_1410_boot.img  linaro-trusty-gnome-ifc6410-20141024-37.img  linaro-trusty-gnome-ifc6410-20141024-37.img.raw
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ mkdir rootfs
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ sudo mount -o loop linaro-trusty-gnome-ifc6410-20141024-37.img.raw rootfs
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ cd rootfs/
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/rootfs$ ls
bin  boot  dev  etc  home  lib  lost+found  md5sum.txt  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/rootfs$ ls /media/tfoote/20f92951-480d-443f-98b7-c39cb0a88056/
bin  boot  dev  etc  home  lib  lost+found  md5sum.txt  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/rootfs$ cd /media/tfoote/20f92951-480d-443f-98b7-c39cb0a88056/
tfoote@yeti:/media/tfoote/20f92951-480d-443f-98b7-c39cb0a88056$ ls
bin  boot  dev  etc  home  lib  lost+found  md5sum.txt  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
tfoote@yeti:/media/tfoote/20f92951-480d-443f-98b7-c39cb0a88056$ sudo rm -rf *
tfoote@yeti:/media/tfoote/20f92951-480d-443f-98b7-c39cb0a88056$ cd -
/home/tfoote/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/rootfs
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/rootfs$ sudo cp -a * /media/tfoote/20f92951-480d-443f-98b7-c39cb0a88056/
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/rootfs$ sudo umount /media/tfoote/20f92951-480d-443f-98b7-c39cb0a88056 
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/rootfs$ cd ..
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ ls
firmware-ifc6410-20141024-37.img  linaro_1410_boot.img  linaro-trusty-gnome-ifc6410-20141024-37.img  linaro-trusty-gnome-ifc6410-20141024-37.img.raw  rootfs
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ abootimg
The program 'abootimg' is currently not installed. You can install it by typing:
sudo apt-get install abootimg
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ sudo apt-get install abootimg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  abootimg
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 15.1 kB of archives.
After this operation, 86.0 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe abootimg amd64 0.6-1 [15.1 kB]
Fetched 15.1 kB in 0s (53.7 kB/s) 
Selecting previously unselected package abootimg.
(Reading database ... 470088 files and directories currently installed.)
Preparing to unpack .../abootimg_0.6-1_amd64.deb ...
Unpacking abootimg (0.6-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up abootimg (0.6-1) ...
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ man abootimg 
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ ls
firmware-ifc6410-20141024-37.img  linaro_1410_boot.img  linaro-trusty-gnome-ifc6410-20141024-37.img  linaro-trusty-gnome-ifc6410-20141024-37.img.raw  rootfs
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ mkdir tmp
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries$ cd tmp/
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/tmp$ cp ../linaro_1410_boot.img .
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/tmp$ abootimg -u linaro_1410_boot.img -c "cmdline=console=ttyHSL0,115200n8 root=/dev/mmcblk1p1 rootwait rw text"
reading config args
Writing Boot Image linaro_1410_boot.img
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/tmp$ sudo fastboot devices
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/tmp$ sudo fastboot devices
153cfd2                                                                         fastboot
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/tmp$ ls
linaro_1410_boot.img
tfoote@yeti:~/ifc6410/bsp1.5/IFC6410_Ubuntu_Linux_BSP_880348_V1.5/binaries/tmp$ sudo fastboot flash boot linaro_1410_boot.img 
sending 'boot' (9216 KB)...
OKAY [  0.291s]
writing 'boot'...
OKAY [  0.801s]
finished. total time: 1.092s
```
