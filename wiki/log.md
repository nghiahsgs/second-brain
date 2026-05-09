# 📝 Nhật Ký Thao Tác

## 2026-04-27

### Reset wiki — chuyển sang chủ đề Chứng khoán VN
- **Lý do:** Demo wiki cho domain tra cứu nhiều (chứng khoán VN). Skincare và methodology nội dung làm loạn graph.
- **Đã xóa:**
  - Skincare: 2 raw notes + 4 wiki concepts + 2 source pages
  - Karpathy/methodology: 1 raw article + 1 concept + 1 entity + 1 comparison + 1 source page
  - Stock wiki cũ (lần ingest đầu thiếu source-summary): 9 entities + 12 concepts + 1 comparison
- **Giữ:** 16 raw files trong `raw/articles/stocks/`, CLAUDE.md

### Ingest #1: Chứng khoán VN — 8 mã VN30 đại diện ngành (sạch)
- **Mục đích:** Demo end-to-end ingest workflow theo CLAUDE.md spec, lần này có đủ source-summary pages.
- **Mã ingest:** VCB (ngân hàng), FPT (công nghệ), VNM (tiêu dùng/sữa), VIC (BĐS/đa ngành), HPG (thép), MWG (bán lẻ), GAS (năng lượng), MSN (tiêu dùng/holding).
- **Nguồn raw:** 16 file (8 mã × 2 nguồn: Wikipedia VN + Simplize.vn) — snapshot 2026-04-27.
- **Trang tạo mới (30):**
  - **8 source-summary** (NEW lần này): `wiki/sources/source-{vcb,fpt,vnm,vic,hpg,mwg,gas,msn}.md` — mỗi trang gói 2 raw, ghi rõ giới hạn nguồn
  - **8 entity cổ phiếu:** `wiki/entities/{vcb,fpt,vnm,vic,hpg,mwg,gas,msn}.md` — link về source-summary thay vì raw trực tiếp
  - **1 entity người:** `wiki/entities/pham-nhat-vuong.md`
  - **5 concept nền:** `wiki/concepts/{vn-stock-101,chi-so-tai-chinh,co-phieu-co-tuc,co-phieu-chu-ky,co-phieu-tang-truong}.md`
  - **7 concept ngành:** `wiki/concepts/{ngan-hang,bat-dong-san,cong-nghe,tieu-dung,ban-le,thep,nang-luong-dau-khi}.md`
  - **1 comparison:** `wiki/comparisons/vic-vs-vnm.md`
- **Cross-link:** ~80 wikilink — graph dày đặc quanh entity
- **Khác lần trước:**
  - ✅ Có source-summary đầy đủ → trace được từng claim về raw cụ thể
  - ✅ Frontmatter `sources` link tới `[[source-XXX]]` thay vì raw path → graph Obsidian show được
  - ✅ Các nguồn lỗi/cũ được flag rõ trong source-summary (VD: GAS Wiki doanh thu thiếu zero, VIC tài chính 2018, MSN thị phần 2016)

## 2026-05-08

### Query → Save: VCB vs FPT
- **Thao tác:** Query so sánh VCB vs FPT → lưu thành trang comparison
- **Trang tạo mới:** `wiki/comparisons/vcb-vs-fpt.md`
- **Trang cập nhật:** `wiki/index.md` (thêm comparison mới, tổng 31 trang)
- **Nguồn tham khảo:** [[vcb]], [[fpt]], [[ngan-hang]], [[cong-nghe]], [[chi-so-tai-chinh]], [[co-phieu-tang-truong]]

### Lưu ý dữ liệu cần verify lần sau
- **GAS:** Wikipedia ghi doanh thu 2021 = 915 tỷ VND — có vẻ thiếu zero, thực tế ~80.000 tỷ. Verify từ BCTC.
- **Snapshot Simplize:** giá/P/E ngày 2026-04-27 sẽ lỗi thời nhanh. Lint sau ~1 tháng cần check + cập nhật.
- **Wikipedia một số mã có dữ liệu cũ** (VIC 2018, HPG 2021, MSN 2016) — chỉ dùng làm profile, không dùng làm chỉ số.
