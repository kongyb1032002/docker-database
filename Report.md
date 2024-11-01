# Báo cáo Benchmark Database với HammerDB

## Cấu hình chung:

-  **Virtual Users:** 32
-  **Số lượng warehouse:** 80
-  **Transaction storage engine:** InnoDB

## Tổng Quan

Báo cáo này tổng hợp kết quả benchmark với HammerDB trên ba hệ quản trị cơ sở dữ liệu: MySQL, PostgreSQL và MariaDB. Mục tiêu là đánh giá hiệu suất của các hệ thống này thông qua số giao dịch mỗi phút (tpm) trong điều kiện tải.

### 1. Báo cáo Benchmark MySQL với HammerDB

**Ngày thực hiện Benchmark:** Thứ Năm, 31 tháng 10, 2024  
**Thời gian bắt đầu:** 14:56:14 (UTC+7)  
**Thời gian kết thúc:** 15:05:07 (UTC+7)  
**Tổng thời gian:** Khoảng 9 phút

#### Phân Tích

-  **tpm tối đa đạt được:** 10,572 tại 15:00:47
-  **Giá trị tpm thấp nhất (không bằng 0):** 564 tại 15:03:17
-  **Trung bình tpm (không tính giá trị bằng 0):** 4,954
-  **Số khoảng thời gian tpm bằng 0:** 12

### 2. Báo cáo Benchmark PostgreSQL với HammerDB

**Ngày thực hiện Benchmark:** Thứ Năm, 31 tháng 10, 2024  
**Thời gian bắt đầu:** 16:09:26 (UTC+7)  
**Thời gian kết thúc:** 16:13:07 (UTC+7)  
**Tổng thời gian:** Khoảng 4 phút

#### Phân Tích

-  **Tmp lớn nhất:** 100,662 tại 16:11:17
-  **Giá trị tpm thấp nhất (không bằng 0):** 0 tại 16:09:27
-  **Trung bình tpm (không tính giá trị bằng 0):** 31,831
-  **Số khoảng thời gian tpm bằng 0:** 1

### 3. Báo cáo Benchmark MariaDB với HammerDB

**Ngày thực hiện Benchmark:** Thứ Sáu, 01 tháng 11, 2024  
**Thời gian bắt đầu:** 09:36:45 (UTC+7)  
**Thời gian kết thúc:** 09:40:27 (UTC+7)  
**Tổng thời gian:** Khoảng 4 phút

#### Phân Tích

-  **Tmp lớn nhất:** 21,450 tại 09:39:37
-  **Giá trị tpm thấp nhất (không bằng 0):** 0 tại 09:36:47
-  **Trung bình tpm (không tính giá trị bằng 0):** 11,297
-  **Số khoảng thời gian tpm bằng 0:** 6

## Kết luận so sánh

### Hiệu suất tổng thể:

-  **PostgreSQL** cho thấy hiệu suất tốt nhất với Tmp lớn nhất là 100,662 và trung bình tpm là 31,831, vượt trội so với MySQL và MariaDB.
-  **MariaDB** có Tmp lớn nhất là 21,450, với trung bình tpm là 11,297, cho thấy khả năng xử lý khá tốt nhưng vẫn thấp hơn PostgreSQL.
-  **MySQL** có đỉnh tpm thấp nhất chỉ 10,572, với trung bình là 4,954, cho thấy khả năng xử lý giao dịch dưới tải thấp hơn đáng kể.

### Ảnh hưởng của tài nguyên:

-  **Sự bão hòa hiệu suất** là điểm chung giữa các hệ thống, nhưng PostgreSQL có thể duy trì hiệu suất cao hơn trong thời gian dài hơn trước khi giảm xuống.
-  **Giá trị tpm bằng 0** xuất hiện nhiều ở MySQL và một lần ở PostgreSQL, cho thấy có thời điểm không xử lý giao dịch, có thể là do thiếu tài nguyên hoặc thời gian khởi động.

### Khuyến nghị:

Dựa trên các kết quả benchmark, PostgreSQL là lựa chọn tốt nhất cho các ứng dụng yêu cầu hiệu suất cao dưới tải lớn. MariaDB có thể là một sự thay thế phù hợp, trong khi MySQL có thể cần tối ưu hóa hơn nữa để cải thiện hiệu suất trong các tình huống tương tự.
