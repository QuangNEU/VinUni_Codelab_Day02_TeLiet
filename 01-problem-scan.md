# 01-problem-scan.md — Problem Scan & Quick Assessments (Vin Smart Future)

> **Dự án:** AI Product Scoping — Vin Smart Future (Vingroup)  
> **Người thực hiện:** AI Product Engineer  
> **Mục tiêu tài liệu:** Quét tìm các bài toán/bottleneck vận hành thực tế tại các công ty thành viên Vingroup, áp dụng 4 Lenses để đánh giá và hoàn thiện 3 Thẻ bài toán nhanh (Quick Problem Cards) cho các bài toán tiềm năng nhất trước khi bước vào giai đoạn Phân tích chuyên sâu (Deep-Dive).

---

## 🏛️ Bối cảnh: Vin Smart Future & Sứ mệnh Tối ưu hóa Vận hành Vingroup

Với vai trò là Kỹ sư Sản phẩm AI (**AI Product Engineer**) tại **Vin Smart Future** — đơn vị công nghệ nòng cốt chịu trách nhiệm nghiên cứu, chuyển đổi số và triển khai các giải pháp AI trên toàn hệ sinh thái Vingroup, chúng tôi tiến hành khảo sát thực địa và rà soát các luồng vận hành tại các đơn vị thành viên: **Vinhomes**, **Xanh SM (GSM)**, **VinFast**, **Vinmec**, và **VinUni**.

Mục tiêu cốt lõi là phát hiện những điểm nghẽn (bottlenecks) nơi con người đang phải xử lý thủ công lặp đi lặp lại, tốn thời gian hoặc gây ức chế cho các bên liên quan, từ đó xác định xem công nghệ AI (Rule-based, LLM Feature hay Agentic Workflow) có thể mang lại bước nhảy vọt về hiệu suất và trải nghiệm khách hàng hay không.

---

# 🔍 Phase 1 — SCAN: Bảng Quét Tìm Cơ Hội AI (5 Bài Toán Vingroup)

Sử dụng **4 Lenses** tiêu chuẩn của Vin Smart Future:
1. 🔁 **Lặp lại (Repetitive):** Tác vụ diễn ra tần suất cao hằng ngày, quy trình tương tự nhau.
2. ⏱️ **Tốn thời gian (Time-consuming):** Tác vụ tốn nhiều giờ làm việc thủ công của nhân sự chuyên môn.
3. ⚡ **AI có thể tốt hơn (AI-upgrade):** Dịch vụ hiện tại phản hồi chậm, rập khuôn, thiếu cá nhân hóa.
4. 💢 **Pain từ người khác (Stakeholder Pain):** Điểm nghẽn gây bức xúc lớn cho khách hàng, cư dân, đối tác hoặc nhân viên tuyến đầu.

### 📝 Bảng quét cơ hội vận hành:

| # | Đơn vị thành viên (Subsidiary) | Tên bài toán / Nghiệp vụ | Lens chính | Mô tả ngắn bài toán & Điểm nghẽn thực tế |
|:---:|:---|:---|:---:|:---|
| **1** | **Vinhomes** (Vận hành & Quỹ căn) | **Nền tảng AI Trợ lý Tìm kiếm & Đề xuất Căn hộ Thông minh** *(Smart Living Matchmaker)* | ⚡ AI-upgrade<br>⏱️ Tốn thời gian | Hiện tại khách tìm thuê/mua căn hộ Vinhomes phải tự lướt hàng chục hội nhóm MXH, tin đăng BĐS trôi nổi, môi giới kê giá. Thiếu nền tảng tập trung có AI hiểu sâu nhu cầu: phân tích vị trí bản đồ (gần trường cấp 3 cho con, gần bệnh viện, cơ quan), đọc hiểu cơ cấu gia đình để tư vấn số phòng ngủ tối ưu, dự báo thời hạn định cư và chủ động cảnh báo các căn hộ sắp đáo hạn hợp đồng thuê. |
| **2** | **Vinhomes** (App Resident & BQL) | **Phân loại, Điều hướng Phản ánh Cư dân & Phát hiện Sự cố Cụm Tòa nhà** *(Smart Ticket Routing & Cluster Anomaly)* | 🔁 Lặp lại<br>💢 Stakeholder Pain | Hàng ngàn phản ánh (mất nước, hỏng đèn, ồn ào) gửi qua App Vinhomes Resident cần nhân viên đọc và phân loại thủ công về từng BQL tòa nhà. Điểm nghẽn nghiêm trọng: BQL không biết đó là sự cố riêng lẻ của 1 phòng hay sự cố hệ thống của cả tòa/trục tầng (vd: hỏng bơm tăng áp, nhảy aptomat tổng), dẫn đến xử lý rời rạc, quá tải ticket và chậm trễ sửa chữa diện rộng. |
| **3** | **Xanh SM** (GSM - Vận hành Taxi) | **Thẩm định Tính Công tâm Đánh giá Thấp (1-Star Review) & Cảnh báo Sớm Tài xế** *(Fair Review Audit & Proactive Coaching)* | 💢 Stakeholder Pain<br>⏱️ Tốn thời gian | Tài xế bức xúc vì bị phạt oan từ các đánh giá 1-3 sao vô lý (khách giận vì kẹt xe, bắt tài xế vượt đèn đỏ/chở quá số người nhưng tài xế từ chối). Đội QA mất nhiều ngày để xác minh thủ công telemetry chuyến đi (GPS, vận tốc, lộ trình, chat). AI thẩm định tính công tâm để bảo vệ tài xế, đồng thời trích xuất các pattern lỗi lặp lại để nhắc nhở phòng ngừa cho các tài xế khác. |
| **4** | **VinUni** (CECS - Đào tạo CNTT) | **Hệ thống Tự động hóa Chấm điểm & Phản hồi Sư phạm Bài Lab Lập trình** *(Pedagogical Autograder & Feedback Assistant)* | 🔁 Lặp lại<br>⏱️ Tốn thời gian | Trợ giảng (TA) và Giảng viên quá tải khi chấm hàng trăm bài thực hành code mỗi tuần. Các autograder truyền thống chỉ dừng lại ở Pass/Fail unit test, không giải thích được lỗi tư duy logic hay phong cách code (code smells). AI tự động phân tích cú pháp, thuật toán và soạn thảo phản hồi mang tính sư phạm gợi mở, giúp sinh viên tự sửa lỗi mà không làm hộ. |
| **5** | **Vinmec** (Chăm sóc Khách hàng & Lâm sàng) | **Trợ lý AI Phân loại Triệu chứng & Điều phối Lịch Hẹn Khám Ban đầu** *(Clinical Symptom Triage & Appointment Router)* | ⚡ AI-upgrade<br>💢 Stakeholder Pain | Khách hàng mô tả triệu chứng tự nhiên qua tổng đài/chatbot (vd: đau tức ngực khi gắng sức) thường bị đặt nhầm giữa chuyên khoa Tim mạch và Hô hấp hoặc Cơ xương khớp. Bệnh nhân phải khám nhiều lần, trễ "thời gian vàng". AI đóng vai trò sơ lược bệnh sử ban đầu, gợi ý chuyên khoa chính xác và cảnh báo các dấu hiệu báo động (Red Flags) chuyển cấp cứu. |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Đánh Giá Nhanh Top 3)

Trong 5 bài toán trên, **3 bài toán tiềm năng nhất** mang lại giá trị vận hành trực tiếp, tác động quy mô lớn và khả thi về mặt kỹ thuật cho hệ sinh thái Vingroup là:
- **Card #1 (Vinhomes):** Nền tảng AI Trợ lý Tìm kiếm & Đề xuất Căn hộ Thông minh.
- **Card #2 (Vinhomes):** Phân loại, Điều hướng Phản ánh Cư dân & Phát hiện Sự cố Cụm Tòa nhà.
- **Card #3 (Xanh SM):** Thẩm định Tính Công tâm Đánh giá Thấp & Cảnh báo Phòng ngừa Tài xế.

---

## 📇 QUICK PROBLEM CARD #1: Vinhomes — Nền tảng AI Trợ lý Tìm kiếm & Đề xuất Căn hộ Thông minh

```text
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                                                   │
│                                                                                         │
│ Bài toán (1 câu): Xây dựng nền tảng web/app tích hợp AI Trợ lý tổng hợp quỹ căn         │
│ Vinhomes, phân tích nhu cầu cá nhân & bản đồ (trường học, bệnh viện) để tư vấn căn hộ   │
│ phù hợp và chủ động cảnh báo căn hộ sắp hết hạn thuê.                                   │
│                                                                                         │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  [ ] Vinmec  [ ] Khác        │
│                                                                                         │
│ Ai đang đau (Actor)? Khách hàng tìm thuê/mua nhà (đặc biệt gia đình có con nhỏ/người    │
│ già) bị quá tải thông tin ảo; Đội ngũ Quản lý Quỹ căn / Vinhomes Market chậm khớp lệnh. │
│                                                                                         │
│ Workflow thủ công hiện tại (5 bước):                                                    │
│   1. Khách lên MXH/Group Facebook/Zalo tìm kiếm bài đăng cho thuê/bán tự phát.          │
│   ──> 2. Mở Google Maps đo thủ công khoảng cách tới trường học, bệnh viện, chỗ làm.     │
│   ──> 3. Tự ước tính số phòng ngủ dựa theo ngân sách và số lượng thành viên gia đình.   │
│   ──> 4. Nhắn tin hỏi hàng loạt môi giới/chủ nhà xem căn còn trống không, khi nào hết HĐ│
│   ──> 5. Đi xem thực tế nhiều lần, thông tin sai lệch so với quảng cáo, chốt thuê chậm. │
│                                                                                         │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2, 3 và 4 (⏱ Mất từ 7 - 14 ngày tìm kiếm/lượt).   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2, 3, 4:                                     │
│   - Tiếp nhận input ngôn ngữ tự nhiên về thành viên, độ tuổi, trường học/nơi làm việc.  │
│   - Tự động gọi Google Maps API tính toán bán kính, lưu lượng giao thông thực tế.       │
│   - Tư vấn số phòng ngủ & layout tối ưu; tự động lọc quỹ căn trống và sắp hết hạn HĐ.   │
│                                                                                         │
│ Đo thành công bằng gì (Metric có số)?                                                   │
│   - Rút ngắn thời gian từ lúc tìm kiếm đến lúc chọn được căn từ 14 ngày ──> dưới 48 giờ.│
│   - Tỉ lệ gợi ý chính xác theo tiêu chí gia đình & tiện ích đạt ≥ 92%.                  │
│   - Tỷ lệ lấp đầy quỹ căn tăng 20%, giảm thời gian căn hộ để trống từ 30 ngày ──> 10 ngày│
│                                                                                         │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent (LLM + Tools: Maps/DB Query)│
└─────────────────────────────────────────────────────────────────────────────────────────┘
```

### 📋 Bảng Phân Tích Chuyên Sâu Card #1:
* **Khách hàng mục tiêu & Hành vi (User Persona):**
  * Gia đình trẻ hoặc gia đình đa thế hệ chuyển về khu đô thị Vinhomes (như Ocean Park, Smart City, Grand Park). Khách có con chuẩn bị vào cấp 3 (cần gần trường THPT công lập/chuyên hoặc Vinschool Gateway), có người cao tuổi (cần gần Vinmec hoặc công viên đi bộ).
* **Nghiệp vụ AI can thiệp chi tiết:**
  1. *Smart Profiling:* Phân tích hồ sơ gia đình (VD: "Gia đình tôi gồm 2 vợ chồng, 1 con học lớp 10, 1 bé 3 tuổi và bà nội lên chăm cháu") ➔ AI tự động tư vấn mô hình tối thiểu **2PN+1 hoặc 3PN** để đảm bảo không gian học tập cho con cấp 3 và phòng yên tĩnh cho người lớn tuổi, tránh việc khách chọn căn 2PN thông thường gây xung đột sinh hoạt.
  2. *Spatial Context Search:* Người dùng ghim vị trí hoặc nhập từ khóa "Trường cấp 3 Chu Văn An", "Trường THPT Chuyên Hà Nội - Amsterdam", "Bệnh viện Đa khoa Quốc tế Vinmec" ➔ AI kết nối API Google Maps tính toán thời gian di chuyển bằng xe bus điện VinBus / xe máy điện Xanh SM trong giờ cao điểm sáng để gợi ý phân khu/tòa nhà có tuyến kết nối thuận tiện nhất.
  3. *Lease Expiry Notification (Dự báo quỹ căn sắp trống):* Người dùng đăng ký "Thời gian định cư dự kiến: Tháng 8/2026" ➔ Hệ thống rà soát CSDL hợp đồng thuê, phát hiện các căn hộ đẹp sắp hết hạn vào tháng 6-7/2026 mà chủ nhà có nhu cầu cho thuê tiếp để gửi thông báo ưu tiên đặt cọc sớm.
* **Operational Boundary (Ranh giới an toàn):**
  * AI chỉ đóng vai trò **Tư vấn và Đề xuất thông tin minh bạch**; AI tuyệt đối **KHÔNG** tự ý thực hiện giao dịch tài chính, không tự ký kết hợp đồng đặt cọc hoặc hứa hẹn mức giá cam kết khi chưa có sự xác nhận của Chủ nhà / Ban Quản lý Quỹ căn Vinhomes (Bắt buộc Human-in-the-loop).

---

## 📇 QUICK PROBLEM CARD #2: Vinhomes — Phân loại & Điều hướng Phản ánh Cư dân, Phát hiện Sự cố Cụm Tòa nhà

```text
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                                                   │
│                                                                                         │
│ Bài toán (1 câu): Phân loại và điều hướng tự động phản ánh của cư dân qua App Vinhomes   │
│ Resident đến đúng BQL từng tòa nhà, đồng thời phân tích tương quan thời gian thực để    │
│ phát hiện xem là sự cố đơn lẻ của 1 phòng hay sự cố kỹ thuật chung của cả tòa nhà.     │
│                                                                                         │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  [ ] Vinmec  [ ] Khác        │
│                                                                                         │
│ Ai đang đau (Actor)? Cư dân Vinhomes (chờ phản hồi lâu, bực bội); Ban Quản lý Tòa nhà    │
│ (BQL) & Đội Kỹ thuật bảo trì (quá tải hàng trăm ticket rời rạc, sót sự cố diện rộng).   │
│                                                                                         │
│ Workflow thủ công hiện tại (5 bước):                                                    │
│   1. Cư dân gửi ticket phản ánh qua App Vinhomes Resident (text tự do + ảnh đính kèm).   │
│   ──> 2. Nhân viên CSKH trung tâm đọc nội dung, đoán xem thuộc tòa nhà & phòng ban nào. │
│   ──> 3. CSKH gán vé thủ công cho Trưởng BQL tòa nhà liên quan trên hệ thống nội bộ.    │
│   ──> 4. Kỹ thuật viên tòa nhà liên hệ căn hộ hẹn giờ lên kiểm tra từng căn một.        │
│   ──> 5. Khi có 5-10 căn cùng tầng báo mất nước, kỹ thuật mới biết là sự cố vỡ ống chung│
│                                                                                         │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 và Bước 5 (⏱ Mất 30-60 phút để route; mất 2-4 giờ│
│ để nhận ra sự cố hệ thống chung của cả tòa nhà).                                        │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2, 3 và 5:                                   │
│   - LLM đọc hiểu ngôn ngữ tự nhiên, trích xuất mã lỗi, phân loại chuyên môn (Kỹ thuật, │
│     An ninh, Vệ sinh, Cây xanh) và route tức thì (< 5 giây) về BQL tòa nhà tương ứng.   │
│   - Cluster Detection Engine: Quét các ticket trong vòng 30 phút từ cùng 1 tòa/trục tầng│
│     để gom nhóm sự cố chung (vd: sụt áp điện, mất nước, kẹt thang máy), cảnh báo khẩn.   │
│                                                                                         │
│ Đo thành công bằng gì (Metric có số)?                                                   │
│   - Giảm thời gian tiếp nhận & định tuyến vé từ 45 phút ──> dưới 10 giây (giảm 99%).     │
│   - Độ chính xác phân loại bộ phận chuyên trách đạt ≥ 96%.                               │
│   - Phát hiện sự cố diện rộng toàn tòa trong vòng 10 phút đầu tiên, giảm 80% số lượng    │
│     ticket gửi trùng lặp nhờ tự động gửi thông báo Broadcast cho cư dân cùng tòa.        │
│                                                                                         │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM Feature (kết hợp Rule Clustering)      │
└─────────────────────────────────────────────────────────────────────────────────────────┘
```

### 📋 Bảng Phân Tích Chuyên Sâu Card #2:
* **Bản chất vấn đề vận hành (The Operational Bottleneck):**
  * Tại các đại đô thị Vinhomes với quy mô hàng chục ngàn căn hộ, trung bình mỗi ngày phát sinh từ 500 - 1.500 phản ánh cư dân. Hiện tượng "nghẽn cổ chai" xảy ra khi một sự cố hạ tầng kỹ thuật chung (ví dụ: máy bơm tăng áp của Tòa S2.01 bị ngắt mạch):
    * 30 cư dân thuộc các tầng 15 đến 25 cùng lúc nộp ticket: *"Phòng 1805 mất nước hoàn toàn"*, *"Vòi sen nhà 2012 không chảy"*, *"Sao tự nhiên nước yếu thế BQL"*.
    * Nhân viên CSKH đọc từng ticket và gán rời rạc 30 công việc cho thợ kỹ thuật lên gõ cửa từng nhà để kiểm tra van khóa nước trong căn hộ!
    * Hậu quả: Lãng phí hàng chục giờ công kỹ thuật, cư dân bức xúc vì chờ đợi, trong khi phòng kỹ thuật bơm trung tâm lại không được xử lý ngay lập tức.
* **Giải pháp AI nâng cấp:**
  1. *Text Understanding & Entity Extraction:* LLM nhận diện nội dung phản ánh, tự động gắn nhãn thẻ: `Category: Plumbing`, `Urgency: High`, `Location: S2.01 - Unit 1805`.
  2. *Cross-Unit Incident Correlation (Phân tích Tương quan Cụm):* Thuật toán phát hiện sự kiện bất thường (Anomaly Clustering) quét cửa sổ trượt thời gian (vd: 30 phút gần nhất). Nếu $\ge 3$ căn hộ trong cùng một trục kỹ thuật hoặc cùng tòa nhà phản ánh cùng một loại sự cố (mất nước, chập điện, kẹt thang máy số 3, tiếng ồn thi công), hệ thống tự động:
     * Gom cụm thành **"Parent Ticket — Sự cố diện rộng Tòa S2.01"**.
     * Kích hoạt còi báo động ưu tiên cấp P1 cho Đội trưởng Kỹ thuật tòa nhà.
     * Tự động gửi thông báo đẩy (Push Notification) trên App Resident cho các căn hộ còn lại trong tòa: *"BQL đã ghi nhận hiện tượng gián đoạn cấp nước tại Tòa S2.01 và đang tiến hành xử lý tại phòng kỹ thuật. Dự kiến hoàn tất trong 45 phút. Quý cư dân không cần gửi thêm phản ánh."* ➔ Dập tắt ngay làn sóng spam ticket.
* **Operational Boundary (Ranh giới an toàn):**
  * AI **KHÔNG** tự ý đóng vé (close ticket) khi chưa có sự xác nhận hoàn tất từ Kỹ thuật viên thực địa và đánh giá hài lòng từ cư dân; đối với các phản ánh có dấu hiệu khẩn cấp về an toàn sinh mạng (cháy nổ, rò rỉ khí gas, kẹt thang có người bên trong), AI phải chuyển ngay lập tức sang kênh Hotline Báo động đỏ của Đội An ninh cơ động.

---

## 📇 QUICK PROBLEM CARD #3: Xanh SM — Thẩm định Tính Công tâm Đánh giá Thấp & Cảnh báo Phòng ngừa Tài xế

```text
┌─────────────────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                                                   │
│                                                                                         │
│ Bài toán (1 câu): Hệ thống AI tự động phân tích các đánh giá thấp (1-3 sao) của khách    │
│ Xanh SM, đối chiếu dữ liệu telemetry chuyến đi để thẩm định tính công tâm (tránh phạt oan│
│ tài xế), đồng thời trích xuất pattern lỗi để phát thông báo cảnh báo phòng ngừa tài xế. │
│                                                                                         │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM (GSM)  [ ] Vinhomes  [ ] Vinmec  [ ] Khác   │
│                                                                                         │
│ Ai đang đau (Actor)? Tài xế Xanh SM (bị trừ sao, trừ thưởng oan, mất động lực); Đội ngũ │
│ QA / Kiểm soát Chất lượng GSM (quá tải hàng ngàn đơn khiếu nại phúc khảo mỗi tuần).      │
│                                                                                         │
│ Workflow thủ công hiện tại (5 bước):                                                    │
│   1. Khách hàng chấm 1-3 sao trên App Xanh SM kèm phản ánh (hoặc chỉ vote sao trống).   │
│   ──> 2. Hệ thống tự động ghi nhận điểm xấu, trừ điểm thưởng KPI/khoá app tài xế theo quy│
│   ──> 3. Tài xế bức xúc gửi đơn khiếu nại phúc khảo lên bộ phận Hỗ trợ Đối tác.         │
│   ──> 4. Nhân viên QA đọc log, mở bản đồ tua lại GPS, kiểm tra tốc độ, nghe ghi âm cước.│
│   ──> 5. QA đưa ra kết luận thủ công để hoàn tiền/gỡ phạt cho tài xế (mất 3 - 5 ngày).  │
│                                                                                         │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 và Bước 4 (⏱ Mất 48 - 72 giờ thẩm định 1 đơn).   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2, 4, 5:                                     │
│   - AI nhận diện đánh giá thấp, tự động cross-check dữ liệu chuyến đi: GPS di chuyển,   │
│     vận tốc xe, tình trạng ùn tắc giao thông thực tế, lịch sử đánh giá của khách hàng.  │
│   - Thẩm định tính công tâm: Phát hiện khách phàn nàn sai thực tế (vd: chê đi chậm do   │
│     tắc đường, đòi tài xế vượt đèn đỏ nhưng tài xế từ chối) ➔ Tự động tạm hoãn phạt.     │
│   - Trích xuất pattern lỗi phổ biến để gửi bài học cảnh báo ngắn cho các tài xế khác.   │
│                                                                                         │
│ Đo thành công bằng gì (Metric có số)?                                                   │
│   - Rút ngắn thời gian thẩm định đánh giá 1 sao từ 72 giờ ──> dưới 15 phút.             │
│   - Độ chính xác phát hiện phản ánh không công tâm đạt ≥ 90%.                           │
│   - Giảm 60% số lượng khiếu nại phúc khảo từ tài xế; Giảm 25% tỷ lệ lặp lại các lỗi phổ  │
│     biến nhờ các bản tin cảnh báo phòng ngừa chủ động gửi qua Driver App.                │
│                                                                                         │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM Feature (kết hợp Telemetry Engine)     │
└─────────────────────────────────────────────────────────────────────────────────────────┘
```

### 📋 Bảng Phân Tích Chuyên Sâu Card #3:
* **Tình huống thực tế gây ức chế tài xế (Real-world Edge Cases):**
  * *Trường hợp 1 (Khách phàn nàn vì tắc đường):* Khách đi từ Cầu Giấy về Hoàn Kiếm vào 18h00 thứ Sáu trời mưa to, đường ngập lụt. Khách cáu gắt và rate 1 sao: *"Tài xế đi quá lâu, cố tình đi chậm để câu giờ cước"*. Trên thực tế, xe điện Xanh SM tính cước trọn gói cố định (fixed price), tốc độ di chuyển trung bình toàn tuyến chỉ 12 km/h do ùn tắc nghiêm trọng được ghi nhận trên dữ liệu bản đồ. Tài xế bị phạt oan 500.000đ tiền thưởng tuần!
  * *Trường hợp 2 (Khách đòi vi phạm luật an toàn):* Khách đặt xe Xanh SM Taxi 4 chỗ nhưng đi 5 người lớn kèm 2 trẻ em, hoặc yêu cầu tài xế quay đầu trên cầu / đi vào đường cấm. Tài xế từ chối vì quy định an toàn của Bộ Giao thông và GSM. Khách cay cú chấm 1 sao: *"Tài xế thái độ lồi lõm, không tôn trọng khách hàng"*.
* **Cơ chế AI Thẩm Định Công Tâm (Fair Review Audit):**
  * **Thu thập dữ liệu đa chiều (Data Ingestion):** Text đánh giá của khách + Dữ liệu GPS/OBD của xe (vận tốc, gia tốc phanh, quãng đường thực tế vs quãng đường khuyến nghị) + Dữ liệu giao thông thời gian thực tại thời điểm cuốc xe + Đoạn chat trao đổi trên app.
  * **Phân tích đối sánh (Discrepancy Check):**
    * Nếu khách phàn nàn *"Tài xế phóng nhanh vượt ẩu, phanh gấp liên tục"* nhưng cảm biến G-force trên xe điện VinFast báo gia tốc ổn định, vận tốc trung bình không vượt quá tốc độ tối đa cho phép ➔ Gắn nhãn `Unverified Complaint / Low Credibility`.
    * Nếu khách phàn nàn *"Tài xế đi lòng vòng"* nhưng tỷ lệ sai lệch quãng đường thực tế so với lộ trình đề xuất của hệ thống điều vận $\le 5\%$ ➔ Kết luận: Lộ trình hoàn toàn tối ưu.
  * **Khuyến nghị tự động (Auto-Recommendation):** Đưa ra đề xuất: `[WAIVE_PENALTY]` (Miễn trừ phạt cho tài xế), kèm văn bản tóm tắt chứng cứ logic để nhân viên giám sát chỉ cần click phê duyệt trong 5 giây thay vì ngồi tra cứu 30 phút.
* **Cơ chế Cảnh báo Sớm & Đào tạo Phòng ngừa (Proactive Driver Coaching):**
  * AI không dừng lại ở việc gỡ phạt mà gom cụm các bài học kinh nghiệm:
    * *Ví dụ:* AI phát hiện vào các ngày mưa tại khu vực Kangnam/Keangnam, 70% đánh giá thấp đến từ việc khách chờ lâu tại điểm đón. AI kích hoạt thông báo tự động trên Driver App cho toàn bộ tài xế nhận cuốc tại khu vực này: *"Khu vực đón trả khách đang ùn ứ nghiêm trọng. Bác tài vui lòng bấm gọi hoặc gửi tin nhắn mẫu cho khách: 'Đường đang ùn tắc, em đang tiến vào sảnh đón, mong anh/chị thông cảm đợi em 5 phút nhé' để tránh bị đánh giá thấp!"*. Kết quả là sự thấu hiểu từ khách hàng tăng lên, giảm hẳn 1-star review.
* **Operational Boundary (Ranh giới an toàn):**
  * AI **KHÔNG ĐƯỢC PHÉP** tự động khóa vĩnh viễn tài khoản của tài xế hoặc tự ý cấm người dùng sử dụng dịch vụ; mọi quyết định kỷ luật nghiêm khắc hoặc khấu trừ tiền đều phải có chữ ký điện tử của Trưởng phòng Vận hành GSM. AI cũng không được lưu trữ thông tin nhạy cảm của khách hàng ngoài phạm vi cuốc xe.

---

# 🗳️ Quyết định Đánh giá & Định hướng Lựa chọn cho Phase 3 (DEEP-DIVE)

Dưới đây là ma trận so sánh nhanh 3 bài toán để lựa chọn ứng viên xuất sắc nhất đưa vào Báo cáo Phân tích Chuyên sâu (**02-deep-dive-report.md**):

| Tiêu chí đánh giá | Card #1: Vinhomes Tìm căn hộ | Card #2: Vinhomes Điều hướng sự cố tòa nhà | Card #3: Xanh SM Thẩm định đánh giá 1-sao |
|:---|:---:|:---:|:---:|
| **Tác động nghiệp vụ (Business Impact)** | Cao (Tăng doanh thu & lấp đầy quỹ căn) | Rất cao (Bảo vệ SLA đô thị, giảm chi phí vận hành) | Rất cao (Giữ chân tài xế, nâng cao chất lượng dịch vụ) |
| **Tính sẵn sàng của dữ liệu (Data Readiness)** | Trung bình (Cần tích hợp DB quỹ căn, GIS Maps) | Rất cao (Logs App Resident & dữ liệu BQL có sẵn) | Cực cao (Telemetry xe VinFast, GPS, logs chuyến đi có sẵn) |
| **Mức độ khả thi kỹ thuật (Feasibility)** | Cần tích hợp Agent + External Tool APIs | Rất khả thi (LLM NLU + Time-series Clustering) | Rất khả thi (LLM Analysis + Rule Guardrails) |
| **Rủi ro vận hành (Operational Risk)** | Thấp (Thông tin gợi ý, có HITL duyệt cọc) | Thấp - Trung bình (Cần bảo vệ kênh khẩn cấp) | Thấp (Có kiểm soát qua cơ chế phúc khảo và HITL) |
| **Thời gian triển khai Prototype (Time-to-Value)** | 3 - 4 tuần | 1 - 2 tuần | 1 - 2 tuần |

### 📌 Kết luận & Đề xuất lựa chọn:
Cả 3 bài toán đều sở hữu nền tảng nghiệp vụ cực kỳ vững chắc và giải quyết đúng nỗi đau nhức nhối của các công ty thành viên Vingroup. Trong đó:
- **Card #2 (Vinhomes)** và **Card #3 (Xanh SM)** là hai bài toán có sẵn nguồn dữ liệu telemetry/logs chuẩn mực nhất trong hệ sinh thái của Vin Smart Future.
- Nếu ưu tiên bài toán có tính liên kết phần cứng và dữ liệu vận hành thời gian thực lớn nhất của xe điện, **Card #3 (Xanh SM Thẩm định Đánh giá Thấp)** là lựa chọn vượt trội.
- Nếu ưu tiên bài toán có độ phủ dân sinh và tối ưu hóa quy trình dịch vụ đô thị quy mô lớn, **Card #2 (Vinhomes Phân loại phản ánh & Sự cố cụm)** hoặc **Card #1 (Vinhomes Trợ lý Quỹ căn)** là ứng viên lý tưởng.

---
*Tài liệu đã hoàn thành đầy đủ các tiêu chí của Phase 1 (SCAN 5 bài toán) và Phase 2 (QUICK-ASSESS 3 thẻ chi tiết) theo đúng quy chuẩn Vin Smart Future.*
