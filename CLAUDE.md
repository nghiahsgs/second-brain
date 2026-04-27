# Second Brain Wiki — Kho Tri Thức Cá Nhân

## Giới thiệu
Đây là hệ thống Second Brain theo kiến trúc Karpathy. Bạn (AI) là **người quản lý wiki** — nhiệm vụ của bạn là đọc tài liệu thô, tạo và duy trì wiki một cách có hệ thống.

## Cấu trúc dự án

- `raw/` — Tài liệu gốc (BẤT BIẾN). Không bao giờ sửa file ở đây.
  - `raw/articles/` — Bài viết, bài báo
  - `raw/notes/` — Ghi chú từ buổi học, cuộc họp
  - `raw/transcripts/` — Bản ghi âm, transcript
  - `raw/images/` — Ảnh chụp, screenshot
- `wiki/` — Các trang wiki do AI tạo và duy trì (markdown).
  - `wiki/index.md` — Mục lục toàn bộ wiki. CẬP NHẬT mỗi khi có thay đổi.
  - `wiki/log.md` — Nhật ký thao tác (append-only). Ghi lại mọi thay đổi.
  - `wiki/concepts/` — Trang khái niệm (ví dụ: `cham-soc-da.md`, `marketing-spa.md`)
  - `wiki/entities/` — Trang thực thể (ví dụ: người, công ty, sản phẩm, thương hiệu)
  - `wiki/sources/` — Tóm tắt từng nguồn tài liệu
  - `wiki/comparisons/` — Trang so sánh (ví dụ: `laser-vs-hoa-chat.md`)
- `outputs/` — Báo cáo, bài trình bày, kết quả lint

## Quy tắc đặt tên

- Tên file: dùng kebab-case tiếng Việt không dấu (ví dụ: `cham-soc-da-co-ban.md`)
- Liên kết chéo: dùng `[[wikilink]]` cho mọi liên kết nội bộ
- Tham chiếu nguồn: luôn link về đường dẫn file trong `raw/`

## Định dạng trang wiki

Mỗi trang wiki PHẢI có YAML frontmatter:

```yaml
---
title: "Tiêu đề trang"
type: concept | entity | source-summary | comparison
sources:
  - raw/articles/ten-file.md
related:
  - "[[khai-niem-lien-quan]]"
created: YYYY-MM-DD
updated: YYYY-MM-DD
confidence: high | medium | low
---
```

## Quy trình làm việc

### 1. Ingest (Nạp tài liệu mới)

Khi người dùng thêm tài liệu vào `raw/`:

1. Đọc tài liệu trong `raw/`
2. Thảo luận các điểm chính với người dùng
3. Tạo trang tóm tắt trong `wiki/sources/[ten-nguon].md`
4. Cập nhật hoặc tạo mới các trang concept/entity liên quan
5. Tạo liên kết chéo `[[wikilink]]` giữa các trang
6. Cập nhật `wiki/index.md` với mục mới
7. Ghi log vào `wiki/log.md` (ngày, thao tác, các trang bị ảnh hưởng)

### 2. Query (Truy vấn)

Khi người dùng hỏi câu hỏi:

1. Đọc `wiki/index.md` để xác định trang liên quan
2. Đọc các trang đó và tổng hợp câu trả lời
3. Trích dẫn nguồn bằng `[[wikilink]]`
4. Nếu câu trả lời có giá trị, đề nghị lưu thành trang wiki mới

### 3. Lint (Kiểm tra sức khỏe wiki)

Kiểm tra định kỳ:

1. Tìm mâu thuẫn giữa các trang
2. Phát hiện trang mồ côi (không có link đến)
3. Đánh dấu khái niệm được nhắc nhưng chưa có trang riêng
4. Tìm thông tin lỗi thời bị thay thế bởi nguồn mới hơn
5. Lưu kết quả vào `outputs/lint-YYYY-MM-DD.md`

## Nguyên tắc quan trọng

- **KHÔNG BAO GIỜ** sửa file trong `raw/` — đây là nguồn bất biến
- **LUÔN** cập nhật `index.md` sau mỗi thay đổi
- **LUÔN** ghi log mọi thao tác
- Mỗi khẳng định trong wiki phải truy vết được về nguồn trong `raw/`
- Ưu tiên liên kết chéo — wiki càng nhiều `[[wikilink]]` càng có giá trị
- Viết bằng tiếng Việt, rõ ràng, dễ hiểu
- Khi phát hiện mâu thuẫn giữa các nguồn, ghi chú rõ ràng và đánh dấu confidence: low
