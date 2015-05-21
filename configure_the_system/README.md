# Configure the System

There are a few modifications suggested to be made to make ROS more effective.

## Making enough disk space

The IFC6410 has 4 GB of disk space but after all the various required system directories the filesystem is effectively only has 2GB available for the root filesystem.

To make more space available it is suggested to use a MicroSD card to expand available disk space.

There are instructions for putting the whole OS on the SD card, however those instructions have not been shown to be effective and have been discouraged on forums.

### Install the SD card

Put a >4GB SD card into the board formatted as ext4.

### Configure mounting

We will wand the microSD card to be mounted in /opt to enable the installation of many ROS packages from debian packages.

Run the following command to add a line to `/etc/fstab`. 


```
echo "/dev/mmcblk1p1 /opt ext4 defaults" | sudo tee -a /etc/fstab
```

This assumes that you have formatted the microSD card as a single partition.

Reboot to make sure it's all installed

Make /opt browsable.

```
sudo chmod o+x /opt
```




### Move /var to the SD card

Install rsync:

```
sudo apt-get install rsync
```

Copy var into /opt

```
sudo rsync -aP /var /opt/
```

Set up the mount point by adding the following to `/etc/fstab`:

```
echo "/opt/var /var none bind" | sudo tee -a /etc/fstab
```

Remove the old data

```
sudo rm -rf /var/*
```

Now mount the directory in the new location

```
sudo mount /var
```

### Move /home to the uSD card

Copy home into /opt

```
sudo rsync -aP /home /opt/
```

Set up the mount point by adding the following to `/etc/fstab`:

```
echo "/opt/home /home none bind" | sudo tee -a /etc/fstab
```

Remove the old data

```
sudo rm -rf /home/*
```

Now mount the directory in the new location

```
sudo mount /home
```

If you're in the user directory. It will have moved underneath you. This will avoid cwd issues.

```
cd .
```

### Move /usr to the uSD card

WARNING: This will require a immediate reboot, the computer will become non-operational until rebooted when /usr is moved below.

Copy /usr into /opt

```
sudo rsync -aP /usr /opt/
```

Create the new mount point

```
echo "/opt/usr /usr none bind" | sudo tee -a /etc/fstab
```

Move the current /usr directory to a new location so we can clean it up later.

```
sudo mv /usr /usr.bak
```

#### HARD Reboot!

With usr moved from it's usual place your installation will not operate. You will need to hard powercycle to wait for `/usr` to be remounted on reboot.


Assuming this came up lets clean up the old copy of /usr:

```
sudo rm -rf /usr.bak
```
### Create a user accont to use

We will also want our home directory to be on the larger disk. We will use USERNAME as the standing for your perferred username.

Create the user
```
sudo adduser USERNAME
```

You will probably want to give your user admin access

```
sudo adduser USERNAME admin
```

This is not strictly necessary but is likely desired.

# Misc Tuning advice

These are some tips for making the system work better.

## Remove hardcoded ethernet address

The hardcoded ethernet settings are necessary for the developer edition, but get in the way of the full gnome version with an active network manager.

Comment out the following lines in `/etc/network/interfaces`
```
#auto eth0
#iface eth0 inet dhcp
```

[Forum Thread](http://mydragonboard.org/community/hw-sw-8064/ifc6410-bsp-1-3-does-not-sutdown-eth0-interface-when-ethernet-cable-is-unplugged/)


## Fix ping permissions

My default ping requires sudo:

```
sudo chmod u+s `which ping`
```

## Networking

In case wireless networking with NetworkManager becomes unreliable, you can just follow these instructions to configure the wireless adapter:

https://wiki.debian.org/WiFi/HowToUse#wpa_supplicant
