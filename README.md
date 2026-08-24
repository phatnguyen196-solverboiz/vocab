# Vocabulary Paste & Learn Pro

Ứng dụng học từ vựng tĩnh, chạy hoàn toàn trên trình duyệt và lưu dữ liệu bằng `localStorage`.

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

## Chạy local

Mở `index.html` trực tiếp hoặc phục vụ thư mục bằng một static HTTP server.

## Nguồn dữ liệu và độ bền

Datamuse hiện cung cấp API đọc, hỗ trợ `rel_syn`, wildcard `sp`, metadata từ loại và tần suất. Theo tài liệu của Datamuse, API sẽ yêu cầu API key từ ngày 01/01/2027. Vì vậy ứng dụng không phụ thuộc hoàn toàn vào dịch vụ: dữ liệu nhập/sửa thủ công, cache cục bộ và các chế độ học vẫn hoạt động khi không gọi được API.

- Tài liệu: https://www.datamuse.com/api/
