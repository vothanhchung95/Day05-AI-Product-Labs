# Bài tập UX: phân tích sản phẩm AI thật

## Sản phẩm chọn
- **Sản phẩm**: MoMo — Trợ thủ AI Moni  
- **AI feature**: Phân loại chi tiêu, chatbot tài chính  
- **Truy cập**: App MoMo  

---

## Phần 1 — Khám phá

### Trước khi dùng (Marketing nói gì)
- Tự động phân loại chi tiêu thông minh
- Trợ lý tài chính cá nhân
- Gợi ý chi tiêu, tiết kiệm, đầu tư
- Chatbot hỗ trợ tài chính

### Sau khi dùng (Thực tế quan sát)
- AI tự động gán category cho giao dịch
- Không hiển thị mức độ chắc chắn (confidence)
- Không giải thích lý do phân loại
- Không hỏi lại khi không chắc
- Có một số gợi ý tài chính cơ bản

---

## Phần 2 — Phân tích 4 paths

### 1. Khi AI đúng
- User thấy category đã được gán sẵn
- UI hiển thị luôn, không cần confirm
- Không có giải thích

**Nhận xét:**
- Nhanh, mượt
- Tạo cảm giác “AI làm được việc”

---

### 2. Khi AI không chắc
- Hệ thống vẫn gán nhãn như bình thường
- Không hỏi lại
- Không hiển thị lựa chọn thay thế

**Nhận xét:**
- Không phân biệt được case chắc vs không chắc
- Dễ dẫn đến sai sót

---

### 3. Khi AI sai
- User phải tự phát hiện
- Phải chỉnh sửa thủ công
- Không có gợi ý sửa

**Nhận xét:**
- Tốn effort
- Không hỗ trợ user sửa nhanh

---

### 4. Khi user mất tin
- User bỏ qua AI, tự nhập thủ công
- Không có fallback rõ ràng
- Không có cơ chế tăng trust lại

**Nhận xét:**
- AI dễ bị “disable ngầm”
- Trải nghiệm kém dần theo thời gian

---

### Tổng kết
- **Path tốt nhất**: Khi AI đúng (nhanh, mượt)
- **Path yếu nhất**: Khi AI không chắc
- **Gap marketing vs thực tế**:
  - Marketing: AI thông minh, hiểu user
  - Thực tế: AI không thể hiện mức độ chắc chắn, thiếu tương tác

---

## Phần 3 — Sketch “làm tốt hơn”

### Path chọn: Khi AI không chắc

### As-is
User ghi chú chi tiêu  
→ AI tự động gán nhãn  
→ Hiển thị luôn  

❌ Vấn đề: không biết AI có chắc hay không

---

### To-be
User ghi chú chi tiêu  
→ AI gán nhãn + hiển thị **confidence (%)**  

- Nếu confidence ≥ 80%  
  → Hiển thị luôn  

- Nếu confidence < 80%  
  → Hỏi user xác nhận  
  → Đưa 2–3 lựa chọn category  
  → User chọn → lưu lại  

---

### Thay đổi
- **Thêm**: confidence score
- **Thêm**: flow hỏi lại khi không chắc
- **Thêm**: lựa chọn nhanh (quick options)
- **Đổi**: từ auto luôn → có điều kiện

---

## Phần 4 — (Chuẩn bị share)
- Key idea: dùng confidence để điều hướng UX
- Giảm sai → tăng trust → tăng adoption AI

