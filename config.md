## config ip address
### R0
```
ena
conf t
hostname R0 
int g0/0
ip address 192.168.1.1 255.255.255.0
no shut
int g0/1
ip address 192.168.2.1 255.255.255.0
no shut
int g0/2
ip address 192.168.3.1 255.255.255.0
no shut
end
show ip int brief
```
### R1
```
ena
conf t
hostname R1
int g0/0
ip address 192.168.1.2 255.255.255.0
no shut
end
show ip int brief
```
### R2
```
ena
conf t
hostname R2
int g0/0
ip address 192.168.2.2 255.255.255.0
no shut
end
show ip int brief
```
### R3
```
ena
conf t
hostname R3
int g0/0
ip address 192.168.3.2 255.255.255.0
no shut
end
show ip int brief
```
## config ospf
### R0
```
ena
conf t
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
network 192.168.2.0 0.0.0.255 area 0
network 192.168.3.0 0.0.0.255 area 0
end
```

### R1
```
ena
conf t
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
end
```

### R2
```
ena
conf t
router ospf 1
network 192.168.2.0 0.0.0.255 area 0
end
```

### R3
```
ena
conf t
router ospf 1
network 192.168.3.0 0.0.0.255 area 0
end
```
### check ospf config
```
show ip ospf neighbor         → Xem OSPF đã hình thành láng giềng chưa
show ip route ospf            → Kiểm tra các route học được qua OSPF
show ip protocols             → Xác nhận cấu hình OSPF
show ip ospf interface brief  → Xem interface nào đang chạy OSPF
```
## config vlan
R1
```
ena
conf t
int g0/1
no shut
exit
int g0/1.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit
int g0/1.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
end
```
R2
```
ena
conf t
int g0/1
no shut
exit
int g0/1.30
encapsulation dot1Q 30
ip address 192.168.30.1 255.255.255.0
exit
int g0/1.40
encapsulation dot1Q 40
ip address 192.168.40.1 255.255.255.0
exit
int g0/1.50
encapsulation dot1Q 50
ip address 192.168.50.1 255.255.255.0
end
```
R2
```
ena
conf t
int g0/1
no shut
int g0/2
no shut
exit
int g0/1.60
encapsulation dot1Q 60
ip address 192.168.60.1 255.255.255.0
exit
int g0/2.70
encapsulation dot1Q 70
ip address 192.168.70.1 255.255.255.0
end
```
SW1
```
ena
conf t
hostname SW1
vlan 10
vlan 20
exit 
interface fa0/1
switchport mode trunk
switchport trunk allowed vlan 10,20
no shutdown
interface fa0/2
switchport mode trunk
switchport trunk allowed vlan 10
no shutdown
interface fa0/3
switchport mode trunk
switchport trunk allowed vlan 20
no shutdown
end
```
SW3
```
ena
conf t
hostname SW3
vlan 10

! Cổng nối đến Switch1
int fa0/1
switchport mode trunk
switchport trunk allowed vlan 10
no shutdown

! Cổng nối đến PC1
int fa0/3
switchport mode access
switchport access vlan 10
no shutdown

! Cổng nối đến PC2
int fa0/4
switchport mode access
switchport access vlan 10
no shutdown
end
```
SW4
```
ena
conf t
hostname SW4
vlan 20

! Cổng nối đến Switch1
int fa0/1
switchport mode trunk
switchport trunk allowed vlan 20
no shutdown

! Cổng nối đến PC1
int fa0/3
switchport mode access
switchport access vlan 20
no shutdown

! Cổng nối đến PC2
int fa0/4
switchport mode access
switchport access vlan 20
no shutdown
end
```
SW2
```
ena
conf t
hostname SW2
vlan 30
vlan 40
vlan 50
exit 
interface fa0/1
switchport mode trunk
switchport trunk allowed vlan 30,40,50
no shutdown
interface fa0/4
switchport mode trunk
switchport trunk allowed vlan 30
no shutdown
interface fa0/5
switchport mode trunk
switchport trunk allowed vlan 40
no shutdown
interface fa0/6
switchport mode trunk
switchport trunk allowed vlan 50
no shutdown
end
```
SW5
```
ena
conf t
hostname SW5
vlan 30

! Cổng nối đến Switch2
int fa0/2
switchport mode trunk
switchport trunk allowed vlan 30
no shutdown

! Cổng nối đến PC1
int fa0/3
switchport mode access
switchport access vlan 30
no shutdown

! Cổng nối đến PC2
int fa0/4
switchport mode access
switchport access vlan 30
no shutdown
end
```
SW6
```
ena
conf t
hostname SW6
vlan 40

! Cổng nối đến Switch2
int fa0/2
switchport mode trunk
switchport trunk allowed vlan 40
no shutdown

! Cổng nối đến PC1
int fa0/3
switchport mode access
switchport access vlan 40
no shutdown

! Cổng nối đến PC2
int fa0/4
switchport mode access
switchport access vlan 40
no shutdown
end
```
SW7
```
ena
conf t
hostname SW7
vlan 60

! Cổng nối đến Switch2
int fa0/1
switchport mode trunk
switchport trunk allowed vlan 60
no shutdown

! Cổng nối đến server
int fa0/2
switchport mode access
switchport access vlan 60
no shutdown
end
```
SW8
```
ena
conf t
hostname SW8
vlan 70

! Cổng nối đến Switch2
int fa0/1
switchport mode trunk
switchport trunk allowed vlan 70
no shutdown

! Cổng nối đến server
int fa0/2
switchport mode access
switchport access vlan 70
no shutdown
end
```
## Cấu hình NAT Overload (PAT)
### R1
```
ena
conf t

interface G0/1.10
ip nat inside
interface G0/1.20
ip nat inside

interface G0/0
 ip nat outside
exit

access-list 1 permit 192.168.10.0 0.0.0.255
access-list 1 permit 192.168.20.0 0.0.0.255

ip nat inside source list 1 interface G0/0 overload
ip route 0.0.0.0 0.0.0.0 192.168.1.1
end
```
##   NOTE
### Vlan
chỉ mặc định cho vlan 10, những vlan còn lại cấm
```
switchport trunk allowed vlan 10
```
