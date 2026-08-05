# Hướng dẫn đưa landing page lên WordPress

## File sử dụng

`landing-page-tiktok-shop-business-master.html` là một HTML fragment tự chứa:

- CSS inline đã scope trong `#tuki-tts-landing`.
- Toàn bộ class và biến dùng prefix `tts`.
- Các declaration giao diện quan trọng đều có `!important`.
- JavaScript thuần, không cần jQuery.
- Hình ảnh và video được đặt trực tiếp bằng thẻ `<img>` và `<iframe>`.

## Cách đưa lên trang

### Elementor

1. Tạo page mới và chọn layout **Elementor Full Width** hoặc **Elementor Canvas**.
2. Thêm một **HTML Widget**.
3. Mở file landing page, sao chép toàn bộ nội dung và dán vào widget.
4. Không bọc thêm bằng class `.container`, `.row` hoặc `.content` của theme.
5. Publish và xóa cache LiteSpeed/CDN nếu production đang bật cache.

### Gutenberg

1. Tạo page mới, chọn template full width.
2. Thêm block **Custom HTML**.
3. Dán toàn bộ nội dung của file landing page.
4. Tài khoản cần quyền `unfiltered_html`; nếu WordPress loại bỏ `<style>` hoặc `<script>`, dùng Elementor HTML Widget hoặc page template riêng.

## Các giá trị nên cấu hình trước khi chạy quảng cáo

### Ảnh ba nhóm học viên

Section “Khóa học phù hợp với ai?” đang dùng trực tiếp:

- `source/img/3.jpg` — Quản lý team TMĐT.
- `source/img/2.jpg` — Nhà bán hàng.
- `source/img/1.jpg` — Nhân sự vận hành.

Khi đưa lên production, cần upload cả thư mục `source/img/` vào đúng đường dẫn tương đối của landing page. Nếu dùng WordPress Media Library, thay ba thuộc tính `src` bằng URL tuyệt đối của ảnh sau khi upload.

### Video giới thiệu

Trong file hiện đang dùng video chính thức đã xuất hiện trên trang chủ Tuki Group:

```html
https://www.youtube-nocookie.com/embed/RjcTyh3g6Gg
```

Khi có video giới thiệu riêng của Mr. Hoàng Vương Hoàng, thay duy nhất ID video trong thuộc tính `src` của iframe.

### Form đăng ký

Do brief chưa cung cấp API/CRM/form endpoint, form hiện tại:

- kiểm tra dữ liệu ở trình duyệt;
- chuẩn bị email gửi tới `tukigroup123@gmail.com`;
- không tự động lưu hoặc gửi dữ liệu lên server.

Đây là hành vi minh bạch và hoạt động không cần backend. Trước khi chạy paid traffic, nên nối form với CRM, WPForms/Fluent Forms hoặc endpoint WordPress có xác thực và chống spam. Không nên hiển thị thông báo “đăng ký thành công” khi server chưa thật sự nhận lead.

### Tracking

Nếu trang production đã có Google Tag Manager, landing page tự đẩy các event:

- Event: `tuki_tts_interaction`
- Parameter: `tuki_tts_action`
- Event sau khi form hợp lệ: `tuki_tts_form_valid`

Không có GTM thì trang vẫn hoạt động bình thường.

## SEO trong WordPress

Thiết lập bằng plugin SEO hoặc phần Page Settings:

- **SEO title:** `TikTok Shop Business Master | Khóa học vận hành có lợi nhuận`
- **Meta description:** `Khóa học TikTok Shop Business Master offline tại Hà Nội và TP.HCM: 4 buổi thực chiến, lộ trình vận hành, GMV Max, nội dung, hàng hóa và tài chính.`
- **Slug gợi ý:** `tiktok-shop-business-master`
- Chỉ để một H1 trên trang; file landing page đã có sẵn một H1.

## Checklist sau publish

- Kiểm tra desktop, tablet và mobile.
- Kiểm tra CTA cuộn đúng tới form.
- Thử form với dữ liệu sai và dữ liệu hợp lệ.
- Kiểm tra hotline, email và địa chỉ.
- Kiểm tra ảnh lớp học tải bình thường.
- Kiểm tra video không autoplay.
- Xóa cache LiteSpeed/CDN sau mỗi lần cập nhật.
- Khi nối CRM, kiểm tra lead thực sự được lưu trước khi chạy quảng cáo.
