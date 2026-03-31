# Template Đồ Án / Luận Văn (LaTeX)

Đây là template LaTeX tiêu chuẩn dành cho việc viết đồ án, luận văn, báo cáo. Mọi thiết lập về định dạng, căn lề, trích dẫn chuẩn APA đã được cấu hình sẵn.

## 🚀 Tính năng nổi bật
- **Biên dịch thông minh**: Tự động reload (`latexmk -pvc`), đẩy file `main.pdf` ra thư mục gốc để dễ xem.
- **Trích dẫn APA**: Cấu hình chuẩn `biblatex` với style APA.
- **Căn lề**: Căn trái toàn bộ văn bản (mặc định) giúp văn bản không bị giãn chữ bất thường.

## 📦 Yêu cầu hệ thống
- Cài đặt Docker & Docker Compose.
- Sử dụng VS Code cùng extension LaTeX Workshop (nếu có để hỗ trợ gõ).

## 🛠 Hướng dẫn sử dụng

### 1. Khởi chạy dự án
Chạy lệnh gốc trong terminal để khởi động dự án:
```bash
docker compose up -d
```
Container sẽ tự động chạy ngầm, theo dõi thay đổi trong các file `.tex` của bạn và cập nhật liên tục vào file `main.pdf` nằm ở thư mục gốc.

### 2. Sửa thông tin
- **Bìa (Cover)**: Sửa file `frontmatter/cover.tex`. Thay thế các đoạn chữ như `<TÊN ĐẠI HỌC>`, `<TÊN KHOA>` bằng thông tin thực tế.
- **Tóm tắt, Lời cảm ơn**: Nằm ở thư mục `frontmatter/`.
- **Nội dung chương**: Sửa trong thư mục `chapters/`. Bạn có thể thay đổi tên file hoặc thêm các chương tuỳ ý, sau đó nhớ đưa vào file `main.tex` bằng cấu trúc `\include{chapters/ten-file}`.

### 3. Cách thêm Tham khảo (Citation) chuẩn APA
Hãy mở file `bibliography.bib` và thêm thông tin tài liệu. Sau đó dùng lệnh trong file `.tex`:
- Trích dẫn ngay trong dòng: `\textcite{id_tai_lieu}` -> Tác giả (2024) khẳng định...
- Trích dẫn trong ngoặc: `\parencite{id_tai_lieu}` -> ...(Tác giả, 2024).

### 4. Cách chuyển qua Căn lề Đều 2 Bên (Justified)
Template này mặc định đặt **Căn Trái** toàn bộ (giúp tránh chữ bị giãn cách quá lớn vì ngôn ngữ tiếng Việt). Nếu trường của bạn **bắt buộc** phải dàn đều chữ 2 bên, bạn chỉ cần làm như sau:
1. Mở file `preamble.tex`.
2. Tìm dòng có chữ `\usepackage[document]{ragged2e}`.
3. Thêm dấu `%` vào trước nó như thế này: `% \usepackage[document]{ragged2e}` hoặc xóa hẳn dòng này đi.

### 5. Cách chèn ảnh / bảng / thuật toán / công thức
- Bạn có thể tham khảo file `chapters/chapter1_template.tex` (nếu có) hoặc xem `chapters/insertanh.txt` để biết một vài cú pháp cơ bản thường dùng khi viết bài.
- Ảnh được đặt ở trong thư mục `images/`.

## 🛑 Lưu ý quan trọng
- Khi thay thế tên biến `<TÊN GÌ ĐÓ>`, hãy **bỏ cả dấu ngoặc `<` và `>`**. Ví dụ: `ĐẠI HỌC BÁCH KHOA HÀ NỘI`.
- Đừng dùng ngoặc vuông `[...]` liền ngay sau dấu xuống dòng `\\` bên trong template, vì biên dịch LaTeX hay hiểu lầm đó là câu lệnh canh lề xuống dòng (như sinh ra lỗi `ÊN KHOA`).
