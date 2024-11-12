# Phân tích ca sử dụng Create Administrative Report
## 1. Mô tả:
Ca sử dụng cho phép Quản trị viên tính lương tạo báo cáo tổng hợp về số giờ làm việc hoặc báo cáo lương từ đầu năm đến nay.

## 2. Xác định các lớp:
- Boundary: AdministrativeReportUI
- Control: ReportController
- Entity: Report, Employee, PayrollData

## 3. Biểu đồ Sequence:
![](https://www.planttext.com/api/plantuml/png/f5LBRjmm3Dth53p0f0UOHP4WwM8MBO86FG1ZqGu1MN8ase3FraMFr2kKygUUfbQHcSx65aTyV8zwb7z-_t6R1AFqhJDOIOZmY6CCpjtPbZqdYQX1ynnwRp6ES1RcWRvI5w9yEvagUD4ic0FtyyfHDEI5PLpYw-fJsxam4gthfUG32XgpLnzkFXOg7nNwjQSa806gI2W4SIwsdv2Xth8yAeEKbZnzJ83cxQxta5WWPEpe07OYWxxHTreaWyUMqiKY7sCOsAxIL2WBHSQBD3wHjty167G29r-7s2f4y505PKf21lItruApmygw9J8DAeigIYaxnEPJpCbd6_S9QN8V_PQmLssE7U7-ZwFTTfUGf_yQygIT8Lk4B_NxWLFdS5phaKi4dpabzWtmrgsBSLUVj0MiQtrHmhlO7tsNNMitWsZmlsOouN3LHEfxpR5TyyiZkSTjOp2bkr3DvaPLc0UmA6ZdPbWwN03wbsUVpgI_mwsvWfq7SihquVTTT8M3lmJXUZKmM4uLHgiuqtagj3BZvaKWrFit_gcU1XCuGUznG7Rux0YqJUm7T6mF1ZrGZ1ffy-WtbFVQUN387gOUoKkXrvKcHve-FJ0lAt8VChkicuovrTVyKVe5003__mC0)

## 4. Nhiệm vụ của các lớp:
- PayrollAdministrator (Actor):
  - Là người dùng hệ thống, chịu trách nhiệm yêu cầu tạo và lưu trữ báo cáo hành chính.
  - Cung cấp các thông tin cần thiết như loại báo cáo, phạm vi ngày và tên nhân viên.
- AdministrativeReportUI (Boundary):
  - Đây là lớp giao diện người dùng, có nhiệm vụ hiển thị giao diện để Payroll Administrator nhập thông tin cần thiết và yêu cầu tạo báo cáo.
  - Nó gửi yêu cầu và dữ liệu đầu vào từ người dùng đến lớp điều khiển (ReportController).
- ReportController (Control):
  - Lớp này điều khiển luồng thực thi của ca sử dụng.
  - Nhận thông tin từ AdministrativeReportUI, kiểm tra tính đầy đủ của dữ liệu, yêu cầu thêm thông tin nếu cần, và tương tác với lớp thực thể (Report và PayrollData) để lấy dữ liệu cần thiết.
  - Đảm bảo rằng báo cáo được tạo ra hoặc được lưu trữ theo yêu cầu của người dùng.
- Report (Entity):
  - Đại diện cho một báo cáo hành chính được tạo ra trong hệ thống.
  - Chứa dữ liệu và logic cần thiết để lưu trữ hoặc xử lý thông tin báo cáo.
  - Lưu giữ thông tin như loại báo cáo, ngày bắt đầu/kết thúc và tên nhân viên.
- Employee (Entity):
  - Lớp này đại diện cho một nhân viên trong hệ thống.
  - Mặc dù trong biểu đồ không có tương tác trực tiếp với Employee, nó có thể cung cấp thông tin liên quan đến nhân viên để tạo báo cáo, chẳng hạn như danh sách thời gian làm việc hoặc thông tin bảng lương.
- PayrollData (Entity):
  - Lớp này lưu trữ dữ liệu liên quan đến bảng lương, bao gồm thông tin về thời gian làm việc và lương của nhân viên.
  - PayrollData cung cấp dữ liệu cần thiết cho ReportController để tạo báo cáo.
    
## 5. Quan hệ giữa các lớp: 
- PayrollAdministrator là tác nhân (actor) tương tác với lớp AdministrativeReportUI để yêu cầu tạo và lưu báo cáo.
- AdministrativeReportUI là lớp giao diện, giao tiếp với lớp ReportController để gửi yêu cầu và dữ liệu từ người dùng.
- ReportController quản lý luồng xử lý, tương tác với lớp PayrollData để lấy thông tin cần thiết và lớp Report để tạo báo cáo.
- Report là lớp thực thể lưu trữ thông tin về báo cáo.
- PayrollData và Employee là các lớp thực thể chứa dữ liệu liên quan, trong đó PayrollData là nguồn dữ liệu chính để tạo báo cáo và Employee cung cấp thông tin nhân viên.

## 6. Biểu đồ lớp:
![](https://www.planttext.com/api/plantuml/png/V9BFIiGm4CRlUOeSzT0NABBiuWeMHCG_U1usun9CapgP2aLyCWy-agzWiarYkrLx2FIRcTzycSdNn-VQCn3thH5YPy1xkL6jjjep0UjNlCNE4Jyqyat8mqVuqgFdKJyvJQhIlZCm7AaUCY18xxd1g9mxo-ICGIhe7I4m_iUOMTWefLax2wQnJsxP8N6ha1z_xuSEQtd7fEq-1GvNtuQUjOndKj6gfTPsnWs8rz2Yh-LLcC_PY5ebKtkqI5FxnSr5gYr-CgnHHtvieC-aYELSlqK6RVmKVGD3d64m2cMAeUBHqVEbwycNaGKnvCu8V-ovgbQB3Od5odwoVezDZ8cfoHZBzn5Y7KOTNzut0000__y30000)

## 7. Giải thích biểu đồ lớp:
- PayrollAdministrator (Actor):
  - Vai trò: Là tác nhân bên ngoài hệ thống, không có thuộc tính hay phương thức cụ thể vì đây chỉ là người dùng sử dụng hệ thống để yêu cầu báo cáo.
  - Tương tác: Tác nhân này chỉ tương tác với lớp AdministrativeReportUI.
- AdministrativeReportUI (Boundary)
  - Thuộc tính: Không có thuộc tính cụ thể vì đây là lớp giao diện chịu trách nhiệm nhận thông tin từ người dùng.
  - Phương thức:
    - requestReport(): Phương thức để nhận yêu cầu tạo báo cáo từ người dùng.
    - displayReport(): Phương thức để hiển thị báo cáo sau khi được tạo.
    - saveReport(): Phương thức để lưu báo cáo sau khi tạo nếu người dùng yêu cầu.
  - Giải thích: Lớp này là trung gian giữa người dùng và lớp điều khiển ReportController, nhận thông tin đầu vào và gửi yêu cầu xử lý.
- ReportController (Control)
  - Thuộc tính: Không có thuộc tính cụ thể vì lớp này tập trung vào xử lý logic.
  - Phương thức:
    - createReport(): Phương thức để xử lý logic tạo báo cáo từ các thông tin được cung cấp.
    - saveReport(): Phương thức để lưu báo cáo sau khi tạo nếu được yêu cầu.
    - requestAdditionalInfo(): Phương thức để yêu cầu thêm thông tin nếu thông tin đầu vào chưa đủ.
  - Giải thích: Đây là lớp điều khiển, đảm bảo luồng xử lý đúng khi tạo báo cáo, tương tác với cả lớp giao diện và lớp thực thể để hoàn thành quy trình.
- Report (Entity)
  - Thuộc tính:
    - reportType: String: Loại báo cáo (ví dụ: tổng số giờ làm việc hoặc lương theo năm).
    - startDate: Date: Ngày bắt đầu của phạm vi báo cáo.
    - endDate: Date: Ngày kết thúc của phạm vi báo cáo.
    - employeeNames: List<String>: Danh sách tên nhân viên được đưa vào báo cáo.
  - Phương thức:
    - generateReport(): Phương thức để tạo ra báo cáo với thông tin được cung cấp.
- Employee (Entity)
  - Thuộc tính:
    - employeeId: String: Mã định danh duy nhất của nhân viên.
    - name: String: Tên nhân viên.
  - Phương thức:
    - getEmployeeDetails(): Phương thức để truy xuất thông tin chi tiết của nhân viên.
  - Giải thích: Lớp này chứa thông tin chi tiết về nhân viên, có thể được truy vấn khi tạo báo cáo.
- PayrollData (Entity)
  - Thuộc tính: Không có thuộc tính cụ thể, vì lớp này đại diện cho việc quản lý dữ liệu lương.
  - Phương thức:
    - getWorkHours(): Phương thức để lấy thông tin về số giờ làm việc của nhân viên.
    - getPayDetails(): Phương thức để lấy thông tin chi tiết về tiền lương của nhân viên.
  - Giải thích: Lớp này cung cấp dữ liệu cần thiết từ bảng lương và thời gian làm việc, phục vụ cho việc tạo báo cáo.

# Phân tích ca sử dụng Create Employee Report
## 1. Mô tả:
Ca sử dụng này cho phép Nhân viên tạo các báo cáo về số giờ làm việc, số giờ làm việc cho một dự án, ngày nghỉ phép/ngày nghỉ ốm, hoặc tổng lương tính đến hiện tại.

## 2. Xác định các lớp:
- Boundary: EmployeeReportUI.
- Entity: Employee, Report, ProjectDatabase, PayrollData.
- Control: EmployeeReportController.

## 3. Biểu đồ Sequence:
![](https://www.planttext.com/api/plantuml/png/b5N1Rjim3BthAuYUitr03aE1Ti1w6OPbmywCH2TQPIcZv0p-jXtsIVk5KOhj9avhExd4fiL7yZsI-lVdxtrCoAcfdKAT0iF7-k12IwIseV46kHqiN-aGE7r_KZhunC6DFZoSh8vOaKysjN2ozszVEFmadHunuHOZ3MPiirSsAzKZmhiFLs7NWlUhePWW1T1Cc0Zu565yzDhz9RcrH8onyvI_0gdUEZsTI0UIsWEjm9I4qEzefWmXucXDdxoKOXEnnHkhs90tLn0ANUfeBrc1ZN3tBIHqy2aq7E57u6SoK8dGs2jofq1-KmoCfCi49BPq971MQ0WLw3toZi0tzPOu5i2HqtGr0jYmduAxJQ576myEsocWrnqtv2JfIxzNuYzI9nOieViIJJwfoOOx6uapgZrfYZ4FfCcpSdPe4RN5QIhgoRQ6XulHwfff9a8vioDFBAxcncdgjUeYbXuUHEe6DEQXZtWSyffNycnRlEMuJ4jvhYpNFSffOInjoPSyYhiB6fCD7b3wmsDDCuLSxArkRom0cj9tCoBZ1eLpPAF8oJGFAPj04Nn8CoJFDS7da6pLzm0O6pMooS7oi0YyGDlTlYo7uOPwgafNvoNNU3oYTRXr1BBRh8zDLLbjvP9PAVH0p6Akym3jobQC-_3RhmfxQN-siRKSPYftOWQILqtkVKuZ5qbAtSjZlYt_0m00__y30000)

## 4. Nhiệm vụ của các lớp:
- Employee (Actor):
  - Là người dùng của hệ thống, chịu trách nhiệm yêu cầu tạo báo cáo, cung cấp thông tin cần thiết như loại báo cáo, khoảng thời gian, và mã charge number (nếu cần).
  - Employee cũng có thể yêu cầu lưu báo cáo sau khi tạo.
- EmployeeReportUI (Boundary):
  - Đây là lớp giao diện người dùng, chịu trách nhiệm nhận yêu cầu và thông tin đầu vào từ Employee và hiển thị kết quả sau khi báo cáo được tạo.
  - Nó chuyển thông tin và yêu cầu từ người dùng đến lớp điều khiển EmployeeReportController.
- EmployeeReportController (Control):
  - Lớp này điều khiển luồng hoạt động của ca sử dụng.
  - Nó xử lý yêu cầu tạo báo cáo từ EmployeeReportUI, kiểm tra tính đầy đủ của dữ liệu, và tương tác với các lớp thực thể ProjectDatabase và PayrollData để lấy dữ liệu cần thiết.
  - Sau đó, nó tạo một báo cáo thông qua lớp Report.
- Report (Entity):
  - Lớp này đại diện cho báo cáo được tạo ra.
  - Nó chứa dữ liệu và logic cần thiết để lưu trữ và xử lý báo cáo.
  - Report được dùng để lưu kết quả của việc tạo báo cáo và hỗ trợ chức năng lưu trữ.
- ProjectDatabase (Entity):
  - Lớp này lưu trữ và quản lý dữ liệu liên quan đến các dự án, bao gồm danh sách mã charge number.
  - Nó cung cấp thông tin về dự án khi EmployeeReportController yêu cầu, đặc biệt là khi cần tạo báo cáo liên quan đến một dự án cụ thể.
- PayrollData (Entity):
  - Lớp này lưu trữ dữ liệu về giờ làm việc và thông tin lương của nhân viên.
  - Nó cung cấp dữ liệu cần thiết cho EmployeeReportController để tạo báo cáo.

## 5. Quan hệ giữa các lớp:
- Tương tác chính: Employee tương tác với EmployeeReportUI.
- Điều khiển: EmployeeReportUI và EmployeeReportController giao tiếp với nhau để xử lý yêu cầu.
- Truy vấn dữ liệu: EmployeeReportController tương tác với ProjectDatabase và PayrollData để lấy dữ liệu cần thiết.
- Tạo thực thể: EmployeeReportController tạo và lưu trữ các báo cáo thông qua lớp Report.
  
## 6. Biểu đồ lớp:
![](https://www.planttext.com/api/plantuml/png/f5H1JiCm4Bpx5JusKYlk4Qeg5H2LAeHI46StMRK1npPh9oX2l8m3J-8BE77gD0uj1tA8bDdrx6Hsak_FhuKs34rPS99ofZMzBXINDG1z9zHUCmeTiCfYkZ6OYrrN4Ao00KGfmci9sYIW99f9H3v8mEegZwkEdT8irugpUYLKQMua5lQGA-YzVFCy0_ODgs0jKsPoAKxFM4fXK78Ew6Sfb2bexUg98_Fa5UDvnWoqIZoQ8bWiqA6jW0xYdOw33qToN8Ut4Tl7Xrf1O6Fh_vMT4jFcVd1TP2FCKLY01RRlG03-hlESmdkKpv2sX5kc-ush7e_fEjVcqXsT-t5ckMUuWxkos0BgIHIqzHDOtUoWOUhP7PP0AZ7JfmOyINovbQKb7-Tl6des7TeLZUmnLaWZubzazgtynp6RpKUP9gEGZxlwL9AJSMrEEV1yJxY-s0R4AeKAWktyGNEqevx2-tzni2uYNQBFlPLZA57uA9A5jRFvlVm0003__mC0)

## 7. Giải thích biểu đồ lớp:
- Employee: Đại diện cho người dùng hệ thống. Nhân viên có thể yêu cầu tạo báo cáo thông qua phương thức requestReport().
- EmployeeReportUI: Giao diện người dùng hiển thị các biểu mẫu nhập thông tin và báo cáo kết quả. Nó có các phương thức để nhận thông tin và hiển thị báo cáo.
- EmployeeReportController: Điều khiển luồng xử lý yêu cầu tạo báo cáo, bao gồm kiểm tra đầu vào, tạo báo cáo và xử lý lưu trữ.
- Report: Thực thể lưu trữ dữ liệu báo cáo. Lớp này có các phương thức để tạo và lưu báo cáo.
- ProjectDatabase: Lưu trữ dữ liệu về các dự án và cung cấp danh sách mã charge number khi cần.
- PayrollData: Lưu trữ thông tin về giờ làm việc và lương của nhân viên, hỗ trợ truy xuất dữ liệu để tạo báo cáo.

# Phân tích ca sử dụng Maintain Employee Information
## 1. Mô tả:
## 2. Xác định các lớp:
## 3. Biểu đồ Sequence:
## 4. Nhiệm vụ của các lớp:
## 5. Quan hệ giữa các lớp:
## 6. Biểu đồ lớp:
## 7. Giải thích biểu đồ lớp:

# Phân tích ca sử dụng Run Payroll
## 1. Mô tả:
## 2. Xác định các lớp:
## 3. Biểu đồ Sequence:
## 4. Nhiệm vụ của các lớp:
## 5. Quan hệ giữa các lớp:
## 6. Biểu đồ lớp:
## 7. Giải thích biểu đồ lớp:

# Phân tích biểu đồ Select Payment Method
## 1. Mô tả:
## 2. Xác định các lớp:
## 3. Biểu đồ Sequence:
## 4. Nhiệm vụ của các lớp:
## 5. Quan hệ giữa các lớp:
## 6. Biểu đồ lớp:
## 7. Giải thích biểu đồ lớp:

# Code java mô phỏng ca sử dụng Maintain Timecard.
