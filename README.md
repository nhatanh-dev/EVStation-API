# ⚡ EvoltStation – EV Charging Management System (Backend API)

> Fork từ repository của nhóm: [DatNguyenSE/EVStation-API](https://github.com/DatNguyenSE/EVStation-API) · Frontend: [EVStation-Client](https://github.com/DatNguyenSE/EVStation-Client)
> 🔗 **Live demo:** https://evoltstation.io.vn

EvoltStation là nền tảng quản lý trạm sạc xe điện: đặt chỗ, sạc bằng QR, ví điện tử, giám sát phiên sạc thời gian thực và dashboard quản trị.

## 👤 Vai trò & đóng góp

**Backend Developer** · [@nhatanh-dev](https://github.com/nhatanh-dev) · 10/2025 – 11/2025

- **Luồng phiên sạc realtime:** xây dựng luồng bắt đầu → theo dõi → kết thúc → xuất hóa đơn; `ChargingHub` (SignalR) đẩy % pin, chi phí và thời gian còn lại xuống client; hỗ trợ kết nối lại khi client mất kết nối.
- **Xử lý nền:** tính phí chiếm chỗ sau khi sạc, theo dõi lịch đặt chỗ, cơ chế nợ của tài xế, tự động khóa/mở tài khoản khi vi phạm quy định kèm email thông báo (`BackgroundService`).
- **Khách vãng lai:** xác thực QR trụ sạc, gợi ý đăng ký tài khoản sau phiên sạc và đồng bộ dữ liệu, cập nhật giấy tờ xe.
- **Nghiệp vụ vận hành:** quản lý trạm & trụ sạc (sinh QR code), phương tiện, phân ca nhân viên, lịch sử phiên sạc theo vai trò, thống kê doanh thu.
- **Dữ liệu & triển khai:** EF Core migrations, seed dữ liệu demo, cấu hình triển khai lên VPS.

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

Frontend: xem hướng dẫn tại [EVStation-Client](https://github.com/DatNguyenSE/EVStation-Client).
