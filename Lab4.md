# Thiết kế các ca sử dụng cho hệ thống "Payroll System"

## I. Ca sử dụng: Maintain Timecard

### 1. Mô tả sự tương tác giữa các đối tượng thiết kế
Tác nhân liên quan:
- Employee (Nhân viên): Người dùng dùng hệ thống để nhập giờ làm việc.
- Project Management (Quản lý dự án): Quản lý thông tin liên quan đến dự án.

Các đối tượng chính trong hệ thống:
- TimecardUIHandler: Giao diện xử lý nhập dữ liệu cho nhân viên.
- TimecardService: Xử lý nghiệp vụ.
- Database: Lưu trữ thông tin.

### 2. Đơn giản hoá sơ đồ trình tự bằng hệ thống con:
![](https://www.planttext.com/api/plantuml/png/f9F1IWCn48RlUOevwg4lu44AHQnGYs05hsasR2ARx99D5teK3nx49n1XYtYpu44GDeY7WE-H9_0Ld89MkxjQnHn2cCdtp_1FykgUkxcbnavKGYYpgO4TbINfb7EIOLWocL5jOIGLPzH4HtjzggE4czRi8JU5PAlaWKbFEBFxLDEOAwuj8HyLeBFT58Oj68fGpJE8PN3NaFXIGO77SqQQbxyel1T7_ZYuEN9FonHiM7-dGAIXUcHWGpLBGGLt9JT9dKR1HiSeEGZLxHGYgWNaViO4z0GrCOVXH8svoKcJwRIsDZAXke4YkDEwGgEHRypfenLd6gm8xgAkiTRP7bANUXM3mfUW_sdvuEL-iWmJGXCBkpW5-Ha3NElQQq5-MVy7ya-6Mk4VT0nZZoy4poNEcoqYXEk8T75R_9Ct0000__y30000)

### 3. Mô tả hành vi lưu trữ:
- Nhập giờ làm việc: Nhân viên (Employee) bắt đầu quy trình bằng cách nhập số giờ làm việc vào hệ thống thông qua giao diện người dùng (TimecardUIHandler).
- Xử lý Timecard: Khi giờ làm việc được nhập, TimecardUIHandler sẽ gửi yêu cầu đến TimecardService để xử lý Timecard (có thể là tìm kiếm hoặc tạo mới một bản Timecard nếu chưa có).
- Lấy danh sách Charge Numbers: Sau khi xử lý Timecard, TimecardService sẽ yêu cầu từ ProjectManagement danh sách các Charge Numbers (mã số dự án).
- Trả về Charge Numbers: ProjectManagement trả về danh sách Charge Numbers cho TimecardService.
- Hiển thị Charge Numbers: TimecardService trả kết quả lại cho TimecardUIHandler, và giao diện người dùng hiển thị danh sách các Charge Numbers cho nhân viên.

### 4. Mô tả luồng sự kiện:
- Nhập giờ làm việc: Employee nhập giờ làm việc vào TimecardUIHandler.
- Xử lý Timecard: TimecardUIHandler gọi TimecardService để xử lý Timecard (tìm kiếm hoặc tạo mới).
- Lấy danh sách Charge Numbers: TimecardService yêu cầu danh sách Charge Numbers từ ProjectManagement.
- Trả về Charge Numbers: ProjectManagement trả về danh sách Charge Numbers cho TimecardService.
- Hiển thị Charge Numbers: TimecardService gửi danh sách Charge Numbers lại cho TimecardUIHandler, giao diện hiển thị cho nhân viên.
- Chọn Charge Number và nhập giờ làm việc: Nhân viên chọn Charge Number và nhập giờ làm việc.
- Lưu Timecard: TimecardUIHandler gửi yêu cầu lưu Timecard đến TimecardService.
- Gửi Timecard (nếu có): Nếu nhân viên quyết định gửi Timecard, họ sẽ gửi yêu cầu gửi Timecard từ TimecardUIHandler đến TimecardService.
- Thông báo thành công: Sau khi gửi Timecard thành công, TimecardService trả về thông báo thành công cho TimecardUIHandler.

### 5. Lý do thiết kế: 
Quy trình thiết kế trên nhằm đảm bảo tính chính xác, hiệu quả, và an toàn trong việc ghi nhận và lưu trữ giờ làm việc của nhân viên. Nó giúp hệ thống dễ dàng quản lý và theo dõi dữ liệu thời gian làm việc, đồng thời cải thiện sự giao tiếp và tích hợp giữa các bộ phận trong tổ chức.

## II. Ca sử dụng: Login


