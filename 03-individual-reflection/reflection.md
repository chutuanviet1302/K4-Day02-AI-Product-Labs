# 03 - Individual Reflection

## Đóng góp của tôi trong nhóm

| Hoạt động | Tôi đã làm gì? | Kết quả |
|---|---|---|
| Scan cá nhân | Đưa ra các vấn đề trong lĩnh vực y tế như quên uống thuốc, khó hiểu kết quả xét nghiệm, chọn sai chuyên khoa, chờ khám lâu | Nhóm có nhiều candidate để so sánh trước khi hội tụ |
| Pitch | Pitch vấn đề người bệnh quên hoặc sử dụng thuốc sai hướng dẫn | Vấn đề được đưa vào nhóm candidate ban đầu |
| Challenge | Hỏi nhóm liệu "quá tải bệnh viện" có quá rộng không và bottleneck thật sự nằm ở bước nào | Nhóm thu hẹp từ chủ đề quá tải sang bài toán phân loại bệnh nhân ban đầu (Triage) |
| Workflow | Góp ý current/future workflow cho quy trình tiếp nhận và phân loại ban đầu | Nhóm xác định rõ bước nghẽn là điều dưỡng phải hỏi triệu chứng và ghi chép thủ công |
| Validation | Đề xuất kiểm chứng với điều dưỡng/bác sĩ và bệnh nhân về thời gian hỏi bệnh, mức độ lặp lại và khả năng bệnh nhân tự khai báo | Nhóm sửa scope: AI chỉ hỗ trợ khai báo text/voice và tóm tắt, không tự phân loại |
| Rule / Workflow / Agent | Lập luận chọn Workflow thay vì Agent vì quy trình có điểm can thiệp rõ và cần điều dưỡng duyệt | Nhóm thống nhất AI là trợ lý nhập liệu; điều dưỡng là người ra quyết định chuyên môn |

## Bảng dùng AI trong reflection

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì |
|---|---|---|---|---|
| Scan | Gợi ý thêm problems trong lĩnh vực y tế | Giúp mở rộng danh sách vấn đề ngoài các ý quen thuộc như chờ khám hoặc nhắc thuốc | Một số gợi ý quá rộng, giống ý tưởng sản phẩm hơn là problem thật | Bỏ các ý không có actor, workflow hoặc dấu hiệu đo được |
| Pitch / Shortlist | Nhờ AI gợi ý tiêu chí so sánh candidate | Giúp nhóm có khung đánh giá: actor, workflow, bottleneck, impact, metric, scope | AI có thể chấm điểm quá tự tin dù chưa có dữ liệu thực tế | Chỉ dùng tiêu chí làm khung thảo luận, quyết định cuối do nhóm |
| Workflow | Nhờ AI chuyển mô tả tiếp nhận bệnh nhân thành current/future workflow | Nhanh hơn khi tách các bước: bốc số, chờ, hỏi triệu chứng, đo sinh hiệu, phân loại | AI có xu hướng bỏ qua ràng buộc thực tế như bệnh nhân lớn tuổi hoặc không dùng được kiosk | Thêm fallback: bệnh nhân không dùng được AI thì điều dưỡng hỏi trực tiếp |
| Problem Statement | Nhờ AI phản biện câu chữ và field còn mơ hồ | AI chỉ ra các cụm từ như "quá tải", "chờ lâu", "giảm tải" chưa đủ cụ thể | AI dễ đề xuất AI triage tự động, rủi ro cao trong y tế | Viết lại problem quanh bước thu thập và cấu trúc thông tin, không phải tự phân loại |
| Rule / Workflow / Agent | Nhờ AI so sánh No AI, Rule, Workflow và Agent | Giúp thấy Rule phù hợp cho checkbox, Workflow phù hợp cho lời kể tự nhiên, Agent quá rủi ro | AI đôi lúc đẩy sang agent tự quyết định mức độ khẩn cấp | Hạ scope về Workflow; đặt human boundary cho điều dưỡng |

## Bài học của tôi

- Problem tốt không phải problem nghe "AI" nhất, mà là problem có actor, workflow, bottleneck và metric rõ.
- Chủ đề lớn như "quá tải bệnh viện" cần được thu hẹp thành một điểm nghẽn cụ thể, ví dụ điều dưỡng mất nhiều thời gian hỏi và ghi triệu chứng ban đầu.
- Vẽ workflow giúp thấy AI nên nằm ở đâu: trong case này là giữa lúc bệnh nhân chờ và trước khi gặp điều dưỡng.
- AI không nên tự chẩn đoán hoặc tự phân loại cấp cứu. Trong bối cảnh y tế, AI nên hỗ trợ cấu trúc thông tin để người có chuyên môn quyết định.
- Agent không phải đích đến mặc định. Workflow hợp lý hơn vì quy trình có đường đi rõ và có human-in-the-loop.
- Research không phải để copy tool, mà để thấy pattern: AI thu thập/tóm tắt, người thật review và chịu trách nhiệm.

## Nếu làm lại

Tôi sẽ validate sớm hơn với nhiều actor thật hơn, đặc biệt là điều dưỡng trực phân loại và bệnh nhân lớn tuổi. Nhóm cần kiểm chứng trước khi chốt pilot:

1. Điều dưỡng hiện mất trung bình bao lâu để hỏi triệu chứng và ghi chép cho một bệnh nhân?
2. Bệnh nhân có sẵn sàng khai báo qua kiosk/QR trong lúc chờ không?
3. Bản tóm tắt AI có đủ ngắn, đúng và dễ duyệt để điều dưỡng dùng thật không?

Tôi cũng sẽ đo baseline rõ hơn trước khi đặt mục tiêu, ví dụ thời gian thao tác tại quầy, số bệnh nhân xử lý mỗi giờ và tỷ lệ bản tóm tắt phải sửa nhiều. Nếu bệnh nhân dùng bot quá chậm hoặc AI tóm tắt sai nhiều, nhóm nên quay về form rule-based đơn giản thay vì cố dùng LLM.
