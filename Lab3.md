## 1. Subsystem context diagrams
# a. Hệ thống con BankSystem:
  ![](https://www.planttext.com/api/plantuml/png/l991JiCm44NtFiMegnOrBUi8eQeK93O8gITmd2b4sEF8CnQAW9Enu4XS0Jk9W1JOih4bVt_zvpz-VttRiEWWqLbbh6Q6Mzq5R-s59yax1dXI0EirjC4RP4wwGvBvGhqerP1WE6Y3SBtLzB3lMD3r1WcQ-83XAbBDSssCZoGtqLKOIjXBQEXk2Thbqn9sFbOMbuD96sayxRHW4jAwA67hlKLDEN60_DUmIzTQto6EBv_sD50ezREseZYVj592PEG_BXvbvCjjdNXO7IkpqzNgPDQR9WZ9CaxeAsHKVWze-DDGGzMfxwndpqK14_P-qgajXiT6xfNQ8DNvqtm0003__mC0)
# Giải thích:
- PayrollController:
  - Chức năng: Quản lý và điều khiển quy trình thanh toán lương cho nhân viên.
  - Phương thức: processPayment(): Bắt đầu quá trình thanh toán tiền lương cho nhân viên.
  - Mối quan hệ: Sử dụng IBankSystem để thực hiện chuyển tiền và cập nhật thông tin thanh toán qua EmployeePayment.
- IBankSystem:
  - Chức năng: Định nghĩa các phương thức cần có để tương tác với hệ thống ngân hàng, cụ thể là chuyển tiền.
  - Phương thức: transferFunds(accountNumber: String, amount: Double, transactionDate: Date): Boolean: Chuyển tiền vào tài khoản ngân hàng.
- BankSystem:
  - Chức năng: Lớp thực thi giao diện IBankSystem, chịu trách nhiệm thực hiện các giao dịch chuyển tiền thực tế vào tài khoản ngân hàng.
  - Phương thức: transferFunds(accountNumber: String, amount: Double, transactionDate: Date): Boolean: Triển khai phương thức của IBankSystem để chuyển tiền.
- EmployeePayment:
  - Chức năng: Đại diện cho một khoản thanh toán của nhân viên, chứa thông tin về tiền lương và các giao dịch liên quan.
  - Mối quan hệ: Được PayrollController cập nhật và được xử lý bởi PayrollSystem.
- PayrollSystem:
  - Chức năng: Quản lý các khoản thanh toán và quy trình xử lý thanh toán cho nhân viên.
  - Mối quan hệ: Xử lý các đối tượng EmployeePayment, giúp tạo và cập nhật các khoản thanh toán cho nhân viên.
    
# b. Hệ thống con PrintService:
![](https://www.planttext.com/api/plantuml/png/l991JWCn34NtEOKrAuewBMmZX2fWqrsbdY2Tc18fJGRReHeLJiQ28t45aau7QLhMh2BRxtyxJhu_lnOiXYJjl6gyOOQLwIXw_nY3b1C93WfWFWV2ruGikSxUjLSJzQ6K2uBqR1g4vOfoi4PwSpagahOa1XfthOyTuj9gM4kkRAV0nXlgD3p5jF4u1OisDU9Yu24tqV0GeqSJIhFJVF_LftTKwd8XTNr_TbyDYP7_GAlRweYVt3BO41hfsMEckfdDhd-XCxc6BGQaiM2m70_WkDy4MjXqQZpUtNjTN_3bwKmZ37idBqejCDZo2tu0003__mC0)
# Giải thích
- PayrollController
  - Chức năng: Quản lý quy trình yêu cầu phiếu lương (payslip) cho nhân viên.
  - Phương thức: requestPayslip(): Phương thức này yêu cầu tạo và in phiếu lương cho nhân viên.
  - Mối quan hệ: Sử dụng giao diện IPrintService để yêu cầu in phiếu lương và tạo đối tượng Payslip.
- IPrintService
  - Chức năng: Định nghĩa các phương thức cần có để in phiếu lương của nhân viên.
  - Phương thức: printPayslip(employeeId: String, salary: Double, deductions: Double): Boolean: In phiếu lương của nhân viên, bao gồm ID nhân viên, lương và các khoản khấu trừ.
- PrintService
  - Chức năng: Lớp thực thi giao diện IPrintService, thực hiện công việc in phiếu lương cho nhân viên.
  - Phương thức: printPayslip(employeeId: String, salary: Double, deductions: Double): Boolean: Triển khai phương thức của IPrintService để in phiếu lương.
- Payslip
  - Chức năng: Đại diện cho phiếu lương của nhân viên, chứa thông tin về lương, các khoản khấu trừ và các chi tiết khác liên quan đến việc thanh toán.
  - Mối quan hệ: PayrollController tạo ra (creates) các đối tượng Payslip, và Payslip được in (printed) bởi PrintService.
    
# c. Hệ thống con ProjectManagementDatabase:
![](https://www.planttext.com/api/plantuml/png/t5D1JiCm4Bpd5Jws4kq38eGgQ2LwGAh4WVFMMT9GnuwyQw48U1a7diGNS9mKhAHOdF75acTcPtPjVxv_h8Z1igjL9loI2eZ43bfhbBenchiThNW9Q5WbygPkb6aHTzOyeUGrCCpcFmpN5C0dyDOuImFwbeMjqeps4IIAxK2w0mqbrgX3hJqGZXnZ9npSjqKkxjbMkfpd8Y8aWqp55wBf2V7HeIC_67j4VxWsRg_GcrmRen1qtCimiF_HnlUzGjirSGxfFSuWqsdqbQTlQR6uIbryBXmX1Ms2TVcwN2R6dlUF32IJUAxua8WoQhhp3_EclsZw05u3KYATSe_XMEAvx7CTVsT6HOcgKbEsGbtu7_e5003__mC0)

# Giải thích:
- PayrollController:
  - Là lớp điều khiển (controller) chính, chịu trách nhiệm lấy dữ liệu dự án của nhân viên và cập nhật số giờ làm việc cho các dự án.
  - Nó sử dụng IProjectManagementDatabase để truy xuất và cập nhật dữ liệu.
- IProjectManagementDatabase
  - Đây là một giao diện (interface) định nghĩa các phương thức để lấy dữ liệu dự án của nhân viên và cập nhật giờ làm việc.
  - Cả PayrollController và ProjectManagementDatabase đều tương tác với giao diện này.
- ProjectManagementDatabase
  - Là lớp thực thi giao diện IProjectManagementDatabase, cung cấp các phương thức để truy vấn và cập nhật thông tin về dự án.
- EmployeeProject
  - Theo dõi các dự án mà nhân viên tham gia.
- Employee
  - Là thực thể cơ bản về nhân viên.
- Project
  - Là thực thể cơ bản về dự án.
- EmployeePayment
  - Liên quan đến thanh toán cho nhân viên dựa trên giờ làm việc.

## 2. Analysis class to design element map
|  Analysis Class | Design Element |  
|-----------------|----------------|
| LoginForm | LoginForm|
| MaintainTimecardForm | MainEmployeeForm |
| TimecardController | TimecardController |
| PayrollController | PayrollController |
| PayCheck | PayCheck |
| SystemClockInterface | SystemCLockInterface |
| BankService | BankService |
| PayrollController | PayrollControllerImplement |
| Employee | EmployeeEntity |
| Timecard | TimecardEntity |
| Payroll | PayrollProcessor |
| BankTransaction | BankTransactionProcessor |
| PaymentUI | PaymentUIComponent |
| PrintService | PrintServiceProcessor |

## 3. Design element to owning package map
|  Design Element | "Owning" Package |  
|-----------------|----------------|
| LoginForm | Middleware::Security::GUIFramwork |
| MainEmployeeForm | Applications::Employee Activities |
| TimecardController | Applications::Employee Activities |
| SystemClockInterface | Applications::Payroll |
| PayrollController | Applications: Payroll |
| PayCheck | Business Services::Payroll Artifacts |
| BankService | Business::Banking |
| EmployeeEntity | Data Access::Employee Management |
| TimecardEntity | Data Access::Employee Management |
| PayrollProcessor | Business Services::Payroll Processing |
| BankTransactionProcessor | Business Services::Banking |
| PaymentUIComponent | Middleware::User Interface Components |
| PaymentUIComponent | Middleware::Print Services |

## 4. Architectural layers and their dependencies
![](https://www.planttext.com/api/plantuml/png/V58nRiCm3Dpr2a9xFj2XI80i0JBLo5HqO6N65gB81aKRC8g-h4EVr2_KSkn4Cefwu_5El3luv-jx6mHPkgjJuM9zYunNQD5SiA921aV0P4If6G9z2iHmy49yHaDmn85OmuU2yNkDosDJMNywl046IEOROO-XVc-GovcGp3V22xKDoxnT1lMP6DYrhRC6nJOUujjcvM6wLn3trj3qIWgiNAIqDPZwINaPaZdReo3iZA4G_kWbweALXeTxDGzeyILOD1tV7IrZF9Dq2PlDSnOBda3Nw4j70Lp4jKgQdUZhU55o9Z7rA2d7GrejRK_qB6NaLkI9KKOsJokjLEOWYl9CKTMZi-MawiPTukf_6PEmfNwMPVvIuQEWDCtDtonIM_Bb-7V_0W00__y30000)
