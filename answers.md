# PHẦN A — KIỂM TRA ĐỌC HIỂU (20 điểm)

## Câu A1 (5đ) — HTTP & Browser

### 1. 5 bước xảy ra khi gõ `https://shopee.vn` vào trình duyệt và nhấn Enter (từ DNS lookup đến render):

> *Nguồn tham chiếu: File `01_introduction_html_universe.md` — Mục "🎬 Cuộc Hành Trình 0.3 Giây Xuyên Đại Dương", Mục "1.1. Kiến trúc Client-Server" và Mục "1.3. Browser Rendering — Từ Code thành Hình ảnh".*

Dưới đây là đúng thứ tự các bước diễn ra:

1. **DNS Lookup (Phân giải tên miền):** Trình duyệt tiến hành dịch tên miền `shopee.vn` thành địa chỉ IP thực của máy chủ để biết cần gửi yêu cầu đi đâu.
2. **Gửi HTTP Request (Hành trình của Client):** Trình duyệt đóng vai trò là **Client** gửi một yêu cầu (HTTP Request - ví dụ phương thức GET) đi qua router WiFi, qua nhà mạng ISP, xuyên qua hệ thống cáp quang để đến máy chủ (Server). 
3. **Xử lý tại Server và phản hồi (HTTP Response):** Máy chủ nhận yêu cầu, xử lý dữ liệu và gửi phản hồi (HTTP Response) chứa các file tài nguyên (HTML, CSS, JS) chạy ngược qua hệ thống cáp quang để về lại thiết bị của người dùng.
4. **Phân tích mã nguồn (Parse HTML & CSS):** Ngay khi nhận được file, trình duyệt Chrome sẽ bắt đầu đọc bản vẽ kiến trúc cấu trúc trang (**Parse HTML**) và đọc bản thiết kế nội thất về màu sắc, layout (**Parse CSS**).
5. **Thực thi và hiển thị hoàn thiện (Execute JS & Paint/Render):** Trình duyệt tiến hành lắp đặt hệ thống tương tác và logic (**Execute JS**), sau đó vẽ giao diện hoàn chỉnh lên màn hình (**Paint & Render**) để hiển thị trang Shopee cho người dùng.

---------------

### 2. Tab Network trong Chrome DevTools và phân tích thực tế:

> *Nguồn tham chiếu: File `01_introduction_html_universe.md` — Mục "4.3. Developer Tools (F12) — "Kính hiển vi" cho website".*

**Tab Network cho thấy thông tin gì?**
Trong Chrome DevTools, tab **Network** đóng vai trò như một bản ghi chi tiết toàn bộ luồng giao tiếp mạng (gửi requests và nhận responses) giữa trình duyệt (Client) và máy chủ (Server). Cụ thể, công cụ này giúp Web Developer:
- **Theo dõi tài nguyên:** Liệt kê tất cả các file được tải về để tạo nên trang web (HTML, CSS, JavaScript, Hình ảnh...).
- **Phân tích hiệu suất:** Cho biết dung lượng và thời gian tải của từng file, giúp giải quyết bài toán tối ưu hóa ("Website tải chậm — file nào nặng nhất?").
- **Kiểm tra trạng thái (Status):** Xác nhận các request gửi đi có thành công hay không thông qua các HTTP Response Codes (ví dụ: `200 OK`, `404 Not Found`).

**Ảnh chụp màn hình phân tích tab Network(E lấy ví dụ trang web của mancity.com):**

![Ảnh phân tích Chrome DevTools](./c2_A1.jpg)


## Câu A2 (5đ) — Semantic HTML

**1. Tại sao trang web trên bị Google đánh giá SEO thấp?**
Trang web này mắc lỗi lạm dụng thẻ `<div>` (thường được giới lập trình gọi là lỗi "div soup"). Thẻ `<div>` là một thẻ vô nghĩa (non-semantic). Khi các công cụ tìm kiếm (như Google Bot) hoặc trình đọc màn hình quét qua, chúng chỉ thấy các khối hộp vô danh mà không thể phân biệt được đâu là phần đầu trang, đâu là menu điều hướng, nội dung chính hay tiêu đề bài viết. Vì không thể hiểu được cấu trúc và ngữ cảnh của nội dung, Google sẽ đánh giá điểm SEO của trang này rất thấp.

**2. Liệt kê 4 lỗi semantic và cách khắc phục:**
1. **Lỗi phần đầu trang:** Dùng `<div class="header">` thay vì thẻ chuẩn `<header>`.
2. **Lỗi thanh điều hướng:** Dùng `<div class="menu">` cho menu. Đáng lẽ phải dùng thẻ `<nav>` kết hợp với danh sách `<ul>`, `<li>` để nhóm các liên kết lại với nhau.
3. **Lỗi khối nội dung chính:** Dùng `<div class="main">` thay vì thẻ `<main>`. Công cụ tìm kiếm cần thẻ `<main>` để biết trọng tâm của trang nằm ở đâu.
4. **Lỗi tiêu đề bài viết:** Dùng `<div class="title">` thay vì các thẻ Heading (như `<h1>` hoặc `<h2>`). Google rất chú trọng vào các thẻ Heading để trích xuất từ khóa chính của trang.
*(Bổ sung thêm: Thẻ `<img>` đang bị thiếu thuộc tính `alt` để mô tả nội dung ảnh cho Google hiểu).*

**3. Mã HTML sau khi đã sửa lại cho chuẩn Semantic:**

```html
<header>
  <div class="logo">ShopTLU</div>
  <nav class="menu">
    <ul>
      <li><a href="/">Trang chủ</a></li>
      <li><a href="/products">Sản phẩm</a></li>
    </ul>
  </nav>
</header>

<main>
  <article class="product">
    <h1 class="title">iPhone 16 Pro</h1>
    <p class="price">25.990.000đ</p>
    <div class="image">
      <img src="iphone.jpg" alt="Điện thoại iPhone 16 Pro">
    </div>
  </article>
</main>

<footer>
  <p>© 2026 ShopTLU</p>
</footer>


## Câu A3 (5đ) — Block vs Inline

**1. Mô phỏng kết quả hiển thị (Text Art):**

Kết quả hiển thị trên trình duyệt sẽ có dạng như sau:

+--------------------------------------------------+
| Hộp 1                                            |
+--------------------------------------------------+
| Text A Text B                                    |
+--------------------------------------------------+
| Hộp 2                                            |
+--------------------------------------------------+
| Text C **Text D** |
+--------------------------------------------------+
| Hộp 3                                            |
+--------------------------------------------------+
*(Lưu ý: Chữ "Text D" sẽ được in đậm do nằm trong thẻ <strong>)*

**2. Giải thích chi tiết tại sao lại hiển thị như vậy:**

Nguyên lý hiển thị của HTML dựa vào đặc tính mặc định của các thẻ (Block hoặc Inline):

* **Thẻ Block (như `<div>`):** Luôn luôn bắt đầu trên một dòng mới và chiếm toàn bộ chiều rộng có thể của phần tử chứa nó (dù nội dung bên trong rất ngắn).
* **Thẻ Inline (như `<span>`, `<strong>`):** Không bắt đầu trên dòng mới, chúng chỉ chiếm khoảng không gian vừa đủ chứa nội dung bên trong và sẽ nằm cạnh nhau trên cùng một dòng (trừ khi hết chỗ mới bị rớt dòng).

**Phân tích từng dòng code:**
1.  `<div>Hộp 1</div>`: Là thẻ Block, nên "Hộp 1" đứng riêng một dòng và chiếm hết chiều ngang.
2.  `<span>Text A</span>` và `<span>Text B</span>`: Đều là thẻ Inline. Chúng sẽ nằm ngay cạnh nhau trên cùng một dòng tiếp theo tạo thành `Text A Text B`.
3.  `<div>Hộp 2</div>`: Là thẻ Block. Dù dòng chứa Text A & B vẫn còn chỗ, `<div>` này vẫn ép nó xuống một dòng mới, chiếm trọn 1 dòng.
4.  `<span>Text C</span>` và `<strong>Text D</strong>`: Đều là thẻ Inline. Tương tự như trên, chúng đứng cạnh nhau trên dòng mới tạo thành `Text C Text D` (trong đó Text D bị làm đậm bởi thẻ `<strong>`).
5.  `<div>Hộp 3</div>`: Là thẻ Block, tiếp tục bị đẩy xuống một dòng mới đứng một mình.






