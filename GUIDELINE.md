# GUIDELINE – HƯỚNG DẪN TẢI VÀ CHẠY DỰ ÁN FLUTTER MQTT SMART HOME APP

Tài liệu này hướng dẫn **từng bước** để mọi người có thể tải, cài đặt môi trường và chạy thành công dự án Flutter trên máy cá nhân.

---

## Mục lục

- [1. Yêu cầu môi trường](#1-yêu-cầu-môi-trường-prerequisites)
- [2. Clone / Tải source code](#2-clone--tải-source-code-dự-án)
- [3. Cài đặt dependencies](#3-cài-đặt-dependencies)
- [4. Cấu hình môi trường](#4-cấu-hình-môi-trường-quan-trọng)
- [5. Cấu trúc dự án](#5-cấu-trúc-dự-án-overview)
- [6. Cấu hình MQTT](#6-cấu-hình-mqtt)
- [7. Chạy ứng dụng](#7-chạy-ứng-dụng)
- [8. Các lỗi thường gặp](#8-các-lỗi-thường-gặp--cách-xử-lý)
- [9. Lệnh Flutter thường dùng](#9-lệnh-flutter-thường-dùng)
- [10. Liên hệ & hỗ trợ](#10-liên-hệ--hỗ-trợ)

---

## 1. Yêu cầu môi trường (Prerequisites)

### 1.1. Hệ điều hành hỗ trợ

- Windows 10 trở lên
- macOS
- Linux (Ubuntu khuyến nghị)

> **Lưu ý**:  
> Đối với **Windows** cũng như **Linux** thì flutter chỉ hỗ trợ cho phiên bản 64-bit.  
> Do đó các bạn phải nâng cấp windows của mình lên bản 64-bit.  
> Các nguồn bạn có thể tham khảo trên google như sau:
>
> - [https://quantrimang.com/cong-nghe/huong-dan-chuyen-tu-windows-10-32-bit-thanh-64-bit-122507](https://quantrimang.com/cong-nghe/huong-dan-chuyen-tu-windows-10-32-bit-thanh-64-bit-122507)
> - [https://www.thegioididong.com/tin-tuc/huong-dan-cach-chuyen-tu-windows-10-32-bit-len-phien-ban-64-bit-699808](https://www.thegioididong.com/tin-tuc/huong-dan-cach-chuyen-tu-windows-10-32-bit-len-phien-ban-64-bit-699808)

### 1.2. Flutter SDK

- **Flutter version**: `3.35.4`
- **Dart version**: `3.9.2`

#### 1.2.1 Hướng dẫn tải flutter

- **Đường link download**: Flutter version (3.35.4) & Dart version (3.9.2)
  - [windows](https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.35.4-stable.zip)
  - [Linux](https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_3.35.4-stable.tar.xz)
  - [MacOS_x64](https://storage.googleapis.com/flutter_infra_release/releases/stable/macos/flutter_macos_3.35.4-stable.zip)
  - [MacOS-arm64](https://storage.googleapis.com/flutter_infra_release/releases/stable/macos/flutter_macos_arm64_3.35.4-stable.zip)

> Hoặc bạn có thể tải từ trang chính thức của flutter nhưng **PHẢI ĐÚNG VERSION MÌNH ĐÃ NÓI (flutter: 3.35.4, dart: 3.9.2)**:
>
> - link trang chính thức: [https://docs.flutter.dev/install/archive](https://docs.flutter.dev/install/archive)

- Sau khi cài đặt xong giải nén folder theo các bước dưới đây:
  - Vào thư mục chứa folder vừa tải, ví dụ như dưới đây:
    ```bash
    C:\Users\<Tên_người_dùng>\Downloads
    ```
  - Tìm folder **flutter_windows_3.35.4-stable.zip** -> giải nén.
  - Vào folder vừa được giải nén chọn folder **flutter** -> Chuột phải -> Cut (Cắt).
  - Truy cập vào

#### 1.2.2 Cài đặt môi trường cho flutter.

> Xem Link tham khảo trên web chính thức: [https://docs.flutter.dev/install/add-to-path#windows](https://docs.flutter.dev/install/add-to-path#windows)
> Hoặc xem hướng dẫn dưới đây.

Sau khi cài đặt xong thực hiện các bước sau (Hướng dẫn cho **windows**, các hệ điều hành khác tương tự, chỉ khác là tổ hợp phím hoặc cách truy cập khác nhau):

- Trên máy của bạn, truy cập vào đường dẫn

  ```sh
  C:\Users\<Tên_người_dùng>
  ```

- Tạo thư mục mới với tên **develop** -> chuột phải -> paste (dán) folder **flutter** vào.
- Truy cập vào folder **flutter** và chọn vào folder **bin** -> sao chép đường dẫn. Lúc này đường dẫn bạn sao chép sẽ giống như sau:

  ```sh
  C:\Users\<Tên_người_dùng>\develop\flutter\bin
  ```

- Mở **Edit the system environment variables** -> click chọn **Environment variables ...** -> double click **Path** trong mục **User variables** -> xuất hiện hộp thoại -> Chọn **New** -> Dán đường dẫn vừa sao chép vào -> Click **OK** -> **OK** -> **OK** (click **OK** 3 lần là xong)

#### 1.2.3 Kiểm tra phiên bản Flutter:

Mở terminal lên (vào tìm kiếm gõ terminal sau đó nhập lệnh dưới đây)

```bash
flutter --version
```

Nếu xuất hiện các dòng cuối như dưới đây là đã cài thành công:

```bash
Flutter 3.35.4 • channel stable • https://github.com/flutter/flutter.git
Framework • revision d693b4b9db (3 months ago) • 2025-09-16 14:27:41 +0000
Engine • hash feee8ee8fb8b975dd9990f86d3bda11e6e75faf3 (revision c298091351) (3 months ago) •
2025-09-15 14:04:24.000Z
Tools • Dart 3.9.2 • DevTools 2.48.0
```

> **Lưu ý**: Lần đầu sẽ hơi lâu, chịu khó đợi

### 1.3. IDE khuyến nghị

- **Android Studio** (Khuyên dùng, dành cho người mới bắt đầu)
- **VS Code** (khó sử dụng hơn vì cần phải setup nhiều thứ)
  - link tham khảo: [https://docs.flutter.dev/install/with-vs-code](https://docs.flutter.dev/install/with-vs-code)
  - Flutter extension
  - Dart extension

| Đối tượng           | Nên dùng              |
| ------------------- | --------------------- |
| Người mới           | Android Studio        |
| Có máy Android thật | VS Code               |
| Máy yếu             | VS Code + device thật |

Bên dưới mình sẽ hướng dẫn cả hai trường hợp.

#### 1.3.1 Cài đặt Android Studio để chạy dự án

- link tham khảo cách cài đặt: [https://docs.flutter.dev/tools/android-studio#setup](https://docs.flutter.dev/tools/android-studio#setup)

#### 1.3.2 Cài đặt VSCode để chạy dự án

- Vào đường link này cài đặt theo hệ điều hành: [https://code.visualstudio.com/Download](https://code.visualstudio.com/Download)
  - Ví dụ hệ điều hành windows thì nhấp vào download cho windows, ... tương tự với các hệ điều hành khác.
- Tải về cài đặt xong thì tiến hành cài các extension có tên như sau:
  - Flutter
  - Dart (nếu cài flutter xong nó tự động cài luôn thì ok, nếu không thì phải tự cài nhé).
- Chọn cái nhiều lượt tải nhất.

### 1.4. Thiết bị chạy thử

- Android Emulator **hoặc**
- Điện thoại Android thật (bật USB Debugging)

> **Chú ý** Chỉ nên sử dụng hai cách mình nói trên để có thể kết nối MQTT dễ dàng mà không cần tinh chỉnh quá rườm rà.

> Một số lưu ý nhỏ cho những người cài đặt vscode như sau
>
> - chạy máy ảo khá khó khăn vì vscode không tự tải các Android SDK, Android Emulator, AVD (Android Virtual Device).
> - do đó theo như những gì mình tìm hiểu -> vẫn cài **android studio** nhưng cài đặt để sử dụng các tính năng cần thiết là hợp lý nhất trừ khi bạn có máy thật.
> - link video hướng dẫn (xem video 3, 4, 5, 6 hoặc xem đến video 9 để chạy trên android studio):
>   [https://www.youtube.com/playlist?list=PL3Ob3F0T-08brnWfs8np2ROjICeT-Pr6T](https://www.youtube.com/playlist?list=PL3Ob3F0T-08brnWfs8np2ROjICeT-Pr6T)
> - Lưu ý sau khi làm theo video thì phải tạo trước máy ảo trên **android studio** để khỏi cần phải tạo sau nhé.

**Tạo máy ảo trên Android Studio**:

- Vào **Android Studio** và nhấp vào `More Actions:` ngay bên dưới các mục `New Project`, `Open`, `Clone Repository`

  <img width="978" height="791" alt="android-1" src="https://github.com/user-attachments/assets/70bd8ba4-fa43-4740-bd52-e9fe09757ba5" />

- Chọn `Virtual Device Manager`:
  <img width="958" height="796" alt="virtualMachine" src="https://github.com/user-attachments/assets/a01fbd98-d63d-4dfc-941e-c707374a56c3" />

- Chọn `Create virtual device...` nếu chưa có máy ảo nào:
  <img width="985" height="796" alt="create-virtual-device" src="https://github.com/user-attachments/assets/60b77edc-4ad1-4160-ab28-12aeb7599d40" />

- Chọn loại thiết bị và bấm `Next` -> `Finish`.
  <img width="1126" height="846" alt="choose" src="https://github.com/user-attachments/assets/43bf4796-3a44-4164-bb78-829eb29202be" />

- Đợi tải các **package** cần thiết là ok.

Kiểm tra thiết bị:

- Nếu sử dụng thiết bị thật thì dùng lệnh này
  ```bash
  flutter devices
  ```
- Còn máy ảo thì kiểm tra máy ảo vừa tạo đã có chưa và launch thử bằng lệnh này:

  ```bash
  flutter emulators
  ```

  => Xuất hiện <tên_máy> và id máy. Copy <id_máy>

  ```bash
  flutter emulators --launch <id_máy> --cold
  ```

  => máy xuất hiện là ok.

---

## 2. Clone / Tải source code dự án

### 2.1. Clone bằng Git

- Tải git từ trang web theo đường link này:
  [https://git-scm.com/install/](https://git-scm.com/install/)

Ví dụ cho hệ điều hành Windows:
<img width="1337" height="899" alt="git" src="https://github.com/user-attachments/assets/b8721a55-3f9b-4fa6-a27b-7f8857093832" />

Theo như trang, các bạn bật terminal lên và tải bằng lệnh dưới đây:

```bash
winget install --id Git.Git -e --source winget
```

Hoặc nhấp vào các đường link của trang để tải git về.

cài đặt xong kiểm tra bằng lệnh sau:

```bash
git --version
```

Hiển thị ra phiên bản của nó như ví dụ dưới này là ok

```bash
git version 2.52.0.windows.1
```

Cài đặt xong tiến hành clone dự án như hướng dẫn dưới đây:

- Bước 1: Truy cập vào thư mục cần lưu dự án:  
  Ví dụ như lưu ở `C:\Users\<Tên_người_dùng>\Desktop`

- Bước 2: Mở terminal lên và nhập lệnh như dưới đây

```bash
git clone <repository_url>
cd <project_name>
```

Với:

- **<repository_url>**: [https://github.com/HTKFOOLISH/source_dart_code_folder.git](https://github.com/HTKFOOLISH/source_dart_code_folder.git)
- **<project_name>**: source_dart_code_folder

### 2.2. Hoặc tải file ZIP

1. Download ZIP từ repository
2. Giải nén
3. Mở thư mục bằng VS Code

---

## 3. Cài đặt dependencies

Tại thư mục gốc của dự án (source_dart_code_folder):

- Truy cập vào folder. Ví dụ đường dẫn đầy đủ:
  C:\Users\<Tên_người_dùng>\Desktop\source_dart_code_folder\CK\Take\test_folders\num_1_test -> Mở VSCode lên (`Ctrl + ~`) nhập:

  ```bash
  flutter pub get
  ```

- Sau đó kiểm tra xem nếu không có thiết bị thật thì chạy thiết bị ảo bằng các lệnh sau:
  - Kiểm tra các thiết bị ảo:

  ```bash
  flutter emulators
  ```

  - Nếu không có (hiển thị No emulators available.) thì tạo mới như trong mục [1.4. Thiết bị chạy thử](#14-thiết-bị-chạy-thử)

  - Còn nếu có thì copy <id_máy> và chạy:

  ```bash
  flutter emulators --launch <id_máy> --cold
  ```

Lệnh này sẽ:

- Tải toàn bộ package trong `pubspec.yaml`
- Tạo file `.packages` và `.dart_tool/`

---

## 4. Cấu hình môi trường (Quan trọng)

### 4.1. Flutter doctor

Chạy lệnh:

```bash
flutter doctor
```

Đảm bảo **không có lỗi nghiêm trọng** (❌). Các cảnh báo (⚠️) về iOS có thể bỏ qua nếu chỉ chạy Android.

---

## 5. Cấu trúc dự án (Overview)

```text
lib\
 ┣ models\
 ┣ mqtt\
 ┣ routing\
 ┣ state\
 ┣ ui\
 ┣ main.dart
 ┗ my_app.dart
```

---

## 6. Cấu hình MQTT

Dự án sử dụng **HiveMQ Cloud** với:

- Port: `8883`
- Giao thức: **MQTT over TLS**

Lưu ý:

- Dữ liệu hiện tại là **dữ liệu mô phỏng (mock / ảo)**
- Không yêu cầu phần cứng thật

### 6.1 Tạo Cloud Clusters

Truy cập link [https://www.hivemq.com/](https://www.hivemq.com/) để vào trang HiveMQ Cloud.

<img width="1918" height="906" alt="hiveMQ_img1" src="https://github.com/user-attachments/assets/5652718c-093e-4bb0-b728-2e92f86c2df8" />

Đăng nhập/Đăng ký bằng tài khoản google của bạn.
<img width="1899" height="898" alt="hiveMQ_img2" src="https://github.com/user-attachments/assets/9d390232-45a0-4028-867c-4bf641eb5f7a" />

Sau khi đăng nhập/đăng ký thành công thì sẽ hiển thị như bên dưới và nhấp chọn `Cloud Clusters` phía bên trái.
<img width="1919" height="907" alt="hiveMQ_img3" src="https://github.com/user-attachments/assets/3925dc3c-63e8-4d28-b437-0fe5d9def788" />

Chọn `Create New Cluster`
<img width="1919" height="842" alt="hiveMQ_img4" src="https://github.com/user-attachments/assets/76a9915e-05d2-44fb-8b17-1c5d4284713f" />

Chọn `Serverless` (FREE)
<img width="1918" height="843" alt="hiveMQ_img5" src="https://github.com/user-attachments/assets/99eec582-7a32-4688-9378-2c1bac5f308d" />

Cái bạn vừa tạo là `Free #1`, nhấp chọn `Manage Cluster`
<img width="1919" height="442" alt="hiveMQ_img6" src="https://github.com/user-attachments/assets/720269b3-5a0d-40f4-8d8e-28313ae87d02" />

Copy đường dẫn URL có dạng `af******.s1.eu.hivemq.cloud` như hình và lưu vào notepad. Vào `Access Management`
<img width="1915" height="845" alt="hiveMQ_img7" src="https://github.com/user-attachments/assets/28361a04-b402-41d5-8d9a-bc40c4d318d6" />

Nhấp chọn `Edit` tại `Credentials` của mục `Authentication`
<img width="1919" height="699" alt="hiveMQ_img8" src="https://github.com/user-attachments/assets/d3f09a48-2582-4e74-bd4d-154c5b328575" />

Chọn `Add Credentials`
<img width="1543" height="621" alt="hiveMQ_img9" src="https://github.com/user-attachments/assets/57ab8a8d-cd85-4d33-9fb0-c901de30b580" />

Nhập `Username`, `Password`, Xác nhận lại password tại `Confirm Password`. Lưu ý: lưu lại `Username`, `Password` vào notepad để sử dụng sau.
<img width="1547" height="656" alt="hiveMQ_img10" src="https://github.com/user-attachments/assets/2c830c3a-f865-486c-a732-cf3aa682cae5" />

Trong mục `Premission` chọn `Publish and Subscribe`
<img width="1594" height="531" alt="hiveMQ_img11" src="https://github.com/user-attachments/assets/21ac5b4f-9684-406e-b10a-91278d1a8182" />

Sau đó nhấn `Save`. Lúc này sẽ hiển thị như ảnh dưới.
<img width="1919" height="794" alt="hiveMQ_img12" src="https://github.com/user-attachments/assets/b1e10b5e-38e9-4c4c-9395-6f1408ce9431" />

Vào mục `Web Client` nhập lại `Username`, `Password` mà bạn vừa tạo và bấm chọn `Connect`.
<img width="1919" height="772" alt="hiveMQ_img13" src="https://github.com/user-attachments/assets/f35fdda2-dc8a-40ca-8738-f52d301fce23" />

Như này là bạn đã setup thành công cho web.
<img width="1917" height="912" alt="hiveMQ_img14" src="https://github.com/user-attachments/assets/ddb121d4-58d5-4ba3-99d6-c97b70a8ac5f" />

### 6.2 Sửa lại file dart để thấy thành quả

- Truy cập vào folder như hướng dẫn cách vào nơi chứa thư mục tại mục [3. Cài đặt dependencies](#3-cài-đặt-dependencies)

- Lúc này bạn sẽ thấy cấu trúc thư mục sẽ như thế này:

  ```bash
  num_1_test
  ┣ .dart_tool
  ┣ .idea
  ┣ android
  ┣ assets
  ┣ build
  ┣ ios
  ┣ lib
  ┣ linux
  ┣ macos
  ┣ test
  ┣ web
  ┣ windows
  ┣ .flutter-plugins-dependencies
  ┣ .gitignore
  ┣ .metadata
  ┣ analysis_options.yaml
  ┣ architecture_structure.md
  ┣ devtools_options.yaml
  ┣ num_1_test.iml
  ┣ pubspec.lock
  ┣ pubspec.yaml
  ┗ README.md
  ```

- Vào thư mục `\lib`, chọn file `main.dart`:
  ```bash
  \lib
  ┣ \models
  ┣ \mqtt
  ┣ \routing
  ┣ \state
  ┣ \ui
  ┣ main.dart # file này
  ┗ my_app.dart
  ```
- Từ `dòng 25` đến `dòng 27` sẽ hiển thị như sau:

  ```dart
    // ĐIỀN THÔNG TIN THẬT 3 dòng dưới đây
  const hivemqHost = 'af1af10d2f264a09a3e2dac9ced2e126.s1.eu.hivemq.cloud';
  const hivemqUser = 'flutter_user';
  const hivemqPass = 'StrongPass!234';
  ```

  - Với:
    - **hivemqHost**: URL
    - **hivemqUser**: Username
    - **hivemqPass**: password

  - Thay ba dòng đó thành `URL`, `Username` và `Password` của bạn (những thứ được lưu trong notepad)

- Đến bước này là xong.

---

## 7. Chạy ứng dụng

### 7.1. Chạy bằng VS Code

1. Mở file `lib/main.dart`
2. Chọn thiết bị ở thanh dưới (Android Emulator / Device)
3. Nhấn **Run ▶** hoặc `F5`

### 7.2. Chạy bằng terminal

```bash
flutter run
```

### 7.3 Kết quả hiển thị

Sau khi chạy app thì sẽ có hiển thị màn hình sau:
<img width="1919" height="1016" alt="result_img1" src="https://github.com/user-attachments/assets/8e638f0b-df02-43e5-92f1-16773ed5e2e4" />

Tài khoản được sử dụng để đăng nhập mặc định là:

```bash
username: admin
password: 123
```

Nhập tài khoản trên và nhấn `Sign In` để vào app.
<img width="1919" height="1016" alt="result_img2" src="https://github.com/user-attachments/assets/8e1c8515-bee4-4441-8628-ff98bdda9dc9" />

Lúc này bên web `HiveMQ Cloud`, mục `Message` chưa hiển thị gì cả.
<img width="1147" height="844" alt="result_img3" src="https://github.com/user-attachments/assets/f61a64ff-eb4d-41c3-a09a-c81fd7402c37" />

Nhấp vào thẻ phòng bất kỳ -> nếu có dòng `Message` nào hiển thị lên thì kết nối MQTT từ app đến web client là thành công. Sau đó bạn cũng có thể bật tắt các thiết bị hiển thị trên app để test.
<img width="1919" height="1016" alt="result_img4" src="https://github.com/user-attachments/assets/0f6dd882-1d7f-42f7-955b-e44fe1ddc8b2" />

Nếu muốn test kết quả trả về để kiểm tra kết nối MQTT từ `Web client` đến app ta làm như sau Trên `Web client` ta tiến hành:

- Vào mục `Send Message`.
  <img width="757" height="477" alt="result_img5" src="https://github.com/user-attachments/assets/4f9d735b-2eed-48fc-9d8b-67b3a0624fb0" />

- Trong phần `topic`, ta nhập theo dạng như sau:

  ```bash
  home/rooms/<Your_Id_Room>/command # thay đổi trạng thái của thiết bị
  home/rooms/<Your_Id_Room>/snapshot # thay đổi giá trị cảm biến
  ```

  Với <Your_Id_Room> là id của phòng, có thể xem trong mục `Message` để biết phòng bạn có id phòng là bao nhiêu.

- Dưới đây là dạng file `json` mà được sử dụng để thay đổi giá trị cho:
  - sensor:
    ```json
    {
      "roomId": "<Your_Id_Room>",
      "sensors": [
        { "id": "temp", "value": 26.5 },
        { "id": "hum", "value": 58 }
      ]
    }
    ```
  - device:
    ```json
    {
      "roomId":"<Your_Id_Room>",
      "devices":[
        {"id":"ceiling-light","on":<boolean_value>}
      ]
    }
    ```
    Với **<boolean_value>**: nhập true hoặc false để thể hiện giá trị được tắt/bật của thiết bị.

- **Vậy làm sao biết được mấy cái dạng json này viết gì ở bên trong mà test?**
  > Câu trả lời là nhìn vào các **message** trong mục **Message** của `Web Client` mỗi khi bạn đẩy dữ liệu từ app của bạn lên `HiveMQ Cloud` bằng cách nhấp vào thẻ phòng để thấy được cấu trúc file `json` của sensor và tương tự như vậy nhấp vào nút của thiết bị để hiển thị **message** của nó (file `json`).

---

## 8. Các lỗi thường gặp & cách xử lý

### Lỗi sai version Flutter

```text
Because package X requires Flutter >=...
```

Giải pháp:

```bash
flutter downgrade 3.35.4
```

Hoặc dùng **FVM** để quản lý version.

---

### Không nhận device

```text
No devices found
```

Kiểm tra:

- Emulator đã chạy chưa
- USB Debugging đã bật chưa
- Cài driver (Windows)

---

### Lỗi pub get

```text
Could not resolve dependencies
```

Thử:

```bash
flutter clean
flutter pub get
```

---

## 9. Lệnh Flutter thường dùng

```bash
flutter clean            # Xoá build cache
flutter pub get          # Cài package
flutter run              # Chạy app
flutter build apk        # Build APK
flutter doctor           # Kiểm tra môi trường
```

---

## 10. Liên hệ & hỗ trợ

Nếu gặp lỗi khi chạy dự án, vui lòng:

1. Chụp màn hình lỗi
2. Gửi log terminal
3. Mô tả thiết bị & OS

Sau đó liên hệ qua mail hoặc số điện thoại:

- mail: khaihtk2004@gmail.com
- số điện thoại: 0369217008

---

**Mến chào,**  
Môn Lập trình ứng dụng - Nhóm 6 - buổi sáng thứ 4 (đợt 1)
