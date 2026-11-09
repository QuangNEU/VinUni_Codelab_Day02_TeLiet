# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

---

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
---

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
---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

---

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
---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
