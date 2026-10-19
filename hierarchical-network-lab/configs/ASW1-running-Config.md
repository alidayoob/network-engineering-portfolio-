```
ASW1#show runn
Building configuration...

Current configuration : 2971 bytes
!
version 15.0
service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname ASW1
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
username ALI secret 5 $1$mERr$AXoIEvWXwsqfAtEEIJlnJ.
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
 switchport voice vlan 100
 switchport port-security
 switchport port-security maximum 3
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
 switchport port-security mac-address sticky 0001.6419.033E
 switchport port-security mac-address sticky 0030.A33B.E80C
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/2
 switchport access vlan 10
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
 switchport port-security mac-address sticky 0001.645D.B240
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/3
 switchport access vlan 90
 switchport mode access
 switchport nonegotiate
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
 switchport port-security mac-address sticky 0001.645D.B240
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/4
!
interface FastEthernet0/5
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
 switchport trunk allowed vlan 10,90,100,900
 switchport mode trunk
 switchport nonegotiate
!
interface GigabitEthernet0/2
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,90,100,900
 switchport mode trunk
 switchport nonegotiate
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan900
 ip address 10.0.1.151 255.255.255.240
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
ntp server 10.0.2.5
!
end


ASW1#
```