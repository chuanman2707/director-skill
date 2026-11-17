# director-skill

Bộ skill đạo diễn toàn diện để thiết kế hình ảnh, phân cảnh điện ảnh và viết prompt video AI (bao gồm chuyên biệt cho cảnh giao đấu/combat). Bộ skill tuân theo chuẩn mở [Agent Skills](https://agentskills.io/specification): mỗi skill là một thư mục có file `SKILL.md` — Claude Code, Codex và Antigravity đều đọc được.

| Skill | Dùng khi |
|---|---|
| [image](skills/image/SKILL.md) | Thiết kế hình ảnh tĩnh, character sheets, bối cảnh, đạo cụ, poster, multi-panel storyboard và keyframe đầu cảnh cho Nano Banana (NB2 / NBP) và GPT Image 2.5 (Flare / Sunburst). |
| [video](skills/video/SKILL.md) | Đạo diễn kịch bản phân cảnh, nhịp dựng điện ảnh (dramaturgy, Murch Rule of Six, 3-detail check, beat map) và viết prompt video cho Seedance 2.5, Kling 3.0, Veo 3.1, Runway, Luma, Sora… |
| [writing-fight-scene-prompts](skills/writing-fight-scene-prompts/SKILL.md) | Viết hoặc sửa prompt cho cảnh đánh nhau, giao đấu, đấu phép (MiniMax H3, Seedance, Kling, Veo…), hoặc khi clip đánh nhau ra chậm, bồng bềnh, đứng im, không có hiệu ứng va chạm. |

## Sáu skill đạo diễn short drama

Các ví dụ Diablo IV lấy số shot từ mục *Breakdown* của *Diablo IV – Announcement Cinematic (BlizzCon 2019)*. Mỗi skill có thêm một cảnh thuộc thể loại khác để thử cùng thủ pháp.

| Khi anh cần | Gọi skill | Đầu ra |
|---|---|---|
| Gài manh mối và chọn lúc tiết lộ | [staging-clues-and-reveals](skills/staging-clues-and-reveals/SKILL.md) | Bảng đối chiếu điều khán giả và nhân vật biết qua từng nhịp |
| Mở tập bằng một hình ảnh báo trước | [directing-cold-opens](skills/directing-cold-opens/SKILL.md) | Phương án dựng mở đầu, cảnh nối và điểm trả lời về sau |
| Tìm đoạn nên giữ, rút hoặc dời | [auditing-emotional-pacing](skills/auditing-emotional-pacing/SKILL.md) | Bản kiểm nhịp cảm xúc gắn với hành động hoặc timecode |
| Cho màu và ánh sáng đổi theo câu chuyện | [designing-color-arcs](skills/designing-color-arcs/SKILL.md) | Kịch bản màu với tác nhân đổi và mốc nối giữa các shot |
| Chỉ đạo hai diễn viên trong cảnh đổi thế chủ động | [directing-two-handers](skills/directing-two-handers/SKILL.md) | Nhịp diễn, tín hiệu cho bạn diễn và điểm đặt máy |
| Ra mắt nhân vật theo từng phần | [staging-character-entrances](skills/staging-character-entrances/SKILL.md) | Shot list cho thấy khán giả nhận ra điều gì ở mỗi hình |

Xem cách chọn và phối hợp các skill trong [AGENTS.md](AGENTS.md).

## Skill theo thể loại

[Phim samurai Nhật Bản](skills/genres/japanese-samurai/) gồm năm skill về bối cảnh và thân phận, môi trường và mỹ thuật, góc máy, không khí và nhịp dựng. Xem [bảng chọn skill theo đầu ra](AGENTS.md#phim-samurai-nhật-bản) để gọi từng skill riêng hoặc phối hợp khi dựng một cảnh.

## Cài đặt

Lấy repo về bằng GitHub CLI.

```bash
gh repo clone chuanman2707/director-skill
```

Chép từng thư mục có `SKILL.md` vào nơi app đọc skill. Với nhóm samurai, chép năm thư mục `samurai-*` bên trong `skills/genres/japanese-samurai/`.

| App | Dùng cho mọi dự án (global) | Chỉ một dự án |
|---|---|---|
| Claude Code | `~/.claude/skills/<tên-skill>/` | `<dự án>/.claude/skills/<tên-skill>/` |
| Codex (CLI, app, IDE) | `~/.agents/skills/<tên-skill>/` (bản cũ: `~/.codex/skills/`) | `<dự án>/.agents/skills/<tên-skill>/` |
| Antigravity | `~/.gemini/config/skills/<tên-skill>/` (bản cũ: `~/.gemini/antigravity/skills/`) | `<dự án>/.agents/skills/<tên-skill>/` |

### Cài cả bộ skill cho cả ba ứng dụng

Windows (PowerShell):

```powershell
$skills = Get-ChildItem -LiteralPath ".\director-skill\skills" -Recurse -File -Filter SKILL.md
foreach ($d in "$HOME\.claude\skills", "$HOME\.agents\skills", "$HOME\.gemini\config\skills") {
  New-Item -ItemType Directory -Force $d | Out-Null
  foreach ($skill in $skills) {
    Copy-Item -LiteralPath $skill.Directory.FullName -Destination $d -Recurse -Force
  }
}
```

macOS / Linux:

```bash
for d in ~/.claude/skills ~/.agents/skills ~/.gemini/config/skills; do
  mkdir -p "$d" || exit 1
  for guide in director-skill/skills/*/SKILL.md director-skill/skills/genres/*/*/SKILL.md; do
    [ -f "$guide" ] || continue
    cp -R "$(dirname "$guide")" "$d/" || exit 1
  done
done
```

### Cài vào 1 dự án cụ thể (Local project cho Antigravity / Codex)

```powershell
New-Item -ItemType Directory -Force ".\.agents\skills" | Out-Null
Get-ChildItem -LiteralPath ".\director-skill\skills" -Recurse -File -Filter SKILL.md | ForEach-Object {
  Copy-Item -LiteralPath $_.Directory.FullName -Destination ".\.agents\skills" -Recurse -Force
}
```

Mở phiên mới để app nạp skill. Các skill tự bật theo ngữ cảnh công việc (tạo ảnh/keyframe → `image`, phân cảnh/quay dựng → `video`, giao đấu/combat → `writing-fight-scene-prompts`), hoặc có thể gọi trực tiếp theo tên skill.

Cập nhật: `git pull` trong thư mục repo rồi chép lại.

## Dùng chung với PanelMint MCP

Khi app AI kết nối PanelMint qua MCP (`https://panelmint.io/mcp`):
- **`image`** hỗ trợ chuẩn hóa prompt tạo nhân vật, bối cảnh, đạo cụ (`create_asset`, `update_asset`) và storyboard tĩnh.
- **`video`** hỗ trợ kiểm soát đường dây cảm xúc, phân cảnh và viết prompt quay dựng (`update_shot`).
- **`writing-fight-scene-prompts`** đảm bảo các shot đánh nhau viết qua `update_shot` tuân thủ đúng nhịp pha đòn và hiệu ứng va chạm 3 lớp. Với MiniMax H3, shot đánh nhau nên chạy trên máy đã nối LoRA `Combat-Base-V2` (xem `skills/writing-fight-scene-prompts/references/model-notes.md`).

## Nguồn & Giấy phép

- `writing-fight-scene-prompts`: Nội bộ dự án (`director-skill`).
- `image` & `video`: Từ bộ *Visual Skills* của **Serge Shima** — [github.com/smixs/visual-skills](https://github.com/smixs/visual-skills), phát hành theo giấy phép **CC BY 4.0** (xem `LICENSE` và `NOTICE` kèm trong từng thư mục skill).
