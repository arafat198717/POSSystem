# POSSystem

A full-featured offline-first Point of Sale desktop application built with **C# WinForms (.NET 10)**, backed by a **PHP REST API** for multi-branch sync. Built for retail use in Saudi Arabia, with ZATCA (Phase 1) e-invoicing QR support.

## Features

- 🖥 **POS / Checkout** — cart, discounts, multiple payment methods, receipt printing
- 📦 **Product Management** — full CRUD, category support, Excel bulk import/export
- 🧾 **Invoices** — history, reprint, void
- 👥 **Customer Credit / Debt Tracking** — record debt, payments, balance history, printable payment receipts
- 📊 **Reports** — daily sales, monthly summary, stock report, invoice detail, customer debt report — all exportable to Excel
- 📈 **Dashboard** — at-a-glance sales and stock overview
- 🔄 **Multi-Branch Sync** — bidirectional sync with a central PHP REST API, online/offline indicator, auto-sync
- 🔐 **Role-Based Access Control** — Admin vs Cashier permissions enforced at UI and navigation level
- 👤 **User Management** — add/edit/deactivate users, bcrypt password hashing
- 🇸🇦 **ZATCA QR Code (Phase 1)** — TLV-encoded base64 QR on every printed receipt
- 💾 **Database Backup & Restore** — one-click backup of local SQLite database

## Tech Stack

**Client**
- C# / .NET 10 — WinForms
- SQLite (local-first storage)
- EPPlus — Excel import/export
- BCrypt.Net-Next — password hashing
- QRCoder — ZATCA QR generation
- MVC-style architecture: `Models → Repositories → Services → Controllers → Views`

### Prerequisites
- .NET 10 SDK
- Windows (WinForms requirement)
- PHP 8+ with MySQL/MariaDB (for sync API, optional for standalone use)

### Run the client
```bash
git clone https://github.com/<your-username>/POSSystem.git
cd POSSystem
dotnet restore
dotnet run --project POSSystem
```

On first launch, a local SQLite database is created automatically at:
```
%APPDATA%\POSSystem\pos.db
```

Default login:
```
Username: admin
Password: admin123
```
⚠️ Change this immediately after first login.

### Run the sync API (optional)
```bash
cd api/newAPI
php -S localhost:8000
```
Set the API URL in **Settings → API** inside the app.

## Excel Import Template

Products can be bulk-imported via **Products → Import**. Use **Products → Template** to download the expected column format:

| Barcode | Name | CategoryId | Price | Cost | Stock | Unit |
|---|---|---|---|---|---|---|

## Roadmap

- [ ] PDF export for reports
- [ ] ZATCA Phase 2 (XML invoice signing, hash chaining, reporting/clearance API)

## License

MIT — see [LICENSE](LICENSE)

## Disclaimer

This project is for educational/portfolio purposes. ZATCA compliance features are partial (Phase 1 QR only) and not certified for production tax reporting use.
