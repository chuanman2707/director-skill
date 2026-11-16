# Ghi chú theo model

## MiniMax H3 (ComfyUI, MiniMaxH3ReferenceToVideo)

- **Không có negative prompt.** Pipeline nào lọc câu chỉ dẫn (PanelMint) sẽ xoá mọi mệnh đề chứa 绝对, 禁止, 严禁, 不要, 不得, 绝不, 切勿, 不允许, 不出现… Vì vậy chỉ viết câu khẳng định:
  - «画面铺满整个画幅» thay cho «không viền đen»;
  - «画面中只有A和B两人» thay cho «không thêm người»;
  - «最后一帧动作仍在进行» thay cho «không đứng im».
- **Ảnh tham chiếu** gọi bằng tag (`@图片N` trong PanelMint, `<Picture N>` trong node gốc). Ảnh đã cho mặt và trang phục, nên prompt chỉ tả vị trí, hướng và vật cầm tay.
- **Khuôn 8 đoạn tiếng Trung** (PanelMint): 【格式】【主体】【动作】【环境】【镜头】【画面质感】【时间轴】【声音与约束】. Các pha đánh nằm trong 【时间轴】, mỗi mốc giây một pha. Hiệu ứng môi trường viết ngay trong câu của pha đó, rồi tóm lại ở 【环境】.
- **Ngôn ngữ.** Hướng dẫn ComfyUI của H3 khuyên viết tiếng Anh. Tiếng Trung đã chạy tốt ở A/B (giữ khi pipeline dùng tiếng Trung). Đổi ngôn ngữ thì A/B riêng, mỗi lần đổi một biến.
- **LoRA combat (đã chọn): JOKER141 MiniMax-H3-Combat-Base-V2.**
  - File `H3_Combat_V2.safetensors`, 155 110 280 byte, SHA256 `5b3edb09e9d6029439badf9bc9db4ba4a355ae679b0810888de82c4793c0bac8`.
  - URL: https://huggingface.co/JOKER141/MiniMax-H3-Combat-Base-V2/resolve/7b3c5b7157d66517f5bd8f5d3fa8fd2c66bc4d11/H3_Combat_V2.safetensors
  - Strength **0.65**, không cần trigger (`prfight2` cho đòn mạnh hơn). Cắm `LoraLoaderModelOnly` giữa `UNETLoader` (ref2va) và node nhận MODEL (BasicGuider, hoặc `ModelSamplingMiniMaxH3` nếu workflow có).
  - Chạy được trên checkpoint pruned int8 (log "208 patches attached", không có `lora key not loaded`).
  - **Chỉ bật cho shot có đánh nhau.** Shot đi lại, mở cửa, cưỡi ngựa hay thoại thì strength 0.
  - Tác giả khuyên sampler `res_multistep` + `simple` hoặc `euler` + `beta`.
- **SMACK Beta 2 (LeechTM, Apache-2.0)** cho va chạm nặng hơn, nhưng cảnh trôi khỏi ảnh tham chiếu và LoRA có trộn sẵn hiệu ứng máu. Không dùng cho phim có trẻ em.
- **Thời lượng** 5–15 giây; một clip 10 giây gồm 3 pha là vừa.

## Seedance 2.0 (Dreamina)

- Hiểu prompt dài có cấu trúc. **Danh sách phủ định có tác dụng** (「负面提示词：不要…」), nên được dùng để chặn cắt cảnh, mặt bị đổi, CG rẻ tiền.
- Chịu được nhiều nhịp hơn H3 (5 đoạn trong 10 giây), nhưng mỗi đoạn vẫn cần đủ 5 vế và hiệu ứng môi trường.
- Viết rõ khung đầu (ảnh 1 là giây 0), A trái, B phải, ngoại hình để phân biệt hai bên, và khung cuối «仍在角力，不摆结束pose».
- Mẫu đầy đủ: [../examples/seedance-rooftop-climax.md](../examples/seedance-rooftop-climax.md).

## Kling, Veo, Hailuo, model khác

- Áp nguyên cách viết của SKILL.md, viết bằng tiếng Anh, giữ hai người đánh nhau và khoá bên trái / phải cho từng người.
- Chuyển động rất nhanh dễ làm méo mặt: cần giữ mặt thì kéo máy gần hơn ở khoảnh khắc đó.
- Model có negative prompt thì đưa phần «không muốn» vào đó, giữ prompt chính toàn câu khẳng định.
