# Đặt vấn đề 
- Nếu việc upload file lên server, mail server,... nó chiếm rất nhiều bandwidth của hệ thống, điều làm ảnh hưởng rất nhiều đến
các hoạt động khác của hệ thống.
- Yêu cầu là nếu upload một file này từ server này sang server kia, chỉ cho tốc độ là 1.12MB/s
- Để giải quyết vấn đề này, tôi sẽ giới thiệu đến các bạn một tool được sử dụng khá phổ biến hiện nay đó là 
Traffic Controller (tc)
# Giải quyết vấn đề
- Sẽ tạo ra một script
  + **vim /etc/init.d/shaping**
- Nội dung file:
  + <img src="https://i.imgur.com/a2fDhc4.png">
  + <img src="https://i.imgur.com/HW67Mz5.png">
  + Trong file này cần chú ý đến câu lệnh giới hạn, ở mục limit download và limit upload đặt 10mbit (vì 10mbit : 8=1.12MB)
- Sau đó save và exit
- Phân quyền file vừa tạo
  + **chmod +x /etc/init.d/shaping**
- Cuối cùng là restart và start file
  + **/etc/init.d/shaping start**
- Thử copy xem thế nào
  + <img src="https://i.imgur.com/QFimrBs.png">
  
# Như thế là ok
