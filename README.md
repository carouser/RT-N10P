# FreshTomato firmware on ASUS RT-N10P

## 1 -- select and download the appropriate firmware version

Review [compatibility](https://wiki.freshtomato.org/doku.php/hardware_compatibility) and [features](https://wiki.freshtomato.org/doku.php/feature_matrix) to select and [download](https://freshtomato.org/downloads/freshtomato-mips/2021/2021.7/K26RT-N/Asus%20RT-Nxx%20%26%20CO/) the proper version.

The safe choice is [Mini](https://freshtomato.org/downloads/freshtomato-mips/2021/2021.7/K26RT-N/Asus%20RT-Nxx%20%26%20CO/freshtomato-K26-NVRAM32K_RT-N5x-MIPSR2-2021.7-Mini.zip) or you may try [Max](https://freshtomato.org/downloads/freshtomato-mips/2021/2021.7/K26RT-N/Asus%20RT-Nxx%20%26%20CO/freshtomato-K26-NVRAM32K_RT-N5x-MIPSR2-2021.7-Max.zip) as I did.

## 2 -- put the router into Rescue Mode and use TFTP to upload the TRX file

```
2.1 -- reset to factory defaults (keep WPS button pressed while switching power on)
2.2 -- change local IP to 192.168.1.15
2.3 -- put the router into Rescue Mode (keep hidden RESET switch pressed while switching power on)
2.4 -- upload TRX file to the router:
  tftp -i 192.168.1.1 PUT freshtomato-K26-NVRAM32K_RT-N5x-MIPSR2-2021.7-Max.trx
2.5 -- wait for 5 minutes and reboot the router
```

## 3 -- free up some NVRAM ASAP

Connect via telnet or use Web GUI (Tools / System Commands) to execute:
```
for line in `nvram show | grep ^[^=]*=$ `; do var=${line%*=}; nvram unset $var; done; nvram commit
```
https://www.linksysinfo.org/index.php?threads/freshtomato-on-e2500v3-very-low-nvram-free-space.75721/#post-317937

https://www.snbforums.com/threads/any-hopes-to-ever-have-network-map-device-list-ever-again.60200/post-528701
