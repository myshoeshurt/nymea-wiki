# Install *guh*-core on Debian

Debian Wheezy will not be supported since there are missing important Qt libs.

------------------------------------------------------------
| Debian     |  Wheezy 7.0  |  Jessie 8.0  |  Stretch 9.0  |
|:-----------|-------------:|:------------:|:-------------:|
| `amd64`    |       ✘      |       ✔      |       ✔       |
| `i386`     |       ✘      |       ✔      |       ✔       |
| `armhf`    |       ✘      |       ✔      |       ✔       |
| `arm64`    |       ✘      |       ✔      |       ✔       |
------------------------------------------------------------

In order to install *guh* on Debian you need to create the `/etc/apt/sources.list.d/guh.list` file and add the *guh*-repository:

1. Create the [*guh*-repository](http://repository.guh.io) list file:
        
        $ sudo nano /etc/apt/sources.list.d/guh.list
        
    In the repository are following distributions available:
    * `jessie` 
    * `stretch`

    Available architectures are `amd64` `i386` `armhf` and `arm64`.
    
    > *Note:* You can get your system version with `cat /etc/os-release`. 

    Copy following lines into the file and save it:

        ## guh repo
        deb http://repository.guh.io jessie main
        deb-src http://repository.guh.io jessie main
        

    > **Alternative:** `$ echo -e "\n## guh repo\ndeb http://repository.guh.io jessie main\ndeb-src http://repository.guh.io jessie main" | sudo tee /etc/apt/sources.list.d/guh.list`
    
    Add the public key of the [*guh*-repo](http://repository.guh.io) to your keylist.
    
        $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key A1A19ED6
    
        
2. Update your package lists:
    
        $ sudo apt-get update

    The *guh*-repo provides following packages:
    
        $ apt-cache search guh
    
        guh - An open source IoT server - meta package
        guh-cli - guh command line interface - python
        guh-dbg - An open source IoT server - debug symbols
        guh-doc - Documentation for the guh package (on-site) - documentation
        guh-plugins - Plugins for guh IoT server
        guh-plugins-maker - Plugins for guh IoT server - Meta package for makers, tinkers and hackers
        guh-plugins-merkurboard - Plugins for guh IoT server - Meta package for 6LoWPAN Merkur boards
        guh-plugins-433mhz - Plugins for guh IoT server - Meta package for RF 433 MHz plugins
        guh-plugins-all - Plugins for guh IoT server - Meta package for all plugins
        guh-tests - Tests and mock plugin for the guh package
        guh-webinterface - Browser based user interface for guh
        guh-webinterface-doc - Documentation of the guh webinterface source code (on-site) - documentation
        guhd - An open source IoT server - daemon
        libguh1 - An open source IoT server - core library
        libguh1-dev - An open source IoT server - development files


3. Install *guh* with following command:
    
        $ sudo apt-get install guh guh-plugins guh-cli guh-webinterface
        
    The repository contains always the latest stable build of the *guh* `master` branch. 
    If you want to install the source code you can install:
        
        $ sudo apt-get source guh        
        $ sudo apt-get source guh-cli
        $ sudo apt-get source guh-webinterface
        
Once, the installation is finished you continue with the [[Getting started]] instruction.


