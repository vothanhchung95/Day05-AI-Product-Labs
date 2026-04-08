# BÀI TẬP UX: PHÂN TÍCH TRỢ LÝ ẢO NEO (VIETNAM AIRLINES)

## 1. Phân tích 4 Paths (Framework AI UX)

| Path | Mô tả trải nghiệm | Phản ứng của hệ thống & UI |
| :--- | :--- | :--- |
| **1. Khi AI ĐÚNG** | Tra cứu thông tin hành lý ký gửi theo hạng vé | Đưa ra thông tin chính xác, hỏi kĩ thông tin hạng vé, chuyến bay mới trả lời
| **2. Khi AI KHÔNG CHẮC** | User nhập câu hỏi: Tôi muốn mang chất lỏng lên máy bay | Chỉ đưa ra thông tin các chất lỏng được phép mang lên máy bay, còn các chất cấm như xăng, dầu, axit thì không nói gì
| **3. Khi AI SAI** | User nói rằng muốn hoàn tiền vé với ngữ cảnh: Vé đã bay cách đây 1 tháng, User không lên chuyến bay, vé siêu tiết kiệm | NEO tiếp tục hỏi mã vé để kiểm tra thông tin, nhưng thực tế, câu trả lời ngay và luôn là KHÔNG ĐƯỢC HOÀN TIỀN |
| **4. Khi user MẤT TIN** | User thất vọng sau nhiều lần AI không hiểu hoặc gặp lỗi kỹ thuật. | Tiếp tục đưa ra thông báo thủ tục hoàn vé |

*   **Path yếu nhất:** **Path 3 (Khi AI sai/thất bại)**. NEO chưa trả lời thành công về chính sách hoàn vé, còn bị ảo giác, mặc dù ngữ cảnh rất rõ ràng.
## 2. Nhận xét Gap Marketing vs Thực tế
*   **Lời hứa (Marketing):** Là "Trợ lý ảo thông minh" sử dụng Machine Learning để cá nhân hóa, sẵn sàng giải đáp "mọi thắc mắc" và đồng hành 24/7.
*   **Thực tế (Reality):** Hoạt động chủ yếu dựa trên quy tắc (rule-based). Khả năng xử lý ngôn ngữ tự nhiên còn hạn chế; nhiều tính năng quan trọng vẫn yêu cầu can thiệp thủ công từ con người thay vì thực thi tự động. Ảo giác, đôi khi lỗi markdown, các chữ dính sát nhau không có dấu cách, còn mơ hồ.
*   **Gap:** Khoảng cách lớn nằm ở tính **"Thực thi"**. Marketing tạo kỳ vọng về một người bạn hành trình năng động, nhưng thực tế user chỉ dùng bot để đọc hướng dẫn rồi tự đi làm thủ công ở kênh khác. --> KHÔNG GIÚP ÍCH ĐC GÌ

## 3. Sketch "Làm tốt hơn" (Cải tiến Path 3: Sửa lỗi tên)

### **As-is (Hiện tại - Chỗ gãy: Thoát kênh)**

**Tình huống:** User muốn hoàn tiền vé máy bay (vé siêu tiết kiệm, chuyến bay đã diễn ra 1 tháng trước, user không lên chuyến).

**User Journey:**
1. **User**: "Tôi muốn hoàn tiền vé của mình" (ngữ cảnh: vé siêu tiết kiệm, không lên chuyến)
2. **NEO**: "Vâng, tôi sẽ giúp bạn. Vui lòng cung cấp mã vé của bạn để kiểm tra thông tin."
3. **User**: Nhập mã vé
4. **NEO**: "Cảm ơn. Tôi đang kiểm tra... Hành lý của bạn có thể được hoàn tiền trong 5-7 ngày làm việc."
5. **User**: Thất vọng - "Nhưng vé KO ĐƯỢC HOÀN TIỀN???" → **Rời khỏi chat, liên hệ Call Center**

**Vấn đề (Pain Point):**
- NEO không nhận ra ngữ cảnh "vé siêu tiết kiệm" = KHÔNG HOÀN VÉ
- Ảo giác dữ liệu: trả lời sai (nói về hoàn hành lý thay vì hoàn vé)
- User mất niềm tin → chuyển sang kênh khác (Call Center) → tốn chi phí & không giải quyết tức thì
- **Kết quả:** Customer Dissatisfaction ↑, Cost/Call ↑

---

### **To-be**

**Tình huống:** GIỐNG (vé siêu tiết kiệm, chuyến bay 1 tháng trước, chưa lên)

**Improved User Journey:**
1. **User**: "Tôi muốn hoàn tiền vé của mình"
2. **NEO** (Ngay lập tức nhận ra ngữ cảnh từ booking history):
   - "Mã vé: XX123456 - **Vé Siêu Tiết Kiệm**"
   - "⚠️ **Thông báo quan trọng:** Vé loại này **KHÔNG ĐỦ ĐIỀU KIỆN HOÀN TIỀN** sau khi chuyến bay diễn ra."
   - ✅ Nêu rõ lý do: "Vé siêu tiết kiệm chỉ được hoàn đổi (không hoàn tiền) theo chính sách"
   - 💡 **Đề xuất thay thế:**
     - "Bạn có thể **đổi sang chuyến bay khác** (miễn phí nếu trong 30 ngày)"
     - "Hoặc liên hệ Call Center để thảo luận các tùy chọn khác"
3. **User**: Hiểu rõ → Có thể accept hoặc chọn đổi chuyến ngay trong chat
4. **Kết quả**: ✅ Transparent, ✅ Self-service, ✅ Không phải chuyển kênh

---

**Điểm cải tiến chính:**
| Khía cạnh | As-is | To-be |
|:--- |:--- |:--- |
| **Context Awareness** | ❌ Bỏ qua loại vé | ✅ Phát hiện "Siêu Tiết Kiệm" |
| **Honesty** | ❌ Ảo giác dữ liệu | ✅ Nói rõ "KHÔNG HOÀN TIỀN" |
| **User Agency** | ⚠️ User bị động | ✅ Cung cấp lựa chọn thay thế |
| **Channel Retention** | ❌ Rời chat → Call Center | ✅ Giải quyết trong chat |
| **Emotional Outcome** | 😠 Thất vọng | 😌 Rõ ràng & công bằng |

***
Ngoài ra nên cải thiện UI, đối với các câu hỏi mập mờ như mang chất lỏng, chất rắn, những thứ mơ hồ thì phải đưa ra cả thông tin được phép và không được phép.