# BÁO CÁO PHÂN TÍCH SÂU: HỆ THỐNG VINFAST TECHNICAL VOICE-AGENT

## 3.2. Problem Statement (6-field) & Metrics

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Kỹ thuật viên (KTV) sửa chữa và bảo dưỡng tại các xưởng dịch vụ VinFast. |
| **2. Current Workflow** | Xe cắm máy chẩn đoán hiện mã lỗi lạ ──> KTV chui ra khỏi gầm xe, cởi găng tay ──> Mở máy tính tra cứu mã lỗi trên file Service Manual (hàng nghìn trang PDF) ──> Đọc hiểu cách xử lý ──> Quay lại xe thao tác. |
| **3. Bottleneck** | Bước tra cứu tài liệu (Context Switching). KTV đang làm việc chân tay (tay dính dầu mỡ, tư thế khó) phải chuyển sang thao tác thiết bị điện tử, gây đứt gãy mạch làm việc và tốn thời gian. |
| **4. Business Impact** | Tăng thời gian lưu chuồng (Turn-Around-Time) của xe. Giảm năng suất tiếp nhận xe của xưởng trong những ngày cao điểm. |
| **5. Success Metric** | - Giảm 20% tổng thời gian tra cứu và xử lý các ca lỗi phần mềm/điện tử phức tạp.<br>- Zero-touch: 100% truy vấn tài liệu trong lúc đang thao tác dưới gầm xe không cần dùng tay bấm máy tính. |
| **6. Operational Boundary** | - **ĐƯỢC PHÉP:** Trích xuất và đọc chính xác các bước kiểm tra từ tài liệu chính hãng (RAG).<br>- **CẤM TUYỆT ĐỐI:** AI không được tự ý chẩn đoán bệnh, không được tự khuyên KTV thay mới linh kiện đắt tiền nếu tài liệu chỉ ghi "kiểm tra", không bịa ra thông số dòng điện/điện áp (Hallucination).<br>- **BẮT BUỘC:** Chỉ trả lời dựa trên file PDF xưởng cung cấp, không search web ngoài. |

## 3.3. Future-State Flow & AI Fit
- **Mức AI Fit:** `[x] Agentic Loop` (AI có khả năng nghe giọng nói, search RAG database, và tổng hợp câu trả lời thành giọng nói).
- **Future-State Flow:**
  * 🔵 **AI Step:** AI lắng nghe voice prompt của KTV qua tai nghe open-ear (VD: "BMS_X72 xử lý sao?") -> Chuyển Speech-to-Text -> AI Query CSDL Manual -> Sinh câu trả lời Text -> Chuyển Text-to-Speech đọc lại vào tai KTV.
  * 🟢 **Human Step (HITL):** KTV nghe hướng dẫn từ AI, đối chiếu với tình trạng thực tế của xe trước khi vặn ốc hoặc đo điện.
  * ↩️ **Fallback:** Nếu AI trả lời "Không tìm thấy trong tài liệu" hoặc đưa ra thông số quá vô lý, KTV tuân thủ quy trình cũ: ra ngoài mở máy tính tự tra hoặc gọi Quản đốc xưởng hỗ trợ.

## Phase 5 — EVALUATE
### AI Readiness Checklist:
1. [x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test? *(Đã có các bộ file PDF Service Manual chuẩn của VinFast VF8/VF9).*
2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát? *(Có, KTV là thợ lành nghề, có khả năng nhận biết thông số phi lý để kích hoạt Fallback).*
3. [x] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ? *(Cực kỳ sẵn sàng vì thợ rất ghét việc đang làm phải đi rửa tay để bấm máy tính).*

### Quyết định của nhóm:
- [x] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp (chỉ test với bộ tài liệu lỗi Pin của một dòng xe cụ thể trước khi nhân rộng).