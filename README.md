#This script checks the status of Softether on the vpn-rwc server. 
#0 = running; 2 = not running.

STATE_OK=0
STATE_WARNING=1
STATE_CRITICAL=2
STATE_UNKNOWN=3

        for status in $(vpncmd localhost /server  /hub:care2hub /cmd statusget|grep "Status"|tail -1|cut -b 31-)

        do

                if [ "$status" == Online ]

                then

                echo $STATE_OK

                 else

                 echo $STATE_CRITICAL 

                 fi

        done

