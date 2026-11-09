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
|---|----------------------------------|------|---------------------|
| 1 |Vinhomes |Lặp lại & Tốn thời gian |Phân loại và điều phối (routing) thủ công hàng ngàn yêu cầu/khiếu nại của cư dân từ app đến các bộ phận BQL. |
| 2 |Vinhomes |Lặp lại & Stakeholder Pain |Bóc tách văn bản và phân loại lỗi thủ công từ các biên bản bàn giao căn hộ để gửi lệnh sửa chữa cho nhà thầu. |
| 3 |Vinhomes |AI có thể tốt hơn |Vận hành hệ thống điều hòa và chiếu sáng sảnh theo khung giờ cố định thay vì lượng người thực tế, gây lãng phí điện. |
| 4 |Vinhomes |Stakeholder Pain & Lặp lại |Kiểm duyệt giấy tờ và gọi điện xác nhận thủ công từng khách vãng lai/shipper tại sảnh, gây ùn ứ giờ cao điểm. |
| 5 |Vinhomes |Tốn thời gian & Stakeholder Pain |Đối soát hóa đơn tiện ích bằng mắt, chậm phát hiện bất thường về chỉ số điện/nước gây ra tranh chấp gay gắt với cư dân. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #___                                     │
│                                                             │
│ Bài toán (1 câu): ________________________________________  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________ │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. ___ ──> 2. ___ ──> 3. ___ ──> 4. ___                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? ___ (⏱ ___ phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? _____________________ │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Phân loại và điều phối tự động hàng ngàn  │
│ yêu cầu/khiếu nại của cư dân trên app đến đúng bộ phận xử lý│
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên CSKH Ban Quản Lý và Cư dân   │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Cư dân gửi ticket ──> 2. NV CSKH đọc text/ảnh ──>      │
│   3. Xác định phân loại & độ ưu tiên ──> 4. Assign bộ phận  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 3-5 phút/lượt)
│ AI có thể nhảy vào hỗ trợ ở bước nào? Phân tích nội dung (NL│
│ P) ở bước 2 để tự động dán nhãn (tagging) và routing ở bước 3
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   "Giảm thời gian phân loại từ 5 phút ──> dưới 10 giây/lượt"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Bóc tách, chuẩn hóa lỗi từ biên bản bàn   │
│ giao nhà và tự động tạo lệnh sửa chữa cho đúng nhà thầu.    │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Thư ký dự án, Kỹ sư giám sát & Chủ nhà │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Ghi nhận lỗi thô ──> 2. Thư ký đọc lại biên bản ──>    │
│   3. Dịch sang từ ngữ kỹ thuật ──> 4. Map với mã nhà thầu   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (⏱ 45 phút/lượt)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Trích xuất thông tin, │
│ dịch từ ngôn ngữ nói sang chuẩn kỹ thuật và phân loại thầu. │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   "Giảm thời gian xử lý biên bản 45 phút ──> under 3 phút"  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Tự động hóa quy trình xác minh thông tin  │
│ và gọi điện xin phép cư dân cho khách vãng lai/shipper.     │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Bảo vệ sảnh, Shipper và Cư dân         │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách báo lễ tân ──> 2. BV kiểm tra giấy tờ ──>        │
│   3. BV chép sổ sách ──> 4. Gọi điện Intercom cho cư dân    │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (⏱ 3 phút/lượt) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? AI đọc OCR giấy tờ để │
│ thay bước 3, Voice Agent/Auto-notification thay bước 4.     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   "Giảm thời gian ùn ứ tại sảnh từ 3 phút ──> under 30 giây"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘