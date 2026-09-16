# 🧋 Hệ Thống Quản Lý Tiệm Trà Sữa

> Ứng dụng web quản lý tiệm trà sữa toàn diện với đặt hàng trực tuyến, quản lý sản phẩm, nhân viên và thống kê doanh thu.

---

## 📋 Mục Lục

- [🎯 Tính Năng Chính](#tính-năng-chính)
- [🔧 Yêu Cầu Hệ Thống](#yêu-cầu-hệ-thống)
- [📦 Cài Đặt](#cài-đặt)
- [⚙️ Cấu Hình Database](#cấu-hình-database)
- [▶️ Chạy Ứng Dụng](#chạy-ứng-dụng)
- [👥 Tài Khoản Mẫu](#tài-khoản-mẫu)
- [📂 Cấu Trúc Dự Án](#cấu-trúc-dự-án)
- [🎨 Giao Diện Chính](#giao-diện-chính)
- [📊 Các API Chính](#các-api-chính)
- [☕ Sản Phẩm & Giá Cả](#sản-phẩm--giá-cả)
- [🔐 Tính Năng Bảo Mật](#tính-năng-bảo-mật)
- [🚨 Xử Lý Lỗi](#xử-lý-lỗi)
- [🔄 Quy Trình Hoạt Động](#quy-trình-hoạt-động)
- [📈 Vai Trò HTTT Trong Tổ Chức](#vai-trò-httt-trong-tổ-chức)
- [🛠️ Công Nghệ Sử Dụng](#công-nghệ-sử-dụng)
- [📞 Hỗ Trợ](#hỗ-trợ)

---

## 🎯 Tính Năng Chính

### ✨ Dành Cho Khách Hàng
- ✅ **Đăng Ký / Đăng Nhập** - Tài khoản an toàn với 2 mật khẩu
- ✅ **Đặt Hàng Online** - Chọn sản phẩm, ghi chú, tự động tìm thời gian giao
- ✅ **Lịch Sử Đơn Hàng** - Xem tất cả các đơn đã đặt trước đó
- ✅ **Chọn Cách Thanh Toán** - Tiền mặt, chuyển khoản, ví điện tử
- ✅ **Lịch Sử Chi Tiêu** - Theo dõi các khoản thanh toán đã thực hiện

### 👨‍💼 Dành Cho Quản Lý / Chủ Tiệm
- ✅ **Dashboard** - Thống kê doanh thu, đơn hàng mới, tồn kho
- ✅ **Quản Lý Đơn Hàng** - Xác nhận, chuẩn bị, giao hàng, hoàn tất
- ✅ **Quản Lý Sản Phẩm** - Thêm, sửa, xóa, điều chỉnh giá và tồn kho
- ✅ **Quản Lý Nhân Viên** - Thêm, sửa xóa nhân viên, quản lý tài khoản
- ✅ **Khách Hàng** - Xem lịch sử khách, chi tiêu, thông tin liên hệ
- ✅ **Biểu Đồ Doanh Thu** - Thống kê theo ngày, tuần, tháng
- ✅ **Báo Cáo Tồn Kho** - Theo dõi nguyên liệu và tồn kho

---

## 🔧 Yêu Cầu Hệ Thống

### 💻 Máy Tính
- **Hệ điều hành**: Windows 10+, macOS, Linux
- **RAM**: 4GB trở lên
- **Ổ cứng**: 500MB dung lượng trống

### 📌 Phần Mềm Cần Cài

| Phần Mềm | Phiên Bản | Tải Về |
|---------|----------|--------|
| **Node.js** | 18.0+ | [nodejs.org](https://nodejs.org) |
| **SQL Server** | 2019+ | [microsoft.com/sql-server](https://www.microsoft.com/sql-server) |
| **Git** (tùy chọn) | Mới nhất | [git-scm.com](https://git-scm.com) |

### ✔️ Kiểm Tra Cài Đặt
```bash
node --version    # Phải là v18.0+
npm --version     # Phải là v8.0+
```

---

## 📦 Cài Đặt

### 1️⃣ Tải / Clone Dự Án

**Cách A: Clone từ Git**
```bash
git clone https://github.com/Nguyenhoangnam2005/Quanlytrasua.git
cd Quanlytrasua
```

**Cách B: Tải File ZIP**
- Tải file ZIP từ GitHub
- Giải nén vào thư mục tùy ý
- Mở Command Prompt / Terminal tại thư mục đó

### 2️⃣ Cài Đặt Dependencies

```bash
npm install
```

**Output chờ đợi:**
```
added 45 packages in 2m
```

---

## ⚙️ Cấu Hình Database

### 📍 Bước 1: Tạo Database SQL Server

**Mở SQL Server Management Studio (SSMS):**

1. Kết nối đến SQL Server của bạn
2. Click chuột phải vào **Databases** → **New Database**
3. Đặt tên: `QuanlyTrasua`
4. Click **OK**

### 📍 Bước 2: Chạy Script SQL

Nếu bạn có file `.sql`, hãy:

1. Mở SSMS → File → Open → Query File
2. Chọn file SQL
3. Nhấn **Execute** (F5)

**Hoặc** nhập các lệnh SQL sau:

```sql
-- Tạo bảng KhachHang (Khách hàng)
CREATE TABLE KhachHang (
    ID INT PRIMARY KEY IDENTITY(1,1),
    HoTen NVARCHAR(100) NOT NULL,
    Email VARCHAR(100),
    SoDienThoai VARCHAR(20),
    DiaChi NVARCHAR(200),
    MatKhau VARCHAR(100),
    MatKhauCap2 VARCHAR(100),
    NgayDangKy DATETIME DEFAULT GETDATE(),
    TrangThai NVARCHAR(50) DEFAULT 'Hoạt động'
);

-- Tạo bảng NhanVien (Nhân viên)
CREATE TABLE NhanVien (
    MaNV INT PRIMARY KEY IDENTITY(1,1),
    HoTen NVARCHAR(100),
    TenDangNhap VARCHAR(50) UNIQUE,
    MatKhau VARCHAR(100),
    ChucVu NVARCHAR(50),
    SoDienThoai VARCHAR(20),
    Email VARCHAR(100),
    QueQuan NVARCHAR(100),
    NgayVaoLam DATE,
    TrangThai NVARCHAR(50) DEFAULT 'Hoạt động'
);

-- Tạo bảng SanPham (Sản phẩm)
CREATE TABLE SanPham (
    MaSP INT PRIMARY KEY IDENTITY(1,1),
    TenSP NVARCHAR(100) NOT NULL,
    LoaiSP NVARCHAR(50),
    Gia DECIMAL(10,0),
    TonKho INT DEFAULT 0,
    MoTa NVARCHAR(500),
    Hinh NVARCHAR(255),
    TrangThai NVARCHAR(50) DEFAULT 'Kinh doanh'
);

-- Tạo bảng DonHang (Đơn hàng)
CREATE TABLE DonHang (
    ID INT PRIMARY KEY IDENTITY(1,1),
    KhachHangID INT,
    NgayDat DATETIME DEFAULT GETDATE(),
    NgayGiao DATETIME,
    DiemGiao NVARCHAR(200),
    GhiChu NVARCHAR(500),
    TongTien DECIMAL(18,0),
    TrangThai NVARCHAR(50) DEFAULT 'Chờ xác nhận',
    PhuongThucTT NVARCHAR(50),
    FOREIGN KEY (KhachHangID) REFERENCES KhachHang(ID)
);

-- Tạo bảng ChiTietDonHang (Chi tiết đơn hàng)
CREATE TABLE ChiTietDonHang (
    ID INT PRIMARY KEY IDENTITY(1,1),
    DonHangID INT,
    SanPhamID INT,
    SoLuong INT,
    DonGia DECIMAL(10,0),
    ThanhTien DECIMAL(18,0),
    FOREIGN KEY (DonHangID) REFERENCES DonHang(ID),
    FOREIGN KEY (SanPhamID) REFERENCES SanPham(MaSP)
);

-- Tạo bảng NguyenLieu (Nguyên liệu)
CREATE TABLE NguyenLieu (
    MaNL INT PRIMARY KEY IDENTITY(1,1),
    TenNL NVARCHAR(100),
    DonViTinh NVARCHAR(20),
    TonKho DECIMAL(10,2),
    GiaNhap DECIMAL(10,0),
    NgayNhap DATE DEFAULT GETDATE()
);

-- Thêm dữ liệu khách hàng mẫu
INSERT INTO KhachHang (HoTen, Email, SoDienThoai, DiaChi, MatKhau, MatKhauCap2)
VALUES (N'Nguyễn Văn A', 'nguyenvana@email.com', '0912345678', N'123 Nguyễn Huệ, Huế', '123123', '111111');

-- Thêm nhân viên Admin
INSERT INTO NhanVien (HoTen, TenDangNhap, MatKhau, ChucVu, SoDienThoai, Email, QueQuan)
VALUES (N'Admin', 'admin', '123123', 'Quản Lý', '0988888888', 'admin@trasua.com', N'Huế');

-- Thêm sản phẩm mẫu
INSERT INTO SanPham (TenSP, LoaiSP, Gia, TonKho, MoTa, TrangThai)
VALUES 
(N'Trà Sữa Đường Đen', N'Trà Sữa', 35000, 50, N'Trà sữa truyền thống với đường đen ngon', N'Kinh doanh'),
(N'Trà Sữa Matcha', N'Trà Sữa', 40000, 40, N'Trà xanh Matcha thơm ngon', N'Kinh doanh'),
(N'Trà Sữa Dâu', N'Trà Sữa', 38000, 35, N'Trà sữa vị dâu tươi', N'Kinh doanh'),
(N'Cà Phê Đen', N'Cà Phê', 25000, 60, N'Cà phê đen nóng', N'Kinh doanh'),
(N'Cà Phê Sữa', N'Cà Phê', 28000, 55, N'Cà phê sữa nóng', N'Kinh doanh'),
(N'Nước Chanh Tươi', N'Nước Ép', 20000, 70, N'Nước chanh tươi mát', N'Kinh doanh'),
(N'Sinh Tố Xoài', N'Sinh Tố', 35000, 45, N'Sinh tố xoài ngon', N'Kinh doanh'),
(N'Kem Đánh Ý', N'Tráng Miệng', 15000, 100, N'Kem đánh ý lạnh', N'Kinh doanh');
```

### 📍 Bước 3: Sửa Cấu Hình Trong server.js

Mở file `server.js` bằng trình soạn thảo (VS Code, Notepad++...):

```javascript
// Tìm dòng này (khoảng dòng 17-25):
const dbConfig = {
    server: 'localhost',         // ← Sửa IP/hostname SQL Server của bạn
    port: 53439,                 // ← Sửa cổng SQL Server
    user: 'sa',                  // ← Sửa username SQL Server
    password: '123123',          // ← Sửa password SQL Server
    database: 'QuanlyTrasua',    // ← Tên database
    options: {
        encrypt: false,
        trustServerCertificate: true,
        enableArithAbort: true
    }
};
```

---

## ▶️ Chạy Ứng Dụng

### 📍 Bước 1: Mở Terminal/Command Prompt

- **Windows**: Nhấn `Win + R`, gõ `cmd`
- **macOS/Linux**: Mở Terminal

### 📍 Bước 2: Điều Hướng Đến Thư Mục Dự Án

```bash
cd đường/dẫn/đến/Quanlytrasua
```

Ví dụ:
```bash
cd C:\Users\Admin\MyWebsite\Quanlytrasua
```

### 📍 Bước 3: Chạy Server

```bash
node server.js
```

**Output chờ đợi:**
```
✅ Đã kết nối SQL!
🚀 Server đã sẵn sàng!
👉 Bây giờ hãy sang trình duyệt nhấn truy cập: http://localhost:3000/Trangchu.html
```

### 📍 Bước 4: Mở Trình Duyệt

Nhập vào thanh địa chỉ:
```
http://localhost:3000/Trangchu.html
```

**✅ Xong! Ứng dụng đã chạy thành công.**

---

## 👥 Tài Khoản Mẫu

### 🟢 Tài Khoản Khách Hàng

```
Số Điện Thoại: 0912345678
Mật Khẩu: 123123
Mật Khẩu Cấp 2 (quên MK): 111111
Tên: Nguyễn Văn A
```

**Cách Đăng Nhập:**
1. Vào trang chủ (Trangchu.html)
2. Nhấn nút **Đăng Nhập Khách Hàng**
3. Nhập SĐT + Mật khẩu

### 🔴 Tài Khoản Quản Lý/Nhân Viên

```
Tài Khoản: admin
Mật Khẩu: 123123
Chức Vụ: Quản Lý
```

**Cách Đăng Nhập:**
1. Vào trang chủ (Trangchu.html)
2. Nhấn nút **Đăng Nhập Quản Lý** (nút đỏ)
3. Nhập username + password
4. Sẽ vào trang dashboard (giaodienql.html)

---

## 📂 Cấu Trúc Dự Án

```
Quanlytrasua/
│
├── 📄 server.js                    # Backend API chính
├── 📄 package.json                 # Dependencies
├── 📄 package-lock.json
│
├── 📄 Trangchu.html                # Trang chủ - Giao diện khách hàng
├── 📄 giaodienql.html              # Dashboard quản lý
├── 📄 login.html                   # Trang đăng nhập
│
├── 📁 css/                         # File CSS
│   ├── trangchu.css
│   ├── giaodienql.css
│   └── login.css
│
├── 📁 js/                          # File JavaScript
│   ├── main.js
│   ├── giaodienql.js
│   └── login.js
│
├── 📁 images/                      # Hình ảnh sản phẩm & nền
│   ├── bg.jpg                      # Hình nền (xe espresso)
│   ├── trasua.jpg
│   ├── cafe.jpg
│   └── ...
│
└── 📄 README.md                    # File hướng dẫn này
```

---

## 🎨 Giao Diện Chính

### 🏠 Trang Chủ (Trangchu.html)
- **Nền**: Hình ảnh xe espresso Chang Espresso
- **Tính năng:**
  - Giới thiệu tiệm trà sữa
  - Nút Đăng Nhập / Đăng Ký
  - Danh sách sản phẩm nổi bật
  - Mô tả chi tiết từng loại trà sữa
  - Responsive design - Tương thích mobile

### 📊 Dashboard Quản Lý (giaodienql.html)
- Giao diện quản lý toàn bộ hệ thống
- **Chức năng chính:**
  - Thống kê: Doanh thu hôm nay, Đơn hàng mới, Tồn kho
  - Tab quản lý: Sản phẩm, Nhân viên, Khách hàng, Đơn hàng
  - Biểu đồ doanh thu theo ngày/tuần/tháng
  - Bảng dữ liệu chi tiết

### 🔐 Trang Đăng Nhập (login.html)
- Giao diện đẹp với nền hình ảnh
- **2 chế độ đăng nhập:**
  - 👤 Đăng nhập khách hàng (SĐT + Mật khẩu)
  - 👨‍💼 Đăng nhập quản lý (Tài khoản + Mật khẩu)
- Tính năng "Ghi nhớ mật khẩu"
- Hiển thị tài khoản demo

---

## �� Các API Chính

### 🔑 Xác Thực

| API | Method | Tác Vụ |
|-----|--------|--------|
| `/login` | POST | Đăng nhập khách hàng |
| `/login-admin` | POST | Đăng nhập quản lý |
| `/dang-ky` | POST | Đăng ký tài khoản |
| `/quen-mat-khau` | POST | Lấy lại mật khẩu |

**Ví dụ:**
```bash
POST http://localhost:3000/login
Content-Type: application/json

{
  "sdt": "0912345678",
  "password": "123123"
}
```

### 🥤 Sản Phẩm

| API | Method | Tác Vụ |
|-----|--------|--------|
| `/api/san-pham` | GET | Danh sách tất cả sản phẩm |
| `/api/san-pham/:id` | GET | Chi tiết sản phẩm |
| `/api/san-pham` | POST | Thêm sản phẩm mới |
| `/api/san-pham/:id` | PUT | Cập nhật sản phẩm |
| `/api/san-pham/:id` | DELETE | Xóa sản phẩm |

### 🛒 Đặt Hàng

| API | Method | Tác Vụ |
|-----|--------|--------|
| `/dat-hang` | POST | Đặt hàng mới |
| `/my-orders/:userId` | GET | Lịch sử đặt hàng |
| `/api/don-hang/:id` | GET | Chi tiết đơn hàng |
| `/api/cap-nhat-trang-thai/:id` | PUT | Cập nhật trạng thái |

### 👨‍💼 Nhân Viên

| API | Method | Tác Vụ |
|-----|--------|--------|
| `/api/nhan-vien` | GET | Danh sách nhân viên |
| `/api/them-nhan-vien` | POST | Thêm nhân viên |
| `/api/nhan-vien/:id` | PUT | Cập nhật nhân viên |
| `/api/nhan-vien/:id` | DELETE | Xóa nhân viên |

### 📊 Thống Kê

| API | Method | Tác Vụ |
|-----|--------|--------|
| `/api/thong-ke-dashboard` | GET | Thống kê dashboard |
| `/api/doanh-thu-ngay` | GET | Doanh thu ngày |
| `/api/doanh-thu-thang` | GET | Doanh thu tháng |
| `/api/bieu-do-tuan` | GET | Dữ liệu biểu đồ tuần |

---

## ☕ Sản Phẩm & Giá Cả

### 🥤 Trà Sữa

| Sản Phẩm | Giá | Mô Tả |
|---------|-----|-------|
| **Trà Sữa Đường Đen** | 35,000 VND | Trà sữa truyền thống |
| **Trà Sữa Matcha** | 40,000 VND | Trà xanh Matcha thơm |
| **Trà Sữa Dâu** | 38,000 VND | Vị dâu tươi mới |
| **Trà Sữa Cafe** | 40,000 VND | Kết hợp trà và cafe |

### ☕ Cà Phê

| Sản Phẩm | Giá | Mô Tả |
|---------|-----|-------|
| **Cà Phê Đen** | 25,000 VND | Cà phê đen nóng |
| **Cà Phê Sữa** | 28,000 VND | Cà phê sữa nóng |
| **Cà Phê Kem** | 35,000 VND | Cà phê với kem |

### 🍋 Nước Ép & Nước Trái Cây

| Sản Phẩm | Giá | Mô Tả |
|---------|-----|-------|
| **Nước Chanh Tươi** | 20,000 VND | Nước chanh tươi mát |
| **Nước Cam** | 25,000 VND | Nước cam tươi |
| **Nước Dâu** | 28,000 VND | Nước dâu ngọt |

### 🍓 Sinh Tố

| Sản Phẩm | Giá | Mô Tả |
|---------|-----|-------|
| **Sinh Tố Xoài** | 35,000 VND | Sinh tố xoài ngon |
| **Sinh Tố Dâu** | 38,000 VND | Sinh tố dâu tươi |
| **Sinh Tố Chuối** | 30,000 VND | Sinh tố chuối |

### 🍰 Tráng Miệng

| Sản Phẩm | Giá | Mô Tả |
|---------|-----|-------|
| **Kem Đánh Ý** | 15,000 VND | Kem lạnh |
| **Bánh Ngọt** | 25,000 VND | Bánh ngọt tươi |

---

## 🔐 Tính Năng Bảo Mật

### ✅ Các Biện Pháp Bảo Mật Hiện Tại
- 🔒 **Xác thực 2 lớp** - Mật khẩu cấp 2 để khôi phục tài khoản
- 🔐 **Lưu mật khẩu** - Lưu trực tiếp trong DB (nên hash trong sản phẩm thực)
- 🛡️ **CORS** - Kiểm soát truy cập từ các domain khác
- ✔️ **Validation** - Kiểm tra dữ liệu đầu vào

### ⚠️ Khuyến Nghị Bảo Mật

Để sản phẩm hoàn hảo hơn, nên thêm:
1. **Hash mật khẩu** với bcrypt
2. **JWT token** cho phiên đăng nhập
3. **Rate limiting** chống brute force
4. **HTTPS** khi triển khai thực tế
5. **SQL Injection prevention** (hiện tại đã an toàn)

---

## 🚨 Xử Lý Lỗi

### ❌ Lỗi: "Cannot connect to database"

**Nguyên Nhân:**
- SQL Server không chạy
- Cấu hình sai trong `server.js`
- Network bị chặn

**Giải Pháp:**
```bash
# 1. Kiểm tra SQL Server đang chạy
# Windows: Services → SQL Server (MSSQLSERVER) = Running
# macOS: brew services list | grep sqlserver
# Linux: sudo systemctl status mssql-server

# 2. Kiểm tra kết nối
sqlcmd -S localhost -U username -P password

# 3. Reset config trong server.js
# Đảm bảo server, port, user, password đúng
```

### ❌ Lỗi: "Port 3000 already in use"

**Giải Pháp:**
```bash
# Windows - Tìm process chiếm port 3000
netstat -ano | findstr :3000
# Kết quả: TCP  0.0.0.0:3000  LISTENING  12345
# Kill process:
taskkill /PID 12345 /F

# macOS/Linux
lsof -i :3000
kill -9 <PID>

# Hoặc sử dụng port khác
# Mở server.js, sửa dòng:
// const port = 3001; // Thay 3000 bằng 3001
```

### ❌ Lỗi: "npm ERR! 404 Not Found"

**Giải Pháp:**
```bash
# Xóa node_modules và cài lại
rm -rf node_modules package-lock.json
npm install

# Hoặc xóa cache npm
npm cache clean --force
npm install
```

### ❌ Lỗi: CSS không load (Trangchu.css)

**Nguyên Nhân:** Đường dẫn CSS sai

**Giải Pháp:** 
Kiểm tra file trangchu.css nằm trong thư mục `css/`

```html
<!-- Đúng -->
<link rel="stylesheet" href="css/trangchu.css">

<!-- Sai -->
<link rel="stylesheet" href="trangchu.css">
```

### ❌ Lỗi: Hình ảnh không hiển thị

**Nguyên Nhân:** Đường dẫn ảnh sai

**Giải Pháp:**
Kiểm tra file bg.jpg nằm trong thư mục `images/`

```html
<!-- Đúng -->
<img src="images/bg.jpg" alt="Background">

<!-- Sai -->
<img src="bg.jpg" alt="Background">
```

---

## 🔄 Quy Trình Hoạt Động

### 📋 Quy Trình Đặt Hàng

```
1. KHÁCH HÀNG TRUY CẬP
   ├─ Chưa có tài khoản → Nhấn "Đăng Ký"
   └─ Có tài khoản → Nhấn "Đăng Nhập"
          ↓
2. VÀO TRANG ĐẶT HÀNG
   ├─ Chọn sản phẩm
   ├─ Nhập số lượng
   ├─ Thêm ghi chú
   └─ Chọn địa chỉ giao hàng
          ↓
3. CHỌN PHƯƠNG THỨC THANH TOÁN
   ├─ Tiền mặt
   ├─ Chuyển khoản
   └─ Ví điện tử
          ↓
4. XÁC NHẬN ĐẶT HÀNG
   ├─ Xác nhận giá tiền
   ├─ Tạo đơn hàng
   └─ Trạng thái: "Chờ xác nhận" ✅
          ↓
5. NHÂN VIÊN XÁC NHẬN
   └─ Trạng thái: "Chờ xác nhận" → "Chuẩn bị" ✅
```

### 🏪 Quy Trình Chuẩn Bị & Giao Hàng

```
QUẢN LÝ XÁC NHẬN ĐƠN
   ↓
Trạng thái: "Chờ xác nhận" → "Chuẩn bị" ✅
   ↓
NHÂN VIÊN CHUẨN BỊ ĐƠN
   ↓
... (gói hàng, chuẩn bị)
   ↓
QUẢN LÝ NHẤN "ĐANG GIAO"
   ↓
Trạng thái: "Chuẩn bị" → "Đang giao" ✅
   ↓
... (giao hàng cho khách)
   ↓
QUẢN LÝ NHẤN "HOÀN TẤT"
   ↓
Trạng thái: "Đang giao" → "Hoàn tất" ✅
   ↓
CẬP NHẬT DOANH THU
```

---

## 📈 Vai Trò HTTT Trong Tổ Chức

### 1️⃣ Hỗ Trợ Tác Nghiệp (Operational Support)

**Khái Niệm:** Giúp **ghi nhận, xử lý** các giao dịch và hoạt động **hàng ngày**.

**Ví Dụ Thực Tế:**
- ✅ Ghi nhận tự động đơn hàng: tên sản phẩm, số lượng, giá tiền, thời gian
- ✅ Xử lý thanh toán: Tính tiền, lưu thông tin, tạo hóa đơn
- ✅ Cập nhật tồn kho: Giảm tồn kho khi bán, cảnh báo hết hàng

**Lợi Ích:**
- ⚡ Nhanh chóng - Tiết kiệm thời gian
- 📊 Chính xác - Giảm sai sót
- 💾 Minh bạch - Lưu trữ đầy đủ

---

### 2️⃣ Hỗ Trợ Quản Lý (Management Support)

**Khái Niệm:** **Lập báo cáo, giám sát** hoạt động để quản lý có cái nhìn tổng quan.

**Ví Dụ Thực Tế:**

📊 **Báo Cáo:**
- Doanh thu hôm nay: 5,250,000 VND
- TOP sản phẩm bán chạy: Trà Sữa Đường Đen (245 ly)
- Khách mới: 45 người, Khách quay lại: 230 người

📈 **Giám Sát:**
- Đơn chờ xác nhận: 12, Đơn đang chuẩn bị: 8
- Sản phẩm hết hàng: Trà Sữa Matcha (CẢNH BÁO)
- Hiệu suất nhân viên: A (45 đơn), B (28 đơn), C (52 đơn)

**Lợi Ích:**
- 👁️ Cái nhìn toàn cảnh - Biết tình hình kinh doanh
- 🚨 Phát hiện vấn đề - Sản phẩm bán chậm, tồn kho dư thừa
- 🎯 Tối ưu hóa - Điều chỉnh menu theo nhu cầu

---

### 3️⃣ Hỗ Trợ Ra Quyết Định (Decision-Making Support)

**Khái Niệm:** **Phân tích dữ liệu** để giúp quản lý đưa ra quyết định chiến lược.

**Ví Dụ Thực Tế:**

💡 **Vấn Đề 1:** Doanh thu giảm thứ 2-3
- Phân tích: Thứ 2 (3.5M), Thứ 3 (4.2M), trung bình (8.1M)
- Quyết định: Tung khuyến mãi "Thứ 2-3 Siêu Rẻ" → Tăng 30%

💡 **Vấn Đề 2:** Quản lý nhân sự
- Phân tích: Giờ cao điểm 10h-12h (120 đơn), thấp nhất 14h-16h (45 đơn)
- Quyết định: Tăng nhân viên vào giờ cao điểm → Tránh quá tải

💡 **Vấn Đề 3:** Ra sản phẩm mới
- Phân tích: 60% khách là độ tuổi 18-25, trend Matcha + sức khỏe
- Quyết định: Ra "Trà Sữa Matcha Latte" → Doanh thu +2.7M/tháng

💡 **Vấn Đề 4:** Mở chi nhánh
- Phân tích: Lợi nhuận 7M/ngày, tỷ lệ khách lặp lại 65%
- Quyết định: Mở chi nhánh gần trường đại học → Hoàn vốn 28-30 tháng

**Lợi Ích:**
- 🎯 Giảm rủi ro - Quyết định dựa dữ liệu, không phỏng đoán
- 📈 Phát triển bền vững - Chiến lược rõ ràng
- ⚔️ Cạnh tranh tốt - Nhanh thích ứng thị trường

---

### 4️⃣ Tạo Lợi Thế Cạnh Tranh (Competitive Advantage)

**Khái Niệm:** **Cải tiến sản phẩm, dịch vụ, tối ưu hóa quy trình** để **vượt trội so với đối thủ**.

**Ví Dụ Thực Tế:**

🏆 **Lợi Thế 1: Sản Phẩm Chất Lượng Cao**
- Trước: Menu cố định, không cập nhật
- Sau: Menu động theo nhu cầu khách → Điểm đánh giá 4/5 ⭐ → 4.8/5 ⭐

🏆 **Lợi Thế 2: Dịch Vụ Vượt Trội**
- Trước: Dịch vụ như nhau cho ai nấy
- Sau: Nhớ sở thích khách, gợi ý sản phẩm → Khách quay lại 45% → 75%

🏆 **Lợi Thế 3: Tối Ưu Hóa Chi Phí**
- Trước: Lỗ hàng tồn kho 500K/tháng
- Sau: Tính toán chính xác → Lỗ chỉ 50K/tháng (giảm 90%) → Lợi nhuận +20%

🏆 **Lợi Thế 4: Quy Trình Hiệu Quả**
- Trước: Ghi tay, dễ sai, thời giao 30 phút
- Sau: App online, tự động → Thời giao 15 phút, hài lòng 95%

🏆 **Lợi Thế 5: Quản Lý Thông Minh**
- Trước: Chủ tiệm phải ngồi cả ngày ở tiệm
- Sau: Theo dõi dashboard điện thoại → Chủ thoải mái, tiệm vẫn chạy tốt

**So Sánh Với Đối Thủ:**
```
TIỆM TRUYỀN THỐNG           VS      TIỆM MODERN
❌ Ghi tay, chậm            ✅ Tự động, nhanh
❌ Menu cố định             ✅ Menu động
❌ Dịch vụ như nhau         ✅ Dịch vụ cá nhân
❌ Khách ít quay lại        ✅ Khách quay lại 75%
❌ Chi phí cao              ✅ Chi phí thấp
❌ Lợi nhuận thấp           ✅ Lợi nhuận cao 20%
                            🏆 VƯỢT TRỘI!
```

**Lợi Ích:**
- 👑 Vượt trội đối thủ - Chất lượng cao, giá thấp, dịch vụ tốt
- 💚 Giữ chân khách - Khách hài lòng, quay lại nhiều
- 📈 Tăng doanh thu - Hiệu suất cao, giảm chi phí
- 🚀 Phát triển bền vững - Tiệm luôn được cải thiện

---

## 🛠️ Công Nghệ Sử Dụng

### Frontend
- **HTML5** - Markup
- **CSS3** - Styling (trangchu.css, giaodienql.css, login.css)
- **JavaScript** - Interactivity (main.js, giaodienql.js, login.js)
- **Font Awesome** - Icon library

### Backend
- **Node.js** - Môi trường chạy JavaScript
- **Express.js** - Framework web
- **MSSQL** - Thư viện kết nối SQL Server

### Database
- **SQL Server 2019+** - Cơ sở dữ liệu

### Tools
- **Git** - Quản lý phiên bản
- **Visual Studio Code** - Editor
- **SQL Server Management Studio** - Quản lý database

---

## 📞 Hỗ Trợ

Nếu gặp vấn đề, vui lòng:
1. Kiểm tra phần **🚨 Xử Lý Lỗi**
2. Đọc lại các bước **Cấu Hình Database**
3. Liên hệ admin qua email hoặc GitHub Issues

**Contact:**
- Email: admin@trasua.com
- GitHub: [Nguyenhoangnam2005/Quanlytrasua](https://github.com/Nguyenhoangnam2005/Quanlytrasua)

---

## 📝 License

Dự án này được phát triển cho mục đích giáo dục.

**Happy Coding! 🚀**
