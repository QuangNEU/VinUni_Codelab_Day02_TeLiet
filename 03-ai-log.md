# Nhật ký tương tác AI (AI Log & Reflection)

**1. AI đã giúp tôi làm được gì?**
- AI đóng vai trò như một người "brainstorming partner" rất tốt trong giai đoạn đầu (Phase 1). Khi tôi bị bí ý tưởng, việc cung cấp cho AI các "Lens" (Repetitive, Time-consuming) và scope của Vingroup giúp mô hình nhả ra được rất nhiều quy trình vận hành bề nổi.
- Giúp tôi format lại các thẻ bài toán (Problem Cards) một cách gọn gàng, chia rõ bước nào thủ công, bước nào AI có thể can thiệp.

**2. AI đã sai, ảo tưởng (hallucinate) hoặc ngây ngô ở đâu?**
- Lúc đầu, AI đưa ra các ý tưởng quá "sách giáo khoa" và không cập nhật. Ví dụ: AI gợi ý bài toán "bác sĩ đọc cho y tá chép bệnh án", trong khi thực tế ở các bệnh viện lớn (như Vinmec) bác sĩ đã tự gõ thẳng vào hệ thống từ lâu. 
- Về phần Metric, AI hay có xu hướng "ảo tưởng" sức mạnh, đưa ra các chỉ số tuyệt đối kiểu như "100% tự động hóa", "độ chính xác 100%".
- Khi gợi ý giải pháp, AI thường bỏ qua yếu tố an toàn (Operational Boundary) trong vận hành thực tế của doanh nghiệp.

**3. Tôi đã sửa prompt, thiết lập ranh giới và tương tác lại như thế nào?**
- Thay vì hỏi chung chung, tôi ép AI phải đóng vai một "System Engineer / CTO khắt khe". Tôi bắt AI phải tập trung vào dữ liệu phi cấu trúc (Unstructured Data) hoặc các tình huống người lao động không thể thao tác bằng tay (hands-free).
- Nhờ vậy, tôi và AI đã pivot (xoay trục) thành công sang bài toán thực tế hơn: "Voice-Agent tra cứu tài liệu rảnh tay cho thợ sửa xe VinFast". 
- Tôi đã phải tự mình điều chỉnh lại các Metric (VD: sửa từ 100% xuống "giảm 20% thời gian lưu chuồng", thêm bước Human-in-the-loop) để bản scoping trở nên khả thi khi làm thực tế.