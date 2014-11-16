# Configure the System

There are a few modifications suggested to be made to make ROS more effective.

## Making enough disk space

The IFC6410 has 4 GB of disk space but after all the various required system directories the filesystem is effectively only has 2GB available for the root filesystem.

To make more space available it is suggested to use a MicroSD card to expand available disk space.

### Install the SD card

Put a >4GB SD card into the board formatted as ext4.

### Configure mounting

We will wand the microSD card to be mounted in /opt to enable the installation of many ROS packages from debian packages.

Edit /etc/fstab and add the following line:


```
/dev/mmcblk1p1 /opt ext4 defaults
```

This assumes that you have formatted the microSD card as a single partition.

Reboot to make sure it's all installed

Make /opt browsable.

```
chmod o+x /opt
```


### Create a user accont with a home directory in /opt

We will also want our home directory to be on the larger disk. We will use USERNAME as the standing for your perferred username.

Create the user
```
adduser USERNAME
```

You will probably want to give your user admin access

```
adduser USERNAME sudo
```

Create /opt/USERNAME

```
mkdir /opt/USERNAME
```

Give it to the user:

```
chown -R USERNAME:USERNAME /opt/USERNAME
```

Update the user settings:

```
usermod -d /opt/USERNAME -m USERNAME
```
[More info](https://superuser.com/questions/40450/how-does-one-change-users-home-directory-in-ubuntu-9-04)


