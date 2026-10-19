# PAWO — Pet Happy Place 🐾

Website MVP tiếng Việt cho dịch vụ spa/khách sạn thú cưng và cửa hàng phụ kiện, thời trang, thức ăn.

## Tính năng
- Giao diện responsive, pastel, trẻ trung.
- Tìm kiếm và lọc sản phẩm.
- Chọn sản phẩm/dịch vụ vào checklist.
- Lưu checklist vào PostgreSQL.
- Gửi yêu cầu đặt lịch Spa/khách sạn, dữ liệu được lưu trong PostgreSQL.
- Express API kiểm tra dữ liệu đầu vào và tự tạo bảng/dữ liệu mẫu lần đầu.

> Bản MVP chưa có thanh toán, đăng nhập quản trị, quản lý đơn hàng hay gửi SMS/email. Lịch đặt cần nhân viên xác nhận thủ công.

## Chạy trên máy tính
Yêu cầu Node.js 20+ và PostgreSQL.

1. Tạo database tên `pawo`.
2. Sao chép `.env.example` thành `.env`, sau đó điền chuỗi kết nối database.
3. Chạy:

```bash
npm install
npm run dev
```

4. Mở `http://localhost:5173`.

Kiểm tra API tại `http://localhost:3001/api/health`; khi database kết nối đúng, kết quả là `{"status":"ok","database":true}`.

## Deploy từ GitHub
- Build command: `npm install && npm run build`
- Start command: `npm start`
- Environment variables: `DATABASE_URL` (bắt buộc để lưu dữ liệu), `DB_SSL=true` nếu PostgreSQL yêu cầu SSL, và `PORT` nếu nền tảng cần chỉ định cổng.
- Sau khi deploy, kiểm tra `https://TEN-MIEN-CUA-BAN/api/health`.

**Bảo mật:** Không commit file `.env`, mật khẩu hoặc chuỗi kết nối thật vào GitHub. Chỉ cấu hình bí mật trong phần Environment Variables của nền tảng deploy.

## Database tables
`products`, `services`, `checklist_sessions`, `checklist_items`, `bookings`.

## API
- `GET /api/health`
- `GET /api/products`
- `GET /api/services`
- `POST /api/checklist`
- `POST /api/bookings`

Trước khi dùng production, nên bổ sung tài khoản/quyền quản trị, migration có phiên bản, sao lưu, rate limit và quy trình bảo vệ dữ liệu cá nhân.