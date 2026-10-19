# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

- **Họ và tên:** Nguyễn Lê Hữu Tài
- **MSSV:** 125001425
- **Tên đề tài Website:** LUMIÈRE Cinema – Landing Page Rạp Chiếu Phim Cao Cấp, Đa Thể Loại
- **Công cụ AI đã sử dụng:** Antigravity (Google DeepMind)
- **Repository GitHub:** [https://github.com/htai1497/TaiNguyenLeHuu_125001425](https://github.com/htai1497/TaiNguyenLeHuu_125001425)
- **Live Preview (GitHub Pages):** [https://htai1497.github.io/TaiNguyenLeHuu_125001425/](https://htai1497.github.io/TaiNguyenLeHuu_125001425/)

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> *"Tôi cần xây dựng một Landing Page giới thiệu rạp chiếu phim cao cấp đa thể loại mang tên 'LUMIÈRE Cinema' cho bài thi giữa kỳ môn Thiết kế Web tại Trường Đại học Lạc Hồng.
> Yêu cầu kỹ thuật bắt buộc:
> 1. Chuẩn Semantic HTML5: Bắt buộc đủ 5 thành phần ngữ nghĩa gồm `<header>`, `<nav>`, `<main>`, `<section>` hoặc `<article>`, `<footer>`. Không lạm dụng thẻ `<div>` vô nghĩa.
> 2. Kỹ thuật CSS & CSS Variables: Khai báo đầy đủ trong `:root` cho màu vàng Gold hoàng gia (`#d4af37`), nền tối (`#0b0b10`), font chữ Cormorant Garamond và Inter, spacing nhất quán. Sử dụng Flexbox và CSS Grid responsive.
> 3. Tương tác & Hiệu ứng: Tích hợp thư viện Animate.css và AOS (Animate On Scroll), tự viết hiệu ứng `:hover`, `:focus` bằng CSS cho nút bấm và card phim.
> 4. Đặc biệt: BỎ FILE JS RA, toàn bộ bố cục, tương tác menu mobile và poster phim phải được xử lý bằng CSS thuần để bài làm tối ưu, không phát sinh lỗi trên GitHub Pages."*

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML & CSS Variable
- **Prompt đã dùng:**
  > *"Hãy xây dựng cấu trúc `index.html` cho rạp phim LUMIÈRE Cinema với đầy đủ các thẻ ngữ nghĩa: `<header>` chứa logo và menu, `<nav>` điều hướng, `<main>` chứa 5 section (Hero, Phim đang chiếu, Thể loại phim, Phim nổi bật của tháng, Gói hội viên, Liên hệ đặt vé), và `<footer>` có thẻ `<address>`. Tạo file `style.css` khai báo CSS Variables trong `:root`."*
- **Kết quả AI tạo ra:**
  - AI đã tạo ra các khối section chính, tuy nhiên phần danh sách phim và thể loại AI lại dùng thẻ `<div class="movie-card">` và `<div class="genre-item">`.
- **Nhận xét & Tinh chỉnh của SV:**
  - ⚠️ **Phát hiện lỗi:** Lạm dụng thẻ `<div>` làm giảm điểm tiêu chí 2 (Semantic HTML5).
  - 🛠️ **Yêu cầu AI sửa lại:** Thay toàn bộ thẻ `<div>` của 8 phim bằng thẻ `<article class="card movie">`, ảnh poster dùng thẻ `<figure>` và `<figcaption>`, thông số phim nổi bật dùng `<dl>`, `<dt>`, `<dd>`.

---

### Lần 2: Tích hợp thư viện Animate.css & AOS (Animate On Scroll)
- **Prompt đã dùng:**
  > *"Tích hợp link CDN của Animate.css và AOS vào `<head>`. Áp dụng Animate.css cho tiêu đề Hero (`fadeInDown`), đoạn mô tả (`fadeIn`) và nút CTA (`fadeInUp`). Áp dụng AOS cho các section và từng card phim khi cuộn trang (`data-aos="fade-up"`, `data-aos="zoom-in"`, `data-aos="flip-left"`). Không lạm dụng chuyển động quá đà gây rối mắt."*
- **Kết quả AI tạo ra:**
  - Trang web đã có hiệu ứng xuất hiện cuộn trang sinh động.
- **Thách thức gặp phải:**
  - ⚠️ **Sự cố:** Các phần tử ban đầu có thể bị giật hoặc không đồng bộ thời gian trễ khi cuộn nhanh.
- **Cách sửa prompt (Debug prompt):**
  - 🛠️ **Chỉ đạo tinh chỉnh:** *"Cấu hình `AOS.init()` với `duration: 800`, `once: true`, `offset: 60`, và thêm `easing: 'ease-out-cubic'`. Đồng thời đặt `data-aos-delay` tăng dần từ 50ms đến 300ms cho các card để tạo hiệu ứng lướt sóng mượt mà."*

---

### Lần 3: Tự viết hiệu ứng `:hover`, `:focus` và thiết kế Poster bằng CSS Gradient
- **Prompt đã dùng:**
  > *"Không dùng hình ảnh ngoài từ internet để tránh bị lỗi 404 broken image khi nộp bài trên GitHub Pages. Hãy vẽ poster cho cả 8 bộ phim (Hành động, Viễn tưởng, Tâm lý, Kinh dị, Hoạt hình, Lãng mạn,...) hoàn toàn bằng CSS Gradients (`radial-gradient` kết hợp `linear-gradient`). Đồng thời tự viết hiệu ứng `:hover` phóng to poster, quét vệt sáng qua nút bấm (`::before`), và hiệu ứng `:focus-visible` viền vàng gold cho Accessibility."*
- **Kết quả AI tạo ra:**
  - Poster phim hiện lên tuyệt đẹp với màu sắc đặc trưng từng thể loại.
  - Hiệu ứng `:hover` và `:focus` chạy cực kỳ mượt mà, phản hồi ngay lập tức khi rê chuột hoặc dùng phím Tab.

---

### Lần 4: Điều chỉnh quan trọng – Bỏ hoàn toàn file JS ngoài, xử lý thuần CSS
- **Prompt đã dùng của sinh viên:**
  > *"khoan bỏ file JS đi sửa lại promtp là web xem phim đa dang cao cấp chứ không phải web game nhớ bỏ JS ra"*
- **Lý do & Tinh chỉnh của SV:**
  - ⚠️ **Phát hiện:** Việc đính kèm file JavaScript riêng (`script.js` / `main.js`) có thể khiến bài thi bị trừ điểm nếu có lỗi đường dẫn hoặc xung đột kịch bản. Yêu cầu của đề thi nhấn mạnh vào HTML5, CSS Variables, Flexbox/Grid và CSS Effects.
  - 🛠️ **Giải pháp tinh chỉnh kiến trúc:**
    1. Xóa bỏ hoàn toàn thư mục `js/` và các file `.js` bên ngoài.
    2. Menu điều hướng trên điện thoại (Mobile Menu) được chuyển đổi sang kỹ thuật **CSS Checkbox Hack** (`input[type="checkbox"]` kết hợp bộ chọn `~` trong CSS), mở/đóng menu 100% bằng CSS mà không cần một dòng JS nào.
    3. Thư viện AOS chỉ cần khởi chạy bằng một đoạn `<script>` nội tuyến 5 dòng ở cuối trang `index.html`.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

### 1. AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?
- Tiết kiệm hơn 80% thời gian viết mã các dải màu phức tạp trong CSS Gradients để vẽ 8 poster phim nghệ thuật thay vì phải tự căn chỉnh từng góc độ màu.
- Tự động sinh ra cấu trúc ngữ nghĩa HTML5 phong phú, đầy đủ nhãn tiếp cận người dùng (`aria-label`, `aria-labelledby`, `role`).
- Hỗ trợ xây dựng nhanh hệ thống biến `:root` quản lý màu sắc, khoảng cách và font chữ một cách khoa học.

### 2. Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?
- **Phải nắm vững kiến thức nền tảng:** Nếu không hiểu chuẩn Semantic HTML5, sinh viên sẽ không thể phát hiện ra việc AI lạm dụng thẻ `<div>` để nhắc nhở và yêu cầu sửa lại thành `<article>`, `<figure>`, `<section>`.
- **Rõ ràng và có định hướng:** Cần đưa ra các ràng buộc cụ thể (ví dụ: "nhớ bỏ JS ra", "dùng màu vàng gold `#d4af37`", "sử dụng CSS Variables") thay vì những câu lệnh mơ hồ như "làm một trang web đẹp".
- **Kiểm soát mã nguồn (Iteration Mindset):** Vibe Coding không phải là sao chép mù quáng, mà là quá trình đối thoại liên tục, tinh chỉnh từng phần nhỏ để sản phẩm cuối cùng đạt điểm số tối đa theo đúng barem chấm điểm của Giảng viên.
