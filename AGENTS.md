# Chọn skill đạo diễn theo yêu cầu

Người dùng có thể mô tả việc cần làm bằng tiếng Việt hoặc gọi trực tiếp bằng `$tên-skill`. Chọn theo **đầu ra họ cần**, mở `SKILL.md` ở hàng tương ứng và áp dụng vào truyện, cảnh, shot list hoặc bản dựng họ đưa. Với một yêu cầu hẹp, có thể dùng riêng một skill.

| Khi người dùng cần… | Skill cần mở | Đầu ra |
|---|---|---|
| Thiết kế nhân vật, bối cảnh, poster, khung storyboard tĩnh hoặc keyframe | [image](skills/image/SKILL.md) | Prompt ảnh mô tả chủ thể, bố cục và các chi tiết cần giữ nhất quán |
| Chuyển kịch bản thành phân cảnh, chọn cỡ cảnh và chuyển động máy, hoặc viết prompt video theo model | [video](skills/video/SKILL.md) | Bản phân cảnh, shot list hoặc prompt chuyển động theo yêu cầu |
| Viết hoặc sửa prompt cho cảnh giao đấu, nhất là khi chuyển động thiếu lực hoặc khó đọc trên màn hình | [writing-fight-scene-prompts](skills/writing-fight-scene-prompts/SKILL.md) | Prompt cảnh giao đấu theo nhịp hành động, phản ứng và chuyển động máy |
| **1. Mở tập bằng hình ảnh báo trước.** Cho thấy một khoảnh khắc ở cuối tập nhưng vẫn giữ được câu hỏi dẫn vào chuyện | [directing-cold-opens](skills/directing-cold-opens/SKILL.md) | Chuỗi shot mở màn, điểm trở về mạch chính và cảnh trả lời câu hỏi |
| **2. Gài manh mối và chọn lúc tiết lộ.** Cần quyết định khán giả biết bí mật trước, sau hay cùng lúc với nhân vật | [staging-clues-and-reveals](skills/staging-clues-and-reveals/SKILL.md) | Bảng theo từng nhịp ghi ai đang nghi, ai đã biết chắc và bằng chứng nào cho phép họ biết |
| **3. Kiểm tra nhịp cảm xúc.** Đã có kịch bản, shot list hoặc bản dựng và cần tìm đoạn lê thê, lặp ý hay cắt quá sớm | [auditing-emotional-pacing](skills/auditing-emotional-pacing/SKILL.md) | Đề xuất giữ, rút hoặc dời từng nhịp, gắn với hành động hoặc timecode nếu có |
| **4. Thiết kế màu theo bước ngoặt.** Ánh sáng hoặc vật mang màu cần đổi đúng lúc nhân vật nhận ra điều gì đó, hay cần khớp màu qua hai góc quay | [designing-color-arcs](skills/designing-color-arcs/SKILL.md) | Kịch bản màu ghi nguồn sáng, tác nhân gây đổi và mốc màu cần khớp |
| **5. Đạo diễn cảnh hai người đổi thế chủ động.** Cần chỉ đạo ai đang thuyết phục ai, tín hiệu nào khiến bạn diễn đáp lại và khi nào nên chuyển góc | [directing-two-handers](skills/directing-two-handers/SKILL.md) | Nhịp diễn cho cả hai người, hành động làm đổi thế và góc máy đọc được sự thay đổi |
| **6. Dàn cảnh ra mắt nhân vật.** Muốn khán giả dần nhận ra danh tính, vai trò hoặc tầm ảnh hưởng của một người qua cách họ xuất hiện | [staging-character-entrances](skills/staging-character-entrances/SKILL.md) | Shot list ghi mỗi hình hé thêm điều gì và phản ứng nào xác nhận điều đó |

## Ví dụ chọn và phối hợp

- **“Mở tập bằng cảnh con gái xé lá thư. Cuối tập mới cho biết ai viết.”** Dùng `staging-clues-and-reveals` để chốt lúc tên người viết được lộ, rồi dùng `directing-cold-opens` để chọn phần lá thư được thấy ở đầu tập.
- **“Khán giả đã biết mặt bà chủ quán. Cho họ thấy cả phòng đợi bà gật đầu.”** Dùng `staging-character-entrances` để lộ vai trò qua phản ứng của cả phòng. Nếu trọng tâm chuyển sang cuộc mặc cả giữa bà và một nhân viên, dùng `directing-two-handers` cho cuộc đối đáp đó.
- **“Chia cảnh chờ tin thành các shot, rồi viết prompt cho Kling.”** Dùng `video` để lên shot list và viết prompt. Nếu người dùng đã có bản dựng và hỏi nên giữ hay rút khoảng im trước tiếng chuông, dùng `auditing-emotional-pacing` để trả lời trực tiếp.

## Phim samurai Nhật Bản

Bộ skill nằm trong [`skills/genres/japanese-samurai/`](skills/genres/japanese-samurai/). Khi làm một cảnh samurai Nhật Bản, chọn theo quyết định đạo diễn đang cần chốt. Một địa danh Nhật hay một thanh kiếm xuất hiện trong cảnh chưa đủ để gọi cả bộ.

| Khi cần quyết định | Gọi skill | Đầu ra |
|---|---|---|
| Cảnh diễn ra thời nào? Thân phận, lễ nghi hay một lời thề khiến nhân vật được phép làm gì? | [`samurai-boi-canh`](skills/genres/japanese-samurai/samurai-boi-canh/SKILL.md) | Brief lịch sử và quan hệ, kèm chi tiết đưa được lên hình |
| Cổng, bậc đá, cửa sổ hoặc đạo cụ nằm ở đâu? Người xem còn nhận ra lối đi khi máy đảo góc nhờ mốc nào? | [`samurai-moi-truong`](skills/genres/japanese-samurai/samurai-moi-truong/SKILL.md) | Sơ đồ không gian, vật liệu và mốc giữ liên tục giữa các góc |
| Máy đứng về phía ai? Khán giả cần thấy ánh mắt, bàn tay hay người đang chờ ở hậu cảnh? | [`samurai-goc-may`](skills/genres/japanese-samurai/samurai-goc-may/SKILL.md) | Shot list có cỡ cảnh, hướng nhìn, điểm nét và lý do chuyển máy |
| Muốn chuyển từ dè chừng sang nhận ra nhau bằng ánh lửa, bóng tối, âm nền hoặc khoảng lặng? | [`samurai-khong-khi`](skills/genres/japanese-samurai/samurai-khong-khi/SKILL.md) | Chỉ dẫn ánh sáng, màu và âm thanh theo diễn tiến cảm xúc |
| Đã có chất liệu cảnh và cần chọn lúc cắt, giữ ánh mắt bao lâu hoặc trả về phản ứng nào sau một câu thoại? | [`samurai-nhip-dung`](skills/genres/japanese-samurai/samurai-nhip-dung/SKILL.md) | Bản nhịp dựng với điểm vào, điểm cắt và phản ứng cần giữ |

Ví dụ, với yêu cầu **“Lên shot list cảnh một người đưa thư nhận ra thầy cũ ở bến đò”**, nếu vị trí hai người còn bỏ ngỏ, dùng `samurai-moi-truong` để đặt cọc buộc đò và lối lên bờ, rồi dùng `samurai-goc-may` để chọn lúc lộ gương mặt người thầy. Nếu đã có bản dựng và chỉ cần biết nên giữ cái cúi đầu bao lâu, vào thẳng `samurai-nhip-dung`. Khi đích đến là prompt ảnh hoặc video, chuyển các quyết định đã chốt sang `image` hoặc `video`.
