# HCM-KS26-CNTT1_NhapMonCNTT_Session21_Ex09
# BÀI 9: XÂY DỰNG PROMPT 3 THÀNH PHẦN GIẢI MÃ THÔNG BÁO LỖI TRẠM SẠC CÙNG TRỢ LÝ AI

**Họ và tên:** Phạm Thành Đạo  
**Lớp:** HCM-KS26-CNTT1  
**Môn học:** Nhập môn Công nghệ thông tin  

---

# PHẦN 1: THIẾT KẾ PROMPT 3 THÀNH PHẦN CHUẨN HÓA

## Câu 1. Phân tích nguyên nhân vì sao câu hỏi chung chung khiến AI đưa ra câu trả lời sai lệch

Câu hỏi: *"AI ơi phần mềm trạm sạc của tôi bị hỏng rồi làm sao đây?"* là một câu hỏi quá chung chung, không cung cấp đủ thông tin kỹ thuật để AI xác định chính xác vấn đề.

Cụ thể, câu hỏi còn thiếu những thông tin quan trọng như:

- **Ngữ cảnh:** Không cho biết đang sử dụng hệ thống VoltCharge, trụ sạc số 04 hay hệ điều hành Windows 11.
- **Thông báo lỗi:** Không cung cấp nội dung lỗi tiếng Anh xuất hiện trên màn hình Terminal.
- **Tác vụ đang thực hiện:** Không nói rõ phần mềm đang khởi động, ghi dữ liệu hay thực hiện chức năng nào.
- **Yêu cầu cụ thể:** Không hướng dẫn AI cần phân tích nguyên nhân, dịch lỗi hay đưa ra cách khắc phục.

Khi thiếu những dữ liệu trên, AI không có đủ căn cứ để xác định nguyên nhân thực tế. Vì vậy, AI có thể tự suy đoán và đưa ra những thông tin không chính xác. Hiện tượng này được gọi là **AI Hallucination (ảo giác AI)**.

Trong tình huống trên, AI đã phỏng đoán rằng trạm sạc gặp sự cố phần cứng và khuyên tháo vỏ sắt để kiểm tra dây điện. Tuy nhiên, nhật ký lỗi thực tế lại cho thấy đây là lỗi quyền truy cập file của phần mềm.

**Kết luận:** Để hạn chế AI Hallucination, người dùng cần cung cấp đầy đủ ngữ cảnh, sao chép chính xác thông báo lỗi và đưa ra yêu cầu cụ thể. AI chỉ nên được xem là công cụ hỗ trợ phân tích, không phải nguồn thông tin tuyệt đối chính xác.

## Câu 2. Soạn thảo Prompt 3 Thành phần hoàn chỉnh

Dưới đây là câu Prompt được xây dựng theo công thức: **Context → Raw Error → Instruction**.

### [CONTEXT] – Ngữ cảnh

Tôi là nhân viên kỹ thuật đang trực ca đêm tại hệ thống Kiosk nạp năng lượng thông minh VoltCharge ở Bến xe Miền Đông.

- Thiết bị: Trụ sạc nhanh VoltCharge số 04.
- Hệ điều hành: Windows 11.
- Tình trạng: Trụ sạc đột ngột dừng cung cấp điện cho xe taxi điện.
- Tác vụ: Phần mềm điều khiển ControllerDaemon khởi động nhưng bị lỗi và tự động dừng hoạt động.
- Mục tiêu: Xác định nguyên nhân lỗi phần mềm và tìm cách khắc phục an toàn để hệ thống có thể hoạt động trở lại.

### [RAW ERROR] – Lỗi nguyên văn

Đây là nội dung nhật ký lỗi được ghi nhận trực tiếp trên màn hình Terminal:

```text
[TERMINAL ERROR LOG - VOLTCHARGE CHARGER #04]
2026-09-21 21:15:30 [FATAL] ControllerDaemon failed to start.
System.UnauthorizedAccessException: Access to the path 'C:\Program Files\VoltCharge\data\session.log' is denied.
   at [System.IO].FileStream.ValidateFileHandle(SafeFileHandle handle)
   at VoltCharge.Core.SessionManager.Initialize()
InnerException: None. Process terminated with exit code 5 (0x00000005).
Suggestion: Run the application with elevated administrator privileges or verify NTFS file permissions.
```

### [INSTRUCTION] – Yêu cầu

Hãy đóng vai một trợ lý kỹ thuật có kinh nghiệm về hệ điều hành Windows và phần mềm quản lý trạm sạc.

Tôi cần bạn thực hiện các yêu cầu sau:

1. Dịch thông báo lỗi tiếng Anh sang tiếng Việt đơn giản, dễ hiểu đối với một nhân viên kỹ thuật mới.
2. Phân tích nguyên nhân gốc rễ khiến phần mềm không thể khởi động.
3. Đưa ra 3 bước khắc phục cụ thể trên Windows 11, tập trung vào quyền Administrator và quyền ghi file của thư mục `data`.
4. Giải thích rõ từng bước cần thực hiện và cảnh báo những thao tác có thể gây mất an toàn cho hệ thống.
5. Không tự suy đoán lỗi phần cứng khi nhật ký chưa có bằng chứng. Nếu có thông tin chưa chắc chắn, hãy nói rõ và hướng dẫn cách kiểm tra.

Hãy trình bày bằng tiếng Việt bình dân, có ví dụ cụ thể và ưu tiên giải pháp an toàn, dễ thực hiện.

---

# PHẦN 2: GIẢI MÃ LỖI VÀ KỊCH BẢN KHẮC PHỤC

## Câu 3. Dịch và giải thích nguyên nhân gốc rễ của lỗi UnauthorizedAccessException

### 1. Dịch thông báo lỗi

Thông báo:

`System.UnauthorizedAccessException: Access to the path 'C:\Program Files\VoltCharge\data\session.log' is denied.`

Dịch sang tiếng Việt:

**Lỗi không được phép truy cập: Hệ thống từ chối quyền truy cập vào đường dẫn `C:\Program Files\VoltCharge\data\session.log`.**

Nói một cách dễ hiểu, phần mềm VoltCharge đang muốn tạo hoặc ghi thông tin vào file `session.log` để lưu lại hoạt động của trạm sạc. Tuy nhiên, Windows không cho phép phần mềm thực hiện thao tác này vì tài khoản hoặc tiến trình đang chạy không có đủ quyền truy cập.

### 2. Giải thích các thông tin liên quan

- **UnauthorizedAccessException:** Lỗi xảy ra khi chương trình cố truy cập tài nguyên nhưng không có đủ quyền được cấp.
- **Access is denied:** Windows từ chối cho phép chương trình truy cập hoặc ghi dữ liệu.
- **Program Files:** Đây là thư mục hệ thống thường được bảo vệ, nơi lưu trữ các ứng dụng đã cài đặt.
- **session.log:** File nhật ký dùng để ghi lại thông tin phiên hoạt động của phần mềm.
- **ControllerDaemon failed to start:** Tiến trình điều khiển không thể khởi động thành công.
- **Exit code 5 (0x00000005):** Mã lỗi thể hiện thao tác bị từ chối quyền truy cập trong tình huống này.

### 3. Nguyên nhân gốc rễ

Nguyên nhân chính là phần mềm VoltCharge đang cố gắng ghi dữ liệu vào file `session.log` nằm trong thư mục `Program Files`, nhưng tiến trình chạy phần mềm không có đủ quyền ghi tại vị trí đó.

Windows bảo vệ thư mục `Program Files` để tránh các chương trình hoặc người dùng không được phép tự ý thay đổi dữ liệu hệ thống.

Do đó, khi phần mềm cố ghi nhật ký nhưng bị Windows từ chối, quá trình khởi tạo SessionManager thất bại. Tiếp theo, ControllerDaemon không thể khởi động và chương trình kết thúc với mã lỗi 5.

**Kết luận:** Đây chủ yếu là lỗi phân quyền truy cập file trên Windows, không có bằng chứng trong nhật ký cho thấy dây điện, bộ sạc hoặc linh kiện phần cứng bị hỏng. Vì vậy, không nên tháo vỏ trạm sạc để kiểm tra dây điện chỉ dựa trên thông báo lỗi này.

## Câu 4. Đưa ra 3 bước xử lý cụ thể trên Windows 11

### Bước 1. Khởi chạy phần mềm bằng quyền Administrator

1. Tại máy tính điều khiển trạm sạc, tìm biểu tượng phần mềm VoltCharge.
2. Nhấn chuột phải vào biểu tượng phần mềm.
3. Chọn **Run as administrator**.
4. Nếu Windows hiện cửa sổ User Account Control (UAC), kiểm tra đúng ứng dụng rồi xác nhận bằng tài khoản quản trị được cấp phép.
5. Kiểm tra xem phần mềm có khởi động bình thường và còn xuất hiện lỗi cũ hay không.

**Giải thích:** Run as administrator giúp chương trình chạy với quyền cao hơn tài khoản thông thường. Điều này có thể giải quyết lỗi nếu nguyên nhân là tiến trình không có đủ quyền cần thiết.

Lưu ý: Chỉ thực hiện khi được người phụ trách hệ thống cho phép. Không tự ý dùng tài khoản quản trị không được cấp quyền.

### Bước 2. Kiểm tra và cấp quyền ghi cho thư mục data

Nếu chạy bằng Administrator vẫn gặp lỗi, cần kiểm tra quyền truy cập của thư mục `data`.

1. Mở File Explorer.
2. Truy cập đường dẫn:

`C:\Program Files\VoltCharge\`

3. Tìm thư mục `data`, nhấn chuột phải và chọn **Properties**.
4. Chọn tab **Security**.
5. Chọn tài khoản hoặc nhóm người dùng được phần mềm sử dụng để chạy, sau đó kiểm tra quyền được cấp.
6. Nếu thiếu quyền ghi, nhờ quản trị viên cấp quyền **Write** hoặc **Modify** phù hợp cho đúng tài khoản hoặc tài khoản dịch vụ của phần mềm.

**Giải thích:** Quyền Write cho phép ghi dữ liệu vào thư mục, còn Modify cho phép đọc, ghi, sửa và xóa dữ liệu trong phạm vi được cấp. Phần mềm cần quyền phù hợp để tạo hoặc cập nhật file `session.log`.

**Lưu ý an toàn:** Không cấp quyền Full Control cho Everyone hoặc Users một cách tùy tiện. Chỉ cấp quyền tối thiểu cần thiết cho đúng tài khoản chạy dịch vụ VoltCharge. Không thay đổi quyền của toàn bộ thư mục `Program Files`.

### Bước 3. Khởi động lại và kiểm tra hoạt động của trạm sạc

Sau khi được cấp quyền phù hợp:

1. Đóng phần mềm VoltCharge nếu đang mở.
2. Khởi động lại phần mềm theo đúng quy trình vận hành của đơn vị.
3. Kiểm tra xem ControllerDaemon đã khởi động thành công hay chưa.
4. Kiểm tra nhật ký `session.log` để xác nhận phần mềm có thể ghi dữ liệu.
5. Thực hiện kiểm tra trạng thái trạm sạc theo quy trình kỹ thuật được nhà sản xuất phê duyệt.

**Kết quả mong đợi:**

- Phần mềm không còn xuất hiện lỗi `UnauthorizedAccessException`.
- ControllerDaemon khởi động thành công.
- File `session.log` được tạo hoặc cập nhật bình thường.
- Trạng thái trạm sạc được hệ thống ghi nhận ổn định.

Nếu lỗi vẫn tiếp tục xuất hiện, cần lưu lại nhật ký mới và báo cho quản trị viên hoặc bộ phận kỹ thuật của nhà sản xuất để kiểm tra cấu hình quyền, tài khoản chạy dịch vụ và chính sách bảo mật.

**Lưu ý quan trọng:** Vì đây là trạm sạc đang phục vụ phương tiện thực tế, không tự ý khởi động lại dịch vụ điều khiển, thử sạc hoặc thay đổi cấu hình khi chưa được người phụ trách vận hành cho phép. Việc kiểm tra phải tuân thủ quy trình an toàn của đơn vị.

## Câu 5. Bẫy an ninh: Cách xử lý chuỗi API_KEY trước khi gửi cho AI

Giả sử trong nhật ký lỗi có chứa chuỗi:

`API_KEY: volt_secret_token_889922`

Kỹ thuật viên tuyệt đối không được sao chép nguyên văn chuỗi này và gửi lên ChatGPT hoặc Gemini.

### Cách xử lý đúng

Trước khi gửi nội dung nhật ký cho AI, cần tìm và che toàn bộ thông tin bí mật. Có thể thay thế bằng một chuỗi giữ chỗ như sau:

**Trước khi che:**

```text
API_KEY: volt_secret_token_889922
```

**Sau khi che:**

```text
API_KEY: [REDACTED]
```

Hoặc:

```text
API_KEY: your_api_key_here
```

Sau đó mới sao chép phần nhật ký đã được làm sạch để gửi cho AI phân tích.

### Vì sao phải che thông tin bí mật?

API Key là một loại khóa xác thực được sử dụng để cho phép ứng dụng hoặc người dùng truy cập vào dịch vụ và tài nguyên nhất định.

Nếu để lộ API Key, người khác có thể lợi dụng khóa này để truy cập trái phép vào hệ thống, sử dụng dịch vụ, lấy dữ liệu hoặc thực hiện những hành động vượt quá quyền được phép.

Ngoài API Key, kỹ thuật viên cũng không được gửi những thông tin nhạy cảm như:

- Mật khẩu tài khoản quản trị.
- Mật khẩu cơ sở dữ liệu.
- Mã OTP xác thực.
- Token đăng nhập và khóa truy cập.
- Thông tin cá nhân hoặc dữ liệu khách hàng không cần thiết cho việc xử lý lỗi.

Nếu vô tình để lộ một API Key thật, cần báo ngay cho người phụ trách bảo mật để thu hồi hoặc vô hiệu hóa khóa cũ và tạo khóa mới theo quy trình của đơn vị.

**Kết luận:** Luôn kiểm tra và loại bỏ thông tin bí mật trước khi gửi nhật ký lỗi cho AI. Chỉ cung cấp những dữ liệu kỹ thuật cần thiết để AI có thể phân tích vấn đề mà không làm lộ thông tin quan trọng của hệ thống.

---

# KẾT LUẬN

Qua bài học, em hiểu được cách sử dụng công thức Prompt 3 thành phần gồm **Ngữ cảnh (Context), Lỗi nguyên văn (Raw Error) và Yêu cầu (Instruction)** để giúp AI hiểu đúng vấn đề và đưa ra câu trả lời phù hợp hơn.

Đồng thời, em biết cách đọc và giải mã lỗi `UnauthorizedAccessException`, nhận diện nguyên nhân liên quan đến quyền truy cập file trên Windows và đưa ra hướng xử lý phù hợp.

Đặc biệt, khi sử dụng AI trong công việc kỹ thuật, cần tuân thủ ba nguyên tắc an toàn:

1. Không sao chép và chạy mù quáng các câu lệnh do AI đề xuất.
2. Cung cấp đầy đủ ngữ cảnh, kiểm chứng thông tin để hạn chế hiện tượng AI Hallucination.
3. Tuyệt đối không gửi API Key, mật khẩu, mã OTP hoặc thông tin bí mật lên công cụ AI.

AI là công cụ hỗ trợ đắc lực cho kỹ thuật viên, nhưng mọi thao tác trên hệ thống thực tế vẫn cần được kiểm tra và thực hiện theo đúng quy trình an toàn.
