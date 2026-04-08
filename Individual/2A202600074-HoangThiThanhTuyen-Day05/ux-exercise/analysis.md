# UX exercise — MoMo Moni AI

## Sản phẩm: MoMo — Moni AI Assistant / Quản lý chi tiêu

## Trước khi dùng

### Sản phẩm hứa gì (marketing promise)

- MoMo hiện tự định vị là **"Trợ thủ tài chính với AI"**, hứa AI sẽ giúp người dùng “làm được nhiều hơn với tiền”. Trên landing page, AI được gắn với quản lý chi tiêu, nhập hóa đơn, bảo mật giao dịch, gợi ý tài chính và các tác vụ cá nhân hóa khác.
- Với **quản lý chi tiêu**, MoMo hứa AI sẽ **tự động phân loại giao dịch**, tiết kiệm thời gian ghi chép, giúp người dùng nhìn rõ mình đã tiêu tiền vào đâu.
- Với **nhập hóa đơn**, MoMo hứa chỉ cần chụp ảnh là AI nhận diện thông tin và nhập vào hệ thống trong khoảng 10 giây, không cần nhập tay.

## Sau khi dùng

### Quan sát nhanh về UI/flow AI

- Ở lớp định vị sản phẩm, AI được đưa lên rất mạnh: tên app trên App Store đã là **“MoMo - Trợ Thủ Tài Chính với AI”**.
- Ở lớp task thực tế, AI xuất hiện theo hai kiểu:
  - **AI như một entry point riêng**: Moni / trợ lý chi tiêu / chat để hỏi dữ liệu chi tiêu.
  - **AI nhúng trong flow cũ**: tự động phân loại giao dịch; thêm nút/flow “Nhập hóa đơn siêu tốc”; có bước review trước khi lưu.
- Điều này cho thấy MoMo không chỉ làm chatbot, mà dùng AI như một lớp tự động hóa đè lên các hành vi tài chính quen thuộc.

## 4 paths

### 1. AI đúng

User nói một khoản chi tiêu hợp lý, nằm trong ngữ cảnh tài chính đã khai báo trước đó, ví dụ: chỉ còn 500k trong tháng này rồi ghi nhận một khoản nhỏ như ăn uống, mua nhu yếu phẩm.
Hệ thống tính tiền, lưu giao dịch và gán vào danh mục phù hợp.
User nhìn vào sổ chi tiêu hoặc báo cáo tháng thấy dữ liệu đúng, không cần sửa gì thêm.
UI suy ra: giao dịch được thêm vào ngân sách/thống kê hiện có, category/tag được điền sẵn.

#### Nhận xét

Đây vẫn là path mạnh nhất: khi dữ liệu hợp lý và nằm trong pattern quen thuộc, AI giúp user ghi nhận chi tiêu nhanh, ít thao tác.
Giá trị nằm ở việc giảm nhập tay và tạo cảm giác “app hiểu mình”.

### 2. AI không chắc

User đưa ra một input mơ hồ không rõ ràng khi muốn lưu danh mục chi tiêu ví dụ:

- user nói “tôi đi ăn, đi mua đồ, đi du lịch, đi học hết 500K”

Với trường hợp này, đáng lẽ hệ thống phải nhận ra đây là mơ hồ, nhưng hệ thống lại tự lưu 500K danh mục giải trí mà không hỏi lại, trong khi có nhiều hoạt động chi tiêu

UI hiện tại vì vậy cho cảm giác AI không có trạng thái “không chắc”, dù về logic đây chính là lúc nó nên dừng lại và kiểm tra lại với user.

#### Vấn đề

- Không có bước hỏi lại như:
  - “Khoản này bạn dùng cho nhiều hoạt động, vui lòng cung cấp cụ thể từng khoản để lưu theo từng danh mục, hay bạn muốn lưu chung vào danh mục nào”
- Hệ thống đang hành xử như thể AI luôn chắc chắn, kể cả trong tình huống lẽ ra phải nghi ngờ rất cao.

### 3. AI sai

Trường hợp ví dụ AI sai, khi có sự nhập nhằng xung đột ngữ cảnh.
ví dụ trước đó tôi nói: chỉ có 500K trong tháng này để chi tiếu. Sau đó nói: tôi mua 2 ôtô.

- AI hiểu câu nói thành một giao dịch chi tiêu thực tế,
- tự tính tiền,
- tự lưu vào danh mục,
- trong khi không kiểm tra xem điều đó có hợp lý với ngân sách bạn đã khai báo hay không.

User phát hiện lỗi sau khi thấy giao dịch bị ghi nhận vào hệ thống.
Khi đó user phải quay lại sửa hoặc xóa, thay vì được chặn lỗi ngay từ đầu.
Vấn đề không chỉ là gán sai category, mà là sai ở tầng diễn giải ý định: AI không phân biệt được giữa input cần xác nhận và input có thể commit thẳng.

#### Vấn đề

- Recovery xảy ra sau khi lỗi đã được lưu, tức là quá muộn.
- User phải tự sửa hậu quả thay vì được ngăn lỗi từ đầu.
- Không rõ hệ thống có học từ correction này hay không.
- Đây là lỗi nghiêm trọng hơn lỗi tag sai thông thường, vì nó ảnh hưởng trực tiếp đến độ tin cậy của dữ liệu chi tiêu.

### 4. User mất niềm tin

Sau trải nghiệm như trên, user dễ mất niềm tin vào toàn bộ báo cáo chi tiêu tự động.
Lý do là:

- user đã cung cấp ngữ cảnh rất quan trọng: chỉ còn 500k trong tháng
- nhưng AI vẫn ghi nhận một khoản chi phi lý như mua 2 oto
- và còn không hỏi lại

Khi đó user sẽ đặt câu hỏi:

- AI có thật sự hiểu ngữ cảnh không?
- Các giao dịch khác có đang bị lưu sai không?
- Báo cáo tháng còn đáng tin nữa không?

Nếu không có fallback rõ ràng, user buộc phải:

- kiểm tra lại từng giao dịch,
- sửa thủ công,
- hoặc ngừng tin vào tính năng tự động này.

#### Vấn đề

- Không có escape hatch rõ ràng kiểu:
  - “Luôn hỏi lại khi giao dịch vượt ngân sách”
  - “Chỉ lưu sau khi tôi xác nhận”
  - “Tắt auto-save với các giao dịch bất thường”
- Một khi niềm tin đã giảm, hệ thống chưa cho user cách lấy lại kiểm soát đủ nhanh.

### Path yếu nhất

Path yếu nhất là path 3:

- input mâu thuẫn với ngân sách,
- số tiền có khả năng vượt rất xa hạn mức,
- rủi ro hiểu sai ý user rất cao.

Nhưng thay vì hỏi lại, hệ thống vẫn commit luôn.
Điều đó khiến Path 3 gần như không tồn tại trong trải nghiệm thực tế.
Hệ quả là Path 4 đến rất nhanh: user mất niềm tin vì AI không biết lúc nào nên dừng.

### Gap marketing vs thực tế

Marketing: AI được hứa hẹn như một trợ thủ tài chính thông minh, hiểu ngữ cảnh chi tiêu của user, hỗ trợ quản lý tiền hiệu quả và đáng tin.

Thực tế trải nghiệm của bạn: hệ thống có thể vẫn auto-save ngay cả khi input phi logic so với ngân sách đã biết.

Gap lớn nhất không còn chỉ là “AI đôi khi tag sai”, mà là:

- AI không biết lúc nào cần nghi ngờ chính mình
- và không hỏi lại ở tình huống rủi ro cao

Điều này làm sản phẩm giống một hệ thống tự động hóa cứng nhắc hơn là một “trợ thủ” thực sự hiểu bối cảnh.

### As-is

- User nói: “Tôi chỉ có 500k trong tháng này”
- Sau đó user nói: “Tôi mua 2 oto”
- Hệ thống vẫn tự hiểu đây là một khoản chi hợp lệ
- AI tính tiền và lưu vào danh mục
- Không hỏi lại, không cảnh báo vượt ngân sách, không yêu cầu xác nhận
- User chỉ phát hiện khi nhìn thấy giao dịch/báo cáo bị sai

#### Điểm gãy

- Không phát hiện mâu thuẫn với ngữ cảnh ngân sách
- Không có confidence check
- Không có bước confirm với giao dịch bất thường
- Sai rồi mới bắt user đi sửa

### To-be

- User nói: “Tôi chỉ có 500k trong tháng này”
- Sau đó user nói: “Tôi mua 2 oto”
- Hệ thống phát hiện đây là input bất thường so với ngân sách/thói quen
- Thay vì lưu ngay, AI hiện confirm card:
  - “Khoản chi này có vẻ vượt xa ngân sách bạn đã đặt. Bạn muốn làm gì?”
- Nút:
  - Xác nhận vẫn lưu
  - Sửa lại số tiền / nội dung
  - Bỏ qua
- Nếu user xác nhận thì mới lưu
- Nếu user sửa lại, AI cập nhật theo dữ liệu mới
- Đồng thời hiện feedback:
  - “Mình sẽ hỏi lại ở các khoản chi bất thường tương tự.”

### Thêm gì? Bớt gì? Đổi gì?

Thêm:

- kiểm tra xung đột với ngân sách
- cảnh báo giao dịch bất thường
- confirm-before-save cho khoản chi vượt ngưỡng
- feedback rõ rằng AI đã ghi nhận preference của user

Bớt:

- auto-save trong các case rủi ro cao
- việc để user tự phát hiện lỗi sau khi đã lưu

Đổi:

- từ “cứ hiểu là giao dịch thật và lưu luôn”
- sang “nếu bất thường thì hỏi lại trước khi commit”

### Kết luận ngắn

Trải nghiệm của bạn cho thấy điểm yếu lớn nhất không phải chỉ là AI gán sai danh mục, mà là AI không có cơ chế uncertainty trong tình huống rất rõ ràng là cần xác nhận. Khi bạn đã nói chỉ còn 500k trong tháng, nhưng hệ thống vẫn ghi nhận câu “tôi mua 2 oto” như một khoản chi thật và lưu luôn, thì vấn đề nằm ở khả năng hiểu ngữ cảnh, kiểm soát rủi ro, và bảo vệ niềm tin người dùng. Đây là khoảng cách rất lớn giữa lời hứa “trợ thủ tài chính thông minh” và trải nghiệm thực tế.
