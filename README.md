# ⚡ EvoltStation – EV Charging Management System (Backend API)

> 🍴 Đây là bản fork từ repo nhóm [DatNguyenSE/EVStation-API](https://github.com/DatNguyenSE/EVStation-API) · Frontend: [EVStation-Client](https://github.com/DatNguyenSE/EVStation-Client)
> 🔗 **Live demo:** https://evoltstation.io.vn

EvoltStation là nền tảng quản lý trạm sạc xe điện: đặt chỗ, sạc bằng QR, ví điện tử, giám sát phiên sạc thời gian thực và dashboard quản trị.

## 👤 Phần tui làm (nhatanh-dev)

Khoảng 37% commit backend (58/156, 10/2025 → 11/2025). Các phần chính:

- **Luồng phiên sạc lõi** (bắt đầu → theo dõi trực tiếp → dừng → hóa đơn): tui tạo `ChargingHub` (SignalR) và `ChargingSimulationService` để đẩy % pin, chi phí và thời gian còn lại xuống client theo thời gian thực, thêm API reconnect khi client mất kết nối.
- **Phí & luật vận hành chạy nền:** phí chiếm chỗ sau khi sạc xong (`IdleFeeService`), theo dõi reservation (`ReservationMonitorService`), cơ chế nợ tài xế, tự động ban/unban khi vi phạm luật đặt chỗ, có gửi email thông báo. Tất cả chạy bằng `BackgroundService`.
- **Tài xế vãng lai (walk-in):** validate mã QR trụ sạc, gợi ý đăng ký tài khoản sau phiên sạc và đồng bộ dữ liệu khách, upload giấy tờ xe.
- **Quản lý vận hành:** Station / Charging Post (QR code bằng QRCoder), Vehicle & VehicleModel, phân ca nhân viên (Assignment roster), lịch sử phiên sạc theo từng vai trò, thống kê doanh thu cho Admin/Manager.
- **Dữ liệu & triển khai:** EF Core migrations + seed dữ liệu demo, cấu hình CORS và deploy lên VPS.
- Phía frontend (Angular) tui làm thêm dashboard sạc realtime (SignalR client) và màn hình đăng ký walk-in.

Phần thanh toán VNPay và ví điện tử do thành viên khác trong nhóm phụ trách.

## 🛠 Tech stack

| Thành phần | Công nghệ |
|---|---|
| Backend | .NET 9 Web API, Entity Framework Core, SignalR, ASP.NET Identity (JWT), BackgroundService |
| Frontend | Angular, Tailwind CSS, DaisyUI, Leaflet, Chart.js |
| Database | Microsoft SQL Server |
| Tích hợp | VNPay, Cloudinary, MailKit, QRCoder |

## 🚀 Tính năng chính

- 🗺️ **Đặt chỗ & bản đồ:** tìm trạm trên bản đồ, lọc trụ sạc tương thích, giữ chỗ theo khung giờ.
- ⚡ **Sạc bằng QR:** quét QR → xác thực → kích hoạt sạc → trừ tiền tự động.
- 💳 **Ví điện tử:** nạp tiền qua cổng thanh toán, lịch sử giao dịch.
- 🤖 **Chatbot hỗ trợ** qua SignalR.
- 📊 **Admin dashboard:** doanh thu, trạng thái trụ sạc, xử lý sự cố realtime.

## ⚙️ Chạy local

```bash
git clone https://github.com/DatNguyenSE/EVStation-API.git
cd EVStation-API
# Cập nhật connection string trong appsettings.json
dotnet ef database update
dotnet run
```

Frontend: xem hướng dẫn ở [EVStation-Client](https://github.com/DatNguyenSE/EVStation-Client).
