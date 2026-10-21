# BÀI LÀM – ÔN TẬP NGÀY 2

-  **Họ tên:** Đoàn Tuấn Long

-  **Lớp:** CNTT3

-  **Link repository:**

-  **Hệ điều hành (Windows/macOS):** Windows

  

## Bài 1. Lọc log thủ công

### Lệnh đã chạy

```shell
Get-Content .\logs\access.log | Select-String "ERROR" >.\logs\error_report.txt
```

### 2 dòng lỗi đầu tiên trong error_report.txt
```text
2025-10-18 08:17:59 [ERROR] Khong tim thay trang /lich-thi (404)
2025-10-18 08:25:55 [ERROR] Het thoi gian cho (timeout)
```
## Bài 2. Đếm bằng pipeline

### Lệnh
```Powershell
(Get-Content .\logs\access.log | Select-String "WARNING").count
(Get-Content .\logs\payment.log | Select-String "ERROR").count
```
### Kết quả đếm (Windows: giá trị Count; macOS: con số in ra)
```text

WARNING trong access.log: 4

ERROR trong payment.log: 3

```

## Bài 3. Chạy script auto_warning (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```Powershell

.\auto_warning.ps1

```

### Nội dung file logs/warning_report.txt

```text
=== CANH BAO THANH TOAN ===

2025-10-18 08:13:31 [WARNING] Lop GT01 sap du si so
2025-10-18 08:21:27 [WARNING] Lop GT01 sap du si so
2025-10-18 08:45:15 [WARNING] Thoi gian tai trang cham
2025-10-18 09:21:27 [WARNING] Video bai giang dung luong lon
```

## Bài 4. Báo cáo tổng hợp

### Các lệnh đã chạy

```Powershell
(Get-Content ".\logs\access.log" | Select-String "error").count >> ".\logs\tong_hop_ngay_2.txt"
(Get-Content ".\logs\payment.log" | Select-String "warning").count >> ".\logs\tong_hop_ngay_2.txt"
```

### Nội dung file logs/tong_hop_ngay2.txt

```text
=== TONG HOP ACCESS LOG ===
6
5

```

## Bài 5. Câu hỏi ngắn
- **a)** Lệnh ... > file và ... >> file khác nhau thế nào?
  -   Lệnh `...>`: là ghi đè, sẽ xóa hết dữ liệu trước đó.
  -   Lệnh `...>>`: là ghi nối, sẽ ghi tiếp vào dữ liệu trước đó.
- **b)** Ở Bài 4, nếu lệnh thứ hai (nối các dòng ERROR) dùng > thay cho >>, nội dung file tong_hop_ngay2.txt sẽ thay đổi ra sao?
  - Nếu sử dụng `>` thay cho `>>` thì sẽ bị mất đi dòng `=== TONG HOP ACCESS LOG ===`
- **c)** Vì sao trong script nên dùng đường dẫn tương đối logs/payment.log thay vì đường dẫn tuyệt đối trên máy mình (ví dụ C:/Users/An/Desktop/...)?
  - Vì đường dẫn tương đối sẽ sử dụng trên thư mục đang đứng hiện tại sẽ phù hợp cho việc chia sẻ với nhiều người. Khác với đường dẫn tuyệt đối khi chỉ tối ưu cho duy nhất một máy.

## Tự chấm (điền sau khi có đáp án)

  

-  **Điểm tự chấm:** ..../100

-  **Lỗi mình đã mắc và cách sửa:**