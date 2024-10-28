# Tài liệu hợp nhất phân tích hệ thống Payroll System

## 1. Kiến trúc đề xuất:
Kiến trúc ba tầng (Three-tier architecture) là một kiến trúc ứng dụng phần mềm phổ biến, đặc biệt phù hợp với hệ thống xử lý dữ liệu phức tạp như hệ thống quản lý bảng lương, tổ chức các ứng dụng thành ba tầng tính toán logic và vật lý: 
  - Tầng trình bày (presentation tier), hay còn gọi là giao diện người dùng;
  - Tầng ứng dụng (application tier), nơi xử lý dữ liệu;
  - Tầng dữ liệu (data tier), nơi lưu trữ và quản lý dữ liệu của ứng dụng.

Giải thích lý do lựa chọn kiến trúc ba tầng:
  - Kiến trúc ba tầng được lựa chọn vì nó mang lại sự linh hoạt, hiệu quả và khả năng bảo trì cao.
  - Việc phân chia ứng dụng thành các tầng riêng biệt giúp dễ dàng quản lý và phát triển từng phần độc lập, đảm bảo tính bảo mật và hiệu suất.
  - Ngoài ra, kiến trúc này cũng cho phép dễ dàng mở rộng (scaling), do đó đáp ứng tốt hơn cho ứng dụng nếu muốn mở rộng.
  - Khi một tầng cần được thay đổi hoặc nâng cấp, kiến trúc ba tầng giúp giảm thiểu ảnh hưởng đến các tầng khác, nhờ vậy, hệ thống dễ bảo trì và phát triển theo thời gian.

Ý nghĩa của từng thành phần trong kiến trúc ba tầng:
  - Tầng trình bày (Presentation Tier): Đây là tầng giao diện người dùng, nơi người dùng tương tác trực tiếp với hệ thống. Nó giúp hệ thống có giao diện dễ sử dụng, có thể thay đổi hoặc nâng cấp mà không ảnh hưởng đến các phần khác của hệ thống.
  - Tầng ứng dụng (Application Tier): Tầng này chứa toàn bộ logic xử lý của hệ thống, thực hiện các quy trình kinh doanh và điều phối việc xử lý dữ liệu. Điều này đảm bảo rằng hệ thống hoạt động ổn định và tuân thủ đúng các quy tắc nghiệp vụ.
  - Tầng dữ liệu (Data Tier): Đây là nơi lưu trữ và quản lý dữ liệu của hệ thống, giúp bảo vệ thông tin và duy trì tính nhất quán cho dữ liệu.

# Biểu đồ package mô tả kiến trúc
![Package Diagram](https://www.planttext.com/api/plantuml/png/NCyn3i8m30NGFQUmklSAg8swHCh0aWanMAcf8Y15iJiWnCaOUYIkG9A9za_Mjzxmlv-rOy4ao_scr0Fz5IU2vfY8AGfAc2DOV59guAKWv-IO4fWeb2xewGp8u8nw_s6zS8Z437QUWj_nxRDoRJTyGC4TgbNlVNPL37qHpa3R7WhNjbwvLXt5iMpv0G00__y30000)

## 2. Cơ chế phân tích:
Một số cơ chế được đề xuất:
  - User Authentication and Access Control: Đảm bảo chỉ nhân viên có quyền truy cập hệ thống và chỉ có thể chỉnh sửa thông tin của riêng mình để bảo mật dữ liệu.
  - Timecard Management: Cho phép nhân viên nhập thông tin thời gian làm việc, giúp hệ thống tự động tính toán tiền lương theo giờ và loại hình trả lương.
  - Automated Payroll Processing: Xử lý bảng lương tự động vào các ngày định trước, giảm thiểu sai sót và đảm bảo nhân viên được trả lương đúng hạn.
  - Commission Calculation for Sales: Tính toán hoa hồng cho nhân viên có lương cố định dựa trên doanh số bán hàng, theo tỷ lệ đã xác định.
  - Payment Method Selection: Cho phép nhân viên lựa chọn phương thức thanh toán linh hoạt, như chuyển khoản, gửi qua bưu điện hoặc nhận trực tiếp.
  - Integration with Legacy Database: Tương tác với cơ sở dữ liệu cũ mà không thay đổi dữ liệu, giúp truy cập thông tin cần thiết cho bảng lương.
  - Reporting Features for Employees: Cung cấp báo cáo để nhân viên tra cứu thông tin như giờ làm, tổng lương và thời gian nghỉ còn lại.
  - Audit and Change Log: Theo dõi và ghi lại các thay đổi trong hệ thống để bảo mật và xử lý tranh chấp.
  - Error Handling and Notifications: Cơ chế xử lý lỗi và thông báo cho người dùng khi có vấn đề xảy ra, nâng cao trải nghiệm và tính chính xác.

## 3. Phân tích ca sử dụng Payment:

## 4. Phân tích ca sử dụng Maintain Timecard:
# 1. Mô tả:
Ca sử dụng này cho phép Nhân viên cập nhật và nộp thông tin về bảng chấm công. Nhân viên tính lương theo giờ và theo tháng phải nộp bảng chấm công hàng tuần ghi lại tất cả số giờ làm việc trong tuần đó và các dự án mà số giờ đó được tính phí. Nhân viên chỉ có thể thực hiện thay đổi trên bảng chấm công cho kỳ trả lương hiện tại và trước khi bảng chấm công được nộp.

# 2. Các lớp phân tích:
  - Boudary Class:
      - Employee Interface: Cung cấp giao diện cho nhân viên để nhập giờ làm việc và gửi thẻ thời gian.
      - Timecard UI: Giao diện hiển thị thông tin thẻ thời gian và danh sách số hiệu tính phí cho nhân viên.
  - Control Class:
      - TimecardManager: Quản lý quá trình tạo, lưu trữ, và gửi thẻ thời gian. Xác thực thông tin giờ làm việc trước khi gửi thẻ thời gian.
      - ValidationService: Xác thực thông tin giờ làm việc và đảm bảo rằng các quy tắc (như giới hạn giờ làm) được tuân thủ.
  - Entity Class:
      - Employee: Lưu trữ thông tin về nhân viên, bao gồm ID, tên, vai trò và danh sách thẻ thời gian.
      - Timecard: Lưu trữ thông tin về giờ làm việc, trạng thái gửi và các số hiệu tính phí liên quan.
      - Project: Cung cấp thông tin về các dự án và số hiệu tính phí liên quan.
      - Charge Number: Đại diện cho các số hiệu tính phí mà nhân viên có thể chọn để ghi nhận giờ làm việc.
