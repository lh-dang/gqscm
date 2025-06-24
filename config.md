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
