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






