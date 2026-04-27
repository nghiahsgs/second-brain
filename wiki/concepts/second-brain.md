---
title: "Second Brain — Kho Tri Thức Cá Nhân với AI"
type: concept
sources:
  - raw/articles/karpathy-second-brain.md
related:
  - "[[andrej-karpathy]]"
  - "[[rag-vs-llm-wiki]]"
created: 2026-04-27
updated: 2026-04-27
confidence: high
---

# Second Brain — Kho Tri Thức Cá Nhân với AI

## Tổng quan
Second Brain là phương pháp xây dựng kho tri thức cá nhân, sử dụng AI làm "quản sư" — AI đọc tài liệu, tóm tắt, tổ chức, liên kết chéo, và duy trì wiki thay cho con người.

## Kiến trúc 3 tầng (theo [[andrej-karpathy]])

### Tầng 1: `raw/` — Tài liệu gốc
- Bài báo, paper, screenshot, ghi chú, transcript
- AI chỉ **đọc**, không bao giờ sửa
- Là nguồn sự thật duy nhất (source of truth)

### Tầng 2: `wiki/` — Wiki do AI duy trì
- File markdown (.md) — tương thích Obsidian, Notion
- Trang tóm tắt, trang khái niệm, trang so sánh
- Backlinks `[[wikilink]]` nối thành mạng lưới
- Trung tâm là `index.md` — bản đồ toàn wiki
- AI sở hữu hoàn toàn tầng này

### Tầng 3: `CLAUDE.md` — File cấu hình
- Dạy AI cách vận hành wiki
- Cấu trúc, format, khi nào tạo trang mới, khi nào cập nhật
- Biến chatbot thành "người quản lý wiki có kỷ luật"

## Ưu điểm so với cách truyền thống
- Không cần server, database, hay vector embedding
- Chi phí gần bằng 0 (chỉ cần LLM subscription)
- Tri thức tích lũy theo thời gian (compound)
- Có thể kiểm tra mâu thuẫn (lint)
- Truy vết được mọi khẳng định về nguồn gốc

## So sánh chi tiết
Xem [[rag-vs-llm-wiki]] để hiểu khi nào dùng Second Brain, khi nào dùng RAG.
