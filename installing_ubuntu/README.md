# Installing Ubuntu

## Installing base image

You will need to start by installing Ubuntu on your machine. There is a linaro build for IFC6410

http://releases.linaro.org/14.05/ubuntu/ifc6410

(Don't use newer Linaro builds; the SD card support is broken, see the [Discussion Forum Post](http://mydragonboard.org/community/hw-sw-8064/sd-card-support-in-linaro-14-09-on-ifc6410/) )

This is great except that to use the board successfully you will need the proprietary firmware from [InForce's TechWeb](http://www.inforcecomputing.com/techweb/).

The instructions from Linaro tell how to overlay the firmware onto your image. Inforce also provides a fully baked image available from the TechWeb website.

Unfortunately it requires registration to get access to the TechWeb site.

There are more details on most of this process on the [Linaro landing page](http://releases.linaro.org/14.05/ubuntu/ifc6410)


### Flash the OS onto the device

You will need to flash the images onto the board using fastboot.

To get the board into fastbook you need to jumper pins 30 to 25 on the largest connector. Detalis with pictures [in this article](http://mydragonboard.org/2013/forcing-ifc6410-into-fastboot/).


```
sudo fastboot flash boot boot-ifc6410-20140526-15.img
sudo fastboot flash cache firmware-ifc6410-20140526-15.img
sudo fastboot flash -S 768M userdata linaro-trusty-gnome-ifc6410-20140526-15.img
```

#### Prereqisites.
More documentation of this process can be found on the linaro page.


### Boot to Ubuntu

Remove the jumper and reboot the machine now. It should give you a login prompt.

There's a default user linaro:linaro.

And tty1 will autologin as root.


#### Start GDM

If you don't get the graphical login start gnome by running

```
service gdm start
```
