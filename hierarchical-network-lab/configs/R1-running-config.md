```
R1#show running-config 
Building configuration...

Current configuration : 1668 bytes
!
version 15.1
service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname R1
!
logging userinfo
!
!
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
no ipv6 cef
!
!
!
username ALI privilege 15 secret 5 $1$mERr$AXoIEvWXwsqfAtEEIJlnJ.
!
!
license udi pid CISCO2911/K9 sn FTX1524B298-
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
!
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
 ip address 10.255.255.1 255.255.255.255
!
interface GigabitEthernet0/0
 ip address 10.0.2.5 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 10.0.2.9 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 ip address 10.0.2.1 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/3/0
 ip address 8.8.8.10 255.255.255.252
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 log-adjacency-changes
 network 10.0.2.4 0.0.0.3 area 0
 network 10.0.2.8 0.0.0.3 area 0
 network 10.0.2.0 0.0.0.3 area 0
 network 8.8.8.8 0.0.0.3 area 0
 default-information originate
!
ip classless
ip route 0.0.0.0 0.0.0.0 GigabitEthernet0/3/0 8.8.8.9 
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
Authorized access only. All activity is monitored and logged.^C
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
ntp master 3
ntp update-calendar
!
end


R1# 
```