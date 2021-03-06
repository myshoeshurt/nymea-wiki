# Install *guhIO* on ubuntu-core (Snappy)
--------------------------------------------

> Ubuntu Core provides transactional updates with rigorous application isolation. This is the smallest, safest Ubuntu ever, on devices and on the cloud. We’re excited to unleash a new wave of developer innovation with snappy Ubuntu Core! ” - *Mark Shuttleworth, founder of Ubuntu and Canonical*.

So we decided to try the new system to use the advantages of the snappy package system and give you the possibility to play with Ubuntu Core and guh on you [Beaglebone Black](http://beagleboard.org/BLACK) or [Raspberry Pi 2](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/). You can find a good documentation of the new operating system from Canonical [Ubuntu Core](https://developer.ubuntu.com/en/snappy/).

Currently we provide a guhIO snappy package only `armhf`, but we have planned to change that soon. If you want to install guhIO on you device you can do following: 

## Install snappy tools

First you need to add the PPA file:

        $ sudo add-apt-repository ppa:snappy-dev/tools

Now you can install the snappy-tools

        $ sudo apt-get update
        $ sudo apt-get upgrade
        $ sudo apt-get install snappy-tools bzr

## Prepare SD card

If you want to install Ubuntu Core on your device, you can follow the [official instruction](https://developer.ubuntu.com/en/snappy/start/#try-beaglebone) or use this one.

### Beaglebone Black

1. Download the system

        $ wget http://releases.ubuntu.com/15.04/ubuntu-15.04-snappy-armhf-bbb.img.xz
 
2. Insert SD card (minimum 4GB) in your system and check which device it is:

        $ lsblk
        NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
        sda      8:0    0 465,9G  0 disk 
        ├─sda1   ...
        └─sda5   ...
         sdb      8:16   1   7,2G  0 disk 
        ├─sdb1   8:17   1    64M  0 part 
        ├─sdb2   8:18   1     1G  0 part 
        ├─sdb3   8:19   1     1G  0 part 
        └─sdb4   8:20   1   1,6G  0 part 

In this example I have a 8 GB SD card which is device `/dev/sdb`.

3. Extrackt the image:

        $ unxz ubuntu-15.04-snappy-armhf-bbb.img.xz

4. Flash the image to the SD card:
    > **Note:** this will delete all data from your micro SD!    

        $ sudo dd if=ubuntu-15.04-snappy-armhf-bbb.img of=/dev/sdX bs=32M
        $ sync

    > **Note:** check [official instructions](https://developer.ubuntu.com/en/snappy/start/#try-beaglebone) for more information.

5. Once the installation is finished you can insert the SD card into your Beaglebone Black and power it on. When the system has started you can log in with ssh in you new system:

        $ ssh ubuntu@webdm.local	# password: ubuntu


### Raspberry Pi 2

1. Download the system

        $ wget http://people.canonical.com/~platform/snappy/raspberrypi2/ubuntu-15.04-snappy-armhf-rpi2.img.xz
 
2. Insert SD card (minimum 4GB) in your system and check which device it is:

        $ lsblk
        NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
        sda      8:0    0 465,9G  0 disk 
        ├─sda1   ...
        └─sda5   ...
         sdb      8:16   1   7,2G  0 disk 
        ├─sdb1   8:17   1    64M  0 part 
        ├─sdb2   8:18   1     1G  0 part 
        ├─sdb3   8:19   1     1G  0 part 
        └─sdb4   8:20   1   1,6G  0 part 

In this example I have a 8 GB SD card which is device `/dev/sdb`.

3. Extract the image:

        $ unxz ubuntu-15.04-snappy-armhf-rpi2.img.xz

4. Flash the image to the SD card:
    > **Note:** this will delete all data from your micro SD!    

        $ sudo dd if=ubuntu-15.04-snappy-armhf-rpi2.img of=/dev/sdX bs=32M
        $ sync

    > **Note:** check [official instructions](https://developer.ubuntu.com/en/snappy/start/#snappy-raspi2) for more information.

5. Once the installation is finished you can insert the SD card into your Raspberry Pi 2 and power it on. When the system has started you can log in with ssh in you new system:

        $ ssh ubuntu@webdm.local	# password: ubuntu


## Install guh snap

1. Download the latest guh snappy package [guhio_0.1.8_armhf.snap](https://guh.guru/downloads/snappy/guhio_0.1.8_armhf.snap):

        $ wget https://guh.guru/downloads/snappy/guhio_0.1.8_armhf.snap

2. Install guh snappy on the device:

    > **Note:** the avahi sometimes does not work correctly. In this case try to replace `webdm.local` with the ip of your device.

        $ snappy-remote --url=ssh://webdm.local:22 install guhio_0.1.8_armhf.snap

        =======================================================
        Installing guhio_0.1.8_armhf.snap from local environment
        Installing /tmp/guhio_0.1.8_armhf.snap
        2015/09/30 12:19:05.216483 verify.go:85: Signature check failed, but installing anyway as requested
        Name        Date       Version      Developer 
        ubuntu-core 2015-09-25 2            ubuntu    
        guhio       2015-09-30 ICGAWgEBRJKY sideload  
        webdm       2015-09-25 0.9          canonical 
        pi2         2015-09-25 0.16         canonical
        =======================================================


Now you have successfully installed guh on your `armhf` device and can continue with [[Getting-started-snappy]]































