# ⚡ EVoltStation – EV Charging Management System (Backend API)

> Forked from [DatNguyenSE/EVStation-API](https://github.com/DatNguyenSE/EVStation-API) · Frontend: [EVStation-Client](https://github.com/DatNguyenSE/EVStation-Client)
> 🔗 **Live demo:** https://evoltstation.io.vn

EVoltStation is a platform for operating electric-vehicle charging stations. Drivers find stations on a map, reserve a charging slot, start a session by scanning a QR code and pay from an in-app wallet. Operators and managers monitor charging posts in real time, handle incidents and track revenue.

## 🚀 Features

- 🗺️ **Station map & reservations:** find nearby stations, filter compatible charging posts and reserve a time slot.
- ⚡ **QR charging flow:** scan the post's QR code → authenticate → start charging → automatic payment at the end of the session.
- 📡 **Real-time session monitoring:** battery level, cost and time remaining are pushed to the driver over SignalR.
- 💳 **E-wallet:** top up through VNPay and view transaction history.
- ⏱️ **Operating rules:** overstay fees, reservation no-show handling and account restrictions, processed by background services.
- 🚶 **Walk-in drivers:** charge without an account, then register and keep the session history.
- 🤖 **Support chatbot** over SignalR.
- 📊 **Admin & manager dashboards:** revenue analytics, post status, staff assignments and incident reports.

## 🛠 Tech stack

| Layer | Technologies |
|---|---|
| Backend | .NET 9 Web API, Entity Framework Core, SignalR, ASP.NET Identity (JWT), BackgroundService |
| Frontend | Angular, Tailwind CSS, DaisyUI, Leaflet, Chart.js |
| Database | Microsoft SQL Server |
| Integrations | VNPay, Cloudinary, MailKit, QRCoder |

## 👥 Roles

| Role | Main capabilities |
|---|---|
| Driver | Reserve slots, charge via QR, wallet, session history |
| Operator / Technician | Monitor posts, handle incidents and emergency stops |
| Manager | Station operations, staff roster, revenue reports |
| Admin | System configuration, pricing, accounts |

## ⚙️ Getting started

```bash
git clone https://github.com/DatNguyenSE/EVStation-API.git
cd EVStation-API
# Update the connection string in appsettings.json
dotnet ef database update
dotnet run
```

Frontend setup: see [EVStation-Client](https://github.com/DatNguyenSE/EVStation-Client).
