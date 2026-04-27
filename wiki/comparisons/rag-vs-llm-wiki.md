---
title: "RAG vs LLM Wiki"
type: comparison
sources:
  - raw/articles/karpathy-second-brain.md
related:
  - "[[second-brain]]"
  - "[[andrej-karpathy]]"
created: 2026-04-27
updated: 2026-04-27
confidence: high
---

# RAG vs LLM Wiki — Khi Nào Dùng Cái Nào?

## So sánh tổng quan

| Tiêu chí | RAG (truyền thống) | LLM Wiki (Karpathy) |
|----------|-------------------|-------------------|
| **Hạ tầng** | Vector DB + embedding pipeline | Folder `.md` files |
| **Tri thức** | Stateless — mỗi query độc lập | Stateful — tích lũy theo thời gian |
| **Liên kết chéo** | Tìm ad-hoc mỗi lần | AI tạo sẵn, luôn có |
| **Bảo trì** | Cập nhật embedding, rebuild index | AI cập nhật mỗi khi nạp nguồn mới |
| **Chi phí token/query** | Cao (retrieve + re-rank + generate) | Thấp (đọc index + vài trang) |
| **Truy vết** | Chunk-level (thường bị mất ngữ cảnh) | Source-level (link về file gốc) |
| **Phát hiện mâu thuẫn** | Không | Có (qua Lint) |
| **Quy mô phù hợp** | Enterprise (triệu tài liệu) | Cá nhân/nhóm (<200 tài liệu nguồn) |

## Khi nào dùng RAG?
- Hàng triệu tài liệu
- Tài liệu thay đổi liên tục
- Cần query nhanh sub-second
- Nhiều team với quyền truy cập khác nhau

## Khi nào dùng LLM Wiki?
- Dưới ~200 tài liệu nguồn
- Muốn tri thức compound — mỗi nguồn mới cải thiện toàn bộ wiki
- Cần truy vết (mọi khẳng định link về nguồn gốc)
- Không muốn setup infra phức tạp
- **Phù hợp cho: chủ spa, freelancer, học viên, nhóm nhỏ**

## Kết luận
Với quy mô cá nhân/spa nhỏ: **LLM Wiki là lựa chọn tốt hơn** — đơn giản, miễn phí infra, và tri thức tích lũy theo thời gian. Xem [[second-brain]] để hiểu kiến trúc chi tiết.
