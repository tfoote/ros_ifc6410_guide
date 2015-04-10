# Installing Ubuntu

## Installing base image

You will need to start by installing Ubuntu on your machine. There is a linaro build for IFC6410

http://releases.linaro.org/14.05/ubuntu/ifc6410

This is great except that to use the board successfully you will need the proprietary firmware from [InForce's TechWeb](http://www.inforcecomputing.com/techweb/).


The instructions from Linaro tell how to overlay the firmware onto your image.
Inforce also provides a fully baked image available from the TechWeb website.
For simplicity it's recommended to pull BSP 1.3 from the Linaro TechWeb site.
It will include the images already built.
There is also a PDF guide for installing with these instructions in the BSP.

Unfortunately it requires registration to get access to the TechWeb site.

There are more details on most of this process on the [Linaro landing page](http://releases.linaro.org/14.05/ubuntu/ifc6410)


### Flash the OS onto the device

You will need to flash the images onto the board using fastboot. 

The images are contained in the BSP 1.3 downloaded from Inforce, they already contain the proprietary firmware. You do not need to follow the Linaro instructions for inserting them into the images. 

To get the board into fastbook you need to jumper pins 30 to 26 on the largest connector.
Details with pictures [in this article](http://mydragonboard.org/2013/forcing-ifc6410-into-fastboot/).

After adding the jumper plug in the USB and the DC power. You should see multiple LEDs. (USB slave power is not enough, some LEDs will turn on but the board won't boot.)

You will want to install `android-tools-fastboot`

If the device is available in fastboot mode `sudo fastboot devices` will list the device.

To flash the devices use the following commands from inside the extracted BSP. 

```
sudo fastboot flash boot linaro_1410_boot.img
sudo fastboot flash cache firmware-ifc6410-20141024-37.img
sudo fastboot flash -S 768M userdata linaro-trusty-gnome-ifc6410-20141024-37.img
sudo fastboot reboot
```

Note: flashing the userdata will take a few minutes. 

#### Prereqisites.
More documentation of this process can be found on the linaro page.


### Boot to Ubuntu

Remove the jumper and reboot the machine now. It should give you a login prompt.

I recommend having an ethernet cable plugged in for the first boot so that it can pick up the date from the network.
If you do not it will have a date in 1979 and several things will fail such as SSL certificates.
Once the date is set correctly you will be fine again. 

There's a default user linaro:linaro.

And tty1 will autologin as root.


#### Start GDM

If you don't get the graphical login start gnome by running

```
service gdm start
```
