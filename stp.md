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
























```
