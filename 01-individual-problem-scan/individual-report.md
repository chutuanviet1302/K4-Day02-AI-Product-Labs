# 01 - Individual Problem Scan

> Người scan: Chu Tuấn Việt
> Ngày: 27/07/2026
> Lĩnh vực: Y tế

## Scan rộng

Tôi scan 10 problems, vượt mức tối thiểu 5.

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---:|---|---|---|---|
| 1 | Tốn thời gian | Người bệnh phải chờ lâu và không biết khi nào đến lượt khám | Bệnh nhân, người nhà, nhân viên tiếp nhận | Thời gian chờ cao; bệnh nhân hỏi lượt nhiều lần; có trường hợp bỏ lượt |
| 2 | Lặp lại | Người bệnh quên uống thuốc, uống sai giờ hoặc nhầm liều | Người bệnh, người cao tuổi, người chăm sóc | Quên thuốc nhiều lần/tuần; thuốc còn dư; phải hỏi lại cách dùng |
| 3 | AI có thể tốt hơn | Người bệnh khó hiểu chỉ số và thuật ngữ trong kết quả xét nghiệm | Bệnh nhân, người nhà, bác sĩ tư vấn | Nhiều câu hỏi về chỉ số; tự tra Internet; lo lắng hoặc hiểu sai |
| 4 | Tốn thời gian | Tình trạng quá tải tại các bệnh viện tuyến trung ương khiến bệnh nhân phải chờ lâu để được tiếp nhận, khám hoặc nhập viện | Bệnh nhân, người nhà, nhân viên tiếp nhận, điều dưỡng, bác sĩ | Khu chờ đông; thời gian chờ kéo dài; bệnh nhân phải chuyển tuyến/chờ giường; nhân viên y tế xử lý quá tải |
| 5 | Lặp lại | Người bệnh bỏ lỡ lịch tái khám hoặc quên làm xét nghiệm trước lịch hẹn | Người bệnh mạn tính, bác sĩ, người chăm sóc | Lỡ hẹn; đến sai ngày; thiếu kết quả xét nghiệm khi tái khám |
| 6 | Pain từ người khác | Điều dưỡng phải nhắc lại cùng một hướng dẫn chăm sóc sau khám cho nhiều bệnh nhân | Điều dưỡng, bệnh nhân, người nhà | Câu hỏi lặp lại; thời gian tư vấn kéo dài; bệnh nhân vẫn làm sai |
| 7 | Tốn thời gian | Nhân viên phải xác minh thủ công trạng thái giường giữa nhiều khoa | Nhân viên điều phối giường, điều dưỡng, bệnh nhân nhập viện | Nhiều cuộc gọi/nhắn tin; thông tin giường chậm; bệnh nhân chờ nhận giường |
| 8 | AI có thể tốt hơn | Bác sĩ mất thời gian đọc lại lịch sử khám dài trước khi tiếp nhận bệnh nhân tái khám | Bác sĩ, bệnh nhân tái khám | Hồ sơ dài; thời gian chuẩn bị lâu; dễ bỏ sót thông tin quan trọng |
| 9 | Pain từ người khác | Người nhà bệnh nhân không nắm được các bước thủ tục nhập viện, thanh toán, bảo hiểm | Người nhà, nhân viên hành chính | Hỏi nhiều quầy; đi lại nhiều lần; thiếu giấy tờ |
| 10 | Lặp lại | Nhân viên tổng đài trả lời lặp lại các câu hỏi về giờ khám, giấy tờ, quy trình đặt lịch | Nhân viên tổng đài, bệnh nhân | Câu hỏi trùng lặp hằng ngày; thời lượng cuộc gọi cao |

Vì sao phần scan này mạnh:

- Có scan rộng trước khi hội tụ.
- Có nhiều lăng kính khác nhau: lặp lại, tốn thời gian, pain từ người khác, AI có thể tốt hơn.
- Mỗi problem đều có actor và dấu hiệu thật có thể quan sát.
- Không bắt đầu bằng "làm chatbot" hoặc "xây agent".

## Top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---:|---|---|---|
| 1 | Tình trạng quá tải tại các bệnh viện tuyến trung ương | Impact lớn, ảnh hưởng nhiều actor, có thể đo bằng thời gian chờ, số bệnh nhân tồn và thông lượng xử lý theo giờ | Đây là chủ đề rộng; cần thu hẹp thành bottleneck cụ thể như tiếp nhận ban đầu, triage, điều phối giường hoặc phân luồng khám |
| 2 | Người bệnh quên hoặc sử dụng thuốc sai hướng dẫn | Actor rõ, xảy ra hằng ngày, impact sức khỏe cao, đo được số lần quên/sai thuốc | Sai thuốc đến từ quên lịch, khó hiểu đơn, hay thiếu người chăm sóc? |
| 3 | Người bệnh khó hiểu kết quả xét nghiệm | Pain thật, AI có thể hỗ trợ diễn giải ngôn ngữ chuyên môn | Ranh giới giữa giải thích và chẩn đoán phải kiểm soát chặt |

## Problem Card #1 - Tình trạng quá tải tại các bệnh viện tuyến trung ương

### Problem 1 câu

Tại các bệnh viện tuyến trung ương, lượng bệnh nhân đến khám và nhập viện lớn khiến khu tiếp nhận ban đầu bị ùn tắc, trong đó bước hỏi triệu chứng, ghi nhận thông tin và phân loại ưu tiên đang làm bệnh nhân phải chờ lâu.

### Actor

Actor chính là điều dưỡng hoặc nhân viên y tế phụ trách tiếp nhận/phân loại ban đầu. Actor chịu ảnh hưởng gồm bệnh nhân, người nhà, bác sĩ khám, nhân viên tiếp nhận và bộ phận điều phối trong bệnh viện.

### Thời điểm / bối cảnh

Vấn đề xảy ra vào giờ cao điểm tại khu khám bệnh hoặc khu tiếp nhận ban đầu của bệnh viện tuyến trung ương, khi nhiều bệnh nhân cùng đến đăng ký, khai báo triệu chứng, chờ đo sinh hiệu và chờ được phân loại ưu tiên.

### Current workflow

1. Bệnh nhân đến bệnh viện và lấy số thứ tự.
2. Bệnh nhân ngồi chờ đến lượt tiếp nhận.
3. Nhân viên y tế hoặc điều dưỡng hỏi thông tin cá nhân, lý do đến khám và triệu chứng chính.
4. Điều dưỡng ghi chép lại thông tin ban đầu.
5. Điều dưỡng đo sinh hiệu.
6. Điều dưỡng đánh giá mức ưu tiên hoặc hướng bệnh nhân sang luồng khám phù hợp.
7. Bệnh nhân tiếp tục chờ bác sĩ khám hoặc chờ xử lý bước tiếp theo.

### Bottleneck

Bottleneck nằm ở bước 3-4: điều dưỡng phải hỏi và ghi chép thủ công thông tin ban đầu cho từng bệnh nhân.

Khi bệnh nhân đông, nhiều câu hỏi bị lặp lại như lý do đến khám, thời gian xuất hiện triệu chứng, mức độ đau, bệnh nền, thuốc đang dùng. Điều dưỡng vừa phải khai thác thông tin vừa nhập liệu, khiến hàng đợi kéo dài.

### Impact

Bệnh nhân và người nhà phải chờ lâu, dễ bức xúc và lo lắng. Điều dưỡng bị quá tải ở khâu tiếp nhận, bác sĩ nhận bệnh nhân chậm hơn, còn bệnh viện khó phát hiện sớm các trường hợp cần ưu tiên nếu khu chờ quá đông.

### Success metric

Giảm thời gian từ lúc bệnh nhân lấy số đến lúc hoàn tất tiếp nhận/phân loại ban đầu; giảm thời gian thao tác của điều dưỡng trên mỗi bệnh nhân; tăng số bệnh nhân được tiếp nhận mỗi giờ; giảm số lần bệnh nhân phải hỏi lại về lượt chờ hoặc quy trình.

### Non-AI alternative

Tăng số quầy tiếp nhận, tăng điều dưỡng giờ cao điểm, phát phiếu giấy để bệnh nhân điền trước, dùng form checkbox cố định, hoặc phân luồng riêng cho bệnh nhân tái khám/khám mới/cấp cứu.

### AI hypothesis

AI có thể hỗ trợ bệnh nhân khai báo triệu chứng bằng text hoặc giọng nói trong lúc chờ, sau đó tóm tắt thành form có cấu trúc để điều dưỡng đọc nhanh, xác nhận lại và đo sinh hiệu.

AI không được chẩn đoán, không được tự phân loại cấp cứu, không được đưa lời khuyên điều trị. Quyết định chuyên môn vẫn thuộc về điều dưỡng và bác sĩ.

### Quick gut

**Workflow.**

Rule có thể dùng để chuẩn hóa các trường thông tin bắt buộc. AI hữu ích ở phần chuyển lời kể tự nhiên của bệnh nhân thành bản tóm tắt ngắn. Con người vẫn kiểm tra, hỏi lại và quyết định cuối cùng.

### Draft current workflow

```text
CURRENT STATE

[Bệnh nhân đến bệnh viện]
        ↓
[Lấy số thứ tự]
        ↓
[Ngồi chờ đến lượt]
        ↓
[Điều dưỡng hỏi triệu chứng và thông tin nền]
        ↓
[Điều dưỡng ghi chép thủ công]  <-- BOTTLENECK
        ↓
[Đo sinh hiệu]
        ↓
[Phân loại ưu tiên / chuyển luồng khám]
        ↓
[Chờ bác sĩ khám]
```

### Draft future workflow

```text
FUTURE STATE

[Bệnh nhân lấy số]
        ↓
[Khai báo triệu chứng qua QR/kiosk trong lúc chờ]
        ↓
[AI tóm tắt thành form có cấu trúc]
        ↓
[Điều dưỡng đọc và xác nhận lại thông tin]
        ↓
[Điều dưỡng đo sinh hiệu]  <-- HUMAN BOUNDARY
        ↓
[Điều dưỡng phân loại ưu tiên / chuyển luồng khám]
        ↓
[Chờ bác sĩ khám]

Fallback: bệnh nhân không dùng được AI hoặc khai báo thiếu -> điều dưỡng hỏi trực tiếp như workflow hiện tại.
```

## Problem Cards #2 và #3 - Tóm tắt

| Card | Actor | Bottleneck | Metric | Quick gut | Vì sao chưa chọn làm #1 |
|---|---|---|---|---|---|
| Quên hoặc dùng sai thuốc | Người bệnh dùng nhiều thuốc, người cao tuổi, người chăm sóc | Người bệnh phải tự diễn giải đơn thuốc thành lịch uống cụ thể | Giảm số lần quên thuốc, sai giờ, sai liều; tăng tỷ lệ hoàn thành liệu trình | Workflow kết hợp Rule và AI | Impact quan trọng nhưng phạm vi cá nhân hơn, không phản ánh trực tiếp bài toán quá tải bệnh viện tuyến trung ương |
| Khó hiểu kết quả xét nghiệm | Người bệnh vừa nhận kết quả xét nghiệm | Khoảng trống giữa lúc nhận kết quả và lúc được bác sĩ giải thích | Giảm số câu hỏi cơ bản; giảm thời gian tự tra Internet; tăng hiểu đúng giới hạn của kết quả | AI có kiểm soát + Workflow | Rủi ro cao nếu AI bị hiểu nhầm là chẩn đoán; cần boundary rất chặt |
