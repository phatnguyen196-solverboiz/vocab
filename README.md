# Vocabulary Paste & Learn Pro

Ứng dụng học từ vựng tĩnh, chạy hoàn toàn trên trình duyệt và lưu dữ liệu bằng `localStorage`.

## Tài khoản cục bộ

- Người học có thể tạo tài khoản chỉ bằng tên đăng nhập và mật khẩu, sau đó đăng nhập/đăng xuất hoặc đổi tài khoản ngay trên trang.
- Mỗi tài khoản có danh sách từ, trạng thái đánh dấu, từ sai và toàn bộ thống kê riêng. Dữ liệu chế độ khách cũ vẫn được giữ nguyên và không bị trộn vào tài khoản.
- Mật khẩu không được lưu dạng văn bản thuần; ứng dụng tạo salt riêng và băm bằng PBKDF2-SHA-256 trước khi lưu.
- Vì đây là ứng dụng tĩnh trên GitHub Pages, tài khoản và dữ liệu chỉ tồn tại trong trình duyệt trên thiết bị hiện tại; chưa có đồng bộ đa thiết bị hoặc khôi phục mật khẩu qua máy chủ.

## Đồng nghĩa, word family và collocation

Mỗi mục từ hỗ trợ ba trường mở rộng:

- `synonyms`: danh sách từ đồng nghĩa.
- `wordFamily`: danh sách thành viên cùng họ từ, có thể kèm từ loại.
- `collocations`: các cụm từ tự nhiên thường đi cùng mục từ.

Có ba cách bổ sung dữ liệu:

1. Thêm ngay trong dữ liệu dán vào:

   ```text
   create (v) – tạo ra | syn: make, produce | family: noun: creation; adjective: creative; adverb: creatively | collocations: create an account, create opportunities
   ```

2. Mở **Sửa đồng nghĩa / word family / collocation** ở từng mục trong phần Preview.
3. Bấm **Gợi ý đồng nghĩa, word family & collocation** để lấy đề xuất từ Datamuse API.

Gợi ý tự động được cache 30 ngày. Đồng nghĩa dùng quan hệ WordNet `rel_syn`; word family dùng truy vấn hình thái theo gốc từ, sau đó lọc hậu tố và ưu tiên từ có tần suất cao. Collocation kết hợp các quan hệ từ thường đứng trước `rel_bgb` và đứng sau `rel_bga`. Đây là gợi ý heuristic, nên người học vẫn cần kiểm tra theo ngữ cảnh và có thể sửa thủ công.

## Chế độ học mới

- **Từ đồng nghĩa**: chọn từ đồng nghĩa đúng.
- **Word family**: chọn thành viên thuộc cùng họ từ.
- **Collocation**: chọn cụm từ tự nhiên có chứa từ đang học.
- **Từ đã đánh dấu**: học riêng các mục đã bấm sao trong Preview; trạng thái sao được lưu cùng dữ liệu cục bộ.
- Flashcard hiển thị nghĩa, đồng nghĩa, word family và collocation ở mặt sau.
- Sau mỗi đáp án, khối **Ghi nhớ thêm** hiện toàn bộ dữ liệu mở rộng của từ.

Nếu nhóm đang chọn chưa có dữ liệu phù hợp, ứng dụng sẽ hướng dẫn bổ sung thay vì bắt đầu một phiên trống.

## Trò chơi từ vựng

- **Lật thẻ trí nhớ**: ghép cặp từ tiếng Anh – nghĩa tiếng Việt; tính số lượt lật, số lần lỡ và điểm.
- **Xếp chữ**: đảo chữ của từ/cụm từ tiếng Anh rồi yêu cầu giải mã theo nghĩa tiếng Việt.
- **Bắt từ**: chọn nhanh từ tiếng Anh đúng trong các “bong bóng” trước khi hết 8 giây.
- **Đúng/Sai chớp nhoáng**: phán đoán cặp từ – nghĩa trong 6 giây.
- Các game dùng chung bộ lọc nhóm, số câu, streak, từ sai và dashboard thống kê với các chế độ học khác.

## Xuất và nhập lại Word

- **Xuất Word (.docx)** tạo một learning pack có bảng từ, nghĩa, đồng nghĩa, word family và collocation.
- File có thêm vùng dữ liệu tái nhập. Có thể sửa các dòng này trong Word rồi dùng **Nhập lại từ Word** để đưa danh sách trở lại web.
- Việc xuất/nhập chạy ngay trong trình duyệt. Thư viện DOCX và JSZip chỉ được tải khi người dùng bấm chức năng tương ứng.

## Thống kê nâng cao

Dashboard mới lưu và hiển thị:

- Tổng câu đã trả lời, accuracy toàn thời gian, tổng số phiên và streak tốt nhất.
- Chuỗi ngày học liên tiếp và hoạt động trong 7 ngày gần nhất.
- Accuracy theo từng chế độ học.
- Hiệu suất đúng/sai/bỏ qua theo từng nhóm từ.
- Sáu phiên gần nhất và nhận xét tự động về chế độ mạnh, nhóm cần ôn, tỷ lệ bỏ qua.
- Thống kê từng từ được lưu nội bộ để dùng cho việc xếp hạng từ khó.

Dữ liệu thống kê cũ được tự động chuyển sang schema mới. Tối đa 100 phiên gần nhất được giữ trong `localStorage`; hai biểu đồ phiên học chỉ vẽ 20 phiên gần nhất để tránh quá tải giao diện.

## Ôn tập ngắt quãng thông minh

- Chế độ **Ôn thông minh hôm nay** tự chọn các từ mới, đến hạn hoặc quá hạn trong nhóm đang chọn.
- Mỗi từ có lịch riêng gồm số lần nhớ liên tiếp, khoảng cách ôn, hệ số dễ, số lần quên và ngày đến hạn.
- Trả lời đúng làm khoảng cách tăng dần từ 1 ngày, 3 ngày rồi nhân theo độ dễ của từ. Trả lời sai đặt từ về lịch ôn lại trong ngày và giảm hệ số dễ; bỏ qua cũng giữ từ trong hàng đợi hôm nay.
- Lịch được cập nhật từ mọi chế độ học và trò chơi, không chỉ từ chế độ ôn thông minh. Dữ liệu lịch nằm trong thống kê riêng của từng tài khoản.

## Thống kê học thông minh

- Dashboard hiển thị số từ cần ôn hôm nay, số từ đã thành thạo và số từ có nguy cơ quên trong 7 ngày.
- Mức độ thành thạo kết hợp accuracy, chuỗi trả lời đúng, khoảng cách ôn, số lần quên và độ ghi nhớ dự báo theo thời gian.
- Heatmap 35 ngày cho biết nhịp học; bảng phân bố chia từ thành Mới, Đang học, Đang nhớ và Thành thạo.
- Danh sách **Từ cần ưu tiên** xếp từ quá hạn/yếu lên trước, đồng thời hiển thị lịch tiếp theo, mức thành thạo và tỷ lệ ghi nhớ dự báo.

## Phân tích lỗi sai theo nhóm

- Có thể lọc từng nhóm từ theo 7 ngày, 30 ngày hoặc toàn bộ thời gian.
- Bảng tổng hợp hiển thị accuracy, số lượt sai, tỷ lệ bỏ qua và số từ đang đến lịch ôn của nhóm.
- Mỗi lượt đúng, sai hoặc bỏ qua được ghi thành một sự kiện học cục bộ gồm nhóm, chế độ, từ và thời điểm; tối đa 2.000 sự kiện gần nhất được giữ cho từng tài khoản.
- Hệ thống xếp hạng các dạng bài gây sai, các từ khó nhất và tính điểm rủi ro học lại cho từng nhóm.
- Đề xuất luyện tập thay đổi theo lỗi nổi bật: Nhập nghĩa, Việt → Anh, collocation, word family, chính tả hoặc flashcard.
- Dữ liệu thống kê cũ vẫn dùng được cho tổng quan toàn thời gian và danh sách từ khó; phân tích chi tiết theo dạng bài được tích lũy từ phiên bản này trở đi.

## Các lỗi đã sửa

- `reading` và `listening` có nghĩa không còn bị nhận nhầm thành tiêu đề nhóm.
- Số dòng lỗi giữ đúng số dòng gốc kể cả khi dữ liệu có dòng trống.
- Việt → Anh chấp nhận các đáp án thay thế dạng `questionnaire / survey`.
- Không còn chấp nhận đáp án quá ngắn chỉ vì nó là một phần nhỏ của nghĩa.
- “Câu tiếp theo” trên câu chưa trả lời được tính là bỏ qua và vẫn tăng tiến độ.
- Lượt sai hiển thị theo số lần sai, không phải số từ sai duy nhất.
- Mỗi phiên chỉ được ghi một lần; phím tắt hoặc bấm kết thúc nhiều lần không nhân đôi lịch sử.
- Có nút kết thúc phiên thủ công; phiên dở được ghi lại trước khi khởi động lại.
- Ứng dụng vẫn hoạt động nếu Chart.js CDN không tải được; chỉ phần biểu đồ bị ẩn.
- Phím tắt `N`, `F` và `1–4` không còn kích hoạt khi con trỏ đang ở ô nhập, textarea, select hoặc vùng soạn thảo; việc gõ đáp án không còn làm nhảy sang từ khác.

## Chạy local

Mở `index.html` trực tiếp hoặc phục vụ thư mục bằng một static HTTP server.

## Nguồn dữ liệu và độ bền

Datamuse hiện cung cấp API đọc, hỗ trợ `rel_syn`, wildcard `sp`, metadata từ loại và tần suất. Theo tài liệu của Datamuse, API sẽ yêu cầu API key từ ngày 01/01/2027. Vì vậy ứng dụng không phụ thuộc hoàn toàn vào dịch vụ: dữ liệu nhập/sửa thủ công, cache cục bộ và các chế độ học vẫn hoạt động khi không gọi được API.

- Tài liệu: https://www.datamuse.com/api/
