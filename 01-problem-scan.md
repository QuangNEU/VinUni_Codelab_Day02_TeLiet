# Phần 1: Bảng quét cơ hội (SCAN)

| # | Công ty thành viên | Lens (Góc nhìn) | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | **Xanh SM** | Lặp lại (Repetitive) | Nhân viên Onboarding tốn nhiều thời gian check bằng mắt ảnh chụp bằng lái, CCCD, đăng kiểm xe của tài xế mới xem có khớp thông tin hay bị hết hạn không. |
| 2 | **Vinhomes** | Tốn thời gian (Time-consuming) | Bảo vệ tòa nhà phải trực màn hình camera liên tục để phát hiện xe đỗ sai quy định (làn cứu hỏa) hoặc hành lý bỏ quên ở sảnh. Rất dễ sót lỗi do mỏi mắt. |
| 3 | **VinWonders** | AI có thể tốt hơn (AI-upgrade) | Khách mua vé lúng túng khi tự xếp lịch trình. Cần trợ lý AI tự sinh lịch trình cá nhân hóa (dựa trên tuổi trẻ em) và tự route khách né các khu đang ùn tắc theo thời gian thực. |
| 4 | **VinFast** | Lặp lại (Repetitive) | Khi xe gửi mã lỗi (DTC codes) về hệ thống, nhân viên xưởng dịch vụ phải tra bảng Excel thủ công để chuẩn bị linh kiện trước khi xe tới xưởng. |
| 5 | **VinFast** | Pain từ người khác (Stakeholder Pain) | **(Bài toán chọn làm Prototype)** Kỹ thuật viên (KTV) sửa xe đang chui gầm, tay dính dầu mỡ không thể dùng máy tính/điện thoại để tra cứu tài liệu sửa chữa (Service Manual) hàng ngàn trang khi gặp mã lỗi lạ. |

---

# Phần 2: 3 Quick Problem Cards (QUICK-ASSESS)

### QUICK PROBLEM CARD #1
- **Bài toán (1 câu):** Tự động trích xuất OCR và đối chiếu logic thông tin trên hồ sơ đăng ký tài xế mới của Xanh SM.
- **Công ty thành viên:** Xanh SM
- **Ai đang đau (Actor)?** Nhân viên vận hành (Onboarding Team).
- **Workflow thủ công hiện tại:** 
  1. Tài xế upload ảnh CCCD, bằng lái ──> 2. NV mở từng ảnh xem có mờ/nhòe không ──> 3. Gõ lại data vào hệ thống ──> 4. Đối chiếu ngày hết hạn ──> 5. Bấm Duyệt.
- **Bước nào tốn thời gian/lỗi nhất?** Bước 2, 3, 4 (⏱ 5 phút/hồ sơ).
- **AI nhảy vào hỗ trợ ở đâu?** Dùng Vision AI đọc chữ trên ảnh (OCR), tự fill vào form ERP và check rule logic (VD: Bằng lái phải còn hạn > 6 tháng).
- **Đo thành công bằng gì (Metric):** Giảm thời gian xử lý sơ bộ từ 5 phút ──> 30 giây/hồ sơ. Tự động pass 70% hồ sơ chuẩn.
- **Quick Architecture:** [x] LLM/Vision 

### QUICK PROBLEM CARD #2
- **Bài toán (1 câu):** Trợ lý AI sinh lịch trình vui chơi VinWonders cá nhân hóa, định tuyến động để giảm ùn tắc tại các phân khu.
- **Công ty thành viên:** VinWonders
- **Ai đang đau (Actor)?** Khách hàng (trải nghiệm kém do chờ lâu) & BQL (ùn tắc cục bộ).
- **Workflow thủ công hiện tại:** 
  1. Khách xem bản đồ ──> 2. Đi bộ tới khu vui chơi ──> 3. Thấy xếp hàng quá dài (30-45p) ──> 4. Chờ đợi mệt mỏi hoặc bỏ đi khu khác.
- **Bước nào tốn thời gian/lỗi nhất?** Bước 3.
- **AI nhảy vào hỗ trợ ở đâu?** Khách nhập request lên app. AI query API mật độ đám đông hiện tại, sinh lịch trình khuyên khách đi Thủy cung trước vì đang vắng, đẩy các game hot về cuối ngày.
- **Đo thành công bằng gì (Metric):** Giảm thời gian xếp hàng trung bình/khách từ 40p ──> dưới 20p.
- **Quick Architecture:** [x] LLM 

### QUICK PROBLEM CARD #3 (Ý tưởng Focus)
- **Bài toán (1 câu):** Voice-Agent tra cứu tài liệu kỹ thuật rảnh tay (hands-free) cho thợ bảo dưỡng tại xưởng VinFast.
- **Công ty thành viên:** VinFast
- **Ai đang đau (Actor)?** Kỹ thuật viên (KTV) sửa chữa.
- **Workflow thủ công hiện tại:** 
  1. KTV đọc máy báo lỗi ──> 2. Chui ra khỏi gầm, tháo găng tay dính dầu ──> 3. Mở máy tính search file PDF manual ──> 4. Đọc hiểu ──> 5. Quay lại gầm xe.
- **Bước nào tốn thời gian/lỗi nhất?** Bước 2, 3 (⏱ 10-15p/lần tra cứu).
- **AI nhảy vào hỗ trợ ở đâu?** KTV đeo tai nghe, gọi Voice Agent: "Tra cách xử lý mã BMS_X72". AI dùng RAG trích xuất đúng document và đọc từng bước kiểm tra vào tai KTV.
- **Đo thành công bằng gì (Metric):** Giảm thời gian Turn-Around-Time (thời gian lưu chuồng) của ca khó xuống 20%. Đạt Zero-touch (không chạm màn hình) khi tra cứu.
- **Quick Architecture:** [x] Agent