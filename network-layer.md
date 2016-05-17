<a name="top"></a>
##Contents:
===
## I.Các mô hình dịch vụ của tầng mạng
<a name=""></a>

Tầng mạng có nhiệm vụ chuyển các gói tin(**segment**) của tầng giao vận từ máy tính này đến máy tính khác qua các router.
*Vai trò* đơn giản của tầng mạng chỉ là chuyển gói tin từ máy tính gửi đến máy tính nhận.Vì vậy tầng mạng có 3 *chức năng* quan trọng sau đây:
<ul>
<li>Định tuyến: Xác định đường đi của gói từ nguồn đến đích **routing algorithms**
</li>
<li>Chuyển tiếp(forwarding): chuyển gói tin từ  cổng vào sang cổng ra thích hợp ở router</li>
<li>Thiết lập đường truyền: kiểu bắt tay giữa các router</li>
</ul>
###1.Mô hình dịch vụ mạng

####1.1 Chuyển mạch ảo(Virtual circuit-VC)
Cung cấp dịch vụ kết nối
Có 3 giai đoạn trong chuyển mạch ảo:
<ul>
<li>Thiết lập mạch ảo: phía gửi thông báo địa chỉ nhận  với tầng mạng yêu cầu thiết lập VC.Tầng mạng xác định tuyến đường giữa bên gửi và bên nhận
	Giai đoạn này yêu cầu việc cập nhật bảng định tuyến và dự trữ tài nguyên trong mỗi lần thiết bị chuyển mạch
</li>
<li>Truyền dữ liệu: Sau khi thiết lập.Dữ liệu được truyền trong VC</li>
<li>Giải phòng mạch ảo: bắt đầu từ phía gửi(hoặc nhận)báo cho tầng mạng yêu cầu đóng VC</li>
</ul>

- Thông điệp trao đổi giữa các thiết bị đầu cuối yêu cần khởi tạo hay kết thúc  mạch ảo hay thông điệp trao đổi giữa các thiết bị chuyển mạch yêu cầu thiết lập  VC đgl **Thông điệp báo hiệu**
- Giao thức để trao đổi những thông điệp này là **giao thức báo hiệu**
<img src="http://i.imgur.com/pYee7Jv.png">
Mô hình dịch vụ chuyển mạch ảo

####1.2 Chuyển mạch gói
Phi kết nối

<ul>
<li> Không thiết lập kết nối ở tầng mạng</li>
<li>Router không lưu trạng thái kết nối</li>
<li>Do bảng định tuyến được cập nhật liên tục nên Các gói cung nguồn-đích có thể đi theo các đường khác nhau</li>
</ul>
<img src="http://i.imgur.com/srYUlDc.png">

Khác nhau giữa Datagram và VC
<img src="http://i.imgur.com/nBS1190.png">
###2.Bên trong router
Chức năng chính của router
<ul>
<li>Routing</li>
<li>Forwarding</li>
</ul>

###3.Gói dữ liệu IP (internet protocol)
<img src="http://i.imgur.com/cSmFEE4.png">
version: Giải quyết theo phiên bản
Headerlength: xác định vị trí bắt đầ của dữ liệu thực sự trong gói dữ liệu IP
Type of service: cấp độ ưu tiên
Upper layer protocol: Chỉ ra số giao thức của tầng trên 6:TCp 17 UDP
TTL: trường này sẽ giảm đi 1 khi mỗi lần gói tin đi qua 1 router.TTL = 0 router sẽ loại bỏ gói tin.Đảm bảo gói tin không thể lưu chuyển mãi mai trong mạng

####3.1 Phân mảnh và hợp nhất gói tin 
