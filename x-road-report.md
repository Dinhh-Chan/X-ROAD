# Tổng quan về X-ROAD
## X-ROAD là gì?
X-Road là một hệ thống trao đổi dữ liệu an toàn trên môi trường mạng internet, được sử dụng trong các tổ chức chính phủ từ năm 2000. 
Ý tưởng cơ bản của X-Road là các thành viên của hệ sinh thái trao đổi dữ liệu thông qua các điểm truy cập (Máy chủ bảo mật) triển khai cùng thông số kỹ thuật.
X-Road là lớp trao đổi dữ liệu phân tán được quản lý tập trung giữa các hệ thống thông tin, cung cấp phương pháp chuẩn hóa và an toàn để sản xuất và sử dụng dịch vụ.
Mục tiêu của X-Road là đáp ứng đầy đủ 3 yêu cầu khi truyền dữ liệu trên mạng giữa các cơ quan trong chính phủ: 
* Dữ liệu phải cần dễ truy cập bởi những người có thẩm quyền đã được xác thực để sử dụng.
* Tính toàn vẹn của dữ liệu phải được duy trì, không bên thứ 3 nào được thay đổi dữ liệu khi truyền.
* Dữ liệu phải được giữ bí mật khi truyền, phải được bảo vệ khỏi các người dùng chưa được xác thực.
Tất cả các dữ liệu gửi đi đều được ký số và mã hóa, còn dữ liệu được xác thực và lưu lại nhật ký.
Máy chủ bảo mật của nhà cung cấp dịch vụ áp dụng kiểm soát truy cập vào các tin nhắn đến, do đó đảm bảo rằng chỉ những người dùng đã ký thỏa thuận phù hợp với nhà cung cấp dịch vụ mới có thể truy cập dữ liệu.
X-Road triển khai một bộ tính năng tiêu chuẩn để hỗ trợ và tạo điều kiện thuận lợi cho việc trao đổi dữ liệu và đảm bảo tính bảo mật, toàn vẹn và khả năng tương tác giữa các bên trao đổi dữ liệu:
* quản lý địa chỉ
* định tuyến tin nhắn
* quản lý quyền truy cập
* xác thực cấp độ tổ chức
* xác thực cấp máy
* mã hóa cấp độ vận chuyển
* đóng dấu thời gian
* chữ ký số của tin nhắn
* ghi nhật ký
* xử lý lỗi
## Mô hình tổ chức X-ROAD 