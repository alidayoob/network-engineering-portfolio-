```
CSW1#show running-config 
Building configuration...

Current configuration : 2639 bytes
!
version 16.3.2
service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname CSW1
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
!
!
!
!
!
!
interface Loopback0
 ip address 3.3.3.3 255.255.255.255
!
interface Port-channel1
 no switchport
 ip address 10.0.2.21 255.255.255.252
!
interface GigabitEthernet1/0/1
 no switchport
 no ip address
 duplex auto
 speed auto
!
interface GigabitEthernet1/0/2
 no switchport
 no ip address
 duplex auto
 speed auto
!
interface GigabitEthernet1/0/3
 no switchport
 ip address 10.0.2.6 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet1/0/4
 no switchport
 ip address 10.0.2.14 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet1/0/5
!
interface GigabitEthernet1/0/6
!
interface GigabitEthernet1/0/7
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
 ip address 10.0.2.25 255.255.255.252
!
interface GigabitEthernet1/1/2
 no switchport
 ip address 10.0.2.29 255.255.255.252
!
interface GigabitEthernet1/1/3
!
interface GigabitEthernet1/1/4
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 log-adjacency-changes
 network 10.0.2.20 0.0.0.3 area 0
 network 10.0.2.4 0.0.0.3 area 0
 network 10.0.2.12 0.0.0.3 area 0
 network 10.0.2.24 0.0.0.3 area 0
 network 10.0.2.28 0.0.0.3 area 0
!
ip classless
!
ip flow-export version 9
!
!
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


CSW1# 
```