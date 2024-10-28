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
### 1. Mô tả:
Ca sử dụng này cho phép Nhân viên chọn phương thức thanh toán. Phương thức thanh toán xác định cách mà Nhân viên sẽ nhận tiền lương. Nhân viên có thể chọn một trong các cách sau: nhận séc trực tiếp, nhận qua bưu điện, hoặc để tiền lương được chuyển trực tiếp vào một tài khoản ngân hàng cụ thể

### 2. Các lớp phân tích:
  - Boundary Class: Employee Interface.
  - Control Class: PaymentMethodSelector.
  - Entity Classes: Employee, PaymentMethod, EmployeeRepository.
### 3. Biểu đồ Sequence:
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/V99BQiCm54NdMeN8o8Lc0ncK5E911u7WGEUlrWjve5-bPuFNra6Nr2rKyYT5ZTkHXExHlLUVhu_FVMG8t1aje6KNP6syTWEYy6cPMl9WMMvEC1YqV4I-EdL6ZPdTI8ZoT3oNw6BGe7UH4ZQCNDtyupWx2R5ibjkdx2ntCevX1LqzYAmbf6uI4V2zmyZFFP26DuqJ51ELvEtD2ExrqINRBAaxgIXw3SCFysUbkGiF7ii-FMXIm5W0HHMAhvbPT_V1zQJmW9pwnafDOndH-HomxArmdhoeHsd6r2bmfYzarGhxgzGY781X9QnyWLkhjJjidRrGCC3aR3hZ7gtA_-iR003__mC0)
### 4. Nhiệm vụ của các lớp phân tích:
  - Boundary Class:
    - Employee Interface: Giao diện mà nhân viên sử dụng để chọn phương thức thanh toán.
  - Control Class:
    - PaymentMethodSelector: Lớp xử lý logic cho việc chọn phương thức thanh toán, xác thực lựa chọn của nhân viên.
  - Entity Classes:
    - Employee: Đại diện cho nhân viên trong hệ thống với các thông tin liên quan đến nhân viên.
    - PaymentMethod: Đại diện cho phương thức thanh toán mà nhân viên có thể chọn (pick-up, mail, direct deposit).
    - EmployeeRepository: Quản lý thông tin nhân viên trong hệ thống, bao gồm việc tìm kiếm và cập nhật thông tin của nhân viên.
### 5. Quan hệ giữa các lớp:
  - Employee và PaymentMethod: Một nhân viên có thể có nhiều phương thức thanh toán, nhưng mỗi phương thức thanh toán thuộc về một nhân viên.
  - PaymentMethodSelector: Lớp này liên kết với EmployeeRepository để truy xuất và cập nhật thông tin nhân viên.
  - PaymentMethod: Lớp này được sử dụng bởi PaymentMethodSelector để xác định phương thức thanh toán của nhân viên.
### 6. Biểu đồ lớp:
![Class Diagram](https://www.planttext.com/api/plantuml/png/V591JiCm4Bpx5LPE0IaLN2jKzG07990GVS5IBs39iQtiDfA5U1a7diGNS70SuhIGsyxEZ6Tty_NnkIM6ZW-j4Ni3HFAczSO5HFacvF3XMD-gjTnnf-rBmYsqM28UGekMxv5VNIG_p4lnBaR_0iwFSF0BCuKCsj04JlgSxn6z8ysk2ykaKNIdYQyoSvFQpzgg3DN7Kvsj9-l4FtW5Z4UANrfKz4x_DTeE3UvZl9oEVkg2KcU7DB4cRo2a5fMz7emUqeow-ReYxyavWs37AtIkrmglq_xgnHvdcQT3LvULR1fPNQnMvzNYRAT7QfhDYJkKvFziiv7OebN3h_SD003__mC0)
### 7. Giải thích biểu đồ lớp:
  - Employee:
    - Thuộc tính: employeeId, name, role, paymentMethod, timecards.
  - PaymentMethod:
    - Thuộc tính: type, details.
  - EmployeeRepository:
    - Thuộc tính: employees.
    - Phương thức:
      - findEmployee(employeeId: String): Employee: Tìm kiếm nhân viên theo mã nhân viên.
      - updateEmployee(employee: Employee): void: Cập nhật thông tin của nhân viên.
  - PaymentMethodSelector:
    - Phương thức:
      - selectPaymentMethod(): void: Bắt đầu quy trình chọn phương thức thanh toán.
      - displayMethods(): void: Hiển thị các phương thức thanh toán khả dụng.
      - validateMethod(type: String): boolean: Xác thực phương thức thanh toán đã chọn.
      - provideDetails(details: String): void: Cung cấp thông tin chi tiết cho phương thức thanh toán.

## 4. Phân tích ca sử dụng Maintain Timecard:
### 1. Mô tả:
Ca sử dụng này cho phép Nhân viên cập nhật và nộp thông tin về bảng chấm công. Nhân viên tính lương theo giờ và theo tháng phải nộp bảng chấm công hàng tuần ghi lại tất cả số giờ làm việc trong tuần đó và các dự án mà số giờ đó được tính phí. Nhân viên chỉ có thể thực hiện thay đổi trên bảng chấm công cho kỳ trả lương hiện tại và trước khi bảng chấm công được nộp.

### 2. Các lớp phân tích:
  - Boudary Class: Timecard UI.
  - Control Class: TimecardManager, ValidationService.
  - Entity Class: Employee, Timecard, Project, Charge Number.
### 3. Biểu đồ Sequence:
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/Z5LDQjj05DxFAHxPvm85br1IJA1f0dMo7uy7QH9f9AIHYPSbYr9A5w6KBah0nfH2mP3IhgH55bDwZpb1hz0t8ocHB2c95uCqx_lUx_VaVyNjNgfeeh8m88Go5INmCeo3QC4vYV5UC15JgM1d8aBEQ38xETW1ciB9GR_va4hgySHXgkSsy9G6OaQLYEGRdim5umvQtKPRuECaEkDCLPv2ZdVxLD4fJKlQyU7-Y_uydBb-EPgU4J8QmMlVv9iOni8Kr_1ABqCunSTt34OZGkgoOVSvLWVFOA5_PC1C_Zq3MH8zIoHeH4XL7E9KaYtW8ZFvDmKAWOKzYsk1S2h1jn4aA9El1Ab9o6_aXZxE4NKPeYiwx8BfNuG62YOTmBclVqiFOnIVwaY0ly5e5XBr10fDyLKGBcVDH5qlR0gNqe4_F5ParI0xctONPrJwaEeLmzCKLoKh0wKtU1_xUaCSPxSEgXAJhs5kYhTFe9P1xuQubV80gJjqXl2FSW0FSxriQG4255574C7Vcwoo_xdIwuenF7pc73gKQleT9BW0dIauYOzDiH6LH2QbRMmdz9Z2FSVh-jokRGZtjEAafvUBoeVjfPtmoYhNr-tjkFiUe8SB7BkBzPCrktCFUN2RJF4P0xXvbkjhL-Z-jTuTTB-E8S21kzLfEU_R04UQQbmZv7mfzwqZmUuNf16u4P47AHymFRZ70phOuhZqRSjw5jVA_Jsg54NFtEAJFJpjdy5_0000__y30000)
### 4. Nhiệm vụ của các lớp phân tích:
  - Boudary Class:
      - Timecard UI: Giao diện hiển thị thông tin thẻ thời gian và danh sách số hiệu tính phí cho nhân viên.
  - Control Class:
      - TimecardManager: Quản lý quá trình tạo, lưu trữ, và gửi thẻ thời gian. Xác thực thông tin giờ làm việc trước khi gửi thẻ thời gian.
      - ValidationService: Xác thực thông tin giờ làm việc và đảm bảo rằng các quy tắc (như giới hạn giờ làm) được tuân thủ.
  - Entity Class:
      - Employee:
        - Chứa các thuộc tính như employeeId, name.
        - Phương thức: timecards.
        - Lưu trữ thông tin về nhân viên, bao gồm ID, tên, vai trò và danh sách thẻ thời gian.
      - Timecard:
        - Chứa các thuộc tính như timecardId, employeeId, startDate, endDate, status, chargeHours.
        - Lưu trữ thông tin về giờ làm việc, trạng thái gửi và các số hiệu tính phí liên quan.
      - Project:
        - Chứa các thuộc tính như projectId, projectName, chargeNumbers.
        - Cung cấp thông tin về các dự án và số hiệu tính phí liên quan.
      - Charge Number:
        - Chứa các thuộc tính như chargeNumberId, description, maxHours. 
        - Đại diện cho các số hiệu tính phí mà nhân viên có thể chọn để ghi nhận giờ làm việc.
### 5. Quan hệ giữa các lớp:
  - Employee có mối quan hệ một-nhiều với Timecard (một nhân viên có thể có nhiều thẻ thời gian).
  - Timecard có quan hệ nhiều-nhiều với Charge Number (một thẻ thời gian có thể liên kết với nhiều số hiệu tính phí).
  - Project có mối quan hệ một-nhiều với Charge Number (một dự án có thể có nhiều số hiệu tính phí).
  - TimecardManager và ValidationService chịu trách nhiệm xử lý các thao tác và xác thực liên quan đến thẻ thời gian.
### 6. Biểu đồ lớp: 
![Class Diagram](https://www.planttext.com/api/plantuml/png/T5FTIiCm5BxlKuHUgTYXjsMCWHCSk25ClJzB3ZMIj2L9XqDyCYzy95_1_YHPrjHUbERxoNTESlhx_RFK1fHff4WIAa1hyimbKb3iPKq-4z8_ZEjQmD4n5vV9rrYzWH8ALDuY-_MKunK4Ps1uLUvG7JX5xpaC33vKZTAXvLxMeZgYKsO4BR1cETaPnSl24YL87476rg1pyiYrcRkQ5d4JVd_dYVR_DxW_nLLRV4wwjvENBC9QfMdqo4xVG1L3updPG3s_wu5j8_UehicgQlO2WugVLFMErFY2ws4TbMNnRNmiD0XmHnE61c4Xx1D3VnJBK5F5w-wIHuo43zlbq5EN4anSbYt68tNYtOnr8ZSIawJ39ibe_au19BsPpQxILaRIs_uhR3tnOsZ9JZOOVA2xbqXnjb6oR0UZ_UN-0000__y30000)
### 7. Giải thích biểu đồ lớp:
  - TimecardUI
      - Nhiệm vụ: Cung cấp giao diện cho người dùng để hiển thị thông tin về thẻ thời gian và cho phép nhân viên nhập giờ làm việc.
      - Phương thức:
        - displayTimecard(): Phương thức này cho phép hiển thị thẻ thời gian cho nhân viên.
  - TimecardManager
      - Nhiệm vụ: Quản lý các thao tác liên quan đến thẻ thời gian, bao gồm việc tạo, lưu trữ và gửi thẻ thời gian.
      - Phương thức:
        - manageTimecard(): Thực hiện các hoạt động quản lý thẻ thời gian, bao gồm tạo và gửi thẻ thời gian.
  - ValidationService
      - Nhiệm vụ: Xác thực thông tin giờ làm việc được nhập vào thẻ thời gian và đảm bảo rằng chúng tuân thủ các quy tắc (ví dụ: không vượt quá giờ làm tối đa).
      - Phương thức:
        - validateHours(): Phương thức này thực hiện việc kiểm tra và xác nhận số giờ làm việc.
  - Employee
      - Nhiệm vụ: Đại diện cho thông tin của nhân viên trong hệ thống.
      - Thuộc tính:
        - employeeId: ID duy nhất của nhân viên.
        - name: Tên của nhân viên.
        - role: Vai trò của nhân viên (ví dụ: nhân viên làm theo giờ, nhân viên lương).
        - timecards: Danh sách các thẻ thời gian mà nhân viên đã tạo.
  - Timecard
      - Nhiệm vụ: Lưu trữ thông tin liên quan đến thẻ thời gian của nhân viên.
      - Thuộc tính:
        - timecardId: ID duy nhất của thẻ thời gian.
        - employeeId: ID của nhân viên liên kết với thẻ thời gian.
        - startDate: Ngày bắt đầu của thẻ thời gian.
        - endDate: Ngày kết thúc của thẻ thời gian.
        - status: Trạng thái của thẻ thời gian (chẳng hạn như "đã gửi").
        - chargeHours: Bản đồ (Map) lưu trữ số giờ làm việc cho từng số hiệu tính phí (Charge Number).
  - Project
      - Nhiệm vụ: Cung cấp thông tin về các dự án mà nhân viên có thể tham gia.
      - Thuộc tính:
        - projectId: ID duy nhất của dự án.
        - projectName: Tên của dự án.
        - chargeNumbers: Danh sách các số hiệu tính phí liên kết với dự án.
  - ChargeNumber
      - Nhiệm vụ: Đại diện cho các số hiệu tính phí mà nhân viên có thể sử dụng để ghi nhận giờ làm việc.
      - Thuộc tính:
        - chargeNumberId: ID duy nhất của số hiệu tính phí.
        - description: Mô tả về số hiệu tính phí.
        - maxHours: Giới hạn số giờ làm việc tối đa cho số hiệu tính phí này.
      
## 5. Hợp nhất kết quả phân tích:
  - Lớp Timecard:
    - Vai trò: Đại diện cho một thẻ thời gian của nhân viên. Nó lưu trữ thông tin về các khoảng thời gian làm việc.
    - Chức năng chính: Quản lý thông tin liên quan đến giờ công của nhân viên trong một khoảng thời gian xác định.
  - Lớp TimecardUI:
    - Vai trò: Giao diện người dùng cho việc hiển thị thông tin thẻ thời gian.
    - Chức năng chính: Cung cấp các phương thức để người dùng có thể xem và tương tác với thẻ thời gian.
  - Lớp TimecardManager:
    - Vai trò: Quản lý các thao tác liên quan đến thẻ thời gian, như tạo mới, sửa đổi hoặc xóa thẻ thời gian.
    - Chức năng chính: Thực hiện các hành động liên quan đến thẻ thời gian và gọi đến các dịch vụ xác thực khi cần thiết.
  - Lớp ValidationService:
    - Vai trò: Dịch vụ để xác thực thông tin trong thẻ thời gian.
    - Chức năng chính: Đảm bảo rằng các giờ làm việc được ghi nhận là hợp lệ và đáp ứng các tiêu chuẩn đã định.
  - Lớp PaymentMethod:
    - Vai trò: Lưu trữ thông tin về phương thức thanh toán của nhân viên.
    - Chức năng chính: Chứa loại phương thức thanh toán (như nhận trực tiếp, gửi qua bưu điện, hoặc chuyển khoản) và các thông tin chi tiết liên quan.
  - Lớp Employee:
    - Vai trò: Đại diện cho nhân viên trong hệ thống. Lớp này chứa thông tin cá nhân và các phương thức thanh toán cùng thẻ thời gian của nhân viên. Được sử dụng trong cả 2 ca sử dụng "Payment" và "Maintain Timecard".
    - Chức năng chính: Quản lý thông tin của nhân viên, bao gồm mã nhân viên, tên, vai trò, phương thức thanh toán, và danh sách thẻ thời gian. Nó kết nối các lớp Timecard và PaymentMethod, cho phép các ca sử dụng liên quan đến thanh toán và thẻ thời gian sử dụng thông tin chung.
  - Lớp Project:
    - Vai trò: Đại diện cho một dự án trong hệ thống.
    - Chức năng chính: Quản lý thông tin về các dự án, bao gồm mã dự án, tên dự án, và danh sách mã charge liên quan đến dự án đó.
  - Lớp ChargeNumber:
    - Vai trò: Đại diện cho một mã charge cụ thể.
    - Chức năng chính: Lưu trữ thông tin về mã charge, bao gồm mô tả và số giờ tối đa có thể được ghi nhận cho mã charge đó.
  
Biểu đồ class
![](https://www.planttext.com/api/plantuml/png/V5J1QeD04BtlLooUsb93UmqX19f20pK4qlO-MOTaMrUNTGsLaY_heP_KN-YggzrL4q59tfitCpjlzFVxPv5hKBeG2I4Is0ViaGOHy5IRcxvmWGnK7D0lGit54iZp3hLWTOLKMt0LJ-bMAvxk7HA5JB8ISPIi6rY2nYcjdguiZKTnez15FfAA7K3jyIahb64ZaBE76bWNOeVgbYwpOfVWl1QSoCY9NbVEcIYDUIuJA5lswlgyCeBKZ4vvSb5ZbzHlaF0ODC_IBQeZP-ZfZmtRdAUJdnoZDb0AJ3MDK1-odakMQoWlhoub3ePdJel6yyGVQrskoVTeFRIfpfeQqXG4zY3fDZFrUoF-0fa6ddckP-tSvlyjR5JsZant7SZc_w01Yw-7VJ1d7zf2xeuunLoug-Zg1sLZp9dYihApnmZuj4lPh61LnTcvC9pt5udq5wkAQIqO9GUxH4XdMN0_cTm49em6T_MlDi654D-ZxfstR1NNADmvaTQXGJOlYYpCcrrzSlu0003__mC0)
