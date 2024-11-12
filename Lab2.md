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
