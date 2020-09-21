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




S3#sh ip interface brief 
Interface              IP-Address      OK? Method Status                Protocol
Ethernet0/0            unassigned      YES unset  up                    up      
Ethernet0/1            unassigned      YES unset  up                    up      
Ethernet0/2            unassigned      YES unset  up                    up      
Ethernet0/3            unassigned      YES unset  up                    up      
Vlan1                  192.168.1.3     YES manual up                    up  


S1#sh ip interface brief 
Interface              IP-Address      OK? Method Status                Protocol
Ethernet0/0            unassigned      YES unset  up                    up      
Ethernet0/1            unassigned      YES unset  up                    up      
Ethernet0/2            unassigned      YES unset  up                    up      
Ethernet0/3            unassigned      YES unset  up                    up      
Vlan1                  192.168.1.1     YES NVRAM  up                    up  


S2#sh ip interface brief 
Interface              IP-Address      OK? Method Status                Protocol
Ethernet0/0            unassigned      YES unset  up                    up      
Ethernet0/1            unassigned      YES unset  up                    up      
Ethernet0/2            unassigned      YES unset  up                    up      
Ethernet0/3            unassigned      YES unset  up                    up      
Vlan1                  192.168.1.2     YES manual up                    up 

Шаг 4

S1#ping 192.168.1.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.1.2, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 1/1/2 ms
S1#ping 192.168.1.2
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.1.2, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms
S1#ping 192.168.1.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.1.3, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 1/1/1 ms
S1#ping 192.168.1.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.1.3, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms


S2#ping 192.168.1.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.1.3, timeout is 2 seconds:
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 1/1/2 ms
S2#ping 192.168.1.3
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 192.168.1.3, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1/1/1 ms

Часть 2

Шаг 1

S1(config)#interface range e0/0-3
S1(config-if-range)#shut

S2(config)#in range e0/0-3
S2(config-if-range)#shut

S3(config)#int range e0/0-3
S3(config-if-range)#shut

Шаг 2

S1(config)#int range e0/0-3                       
S1(config-if-range)#switchport trunk encapsulation dot1q   
S1(config-if-range)#switchport trunk allowed vlan 1     
S1(config-if-range)#

S2#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S2(config)#int range e0/0-3                       
S2(config-if-range)#switchport trunk encapsulation dot1q   
S2(config-if-range)#switchport trunk allowed vlan 1     
S2(config-if-range)#

S3#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S3(config)#int range e0/0-3                       
S3(config-if-range)#switchport trunk encapsulation dot1q   
S3(config-if-range)#switchport trunk allowed vlan 1     
S3(config-if-range)#

Шаг 3

S1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S1(config)#in
S1(config)#interface e0/0
S1(config-if)#no shut
S1(config-if)#
*Sep 18 15:29:30.668: %LINK-3-UPDOWN: Interface Ethernet0/0, changed state to up
*Sep 18 15:29:31.672: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/0, changed state to up
S1(config-if)#int e0/2
S1(config-if)#no shut
S1(config-if)#
*Sep 18 15:29:46.143: %LINK-3-UPDOWN: Interface Ethernet0/2, changed state to up
*Sep 18 15:29:47.147: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/2, changed state to up
S1(config-if)#

S2(config)#int e0/0
S2(config-if)#no shut
S2(config-if)#int 
*Sep 18 15:30:44.637: %LINK-3-UPDOWN: Interface Ethernet0/0, changed state to up
*Sep 18 15:30:45.641: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/0, changed state to up
S2(config-if)#int e0/2
S2(config-if)#no shut
S2(config-if)#
*Sep 18 15:30:58.294: %LINK-3-UPDOWN: Interface Ethernet0/2, changed state to up
*Sep 18 15:30:59.299: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/2, changed state to up
S2(config-if)#


S3#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S3(config)#int e0/0
S3(config-if)#no shut
S3(config-if)#int e0/0
*Sep 18 15:31:29.631: %LINK-3-UPDOWN: Interface Ethernet0/0, changed state to up
*Sep 18 15:31:30.637: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/0, changed state to up
S3(config-if)#int e0/2
S3(config-if)#no shut
S3(config-if)#
*Sep 18 15:31:39.331: %LINK-3-UPDOWN: Interface Ethernet0/2, changed state to up
*Sep 18 15:31:40.336: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/2, changed state to up
S3(config-if)#


Шаг 4

S1#sh spanning-tree 

VLAN0001
  Spanning tree enabled protocol ieee
  Root ID    Priority    32769
             Address     aabb.cc00.1000
             This bridge is the root                     
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec

  Bridge ID  Priority    32769  (priority 32768 sys-id-ext 1)
             Address     aabb.cc00.1000
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec
             Aging Time  300 sec

Interface           Role Sts Cost      Prio.Nbr Type
------------------- ---- --- --------- -------- --------------------------------
Et0/0               Desg FWD 100       128.1    P2p 
Et0/2               Desg FWD 100       128.3    P2p 


S1#

S2#sh spanning-tree 

VLAN0001
  Spanning tree enabled protocol ieee
  Root ID    Priority    32769
             Address     aabb.cc00.1000
             Cost        100
             Port        1 (Ethernet0/0)
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec

  Bridge ID  Priority    32769  (priority 32768 sys-id-ext 1)
             Address     aabb.cc00.2000
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec
             Aging Time  300 sec

Interface           Role Sts Cost      Prio.Nbr Type
------------------- ---- --- --------- -------- --------------------------------
Et0/0               Root FWD 100       128.1    P2p 
Et0/2               Desg FWD 100       128.3    P2p


S3#sh spanning-tree 

VLAN0001
  Spanning tree enabled protocol ieee
  Root ID    Priority    32769
             Address     aabb.cc00.1000
             Cost        100
             Port        3 (Ethernet0/2)
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec

  Bridge ID  Priority    32769  (priority 32768 sys-id-ext 1)
             Address     aabb.cc00.3000
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec
             Aging Time  300 sec

Interface           Role Sts Cost      Prio.Nbr Type
------------------- ---- --- --------- -------- --------------------------------
Et0/0               Altn BLK 100       128.1    P2p 
Et0/2               Root FWD 100       128.3    P2p

```


***С учетом выходных данных, поступающих с коммутаторов, ответьте на следующие вопросы***

*Какой коммутатор является корневым мостом?* **Коммутатор S1**

*Почему этот коммутатор был выбран протоколом spanning-tree в качестве корневого моста?*

**Приоритет идентификатора моста рассчитывается путем сложения значений приоритета и расширенного идентификатора системы. Расширенным идентификатором системы всегда является номер сети VLAN. В нашем примере все три коммутатора имеют равные значения приоритета идентификатора моста (32769 = 32768 + 1, где приоритет по умолчанию = 32768, номер сети VLAN = 1); следовательно, коммутатор с самым низким значением MAC-адреса (aabb.cc00.1000) становится корневым мостом (в нашем случае — S1).**

```
 Root ID    Priority    32769
 Address     aabb.cc00.1000
 This bridge is the root
 ```

Какие порты на коммутаторе являются корневыми портами?

**Root Port — корневой порт коммутатора. При выборе корневого коммутатора также и определяется корневой порт. Это порт через который подключен корневой коммутатор. Например в нашей топологии порты Et0/0 на S2 и Et0/2 на S3 являются корневыми портами.**

Какие порты на коммутаторе являются назначенными портами? 

**На коммутаторе S1 назначенными (designated) являются оба порта - Et0/0 и Et0/2, на S2 - Et0/2 назначенный (designated) порт.**

Какой порт отображается в качестве альтернативного и в настоящее время заблокирован?

**Порт Et0/0 на коммутаторе S3**

Почему протокол spanning-tree выбрал этот порт в качестве невыделенного (заблокированного) порта?

**Чтобы понять, какой порт лучше использовать, каждый некорневой коммутатор (S2;S3) определяет стоимость маршрута от каждого своего порта до корневого коммутатора (S1). Эта стоимость определяется суммой стоимостей всех линков, которые нужно пройти кадру, чтобы дойти до корневого коммутатора. В нашей топологии стоимость маршрута от порта Et0/0 коммутатора S3 больше чему от порта Et0/2. Поэтому порт Et0/0 выбран в качестве альтернативного и статус у него - "заблокирован".**

***Наблюдение за процессом выбора протоколом STP порта, исходя из стоимости портов***

```
S2#sh spanning-tree 

VLAN0001
  Spanning tree enabled protocol ieee
  Root ID    Priority    32769
             Address     aabb.cc00.1000
             Cost        100
             Port        1 (Ethernet0/0)
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec

  Bridge ID  Priority    32769  (priority 32768 sys-id-ext 1)
             Address     aabb.cc00.2000
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec
             Aging Time  300 sec

Interface           Role Sts Cost      Prio.Nbr Type
------------------- ---- --- --------- -------- --------------------------------
Et0/0               Root FWD 100       128.1    P2p 
Et0/2               Desg FWD 100       128.3    P2p

S3#sh spanning-tree 

VLAN0001
  Spanning tree enabled protocol ieee
  Root ID    Priority    32769
             Address     aabb.cc00.1000
             Cost        100
             Port        3 (Ethernet0/2)
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec

  Bridge ID  Priority    32769  (priority 32768 sys-id-ext 1)
             Address     aabb.cc00.3000
             Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec
             Aging Time  300 sec

Interface           Role Sts Cost      Prio.Nbr Type
------------------- ---- --- --------- -------- --------------------------------
Et0/0               Altn BLK 100       128.1    P2p 
Et0/2               Root FWD 100       128.3    P2p 

```

















































