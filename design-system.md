# Design System — Tuki Group

**Phiên bản:** 2.0.0  
**Cập nhật:** 30/07/2026  
**Nguồn đối chiếu:** giao diện đang hiển thị tại `https://tukigroup.vn/`, logo chính thức và các global token của website WordPress/Elementor.

## 0. Kết quả kiểm tra tính toàn vẹn

Phiên bản 1.0.0 chưa đủ điều kiện dùng cho production vì còn placeholder, tên biến không nhất quán và chưa có quy tắc chống xung đột với theme WordPress. Phiên bản 2.0.0 đã xử lý các điểm sau:

| Hạng mục | Trạng thái cũ | Hoàn thiện trong 2.0.0 |
| --- | --- | --- |
| Màu thương hiệu | Còn `[#Mã màu trên web]` | Xác định đỏ Tuki `#C72027`, navy logo `#172A52`, heading `#0F0C29` |
| Typography | Còn placeholder | Chuẩn hóa Inter cho heading/UI và Plus Jakarta Sans cho body |
| Token CSS | Trộn `--color-*`, `--tuki-*`, `--space-*` | Dùng namespace duy nhất `--tuki-ds-*` |
| Type scale | Chưa khớp website | Cập nhật theo global token: 40/32/24/18/16px và responsive |
| Trạng thái component | Mô tả chung chung | Bổ sung hover, focus-visible, active, disabled, loading |
| Responsive | Chỉ nêu “responsive” | Bổ sung container, gutter và breakpoint cụ thể |
| Accessibility | Chưa có | Bổ sung contrast, focus, target size, reduced motion |
| WordPress isolation | Chưa có | Bổ sung quy tắc scope, biến riêng và `!important` |
| Performance | Chưa có | Bổ sung quy chuẩn ảnh, iframe, font và JavaScript |

### Phân loại token

- **Token xác thực từ website:** màu Elementor toàn cục, màu logo, font và kích thước chữ được ghi nhận trực tiếp.
- **Token hệ thống bổ sung:** breakpoint, spacing, shadow, trạng thái và quy tắc accessibility được chuẩn hóa để có thể triển khai nhất quán. Đây là phần mở rộng của design system, không phải khẳng định rằng website cũ đã dùng toàn bộ giá trị này.

---

## 1. Nguyên tắc thiết kế

1. **Rõ ràng trước trang trí:** mỗi section chỉ nên truyền đạt một ý chính và một hành động tiếp theo.
2. **Tin cậy bằng bằng chứng:** ưu tiên con số, lộ trình, hình ảnh thật và thông tin liên hệ rõ ràng.
3. **Tuki là nhận diện chính:** đỏ Tuki dùng cho CTA; navy và trắng tạo nền tảng chuyên nghiệp.
4. **Ưu tiên chuyển đổi nhưng không gây áp lực:** CTA nổi bật, lặp lại hợp lý, không dùng hiệu ứng nhấp nháy.
5. **Mobile-first:** nội dung, form, bảng và media phải dùng tốt từ màn hình 320px.
6. **Nhanh và bền vững:** ưu tiên HTML semantic, CSS thuần, JavaScript tối thiểu và ảnh đúng kích thước.

---

## 2. Foundations

### 2.1. Màu sắc

#### Brand colors

| Tên | Token | HEX | Vai trò |
| --- | --- | --- | --- |
| Tuki Red | `--tuki-ds-brand-red` | `#C72027` | CTA, active state, điểm nhấn, link quan trọng |
| Tuki Red Dark | `--tuki-ds-brand-red-dark` | `#A9181E` | Hover/pressed của CTA |
| Tuki Navy | `--tuki-ds-brand-navy` | `#172A52` | Logo, nền thương hiệu, khối tạo uy tín |
| Heading Ink | `--tuki-ds-heading` | `#0F0C29` | Heading chính, global primary trên website |
| Deep Navy | `--tuki-ds-deep-navy` | `#061835` | Hero/footer hoặc nền tương phản cao |

#### Neutral colors

| Tên | Token | HEX | Vai trò |
| --- | --- | --- | --- |
| White | `--tuki-ds-white` | `#FFFFFF` | Nền chính, chữ trên nền đậm |
| Surface Soft | `--tuki-ds-surface-soft` | `#F9FAFB` | Section xen kẽ |
| Surface | `--tuki-ds-surface` | `#F1F2F3` | Card phụ, bảng, nền media |
| Border | `--tuki-ds-border` | `#D1D5DB` | Viền input, table, separator |
| Text | `--tuki-ds-text` | `#505E6B` | Nội dung body thực tế trên website |
| Text Strong | `--tuki-ds-text-strong` | `#334155` | Nội dung cần nhấn |
| Text Muted | `--tuki-ds-text-muted` | `#69727D` | Caption, metadata |
| Dark Surface | `--tuki-ds-dark-surface` | `#1E293B` | Section đậm, footer |

#### Functional colors

| Tên | Token | HEX | Vai trò |
| --- | --- | --- | --- |
| Link Blue | `--tuki-ds-link` | `#046BD2` | Link chức năng, không dùng thay CTA đỏ |
| Success | `--tuki-ds-success` | `#168354` | Xác nhận thành công |
| Warning | `--tuki-ds-warning` | `#B45309` | Cảnh báo |
| Error | `--tuki-ds-error` | `#B42318` | Lỗi form |
| Focus | `--tuki-ds-focus` | `#046BD2` | Focus ring |

#### Quy tắc sử dụng màu

- CTA chính dùng nền `#C72027`, chữ trắng.
- Không dùng màu đỏ cho đoạn văn dài hoặc nền diện tích lớn.
- Heading trên nền sáng dùng `#0F0C29`; body dùng `#505E6B`.
- Nền navy dùng chữ trắng; nội dung phụ có thể dùng `#E2E8F0`.
- Mỗi viewport nên có tối đa một CTA đỏ chiếm ưu thế thị giác.
- `#046BD2` là màu link chức năng từ theme, không phải màu nhận diện chính.
- Gradient chỉ dùng tối đa hai màu gần nhau về sắc độ, chuyển nhẹ; không dùng gradient ba màu hoặc tương phản gắt trên diện tích lớn.

### 2.2. Typography

#### Font family

| Ngữ cảnh | Font stack |
| --- | --- |
| Heading, button, navigation, label | `"Inter", "Segoe UI", Arial, sans-serif` |
| Body, paragraph, list | `"Plus Jakarta Sans", "Inter", "Segoe UI", Arial, sans-serif` |
| Font legacy | `"SVN Gilroy", sans-serif` chỉ dùng khi tái hiện component cũ có sẵn |

Không tải thêm icon font cho landing page. Ưu tiên ký hiệu Unicode hoặc icon inline đã được kiểm duyệt.

#### Type scale desktop

| Token | Size / line-height / weight | Ứng dụng |
| --- | --- | --- |
| `--tuki-ds-type-display` | `56px / 1.08 / 750` | Hero ngắn |
| `--tuki-ds-type-h1` | `40px / 1.20 / 700` | H1, khớp global primary |
| `--tuki-ds-type-h2` | `32px / 1.20 / 700` | Section title |
| `--tuki-ds-type-h3` | `24px / 1.25 / 650` | Card/lesson title |
| `--tuki-ds-type-h4` | `18px / 1.30 / 650` | Subheading |
| `--tuki-ds-type-body-lg` | `18px / 1.65 / 400` | Lead paragraph |
| `--tuki-ds-type-body` | `16px / 1.60 / 400` | Nội dung mặc định |
| `--tuki-ds-type-small` | `14px / 1.55 / 500` | Metadata, note |
| `--tuki-ds-type-caption` | `12px / 1.45 / 500` | Caption |

#### Type scale mobile

- H1: `36px`, có thể hạ xuống `32px` ở màn hình dưới 375px.
- H2: `28px`.
- H3: `21px`.
- Body và input không nhỏ hơn `16px` để tránh trình duyệt tự zoom.
- Đoạn văn nên giới hạn `65–72ch`; heading lớn tối đa `18ch`.

### 2.3. Spacing

Hệ spacing theo bội số 4px:

| Token | Giá trị |
| --- | --- |
| `--tuki-ds-space-1` | `4px` |
| `--tuki-ds-space-2` | `8px` |
| `--tuki-ds-space-3` | `12px` |
| `--tuki-ds-space-4` | `16px` |
| `--tuki-ds-space-5` | `20px` |
| `--tuki-ds-space-6` | `24px` |
| `--tuki-ds-space-8` | `32px` |
| `--tuki-ds-space-10` | `40px` |
| `--tuki-ds-space-12` | `48px` |
| `--tuki-ds-space-16` | `64px` |
| `--tuki-ds-space-20` | `80px` |
| `--tuki-ds-space-24` | `96px` |

Khoảng cách section: `96px` desktop, `72px` tablet, `56px` mobile.

### 2.4. Grid, container và breakpoint

| Token | Giá trị |
| --- | --- |
| `--tuki-ds-container` | `1200px` |
| `--tuki-ds-reading` | `760px` |
| `--tuki-ds-gutter-desktop` | `32px` |
| `--tuki-ds-gutter-tablet` | `24px` |
| `--tuki-ds-gutter-mobile` | `18px` |

Breakpoints triển khai:

- `>= 1200px`: desktop rộng.
- `1024–1199px`: desktop nhỏ.
- `768–1023px`: tablet.
- `< 768px`: mobile.
- `< 480px`: mobile nhỏ.

Quy tắc:

- Grid desktop: 12 cột; landing page thường dùng split 7/5 hoặc 6/6.
- Tablet: 8 cột.
- Mobile: 4 cột, phần lớn component xếp một cột.
- Không dùng fixed width cho card, form, bảng hoặc media.

### 2.5. Radius, border và shadow

| Token | Giá trị | Dùng cho |
| --- | --- | --- |
| `--tuki-ds-radius-sm` | `6px` | Badge, input nhỏ |
| `--tuki-ds-radius-md` | `12px` | Button, input |
| `--tuki-ds-radius-lg` | `20px` | Card |
| `--tuki-ds-radius-xl` | `28px` | Hero media, feature panel |
| `--tuki-ds-radius-pill` | `999px` | Pill/badge |
| `--tuki-ds-shadow-sm` | `0 1px 2px rgba(15,12,41,.06)` | Control |
| `--tuki-ds-shadow-md` | `0 12px 32px rgba(15,12,41,.10)` | Card nổi |
| `--tuki-ds-shadow-lg` | `0 24px 64px rgba(6,24,53,.16)` | Hero media/modal |

Border mặc định: `1px solid #D1D5DB`. Card có thể dùng border mờ thay vì shadow để giữ cảm giác tối giản.

### 2.6. Motion

| Token | Giá trị |
| --- | --- |
| `--tuki-ds-ease` | `cubic-bezier(.2,.8,.2,1)` |
| `--tuki-ds-duration-fast` | `160ms` |
| `--tuki-ds-duration-base` | `240ms` |
| `--tuki-ds-duration-slow` | `420ms` |

- Chỉ animate `opacity` và `transform` khi có thể.
- Hover card không dịch quá `4px`.
- Với `prefers-reduced-motion: reduce`, vô hiệu hóa smooth scroll và chuyển động không cần thiết.

---

## 3. Component specifications

### 3.1. Button

#### Primary

- Nền `#C72027`, chữ trắng, font Inter `700`.
- Cao tối thiểu `48px`; padding ngang `22–28px`.
- Radius `12px`, không viết toàn bộ chữ hoa nếu label dài.
- Hover: `#A9181E`, nâng `translateY(-1px)`.
- Active: không dịch chuyển, shadow nhỏ hơn.
- Focus-visible: ring `3px rgba(4,107,210,.28)` + outline rõ.
- Disabled: opacity `.5`, bỏ shadow, cursor `not-allowed`.

#### Secondary

- Nền trắng, chữ `#0F0C29`, border `#D1D5DB`.
- Hover dùng nền `#F9FAFB`, border `#172A52`.

#### Text link

- Màu `#C72027` cho link chuyển đổi; `#046BD2` cho link chức năng.
- Gạch chân ở hover/focus, không chỉ dựa vào màu để biểu đạt trạng thái.

### 3.2. Form

- Label đặt phía trên, không dùng placeholder thay label.
- Input cao tối thiểu `48px`, font `16px`, radius `12px`.
- Default: border `#D1D5DB`, nền trắng.
- Hover: border `#94A3B8`.
- Focus: border `#046BD2` và ring 3px.
- Error: border `#B42318`, thông báo lỗi đặt ngay dưới field.
- Success: thông báo rõ hành động đã hoàn tất; không chỉ đổi màu.
- Trường bắt buộc có ký hiệu và `aria-required="true"`.

### 3.3. Card

- Nền trắng, border mờ, radius `20px`.
- Padding `24–32px`.
- Heading cách body `8–12px`.
- Card tương tác phải có focus-visible tương đương hover.
- Không đặt quá ba cấp shadow trong cùng một section.

### 3.4. Hero

- H1 tối đa 2–4 dòng desktop, 3–6 dòng mobile.
- Lead tối đa 72ch.
- CTA chính xuất hiện trong viewport đầu.
- Media dùng tỷ lệ `16:9`, có width/height hoặc `aspect-ratio` để tránh layout shift.
- Nếu là iframe YouTube: dùng `youtube-nocookie.com`, `loading="lazy"`, `title` và `allowfullscreen`.

### 3.5. Badge

- Font `12–14px`, weight `700`.
- Padding `6px 10px`, radius pill.
- Nền đỏ nhạt hoặc navy nhạt; không dùng badge như button.

### 3.6. Curriculum / timeline

- Mỗi buổi có số thứ tự, tiêu đề và outcome.
- Desktop có thể dùng grid hai cột; mobile xếp một cột.
- Nội dung dài dùng `<details>/<summary>` để giảm chiều dài nhận thức.
- Summary phải thao tác được bằng bàn phím và có icon trạng thái rõ.

### 3.7. FAQ

- Dùng native `<details>` và `<summary>`.
- Mỗi câu hỏi là một khối độc lập, border dưới hoặc card.
- Không đóng câu hỏi khác bằng JavaScript nếu người dùng muốn mở nhiều mục để so sánh.

### 3.8. Sticky CTA mobile

- Chỉ hiển thị dưới `768px`.
- Không che nội dung, cookie banner hoặc control hệ thống.
- Body/landing wrapper cần padding-bottom tương ứng.
- CTA tối thiểu `48px`, label ngắn và rõ.

### 3.9. Navigation và footer

- Khi landing page nằm trong WordPress production, ưu tiên dùng header/footer sẵn có của website.
- Header gốc cao khoảng 90px trên desktop; landing anchor cần `scroll-margin-top`.
- Footer landing chỉ thêm CTA/contact nếu theme chưa có footer hoặc khi chạy standalone.

---

## 4. Nội dung và giọng điệu

- Viết trực tiếp, cụ thể, ưu tiên động từ hành động.
- Heading dùng sentence case hoặc chữ hoa có kiểm soát; không viết toàn bộ đoạn dài bằng chữ hoa.
- Không hứa hẹn kết quả tuyệt đối. Các số như “x3 doanh số” phải được diễn đạt là mục tiêu/kết quả tham chiếu và cần có bằng chứng nếu dùng như cam kết.
- Với số liệu “hơn 21.000 học viên”, nên giữ nguồn nội bộ và thời điểm cập nhật.
- CTA chuẩn:
  - `Đăng ký tư vấn`
  - `Giữ chỗ khóa học`
  - `Xem lộ trình 4 buổi`
  - `Gọi hotline`

---

## 5. Logo, icon và hình ảnh

### 5.1. Logo

- Logo chính thức gồm đỏ `#C72027` và navy `#172A52`.
- Luôn giữ đúng tỷ lệ, không kéo giãn.
- Clear space tối thiểu bằng chiều cao ký tự “T” trong logo.
- Trên nền tối dùng biến thể logo trắng nếu có; không tự đổi màu bằng CSS filter.

### 5.2. Icon

- Ưu tiên bộ icon outline, stroke khoảng 1.75–2px.
- Không trộn nhiều phong cách icon trong cùng một trang.
- Icon trang trí dùng `aria-hidden="true"`; icon là control phải có accessible label.
- Landing page độc lập không tải cả icon font chỉ để dùng vài icon.

### 5.3. Photography

- Hero/media: 16:9.
- Card: 4:3 hoặc 3:2.
- Avatar: 1:1.
- Ảnh phải có `width`, `height`, `alt`, `loading="lazy"` (trừ ảnh LCP) và `decoding="async"`.
- Dùng kích thước WordPress đã resize (`768w`, `1024w`) thay vì ảnh gốc 2K nếu không cần.
- Không dùng background-image cho ảnh mang ý nghĩa nội dung; đặt trực tiếp bằng `<img>` hoặc `<picture>`.

---

## 6. Accessibility

- Mục tiêu WCAG 2.2 AA.
- Text thường đạt contrast tối thiểu 4.5:1; text lớn tối thiểu 3:1.
- Mọi control có focus-visible rõ.
- Vùng chạm tối thiểu 44×44px, ưu tiên 48×48px.
- Heading đi đúng thứ tự H1 → H2 → H3.
- Section quan trọng có `aria-labelledby`.
- Form có label thật và vùng báo lỗi/status dùng `aria-live`.
- Video có title; nội dung quan trọng cần caption/transcript khi có thể.
- Không autoplay video có âm thanh.
- Không khóa zoom, không dùng `user-scalable=no`.

---

## 7. Performance

- Không dùng framework chỉ cho một landing page.
- JavaScript đặt cuối HTML hoặc dùng `defer`; chỉ thêm cho hành vi không có native HTML tương đương.
- Ảnh đầu trang có `fetchpriority="high"` nếu là LCP; ảnh dưới fold dùng lazy loading.
- Dùng `srcset` và `sizes`.
- Iframe video dưới fold dùng `loading="lazy"` và domain YouTube Privacy Enhanced Mode.
- Tránh import nhiều font/weight; tận dụng Inter và Plus Jakarta Sans đã có trên website production.
- Không nhúng base64 ảnh lớn vào HTML vì làm mất browser cache và tăng HTML parse time.
- Giữ CLS gần 0 bằng width/height hoặc aspect-ratio.

---

## 8. Tích hợp WordPress an toàn

Mọi landing page nhúng vào WordPress phải:

1. Có một wrapper ID duy nhất, ví dụ `#tuki-tts-landing`.
2. Scope toàn bộ selector bên dưới wrapper; không viết selector chung như `h2`, `.button`, `.container`.
3. Prefix class và biến theo feature, ví dụ `.tts-card`, `--tts-color-brand`.
4. Không thay đổi `html`, `body`, `:root` hoặc class của theme.
5. Dùng `!important` cho các thuộc tính dễ bị theme/Elementor ghi đè.
6. JavaScript chỉ query bên trong wrapper và chạy an toàn nhiều lần.
7. Không phụ thuộc jQuery.
8. Không dùng tên class phổ biến như `.row`, `.card`, `.btn`, `.active`.

Ví dụ:

```css
#tuki-tts-landing {
  --tts-color-brand: #C72027 !important;
  --tts-color-heading: #0F0C29 !important;
  --tts-font-body: "Plus Jakarta Sans", "Inter", sans-serif !important;
  color: #505E6B !important;
  font-family: var(--tts-font-body) !important;
}

#tuki-tts-landing .tts-button {
  appearance: none !important;
  background: var(--tts-color-brand) !important;
  border: 0 !important;
  border-radius: 12px !important;
  color: #FFFFFF !important;
  min-height: 48px !important;
}
```

---

## 9. Canonical CSS tokens

```css
:root {
  /* Brand */
  --tuki-ds-brand-red: #C72027;
  --tuki-ds-brand-red-dark: #A9181E;
  --tuki-ds-brand-navy: #172A52;
  --tuki-ds-heading: #0F0C29;
  --tuki-ds-deep-navy: #061835;

  /* Neutral */
  --tuki-ds-white: #FFFFFF;
  --tuki-ds-surface-soft: #F9FAFB;
  --tuki-ds-surface: #F1F2F3;
  --tuki-ds-border: #D1D5DB;
  --tuki-ds-text: #505E6B;
  --tuki-ds-text-strong: #334155;
  --tuki-ds-text-muted: #69727D;
  --tuki-ds-dark-surface: #1E293B;

  /* Functional */
  --tuki-ds-link: #046BD2;
  --tuki-ds-success: #168354;
  --tuki-ds-warning: #B45309;
  --tuki-ds-error: #B42318;
  --tuki-ds-focus: #046BD2;

  /* Typography */
  --tuki-ds-font-heading: "Inter", "Segoe UI", Arial, sans-serif;
  --tuki-ds-font-body: "Plus Jakarta Sans", "Inter", "Segoe UI", Arial, sans-serif;

  /* Layout */
  --tuki-ds-container: 1200px;
  --tuki-ds-reading: 760px;

  /* Radius */
  --tuki-ds-radius-sm: 6px;
  --tuki-ds-radius-md: 12px;
  --tuki-ds-radius-lg: 20px;
  --tuki-ds-radius-xl: 28px;
  --tuki-ds-radius-pill: 999px;

  /* Shadow */
  --tuki-ds-shadow-sm: 0 1px 2px rgba(15, 12, 41, 0.06);
  --tuki-ds-shadow-md: 0 12px 32px rgba(15, 12, 41, 0.10);
  --tuki-ds-shadow-lg: 0 24px 64px rgba(6, 24, 53, 0.16);
}
```

---

## 10. Definition of done

Một giao diện Tuki Group chỉ được xem là tuân thủ design system khi:

- Không còn placeholder token.
- Màu, font và component dùng đúng vai trò.
- Chạy tốt ở 320px, 375px, 768px, 1024px và desktop rộng.
- Không có horizontal overflow.
- CTA và form dùng được bằng bàn phím.
- Ảnh/iframe không gây layout shift rõ rệt.
- Không có selector CSS rò rỉ ra theme WordPress.
- JavaScript không phát sinh lỗi khi chạy standalone hoặc bên trong WordPress.
- Nội dung trong ảnh brief đã được chuyển thành HTML có thể đọc, tìm kiếm và chỉnh sửa; không dùng cả ảnh brief như một landing page.
