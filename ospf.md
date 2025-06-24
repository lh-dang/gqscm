
### CẤU HÌNH LẠI
R1
```
ena
conf t
router ospf 1
network 192.168.10.0 0.0.0.255 area 0
end
```
R2
```
ena
conf t
router ospf 1
network 192.168.30.0 0.0.0.255 area 0
end
```
### CẤU HÌNH SAI
R1
```
ena
conf t
router ospf 1
no network 192.168.10.0 0.0.0.255 area 0
end
```
R2
```
ena
conf t
router ospf 1
no network 192.168.30.0 0.0.0.255 area 0
end
```
