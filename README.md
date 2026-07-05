# Đề thi khảo sát — Lập trình C++ (bản web)

Trang web thi trắc nghiệm/tự luận code cho 8 câu trong đề khảo sát C++, có sẵn
bộ giám sát chống gian lận ở mức trình duyệt.

## Cách đưa lên GitHub Pages (5 phút)

1. Tạo một repo mới trên GitHub, ví dụ `de-thi-cpp`.
2. Upload file `index.html` này vào repo (kéo-thả trên GitHub web hoặc `git push`).
3. Vào **Settings → Pages**.
4. Ở mục **Source**, chọn nhánh `main` và thư mục `/ (root)`, bấm **Save**.
5. Sau khoảng 1 phút, GitHub sẽ cấp cho anh một đường link dạng:
   `https://<ten-tai-khoan>.github.io/de-thi-cpp/`
6. Gửi link đó cho học sinh làm bài trực tiếp trên trình duyệt.

Không cần cài đặt gì thêm — đây là 1 file HTML/CSS/JS thuần, không phụ thuộc
framework hay build tool nào.

## Cơ chế chống gian lận (client-side)

Trang sẽ tự động ghi nhận và cảnh báo (hiện thông báo + đếm số lần vi phạm)
khi học sinh:

- Chuyển tab / thu nhỏ trình duyệt (`visibilitychange`, `blur`)
- Thoát chế độ toàn màn hình (trang tự chuyển sang fullscreen khi bắt đầu thi)
- Dán (paste) nội dung vào ô code
- Bấm chuột phải (mở menu ngữ cảnh)
- Bấm F12 hoặc các phím tắt mở DevTools / xem mã nguồn
- Có dấu hiệu đã mở DevTools (dựa vào kích thước cửa sổ bất thường)

Khi nộp bài (hoặc hết giờ tự nộp), hệ thống tự tải xuống 2 file cho học sinh:

- `baithi_<ten>.json` — dữ liệu đầy đủ (bài làm + nhật ký vi phạm) để giáo viên
  xử lý/so sánh bằng công cụ khác nếu cần.
- `baithi_<ten>.txt` — bản đọc dễ dàng, in trực tiếp nhật ký vi phạm và bài
  làm từng câu.

Học sinh cần **gửi lại 1 trong 2 file này cho giáo viên** (qua email, Zalo,
Google Classroom...) sau khi thi, vì trang không có máy chủ lưu trữ (đây là
trang tĩnh trên GitHub Pages).

## Lưu ý quan trọng — giới hạn thực tế

Đây là công cụ giám sát **ở mức trình duyệt**, không thể:
- Ngăn học sinh dùng **điện thoại/máy tính thứ hai** để tra cứu.
- Ngăn học sinh **hỏi người khác** ngồi cạnh (không quay camera được).
- Chặn tuyệt đối việc mở DevTools trên mọi trình duyệt (một số cách vẫn có
  thể lách qua detection).

→ Để hiệu quả nhất, hãy kết hợp trang này với:
- Giám thị coi thi trực tiếp trong phòng.
- Nhiều mã đề khác số liệu (đổi input) cho các bàn cạnh nhau.
- Gọi ngẫu nhiên một vài học sinh giải thích miệng đoạn code sau khi nộp.

## Tuỳ biến

- Đổi thời gian làm bài: sửa biến `EXAM_MINUTES` trong `<script>` (mặc định 90).
- Đổi/thêm câu hỏi: sửa mảng `QUESTIONS` ở đầu phần `<script>`, mỗi câu có
  `title`, `body` (HTML), và `io` (mảng các cặp `[input, output]` hiển thị dạng bảng).
- Đổi giao diện: toàn bộ màu sắc/kiểu chữ nằm trong phần `:root{...}` ở đầu `<style>`.
