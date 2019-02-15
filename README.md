#!/bin/bash

#This script checks the status of Softether on the vpn-rwc server.
#0 = running; 2 = not running.


 STATE_OK=0
 STATE_WARNING=1
 STATE_CRITICAL=2
 STATE_UNKNOWN=3

 status=$(/usr/bin/vpncmd localhost /server  /hub:care2hub /cmd statusget|grep "Status"|tail -1|cut -b 31-)

 if [[ "$status" == "Online" ]]

  then

    echo "VPN Server up"
    exit 0

  else

    echo  "VPN Server down"
    exit 2
 fi
