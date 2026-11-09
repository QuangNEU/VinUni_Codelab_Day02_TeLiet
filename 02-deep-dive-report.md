# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:


```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Thăm khám &  │     │ Tra cứu & kê │     │ Dược sĩ lâm  │     │ Bệnh nhân    │
│ chẩn đoán    │ ──→ │ đơn thủ công │ ──→ │ sàng thẩm    │ ──→ │ nhận thuốc   │
│ bệnh lý      │     │ trên EMR     │     │ định đơn     │     │ tại quầy     │
│              │     │              │     │              │     │              │
│ Ai: Bác sĩ   │     │ Ai: Bác sĩ   │     │ Ai: Dược sĩ  │     │ Ai: Dược sĩ/BN│
│ ⏱ 5 phút     │     │ ⏱ 7 phút 🔴  │     │ ⏱ 3 phút 🔴  │     │ ⏱ 3 phút     │
│ In: Triệu    │     │ In: Bệnh án  │     │ In: Đơn xuất │     │ In: Đơn hợp lệ│
│     chứng    │     │ Out: Đơn nháp│     │ Out: Duyệt đơn│    │ Out: Giao    │
│ Out: Chẩn    │ 🔄  │              │ 🔄  │              │ 🔄  │      thuốc   │
│      đoán    │Handoff             │Handoff             │Handoff             │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                 │
                                                 │ ⚠️ Khi phát hiện xung đột /
                                                 │    dị ứng thuốc (Xác suất ~15%)
                                                 ▼
                                          ┌──────────────┐
                                          │ Nhánh trễ 🔴 │
                                          │ Dược sĩ gọi  │
                                          │ điện yêu cầu │
                                          │ bác sĩ sửa   │
                                          │ ⏱ +10-15 phút│
                                          └──────────────┘

```
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

## 3.2. Problem Statement - 6 Fields & Metrics

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Bác sĩ khám lâm sàng ngoại trú và Dược sĩ lâm sàng tại các bệnh viện Đa khoa Quốc tế Vinmec. |
| **2. Current Workflow** | Bác sĩ chẩn đoán bệnh, mở phân hệ kê đơn trên EMR của Vinmec, tự gõ tìm thuốc, tự nhớ hoặc tra cứu thủ công tương tác thuốc và tiền sử dị ứng bệnh nhân, sau đó phát hành đơn thuốc. Đơn được chuyển sang quầy dược để Dược sĩ lâm sàng rà soát lại trước khi cấp phát; nếu phát hiện xung đột hoặc chống chỉ định, Dược sĩ phải gọi điện thoại yêu cầu Bác sĩ sửa và phát hành lại đơn. Quy trình gồm 4 bước, mất trung bình 18 phút mỗi ca, kéo dài 28 đến 33 phút nếu xảy ra xung đột thuốc. |
| **3. Bottleneck** | Bước 2 là tra cứu, phối hợp thuốc trên EMR và Bước 3 là Dược sĩ rà soát thủ công kèm vòng lặp gọi điện thoại sửa đơn: Bác sĩ mất nhiều thời gian tra cứu Dược thư đối với bệnh nhân đa bệnh lý; hệ thống cảnh báo tĩnh cũ dễ gây tình trạng mệt mỏi vì cảnh báo rác hoặc bỏ sót các tương tác phức hợp; Dược sĩ phát hiện muộn khiến quy trình bị đứt gãy. |
| **4. Business Impact** | Tại mỗi cơ sở Vinmec, trung bình 10 đến 15% đơn thuốc của bệnh nhân mạn tính hoặc đa bệnh lý gặp vấn đề về phối hợp thuốc cần hiệu chỉnh. Mỗi ngày gây lãng phí 2 đến 3 giờ làm việc của Bác sĩ và Dược sĩ trong việc trao đổi sửa đơn; tăng thời gian chờ nhận thuốc của bệnh nhân lên tới 30 đến 45 phút, gây quá tải sảnh chờ nhà thuốc và tiềm ẩn rủi ro sai sót y khoa đe dọa tiêu chuẩn chất lượng quốc tế JCI. |
| **5. Success Metric** | 1. Giảm thời gian kê đơn và thẩm định đơn thuốc từ 10 phút xuống dưới 2.5 phút mỗi lượt.<br>2. Giảm tối thiểu 80% số cuộc gọi sửa đơn giữa Dược sĩ và Bác sĩ do xung đột hoạt chất được cảnh báo ngay tại thời điểm kê đơn.<br>3. Tỷ lệ phát hiện chính xác tương tác thuốc hoặc dị ứng đạt tối thiểu 98%, giảm 70% cảnh báo giả so với hệ thống rule-based cũ. |
| **6. Operational Boundary** | AI ĐƯỢC PHÉP: Truy xuất dữ liệu chẩn đoán ICD-10, tiền sử dị ứng, kết quả cận lâm sàng và lịch sử dùng thuốc trên EMR; sử dụng đồ thị tri thức kết hợp LLM để gợi ý danh mục phối hợp thuốc tối ưu và hiển thị bản nháp cảnh báo tương tác mang thẻ DRAFT_ONLY kèm văn bản giải thích cơ chế rủi ro cho Bác sĩ.<br>AI TUYỆT ĐỐI CẤM: Không được tự ý ký số, tự phát hành hoặc tự lưu đơn thuốc vào cơ sở dữ liệu EMR mà không có sự xác nhận của Bác sĩ; không được tự động từ chối chỉ định của Bác sĩ; không tự ý thay đổi phác đồ cấp cứu khẩn cấp. Bắt buộc 100% Bác sĩ phải xem xét và nhấn Phê duyệt theo cơ chế Human-in-the-loop. |

## 3.3. Future-State Flow & AI Fit

- **AI Fit:** Chọn **LLM Feature** (kết hợp Graph Embedding / Node2Vec trích xuất tri thức, không dùng Agent tự trị vì môi trường y tế đòi hỏi tính tiền định cao, rủi ro sai lệch liều lượng hoặc hoạt chất ảnh hưởng trực tiếp đến tính mạng bệnh nhân nên cần quy trình kiểm soát chặt chẽ).
- **Quy trình tương lai (Future-State):**

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Thăm khám &  │     │ 🔵 AI Graph  │     │ 🔵 AI draft  │     │ 🟢 Bác sĩ    │
│ chẩn đoán    │ ──→ │ quét tương   │ ──→ │ đơn & cảnh   │ ──→ │ click duyệt  │
│ bệnh lý      │     │ tác & dị ứng │     │ báo an toàn  │     │ & ký số EMR  │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ↩️ Fallback:
                                                               Nếu AI gặp lỗi
                                                               hoặc timeout,
                                                               Bác sĩ tự tra
                                                               cứu và kê đơn
                                                               tay lại như cũ.
```

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
> Nhóm quyết định lựa chọn mức độ **GO** cho giai đoạn thử nghiệm phạm vi hẹp (Pilot Prototype) với các luận cứ thực nghiệm sau:
> 
> 1. **Mức độ sẵn sàng của dữ liệu (Data Readiness):** Dữ liệu danh mục dược thư quốc gia, chỉ dẫn lâm sàng và phân loại tương tác thuốc (DrugBank, Dược thư Việt Nam) là tri thức chuẩn hóa dạng đồ thị có sẵn, cấu trúc rõ ràng. Cơ sở dữ liệu EMR tại Vinmec đã số hóa đầy đủ tiền sử dị ứng và hồ sơ bệnh án điện tử, cung cấp nguồn dữ liệu sạch để trích xuất tri thức dạng Graph mà không cần gán nhãn thủ công từ đầu.
> 2. **Kiểm soát rủi ro an toàn y khoa tuyệt đối (Safety & Risk Boundary):** Mô hình được thiết lập chặt chẽ theo cơ chế **Human-in-the-loop (HITL)**. AI chỉ đóng vai trò phân tích, cảnh báo và draft đơn thuốc hỗ trợ; quyền ký số và phát hành đơn bắt buộc thuộc về Bác sĩ điều trị. Khi hệ thống gặp độ trễ hoặc lỗi kết nối, quy trình tự động chuyển sang cơ chế **Fallback** (Bác sĩ tự kê đơn tay như cũ), đảm bảo hoạt động khám chữa bệnh không bao giờ bị gián đoạn.
> 3. **Hiệu quả kinh tế và vận hành (Business Impact & Feasibility):** Giải pháp kiến trúc sử dụng **LLM Feature kết hợp Graph Embedding** có chi phí triển khai tối ưu, không đòi hỏi xây dựng hệ thống Multi-Agent phức tạp. Dự án giải quyết trực tiếp điểm nghẽn lớn nhất trong phối hợp liên phòng ban: giảm thời gian kê đơn từ 10 phút xuống dưới 2.5 phút và giảm trên 80% các cuộc gọi sửa đơn ngắt quãng giữa Dược sĩ và Bác sĩ, nâng cao năng suất khám bệnh và tuân thủ chặt chẽ tiêu chuẩn quốc tế JCI của Vinmec.

