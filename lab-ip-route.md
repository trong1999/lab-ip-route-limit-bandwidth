# Bài toán đặt ra như sau
<img src="https://i.imgur.com/PoT02k9.jpg">
- Trên **router** ta cấu hình hai card mạng qua file 
  + **vim /etc/sysconfig/network-scripts/ifcfg-ens36** => cho card ens36
    + <img src="https://i.imgur.com/79d2TCr.png">
  + **vim /etc/sysconfig/network-scripts/ifcfg-ens37** => cho card ens37
    + <img src="https://i.imgur.com/uJUipWt.png">
- Trên **server A** ta cấu hình như sau
  + **vim /etc/sysconfig/network-scripts/ifcfg-ens36**
    + <img src="https://i.imgur.com/Wf9MsMi.png">
- Trên **server B** ta cấu hình như sau
  + **vim /etc/sysconfig/network-scripts/ifcfg-ens36**
    + <img src="https://i.imgur.com/7hZXQlZ.png">
- Sau đó ta sẽ đứng trên router để định tuyến route cho bài toán:

  + Trên server A : **ip route add 192.168.4.3 via 192.168.3.1**
  + Add route cả dải : **ip route add 192.168.4.0/24 via 192.168.3.1**
  + Show bảng định tuyến : **ip r**
  + <img src="https://i.imgur.com/F4JSOn2.png">
  + Trên server B : **ip route add 192.168.3.2 via 192.168.4.2**
  + Add route cả dải : **ip route add 192.168.3.0/24 via 192.168.4.2**
  + <img src="https://i.imgur.com/Ezo9ZYJ.png">
- Sau đó là sẽ phải forward bằng câu lệnh sau:

  + **echo 1 > /proc/sys/net/ipv4/ip_forward**
  + Show bảng định tuyến : **ip r**
  + <img src="https://i.imgur.com/esITOM3.png">
- Kết quả là ta sẽ ping được hai dải mạng
  + Trên **server A** <img src="https://i.imgur.com/tDWdZ6k.png">
  + Trên **server B** <img src="https://i.imgur.com/uDfFevV.png">
  
# Như vậy đã xong
