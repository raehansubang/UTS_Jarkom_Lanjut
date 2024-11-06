# Konfigurasi Interface
interface Eth1
 ip address 192.168.20.1 255.255.255.0
 no shutdown

interface Tunnel0
 ip address 20.20.20.1 255.255.255.252
 tunnel source 192.168.20.1
 tunnel destination 192.168.20.2
 tunnel mode ipip

interface Tunnel1
 ip address 20.20.20.5 255.255.255.252
 tunnel source 192.168.20.1
 tunnel destination 192.168.20.3
 tunnel mode ipip

# Routing
ip route 192.168.6.0 255.255.255.0 20.20.20.2
ip route 192.168.6.0 255.255.255.0 20.20.20.6

# Konfigurasi Switch di R1 KJ
config terminal
interface range fa0/1 - 24
 switchport mode access
 switchport access vlan 1

vlan 1
 name Lab_Praktikum_KJ