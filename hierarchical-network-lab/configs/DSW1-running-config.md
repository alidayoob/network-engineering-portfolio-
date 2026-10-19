```
DSW1#show running-config 
Building configuration...

Current configuration : 5324 bytes
!
version 16.3.2
service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname DSW1
!
logging userinfo
!
no profinet
enable secret 5 $1$mERr$AXoIEvWXwsqfAtEEIJlnJ.
!
!
!
clock timezone EET 3
!
!
!
!
no ip cef
ip routing
!
no ipv6 cef
!
!
!
username ALI privilege 15 secret 5 $1$mERr$AXoIEvWXwsqfAtEEIJlnJ.
!
!
!
!
!
!
!
!
!
!
ip ssh version 2
no ip domain-lookup
ip domain-name lab.local
!
!
spanning-tree mode pvst
spanning-tree vlan 40-90 priority 4096
spanning-tree vlan 10-30,100 priority 8192
!
!
!
!
!
!
interface Loopback0
 ip address 5.5.5.5 255.255.255.255
!
interface Port-channel2
 no switchport
 ip address 10.0.2.41 255.255.255.252
!
interface GigabitEthernet1/0/1
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,90,100,900
 switchport mode trunk
 switchport nonegotiate
!
interface GigabitEthernet1/0/2
 switchport trunk native vlan 999
 switchport trunk allowed vlan 20,30,100,900
 switchport mode trunk
!
interface GigabitEthernet1/0/3
 switchport trunk native vlan 999
 switchport trunk allowed vlan 40,50,100,900
 switchport mode trunk
!
interface GigabitEthernet1/0/4
 switchport trunk native vlan 999
 switchport trunk allowed vlan 60,100,900
 switchport mode trunk
!
interface GigabitEthernet1/0/5
 switchport trunk native vlan 999
 switchport mode trunk
 switchport nonegotiate
!
interface GigabitEthernet1/0/6
 no switchport
 no ip address
 channel-group 2 mode desirable
 duplex auto
 speed auto
!
interface GigabitEthernet1/0/7
 no switchport
 no ip address
 channel-group 2 mode desirable
 duplex auto
 speed auto
!
interface GigabitEthernet1/0/8
!
interface GigabitEthernet1/0/9
 shutdown
!
interface GigabitEthernet1/0/10
 shutdown
!
interface GigabitEthernet1/0/11
!
interface GigabitEthernet1/0/12
!
interface GigabitEthernet1/0/13
!
interface GigabitEthernet1/0/14
!
interface GigabitEthernet1/0/15
!
interface GigabitEthernet1/0/16
!
interface GigabitEthernet1/0/17
!
interface GigabitEthernet1/0/18
!
interface GigabitEthernet1/0/19
!
interface GigabitEthernet1/0/20
!
interface GigabitEthernet1/0/21
!
interface GigabitEthernet1/0/22
!
interface GigabitEthernet1/0/23
!
interface GigabitEthernet1/0/24
!
interface GigabitEthernet1/1/1
 no switchport
 ip address 10.0.2.34 255.255.255.252
!
interface GigabitEthernet1/1/2
 no switchport
 ip address 10.0.2.26 255.255.255.252
!
interface GigabitEthernet1/1/3
!
interface GigabitEthernet1/1/4
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan10
 mac-address 0001.97c8.2501
 ip address 10.0.1.3 255.255.255.240
 ip helper-address 10.0.1.98
 standby 10 ip 10.0.1.1
 standby 10 priority 90
 standby 0 preempt
!
interface Vlan20
 mac-address 0001.97c8.2502
 ip address 10.0.1.19 255.255.255.240
 ip helper-address 10.0.1.98
 standby 0 preempt
 standby 20 ip 10.0.1.17
 standby 20 priority 90
!
interface Vlan30
 mac-address 0001.97c8.2503
 ip address 10.0.1.35 255.255.255.240
 ip helper-address 10.0.1.98
 standby 0 preempt
 standby 30 ip 10.0.1.33
 standby 30 priority 90
!
interface Vlan40
 mac-address 0001.97c8.2504
 ip address 10.0.1.51 255.255.255.240
 ip helper-address 10.0.1.98
 standby 40 ip 10.0.1.49
 standby 40 priority 110
 standby 40 preempt
!
interface Vlan50
 mac-address 0001.97c8.2505
 ip address 10.0.1.67 255.255.255.240
 ip helper-address 10.0.1.98
 standby 50 ip 10.0.1.65
 standby 50 priority 110
 standby 50 preempt
!
interface Vlan60
 mac-address 0001.97c8.2506
 ip address 10.0.1.83 255.255.255.240
 ip helper-address 10.0.1.98
 standby 60 ip 10.0.1.81
 standby 60 priority 110
 standby 60 preempt
!
interface Vlan70
 mac-address 0001.97c8.2507
 ip address 10.0.1.99 255.255.255.240
 ip helper-address 10.0.1.98
 standby 70 ip 10.0.1.97
 standby 70 priority 110
 standby 70 preempt
!
interface Vlan90
 mac-address 0001.97c8.2508
 ip address 10.0.1.131 255.255.255.240
 ip helper-address 10.0.1.98
 standby 90 ip 10.0.1.129
 standby 90 priority 110
 standby 90 preempt
!
interface Vlan100
 mac-address 0001.97c8.2509
 ip address 10.0.1.115 255.255.255.240
 ip helper-address 10.0.1.98
 standby 100 ip 10.0.1.113
 standby 100 priority 90
 standby 0 preempt
!
interface Vlan900
 mac-address 0001.97c8.250a
 ip address 10.0.1.147 255.255.255.240
 standby version 2
 standby 900 ip 10.0.1.145
 standby 900 priority 110
 standby 900 preempt
!
router ospf 1
 log-adjacency-changes
 passive-interface GigabitEthernet1/0/1
 passive-interface GigabitEthernet1/0/2
 passive-interface GigabitEthernet1/0/3
 passive-interface GigabitEthernet1/0/4
 passive-interface GigabitEthernet1/0/5
 network 10.0.2.40 0.0.0.3 area 0
 network 10.0.2.32 0.0.0.3 area 0
 network 10.0.2.24 0.0.0.3 area 0
 network 10.0.1.0 0.0.0.255 area 0
!
ip classless
!
ip flow-export version 9
!
!
ip access-list extended GUEST_ISOLATION
 permit udp any host 10.0.1.98 eq bootps
 permit udp any any eq bootps
 deny ip any 10.0.0.0 0.0.255.255
 permit ip any any
ip access-list extended MGMT_ACCESS_ONLY
 permit tcp 10.0.1.144 0.0.0.15 any eq 22
 deny tcp any any eq 22
 permit ip any any
!
banner motd ^C
Authorized access only. All activity is monitored and logged.
^C
!
!
!
!
logging trap debugging
logging 10.0.1.101
line con 0
 login local
!
line aux 0
!
line vty 0 4
 access-class MGMT_ACCESS_ONLY in
 login local
 transport input ssh
!
!
!
ntp server 10.0.2.5
!
end


DSW1#
```