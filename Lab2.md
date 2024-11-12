# Phân tích ca sử dụng Create Administrative Report
## 1. Mô tả:
Ca sử dụng cho phép Quản trị viên tính lương tạo báo cáo tổng hợp về số giờ làm việc hoặc báo cáo lương từ đầu năm đến nay.

## 2. Xác định các lớp:
- Boundary: AdministrativeReportUI
- Control: ReportController
- Entity: Report, Employee, PayrollData

## 3. Biểu đồ Sequence:
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/f5LBRjmm3Dth53p0f0UOHP4WwM8MBO86FG1ZqGu1MN8ase3FraMFr2kKygUUfbQHcSx65aTyV8zwb7z-_t6R1AFqhJDOIOZmY6CCpjtPbZqdYQX1ynnwRp6ES1RcWRvI5w9yEvagUD4ic0FtyyfHDEI5PLpYw-fJsxam4gthfUG32XgpLnzkFXOg7nNwjQSa806gI2W4SIwsdv2Xth8yAeEKbZnzJ83cxQxta5WWPEpe07OYWxxHTreaWyUMqiKY7sCOsAxIL2WBHSQBD3wHjty167G29r-7s2f4y505PKf21lItruApmygw9J8DAeigIYaxnEPJpCbd6_S9QN8V_PQmLssE7U7-ZwFTTfUGf_yQygIT8Lk4B_NxWLFdS5phaKi4dpabzWtmrgsBSLUVj0MiQtrHmhlO7tsNNMitWsZmlsOouN3LHEfxpR5TyyiZkSTjOp2bkr3DvaPLc0UmA6ZdPbWwN03wbsUVpgI_mwsvWfq7SihquVTTT8M3lmJXUZKmM4uLHgiuqtagj3BZvaKWrFit_gcU1XCuGUznG7Rux0YqJUm7T6mF1ZrGZ1ffy-WtbFVQUN387gOUoKkXrvKcHve-FJ0lAt8VChkicuovrTVyKVe5003__mC0)

## 4. Nhiệm vụ của các lớp:
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
![Class Diagram](https://www.planttext.com/api/plantuml/png/V9BFIiGm4CRlUOeSzT0NABBiuWeMHCG_U1usun9CapgP2aLyCWy-agzWiarYkrLx2FIRcTzycSdNn-VQCn3thH5YPy1xkL6jjjep0UjNlCNE4Jyqyat8mqVuqgFdKJyvJQhIlZCm7AaUCY18xxd1g9mxo-ICGIhe7I4m_iUOMTWefLax2wQnJsxP8N6ha1z_xuSEQtd7fEq-1GvNtuQUjOndKj6gfTPsnWs8rz2Yh-LLcC_PY5ebKtkqI5FxnSr5gYr-CgnHHtvieC-aYELSlqK6RVmKVGD3d64m2cMAeUBHqVEbwycNaGKnvCu8V-ovgbQB3Od5odwoVezDZ8cfoHZBzn5Y7KOTNzut0000__y30000)

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
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/b5N1Rjim3BthAuYUitr03aE1Ti1w6OPbmywCH2TQPIcZv0p-jXtsIVk5KOhj9avhExd4fiL7yZsI-lVdxtrCoAcfdKAT0iF7-k12IwIseV46kHqiN-aGE7r_KZhunC6DFZoSh8vOaKysjN2ozszVEFmadHunuHOZ3MPiirSsAzKZmhiFLs7NWlUhePWW1T1Cc0Zu565yzDhz9RcrH8onyvI_0gdUEZsTI0UIsWEjm9I4qEzefWmXucXDdxoKOXEnnHkhs90tLn0ANUfeBrc1ZN3tBIHqy2aq7E57u6SoK8dGs2jofq1-KmoCfCi49BPq971MQ0WLw3toZi0tzPOu5i2HqtGr0jYmduAxJQ576myEsocWrnqtv2JfIxzNuYzI9nOieViIJJwfoOOx6uapgZrfYZ4FfCcpSdPe4RN5QIhgoRQ6XulHwfff9a8vioDFBAxcncdgjUeYbXuUHEe6DEQXZtWSyffNycnRlEMuJ4jvhYpNFSffOInjoPSyYhiB6fCD7b3wmsDDCuLSxArkRom0cj9tCoBZ1eLpPAF8oJGFAPj04Nn8CoJFDS7da6pLzm0O6pMooS7oi0YyGDlTlYo7uOPwgafNvoNNU3oYTRXr1BBRh8zDLLbjvP9PAVH0p6Akym3jobQC-_3RhmfxQN-siRKSPYftOWQILqtkVKuZ5qbAtSjZlYt_0m00__y30000)

## 4. Nhiệm vụ của các lớp:
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
![Class Diagram](https://www.planttext.com/api/plantuml/png/f5H1JiCm4Bpx5JusKYlk4Qeg5H2LAeHI46StMRK1npPh9oX2l8m3J-8BE77gD0uj1tA8bDdrx6Hsak_FhuKs34rPS99ofZMzBXINDG1z9zHUCmeTiCfYkZ6OYrrN4Ao00KGfmci9sYIW99f9H3v8mEegZwkEdT8irugpUYLKQMua5lQGA-YzVFCy0_ODgs0jKsPoAKxFM4fXK78Ew6Sfb2bexUg98_Fa5UDvnWoqIZoQ8bWiqA6jW0xYdOw33qToN8Ut4Tl7Xrf1O6Fh_vMT4jFcVd1TP2FCKLY01RRlG03-hlESmdkKpv2sX5kc-ush7e_fEjVcqXsT-t5ckMUuWxkos0BgIHIqzHDOtUoWOUhP7PP0AZ7JfmOyINovbQKb7-Tl6des7TeLZUmnLaWZubzazgtynp6RpKUP9gEGZxlwL9AJSMrEEV1yJxY-s0R4AeKAWktyGNEqevx2-tzni2uYNQBFlPLZA57uA9A5jRFvlVm0003__mC0)

## 7. Giải thích biểu đồ lớp:
- Employee: Đại diện cho người dùng hệ thống. Nhân viên có thể yêu cầu tạo báo cáo thông qua phương thức requestReport().
- EmployeeReportUI: Giao diện người dùng hiển thị các biểu mẫu nhập thông tin và báo cáo kết quả. Nó có các phương thức để nhận thông tin và hiển thị báo cáo.
- EmployeeReportController: Điều khiển luồng xử lý yêu cầu tạo báo cáo, bao gồm kiểm tra đầu vào, tạo báo cáo và xử lý lưu trữ.
- Report: Thực thể lưu trữ dữ liệu báo cáo. Lớp này có các phương thức để tạo và lưu báo cáo.
- ProjectDatabase: Lưu trữ dữ liệu về các dự án và cung cấp danh sách mã charge number khi cần.
- PayrollData: Lưu trữ thông tin về giờ làm việc và lương của nhân viên, hỗ trợ truy xuất dữ liệu để tạo báo cáo.

# Phân tích ca sử dụng Maintain Employee Information
## 1. Mô tả:
Ca sử dụng này cho phép Quản trị viên Bảng lương duy trì, thêm, thay đổi và xóa thông tin nhân viên khỏi hệ thống.

## 2. Xác định các lớp:
- Boundary: PayrollAdminUI.
- Control: EmployeeController.
- Entity: Employee, EmployeeDatabase.
  
## 3. Biểu đồ Sequence:
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/x5PBRjim4Dtp5BDi5ctsNWG9uYoo260ao076uiXc8v4gEKghitNH8_KA7LgMhOyTIt6GLGLOC2ND6yvxRqZ-_VtdEZ1wBlDCOSBEmm8hxxBiHkV6ci0UvQ5Qkj9gz5NdxVEzIfnb6SDTNcIk8hgjnnbvHPODLxit_V4S6PSOIAb32U7hLI_L31xfHqc1WHtaQ2pB3sYB1iQcJdKZ-XWDzWmMtkK5Gofvf6RZB7ovqVhokT38T3cdZ9WkHi_hIRvFk452gw7mxjLe0aqooIoe0nCR4XQ19BO5quGFlsqZD4H6WjWRUYMGUUPEcxJQyoELeLAOCKYbWhxN1UGwdE6O09P-zeYF66FfMcp9EOroWgaEmAQ-uwKqJsTmwqb4xWQxvNTHS4Judkl8OWT3NAaRIxU1cf1ZfSZ_rFWSK6iJbP-Wnzo48iCAGfaa50BaSiDLx3HTIrqR-aorTnNUpoVfV6TPWD-AFg5lFtHo6mpTDLOKWIXzVtMPBanIUY_BtlGUUS0NWcIDTaKXEkkiFYatBj2dYXWIkRNFBhcdn7dzBdVNS_X8RzUhz7zlVxQtMtkdZXB4pIgfLSRT-ZMMnyOU3T9K6WU9n_BuWFvbJq6xc7VP-s3m6GQtJgpjpMhDuDAZdHca8zFDsKDEGhoEczelXg9E1BwqtvIw5hnujli7003__mC0)

## 4. Nhiệm vụ của các lớp:
- PayrollAdminUI:
  - Đây là lớp giao diện người dùng, hiển thị các biểu mẫu và thông báo, nhận dữ liệu đầu vào từ Payroll Administrator và chuyển tiếp dữ liệu này đến EmployeeController.
- EmployeeController:
  - Lớp điều khiển xử lý các yêu cầu từ PayrollAdminUI, đảm bảo luồng công việc đúng và tương tác với lớp Employee và EmployeeDatabase để thêm, cập nhật hoặc xóa nhân viên.
- Employee:
  - Đại diện cho một thực thể nhân viên trong hệ thống, chứa các thuộc tính và thông tin liên quan đến nhân viên.
  - Được sử dụng trong quá trình thêm hoặc cập nhật thông tin nhân viên.
- EmployeeDatabase:
  - Lớp này chịu trách nhiệm lưu trữ và quản lý dữ liệu nhân viên trong hệ thống.
  - Nó thực hiện các thao tác như thêm, cập nhật, và xóa thông tin nhân viên, và trả về thông tin nhân viên khi được yêu cầu.

## 5. Quan hệ giữa các lớp:
- PayrollAdministrator là actor, tương tác với PayrollAdminUI (lớp giao diện người dùng).
- PayrollAdminUI chuyển tiếp các yêu cầu đến EmployeeController để xử lý logic.
- EmployeeController điều phối các thao tác và sử dụng Employee để xử lý dữ liệu nhân viên.
- EmployeeDatabase là nơi lưu trữ dữ liệu nhân viên và hỗ trợ các thao tác với Employee.

## 6. Biểu đồ lớp:
![Class Diagram](https://www.planttext.com/api/plantuml/png/Z5NRRjim37ttL-Yn0nRatGz5kte52hJ3q2mVe4XCB4mNWvIp6SE-R0_xfFt2A2_EnRAR2KY0a8T797N8_Fdr-uwYnDWwMnI2ZxAII7oM7GPhxxKptb146GEA7psWFmtWDg2xLz44V_Ek5FjWTE_-sN_FKAsVpacqeSRAxgDhREW07fdmWge_L8Tl0wA2A8sb7AI2tnfq5LZ84Zgoh5gbWEY5Ft87CpSX1fn2P6KDEJq47rDzSD4VgVK0kD4oolA8h_XNTdNRC0YE4KQNOXNH-DtxWqjNrqbqgdwA94CYi1tsCzZ1UgXxekQpIXTmi3qTAKu-BntarY7YIzTCUBbpoFtF7HIKaNO5gaKJkq-jsm3cg2Y_Lw3RNfTCKeLsO-7a3h46V0lGrC7377aTMhJTAxz77aZIIknokmhE6IA-RJekSJuRPsBc4Zlmm9F7hKrI72KZ22AFbgf1VMNTcprWzmAn3cFmh7AJY3QIO4wtmpkT575Dj_yHCH9fhfuiOclyCQSF7VVYJR4MavjhiRWTxQ5Ih0ce62sdXCi7cwy3hqcqn4DkVDD6mSjFD1ZIFabzdbW6vrIbU43WHj5otJUCn50tqst3jV3XeLBPWOTZ-NgONrhs6--SBosR8dlXosJ-iOnYYZkkCVqB_0K00F__0m00)

## 7. Giải thích biểu đồ lớp:
- PayrollAdministrator: Người dùng (admin) tương tác với hệ thống thông qua giao diện. Lớp này gọi các phương thức của PayrollAdminUI để thực hiện các thao tác quản lý nhân viên.
- PayrollAdminUI: Lớp giao diện người dùng, chịu trách nhiệm hiển thị các biểu mẫu, nhận thông tin từ người dùng và gửi yêu cầu đến EmployeeController.
- EmployeeController: Lớp điều khiển xử lý các thao tác thêm, cập nhật và xóa thông tin nhân viên. Nó tương tác với Employee để thực hiện các thao tác trên dữ liệu nhân viên và EmployeeDatabase để lưu trữ hoặc truy xuất dữ liệu.
- Employee: Lớp thực thể chứa thông tin về nhân viên (ID, tên, loại nhân viên, lương, v.v.) và các phương thức để tạo ID nhân viên và thiết lập phương thức giao lương.
- EmployeeDatabase: Lớp quản lý cơ sở dữ liệu, thực hiện các thao tác thêm, cập nhật, xóa và tìm kiếm thông tin nhân viên trong hệ thống.

# Phân tích ca sử dụng Run Payroll
## 1. Mô tả:
Ca sử dụng này mô tả cách thức thực hiện bảng lương vào mỗi thứ Sáu và ngày làm việc cuối cùng của tháng.

## 2. Xác định các lớp:
- Boundary: PayrollUI.
- Control: PayrollProcessor, BankSystem.
- Entity: Employee, Paycheck, BankTransaction.
  
## 3. Biểu đồ Sequence:
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/Z5HBKiCm3Dtx55x2WWjqmHHQ5bsHWVO0gYDQJ_tfo6fdSZOM78ahOATn4fB-iagUz9wVP2c_tp_Jm41yi4Q0Oa-oW8gyCI-brKu79eYWGCUQgnnRBOJoZkDhHWho2aFeCj_itlWAiSTKMrIx_FqARhSaS24UghrhzHB-MGL6AyGv9_BfkNCnaJ706XWRwE5HjC5UPkjk8kjY_yCTgSqxpoLaqdZ4N5jO-fXqDrs1KGTpCdk1b9KdSeESFnRkovE5rAQRj6nngIqgeF9ISMD6SI2rXO3lL29TwKbzYycVGphLKYCt2Ogmb_w1obCPIM0u9Tau5d9ToRacL2pdkFT1iv3nEISxc9wiFe2ZV18Oe9b_ch8u4UZACIdvwhBaoi4Hj86rmJgSTPlmG3Brj1fhneC4ce3zWcVrKbogislVdhJZMTFf97JdpFbuqTZkHnFHRdDzQjDgnKD6UoAc4Ks_YZy0003__mC0)

## 4. Nhiệm vụ của các lớp:
- PayrollUI:
  - Cung cấp giao diện người dùng để PayrollAdministrator có thể tương tác với hệ thống.
  - Khi PayrollAdministrator yêu cầu, PayrollUI sẽ gửi yêu cầu bắt đầu quy trình chạy bảng lương đến PayrollProcessor và hiển thị thông báo hoàn thành khi quy trình kết thúc.
- PayrollProcessor:
  - Chịu trách nhiệm chính trong việc thực hiện quy trình tính lương.
- Employee:
  - Chứa thông tin về nhân viên như mức lương, thông tin thời gian làm việc, các khoản khấu trừ và các quyền lợi khác.
  - PayrollProcessor truy xuất các thông tin từ Employee để tính toán mức lương và hoàn thành bảng lương.
- Paycheck:
  - Đại diện cho bảng lương của nhân viên, chứa thông tin về số tiền thanh toán, các khoản khấu trừ và phương thức thanh toán (chuyển khoản ngân hàng hoặc séc).
  - PayrollProcessor tạo Paycheck cho mỗi nhân viên và ghi nhận vào hệ thống.
- BankTransaction:
  - Đại diện cho giao dịch ngân hàng khi nhân viên nhận lương qua chuyển khoản trực tiếp.
  - BankTransaction chứa thông tin về số tiền chuyển và tài khoản ngân hàng của nhân viên.
- BankSystem:
  - Chịu trách nhiệm giao tiếp với hệ thống ngân hàng để thực hiện giao dịch chuyển khoản.
  - Nếu hệ thống ngân hàng không khả dụng, BankSystem sẽ thử gửi lại giao dịch sau một khoảng thời gian nhất định.
    
## 5. Quan hệ giữa các lớp:
- PayrollAdministrator tương tác với PayrollUI để bắt đầu quy trình.
- PayrollUI gửi yêu cầu đến PayrollProcessor để bắt đầu và kết thúc quy trình tính lương.
- PayrollProcessor lấy thông tin từ Employee để tính toán lương.
- PayrollProcessor tạo bảng lương cho nhân viên và ghi nhận vào đối tượng Paycheck.
- PayrollProcessor tạo giao dịch ngân hàng khi thanh toán bằng chuyển khoản.
- BankTransaction gửi giao dịch đến BankSystem để thực hiện thanh toán.

## 6. Biểu đồ lớp:
![Class Diagram](https://www.planttext.com/api/plantuml/png/d5HBJiCm4Dtd55w2H2zWeQf5iEYYKaL1h8qpRQqwTl1CYYB4oLXm9Aw0axXfNDmYy7BcpRmtFtzzV4wGXAEgq5cMCV-a5eXi8MfdjPxcXJ8AoGcoZhsrWEvvCob1480NbvpjhCfRn7iYq-Ci2iyLbbhKmJapAnjbwDuQA03kuQK2f5zP5ivAG3pIsbOO8n9iKcXPwQwaf1W3hlFA3SXjAeC33xWHPllWX44XILcJmjcYrD3tBaXIPdswlZiVOMk0g2u8nbdEsPASJp1m6b50men22rTpTckhPmq3nyPM3f-isqAUyEQGLsqvoDbSbDTTtgi072S7qhOf4bm6OrAmA6nbw9_SVVu23Cs1DZQcYBGTJIYII0VxtrGwaAfKddqgPGSvHx-iaQ28jnHCVdvl792hJq4yHPObptOq6W-kaFlJ9R_9af2zAjfa1zS0U3WatWh3fhUDmujeJv6HpNvWcmJzfl9Mhu8TOB-fddjbNI4QzUdmVczuVt7Oxqqwv7YSF1mY3eUP7QFsaM4I-p878Ks94szi_iPl0000__y30000)

## 7. Giải thích biểu đồ lớp:
- PayrollAdministrator: Lớp này đại diện cho người quản trị. Người quản trị khởi xướng quy trình chạy bảng lương.
- PayrollUI: Lớp giao diện người dùng giúp quản trị viên tương tác với hệ thống để yêu cầu bắt đầu quy trình chạy bảng lương.
- PayrollProcessor: Lớp điều khiển xử lý các công việc liên quan đến việc tính toán và thanh toán bảng lương cho nhân viên.
- Employee: Lớp này chứa thông tin về nhân viên như mức lương, số giờ làm việc và các khoản khấu trừ.
- Paycheck: Lớp này đại diện cho bảng lương của nhân viên. Nó chứa thông tin về số tiền thanh toán, các khoản khấu trừ và phương thức thanh toán.
- BankTransaction: Lớp này đại diện cho giao dịch ngân hàng khi thanh toán bằng chuyển khoản.
- BankSystem: Lớp này giao tiếp với hệ thống ngân hàng để thực hiện giao dịch chuyển khoản.

# Phân tích ca sử dụng Select Payment Method
## 1. Mô tả:
Ca sử dụng này cho phép Nhân viên chọn phương thức thanh toán, bao gồm nhận séc trực tiếp, nhận qua bưu điện hoặc chuyển khoản trực tiếp vào tài khoản ngân hàng đã chỉ định.

## 2. Xác định các lớp:
- Boundary: PaymentMethodUI.
- Control: PaymentMethodController.
- Entity: Employee, PaymentMethod, Address, BankAccount.
  
## 3. Biểu đồ Sequence:
![Sequence Diagram](https://www.planttext.com/api/plantuml/png/b9H1Ri8m44NtFiKe-rw0HLLQkc0HAMh50Tnu41QExTeJ46VheaVg5Mex1f8qf2sB29F_P-PDVlZw-7pmn1srZMAy9kDW6Q-CsV2ZhANbcg2e-Ab1JINIpeZDkW3kOREUqJmPJSueXIvfhyUXvxcnofmGaoWSPYecILKE5KiX77gVxiNlmxkFNE-NTMrQJKcHpumbHBYx3momWBMM93cX1zirX2Pr18yAQv96iw0BwYj5SBtWUukURdjwwk0DSCb4Jk810JCuIBqrhk794JNZDfKp1obw1i69ZsedYfNqLl7JPHvZOqq_DVfvwtdOCJVZAYvVrdjeRP55A1Y4px1nLOPgh_XZ2MIWiDdFK7c4ekHIpTPA4EUbykwv9ja4m7afVTcmMWn3dksokTlgEOuc3fuXLjA5yM65rdX9VyTv2y43WHHA_SgKj34L4qLpWCTWoSAxeF-JJdH48XCnr68ok1iRSjTBuL7I3ZGUnz7fmBhtQn7ds4hNt7v7s4De6FzwlW400F__0m00)

## 4. Nhiệm vụ của các lớp:
- PaymentMethodUI:
  - Hiển thị giao diện người dùng cho Actor để lựa chọn phương thức thanh toán.
  - Yêu cầu Actor cung cấp thông tin cần thiết (địa chỉ hoặc thông tin ngân hàng) nếu cần thiết.
  - Truyền các lựa chọn và thông tin từ Actor tới PaymentMethodController để xử lý.
- PaymentMethodController:
  - Điều khiển toàn bộ quy trình lựa chọn phương thức thanh toán.
  - Nhận dữ liệu từ PaymentMethodUI và quyết định hành động cần thực hiện (lưu thông tin, cập nhật phương thức thanh toán, v.v.).
  - Quản lý các logic liên quan đến phương thức thanh toán (chẳng hạn như yêu cầu thông tin bổ sung như địa chỉ hoặc thông tin ngân hàng).
  - Cập nhật thông tin phương thức thanh toán trong lớp Employee sau khi quá trình lựa chọn hoàn tất.
- Employee:
  - Lưu trữ thông tin nhân viên, bao gồm phương thức thanh toán của nhân viên.
  - Được cập nhật khi phương thức thanh toán của nhân viên thay đổi (do lựa chọn của Actor).
- PaymentMethod:
  - Lưu trữ thông tin về phương thức thanh toán của nhân viên (ví dụ: "pick up", "mail", hoặc "direct deposit").
  - Được cập nhật bởi PaymentMethodController dựa trên lựa chọn của Actor.
- Address:
  - Lưu trữ thông tin địa chỉ của nhân viên nếu họ chọn phương thức thanh toán qua bưu điện (Mail).
  - Được PaymentMethodController cập nhật khi Actor cung cấp địa chỉ cho phương thức "Mail".
- BankAccount:
  - Lưu trữ thông tin tài khoản ngân hàng của nhân viên nếu họ chọn phương thức thanh toán qua chuyển khoản ngân hàng (Direct Deposit).
  - Được PaymentMethodController cập nhật khi Actor cung cấp thông tin ngân hàng.

## 5. Quan hệ giữa các lớp:
- Actor tương tác trực tiếp với PaymentMethodUI để lựa chọn phương thức thanh toán.
- PaymentMethodUI chuyển yêu cầu từ Actor sang PaymentMethodController để xử lý và cập nhật thông tin.
- PaymentMethodController cập nhật thông tin trong Employee, PaymentMethod, Address, và BankAccount dựa trên lựa chọn của Actor.
- Các lớp PaymentMethod, Address, và BankAccount chứa thông tin về phương thức thanh toán, địa chỉ gửi thư, và tài khoản ngân hàng của Employee.

## 6. Biểu đồ lớp:
![Class Diagram](https://www.planttext.com/api/plantuml/png/V9D1ReCm44NtFeMLLRl81LXKeL4NB9fKQdk02PwcACPsxQ4IgdAoBdgaNg4GmDYGuXMU_tbZVuRVxv-D8x1KbP8n0_a9ZiXNJr2NgEWHwLsB5VzYl5cv1ETu9FLAjyfBwQKscF1dieKwNiGpEmVaXz98NIF6qA4QyR0lPYBYTKj1YLVA9ZnT4Xysi84G5frBUDez1D81r2dDSrqfIlZzk1dlSYM7ryoVN1JEIAWZUM-eqChTtFOUYnyLEcgQ5wq0CbDlkb6lmxTQaTLIelLDAYE0C79vk8FFcUB1_Nqzo955f4cGUK7rf6HqCoLogyKOkcS68NakTFjTLHxGJbXjmhlmypMaD2Tj-NfzDysLJNEUUSPus7-njUyC8xPeYkTboJaCpf8dd1u_uVCsaJHmes88OXjKelrR_m000F__0m00)

## 7. Giải thích biểu đồ lớp:
- PaymentMethod: Chứa thông tin về phương thức thanh toán của nhân viên (chẳng hạn như "pick up", "mail", hoặc "direct deposit").
- Employee: Chứa thông tin của nhân viên, bao gồm ID nhân viên, tên, phương thức thanh toán (PaymentMethod), địa chỉ (Address), và thông tin tài khoản ngân hàng (BankAccount).
- PaymentMethodUI: Cung cấp giao diện người dùng cho Actor để lựa chọn phương thức thanh toán. Giao diện sẽ yêu cầu Actor cung cấp thông tin bổ sung (nếu cần).
- PaymentMethodController: Điều khiển quá trình thay đổi phương thức thanh toán cho nhân viên. Cập nhật và lưu thông tin về phương thức thanh toán, địa chỉ, và tài khoản ngân hàng của nhân viên.
- Address: Lưu trữ địa chỉ gửi thư cho phương thức thanh toán qua bưu điện (Mail).
- BankAccount: Lưu trữ thông tin tài khoản ngân hàng nếu phương thức thanh toán là chuyển khoản ngân hàng (Direct Deposit).

# Code java mô phỏng ca sử dụng Maintain Timecard.
## Các lớp có trong code mô phỏng: 
- Timecard Class: Đại diện cho thẻ chấm công của nhân viên. Bao gồm các phương thức để thêm giờ làm, kiểm tra tính hợp lệ của giờ làm và nộp thẻ chấm công.
- Employee Class: Đại diện cho nhân viên, có thể tạo thẻ chấm công, thêm giờ làm và nộp thẻ chấm công.
- TimecardSystem: Nơi mô phỏng các bước trong ca sử dụng.

## Các bước thực hiện: 
1. Nhân viên tạo thẻ chấm công cho một kỳ lương.
2. Nhân viên thêm giờ làm cho các dự án khác nhau.
3. Nhân viên nộp thẻ chấm công và không thể chỉnh sửa sau khi nộp.
4. Hệ thống kiểm tra tính hợp lệ của các giờ làm và ngừng cho phép chỉnh sửa sau khi đã nộp thẻ.

## Code của từng lớp: 
- Timecard Class:
```
  class Timecard {
    private Date startDate;
    private Date endDate;
    private Map<String, Integer> hoursWorked = new HashMap<>();
    private boolean isSubmitted = false;

    public Timecard(Date startDate, Date endDate) {
        this.startDate = startDate;
        this.endDate = endDate;
    }

    public Date getStartDate() {
        return startDate;
    }

    public Date getEndDate() {
        return endDate;
    }

    public void addHours(String chargeNumber, int hours) throws IllegalArgumentException {
        if (isSubmitted) {
            throw new IllegalStateException("Timecard already submitted, cannot add hours.");
        }
        if (hours > 24) {
            throw new IllegalArgumentException("Invalid number of hours for a single day.");
        }
        if (hoursWorked.containsKey(chargeNumber)) {
            hoursWorked.put(chargeNumber, hoursWorked.get(chargeNumber) + hours);
        } else {
            hoursWorked.put(chargeNumber, hours);
        }
    }

    public void submitTimecard() throws IllegalStateException {
        if (isSubmitted) {
            throw new IllegalStateException("Timecard is already submitted.");
        }
        this.isSubmitted = true;
        System.out.println("Timecard submitted on: " + new Date());
    }

    public Map<String, Integer> getHoursWorked() {
        return hoursWorked;
    }

    public boolean isSubmitted() {
        return isSubmitted;
    }

    @Override
    public String toString() {
        return "Timecard from " + startDate + " to " + endDate + ", Hours: " + hoursWorked;
    }
}
```

- Employee Class:
```
class Employee {
    private String name;
    private Timecard currentTimecard;
    private static final int MAX_HOURS_PER_DAY = 8;

    public Employee(String name) {
        this.name = name;
    }

    public void createTimecard(Date startDate, Date endDate) {
        this.currentTimecard = new Timecard(startDate, endDate);
        System.out.println("Timecard created for " + name + ": " + currentTimecard);
    }

    public void addHours(String chargeNumber, int hours) {
        try {
            currentTimecard.addHours(chargeNumber, hours);
            System.out.println("Added " + hours + " hours for " + chargeNumber);
        } catch (IllegalArgumentException | IllegalStateException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }

    public void submitTimecard() {
        try {
            currentTimecard.submitTimecard();
            System.out.println("Timecard successfully submitted.");
        } catch (IllegalStateException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }

    public Timecard getCurrentTimecard() {
        return currentTimecard;
    }

}
```

- TimecardSystem (chứa hàm main):
```
public class TimecardSystem {
    public static void main(String[] args) {
        // Mô phỏng hệ thống
        Employee employee = new Employee("John Doe");

        // Bước 1: Tạo bảng chấm công cho kỳ trả lương hiện tại
        Date startDate = new GregorianCalendar(2024, Calendar.NOVEMBER, 1).getTime();
        Date endDate = new GregorianCalendar(2024, Calendar.NOVEMBER, 7).getTime();
        employee.createTimecard(startDate, endDate);

        // Bước 2: Thêm số giờ làm việc cho các mã chi phí khác nhau
        employee.addHours("Project A", 5);
        employee.addHours("Project B", 7);
        employee.addHours("Project C", 3);

        // Bước 3: Cố gắng gửi bảng chấm công
        employee.submitTimecard();

        // Bước 4: Thử sửa đổi sau khi đã gửi (nên thất bại)
        employee.addHours("Project A", 2); // Điều này sẽ thất bại vì bảng chấm công đã được gửi.

        // Hiển thị trạng thái cuối cùng
        System.out.println(employee.getCurrentTimecard());
    }
}
```
## Kết quả mô phỏng: 
![image](https://github.com/user-attachments/assets/5806011a-9c6d-4abc-a2a8-680159e7daa8)
