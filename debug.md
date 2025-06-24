### 🧰 show config
```
show running-config
```
### 📋 Kiểm tra hoạt động ospf
```
show ip ospf neighbor
show ip protocols
show ip route
show ip route ospf
```
show ip ospf neighbor         → Xem OSPF đã hình thành láng giềng chưa
show ip route ospf            → Kiểm tra các route học được qua OSPF
show ip protocols             → Xác nhận cấu hình OSPF
show ip ospf interface brief  → Xem interface nào đang chạy OSPF
### 🛠️ Kiểm tra lại cấu hình Trunk trên switch
```
switchport mode trunk
```
### 🛠️ Kiểm tra lại cấu hình Trunk trên router 
```
show interfaces trunk
```
### 🧪 Mẹo kiểm tra nhanh tình trạng interface
```
show running-config interface Gi0/1
```
### Kiểm tra chi tiết 1 cổng
```
show interfaces Fa0/3 switchport
```
### 🔍 Phân tích kết quả
#### 🧪 Bước 1: Kiểm tra IP của PC1
#### 🧪 Bước 2: Kiểm tra switch nối với PC1
```
show vlan brief
```
#### 🧪 Bước 3: Kiểm tra trunk giữa SW3 và Router
```
show interfaces trunk
```
#### 🧪 Bước 4: Kiểm tra cấu hình Router
```
show int ip brief
```
⚠️ Quan trọng: Đừng quên chạy lệnh **no shutdown** 
#### 🧪 Bước 5: Kiểm tra trạng thái cổng và ARP
```
show ip interface brief
```
#### 🧪 Bước 6: Kiểm tra ARP và Ping
```
show ip arp
```
#### ✅ Kiểm tra Spanning Tree Protocol cho từng VLAN
```
show spanning-tree vlan 10
```
📋 Xác minh VLAN đó đang forward hay bị blocking bởi STP.
### 🧠 Lưu ý
