```
ASW5#show running-config 
Building configuration...

Current configuration : 2838 bytes
!
version 15.0
service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname ASW5
!
enable secret 5 $1$mERr$AXoIEvWXwsqfAtEEIJlnJ.
!
!
!
clock timezone EET 3
!
ip ssh version 2
no ip domain-lookup
ip domain-name lab.local
!
username ALi secret 5 $1$mERr$AXoIEvWXwsqfAtEEIJlnJ.
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
 switchport access vlan 70
 switchport mode access
 switchport nonegotiate
 switchport port-security mac-address sticky 
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/2
 switchport access vlan 70
 switchport mode access
 switchport nonegotiate
 switchport port-security mac-address sticky 
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/3
 switchport access vlan 900
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security mac-address sticky 00E0.F769.7696
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/4
 switchport access vlan 900
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security mac-address sticky 0001.97DB.B138
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/5
 switchport mode access
 spanning-tree portfast
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
 switchport trunk native vlan 999
 switchport trunk allowed vlan 70,900
 switchport mode trunk
!
interface GigabitEthernet0/2
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,20,30,40,50,60,70,100,900
 switchport mode trunk
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan900
 ip address 10.0.1.155 255.255.255.240
!
ip default-gateway 10.0.1.145
!
banner motd ^C
Authorized access only. All activity is monitored and logged.
^C
logging trap debugging
logging 10.0.1.101
!
!
!
ip access-list extended MGMT_ACCESS_ONLY
 permit tcp 10.0.1.144 0.0.0.15 any eq 22
 deny tcp any any eq 22
 permit ip any any
line con 0
 login local
!
line vty 0 4
 access-class MGMT_ACCESS_ONLY in
 login local
 transport input ssh
line vty 5 15
 login
!
!
!
ntp server 10.0.2.17
!
end


ASW5# 
```