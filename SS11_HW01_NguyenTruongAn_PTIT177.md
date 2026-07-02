# Bài 1: Phân Tích & Lựa Chọn Phương Án Tạo Mã Nguồn

## 1. Phương án lựa chọn tối ưu nhất

**Đáp án được chọn: Phương án B**
> "Đóng vai Senior Java Developer. Nhiệm vụ: Viết class PaymentValidator kiểm tra tính hợp lệ của thẻ tín dụng. Ngữ cảnh: Hệ thống E-commerce, cần validate trước khi gửi API thanh toán. Ràng buộc: Dùng Java 17, triển khai thuật toán Luhn, ném ra ngoại lệ IllegalArgumentException nếu thẻ rỗng hoặc chứa chữ cái. Định dạng: Chỉ trả về mã nguồn Java trong một code block, không giải thích."

**Lý do chọn (dựa trên cấu trúc 5 thành phần của một Prompt chuẩn):**
Phương án B phát huy hiệu quả tối đa vì đã cung cấp đầy đủ và rõ ràng các thành phần cần thiết để định hướng AI sinh ra kết quả chính xác nhất:

* **Role (Vai trò):** "Đóng vai Senior Java Developer" -> Thiết lập ngữ cảnh chuyên môn cao, giúp AI sinh ra code tối ưu, tuân thủ best practices của Java (SOLID, Clean Code), thay vì code chỉ ở mức chạy được.
* **Task (Nhiệm vụ):** "Viết class PaymentValidator kiểm tra tính hợp lệ của thẻ tín dụng" -> Xác định rõ mục tiêu cốt lõi cần thực hiện.
* **Context (Ngữ cảnh):** "Hệ thống E-commerce, cần validate trước khi gửi API thanh toán" -> Cung cấp thông tin môi trường hoạt động để AI hiểu rõ tính chất quan trọng của module, từ đó cẩn thận hơn trong việc xử lý bảo mật và tính chính xác.
* **Constraints (Ràng buộc):** "Dùng Java 17, triển khai thuật toán Luhn, ném ra ngoại lệ IllegalArgumentException nếu thẻ rỗng hoặc chứa chữ cái" -> Đây là điểm quan trọng nhất. Các ràng buộc về phiên bản ngôn ngữ, thuật toán cụ thể và cách xử lý edge cases (thẻ rỗng, chứa chữ cái) giúp thu hẹp phạm vi sáng tạo của AI, đảm bảo code sinh ra đáp ứng đúng nghiệp vụ và dễ dàng tích hợp vào hệ thống hiện tại.
* **Format (Định dạng đầu ra):** "Chỉ trả về mã nguồn Java trong một code block, không giải thích" -> Đảm bảo kết quả trả về sạch sẽ, lập trình viên có thể copy-paste trực tiếp vào dự án mà không cần lọc bỏ những lời chào hỏi hay giải thích rườm rà của AI, giúp tiết kiệm thời gian.

---

## 2. Phân tích lỗ hổng của các phương án bị loại trừ

### Phương án A
>
> "Viết cho tôi một class Java tên là PaymentValidator để kiểm tra số thẻ tín dụng bằng thuật toán Luhn. Code ngắn gọn thôi nhé."

* **Thiếu ngữ cảnh và ràng buộc cụ thể:** Prompt quá chung chung. AI có thể sinh ra code chạy được thuật toán Luhn nhưng lại không xử lý các trường hợp ngoại lệ cơ bản (như đầu vào là null, chuỗi rỗng, hoặc chứa ký tự không hợp lệ).
* **Thiếu định dạng:** AI có thể mất thời gian sinh ra những đoạn giải thích dài dòng không cần thiết đi kèm với code.
* **Rủi ro sai lệch và kém an toàn:** Lời nhắc "Code ngắn gọn thôi nhé" có thể khuyến khích AI bỏ qua các bước kiểm tra an toàn (validation) quan trọng, dẫn đến mã nguồn kém chất lượng, dễ gặp lỗi runtime (ví dụ: NullPointerException) khi đưa vào dự án thực tế.

### Phương án C
>
> "Tôi cần một đoạn code kiểm tra thẻ tín dụng. Hãy viết bằng Java và sinh thêm cả database SQL để lưu thông tin thẻ. Nhớ hướng dẫn tôi cách cài đặt database và kết nối JDBC luôn nhé."

* **Ôm đồm, sai lệch mục tiêu (Scope Creep):** Mục tiêu ban đầu của task chỉ là viết một class kiểm tra tính hợp lệ của thẻ (PaymentValidator). Việc yêu cầu AI sinh thêm database schema, hướng dẫn cài đặt và cấu hình JDBC làm cho scope của prompt bị phình to quá mức, đi chệch hoàn toàn khỏi mục tiêu cốt lõi.
* **Rủi ro bảo mật nghiêm trọng:** Yêu cầu "lưu thông tin thẻ" (đặc biệt là số thẻ tín dụng nguyên bản) vào database thông thường (SQL) mà không đề cập đến mã hóa hay tokenization là vi phạm nghiêm trọng tiêu chuẩn bảo mật thanh toán (PCI-DSS). AI có thể vô tình sinh ra code tiếp tay cho việc lưu trữ dữ liệu nhạy cảm một cách thiếu an toàn.
* **Rủi ro ảo tưởng (Hallucination) cao:** Việc yêu cầu hướng dẫn cài đặt DB và kết nối JDBC khi không cung cấp ngữ cảnh về hệ quản trị CSDL cụ thể (MySQL, PostgreSQL, Oracle, v.v.) hay framework dự án đang dùng sẽ khiến AI phải tự đoán. Điều này dễ dẫn đến việc AI sinh ra những đoạn mã cấu hình hoặc thư viện không tương thích với stack công nghệ hiện tại của dự án TechShop.
