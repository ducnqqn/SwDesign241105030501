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
