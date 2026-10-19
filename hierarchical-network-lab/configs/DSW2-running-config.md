```
DSW2#show running-config 
Building configuration...

Current configuration : 5347 bytes
!
version 16.3.2
service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
no service dhcp
!
hostname DSW2
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
spanning-tree vlan 10-30,100 priority 4096
spanning-tree vlan 40-90 priority 8192
!
!
!
!
!
!
interface Loopback0
 ip address 6.6.6.6 255.255.255.255
!
interface Port-channel2
 no switchport
 ip address 10.0.2.42 255.255.255.252
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
 switchport nonegotiate
!
interface GigabitEthernet1/0/3
 switchport trunk native vlan 999
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
!
interface GigabitEthernet1/0/10
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
 ip address 10.0.2.30 255.255.255.252
!
interface GigabitEthernet1/1/2
 no switchport
 ip address 10.0.2.38 255.255.255.252
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
 mac-address 0001.9609.8e01
 ip address 10.0.1.4 255.255.255.240
 ip helper-address 10.0.1.98
 standby 10 ip 10.0.1.1
 standby 10 priority 110
 standby 10 preempt
!
interface Vlan20
 mac-address 0001.9609.8e02
 ip address 10.0.1.20 255.255.255.240
 ip helper-address 10.0.1.98
 standby 20 ip 10.0.1.17
 standby 20 priority 110
 standby 20 preempt
!
interface Vlan30
 mac-address 0001.9609.8e03
 ip address 10.0.1.36 255.255.255.240
 ip helper-address 10.0.1.98
 standby 30 ip 10.0.1.33
 standby 30 priority 110
 standby 30 preempt
!
interface Vlan40
 mac-address 0001.9609.8e04
 ip address 10.0.1.52 255.255.255.240
 ip helper-address 10.0.1.98
 standby 40 ip 10.0.1.49
 standby 40 priority 90
!
interface Vlan50
 mac-address 0001.9609.8e05
 ip address 10.0.1.68 255.255.255.240
 ip helper-address 10.0.1.98
 standby 50 ip 10.0.1.65
!
interface Vlan60
 mac-address 0001.9609.8e06
 ip address 10.0.1.84 255.255.255.240
 ip helper-address 10.0.1.98
 standby 60 ip 10.0.1.81
!
interface Vlan70
 mac-address 0001.9609.8e07
 ip address 10.0.1.100 255.255.255.240
 ip helper-address 10.0.1.98
 standby 70 ip 10.0.1.97
 standby 70 priority 90
!
interface Vlan90
 mac-address 0001.9609.8e08
 ip address 10.0.1.132 255.255.255.240
 standby 90 ip 10.0.1.129
 standby 90 priority 90
!
interface Vlan100
 mac-address 0001.9609.8e09
 ip address 10.0.1.116 255.255.255.240
 ip helper-address 10.0.1.98
 standby 100 ip 10.0.1.113
 standby 100 priority 110
 standby 100 preempt
!
interface Vlan900
 mac-address 0001.9609.8e0a
 ip address 10.0.1.148 255.255.255.240
 standby version 2
 standby 900 ip 10.0.1.145
 standby 900 priority 90
!
router ospf 1
 log-adjacency-changes
 passive-interface GigabitEthernet1/0/1
 passive-interface GigabitEthernet1/0/2
 passive-interface GigabitEthernet1/0/3
 passive-interface GigabitEthernet1/0/4
 passive-interface GigabitEthernet1/0/5
 passive-interface Vlan10
 passive-interface Vlan20
 passive-interface Vlan30
 passive-interface Vlan40
 passive-interface Vlan50
 passive-interface Vlan60
 passive-interface Vlan70
 passive-interface Vlan90
 passive-interface Vlan100
 network 10.0.2.40 0.0.0.3 area 0
 network 10.0.2.28 0.0.0.3 area 0
 network 10.0.2.36 0.0.0.3 area 0
 network 10.0.1.0 0.0.0.255 area 0
!
ip classless
!
ip flow-export version 9
!
!
ip access-list extended GUEST_ISOLATION
 permit udp any host 10.0.1.98 eq bootps
 permit udp any any eq bootpc
 deny ip any 10.0.1.0 0.0.0.255
 deny ip any 10.0.2.0 0.0.0.255
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
ntp server 10.0.2.17
!
end


DSW2#
```