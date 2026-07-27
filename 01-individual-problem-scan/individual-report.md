# 01 - Individual Problem Scan

> Người scan: Chu Tuấn Việt
> Ngày: 27/07/2026
> Lĩnh vực: Y tế

## Scan Việt

Tôi scan 10 problems, vượt mức tối thiểu 5.

| # | Lăng kính | Problem quan sát được | Ai chịu ảnh hưởng? | Dấu hiệu thật |
|---:|---|---|---|---|
| 1 | Tốn thời gian | Người bệnh phải chờ lâu và không biết khi nào đến lượt khám | Bệnh nhân, người nhà, nhân viên tiếp nhận | Thời gian chờ cao; bệnh nhân hỏi lượt nhiều lần; có trường hợp bỏ lượt |
| 2 | Lặp lại | Người bệnh quên uống thuốc, uống sai giờ hoặc nhầm liều | Người bệnh, người cao tuổi, người chăm sóc | Quên thuốc nhiều lần/tuần; thuốc còn dư; phải hỏi lại cách dùng |
| 3 | AI có thể tốt hơn | Người bệnh khó hiểu chỉ số và thuật ngữ trong kết quả xét nghiệm | Bệnh nhân, người nhà, bác sĩ tư vấn | Nhiều câu hỏi về chỉ số; tự tra Internet; lo lắng hoặc hiểu sai |
| 4 | Tốn thời gian | Người bệnh không biết nên đăng ký chuyên khoa nào từ triệu chứng ban đầu | Người lần đầu đi khám, nhân viên tiếp nhận | Đăng ký nhầm khoa; phải chuyển khoa; mất thêm thời gian chờ |
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
| 1 | Người bệnh quên hoặc sử dụng thuốc sai hướng dẫn | Actor rõ, xảy ra hằng ngày, impact sức khỏe cao, đo được số lần quên/sai thuốc | Sai thuốc đến từ quên lịch, khó hiểu đơn, hay thiếu người chăm sóc? |
| 2 | Người bệnh khó hiểu kết quả xét nghiệm | Pain thật, AI có thể hỗ trợ diễn giải ngôn ngữ chuyên môn | Ranh giới giữa giải thích và chẩn đoán phải kiểm soát chặt |
| 3 | Người bệnh không biết nên đăng ký chuyên khoa nào | Workflow rõ, có thể giảm chuyển khoa và thời gian chờ | Rule-based routing có thể đã đủ cho nhiều trường hợp phổ biến |

## Problem Card #1 - Người bệnh quên hoặc sử dụng thuốc sai hướng dẫn

### Problem 1 câu

Người bệnh, đặc biệt là người cao tuổi hoặc người phải dùng nhiều loại thuốc, thường quên lịch uống, uống sai giờ hoặc nhầm liều vì hướng dẫn sử dụng thuốc khó chuyển thành lịch sinh hoạt hằng ngày.

### Actor

Người bệnh đang sử dụng thuốc theo đơn, đặc biệt là người cao tuổi, người mắc bệnh mạn tính hoặc người phải uống nhiều loại thuốc trong ngày. Actor liên quan gồm người chăm sóc, bác sĩ và dược sĩ.

### Thời điểm / bối cảnh

Sau khi khám và nhận đơn thuốc, người bệnh mang thuốc về nhà và phải tự nhớ đúng thuốc, đúng liều, đúng thời điểm trong nhiều ngày hoặc nhiều tuần.

### Current workflow

1. Bác sĩ khám và kê đơn thuốc.
2. Người bệnh nhận thuốc tại nhà thuốc.
3. Dược sĩ hướng dẫn cách dùng bằng lời nói hoặc ghi chú trên bao bì.
4. Người bệnh mang thuốc về nhà.
5. Người bệnh tự đọc đơn và tự tạo lịch uống.
6. Đến giờ uống, người bệnh phải nhớ đúng thuốc, đúng liều, đúng thời điểm.
7. Khi không chắc, người bệnh hỏi người thân, gọi lại dược sĩ/bác sĩ hoặc tự tìm trên Internet.

### Bottleneck

Bước 5-6: người bệnh phải tự diễn giải đơn thuốc thành lịch uống cụ thể và tự ghi nhớ nhiều mốc thời gian trong ngày.

Thông tin trên đơn thường nằm rải rác theo tên thuốc, liều lượng, số lần dùng, thời điểm trước/sau ăn. Với người lớn tuổi hoặc người dùng nhiều thuốc, việc tự chuyển các thông tin này thành hành động đúng mỗi ngày rất dễ sai.

### Impact

Người bệnh có thể quên thuốc, uống sai giờ, nhầm liều hoặc nhầm loại thuốc. Điều này làm giảm hiệu quả điều trị, tăng nguy cơ tác dụng không mong muốn và khiến người bệnh/người nhà phải mất thời gian kiểm tra lại đơn thuốc. Bác sĩ hoặc dược sĩ cũng phải trả lời lại các câu hỏi đã hướng dẫn trước đó.

### Success metric

Giảm số lần quên uống thuốc trong một tuần; giảm số lần uống sai giờ hoặc sai liều; giảm số lần người bệnh phải hỏi lại cách dùng thuốc; tăng tỷ lệ người bệnh hoàn thành đúng liệu trình.

### Non-AI alternative

In lịch uống thuốc theo từng khung giờ, dùng hộp chia thuốc theo ngày/buổi, đặt báo thức cố định trên điện thoại, gửi SMS nhắc thuốc, hoặc dược sĩ viết lại hướng dẫn bằng ngôn ngữ dễ hiểu.

### AI hypothesis

AI có thể đọc thông tin từ đơn thuốc đã được xác nhận, chuyển thành lịch uống dễ hiểu, nhắc đúng thời điểm và trả lời các câu hỏi cơ bản dựa trên hướng dẫn của bác sĩ/dược sĩ.

AI không được tự ý đổi liều, ngừng thuốc, chẩn đoán bệnh hoặc đưa lời khuyên ngoài đơn thuốc. Trường hợp bất thường phải chuyển cho bác sĩ hoặc dược sĩ.

### Quick gut

**Workflow kết hợp Rule và AI.**

Rule phù hợp để nhắc đúng giờ, đúng lịch. AI hữu ích ở bước diễn giải đơn thuốc và hỗ trợ người bệnh hỏi lại bằng ngôn ngữ tự nhiên. Con người vẫn xác nhận đơn và xử lý trường hợp bất thường.

### Draft current workflow

```text
CURRENT STATE

[Bác sĩ kê đơn]
        ↓
[Dược sĩ hướng dẫn bằng lời hoặc ghi trên đơn]
        ↓
[Người bệnh mang thuốc về]
        ↓
[Tự đọc và tự tạo lịch uống]
        ↓
[Tự nhớ đúng giờ, đúng thuốc, đúng liều]  <-- BOTTLENECK
        ↓
[Quên / nhầm / hỏi người thân]
        ↓
[Gọi bác sĩ hoặc tự tìm trên Internet]
```

### Draft future workflow

```text
FUTURE STATE

[Bác sĩ kê đơn]
        ↓
[Dược sĩ hoặc người bệnh xác nhận thông tin đơn]
        ↓
[Hệ thống trích xuất lịch uống]
        ↓
[AI diễn giải thành hướng dẫn dễ hiểu]
        ↓
[Rule nhắc đúng giờ, đúng loại thuốc]
        ↓
[Người bệnh xác nhận đã uống]  <-- HUMAN BOUNDARY
        ↓
[Bất thường được chuyển cho bác sĩ hoặc dược sĩ]

Fallback: AI đọc sai đơn hoặc thiếu thông tin -> dùng hướng dẫn gốc và hỏi dược sĩ/bác sĩ.
```

## Problem Cards #2 và #3 - Tóm tắt

| Card | Actor | Bottleneck | Metric | Quick gut | Vì sao chưa chọn làm #1 |
|---|---|---|---|---|---|
| Khó hiểu kết quả xét nghiệm | Người bệnh vừa nhận kết quả xét nghiệm | Khoảng trống giữa lúc nhận kết quả và lúc được bác sĩ giải thích | Giảm số câu hỏi cơ bản; giảm thời gian tự tra Internet; tăng hiểu đúng giới hạn của kết quả | AI có kiểm soát + Workflow | Rủi ro cao nếu AI bị hiểu nhầm là chẩn đoán; cần boundary rất chặt |
| Không biết chọn chuyên khoa | Người bệnh lần đầu đi khám hoặc đặt lịch online | Người bệnh phải tự ánh xạ triệu chứng sang chuyên khoa | Giảm tỷ lệ đăng ký nhầm khoa; giảm số lượt chuyển khoa; giảm thời gian gặp đúng bác sĩ | Rule trước, AI sau | Nhiều trường hợp phổ biến có thể giải bằng cây câu hỏi/rule, chưa cần AI ngay |
