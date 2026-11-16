# director-skill

Bộ skill đạo diễn toàn diện để thiết kế hình ảnh, phân cảnh điện ảnh và viết prompt video AI (bao gồm chuyên biệt cho cảnh giao đấu/combat). Bộ skill tuân theo chuẩn mở [Agent Skills](https://agentskills.io/specification): mỗi skill là một thư mục có file `SKILL.md` — Claude Code, Codex và Antigravity đều đọc được.

| Skill | Dùng khi |
|---|---|
| [image](skills/image/SKILL.md) | Thiết kế hình ảnh tĩnh, character sheets, bối cảnh, đạo cụ, poster, multi-panel storyboard và keyframe đầu cảnh cho Nano Banana (NB2 / NBP) và GPT Image 2.5 (Flare / Sunburst). |
| [video](skills/video/SKILL.md) | Đạo diễn kịch bản phân cảnh, nhịp dựng điện ảnh (dramaturgy, Murch Rule of Six, 3-detail check, beat map) và viết prompt video cho Seedance 2.5, Kling 3.0, Veo 3.1, Runway, Luma, Sora… |
| [writing-fight-scene-prompts](skills/writing-fight-scene-prompts/SKILL.md) | Viết hoặc sửa prompt cho cảnh đánh nhau, giao đấu, đấu phép (MiniMax H3, Seedance, Kling, Veo…), hoặc khi clip đánh nhau ra chậm, bồng bềnh, đứng im, không có hiệu ứng va chạm. |

## Cài đặt

Lấy repo về (repo private, cần quyền đọc):

```bash
gh repo clone chuanman2707/director-skill
```

Rồi chép các thư mục con trong `skills/` vào nơi app đọc skill:

| App | Dùng cho mọi dự án (global) | Chỉ một dự án |
|---|---|---|
| Claude Code | `~/.claude/skills/<tên-skill>/` | `<dự án>/.claude/skills/<tên-skill>/` |
| Codex (CLI, app, IDE) | `~/.agents/skills/<tên-skill>/` (bản cũ: `~/.codex/skills/`) | `<dự án>/.agents/skills/<tên-skill>/` |
| Antigravity | `~/.gemini/config/skills/<tên-skill>/` (bản cũ: `~/.gemini/antigravity/skills/`) | `<dự án>/.agents/skills/<tên-skill>/` |

### Cài cả bộ 3 skill (Global cho cả 3 app)

Windows (PowerShell):

```powershell
$src = ".\director-skill\skills\*"
foreach ($d in "$HOME\.claude\skills", "$HOME\.agents\skills", "$HOME\.gemini\config\skills") {
  New-Item -ItemType Directory -Force $d | Out-Null
  Copy-Item -Recurse -Force $src $d
}
```

macOS / Linux:

```bash
for d in ~/.claude/skills ~/.agents/skills ~/.gemini/config/skills; do
  mkdir -p "$d" && cp -R director-skill/skills/* "$d"/
done
```

### Cài vào 1 dự án cụ thể (Local project cho Antigravity / Codex)

```powershell
New-Item -ItemType Directory -Force ".\.agents\skills" | Out-Null
Copy-Item -Recurse -Force ".\director-skill\skills\*" ".\.agents\skills\"
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
