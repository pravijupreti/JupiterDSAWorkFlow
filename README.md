#!/bin/sh
# When suspending/resuming, systemd will call executables in /lib/systemd/system-sleep 
# with the following parameters:
# $1 = either "pre" or "post"
# $2 = "suspend", "hibernate", "hybrid-sleep" or "suspend-then-hibernate"
INTERFACE=wlan0
DRIVER_MODULE=<driver module name>    

case "$1" in
    pre)
        nmcli device disconnect $INTERFACE
        modprobe -r $DRIVER_MODULE
        ;;
    post)
        modprobe $DRIVER_MODULE
        nmcli device connect $INTERFACE
        ;;
esac

# Don't stop suspending/resuming even if we fail somehow.
exit 0
