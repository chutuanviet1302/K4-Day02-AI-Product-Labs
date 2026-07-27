# 02 - Group Problem Statement

## Group convergence
Đề tài : Tình trạng quá tải tại các bệnh viện tuyến trung ương
Nhóm chia sẻ các candidate problem trong bối cảnh quá tải bệnh viện và gom lại thành 4 cluster chính.

| Cluster | Candidate examples | Pattern chung |
|---|---|---|
| Thu thập thông tin ban đầu | Khai báo triệu chứng cấp cứu, lịch sử bệnh nền, khai báo y tế | Điều dưỡng phải hỏi lại nhiều câu lặp lại với từng bệnh nhân. |
| Phân bổ nguồn lực | Xếp giường bệnh, phân luồng phòng khám, điều phối bệnh nhân | Mất thời gian tìm thông tin phòng/giường trống và ghép nối bệnh nhân phù hợp. |
| Quản lý hồ sơ / báo cáo | Tóm tắt bệnh án chuyển tuyến, viết báo cáo ca trực | Gom thông tin từ nhiều nguồn như HIS, xét nghiệm, ghi chú bác sĩ để bàn giao. |
| Trả kết quả / hướng dẫn | Giải thích kết quả xét nghiệm, hướng dẫn dùng thuốc | Bác sĩ hoặc dược sĩ phải giải thích các thông tin cơ bản lặp đi lặp lại. |

## Shortlist và score

| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Phân loại bệnh nhân ban đầu (Triage) | 5 | 5 | 5 | 5 | 4 | 5 | 4 | 33 |
| Tóm tắt bệnh án | 4 | 4 | 4 | 4 | 5 | 4 | 4 | 29 |
| Xếp giường bệnh | 3 | 3 | 5 | 4 | 2 | 4 | 3 | 24 |

Nhóm chọn: **Phân loại bệnh nhân ban đầu (Triage)**.

Vì sao chọn:

- Workflow rõ: bệnh nhân đến, khai báo, đo sinh hiệu, điều dưỡng phân loại ưu tiên.
- Bottleneck cụ thể: điều dưỡng phải hỏi triệu chứng và ghi chép thủ công cho từng bệnh nhân.
- Có baseline thời gian ước tính: khoảng 5-7 phút hỏi bệnh/người, dễ tạo nút thắt ở khu chờ khi đông bệnh nhân.
- Có thể vẽ before/after rõ.
- Rủi ro y tế có thể kiểm soát nếu đặt đúng human boundary: điều dưỡng vẫn là người quyết định cuối cùng.

Vì sao không chọn các bài khác:

- Xếp giường bệnh phụ thuộc nhiều vào hệ thống HIS lõi và dữ liệu vận hành thực tế của bệnh viện, khó pilot trong phạm vi lab.
- Tóm tắt bệnh án có giá trị, nhưng impact trực tiếp lên thời gian chờ ban đầu của bệnh nhân không rõ bằng Triage.

## Quick validation

Nhóm hỏi nhanh 2 điều dưỡng trưởng và 1 bác sĩ trực cấp cứu.

| Nguồn | Số người | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Phỏng vấn nhanh | 3 | 3/3 xác nhận khâu hỏi triệu chứng ban đầu lặp lại, tốn thời gian; khi bệnh nhân đông, khu chờ dễ ùn tắc và bệnh nhân dễ bức xúc. | Bệnh nhân lớn tuổi hoặc mệt nhiều có thể không dùng tốt smartphone/app để tự khai báo. | Thu hẹp scope: AI hỗ trợ khai báo bằng text hoặc giọng nói tại kiosk/QR, không bắt buộc chỉ nhập text. |
| Mini poll bệnh nhân | 10 | 8/10 phản ánh phải chờ lâu chỉ để được hỏi triệu chứng cơ bản và lấy sinh hiệu. | Một số bệnh nhân lo rằng khai báo qua máy sẽ không được nhân viên y tế đọc kỹ. | Output của AI phải ở format chuẩn, ngắn, dễ duyệt trên màn hình điều dưỡng. |

Insight sau validation:

> Pain thật không chỉ là "bệnh nhân phải chờ", mà là việc điều dưỡng phải dịch lời kể đời thường của bệnh nhân thành thông tin y tế có cấu trúc. Nếu phần thu thập và cấu trúc thông tin được làm trước trong lúc bệnh nhân chờ, điều dưỡng có thể tập trung vào xác nhận, đo sinh hiệu và ra quyết định ưu tiên.

## Research giải pháp

| Nguồn / tool / case | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|
| Symptom checker như Ada Health / Symptomate | Hỏi triệu chứng và gợi ý hướng xử trí ban đầu | Có logic hỏi triệu chứng theo ngữ cảnh, dễ dùng với bệnh nhân | Dễ bị hiểu nhầm là chẩn đoán; không tích hợp trực tiếp vào quy trình tiếp nhận bệnh viện | Không làm AI chẩn đoán, chỉ làm AI thu thập và cấu trúc thông tin. |
| Kiosk khai báo y tế | Cho bệnh nhân điền form trước khi gặp nhân viên | Nhanh, dễ chuẩn hóa dữ liệu, có thể đồng bộ hệ thống | Form checkbox cứng nhắc, bệnh nhân khó chọn đúng khi triệu chứng phức tạp | AI có thể hỏi linh hoạt hơn form tĩnh, nhưng output vẫn phải chuẩn hóa. |
| Ambient AI / medical scribe | Lắng nghe hội thoại và tự viết ghi chú y tế | Tự nhiên, giảm việc ghi chép thủ công | Chi phí và triển khai phức tạp; rủi ro nếu ghi sai thông tin y tế | Pattern phù hợp: AI nghe/đọc input, cấu trúc lại, người thật duyệt. |

Research takeaway:

> Không nên xây agent tự quyết định mức độ khẩn cấp. Hướng an toàn hơn là Workflow: bệnh nhân tự khai báo bằng text/voice qua AI kiosk hoặc QR, AI cấu trúc thành form ngắn, điều dưỡng xem lại, đo sinh hiệu và chốt phân loại.

## Workflow before/after

### Current state - 10-15 phút/bệnh nhân tại khu tiếp nhận

```text
[1 Bệnh nhân bốc số]
        ↓
[2 Ngồi chờ tới lượt: 15-30']
        ↓
[3 Điều dưỡng hỏi triệu chứng và ghi chép: 5-7']  <-- BOTTLENECK
        ↓
[4 Điều dưỡng đo sinh hiệu: 2']
        ↓
[5 Điều dưỡng phân loại ưu tiên: 1']
        ↓
[6 Chờ bác sĩ khám]
```

### Future state - khoảng 3 phút thao tác tại quầy

```text
[1 Bệnh nhân bốc số và khai báo qua AI kiosk/QR: 3']
        ↓
[2 AI tóm tắt thành form y tế có cấu trúc: vài giây]
        ↓
[3 Điều dưỡng đọc tóm tắt trên màn hình: 30s]
        ↓
[4 Điều dưỡng đo sinh hiệu: 2']  <-- HUMAN BOUNDARY
        ↓
[5 Điều dưỡng xác nhận và phân loại: 30s]
        ↓
[6 Chờ bác sĩ khám]
```

Fallback:

```text
Bệnh nhân không dùng được AI, quá yếu, ngất, lú lẫn hoặc không hợp tác
-> quay về luồng điều dưỡng hỏi trực tiếp như hiện tại.
```

Before/after impact:

| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---:|---:|---|
| Thời gian thao tác của điều dưỡng tại quầy/bệnh nhân | 7-10 phút | Dưới 3 phút | Target chính |
| Trạng thái chờ của bệnh nhân | Chờ thụ động | Dùng thời gian chờ để khai báo | Cải thiện patient experience |
| Bước thủ công của điều dưỡng | Hỏi bệnh từ đầu và tự ghi | Đọc, xác nhận, đo sinh hiệu | Giảm tải nhập liệu |
| Bottleneck chính | Điều dưỡng hỏi và gõ thủ công | Bệnh nhân tự khai báo chậm hoặc thiếu | Chấp nhận được nếu có fallback |

## Problem Statement v0

| Field | Nội dung |
|---|---|
| Actor | Điều dưỡng trực phân loại tại khoa khám bệnh hoặc khu tiếp nhận ban đầu. |
| Workflow | Bệnh nhân lấy số, chờ, điều dưỡng hỏi bệnh sử và triệu chứng, đo sinh hiệu, rồi đánh giá mức ưu tiên. |
| Bottleneck | Bước điều dưỡng hỏi và ghi chép thủ công tốn khoảng 5-7 phút/người; khi đông bệnh nhân, bước này tạo hàng đợi kéo dài. |
| Impact | Bệnh nhân chờ lâu và dễ bức xúc; điều dưỡng stress; có nguy cơ bỏ sót dấu hiệu nặng nếu khu chờ quá tải. |
| Success Metric | Giảm thời gian thao tác tại quầy của điều dưỡng từ khoảng 7 phút xuống dưới 3 phút/bệnh nhân; tăng thông lượng tiếp nhận trong giờ cao điểm. |
| Boundary | AI không chẩn đoán, không kê đơn, không tự quyết định mức ưu tiên; chỉ cấu trúc thông tin đầu vào để điều dưỡng duyệt. |

## No AI / Rule / Workflow / Agent

| Mức | Phương án | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| No AI | Tăng nhân sự điều dưỡng ở quầy tiếp nhận hoặc phát phiếu giấy để bệnh nhân điền trước. | Đủ nếu lượng bệnh nhân tăng chỉ xảy ra trong vài khung giờ cao điểm và bệnh viện có thể bố trí thêm người. | Tốn nhân lực, dữ liệu vẫn phải nhập lại thủ công, khó chuẩn hóa lời khai. | Không chọn làm hướng chính, nhưng dùng làm fallback vận hành. |
| Rule | Kiosk/form checkbox cho bệnh nhân chọn triệu chứng có sẵn. | Đủ với khám sức khỏe định kỳ hoặc triệu chứng đơn giản. | Cứng nhắc, khó xử lý lời kể tự nhiên và triệu chứng phức tạp. | Dùng bổ trợ, không chọn làm core. |
| Workflow | Bệnh nhân chat/nói với AI, AI hỏi thêm tối đa vài câu, sau đó tóm tắt thành form chuẩn cho điều dưỡng review. | Phù hợp vì flow rõ, có điểm can thiệp cụ thể, và con người duyệt trước khi quyết định. | AI có thể bỏ sót hoặc thêm sai triệu chứng nếu không kiểm soát. | Chọn. |
| Agent | AI tự thu thập, tự đánh giá nguy hiểm, tự quyết định phân loại hoặc hướng xử trí. | Chỉ hợp với bối cảnh rất đặc biệt và đã được kiểm định nghiêm ngặt. | Rủi ro y tế/pháp lý cao, có thể nguy hiểm cho bệnh nhân. | Không chọn. |

Mức chọn: **Workflow**.

Vì sao:

- Input là lời kể tự nhiên của bệnh nhân, AI có ích trong việc trích xuất và cấu trúc.
- Output cần định dạng cố định để điều dưỡng đọc nhanh.
- Điều dưỡng vẫn là chốt chặn cuối cùng để xác nhận, đo sinh hiệu và ra quyết định chuyên môn.

## Problem Statement v1

| Field | Nội dung |
|---|---|
| Actor | Điều dưỡng trực phân loại tại khu tiếp nhận ban đầu. |
| Workflow | Bệnh nhân bốc số và khai báo triệu chứng qua AI kiosk/QR trong lúc chờ; AI tóm tắt thông tin; điều dưỡng review, đo sinh hiệu và chốt phân loại ưu tiên. |
| Bottleneck | Điều dưỡng đang mất 5-7 phút để hỏi và chuyển lời kể đời thường của bệnh nhân thành thông tin y tế có cấu trúc. |
| Impact | Tạo ùn tắc cục bộ ở khu tiếp nhận, làm bệnh nhân chờ lâu, tăng áp lực cho điều dưỡng và có nguy cơ chậm phát hiện ca nặng. |
| Success Metric | Giảm thời gian thao tác tại quầy từ baseline 7-10 phút xuống dưới 3 phút/bệnh nhân; ít nhất 90% bản tóm tắt AI được điều dưỡng giữ lại phần chính mà không phải gõ lại từ đầu. Cách đo: ghi timestamp lúc bệnh nhân vào quầy, lúc điều dưỡng hoàn tất khai thác ban đầu và số phần điều dưỡng phải sửa trong bản tóm tắt. |
| Boundary | AI không đưa lời khuyên y tế, không chẩn đoán, không kê đơn và không tự phân loại cấp cứu. |
| AI intervention point | Giữa lúc bệnh nhân bốc số chờ và trước khi bệnh nhân bước vào quầy điều dưỡng. |
| Mức chọn | Workflow: AI trích xuất triệu chứng, thời gian khởi phát, mức độ đau, triệu chứng đi kèm, bệnh nền; xuất ra form có cấu trúc cho điều dưỡng duyệt. |
| Rủi ro & người thật kiểm tra | Rủi ro chính là bỏ sót triệu chứng quan trọng hoặc thêm triệu chứng bệnh nhân không nói. Điều dưỡng phải đọc lại tóm tắt, xác nhận nhanh các dấu hiệu nguy hiểm và chốt phân loại. |

## Final decision

**Decision: Go với pilot nhỏ, scope an toàn.**

Pilot nhỏ nhất:

- Áp dụng thử ở quầy khám bệnh thông thường, chưa dùng cho Red Zone/cấp cứu tối khẩn.
- Làm chatbot hoặc webform đơn giản để giả lập kiosk, cho bệnh nhân nhập triệu chứng bằng text hoặc giọng nói.
- AI trích xuất ra format: lý do chính, thời gian khởi phát, mức độ đau, triệu chứng đi kèm, bệnh nền, dấu hiệu nguy hiểm nếu có.
- Mời 1-2 người có background y tế hoặc đóng vai điều dưỡng để so sánh thời gian đọc form AI với thời gian tự hỏi trực tiếp.

Exit / rollback:

- Nếu AI bịa hoặc thêm triệu chứng bệnh nhân không nói trên 10% số ca, dừng LLM và quay về form checkbox/rule-based.
- Nếu bệnh nhân mất quá 5 phút để dùng bot, giới hạn bot chỉ hỏi tối đa 3 lượt.
- Nếu điều dưỡng phải gõ lại gần như toàn bộ bản tóm tắt, hạ scope về form có cấu trúc, chưa dùng AI.

Decision rationale:

- Giải quyết đúng bottleneck: thu thập và cấu trúc thông tin ban đầu.
- Có human-in-the-loop rõ ràng: điều dưỡng review, đo sinh hiệu và quyết định.
- Trách nhiệm được phân định rõ: AI là trợ lý nhập liệu; điều dưỡng là người ra quyết định chuyên môn.
