#!/bin/bash
# program to check WiFi and reset if not running
  
#dns server 
IPTEST=1.1.1.1
  
iwconfig=/sbin/iwconfig
lspci=/usr/bin/lspci

#find 802 wireless device id
DEVICE=`$iwconfig 2>/dev/null | egrep 802 | awk ' {print $1}'`

#get PCI bus wireless #  
WLNUM=`$lspci | grep -i wireless | awk ' {print $1}'`
  
#get driver to unload
WLMOD=`$lspci -vv -s $WLNUM | grep -i "kernel driver" | awk ' {print $5}'`
  
  
#print out stats      
echo "IP is: $IPTEST"
echo "DEVICE is: $DEVICE"
echo "PCI DEV NUM is $WLNUM"
echo "PCI DRIVER is $WLMOD"
ping -c 1 $IPTEST

read -n 1 -p "Proceed ? " ANS

if [[ "$ANS" =~ [^yY] ]]; then 
    exit 0
fi
  
echo ""
if ping -c 1 $IPTEST >/dev/null 2>&1 ; 
then
    echo "$IPTEST 1 ok"
    exit 0
else
    echo "Ping failed"

    echo "stopping wifi "
    sudo nmcli radio wifi off
    echo "sleeping for 3..."
    sleep 3

    echo "unloading $DEVICE"
    sudo nmcli device disconnect $DEVICE
    echo "sleeping for 3..."
    sleep 3


    echo "unloading $WLMOD ..."
    sudo modprobe -r $WLMOD
    echo "sleeping for 3..."
    sleep 3

    echo "reloading $WLMOD"
    sudo modprobe $WLMOD
    echo "sleeping for 3..."
    sleep 3

    echo "reloading $DEVICE"
    sudo nmcli device connect $DEVICE
    echo "sleeping for 10..."
    sleep 10

    echo "stop wifi "
    sudo nmcli radio wifi off
    echo "sleeping for 3..."
    sleep 3
    
    echo "starting wifi"
    sudo nmcli radio wifi on
    echo "sleeping for 3..."
    sleep 5

    echo "test ping again ..."
    ping -c 1 $IPTEST
fi
exit 0
