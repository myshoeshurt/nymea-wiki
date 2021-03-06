# Configuration
--------------------------------------------

## Settings
--------------------------------------------

The location of the personal settings like configured devices, rules and plugins depends on the user who starts guh.

**User** - If you start guhd as user, the settings can be found in the home directory of the corresponding user: 

        ~/.config/guh/*

**root** -  If you start guhd as root or the system starts it with the init script, the personal settings will be stored in:

        /etc/guh/*


## Reset configuration
 
**user** - If you start guhd as user, you will have to delete following files: 

        $ rm ~/.config/guh/guhd.conf
        $ rm ~/.config/guh/devices.conf
        $ rm ~/.config/guh/rules.conf
        $ rm ~/.config/guh/plugins.conf

**root** -  If you start guhd as root or the system starts it with the init script, you will have to delete following files:

        $ sudo rm /etc/guh/guhd.conf
        $ sudo rm /etc/guh/devices.conf
        $ sudo rm /etc/guh/rules.conf
        $ sudo rm /etc/guh/plugins.conf 

> **Note:** you need to restart guhd to clean up also the runtime configurations after deleting the configuration files.

## Logging Database

The logging database is a sqlite3 database and contains every log event of the guhd server. 

**user** - If you start guhd as user, the logging database will be stored in: 

        ~/.config/guh/guhd.sqlite

**root** -  If you start guhd as root or the system starts it with the init script, the logging database will be stored in: 

        /var/log/guhd.sqlite

To reset the database, just delete the file and restart guhd.

## Log file

The log file contains the debug console logs of the guh daemon. In order to control the files guhd provides a config file for logrotate `/etc/logrotate.d/guhd` 

**user** - If you start guhd as user, the log file will be stored in: 

        ~/.config/guh/guhd.log

>**Note:** if you start guhd as user, logrotate will not trigger on that file. You need to control the filesize by your self (because `guhd` was designed to run as daemon)

**root** -  If you start guhd as root or the system starts it with the init scripts / systemd, the logfile will be stored in: 

        /var/log/guhd.log








