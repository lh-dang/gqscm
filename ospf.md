### 🔎 Bước 1: Ping kiểm tra kết nối đầu cuối
###### ➤ Kết quả:
- Nếu ping thành công → Không lỗi OSPF (có thể test thêm).
- Nếu ping thất bại → Đi lần từng bước.
### 🛤️ Bước 2: Kiểm tra Default Gateway
### 🧱 Bước 3: Kiểm tra Router kết nối với VLAN<...>
Kiểm tra cổng có mở không
```
show ip interface brief
```
### 🌐 Bước 4: Kiểm tra OSPF trên R1
```
show ip ospf neighbor
! show ip protocol
```
### 🧭 Bước 5: Kiểm tra OSPF đã quảng bá mạng chưa
```
show running-config | section ospf
```
### 🔁 Bước 6: Kiểm tra trên R<0> và R<2>
```
show ip route ospf
show ip ospf neighbor
```

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
