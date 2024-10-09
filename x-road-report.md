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
X-Road triển khai một bộ tính năng tiêu chuẩn để hỗ trợ và tạo điều kiện thuận lợi cho việc trao đổi dữ liệu và đảm bảo tính bảo mật, toàn vẹn và khả năng tương tác giữa các bên trao đổi dữ liệu
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
Hệ sinh thái X-Road bao gồm X-Road Operator, Member organizations, và Trust Service Provider
### X-Road Operator
Là chủ sở hữu của hệ sinh thái X-Road, Người vận hành chịu trách nhiệm về mọi khía cạnh của hoạt động. Trách nhiệm bao gồm xác định các quy định và thông lệ, chấp nhận thành viên mới, cung cấp hỗ trợ cho Thành viên và vận hành các thành phần trung tâm của phần mềm X-Road.
### X-Road Member 
Thành viên X-Road là các tổ chức đã tham gia hệ sinh thái và sản xuất và/hoặc tiêu thụ dịch vụ với các Thành viên khác. Một tổ chức Thành viên có thể là nhà cung cấp dịch vụ, người tiêu dùng dịch vụ hoặc cả hai. Các tổ chức có thể trở thành Thành viên của một hệ sinh thái bằng cách hoàn tất quy trình tích hợp do Nhà điều hành xác định. Ngoài ra, các thành viên cần có quyền truy cập vào thành phần kỹ thuật cần thiết để trao đổi tin nhắn qua X-Road, Máy chủ bảo mật. 
### Trust Service Provider(s)
Hệ sinh thái X-Road hoạt động đòi hỏi hai loại dịch vụ tin cậy: 1) cơ quan đóng dấu thời gian (TSA) và 2) cơ quan chứng nhận (CA). Nhà cung cấp dịch vụ tin cậy là các tổ chức cung cấp các dịch vụ này. Nhà cung cấp dịch vụ tin cậy có thể là bên thứ ba thương mại hoặc các dịch vụ cũng có thể được cung cấp và duy trì bởi Nhà điều hành X-Road.
## Kiến trúc X-ROAD
### Central Services (Dịch vụ trung tâm)
* Central Server: Chứa danh sách các thành viên X-Road và các Security Servers của họ. Nó cũng lưu trữ chính sách bảo mật của hệ thống, bao gồm danh sách các cơ quan cấp chứng chỉ và cơ quan đóng dấu thời gian (TSAs) đáng tin cậy. Central Server cung cấp thông tin này cho các Security Servers để chúng có thể xử lý các tin nhắn một cách bảo mật.
* Configuration Proxy: Là một phần tùy chọn, giúp phân phối dữ liệu cấu hình từ Central Server đến các Security Servers, giúp tăng cường độ sẵn sàng của hệ thống và giảm tải cho Central Server.
### Security Server
* Security Server: Là cửa ngõ vào hệ thống X-Road, giúp gửi và nhận dịch vụ giữa các Information Systems. Nó chịu trách nhiệm về bảo mật, quản lý khóa, ký số tin nhắn, đóng dấu thời gian và ghi nhật ký. Security Server hỗ trợ cả giao thức REST và SOAP cho việc trao đổi dịch vụ.
* Multi-tenancy: Một Security Server có thể phục vụ nhiều tổ chức. Security Server cũng có khả năng cân bằng tải nội bộ và hỗ trợ cân bằng tải bên ngoài.
### Information System (Hệ thống thông tin)
* Information System: Là hệ thống của các thành viên X-Road, nơi sản xuất hoặc tiêu thụ dịch vụ qua X-Road. Hệ thống này sử dụng REST hoặc SOAP để kết nối với Security Server.
### Time-Stamping Authority (TSA)
* TSA: Là cơ quan cung cấp dịch vụ đóng dấu thời gian. Tất cả các tin nhắn qua X-Road đều được Security Server đóng dấu thời gian để xác nhận sự tồn tại của dữ liệu tại một thời điểm nhất định.
### Certification Authority (CA)
* CA: Là cơ quan cấp chứng chỉ cho Security Servers và các thành viên của X-Road. Chứng chỉ xác thực được dùng để bảo mật kết nối giữa các Security Servers, còn chứng chỉ ký số được dùng để ký các tin nhắn trao đổi.
Central Services quản lý thông tin thành viên và bảo mật của X-Road.
### Tóm tắt đơn giản:
* Security Servers đảm bảo an toàn cho việc trao đổi tin nhắn giữa các hệ thống thông tin.
* Information Systems sử dụng X-Road để kết nối và trao đổi dịch vụ.
* TSA đảm bảo thời gian chính xác của dữ liệu được trao đổi.
* CA cấp các chứng chỉ cần thiết để đảm bảo kết nối và tin nhắn an toàn