```
R2#show running-config 
Building configuration...

Current configuration : 2513 bytes
!
version 15.1
service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname R2
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
license udi pid CISCO2911/K9 sn FTX152417P3-
license boot module c2900 technology-package uck9
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
 ip address 2.2.2.2 255.255.255.255
!
interface GigabitEthernet0/0
 ip address 10.0.2.13 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 10.0.2.17 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 ip address 10.0.2.2 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/3/0
 ip address 1.1.1.2 255.255.255.248
!
interface Vlan1
 no ip address
 shutdown
!
router ospf 1
 log-adjacency-changes
 network 10.0.2.12 0.0.0.3 area 0
 network 10.0.2.16 0.0.0.3 area 0
 network 10.0.2.0 0.0.0.3 area 0
 network 1.1.1.0 0.0.0.3 area 0
 network 1.1.1.0 0.0.0.7 area 0
 network 2.2.2.2 0.0.0.0 area 0
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
telephony-service
 max-ephones 10
 max-dn 10
 ip source-address 2.2.2.2 port 2000
 auto assign 1 to 10
!
ephone-dn 1
 number 1001
!
ephone-dn 2
 number 1002
!
ephone-dn 3
 number 1003
!
ephone-dn 4
 number 1004
!
ephone-dn 5
 number 1005
!
ephone-dn 6
 number 1006
!
ephone 1
 device-security-mode none
 mac-address 0001.6419.033E
 type 7960
 button 1:1
!
ephone 2
 device-security-mode none
 mac-address 0040.0B89.A9CE
 type 7960
 button 1:2
!
ephone 3
 device-security-mode none
 mac-address 00E0.F785.DD61
 type 7960
 button 1:3
!
ephone 4
 device-security-mode none
 mac-address 00D0.FF3C.D567
 type 7960
 button 1:4
!
ephone 5
 device-security-mode none
 mac-address 00E0.F7EE.EBD1
 type 7960
 button 1:5
!
ephone 6
 device-security-mode none
 mac-address 00D0.5830.26A5
 type 7960
 button 1:6
!
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


R2# 
```