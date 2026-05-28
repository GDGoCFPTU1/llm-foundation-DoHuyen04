KIỂM TRA # Ngày 1 — Bài Tập & Phản Ánh

## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:

```bash
python template.py
```

Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature

Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)

> Temperature càng cao, phản hồi càng đa dạng và sáng tạo hơn. Ở temperature 0.0, câu trả lời có tính xác định cao, gần như giống nhau mỗi lần gọi. Khi tăng lên 0.5 và 1.0, câu trả lời bắt đầu thay đổi về cách diễn đạt và nội dung chi tiết. Ở temperature 1.5, phản hồi có thể rất khác biệt và đôi khi không kiểm soát được.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**

> Temperature 0.2 - 0.3 là phù hợp nhất cho chatbot hỗ trợ khách hàng vì đảm bảo câu trả lời nhất quán, chính xác và dễ dự đoán, trong khi vẫn có một chút linh hoạt để tránh câu trả lời quá cứng nhắc.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí

Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**

> Tổng token mỗi ngày = 10,000 users × 3 calls × 350 tokens = 10,500,000 tokens
> Chi phí GPT-4o = (10,500,000 / 1000) × $0.010 = $105
> Chi phí GPT-4o-mini = (10,500,000 / 1000) × $0.0006 = $6.30
> GPT-4o đắt hơn khoảng 16.67 lần so với GPT-4o-mini cho workload này.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**

> GPT-4o xứng đáng khi cần xử lý các yêu cầu phức tạp đòi hỏi suy luận sâu, phân tích tinh vi, hoặc khi cần độ chính xác cao nhất - ví dụ như trong lĩnh vực y tế, pháp lý, hoặc tài chính.
> GPT-4o-mini là lựa chọn tốt hơn cho các tác vụ đơn giản, lặp đi lặp lại như chatbot hỗ trợ thông thường, hệ thống FAQ, hoặc khi scale lớn với ngân sách hạn chế.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming

**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)

> Streaming quan trọng nhất khi tạo trải nghiệm tương tác thời gian thực - như chatbot hội thoại, công cụ viết code, hoặc các ứng dụng mà người dùng cần nhìn thấy tiến trình sinh text ngay lập tức để duy trì sự tham gia. Non-streaming phù hợp hơn khi cần xử lý batch với nhiều requests, hoặc khi toàn bộ response cần được đánh giá trước khi hiển thị (ví dụ: tóm tắt bài viết dài) để đảm bảo chất lượng và nhất quán.

## Danh Sách Kiểm Tra Nộp Bài

- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định
