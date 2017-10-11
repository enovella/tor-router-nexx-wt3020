## Configuring your TOR router into a Nexx WT3020

My default configuration after installation

* ESSID=`OnionWRT`
* WPA2=`t0rmenta`
* IP_LAN=`192.168.10.1`
* CREDENTIALS_LUCI_WEB=`root:t0rmenta`


## Luci & OpenWrt & Kernel versioning
```sh
Hostname	OpenWrt
Model	Nexx WT3020
Firmware Version	OpenWrt Chaos Calmer 15.05 / LuCI (git-15.248.30277-3836b45)
Kernel Version	3.18.20
```



## Installation

```sh
$ ssh root@192.168.10.1
root@192.168.10.1's password: t0rmenta


BusyBox v1.23.2 (2015-07-25 03:03:02 CEST) built-in shell (ash)

  _______                     ________        __
 |       |.-----.-----.-----.|  |  |  |.----.|  |_
 |   -   ||  _  |  -__|     ||  |  |  ||   _||   _|
 |_______||   __|_____|__|__||________||__|  |____|
          |__| W I R E L E S S   F R E E D O M
 -----------------------------------------------------
 CHAOS CALMER (15.05, r46767)
 -----------------------------------------------------
  * 1 1/2 oz Gin            Shake with a glassful
  * 1/4 oz Triple Sec       of broken ice and pour
  * 3/4 oz Lime Juice       unstrained into a goblet.
  * 1 1/2 oz Orange Juice
  * 1 tsp. Grenadine Syrup
 -----------------------------------------------------

root@OpenWrt:~# wget -qO - http://onionwrt.us.to/install | sh
Installing tor (0.2.5.12-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/ramips/mt7620/packages/packages/tor_0.2.5.12-1_ramips_24kec.ipk.
Installing libevent2 (2.0.22-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/ramips/mt7620/packages/base/libevent2_2.0.22-1_ramips_24kec.ipk.
Installing libopenssl (1.0.2g-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/ramips/mt7620/packages/base/libopenssl_1.0.2g-1_ramips_24kec.ipk.
Installing zlib (1.2.8-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/ramips/mt7620/packages/base/zlib_1.2.8-1_ramips_24kec.ipk.
Installing libpthread (0.9.33.2-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/ramips/mt7620/packages/base/libpthread_0.9.33.2-1_ramips_24kec.ipk.
Installing librt (0.9.33.2-1) to root...
Downloading http://downloads.openwrt.org/chaos_calmer/15.05/ramips/mt7620/packages/base/librt_0.9.33.2-1_ramips_24kec.ipk.
Configuring libpthread.
Configuring libevent2.
Configuring librt.
Configuring zlib.
Configuring libopenssl.
Configuring tor.
```

```sh
$ ssh root@192.168.10.1
root@192.168.10.1's password: t0rmenta


BusyBox v1.23.2 (2015-07-25 03:03:02 CEST) built-in shell (ash)

  _______                     ________        __
 |       |.-----.-----.-----.|  |  |  |.----.|  |_
 |   -   ||  _  |  -__|     ||  |  |  ||   _||   _|
 |_______||   __|_____|__|__||________||__|  |____|
          |__| W I R E L E S S   F R E E D O M
 -----------------------------------------------------
 CHAOS CALMER (15.05, r46767)
 -----------------------------------------------------
  * 1 1/2 oz Gin            Shake with a glassful
  * 1/4 oz Triple Sec       of broken ice and pour
  * 3/4 oz Lime Juice       unstrained into a goblet.
  * 1 1/2 oz Orange Juice
  * 1 tsp. Grenadine Syrup
 -----------------------------------------------------
root@OpenWrt:~# ifconfig
br-lan    Link encap:Ethernet  HWaddr 20:28:18:XX:XX:XX
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fd3d:fc2c:67d1::1/60 Scope:Global
          inet6 addr: fe80::2228:18ff:fea1:d47e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2218856 (2.1 MiB)  TX bytes:30314062 (28.9 MiB)

eth0      Link encap:Ethernet  HWaddr 20:28:18:XX:XX:XX
          inet6 addr: fe80::2228:18ff:fea1:d47e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33217 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36908369 (35.1 MiB)  TX bytes:4827571 (4.6 MiB)
          Interrupt:5

eth0.1    Link encap:Ethernet  HWaddr 20:28:18:XX:XX:XX
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:32668 (31.9 KiB)

eth0.2    Link encap:Ethernet  HWaddr 20:28:18:XX:XX:XX
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2228:18ff:fea1:d47f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:36294465 (34.6 MiB)  TX bytes:4709824 (4.4 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:32670 (31.9 KiB)  TX bytes:32670 (31.9 KiB)

wlan0     Link encap:Ethernet  HWaddr 20:28:18:XX:XX:XX
          inet6 addr: fe80::2228:18ff:fea1:d47e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2553318 (2.4 MiB)  TX bytes:31425402 (29.9 MiB)

root@OpenWrt:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0.2
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0.2
192.168.1.1     *               255.255.255.255 UH    0      0        0 eth0.2
192.168.10.0    *               255.255.255.0   U     0      0        0 br-lan

root@OpenWrt:~# netstat -putan
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.10.1:9040       0.0.0.0:*               LISTEN      844/tor
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      858/uhttpd
tcp        0      0 0.0.0.0:53              0.0.0.0:*               LISTEN      1083/dnsmasq
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      802/dropbear
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      844/tor
tcp        0      0 192.168.1.101:32809     45.76.138.70:443        ESTABLISHED 844/tor
tcp        0    746 192.168.10.1:80         192.168.10.118:38217    ESTABLISHED 858/uhttpd
tcp        0      1 192.168.10.1:9040       192.168.10.198:38514    FIN_WAIT1   -
tcp        0      0 192.168.10.1:9040       192.168.10.198:38566    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.118:37705    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.118:47263    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.118:54239    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.198:48133    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.198:49601    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.198:41065    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.118:54242    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.198:48413    ESTABLISHED 844/tor
tcp        0    288 192.168.10.1:22         192.168.10.118:59063    ESTABLISHED 2209/dropbear
tcp        0      0 192.168.10.1:9040       192.168.10.118:43619    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.198:48954    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.198:48947    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:9040       192.168.10.118:43595    ESTABLISHED 844/tor
tcp        0      0 192.168.10.1:80         192.168.10.118:38264    TIME_WAIT   -
tcp        0      0 192.168.10.1:9040       192.168.10.198:38564    ESTABLISHED 844/tor
tcp        0      0 192.168.1.101:58004     148.251.190.229:9010    ESTABLISHED 844/tor
tcp        0      0 :::80                   :::*                    LISTEN      858/uhttpd
tcp        0      0 :::53                   :::*                    LISTEN      1083/dnsmasq
tcp        0      0 :::22                   :::*                    LISTEN      802/dropbear
udp        0      0 0.0.0.0:53              0.0.0.0:*                           1083/dnsmasq
udp        0      0 0.0.0.0:67              0.0.0.0:*                           1083/dnsmasq
udp        0      0 192.168.10.1:9053       0.0.0.0:*                           844/tor
udp        0      0 :::546                  :::*                                931/odhcp6c
udp        0      0 :::547                  :::*                                772/odhcpd
udp        0      0 :::53                   :::*                                1083/dnsmasq
root@OpenWrt:~#
```