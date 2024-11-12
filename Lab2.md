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
