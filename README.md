# SmartHome-Control-App

## MỤC LỤC

- [1. Mô tả dự án](#1-mô-tả-dự-án)
- [2. Chức năng](#2-chức-năng)
  - [2.1. Chức năng chính](#21-chức-năng-chính)
  - [2.2. Chức năng phụ](#22-chức-năng-phụ)
  - [2.3. Chưa triển khai](#23-chưa-triển-khai)
- [3. Công nghệ sử dụng](#3-công-nghệ-sử-dụng)
- [4. Cấu trúc thư mục trong lib](#4-cấu-trúc-thư-mục-trong-lib)
- [5. Luồng hoạt động của ứng dụng](#5-luồng-hoạt-động-của-ứng-dụng)
- [6. Cài đặt & Chạy project](#6-cài-đặt--chạy-project)
- [7. Các hạn chế](#7-các-hạn-chế)

## 1. Mô tả dự án

Đây là một ứng dụng Flutter demo dùng để quản lý và điều khiển thiết bị điện trong các phòng của một ngôi nhà thông minh.

Ứng dụng mô phỏng việc điều khiển thiết bị thông qua giao thức MQTT (publish / subscribe).
Ngoài ra, app có sử dụng Local Storage để lưu thông tin người dùng và dữ liệu phòng đã tạo.

> Lưu ý:
> Đây chỉ là demo app, không kết nối với phần cứng thật, không có dữ liệu thiết bị thực tế.

## 2. Chức năng

### 2.1. Chức năng chính

- Đăng nhập người dùng (không có backend server)
- Hiển thị danh sách các phòng
- Điều khiển trạng thái thiết bị trong phòng (mô phỏng)
- Kết nối MQTT để:
  - Gửi lệnh (publish)
  - Nhận dữ liệu (subscribe)
- Lưu trạng thái ứng dụng bằng Local Storage

### 2.2. Chức năng phụ

- Thêm phòng mới
- Xóa phòng
- Hiển thị trạng thái cảm biến / thiết bị theo phòng

### 2.3. Chưa triển khai

- Thêm phòng mới
- Xóa phòng
- Hiển thị trạng thái cảm biến / thiết bị theo phòng
- Cảnh báo khi vượt ngưỡng an toàn

## 3. Công nghệ sử dụng

- **Flutter & Dart**
- **MQTT** (sử dụng package mqtt_client)
- **Provider** cho quản lý state
- **SharedPreferences** cho Local Storage
- UI xây dựng bằng widget Flutter (Material Design)

## 4. Cấu trúc thư mục trong `lib/`

```sh
lib/
 ├ models/                  # Model dữ liệu (Room, User)
 ├ mqtt/                    # Cấu hình & service MQTT
 ├ routing/                 # Điều hướng (routes)
 ├ state/                   # Quản lý state (Provider)
 ├ ui/                      # Các màn hình UI
 ├ main.dart                # Entry point
 └ my_app.dart              # Cấu hình MaterialApp
```

Với:

- `models/`: Định nghĩa dữ liệu phòng và người dùng
- `mqtt/`: Xử lý kết nối, publish / subscribe MQTT
- `state/`: Lưu và quản lý trạng thái phòng, user, MQTT
- `ui/`: Các màn hình (login, home, room, config, …)
- `routing/`: Quản lý điều hướng trong app

## 5. Luồng hoạt động của ứng dụng

1. Khởi động app (main.dart)
   - Khởi tạo MQTT
   - Load dữ liệu từ Local Storage
   - Setup Provider cho state management

2. Màn hình đăng nhập
   - Người dùng nhập username / password
   - Kiểm tra dữ liệu trong Local Storage

3. Màn hình Home
   - Hiển thị danh sách các phòng
   - Người dùng chọn phòng để điều khiển

4. Màn hình chi tiết phòng
   - Hiển thị thiết bị trong phòng
   - Gửi lệnh điều khiển qua MQTT
   - Nhận dữ liệu trạng thái qua MQTT topic

5. Lưu dữ liệu
   - Danh sách phòng và user được lưu bằng SharedPreferences
   - Tải lại khi app mở lần sau

## 6. Cài đặt & Chạy project

**Bước 1: Clone repository**

```sh
git clone https://github.com/HTKFOOLISH/SmartHome-Control-App.git
cd SmartHome-Control-App
```

**Bước 2: Cài dependencies**

```sh
flutter pub get
```

**Bước 3: Chạy ứng dụng**

```sh
flutter run
```

> Hoặc bạn có thể xem hướng dẫn chạy demo dành cho người mới tại đây: 👉 [GUIDELINE.md](GUIDELINE.md)

## 7. Các hạn chế

- Chỉ là ứng dụng demo
- Tài khoản người dùng lưu cục bộ, không mã hóa
- MQTT config được viết trực tiếp trong code
- Không có xác thực bảo mật
- Không hỗ trợ nhiều người dùng với quyền khác nhau
