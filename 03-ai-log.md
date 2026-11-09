# 📝 Nhật Ký Tương Tác AI & Tự Luận Phản Ánh (AI Log & Reflection)

* **Học viên:** Lê Quân Bảo
* **Mã sinh viên:** 2A202603888
* **Dự án Lab 02:** AI Product Scoping — Vin Smart Future (Đề tài: Vinmec SafePrescribe AI)
* **Mô hình AI sử dụng đồng hành:** Google Gemini (Gemini Flash thông qua Python SDK & Web Thought-Partner)

---

## 1. Vai trò của AI trong quá trình làm việc (AI đã giúp được gì?)

Trong suốt quá trình thực hiện bài Lab 02 từ khâu tìm kiếm cơ hội (Phase 1) đến thiết kế ranh giới vận hành (Phase 4), AI đóng vai trò như một người cộng sự tư vấn giải pháp (Thought Partner) và trợ lý kỹ thuật:

- **Brainstorm và phân loại bài toán vận hành:** Hỗ trợ quét nhanh các điểm nghẽn thực tế qua 4 Lenses (Lặp lại, Tốn thời gian, AI-upgrade, Pain từ người khác) trên hệ sinh thái đa mảng của Vingroup (Vinmec, VinFast, Xanh SM, Vinhomes).
- **Cấu trúc hóa quy trình y khoa phức tạp:** Giúp phân rã quy trình kê đơn thuốc lâm sàng tại Vinmec thành các bước tuần tự rõ ràng, định vị chính xác điểm nghẽn (Bottleneck) tại khâu tra cứu tương tác đa thuốc và các điểm bàn giao thông tin (Handoff) giữa Bác sĩ – EMR – Dược sĩ lâm sàng.
- **Tư vấn kiến trúc phù hợp (AI-Fit):** Phân tích và định hướng lựa chọn giải pháp **LLM Feature kết hợp Graph Embedding (Node2Vec)** thay vì lạm dụng Autonomous Agent tự trị, giúp đảm bảo tính an toàn và khả năng kiểm soát trong môi trường y tế nghiêm ngặt.
- **Hỗ trợ gỡ lỗi kỹ thuật:** Hỗ trợ kiểm tra danh sách model khả dụng từ tài khoản API, xử lý lỗi nghẽn tải mạng `503 UNAVAILABLE` của mô hình thử nghiệm và cấu hình chuẩn xác biến môi trường cho SDK `google-genai`.

---

## 2. Những sai lệch, ảo giác (Hallucination) và hạn chế của AI

Trong quá trình đồng hành, AI nhiều lần đưa ra phản hồi chưa sát với thực tế hoặc gặp lỗi logic cần sự can thiệp của con người:

1. **Đề xuất bài toán mang tính lý thuyết chung chung (Lack of Domain Specificity):**
   - Khi được yêu cầu tìm bài toán "Pain từ người khác", ban đầu AI đưa ra các bài toán chung chung như "khách phàn nàn vì chờ đợi", "bác sĩ mệt mỏi vì ghi chép". Những điểm này không tạo ra xung đột nghiệp vụ rõ ràng.
   - *Thực tế:* Điểm đau lớn nhất trong vận hành y tế tại bệnh viện quốc tế là việc **Dược sĩ phát hiện xung đột thuốc muộn, phải gọi điện thoại ngắt ngang ca khám của Bác sĩ để yêu cầu sửa đơn**, gây ức chế tâm lý cho cả hai bên và kéo dài thời gian chờ đợi của bệnh nhân tại quầy thuốc.

2. **Ảo giác về quyền hạn tự trị trong y tế (Over-Automation Bias):**
   - Ở giai đoạn đầu đề xuất giải pháp cho Vinmec, AI có xu hướng tự động hóa hoàn toàn quy trình: gợi ý để AI tự động chỉnh sửa liều lượng và tự lưu đơn thuốc vào database EMR.
   - *Sai lệch:* Đây là lỗi vi phạm nghiêm trọng nguyên tắc an toàn lâm sàng. AI không thể thay thế trách nhiệm pháp lý của bác sĩ. Tôi phải bác bỏ đề xuất này và tái khẳng định ranh giới bắt buộc: AI chỉ đóng vai trò phân tích cảnh báo, 100% quyết định kê đơn phải do Bác sĩ phê duyệt (Human-in-the-loop).

3. **Lựa chọn mô hình không khả dụng trong thực tế lập trình:**
   - Khi cấu hình script prototype, việc chỉ định model theo khuyến nghị ban đầu gặp mã lỗi `503 UNAVAILABLE` do cụm server của model đó đang quá tải đột biến. Tôi đã chủ động viết script quét toàn bộ `client.models.list()` để xác định chính xác các phiên bản Flash đang hoạt động ổn định nhằm duy trì pipeline kiểm thử liên tục.

---

## 3. Quá trình tinh chỉnh Prompt và Thiết lập ranh giới an toàn (Prompt Refinement & Boundary Control)

Để khắc phục các điểm yếu trên và đạt được kết quả chuẩn xác cho bài lab, tôi đã thực hiện các bước tinh chỉnh cụ thể:

- **Bổ sung Persona và bối cảnh vận hành khắt khe:**
  - *Thay vì prompt ngắn:* "Gợi ý cách AI giúp bác sĩ kê đơn thuốc",
  - *Tôi tinh chỉnh thành:* "Đóng vai trò là Kỹ sư AI tại Vin Smart Future, phối hợp với Dược sĩ lâm sàng Vinmec. Quy trình kê đơn hiện tại đang đứt gãy do tra cứu tương tác thuốc thủ công. Thiết kế giải pháp sử dụng biểu diễn đồ thị tri thức (Knowledge Graph) kết hợp LLM để phát hiện xung đột hoạt chất và dị ứng, giữ nguyên nguyên tắc Bác sĩ là người xác nhận cuối cùng."

- **Thiết lập ranh giới an toàn vận hành (Operational Boundaries) trong Code Prototype:**
  - Nhận thấy rủi ro người dùng hoặc hệ thống bên ngoài ép LLM thực thi hành động vượt thẩm quyền, tôi đã lập trình các quy tắc cứng (Hard Constraints) trong System Prompt:
    1. **Quy tắc tiền tố bắt buộc `[DRAFT_ONLY]`:** Toàn bộ nội dung trả về bắt buộc phải gắn thẻ bản thảo để chặn việc tự động kích hoạt gửi tin/lưu đơn.
    2. **Quy tắc chặn rủi ro nguy cấp (Critical Boundary):** Đối với các trường hợp vượt ngưỡng an toàn (như pin xe dưới 5% ở bài toán Xanh SM, hoặc tiền sử sốc phản vệ ở bài toán Vinmec), AI bị cấm tuyệt đối việc đưa ra chỉ dẫn thông thường mà phải lập tức chuyển sang chế độ kích hoạt cứu hộ/chặn y lệnh khẩn cấp dạng JSON có cấu trúc.
  - Kết quả kiểm thử thực nghiệm với các prompt mang tính "tấn công ép vượt quyền" (Adversarial Prompts) cho thấy mô hình đã tuân thủ nghiêm ngặt các ranh giới đề ra, không bị bẻ cong bởi áp lực từ câu lệnh đầu vào của người dùng.

---

## 4. Bài học rút ra (Takeaway)

- **AI là bộ khuếch đại tư duy, không phải người ra quyết định thay:** Nếu đặt câu hỏi lỏng lẻo, AI sẽ trả về các câu trả lời sáo rỗng. Giá trị của một kỹ sư AI (AI Product Engineer) nằm ở khả năng thấu hiểu sâu sắc quy trình nghiệp vụ thực địa (Domain Understanding) để đặt ra các ràng buộc chuẩn xác.
- **Ranh giới an toàn quan trọng hơn sự thông minh:** Trong các bài toán vận hành trọng yếu (y tế, giao thông, an toàn năng lượng), khả năng "từ chối an toàn" (Graceful Refusal / Boundary Enforcement) của mô hình quan trọng hơn việc cố gắng tạo ra câu trả lời tự do nhưng tiềm ẩn rủi ro sai lệch.