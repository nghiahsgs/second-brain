# Karpathy không hỏi AI — Anh ấy bắt AI xây thư viện tri thức

**Nguồn:** Bài đăng Facebook của Phong Ho (4 ngày trước)
**Ngày lưu:** 2026-04-27

## Nội dung chính

Andrej Karpathy, thành viên sáng lập OpenAI và cựu Director of AI tại Tesla, vừa chia sẻ một thói quen dùng AI khiến mình ngồi xuống xem lại toàn bộ cách mình đang làm việc với AI.

Điểm khác biệt không phải anh ấy dùng AI nhiều hơn. Là cách anh ấy dùng khác hẳn số đông.

### Vấn đề của số đông
- Đa số coi AI như phiên bản Google cao cấp
- Hỏi xong đóng tab
- Tuần sau cần lại thì hỏi lại từ đầu
- Mọi insight bay đi theo phiên chat
- Kho tri thức cá nhân vẫn bằng 0

### Cách Karpathy làm khác
- Biến AI thành **quản sư cho kho tri thức của riêng mình**, không phải "người trả lời câu hỏi"
- Toàn bộ kiến trúc gọn trong **3 tầng file trên ổ cứng**
- Không server, không database, không vector embedding

### Kiến trúc 3 tầng

**Tầng 1: raw/** — Tài liệu thô. Bài báo, paper, screenshot, transcript, ghi chú rời. AI chỉ đọc chứ không sửa.

**Tầng 2: wiki/** — Markdown files do AI tự viết. Trang tóm tắt, trang khái niệm, trang so sánh, và backlinks nối các trang thành mạng lưới. Trung tâm là file index.md. AI sở hữu hoàn toàn tầng này.

**Tầng 3: CLAUDE.md** — File cấu hình duy nhất ở gốc vault. Dạy AI biết kho được cấu trúc ra sao, khi nào tạo trang mới, khi nào cập nhật trang cũ, format thế nào. Đây là "key configuration file", biến chatbot chung chung thành người quản lý wiki có kỷ luật.

### Kết quả
- Cả ngành AI đua nhau dựng vector database, RAG pipeline, thuê ML engineer
- Karpathy giải xong bài toán "làm sao AI nhớ được ngữ cảnh" bằng một folder trên ổ cứng
