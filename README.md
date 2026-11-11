# Luyện viết tiếng Anh A2–C1 — app cho máy đọc sách Boox

App Android (WebView) chạy hoàn toàn trên máy, chỉ cần mạng khi gọi Claude để chấm bài / tạo bài tập.

## 1. Tạo API key của Anthropic (một lần)
1. Vào https://console.anthropic.com và đăng ký/đăng nhập.
2. **Billing** → nạp tiền (tối thiểu 5 USD là dùng rất lâu: mỗi bài viết chấm bằng Sonnet tốn khoảng 300–800đ, mỗi câu dịch chấm bằng Haiku khoảng 20–50đ).
3. **API Keys** → *Create Key* → đặt tên (ví dụ `boox`) → sao chép key (bắt đầu bằng `sk-ant-`). Key chỉ hiện một lần, hãy lưu lại.
4. Trong app: **Cài đặt → API key → dán key → Lưu key → Kiểm tra**.

Key chỉ được lưu trong bộ nhớ của app trên máy Boox, không gửi đi đâu ngoài api.anthropic.com.

## 2. Build file APK bằng GitHub (không cần cài Android Studio)
1. Tạo tài khoản GitHub (miễn phí) nếu chưa có.
2. Tạo repository mới: **New repository** → tên `luyen-viet` → **Public** hoặc Private đều được → *Create*.
3. Vào repo vừa tạo → **Add file → Upload files** → kéo thả **toàn bộ nội dung** của thư mục này (gồm cả thư mục ẩn `.github`, file `gradlew`, thư mục `gradle`) → *Commit changes*.
   - Nếu trình duyệt không cho kéo thư mục ẩn: giải nén zip rồi kéo từng thư mục/file; hoặc dùng GitHub Desktop.
4. Vào tab **Actions** → chờ workflow "Build APK" chạy xong (3–6 phút, lần đầu lâu hơn).
5. Vào tab **Releases** (cột bên phải trang repo) → release **"latest"** → tải **LuyenViet.apk**.

Mỗi lần bạn sửa gì và upload lại, GitHub tự build APK mới vào cùng release "latest".

## 3. Cài lên Boox
1. Mở link tải APK ngay trên trình duyệt của Boox (hoặc chép file qua USB / Google Drive).
2. Mở file APK → cho phép "cài đặt từ nguồn không xác định" nếu máy hỏi → *Install*.
3. Mở app **Luyện viết** → Cài đặt → nhập API key.

Mẹo trên Boox: đặt chế độ làm mới của app là **Text/HD**; bật bàn phím viết tay của Boox để viết bằng bút.

## Cập nhật nội dung
Toàn bộ app nằm trong một file: `app/src/main/assets/index.html` (giao diện + 36 bài + 540 câu). Thay file này rồi upload lại là xong. Tăng `versionCode` trong `app/build.gradle` nếu muốn Android coi đó là bản mới.

## Nếu build lỗi
Vào Actions → bấm vào lần chạy bị đỏ → đọc dòng lỗi, hoặc gửi lại cho Claude để sửa.
