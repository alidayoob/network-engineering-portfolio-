```
ASW2#show running-config 
Building configuration...

Current configuration : 3331 bytes
!
version 15.0
service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname ASW2
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
 switchport access vlan 20
 switchport mode access
 switchport nonegotiate
 switchport voice vlan 100
 switchport port-security
 switchport port-security maximum 3
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
 switchport port-security mac-address sticky 0002.17D3.A53A
 switchport port-security mac-address sticky 0040.0B89.A9CE
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/2
 switchport access vlan 30
 switchport mode access
 switchport nonegotiate
 switchport voice vlan 100
 switchport port-security
 switchport port-security maximum 3
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
 switchport port-security mac-address sticky 00E0.B08C.B058
 switchport port-security mac-address sticky 00E0.F785.DD61
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/3
 switchport access vlan 30
 switchport mode access
 switchport nonegotiate
 switchport port-security
 switchport port-security mac-address sticky 
 switchport port-security violation restrict 
 switchport port-security mac-address sticky 000A.4121.5973
 spanning-tree portfast
 spanning-tree bpduguard enable
!
interface FastEthernet0/4
 shutdown
!
interface FastEthernet0/5
 shutdown
!
interface FastEthernet0/6
 shutdown
!
interface FastEthernet0/7
 shutdown
!
interface FastEthernet0/8
 shutdown
!
interface FastEthernet0/9
 shutdown
!
interface FastEthernet0/10
 shutdown
!
interface FastEthernet0/11
 shutdown
!
interface FastEthernet0/12
 shutdown
!
interface FastEthernet0/13
 shutdown
!
interface FastEthernet0/14
 shutdown
!
interface FastEthernet0/15
 shutdown
!
interface FastEthernet0/16
 shutdown
!
interface FastEthernet0/17
 shutdown
!
interface FastEthernet0/18
 shutdown
!
interface FastEthernet0/19
 shutdown
!
interface FastEthernet0/20
 shutdown
!
interface FastEthernet0/21
 shutdown
!
interface FastEthernet0/22
 shutdown
!
interface FastEthernet0/23
 shutdown
!
interface FastEthernet0/24
 shutdown
!
interface GigabitEthernet0/1
 switchport trunk native vlan 999
 switchport trunk allowed vlan 20,30,100,900
 switchport mode trunk
 switchport nonegotiate
!
interface GigabitEthernet0/2
 switchport trunk native vlan 999
 switchport trunk allowed vlan 20,30,100,900
 switchport mode trunk
 switchport nonegotiate
!
interface Vlan1
 no ip address
 shutdown
!
interface Vlan900
 ip address 10.0.1.152 255.255.255.240
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


ASW2#
```