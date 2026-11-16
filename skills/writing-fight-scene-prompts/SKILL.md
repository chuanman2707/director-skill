---
name: writing-fight-scene-prompts
description: Use when writing, rewriting or reviewing an AI video prompt for a fight, combat, duel, martial-arts, brawl, sword fight or magic clash shot (đánh nhau, giao đấu, cảnh combat, 打斗, 武打, 交手, 对轰) for MiniMax H3, Seedance, Kling, Veo, Hailuo or similar models, or when a generated fight clip looks slow, floaty, static, weak, has no impact effects, or shows two people just holding wrists.
---

# Viết prompt cảnh đánh nhau

Model video làm đúng theo chữ: lực, va chạm và hậu quả không được viết ra thì sẽ không có. Một clip đánh nhau tốt gồm ít pha, mỗi pha có đà → trúng → hiệu ứng → phản ứng → đòn sau, và máy đi theo đòn.

## Cách viết (làm theo thứ tự)

1. **Đếm pha.** Mỗi pha khoảng 3 giây và có đúng một cú chạm chính (một đòn trúng hoặc một lần đỡ nặng). Tối đa 3 pha trong 10 giây. Biên kịch viết nhiều cú chạm hơn thì chọn 3 cú mạnh nhất, gộp phần còn lại thành một câu kết quả, và đề xuất tách shot.
2. **Viết mỗi pha đủ 5 vế**, theo đúng thứ tự:
   `lấy đà (chân, hông, vai)` → `đòn và điểm chạm` → `hiệu ứng tại điểm chạm` → `phản ứng (người văng theo hướng lực, môi trường phản ứng)` → `đòn sau nối vào`.
3. **Mỗi đòn trúng có hiệu ứng môi trường ba lớp:**
   - Tại điểm chạm: một vòng không khí nén trong suốt nổ ra, sóng xung kích, chớp sáng, tia lửa.
   - Quanh người: bụi, nước, mưa, lá bị đẩy ra thành vòng; tóc và vạt áo bị gió giật.
   - Đồ vật trong cảnh: vỡ, cong, gãy, đung đưa.
   - Mức phá huỷ tăng dần, lớn nhất ở pha cuối. Kho từ theo chất liệu: [references/impact-effects.md](references/impact-effects.md).
4. **Mở đầu đang đánh.** Giây 0 đã chuyển động, cú chạm đầu tiên trước giây 1.5.
5. **Ý đồ biến thành động tác.** "Quan sát", "đọc đối thủ", "nạp lực" viết thành một động tác dài khoảng 0.5 giây, ví dụ "nhìn ngón tay hắn siết lại, cúi né ngay trước khi cú đấm bung ra". Cả clip liên tục chuyển động.
6. **Máy đi theo đòn.** Trung cảnh đến toàn cảnh, cách người 3–6 m, thấy cả người hai bên. Máy cầm tay, lia theo hướng đòn, rung một nhịp khi đòn nặng trúng rồi ổn định lại; chuyển động nhanh có nhoè tự nhiên. Đạo diễn ghi "máy cố định, toàn cảnh xa" thì giữ hướng nhìn đó, kéo về 4–6 m, cho máy đi theo, và nêu lý do trong phần giải thích.
7. **Ánh sáng làm động tác đọc được.** Nguồn sáng có trong cảnh (lửa, đèn, sét, đèn lồng) chiếu lên thân người, viền sáng tách người khỏi nền.
8. **Kết khi còn chuyển động.** Khung cuối hai bên vẫn đang giằng co hoặc đang ra đòn. Thoại để sau pha cuối; nếu nhân vật cần đứng nói một lúc, tách thành shot thoại riêng.
9. **Viết theo model.** Theo [references/model-notes.md](references/model-notes.md). Với MiniMax H3, chỉ viết câu khẳng định: không dùng 不要 / 禁止 / 不得. LoRA combat cho H3 cũng ghi ở đó.

## Một pha mẫu (tiếng Trung, model H3)

```
黑煞右脚猛踏竹板、拧腰抡刀，一记全力横劈狠狠砸在林风横架的剑身上：刀剑相撞处一圈透明的压缩空气猛然炸开，
雨滴被冲击波推成一圈向外扩散的水环，林风被震得向后滑出两步，脚下竹板溅起水花，两端灯笼被气浪掀得剧烈摇晃，
镜头随撞击一震再稳住；林风借势旋身，剑尖直刺黑煞空出的左肋。
```

Prompt đầy đủ theo khuôn 8 đoạn, kèm bản trước và sau: [examples/h3-shot53-before-after.md](examples/h3-shot53-before-after.md). Prompt Seedance mẫu nhiều hiệu ứng: [examples/seedance-rooftop-climax.md](examples/seedance-rooftop-climax.md).

## Kiểm trước khi trả prompt

- [ ] Tối đa 3 pha trong 10 giây; nhịp nào bị bỏ thì có đề xuất tách shot.
- [ ] Mỗi pha đủ 5 vế.
- [ ] Mỗi đòn trúng có hiệu ứng không khí nén hoặc sóng xung kích, môi trường phản ứng, và phá huỷ tăng dần.
- [ ] Cú chạm đầu tiên trước 1.5 giây; không có khoảng đứng im.
- [ ] Máy cách 3–6 m, đi theo đòn, rung khi trúng.
- [ ] Khung cuối vẫn đang chuyển động; thoại nằm sau pha cuối.
- [ ] Câu viết theo model (H3: không có phủ định).

## Lỗi hay gặp

| Lỗi | Sửa |
|---|---|
| Nhồi đủ mọi nhịp biên kịch viết (6–8 nhịp / 10 giây) | Chọn 3 pha, gộp phần còn lại, đề xuất tách shot |
| Máy cố định, toàn cảnh 8 m | Đưa về 3–6 m, cầm tay theo đòn |
| "Đứng im quan sát" 1–2 giây | Một cú né có lý do trong khoảng 0.5 giây |
| Đòn trúng mà không có gì xảy ra | Khí nén nổ ra, môi trường phản ứng, đồ vật vỡ |
| Động từ chung chung ("chém ba nhát, động tác mạnh mẽ") | Lấy đà, điểm chạm, hướng văng cụ thể |
| Kết bằng tư thế đứng hoặc quỳ im | Kết giữa lúc giằng co |
| Cảnh đêm tối, chỉ có đèn xa | Nguồn sáng chiếu lên người, có viền sáng |

## Kết quả đo được

A/B trên MiniMax H3, cùng seed, đo mức chuyển động trung bình giữa các khung: prompt cũ 5.3; prompt viết theo skill 9.9; prompt theo skill cộng LoRA Combat-Base-V2 0.65 được 10.7. Người xem chấm: bản theo skill có đòn trúng thật, có né và mảnh vỡ; bản cũ chỉ là hai người đứng giữ cổ tay nhau.
