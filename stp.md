***Базовая настройка коммутаторов***

```
Switch#conf t
Switch(config)#hostname S2
S2(config)#
S2(config)#no ip domain-lookup
S2#sh run | i domain-lookup
no ip domain-lookup

S2(config)#enable secret class
S2(config)#line co
S2(config)#line console 0
S2(config-line)#pas
S2(config-line)#password cisco
S2(config-line)#login
S2(config-line)#exit
S2(config)#line vty 0 4
S2(config-line)#password cisco
S2(config-line)#login
S2(config-line)#exit
S2(config)#servuc
S2(config)#servic
S2(config)#service pass
S2(config)#service password-encryption 
S2(config)#ba
S2(config)#banner motd $ Autorized Access Only! $

S2(config)#vlan 1
S2#
S2#conf t
S2(config)#int vlan 1
S2(config-if)#ip add 192.168.1.2 255.255.255.0
S2(config-if)#no shut

S2#copy running-config startup-config
Destination filename [startup-config]? 
Building configuration...
Compressed configuration from 1034 bytes to 736 bytes[OK]



Switch>
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#hostnam
Switch(config)#hostname S3
S3(config)#enabl
S3(config)#enable secret class
S3(config)#line console 0
S3(config-line)#password cisco
S3(config-line)#login
S3(config-line)#exit
S3(config)#line vty 0 4
S3(config-line)#password cisco
S3(config-line)#login
S3(config-line)#exit
S3(config)#service pass
S3(config)#service password-encryption 
S3(config)#bann
S3(config)#banner motd $ Autorized Access Only! $
S3(config)#
S3#
S3#
S3#
S3#
*Sep 18 14:10:17.219: %SYS-5-CONFIG_I: Configured from console by console
S3#cop 
S3#copy ru
S3#copy running-config st
S3#copy running-config startup-config
Destination filename [startup-config]? 
Building configuration...
Compressed configuration from 958 bytes to 686 bytes[OK]





















```
