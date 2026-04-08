# BÀI TẬP UX: PHÂN TÍCH TRỢ LÝ ẢO NEO (VIETNAM AIRLINES)

## 1. Phân tích 4 Paths (Framework AI UX)

| Path | Mô tả trải nghiệm | Phản ứng của hệ thống & UI                                                                                                             |
| :--- | :--- |:---------------------------------------------------------------------------------------------------------------------------------------|
| **1. Khi AI ĐÚNG** | Tra cứu thông tin tĩnh (lịch bay, tiêu chuẩn hành lý, mã đặt chỗ PNR).| Trình bày biểu mẫu gọn gàng; hiển thị nút xác nhận và các bước tiếp theo logic.                                                        |
| **2. Khi AI KHÔNG CHẮC** | User nhập câu hỏi mơ hồ hoặc chứa từ lóng. | Sử dụng "Hội thoại dẫn dắt" (Guided Conversation).                       |
| **3. Khi AI SAI** | Phản hồi thông tin sai lệch hoặc không thể xử lý tác vụ giao dịch phức tạp (đổi tên, hoàn vé). | **(Yếu nhất)**: AI đẩy trách nhiệm cho user bằng cách cung cấp văn bản hướng dẫn dài dòng và yêu cầu thoát chat để gửi email thủ công. |
| **4. Khi user MẤT TIN** | User thất vọng sau nhiều lần AI không hiểu hoặc gặp lỗi kỹ thuật. | Cung cấp nút "Gặp tư vấn viên". Tuy nhiên, thường bị nghẽn (tư vấn viên bận) và mất hoàn toàn bối cảnh hội thoại trước đó.             |

*   **Path yếu nhất:** **Path 3 (Khi AI sai/thất bại)**. Quy trình sửa lỗi tên sai trên vé hiện đang bị "gãy" khi buộc người dùng phải rời bỏ kênh số để quay lại kênh truyền thống (Email/Hotline) với thời gian chờ đợi lâu.

## 2. Nhận xét Gap Marketing vs Thực tế
*   **Lời hứa (Marketing):** Là "Trợ lý ảo thông minh" sử dụng Machine Learning để cá nhân hóa, sẵn sàng giải đáp "mọi thắc mắc" và đồng hành 24/7.
*   **Thực tế (Reality):** Hoạt động chủ yếu như một "siêu menu" dựa trên quy tắc (rule-based). Khả năng xử lý ngôn ngữ tự nhiên còn hạn chế; nhiều tính năng quan trọng vẫn yêu cầu can thiệp thủ công từ con người thay vì thực thi tự động.
*   **Gap:** Khoảng cách lớn nằm ở tính **"Thực thi"**. Marketing tạo kỳ vọng về một người bạn hành trình năng động, nhưng thực tế user chỉ dùng bot để đọc hướng dẫn rồi tự đi làm thủ công ở kênh khác.

## 3. Sketch "Làm tốt hơn" (Cải tiến Path 3: Sửa lỗi tên)

### **As-is (Hiện tại - Chỗ gãy: Thoát kênh)**
*   **Màn hình 1:** User báo sai tên -> Bot trả về block text 5-7 dòng quy định sửa tên
*   **Màn hình 2:** Bot hiện thông tin Email và Hotline. Kết thúc hội thoại chat.
*   **Ngoài App:** User mở ứng dụng Email, chụp ảnh hộ chiếu, soạn nội dung, gửi và chờ 24-48h.
*   *Đánh dấu gãy: Bước thoát khỏi Chatbot để đi gửi Email.*

### **To-be (Đề xuất - Sửa lỗi tại chỗ)**
*   **Màn hình 1:** Bot nhận diện ý định sửa tên -> Hiện nút.
*   **Màn hình 2 (AI xử lý):** Tích hợp công nghệ OCR tự động so khớp tên trên ảnh và tên trên vé.
*   **Màn hình 3:** Bot xác nhận: "NEO đã so khớp thành công. Lỗi này được sửa miễn phí. Bạn có muốn cập nhật ngay?" -> Nút [Xác nhận cập nhật].
*   **Màn hình 4:** Thông báo thành công & gửi vé mới ngay trong cửa sổ chat.
*   *Cải tiến: Giữ user ở lại 1 kênh duy nhất, dùng AI để thực thi tác vụ thay vì chỉ hướng dẫn.*

***
