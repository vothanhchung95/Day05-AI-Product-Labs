**1\. Phân tích 4 Paths (Framework AI UX)**

| **Path**                  | **Mô tả trải nghiệm từ Test Cases**                                                                       | **Phản ứng của hệ thống & UI**                                                                                                                                            |
| ------------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1\. Khi AI ĐÚNG**       | Trả lời các câu hỏi về quy định cụ thể (Ví dụ: "Tôi có được mang vật dụng kim loại lên máy bay không?").  | Cung cấp thông tin chi tiết, đầy đủ và đính kèm link dẫn chứng liên quan đến quy định.                                                                                    |
| **2\. Khi AI KHÔNG CHẮC** | User đặt câu hỏi thiếu dữ kiện (Ví dụ: Hỏi về số kg hành lý tối đa nhưng chưa cung cấp hạng vé).          | AI biết cách hỏi lại để làm rõ vấn đề. Yêu cầu user cung cấp thêm thông tin (hạng vé) để đưa ra câu trả lời chính xác cho hành lý xách tay và ký gửi.                     |
| **3\. Khi AI SAI**        | User yêu cầu tìm chuyến bay theo chặng và ngày (Ví dụ: "Tìm chuyến bay Hà Nội - Quy Nhơn ngày 9/4/2026"). | Câu trả lời không khớp với kỳ vọng. Thay vì liệt kê chuyến bay, AI đưa ra các lựa chọn "dư thừa" hoặc không phù hợp (yêu cầu nhập mã đặt chỗ/số hiệu chuyến bay).         |
| **4\. Khi user MẤT TIN**  | User hỏi các câu không liên quan (Ví dụ: Giải phương trình toán học) hoặc để thời gian chờ quá lâu.       | AI biết từ chối khéo, đề xuất: "Quý khách có muốn hỗ trợ thêm không?", hiển thị nút đánh giá, và cung cấp thông tin liên hệ của Tư vấn viên/Trung tâm CSKH để giải quyết. |

**Nhận xét Path yếu nhất:** Path 3 hiện đang là điểm trừ lớn nhất. Khi người dùng có nhu cầu cơ bản là tra cứu chuyến bay mới, bot không thể xử lý ngôn ngữ tự nhiên để truy xuất dữ liệu mà lại ép người dùng đi vào luồng tra cứu của những người "đã mua vé" (đòi mã PNR/số hiệu).

**2\. Nhận xét Gap Marketing vs Thực tế**

- **Lời hứa (Marketing):** Chatbot NEO giúp thuận tiện tra cứu, giải đáp nhanh chóng (24/7) mọi thắc mắc liên quan đến thông tin hành trình, mua vé, thanh toán và nhiều tính năng khác.
- **Thực tế (Reality):** Bot làm tốt vai trò cung cấp thông tin quy định (hành lý, giấy tờ) và biết cách từ chối câu hỏi ngoài luồng. Tuy nhiên, với tính năng cốt lõi được quảng cáo là "tra cứu hành trình, mua vé", bot lại không thể hiểu được ý định tìm kiếm chuyến bay thông thường bằng ngôn ngữ tự nhiên.
- **Gap (Khoảng cách):** Lời hứa là một trợ lý ảo có thể giúp "mua vé, tra cứu hành trình" linh hoạt, nhưng thực tế trải nghiệm (Test case 1) cho thấy bot hoạt động khá rập khuôn. Nó không thể tự động liệt kê chuyến bay theo ngày giờ mà user yêu cầu, làm gián đoạn hành trình mua vé ngay từ bước khám phá.

**3\. Sketch "Làm tốt hơn" (Cải tiến Path 3: Tra cứu chuyến bay)**

**As-is (Hiện trạng - Chỗ gãy: Trải nghiệm tra cứu bị tắc nghẽn)**

- **User input:** "Tìm chuyến bay từ Hà Nội đến Quy Nhơn trong ngày 9/4/2026" _(Mục đích: Muốn biết các chuyến bay trong ngày)._
- **Bot phản hồi:** "Xin mời quý khách lựa chọn hình thức tra cứu: Tra cứu theo mã đặt chỗ/số vé VÀ Tra cứu theo số hiệu chuyến bay".
- **Đánh giá:** Gãy luồng. User chưa có vé nên không thể có mã đặt chỗ hay số hiệu. Bot đưa ra các lựa chọn không giải quyết được nhu cầu tìm kiếm ban đầu.

**To-be (Đề xuất - Liệt kê thông tin trực quan)**

- **User input:** "Tìm chuyến bay từ Hà Nội đến Quy Nhơn trong ngày 9/4/2026".
- **Bot nhận diện ý định:** Hiểu được Điểm đi (A), Điểm đến (B) và Thời gian (Ngày).
- **Màn hình AI xử lý:** Bot kết nối với cơ sở dữ liệu chuyến bay.
- **Bot phản hồi (Cải tiến):** Bot hiển thị trực tiếp một danh sách (List/Carousel) các chuyến bay từ Hà Nội đi Quy Nhơn trong ngày 9/4/2026, bao gồm: Giờ bay, số hiệu, giá vé dự kiến và kèm theo nút **\[Chọn chuyến bay này\]** hoặc **\[Đặt vé ngay\]**.