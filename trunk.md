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
### 🔍 Bước 4: Kiểm tra từ switch – qua CLI
```
show interfaces trunk
```
### 🔍 Bước 5: Kiểm tra mode của cổng cụ thể
```
show running-config interface <interface-id>

```




### CẤU HÌNH ĐÚNG
SW2
```
ena
conf t
int f0/6
switchport access vlan 50
switchport mode access
end
```
SW3
```
ena
conf t
int f0/3
switchport access vlan 10
switchport mode access
end
```
SW4
```
ena
conf t
int f0/3
switchport access vlan 20
switchport mode access
end
```
SW5
```
ena
conf t
int f0/3
switchport access vlan 30
switchport mode access
end
```
SW6
```
ena
conf t
int f0/3
switchport access vlan 40
switchport mode access
end
```
###   CẤU HÌNH SAI
SW2
```
ena
conf t
int f0/6
no switchport access vlan 50 
no switchport mode access
switchport trunk allowed vlan 50
switchport mode trunk
```
SW3
```
ena
conf t
int f0/3
no switchport access vlan 10 
no switchport mode access
switchport trunk allowed vlan 10
switchport mode trunk
```
SW4
```
ena
conf t
int f0/3
no switchport access vlan 20 
no switchport mode access
switchport trunk allowed vlan 20
switchport mode trunk
```
SW5
```
ena
conf t
int f0/3
no switchport access vlan 30 
no switchport mode access
switchport trunk allowed vlan 30
switchport mode trunk
```
SW6
```
ena
conf t
int f0/3
no switchport access vlan 40 
no switchport mode access
switchport trunk allowed vlan 40
switchport mode trunk
```
