# Installing Ubuntu

## Installing base image

You will need to start by installing Ubuntu on your machine. There is a linaro build for IFC6410

http://releases.linaro.org/14.05/ubuntu/ifc6410

This is great except that to use the board successfully you will need the proprietary firmware from [InForce's TechWeb](http://www.inforcecomputing.com/techweb/).

The instructions from Linaro tell how to overlay the firmware onto your image. Inforce also provides a fully baked image available from the TechWeb website.

Unfortunately it requires registration to get access to the TechWeb site.

There are more details on most of this process on the [Linaro landing page](http://releases.linaro.org/14.05/ubuntu/ifc6410)


### Flash the OS onto the device

You will need to flash the images onto the board using fastboot.

To get the board into fastbook you need to jumper pins 30 to 25 on the largest connector. Detalis with pictures [in this article](http://mydragonboard.org/2013/forcing-ifc6410-into-fastboot/).


```
sudo fastboot flash boot boot-ifc6410-${VERSION}.img
sudo fastboot flash cache firmware-ifc6410-${VERSION}.img
sudo fastboot flash -S 768M userdata linaro-trusty-gnome-ifc6410-${VERSION}.img
```


### SD Card Mounting Issue

In the build ifc6410-20140526-15 the SDCard cannot be mounted read/write. It's been patched upstream:

* [Discussion Forum Post](http://mydragonboard.org/community/hw-sw-8064/sd-card-support-in-linaro-14-09-on-ifc6410/)
* [Linaro build patch](https://git.linaro.org/people/nicolas.dechesne/qcom-lt/kernel.git/commit/879c0e014159af05c920429949b41d9ac6aae767)

If there is not a new version released yet you will need to rebuild this kernel and patch it into using the below instructions.

#### Rebuild the Kernel

TODO

#### Rebuild the boot image

With the built kernel image you will need to inject it into the boot image.

You may want to make a backup of the img as the command will mutate it.

```
abootimg -u boot-ifc6410-${VERSION}.img -k ifc6410-custom-kernel-image
```

#### Upload the boot image

You will now need to flash the boot image onto the device.

```
sudo fastboot flash boot boot-ifc6410-20140526-15.img
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
