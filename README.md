# 📱 LAB F3 – NHẬP LIỆU & FORM TRONG FLUTTER

## 📌 1. Thông tin sinh viên và dự án

| Thông tin | Nội dung |
|---|---|
| Họ và tên | Nguyễn Thị Hồng Thắm |
| Mã số sinh viên | 241A010134 |
| Lớp | CNTT – LTDD |
| Trường | Đại học Văn Hiến |
| Môn học | Lập trình trên các thiết bị di động |
| Mã học phần | INT4211 |
| Bài thực hành | Lab F3 – Nhập liệu & Form trong Flutter |
| Tên ứng dụng | F3_241A010134 |
| Tên project | f3_form |
| Ngôn ngữ lập trình | Dart |
| Framework | Flutter |
| Giao diện | Material Design 3 |
| Bài nâng cao | NC1 và NC2 |

---

## 📖 2. Giới thiệu dự án

Lab F3 xây dựng ứng dụng **Đăng ký học phần** bằng Flutter, cho phép sinh viên nhập thông tin cá nhân, lựa chọn học phần, hệ đào tạo, buổi học và các tùy chọn đăng ký.

Ứng dụng sử dụng `Form` kết hợp `GlobalKey<FormState>` để quản lý biểu mẫu và kiểm tra tính hợp lệ của dữ liệu.

Ngoài các chức năng cơ bản, dự án triển khai hai bài nâng cao:

- **NC1:** Thêm chức năng chọn ngày sinh bằng `showDatePicker()`.
- **NC2:** Kiểm tra điều kiện phụ thuộc giữa hệ đào tạo và buổi học.

Dự án giúp sinh viên làm quen với việc xây dựng biểu mẫu, xử lý tương tác, quản lý trạng thái và kiểm tra dữ liệu trong Flutter.

---

## 🎯 3. Mục tiêu thực hành

Sau khi hoàn thành Lab F3, sinh viên có thể:

1. Sử dụng `TextFormField` để xây dựng các trường nhập liệu.
2. Quản lý nội dung nhập bằng `TextEditingController`.
3. Sử dụng `Form` và `GlobalKey<FormState>` để kiểm tra, đặt lại biểu mẫu.
4. Xây dựng các hàm `validator` để kiểm tra dữ liệu.
5. Giới hạn dữ liệu nhập bằng `keyboardType` và `inputFormatters`.
6. Sử dụng `DropdownButtonFormField`, `RadioGroup`, `RadioListTile`, `CheckboxListTile`, `SwitchListTile` và `Slider`.
7. Quản lý trạng thái giao diện bằng `StatefulWidget` và `setState()`.
8. Hiển thị thông báo bằng `SnackBar` và hộp thoại xác nhận bằng `AlertDialog`.
9. Sử dụng `showDatePicker()` để chọn ngày sinh.
10. Xây dựng điều kiện kiểm tra phụ thuộc giữa các thành phần trong biểu mẫu.
11. Đối chiếu cách xây dựng biểu mẫu giữa Android (Java/XML) và Flutter (Dart).

---

## 🛠️ 4. Công nghệ và môi trường phát triển

| Công nghệ / Công cụ | Vai trò |
|---|---|
| Flutter SDK | Framework phát triển ứng dụng đa nền tảng |
| Dart | Ngôn ngữ lập trình chính |
| Material Design 3 | Xây dựng giao diện ứng dụng |
| Visual Studio Code | Soạn thảo và quản lý mã nguồn |
| Android SDK | Hỗ trợ xây dựng và chạy ứng dụng Android |
| Android Emulator | Chạy thử và kiểm tra ứng dụng |
| Git | Quản lý phiên bản mã nguồn |
| GitHub | Lưu trữ và chia sẻ repository |

### Các thư viện sử dụng

Ứng dụng sử dụng các thư viện có sẵn của Flutter:

```dart
import 'package:flutter/material.dart';
import 'package:flutter/services.dart';
```

- `material.dart`: Cung cấp các widget giao diện Material Design.
- `services.dart`: Cung cấp các công cụ kiểm soát dữ liệu nhập như `FilteringTextInputFormatter` và `LengthLimitingTextInputFormatter`.

Hai bài nâng cao NC1 và NC2 không yêu cầu cài đặt thêm package bên ngoài.

---

## 📂 5. Cấu trúc dự án

Cấu trúc các thành phần chính của project Flutter:

```text
f3_form/
├── android/
├── ios/
├── lib/
│   └── main.dart
├── test/
├── pubspec.yaml
├── pubspec.lock
├── analysis_options.yaml
├── .gitignore
└── README.md
```

### Vai trò các file và thư mục

| File / Thư mục | Chức năng |
|---|---|
| `lib/main.dart` | Chứa giao diện và logic xử lý biểu mẫu đăng ký học phần |
| `pubspec.yaml` | Khai báo thông tin project, dependencies và cấu hình Flutter |
| `pubspec.lock` | Ghi nhận các phiên bản dependency đã được giải quyết |
| `android/` | Cấu hình ứng dụng cho nền tảng Android |
| `ios/` | Cấu hình ứng dụng cho nền tảng iOS |
| `test/` | Thư mục dành cho các bài kiểm thử Flutter |
| `analysis_options.yaml` | Cấu hình phân tích mã nguồn Dart |
| `.gitignore` | Loại trừ các file không cần thiết khỏi Git |
| `README.md` | Tài liệu giới thiệu và hướng dẫn sử dụng dự án |

*Lưu ý: Đây là cấu trúc Flutter tiêu chuẩn; các thư mục nền tảng thực tế phụ thuộc vào cấu hình khi tạo project.*

---

## ⚙️ 6. Các chức năng cơ bản

### 6.1. Nhập thông tin sinh viên

Biểu mẫu cung cấp các trường nhập:

- Họ và tên.
- Mã số sinh viên.
- Email.

Các trường được xây dựng bằng `TextFormField` và quản lý bằng `TextEditingController`.

Ứng dụng sử dụng các hàm kiểm tra:

```dart
_kiemTraHoTen()
_kiemTraMssv()
_kiemTraEmail()
```

**Quy tắc kiểm tra dữ liệu:**

| Trường | Điều kiện hợp lệ |
|---|---|
| Họ tên | Không rỗng, tối thiểu 3 ký tự |
| MSSV | Gồm đúng 10 chữ số |
| Email | Không rỗng, đúng định dạng email theo biểu thức chính quy của ứng dụng |
| Học phần | Bắt buộc chọn một học phần |

Đối với MSSV, ứng dụng sử dụng:

```dart
FilteringTextInputFormatter.digitsOnly
LengthLimitingTextInputFormatter(10)
```

Nhờ đó, trường MSSV chỉ chấp nhận chữ số và giới hạn tối đa 10 ký tự.

### 6.2. Chọn học phần

Sử dụng `DropdownButtonFormField<String>` để hiển thị danh sách học phần:

- Lập trình di động.
- Cơ sở dữ liệu.
- Trí tuệ nhân tạo.
- Kiểm thử phần mềm.

Người dùng bắt buộc phải chọn một học phần trước khi đăng ký.

### 6.3. Chọn hệ đào tạo

Sử dụng `RadioGroup<String>` kết hợp `RadioListTile<String>`.

Ứng dụng hỗ trợ hai hệ đào tạo:

- Chính quy.
- Vừa làm vừa học.

Giá trị mặc định là **Chính quy**.

### 6.4. Chọn buổi học

Sử dụng `CheckboxListTile` để cho phép chọn nhiều buổi học:

- Sáng.
- Chiều.
- Tối.

Các buổi học được lưu trong tập hợp:

```dart
final Set<String> _buoiDaChon = {};
```

Người dùng phải chọn ít nhất một buổi học trước khi đăng ký.

### 6.5. Chọn số tín chỉ

Sử dụng `Slider` để lựa chọn số tín chỉ đăng ký.

| Thuộc tính | Giá trị |
|---|---|
| Giá trị nhỏ nhất | 10 |
| Giá trị lớn nhất | 24 |
| Giá trị mặc định | 15 |
| Số khoảng chia | 14 |

Giá trị được cập nhật trên giao diện khi người dùng di chuyển Slider.

### 6.6. Nhận thông báo qua email

Sử dụng `SwitchListTile` để bật hoặc tắt tùy chọn nhận thông báo.

Giá trị mặc định là `true`, tương ứng với trạng thái bật.

### 6.7. Xác nhận đăng ký

Khi nhấn nút **ĐĂNG KÝ**, ứng dụng thực hiện:

1. Gọi `validate()` để kiểm tra các trường thuộc `Form`.
2. Kiểm tra người dùng đã chọn ít nhất một buổi học.
3. Kiểm tra điều kiện phụ thuộc của bài nâng cao NC2.
4. Hiển thị `AlertDialog` nếu tất cả điều kiện hợp lệ.

Hộp thoại xác nhận hiển thị thông tin đăng ký gồm họ tên, ngày sinh, MSSV, email, học phần, hệ đào tạo, buổi học, số tín chỉ và trạng thái nhận thông báo.

### 6.8. Làm lại biểu mẫu

Nút **Làm lại** đưa biểu mẫu về trạng thái ban đầu bằng cách:

- Gọi `FormState.reset()`.
- Xóa nội dung các `TextEditingController`.
- Đưa ngày sinh về trạng thái chưa chọn.
- Xóa học phần đã chọn.
- Đặt hệ đào tạo về Chính quy.
- Xóa các buổi học đã chọn.
- Bật lại tùy chọn nhận thông báo.
- Đưa Slider về 15 tín chỉ.

---

## 🚀 7. Bài nâng cao

### 7.1. NC1 – Thêm chức năng chọn ngày sinh

**Mục tiêu:** Bổ sung chức năng chọn ngày sinh vào biểu mẫu bằng `showDatePicker()` và hiển thị theo định dạng `dd/MM/yyyy`.

**Cách thực hiện:**

- Khai báo biến `_ngaySinh` kiểu `DateTime?`.
- Sử dụng `showDatePicker()` để hiển thị lịch.
- Giới hạn khoảng chọn ngày từ năm 1900 đến ngày hiện tại.
- Xây dựng hàm `_dinhDangNgay()` để định dạng ngày tháng.
- Sử dụng `InkWell` và `InputDecorator` để tạo ô chọn ngày sinh.
- Cập nhật ngày sinh bằng `setState()`.
- Bổ sung ngày sinh vào hộp thoại xác nhận.
- Xóa ngày sinh khi nhấn Làm lại.

**Kết quả:** Người dùng có thể mở lịch, chọn ngày sinh và xem ngày đã chọn trong biểu mẫu. Ngày sinh cũng được hiển thị trong hộp thoại xác nhận đăng ký.

Khi nhấn Làm lại, ô ngày sinh trở về trạng thái ban đầu.

### 7.2. NC2 – Kiểm tra phụ thuộc giữa hệ đào tạo và buổi học

**Mục tiêu:** Nếu chọn hệ **Vừa làm vừa học**, người dùng bắt buộc phải chọn buổi **Tối**.

**Cách thực hiện:**

Bổ sung điều kiện kiểm tra trong hàm `_dangKy()`:

```dart
if (_heDaoTao == 'Vừa làm vừa học' &&
    !_buoiDaChon.contains('Tối')) {
  ScaffoldMessenger.of(context).showSnackBar(
    const SnackBar(
      content: Text(
        'Hệ Vừa làm vừa học bắt buộc chọn buổi Tối',
      ),
    ),
  );
  return;
}
```

**Nguyên lý hoạt động:**

- Kiểm tra hệ đào tạo hiện tại.
- Kiểm tra tập hợp buổi học có chứa `Tối` hay không.
- Nếu điều kiện không hợp lệ, hiển thị `SnackBar`.
- Sử dụng `return` để dừng quá trình đăng ký.

**Kết quả:** Ứng dụng chỉ cho phép hệ Vừa làm vừa học đăng ký khi danh sách buổi học có chứa buổi Tối.

Người dùng vẫn có thể chọn thêm các buổi khác nếu đã chọn Tối.

---

## 🧪 8. Kiểm thử ứng dụng

### 8.1. Kiểm thử chức năng cơ bản

| STT | Kịch bản | Kết quả mong đợi |
|---|---|---|
| 1 | Nhấn ĐĂNG KÝ khi biểu mẫu trống | Hiển thị lỗi tại các trường bắt buộc và SnackBar yêu cầu chọn buổi học |
| 2 | Nhập MSSV không đủ 10 chữ số | Hiển thị lỗi MSSV |
| 3 | Nhập email sai định dạng | Hiển thị lỗi email |
| 4 | Không chọn học phần | Hiển thị thông báo yêu cầu chọn học phần |
| 5 | Nhập đầy đủ thông tin hợp lệ | Hiển thị hộp thoại xác nhận |
| 6 | Nhấn Làm lại | Các trường trở về trạng thái ban đầu |

### 8.2. Kiểm thử bài nâng cao NC1

| Kịch bản | Kết quả |
|---|---|
| Nhấn ô ngày sinh | Hiển thị lịch chọn ngày |
| Chọn ngày 02/03/2006 | Hiển thị đúng định dạng `02/03/2006` |
| Xác nhận đăng ký | Hộp thoại hiển thị ngày sinh |
| Nhấn Làm lại | Ngày sinh trở về trạng thái chưa chọn |

**Đánh giá:** Đạt yêu cầu kiểm thử NC1.

### 8.3. Kiểm thử bài nâng cao NC2

| Hệ đào tạo | Buổi học | Kết quả |
|---|---|---|
| Chính quy | Sáng | Đăng ký thành công khi biểu mẫu hợp lệ |
| Vừa làm vừa học | Chiều | Hiển thị SnackBar yêu cầu chọn buổi Tối |
| Vừa làm vừa học | Chiều + Tối | Đăng ký thành công khi biểu mẫu hợp lệ |

**Đánh giá:** Đạt yêu cầu kiểm thử NC2.

---

## 🔄 9. Bảng đối chiếu Android ↔ Flutter

Bảng đối chiếu dựa trên Lab A4, A6 (Android) và Lab F3 (Flutter).

| Chức năng | Android (Java/XML) | Flutter (Dart) | Dòng trong `main.dart` |
|---|---|---|---|
| Nhập văn bản | `EditText` + `inputType` | `TextFormField` + `keyboardType` | 184–217 |
| Chọn một mục từ danh sách | `Spinner` + `ArrayAdapter` | `DropdownButtonFormField` + `items` | 238–252 |
| Chọn một lựa chọn | `RadioGroup` + `RadioButton` | `RadioGroup` + `RadioListTile` | 257–274 |
| Chọn nhiều mục | `CheckBox` | `CheckboxListTile` + `Set` | 45, 279–291 |
| Bật/tắt | `Switch` / `ToggleButton` | `SwitchListTile` | 305–310 |
| Chọn giá trị trong khoảng | `SeekBar` | `Slider` | 296–303 |
| Báo lỗi nhập liệu | `setError()` | `validator` | 59–78, 191, 206, 216, 251 |
| Thông báo ngắn | `Toast` | `SnackBar` | 114–119, 122–131 |
| Chọn ngày | `DatePickerDialog` | `showDatePicker()` | 80–100, 220–234 |

*Các số dòng được xác định từ phiên bản `main.dart` đã cung cấp. Số dòng có thể thay đổi khi chỉnh sửa mã nguồn.*

### Nhận xét

Android sử dụng XML để khai báo giao diện và Java để xử lý logic, trong khi Flutter sử dụng Dart để xây dựng giao diện bằng hệ thống widget.

Trong Android, việc kiểm tra dữ liệu thường được xử lý thủ công thông qua các điều kiện và listener. Flutter hỗ trợ cơ chế kiểm tra tập trung bằng `Form`, `GlobalKey<FormState>` và `validator`.

Ngoài ra, Flutter sử dụng `setState()` để cập nhật giao diện khi dữ liệu thay đổi.

---

## 💻 10. Hướng dẫn cài đặt và chạy ứng dụng

### 10.1. Yêu cầu môi trường

Máy tính cần cài đặt:

- Flutter SDK tương thích với project.
- Dart SDK đi kèm Flutter.
- Visual Studio Code hoặc Android Studio.
- Android SDK.
- Android Emulator hoặc thiết bị Android thật.

### 10.2. Kiểm tra môi trường

Mở Terminal và chạy:

```bash
flutter doctor
```

Kiểm tra phiên bản Flutter:

```bash
flutter --version
```

### 10.3. Mở project

Mở thư mục `f3_form` trong Visual Studio Code hoặc Android Studio.

### 10.4. Cài đặt dependencies

Chạy lệnh:

```bash
flutter pub get
```

### 10.5. Chạy ứng dụng

Khởi động Android Emulator hoặc kết nối điện thoại Android.

Kiểm tra thiết bị:

```bash
flutter devices
```

Chạy ứng dụng:

```bash
flutter run
```

### 10.6. Kiểm tra mã nguồn

```bash
flutter analyze
```

### 10.7. Làm sạch project khi cần

```bash
flutter clean
flutter pub get
flutter run
```

---

## 🧠 11. Kiến thức đạt được

Thông qua Lab F3, sinh viên đã thực hành:

- Xây dựng biểu mẫu với Flutter.
- Quản lý dữ liệu nhập bằng `TextEditingController`.
- Kiểm tra dữ liệu bằng `validator`.
- Giới hạn dữ liệu bằng `inputFormatters`.
- Sử dụng các widget lựa chọn.
- Quản lý trạng thái bằng `StatefulWidget` và `setState()`.
- Xử lý nút đăng ký và làm lại.
- Hiển thị thông báo bằng `SnackBar`.
- Hiển thị hộp thoại bằng `AlertDialog`.
- Chọn ngày sinh bằng `showDatePicker()`.
- Xây dựng điều kiện kiểm tra phụ thuộc giữa các trường.
- Giải phóng controller bằng `dispose()`.
- So sánh cách xây dựng biểu mẫu giữa Android và Flutter.

---

## ✅ 12. Kết luận

Lab F3 đã xây dựng được ứng dụng đăng ký học phần với các chức năng nhập liệu, kiểm tra dữ liệu, lựa chọn thông tin và xác nhận đăng ký.

Ứng dụng sử dụng các widget của Flutter Material Design 3, kết hợp `Form`, `TextEditingController`, `validator` và `setState()` để quản lý dữ liệu và cập nhật giao diện.

Hai bài nâng cao **NC1 – Chọn ngày sinh** và **NC2 – Kiểm tra phụ thuộc giữa hệ đào tạo và buổi học** đã được triển khai và kiểm thử theo các kịch bản yêu cầu.

Qua bài thực hành, sinh viên củng cố kiến thức về lập trình giao diện, quản lý trạng thái và xử lý biểu mẫu trong Flutter, đồng thời hiểu rõ hơn những điểm tương đồng và khác biệt giữa Flutter và Android truyền thống.

---

## 👩‍💻 13. Tác giả

**Nguyễn Thị Hồng Thắm**

- MSSV: `241A010134`
- Lớp: CNTT – LTDD
- Trường: Đại học Văn Hiến
- Môn học: Lập trình trên các thiết bị di động
- GitHub: [HTham326](https://github.com/HTham326)

---

*Tài liệu README được xây dựng phục vụ mục đích học tập và báo cáo thực hành môn Lập trình trên các thiết bị di động – Lab F3.*