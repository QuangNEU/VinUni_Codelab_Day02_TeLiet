# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Nhân viên CSKH / Ban Quản Lý,Kỹ thuật viên / An ninh / Vệ sinh, Cư dân |
| **2. Current Workflow** | Cư dân gửi ticket (kèm text/ảnh) qua App Vinhomes ──> Ticket đổ về hàng đợi (Queue) chung ──> Nhân viên CSKH mở đọc từng ticket ──> Phân tích nội dung để xác định loại lỗi & độ ưu tiên ──> Gán (assign) thủ công cho bộ phận/cá nhân phụ trách ──> Nhân viên đi xử lý ──> Đóng ticket. |
| **3. Bottleneck** | Bước Đọc, phân loại và gán ticket thủ công. Với 1.500 - 2.000 ticket/ngày ở một đại đô thị, nhân viên tốn 3-5 phút để đọc hiểu và xử lý một ticket. Khi quá tải, việc gán nhầm bộ phận (ví dụ: lỗi camera lại giao cho thợ điện nước) hoặc đánh giá sai độ ưu tiên (rò rỉ nước nghiêm trọng bị xếp sau việc xin đăng ký khách) thường xuyên xảy ra |
| **4. Business Impact** | Lãng phí chi phí vận hành (OPEX): Tốn khoảng 15-20 nhân sự/ngày chỉ để làm công việc phân loại văn bản. Sụt giảm CSAT & Trễ SLA: Độ trễ từ lúc báo cáo đến lúc có người tiếp nhận có thể lên tới 2-4 tiếng vào giờ cao điểm, khiến cư dân bức xúc, rủi ro hư hỏng tài sản tăng cao |
| **5. Success Metric** | Thời gian phân loại (Routing Time): Giảm từ 3-5 phút/ticket xuống dưới 10 giây/ticket (Real-time). Độ chính xác (Routing Accuracy): Tỷ lệ AI gán đúng bộ phận và đúng mức độ ưu tiên đạt > 90%.|
| **6. Operational Boundary** | ĐƯỢC PHÉP: AI được quyền đọc text, phân tích hình ảnh đính kèm, tự động dán nhãn (tagging) phân loại sự cố và đẩy thẳng lệnh công việc (Work Order) đến app của kỹ thuật viên phụ trách. TUYỆT ĐỐI KHÔNG: Tuyệt đối không tự động đóng ticket khi chưa có xác nhận nghiệm thu từ phía cư dân. Không được phép tự xử lý các từ khóa liên quan đến an toàn tính mạng, hỏa hoạn, bạo lực. ĐIỂM CẦN DUYỆT (Human-in-the-loop): Các ticket có nội dung quá ngắn không rõ nghĩa, hoặc hệ thống phát hiện cảm xúc (sentiment) của cư dân đang cực kỳ giận dữ, AI phải đưa vào một hàng đợi (Escalation Queue) ưu tiên để Quản lý CSKH trực tiếp đọc và gọi điện xoa dịu. |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [x] LLM Feature [ ] Agentic Loop.
* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.
[ CƯ DÂN ] ──(Gửi ticket Text/Ảnh qua App)──> [ HỆ THỐNG CRM VINHOMES ]
                                                       │
                                                       ▼
┌──────────────────────────────────────────────────────────────┐
│ 🔵 AI STEP: LLM MULTIMODAL ROUTER                            │
│  - Phân tích Text & Ảnh đính kèm.                            │
│  - Phân loại sự cố (Tagging) & Xác định Bộ phận phụ trách.   │
│  - Chấm điểm ưu tiên (P1-Khẩn cấp đến P4-Thường).            │
│  - Quét sắc thái (Sentiment): Bình thường vs. Giận dữ.       │
│  - Xuất ra điểm tự tin (Confidence Score).                   │
└──────────────────────────────┬───────────────────────────────┘
                               │
            ┌──────────────────┴──────────────────┐
            ▼                                     ▼
[ Khớp điều kiện Ngoại lệ ]            [ Điểm tự tin ≥ 80% & Hợp lệ ]
 (Score < 80%, hoặc có từ                 (Sự cố vận hành tiêu chuẩn)
  khóa báo cháy/bạo lực, 
  hoặc Sentiment = Cực độ)                        │
            │                                     │
            ▼                                     ▼
┌───────────────────────────┐          ┌───────────────────────────┐
│ ↩️ FALLBACK: ESCALATION   │          │ 🔵 AI STEP: AUTO-DISPATCH │
│ Hệ thống ngưng tự động,   │          │ LLM tự động chuyển đổi    │
│ chuyển ticket sang hàng   │          │ thành Work Order (Lệnh    │
│ đợi ưu tiên (Priority     │          │ việc) và gọi API đẩy      │
│ Queue).                   │          │ thẳng về App kỹ thuật.    │
└───────────┬───────────────┘          └──────────┬────────────────┘
            │                                     │
            ▼                                     ▼
┌───────────────────────────┐          ┌───────────────────────────┐
│ 🟢 HUMAN STEP (HITL)      │          │ [ NHÂN VIÊN THỰC ĐỊA ]    │
│ Quản lý CSKH trực tiếp đọc│          │ Kỹ thuật viên/Vệ sinh nhận│
│ ticket, gọi điện xoa dịu  │          │ Pop-up, tiếp nhận và đến  │
│ cư dân và gán việc tay.   │          │ hiện trường xử lý.        │
└───────────┬───────────────┘          └──────────┬────────────────┘
            │                                     │
            └──────────────────┬──────────────────┘
                               ▼
┌───────────────────────────┐
│ 🟢 HUMAN STEP (ĐÓNG TICKET)│
│ Cư dân bấm xác nhận hoàn  │
│ thành sự cố trên App.     │
└───────────────────────────┘

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [x] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[x] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *Viết lý giải chi tiết tại đây*
Dự án được cấp quyền GO (Bắt đầu ở scope hẹp - Pilot tại 1-2 khu đô thị lớn như Ocean Park trước) dựa trên 3 luận điểm:

1. Tính khả thi kỹ thuật (Technical Feasibility) đã được chứng minh: Thông qua bài test giới hạn (Boundary Stress-Testing) với Gemini 2.5 Flash, hệ thống LLM Multimodal đã chứng minh khả năng đọc hiểu song song cả văn bản tiếng Việt (sai chính tả, tiếng lóng) và hình ảnh hiện trường để xuất ra JSON chuẩn. Hệ thống hoàn toàn tuân thủ các ranh giới cấm (Emergency Rule, Sentiment Rule).

2. Hiệu quả kinh tế (ROI) rõ ràng: Chi phí gọi API LLM cho 2.000 ticket/ngày chỉ tốn vài USD, nhưng có thể tiết kiệm trực tiếp 15-20 nhân sự (headcount) đang phải ngồi làm tác vụ "chia việc" thủ công. Lợi ích gián tiếp là loại bỏ 100% rò rỉ SLA do kẹt ticket vào giờ cao điểm, ngăn chặn kịp thời các thiệt hại tài sản lớn (như tràn nước) nhờ tốc độ điều phối giảm từ 3-5 phút xuống dưới 10 giây.

3. Rủi ro vận hành được cô lập (Isolated Risk): Hệ thống không tự ý ra quyết định sửa chữa hay đóng ticket mà chỉ làm nhiệm vụ "Routing" (Điều phối) và lập Work Order. Các rủi ro như AI hiểu sai ý sẽ được hứng trọn bởi lớp lưới lọc confidence_score và đưa về luồng xử lý bằng mắt người (Human-in-the-loop), đảm bảo không tạo ra khủng hoảng dịch vụ khách hàng.