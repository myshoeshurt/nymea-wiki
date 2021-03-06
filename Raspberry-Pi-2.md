# Install *guh* on the Raspberry Pi 2
--------------------------------------------

This tutorial shows you how to install *guh* on the [Raspberry Pi 2](https://www.raspberrypi.org/documentation/hardware/raspberrypi/models/README.md). The easiest and recommended way is to use the preconfigured image provided by *guh*. You can find the latest image [here](https://downloads.guh.io/images/rpi2/2017-01-17-guh-ubuntu-16.04-armhf-raspberry-pi-2.zip). This image was build with the `guh-image-builder` which can be found here:

https://github.com/guh/guh-image-builder

-----------------------------------------------------
### Install needed packages
    
    $ sudo apt-get update
    $ sudo apt-get upgrade
    
    $ sudo apt-get install zip


Download the image:

    $ wget https://downloads.guh.io/images/rpi2/2017-01-17-guh-ubuntu-16.04-armhf-raspberry-pi-2.zip

Once you have downloaded the image you can unzip the file:
   
     $ unzip 2017-01-17-guh-ubuntu-16.04-armhf-raspberry-pi-2.zip


-----------------------------------------------------
### Flash the image to the micro SD card (minimum size 4GB):

> **Note:** Please replace `sdX` with the device of your SD card. You can use `lsblk` to check which device is your SD card. 


    $ sudo dd if=2017-01-17-guh-ubuntu-16.04-armhf-raspberry-pi-2.img of=/dev/sdX bs=1M

Once the process is finished you can insert the micro SD card into the Raspberry Pi 2, connect the ethernet cable and power it on.

-----------------------------------------------------

### Login 
You can try to connect to the Raspberry Pi 2 using the hostname of the device (`guh`):

    $ ssh guh@guh.local    # password: guh

Depending on the network setup `avahi` sometimes does not work. In that case you can connect to the device using the ip address:

> **Note:** Please replace `192.168.0.X` with the ip of your Raspberry Pi 2.

    $ ssh guh@192.168.0.X    # password: guh

Please make an update on the new system to make sure there is the newest version of `guh` installed:

    $ sudo apt-get update
    $ sudo apt-get dist-upgrade


-----------------------------------------------------
### Post installation (optional)

#### Resize rootfs

Once you are logged in successfully, you can resize the partition to the size of your micro SD card.

    $ sudo fdisk /dev/mmcblk0

* Delete the second partition (`d`, `2`) 
* Re-create it using the defaults (`n`, `p`, `2`, `enter`, `enter`) 
* Write and exit (`w`). 

Reboot the system, login and run:

    $ sudo resize2fs /dev/mmcblk0p2

#### Set up timezone

You can select your timezone using following command:

    $ tzselect

Once you have selected your timezone, you can run following command:
> **Note:** Replace `Europe/Vienna` with your selected timezone.

    $ sudo echo "Europe/Vienna" > /etc/timezone
    $ sudo dpkg-reconfigure -f noninteractive tzdata

#### Change password

    $ passwd
  
    Changing password for guh.
    (current) UNIX password: guh
    Enter new UNIX password:
    Retype new UNIX password:
    passwd: password updated successfully


Now you can continue with the [[Getting-Started]] wiki.
