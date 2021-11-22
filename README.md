# RT-N10P
FreshTomato firmware on ASUS RT-N10P

To free up some NVRAM execute the following ASAP -- connect via telnet or use Web GUI (Tools / System Commands):

for line in `nvram show | grep ^[^=]*=$ `; do var=${line%*=}; nvram unset $var; done; nvram commit

https://www.linksysinfo.org/index.php?threads/freshtomato-on-e2500v3-very-low-nvram-free-space.75721/#post-317937
https://www.snbforums.com/threads/any-hopes-to-ever-have-network-map-device-list-ever-again.60200/post-528701
