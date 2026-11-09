# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | **Vinmec** | **AI-upgrade** | Gợi ý phối hợp đơn thuốc tối ưu và cảnh báo sớm xung đột hoạt chất, dị ứng bằng; hệ thống giải thích nguy cơ tương tác đa thuốc và bác sĩ luôn là người phê duyệt cuối cùng. |
| 2 | **Vinmec** | **Pain từ người khác** | Dược sĩ phát hiện tương tác thuốc muộn phải gọi điện thoại ngắt ngang ca khám của bác sĩ để yêu cầu sửa đơn; việc này gây ức chế cho cả hai bên và khiến bệnh nhân tại quầy thuốc phải chờ đợi kéo dài 30–45 phút. |
| 3 | **VinFast** | **Tốn thời gian** | Kỹ thuật viên xưởng dịch vụ mất 20–30 phút đọc telemetry logs kết hợp tra cứu sổ tay kỹ thuật PDF để xác định nguyên nhân gốc từ các mã lỗi viễn thông phức tạp trên xe điện. |
| 4 | **Xanh SM** | **Lặp lại** | Nhân viên CSKH phải rà soát, đọc và gán nhãn thủ công hàng nghìn đánh giá 1–3 sao mỗi ngày (mùi xe, thái độ tài xế, app lag, điều hòa) để phân loại nguyên nhân gốc và chuyển giao cho các đội vận hành liên quan. |
| 5 | **Vinhomes** | **Pain từ người khác** | Cư dân bức xúc vì gửi phản ánh tiếng ồn hoặc hư hỏng tiện ích qua ứng dụng chỉ nhận lại phản hồi tự động rập khuôn; Ban Quản lý chậm trễ cử an ninh xuống hiện trường xử lý dẫn đến mâu thuẫn trực tiếp giữa các hộ dân. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Hỗ trợ bác sĩ gợi ý đơn thuốc tối ưu,     │
│ cảnh báo sớm xung đột hoạt chất và dị ứng qua Graph-AI.     │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ điều trị, Dược sĩ lâm sàng.     │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Đọc tiền sử dị ứng & bệnh án cũ                        │
│   ──> 2. Chọn thuốc & tra cứu tương tác đa hoạt chất thủ công│
│   ──> 3. Kê đơn trên hệ thống EMR                           │
│   ──> 4. Chờ dược sĩ duyệt (gọi điện sửa nếu có xung đột)   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 4 (⏱ 12 phút/ca)   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3: AI dùng   │
│ Knowledge Graph + LLM gợi ý danh mục và gắn cờ cảnh báo.    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian kê đơn │
│ từ 15 min ──> under 4 min; giảm 80% cuộc gọi sửa đơn thuốc. │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Phân tích dữ liệu viễn thông và sổ tay kỹ │
│ thuật để tự động chẩn đoán nguyên nhân gốc mã lỗi xe điện.  │
│ Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Kỹ thuật viên xưởng dịch vụ VinFast.   │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Cắm máy quét đọc mã lỗi DTC từ xe điện                 │
│   ──> 2. Tra cứu thủ công Service Manual PDF & Telemetry log│
│   ──> 3. Khoanh vùng linh kiện nghi hỏng                    │
│   ──> 4. Lập biên bản đề xuất thay thế/sửa chữa             │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (⏱ 25 phút/lượt)     │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3: RAG + LLM │
│ trích xuất tài liệu kỹ thuật, đối chiếu log và tóm tắt lỗi. │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian chẩn   │
│ đoán mã lỗi từ 30 min ──> under 6 min; độ chính xác ≥ 90%.  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Tự động phân loại, trích xuất nguyên nhân │
│ gốc từ hàng nghìn đánh giá 1-3 sao của hành khách Xanh SM.  │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên CSKH & Quản lý vận hành GSM. │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Tải báo cáo đánh giá 1-3 sao từ ứng dụng hàng ngày     │
│   ──> 2. Đọc thủ công từng phản hồi phi cấu trúc của khách  │
│   ──> 3. Gắn tag phân loại lỗi (xe hôi, tài xế gắt, app lag)│
│   ──> 4. Chuyển vé cho đội Vận hành/Kỹ thuật tương ứng      │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 3-4 giờ/ngày) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3: LLM đọc   │
│ hiểu văn bản, trích xuất thực thể và gán nhãn phân loại.    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Phân loại tự động 95% │
│ phản hồi dưới 5 giây; giảm 80% thời gian xử lý thủ công.    │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*
