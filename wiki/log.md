# 📝 Nhật Ký Thao Tác

## 2026-04-27

### Ingest #1: Bài viết Karpathy Second Brain
- **Nguồn:** `raw/articles/karpathy-second-brain.md`
- **Thao tác:** Tạo mới
- **Trang tạo mới:**
  - `wiki/sources/source-karpathy-second-brain.md`
  - `wiki/concepts/second-brain.md`
  - `wiki/entities/andrej-karpathy.md`
  - `wiki/comparisons/rag-vs-llm-wiki.md`
- **Trang cập nhật:** `wiki/index.md`
- **Ghi chú:** Nguồn đầu tiên được nạp. Đây là bài viết nền tảng giải thích kiến trúc 3 tầng của Karpathy.

### Ingest #2: Ghi chú buổi học Chăm sóc da
- **Nguồn:** `raw/notes/buoi-hoc-cham-soc-da-co-ban.md`
- **Thao tác:** Tạo mới
- **Trang tạo mới:**
  - `wiki/sources/source-buoi-hoc-cham-soc-da.md`
  - `wiki/concepts/cham-soc-da-co-ban.md`
  - `wiki/concepts/hoat-chat-skincare.md`
- **Trang cập nhật:** `wiki/index.md`
- **Ghi chú:** Kiến thức nền tảng về skincare cho spa. Bao gồm phân loại da, quy trình, và hoạt chất.

### Ingest #3: Ghi chú buổi học Marketing Spa
- **Nguồn:** `raw/notes/buoi-hoc-marketing-spa.md`
- **Thao tác:** Tạo mới
- **Trang tạo mới:**
  - `wiki/sources/source-buoi-hoc-marketing.md`
  - `wiki/concepts/marketing-spa.md`
  - `wiki/concepts/quan-ly-khach-hang-spa.md`
- **Trang cập nhật:** `wiki/index.md`
- **Ghi chú:** Chiến lược marketing đa kênh cho spa. Liên kết với [[quan-ly-khach-hang-spa]] về phần CRM.

### Ingest #4: Crawl chứng khoán VN — 8 mã VN30 đại diện ngành
- **Mục đích:** Demo khả năng wiki cho chủ đề tra cứu nhiều, đồng thời cung cấp kiến thức cơ bản về TTCK VN.
- **Mã được crawl:** VCB (ngân hàng), FPT (công nghệ), VNM (tiêu dùng/sữa), VIC (BĐS/đa ngành), HPG (thép), MWG (bán lẻ), GAS (năng lượng), MSN (tiêu dùng/holding).
- **Nguồn:** Wikipedia tiếng Việt (profile/lịch sử) + Simplize.vn (snapshot tài chính 2026-04-27) — tổng 16 file.
- **Trang tạo mới:**
  - **8 entity pages:** `wiki/entities/{vcb,fpt,vnm,vic,hpg,mwg,gas,msn}.md`
  - **1 entity người:** `wiki/entities/pham-nhat-vuong.md`
  - **5 concept nền:** `wiki/concepts/{vn-stock-101,chi-so-tai-chinh,co-phieu-co-tuc,co-phieu-chu-ky,co-phieu-tang-truong}.md`
  - **7 concept ngành:** `wiki/concepts/{ngan-hang,bat-dong-san,cong-nghe,tieu-dung,ban-le,thep,nang-luong-dau-khi}.md`
  - **1 comparison:** `wiki/comparisons/vic-vs-vnm.md` (tăng trưởng vs cổ tức)
- **Trang cập nhật:** `wiki/index.md` (cấu trúc lại theo nhóm chủ đề)
- **Cross-link cao:** ~80 wikilink mới — wiki giờ "dày" về chứng khoán
- **Lưu ý dữ liệu:**
  - Giá/vốn hóa/P/E là **snapshot ngày 2026-04-27** — sẽ lỗi thời nhanh, lint sau 1 tháng cần check
  - Một số số liệu Wikipedia khá cũ (VIC tài chính 2018, HPG 2021, Masan Consumer 2016) — đã ghi rõ năm trong nội dung
  - GAS doanh thu 2021 ghi "915 tỷ VND" trong Wikipedia có vẻ thiếu zero (PV GAS doanh thu thực tế ~80.000 tỷ) — **flag để verify**
