# Thần Dụ Kể Chuyện (Story Oracle) —— Tiện Ích Mở Rộng Cho SillyTavern

> **Nguồn gốc / Upstream Repository:** [namelessone88/story-oracle](https://github.com/namelessone88/story-oracle)  
> *Bản Việt hóa hoàn chỉnh cho tiện ích mở rộng Story Oracle (Thần Dụ Kể Chuyện) trong SillyTavern.*

Một bảng điều khiển bên có thể kéo thả linh hoạt: kết nối trực tiếp với endpoint tương thích **OpenAI** tùy chỉnh của bạn để hỏi đáp LLM về diễn biến cốt truyện *đang diễn ra*.  
Mọi trao đổi diễn ra trong **cửa sổ độc lập, lịch sử riêng biệt** — **hoàn toàn không làm ảnh hưởng đến cuộc trò chuyện chính**, có thể dọn dẹp hoặc xóa bất kỳ lúc nào.

---

## 🌟 6 Chức Năng Cốt Lõi (Chuyển đổi qua biểu tượng trên đỉnh)

- 💬 **Trò chuyện thường (Chat)** —— Hỏi đáp về tình tiết cốt truyện: *"Tại sao cô ấy lại hành động như vậy?", "Hiện tại hảo cảm của nhân vật là bao nhiêu?"*.
- 🩺 **Chẩn đoán (Diagnose)** —— Kiểm tra và sửa chữa biến trạng thái MVU (khi chỉ số / thanh trạng thái hiển thị sai lệch).
- 📖 **Sách thế giới (Lorebook)** —— Tra cứu Lorebook hoặc yêu cầu AI **trực tiếp chỉnh sửa** nội dung Lorebook cho bạn.
- 🧭 **Tham mưu cốt truyện (Advisor)** —— Cùng lên ý tưởng hướng đi tiếp theo và **âm thầm dẫn dắt** cuộc trò chuyện chính (bao gồm cốt truyện dài nhiều nhịp "Hồi/Arc" và "Chuỗi nhịp/Sequence").
- ✨ **Hiệu chỉnh (Fix/Polish)** —— Khử sạch "vị AI" trong câu trả lời mới nhất chỉ với 1 click (chỉ định thủ công hoặc tự động kích hoạt mỗi lượt).
- 🎭 **Xưởng nhân vật (Character Forge)** —— Trò chuyện vài câu để mài giũa nhân vật từ con số không thành thiết lập hoàn chỉnh, ghi vào Persona hoặc mục NPC trong Lorebook.

---

## 📌 Điểm Nổi Bật Của Các Bản Cập Nhật Gần Đây

- **v1.84.0**: Tối ưu hóa cầu nối cơ sở dữ liệu (Database Bridge), hỗ trợ tùy chọn giữ lại khối dẫn dắt khi gửi tới mô hình chính; cập nhật nhãn ngôn ngữ.
- **v1.83.0**: Hỗ trợ đồng ghi MVU với các kịch bản khác (tránh việc xung đột biến làm hủy toàn bộ lượt chẩn đoán).
- **v1.82.0**: Xưởng nhân vật mặc định chỉ nạp các mục Lorebook đang bật; bổ sung bộ đếm dung lượng token trực quan.
- **v1.79.0**: Thêm chế độ "chạm chọn" (Tap-select) trên thiết bị di động khi hiệu chỉnh từng đoạn văn.
- **v1.77.x**: Bổ sung chế độ Mẫu tùy chỉnh (Custom Template) cho Hiệu chỉnh; tối ưu cơ chế nắn chỉnh và chẩn đoán MVU; sửa lỗi tương thích với các plugin bộ nhớ.
- **v1.74.x**: Bổ sung tính năng tự động thử lại khi chẩn đoán thất bại; cảm biến kết thúc nhịp (Beat Detection) cho Chuỗi dẫn dắt.
- **v1.72.0**: Ra mắt Chuỗi dẫn dắt (Sequence Guidance) — lên kế hoạch toàn bộ hành trình dài và thúc đẩy từng nhịp mà không tốn thêm token gọi mô hình.
- **v1.67.x**: Tự động kiểm tra thể trạng bản vá JSONPatch và nắn chỉnh lỗi cú pháp phổ biến của mô hình trước khi ghi vào MVU.
- **v1.55.x**: Ra mắt Bộ chỉnh sửa biến (Variable Editor 🎛) và Khóa biến / Bộ sửa đổi (Variable Modifiers 🔒).

---

## 📥 Cài Đặt & Mở Tiện Ích

Đặt toàn bộ thư mục `story-oracle/` vào thư mục tiện ích mở rộng bên thứ ba của SillyTavern, sau đó làm mới trình duyệt:

- **Phiên bản ST mới**: `SillyTavern/data/<tên-người-dùng>/extensions/story-oracle/` (mặc định là `default-user`)
- **Phiên bản ST cũ**: `SillyTavern/public/scripts/extensions/third-party/story-oracle/`

Mở **Menu Đũa phép** (biểu tượng 🪄 cạnh khung nhập liệu) → **Story Oracle (Thần Dụ Kể Chuyện)**.  
Để thao tác nhanh hơn, bạn có thể bật *"Hiển thị nút phím tắt trên thanh nhập liệu chat"* trong Cài đặt, một biểu tượng mặt trăng 🌙 sẽ xuất hiện cạnh khung chat để bật/tắt cửa sổ chỉ với một cú nhấp.

### 🔔 Thông Báo Cập Nhật (Từ v1.38)

Mỗi khi mở cửa sổ Story Oracle, hệ thống sẽ tự động kiểm tra phiên bản mới từ GitHub một lần (sau mỗi lần làm mới trang):
- Khi có bản cập nhật mới, biểu tượng **⋯ / ⚙** trên thanh tiêu đề và nhóm **Cập nhật** trên cùng của bảng Cài đặt sẽ hiển thị **chấm đỏ**.
- Trong bảng cài đặt sẽ xuất hiện thông báo "Phát hiện phiên bản mới vX.Y.Z" cùng nút **"Cập nhật ngay"**.
- Bấm vào nút này để tải bản mới thông qua cơ chế cập nhật tiện ích của SillyTavern. Sau khi tải thành công, trang sẽ tự động làm mới sau **5 giây** để áp dụng (bạn có thể bấm vào thông báo để hủy tự động làm mới nếu muốn tiếp tục phiên làm việc).
- **Lưu ý**: Tự động cập nhật yêu cầu tiện ích được cài qua tính năng "Tải tiện ích mở rộng" của SillyTavern bằng liên kết GitHub. Nếu cài đặt thủ công bằng cách sao chép thư mục, bạn có thể cập nhật trong phần Quản lý tiện ích mở rộng hoặc tải file mới về ghi đè.
- **Quyền riêng tư**: Quá trình kiểm tra chỉ đọc file số phiên bản công khai trên GitHub, hoàn toàn không gửi bất kỳ dữ liệu cá nhân nào; nếu kết nối thất bại sẽ âm thầm bỏ qua. Bạn có thể tắt tính năng này trong phần Cài đặt bất kỳ lúc nào.

---

## ⚙️ Cài Đặt Kết Nối

Bấm biểu tượng **⋯ Thêm** trên thanh tiêu đề → ⚙ **Cài đặt**. Có 2 phương thức kết nối chính:

1. **Kết nối trực tiếp (Direct - Mặc định)**:
   - Điền URL Endpoint (ví dụ: `https://your-proxy.com/v1`, hệ thống sẽ tự động nối `/chat/completions`), API Key và Tên mô hình.
   - **Chuyển tiếp qua backend SillyTavern (Tránh lỗi CORS)** ✅: Bật mục này nếu gặp lỗi `CORS / failed to fetch`. Yêu cầu sẽ được máy chủ SillyTavern gửi hộ, vượt qua rào cản hạn chế tên miền của trình duyệt mà không cần tạo profile kết nối riêng. Danh sách mô hình cũng được lấy thông qua backend.
   - **Giữ nguyên địa chỉ URL (Không tự động thêm /v1)**: Dành cho các trạm trung gian có cấu trúc đường dẫn đặc thù. Khi bật, hệ thống sẽ gửi chính xác theo URL bạn nhập.
   - **Lưu cấu hình kết nối**: Cho phép lưu Endpoint / Key / Model thành các bản lưu có tên để chuyển đổi nhanh giữa các nhà cung cấp dịch vụ khác nhau.

2. **Hồ sơ kết nối (Profile)**:
   - Sử dụng trực tiếp cấu hình kết nối đã lưu sẵn trong SillyTavern. Yêu cầu sẽ tự động đi qua backend SillyTavern mà không bao giờ bị CORS chặn.
   - Lưu ý: Nếu hồ sơ không có API Key riêng, ST sẽ dùng chung key của kết nối đang kích hoạt.

3. **Tham số bổ sung (Extra Parameters)**:
   - Cho phép tùy biến **Tham số thân yêu cầu** (gửi kèm JSON/YAML), **Loại trừ tham số**, và **Tiêu đề yêu cầu bổ sung (Headers)**.
   - Ứng dụng tiêu biểu: Tắt chuỗi suy nghĩ (Thinking Chain) đối với các trạm trung gian của DeepSeek để tiết kiệm token và thời gian phản hồi:
     ```yaml
     enable_thinking: false
     ```

Các tùy chọn phổ biến khác: Temperature, Max Tokens, **Độ sâu ngữ cảnh** (số lượng tin nhắn gần nhất gửi kèm, `-1` là toàn bộ, `0` là không gửi tin nhắn cũ), nạp thẻ nhân vật, và System Prompt tùy chỉnh. Chế độ thường mặc định gửi kèm trạng thái biến thời gian thực (`stat_data`) để trả lời chính xác các câu hỏi về chỉ số.

---

## 🔓 Phá Hạn Tích Hợp (Built-in Jailbreak)

Nếu mô hình thường xuyên từ chối trả lời, thuyết giáo, hoặc bỏ qua các tình tiết nhạy cảm, bạn có thể sử dụng mục **Jailbreak tích hợp** trong menu Preset hoàn thành của Cài đặt:

> **🔓 Sơ Tâm Phá Hạn 1.2 (Tác giả: Sơ Ngộ / ChuYu)**

- **Cơ chế bọc ngoài**: Không ghi đè System Prompt của Story Oracle mà bọc bên ngoài khung phân tích, giúp giữ nguyên toàn bộ khả năng định dạng cấu trúc của các chế độ.
- **Mặc định**: Chỉ áp dụng cho chế độ [Trò chuyện thường]. Bạn có thể bật cho các chế độ khác trong phần cài đặt của từng chế độ nếu cần (ngoại trừ Chẩn đoán vì chế độ này cần độ chính xác cơ học tuyệt đối).

---

## 💬 Chế Độ Trò Chuyện Thường (Chat)

Chế độ mặc định dùng để phân tích cốt truyện, tâm lý nhân vật và diễn biến. System Prompt được tái tạo theo ngữ cảnh mới nhất của cuộc trò chuyện tại thời điểm gửi tin.

---

## 🩺 Chế Độ Chẩn Đoán (Diagnose - MVU)

Chuyên dụng để sửa chữa và đồng bộ các biến trạng thái trong khuôn khổ MVU (MagVarUpdate):
- Story Oracle đọc quy tắc MVU của thẻ nhân vật, biến hiện tại (`stat_data`), và khối `<UpdateVariable>` trong phản hồi mới nhất để đưa ra bản vá hiệu chỉnh an toàn.
- Bên dưới phản hồi sẽ có nút **"Áp dụng sửa chữa vào trạng thái"** (chạy qua kênh xử lý của chính MVU) kèm nút **"Hoàn tác"**.

### Các Tính Năng Nâng Cao Của Chẩn Đoán:
1. **Kiểm tra và tự động nắn chỉnh bản vá (Tự động kích hoạt)**:
   - Trước khi nộp bản vá cho MVU, hệ thống tự động sửa các lỗi cú pháp thường gặp của mô hình: từ đồng nghĩa động từ chuyển thành `replace`, bỏ dấu gạch chéo thừa ở cuối đường dẫn, chuyển `delta` dạng chuỗi `"+5"` thành số thực, loại bỏ khoảng trắng thừa trong thẻ `<JSONPatch >`, và lược bỏ các mục không hợp lệ có nguy cơ làm MVU từ chối toàn bộ khối lệnh.
2. **Báo cáo nguyên nhân chính xác**:
   - Khi không có giá trị nào thay đổi, hệ thống sẽ phân tích rõ nguyên nhân (đường dẫn không tồn tại, giá trị đã khớp từ trước, kiểu dữ liệu không tương thích, hoặc danh sách không cho phép mở rộng theo schema của thẻ).
3. **Chẩn đoán tự động (AUTO)**:
   - Khi bật tùy chọn này, mỗi phản hồi mới trong cuộc trò chuyện chính sẽ được kiểm tra và áp dụng bản vá tự động dưới nền nếu biến chưa được cập nhật chính xác.
4. **Tự động thử lại khi thất bại (Auto-retry)**:
   - Tự động chạy lại lượt chẩn đoán nếu mô hình trả về nội dung rỗng, sai định dạng, hoặc gặp lỗi mạng (có thể tùy chỉnh số lần thử lại).
5. **Đồng ghi với các kịch bản khác (v1.83.0)**:
   - Cho phép phối hợp nhịp nhàng với các kịch bản chạy sau lượt chat khác mà không làm hủy toàn bộ bản vá khi biến bị thay đổi giữa chừng.
6. **Bộ chỉnh sửa biến (Variable Editor 🎛)**:
   - Giao diện trực quan dạng cây thư mục và phân trang: cho phép trực tiếp sửa đổi các giá trị số, chuỗi, công tắc bật/tắt của MVU mà không tốn token gọi mô hình.
7. **Khóa biến & Bộ sửa đổi (Variable Modifiers 🔒)**:
   - Cho phép khóa cố định một biến ở giá trị nhất định, hoặc áp dụng quy tắc tăng/giảm tự động mỗi lượt (±X) và giới hạn chặn trên/dưới.

---

## 📖 Chế Độ Sách Thế Giới (Lorebook)

Hỗ trợ hỏi đáp về Lorebook hoặc yêu cầu AI **trực tiếp chỉnh sửa** nội dung Lorebook:
- **Chọn sách & Chọn mục thông minh 🪄**: Cho phép chọn toàn bộ hoặc lọc từng mục cụ thể gửi cho AI. Tính năng thông minh 🪄 cho phép ra lệnh bằng ngôn ngữ tự nhiên (ví dụ: *"Chọn toàn bộ các mục về bối cảnh chiến tranh"*).
- **Các thao tác chỉnh sửa**: Hỗ trợ 4 hành động thông qua khối `<LorebookEdit>`:
  - `create`: Tạo mục mới.
  - `edit`: Ghi đè toàn bộ mục.
  - `patch`: Sửa đổi một đoạn văn dựa trên điểm neo văn bản.
  - `delete`: Xóa mục.
- **Kiểm tra trước khi áp dụng (Pre-check)**: Hiển thị trạng thái của từng mục cần sửa, phát hiện điểm neo không khớp hoặc trùng lặp trước khi thực sự ghi vào Lorebook.
- **Đo lường token**: Cảnh báo màu đỏ khi dung lượng nội dung gửi đi vượt quá 100.000 token để tránh tràn ngữ cảnh.

---

## 🧭 Chế Độ Tham Mưu Cốt Truyện (Story Advisor)

Cùng lên ý tưởng phát triển cốt truyện và âm thầm dẫn dắt diễn biến trong đoạn chat chính:

1. **Phương án đơn bước (Single-step Plan)**:
   - Đề xuất các hướng đi khả thi dưới dạng thẻ `<StoryPlan>` (Mục tiêu + Dấu hiệu khởi đầu + Điểm tương thích).
   - Chọn cường độ (**Chỉ đặt nền móng** / **Tiến triển tự nhiên** / **Kích hoạt nhanh chóng**) và bấm **[Bắt đầu dẫn dắt]**.
   - Hướng dẫn sẽ được bí mật đưa vào prompt của SillyTavern để định hướng cho AI mà người chơi không cần trực tiếp can thiệp.
2. **Chỉnh sửa chỉ thị dẫn dắt (✏️)**:
   - Cho phép trực tiếp sửa đổi nội dung văn bản dẫn dắt gửi tới mô hình chính theo ý muốn.
3. **Hồi cốt truyện (Story Arc - Dẫn dắt dài hạn)**:
   - Thiết lập tuyến truyện dài nhiều nhịp. Hỗ trợ 2 chế độ: **Minh bạch** (người chơi xem được chỉ thị từng nhịp) và **Hộp mù** (chỉ thấy mục tiêu, ẩn giấu tình tiết bất ngờ).
4. **Chuỗi nhịp dẫn dắt (Sequence Guidance - v1.72.0)**:
   - Lên kế hoạch toàn bộ hành trình dài thành danh sách các nhịp tuần tự. Chuyển đổi giữa các nhịp mà không cần gọi lại mô hình, hoàn toàn miễn phí token.
5. **Cảm biến kết thúc nhịp (Beat Detection)**:
   - Tự động phát hiện khi một tình tiết trong kế hoạch đã thực sự diễn ra trong đoạn chat và gợi ý hoàn thành nhịp.

---

## ✨ Chế Độ Hiệu Chỉnh (Reply Fixer)

Chuyên dụng để "tút tát" lại câu trả lời mới nhất của AI: loại bỏ văn phong sáo rỗng, đối thoại gượng gạo, văn phong học thuật khô khan, hoặc sửa các chi tiết sai lệch:
- **Nguyên tắc an toàn**: Kết quả hiệu chỉnh luôn được tạo dưới dạng một **Swipe mới** (lượt vuốt mới), bản gốc vẫn được lưu nguyên vẹn ở lượt vuốt trước đó. Các khối biến `<UpdateVariable>` và thanh trạng thái được bảo toàn nguyên vẹn.
- **3 Cách sử dụng**:
  1. **Thủ công**: Mô tả yêu cầu chỉnh sửa bằng ngôn ngữ tự nhiên (ví dụ: *"Viết lại đoạn đối thoại này cho tự nhiên hơn, bỏ câu cuối"*).
  2. **Khử vị AI**: Tích chọn các mục tiêu muốn dọn dẹp (văn mẫu, đối thoại cơ học, mô tả rườm rà, v.v.) và chọn mức độ hiệu chỉnh.
  3. **Mẫu tùy chỉnh (Custom Template - v1.77.0)**: Áp dụng một khuôn mẫu riêng biệt cho mỗi tin nhắn (ví dụ: tự động dịch toàn bộ lời thoại sang ngôn ngữ khác, tạo khung bong bóng thoại đẹp mắt).
- **Tự động nhận diện cấu trúc**: Tự động nhận diện phần nội dung văn xuôi chính để chỉnh sửa và giữ nguyên các khối trạng thái/bảng biểu xung quanh.

---

## 🎭 Chế Độ Xưởng Nhân Vật (Character Builder)

Mài giũa một nhân vật từ con số không thành thiết lập hoàn chỉnh chỉ qua vài câu trò chuyện:
- **Mục tiêu chế tác**:
  - **Mục NPC Lorebook**: Tạo một nhân vật phụ hoàn chỉnh ghi vào Sách thế giới.
  - **Persona người dùng (Cướp lời)**: Nhân cách người chơi mà AI có thể hỗ trợ hành động/đối thoại.
  - **Persona người dùng (Không cướp lời)**: Nhân cách người chơi thuần túy, AI tuyệt đối không nói thay bạn.
- **Lựa chọn các phần nội dung (Chips)**:
  - Thông tin cơ bản, Ngoại hình, Bối cảnh trải nghiệm, Quan hệ nhân vật, Chân dung tính cách, Cách nói chuyện, Động cơ mục tiêu, Nhân cách tầng sâu, Gợi ý chống hiểu sai của AI.
  - Tùy chọn nâng cao: Đa diện mạo, Tương phản lời nói - hành động, Ẩn dụ đắt giá.
- **Quy trình chế tác**:
  - Phỏng vấn viên trao đổi ngắn gọn để thu thập thông tin còn thiếu.
  - Xuất bản tóm tắt thông tin sơ bộ.
  - Bấm **[Tạo nhân vật]** để tiến hành đúc thành hình hoàn chỉnh.
  - Hỗ trợ xem trước bản gốc, tinh giản gọn gàng (✂️), chỉnh sửa từng chi tiết và ghi trực tiếp vào Persona hoặc Lorebook.

---

## 📜 Lịch Sử & Thao Tác Trò Chuyện

- **Lịch sử riêng biệt cho từng phòng**: Mỗi chế độ (Trò chuyện, Chẩn đoán, Lorebook, Tham mưu, Hiệu chỉnh, Xưởng nhân vật) sở hữu lịch sử độc lập, không lẫn lộn với nhau và được lưu trữ theo từng cuộc trò chuyện của SillyTavern.
- **Tóm tắt vận hành (📜)**: Cho phép ghi lại bối cảnh cốt truyện chính để gửi kèm cho Story Oracle trong các cuộc trò chuyện dài.
- **Xuất / Nhập đối thoại (📥/📤)**: Xuất lịch sử thảo luận thành file Markdown lưu trữ cục bộ hoặc nạp lại để tiếp tục làm việc.

---

## 🔌 Giao Diện Phát Triển Mở Rộng (Hook API)

Từ phiên bản 1.21.0, Story Oracle cung cấp giao diện lập trình ổn định `window.StoryOracleAPI` cùng sự kiện `story-oracle-ready`:
- Hỗ trợ các nhà phát triển plugin bên thứ ba đăng ký thêm các chế độ mới thông qua `registerMode(spec)`.
- Cung cấp cơ chế đọc chỉ thị dẫn dắt qua `api.guidance.getActive()`.
- Tạo điều kiện thuận lợi cho việc tích hợp với các tiện ích mở rộng cốt truyện khác như World Engine, Bách Bảo Thư (BaiBaiBook), Tiểu Bạch X (LittleWhiteBox), và Cơ sở dữ liệu SP.

---

## 📄 Bản Quyền & Trích Dẫn Nguồn Gốc

- **Dự án gốc**: [namelessone88/story-oracle](https://github.com/namelessone88/story-oracle) (Tác giả: `built for Prince`)
- **Bản quyền & Phát triển**: Tuân thủ giấy phép phân phối của dự án gốc. Mọi đóng góp, báo lỗi hoặc yêu cầu tính năng xin vui lòng tham khảo kho lưu trữ gốc hoặc liên hệ cộng đồng phát triển.
