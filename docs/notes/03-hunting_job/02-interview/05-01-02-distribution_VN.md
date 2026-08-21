---
layout: post
category: hunting_job
title: Hệ thống phân tán, Cache, Khóa & Giao dịch (Phần 02)
tagline: by A Tú
tags:
    - Nguyên tác
    - Cache phân tán
    - Khóa phân tán
    - Giao dịch phân tán
excerpt: Hệ thống phân tán, Cache, Khóa & Giao dịch (Phần 02)
comment: false
---

<h1 align="center">Cache Phân Tán, Khóa Phân Tán và Giao Dịch Phân Tán</h1>

<p id="数据库第一部分"></p>

<div style="border-color: #24C6DC;
            background-color: #e9f9f3;         
            margin: 1rem 0;
        padding: .25rem 1rem;
        border-left-width: .3rem;
        border-left-style: solid;
        border-radius: .5rem;
        color: inherit;">
  <p>Đây là 6 thông tin có thể sẽ hữu ích cho bạn:</p>
<p>⭐️1. A Tú cùng bạn bè hợp tác phát triển một <span style="font-weight:bold;color:red">website tài nguyên lập trình</span>, hiện đã tổng hợp rất nhiều tài liệu học tập chất lượng và công cụ hữu ích (kèm link tải). Nếu bạn đang tìm kiếm tài nguyên lập trình phù hợp, <a href="https://tools.interviewguide.cn/home" style="text-decoration: underline" target="_blank">hoan nghênh trải nghiệm</a> cũng như giới thiệu những tài nguyên bạn thấy hay. Góp gió thành bão, mình vì mọi người, mọi người vì mình🔥!</p>  <p>2. 👉 Tháng 5/2023, trong thời gian <a style="text-decoration: underline" href="https://mp.weixin.qq.com/s?__biz=Mzk0ODU4MzEzMw==&mid=2247512170&idx=1&sn=c4a04a383d2dfdece676b75f17224e78" target="_blank">rời ByteDance để chuyển sang một công ty đa quốc gia</a>, nhằm <span style="font-weight:bold">thuận tiện cho bản thân khi tìm việc và nâng cao tỷ lệ trúng tuyển</span>, A Tú cùng bạn bè đã phát triển từ con số 0 một <span style="font-weight:bold;color:red">website giải đề phỏng vấn thực chiến của các Big Tech</span>, bao gồm hai frontend và một backend. Trang web cho phép tra cứu có định hướng đề thi viết của các công ty Internet, ví dụ như muốn tra cứu đề thi viết của ByteDance trong 1 năm gần đây gồm những gì đều có thể làm được. Hoan nghênh trải nghiệm~
<div align="center">
</div>Địa chỉ website: <a style="text-decoration: underline" href="https://niumacode.com/home?ref=F6O2625K" target="_blank">Website đề thi thuật toán phỏng vấn Big Tech</a>.
    </p>3. 😊
    Chia sẻ một <span style="font-weight:bold;color:red">website công cụ tiện ích</span> mà A Tú tâm đắc sưu tầm, <a style="text-decoration: underline" href="https://hkjtz.cn/" target="_blank">nhấn vào đây để truy cập</a>, chủ yếu là các ứng dụng, website ngách hữu ích, ngoài ra còn có tài nguyên phim ảnh HD, âm nhạc, phim truyền hình, AI, phim tài liệu, tài liệu thi tiếng Anh, thi công chức, cao học, nghề tay trái...
  </p>
  <p>4. 😍 Chia sẻ miễn phí tài nguyên học tập mà A Tú đã tích lũy từ khi theo học máy tính, <a style="text-decoration: underline" href="/notes/07-resources/01-free/01-introduce.html" target="_blank">nhấn vào đây để nhận miễn phí</a>; đồng thời cũng lưu lại nhật ký đánh giá <a style="text-decoration: underline" href="/notes/07-resources/02-precious.html" target="_blank">những cuốn sách máy tính, chuyên mục online chất lượng cũng như những khóa học trả phí kém chất lượng</a> từng mua trước đây.
  </p>
  <p>5. 🚀 Nếu bạn muốn thuận lợi giành được offer tốt hơn trong kỳ tuyển dụng trường học (Campus Recruitment), A Tú khuyên bạn nên xem thêm những <a style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/npg1k81zeq4wfpyz" target="_blank">cạm bẫy từng vấp phải</a> và <a style="text-decoration: underline"  target="_blank" href="https://www.yuque.com/tuobaaxiu/httmmc/gge9ppd0mbu2d3dp">kinh nghiệm đúc kết</a> của người đi trước. Thực tế, hầu hết các vấn đề bạn đang gặp phải thì các anh chị khóa trước đều đã từng trải qua.
  </p>
  <p>6. 🔥 Hoan nghênh các bạn đang chuẩn bị cho kỳ tuyển dụng trường học ngành CNTT tham gia <a  style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/xg0otqvc17wfx4u9" target="_blank">Cộng đồng học tập</a> của tôi. Độc hành một mình chi bằng cùng nhau sưởi ấm, trong nhóm đã đọng lại rất nhiều <a  style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/gge9ppd0mbu2d3dp" target="_blank">kinh nghiệm và tổng kết</a> của các anh chị khóa 21/22/23/24/25. Kiên trì đi theo lộ trình, cuối cùng đa phần đều có thể nhận được offer ưng ý! Nếu bạn cần phiên bản PDF tổng hợp các điểm kiến thức 📚︎ Bát cổ văn phỏng vấn tuyển dụng trường học trên website 《Ghi chép học tập của A Tú》, có thể <a style="text-decoration: underline" href="https://www.yuque.com/tuobaaxiu/httmmc/qs0yn66apvkzw0ps" target="_blank">nhấn vào đây để tải về</a>.</p>   </div>

## 1. Bộ đệm Phân tán (Distributed Caching)

### 1. Các Kịch bản Ứng dụng
1. **Page Cache**: Đệm các đoạn mã HTML/CSS/JS tĩnh hoặc trang kết xuất SSR.
2. **Object Cache & Session Store**: Đệm kết quả truy vấn ORM giảm tải cho CSDL; Lưu trữ trạng thái Session cho cụm Web Server không trạng thái (Stateless).
3. **Parallel Compute Intermediate Buffer**: Lưu trữ kết quả tính toán trung gian dùng chung giữa các worker.

### 2. Tổng quan 5 Vấn đề Bộ đệm
- **Cache Avalanche**: Cần cài đặt TTL ngẫu nhiên (Jitter) và xây dựng cụm Redis HA.
- **Cache Penetration**: Dùng Bloom Filter hoặc Cache Null Object.
- **Cache Pre-warming**: Chủ động nạp dữ liệu hot khi khởi động service.
- **Cache Update**: Áp dụng Cache-Aside (Xóa cache sau khi ghi DB) hoặc lắng nghe Binlog.
- **Cache Downgrade**: Giáng cấp dịch vụ, trả về giá trị mặc định khi hệ thống quá tải.

<p id="分布式锁"></p>

## 2. Khóa Phân tán (Distributed Lock)

### 1. Thuật toán Redlock trên Cụm Redis
Nhằm loại bỏ rủi ro Single Point of Failure (SPOF) của 1 node Redis Master duy nhất:
1. Triển khai $N$ máy chủ Redis Master hoàn toàn độc lập ($N$ là số lẻ, ví dụ $N=5$).
2. Client lấy timestamp hiện tại $T_1$.
3. Lần lượt gửi lệnh `SET key my_random_value NX PX 30000` đến cả 5 node với timeout mạng ngắn (5-50ms).
4. Nếu lấy khóa thành công trên $\ge \frac{N}{2} + 1$ node (tức $\ge 3$ node) và tổng thời gian xin khóa $T_2 - T_1 < \text{Lock Validity Time}$, Client được coi là **Chiếm khóa thành công**. Thời gian giữ khóa thực tế bằng $\text{Validity Time} - (T_2 - T_1)$.
5. Nếu thất bại, Client gửi lệnh giải phóng khóa (Lua script so sánh `my_random_value`) đến **toàn bộ 5 node**.

### 2. Khóa phân tán trên Apache ZooKeeper
- **Cơ chế**:
  1. Client tạo một **Ephemeral Sequential Node (Nút tạm thời có thứ tự)** dưới đường dẫn `/locks/lock_`.
  2. Lấy danh sách tất cả các nút con trong `/locks`.
  3. Nếu nút của Client có số thứ tự nhỏ nhất $\rightarrow$ **Lấy khóa thành công**.
  4. Nếu không phải nhỏ nhất, Client chỉ đặt một **Watcher theo dõi nút liền kề trước nó** (Tránh *Hiệu ứng đàn cừu - Herd Effect / Thundering Herd*).
  5. Khi nút trước hoàn tất và xóa đi, ZooKeeper kích hoạt Watcher đánh thức Client tiếp theo.
- **Ưu điểm**: Độ tin cậy cao, tự giải phóng khóa khi Client bị mất kết nối (nhờ tính chất nút Ephemeral).

<p id="分布式事务"></p>

## 3. 4 Giải pháp Giao dịch Phân tán (Distributed Transactions)

### 1. Two-Phase Commit (2PC / XA Protocol)
- **Coordinator (Bộ điều phối)** hỏi tất cả các CSDL tham gia: *"Đã chuẩn bị xong chưa?"* (Prepare Phase).
- Nếu 100% các bên đều trả lời YES $\rightarrow$ Coordinator phát lệnh `COMMIT`; Nếu có bất kỳ bên nào từ chối hoặc timeout $\rightarrow$ Phát lệnh `ROLLBACK` (Commit Phase).
- *Nhược điểm*: Bị khóa tài nguyên đồng bộ kéo dài, thông lượng thấp, không phù hợp cho Microservices quy mô lớn.

### 2. TCC Pattern (Try - Confirm - Cancel)
- **Try**: Kiểm tra tính hợp lệ và **Tạm khóa / Giữ chỗ tài nguyên** (ví dụ trừ số dư khả dụng, tăng số dư đóng băng).
- **Confirm**: Thực thi giao dịch chính thức bằng tài nguyên đã giữ chỗ.
- **Cancel**: Giải phóng tài nguyên giữ chỗ nếu có bước thất bại (Bù trừ nghiệp vụ).
- *Nhược điểm*: Lượng code nghiệp vụ bù trừ rất phức tạp.

### 3. Giải pháp Nhất quán cuối cùng qua Reliable Message Queue (RocketMQ Transaction Message - Khuyên dùng)
1. Service A gửi tin nhắn **Half Message (Prepared Message)** lên RocketMQ.
2. Service A thực thi Local Transaction trong DB của mình.
3. Nếu thành công $\rightarrow$ Gửi lệnh `Commit Message` cho RocketMQ để chuyển tiếp tin nhắn đến Service B; Nếu thất bại $\rightarrow$ Gửi lệnh `Rollback`.
4. RocketMQ có cơ chế **Check-back (Thăm dò trạng thái)** tự động hỏi lại Service A nếu không nhận được phản hồi sau một khoảng thời gian.
5. Service B nhận tin nhắn và thực thi Local Transaction của mình (kèm cơ chế Retry vô hạn và Xử lý lũy thừa - Idempotency).

### 4. Best-Effort Notification (Thông báo Nỗ lực Tối đa)
Sử dụng cho các giao dịch liên kết bên thứ 3 (như Cổng thanh toán VNPay, Momo): Bên nhận chủ động gọi webhook lặp lại theo quy luật thời gian lũy thừa ($1\text{s}, 5\text{s}, 30\text{s}, 2\text{m}, 10\text{m}$) kèm API tra cứu trạng thái chủ động.
