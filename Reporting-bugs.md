# Reporting bugs
--------------------------------------------

If you have found a bug in *guh*, please create a new issue with the "**bug**" label in the related repository:

* *guh*-daemon - [https://github.com/guh/guh/issues](https://github.com/guh/guh/issues)
* *guh*-cli - [https://github.com/guh/guh-cli/issues](https://github.com/guh/guh-cli/issues)
* *guh*-webinterface - [https://github.com/guh/guh-webinterface/issues](https://github.com/guh/guh-webinterface/issues)

If you don't know where the bug occurs, please use the *guh*-daemon issues link.

## Steps to find out whats wrong

1. In order to find out what's wrong it's very helpful to start the *guh* daemon in the foreground:

        $ guhd -n

    Now you can follow the debug output of the core and check what's going on.
    In order to get detailed information about a certain part of *guhd* it's helpful to use the debug categories. You can find a list of available debug categories with the command

        $ guhd -h

    In order to enable a certain categorie you can start *guhd* with following command:

        $ guhd -n -d <DebugCategory>

2. Make sure, there is only one instance of `guhd` running on your system, otherwise they will block each others ports.
3. Try to use the [guh-cli](https://github.com/guh/guh/wiki/guh-cli) (which is communicating directly with the JSON-RPC API)
4. If you have made an upgrade of guh, a plugin configuration might have changed. Try to reset the configurations (see [here](https://github.com/guh/guh/wiki/Configuration)) and restart the guh daemon.


## Questions, Comments, and Troubleshooting

If you have any questions, you can get help in following locations:

* [guh-community](https://plus.google.com/u/0/communities/113467056514652214831)
* [guh-blog](https://blog.guh.guru)
* [#guh]() IRC channel on [freenode.net](https://freenode.net/)

If you need any help with *guh* or if you are not shore if something is really a bug, or how to reprodue it please use one of the above channels.









