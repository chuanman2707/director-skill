# director-skill

Đây là bộ skill đạo diễn để viết prompt cho video AI. Skill theo chuẩn mở [Agent Skills](https://agentskills.io/specification): mỗi skill là một thư mục có file `SKILL.md`. Claude Code, Codex và Antigravity đều đọc được.

| Skill | Dùng khi |
|---|---|
| [writing-fight-scene-prompts](skills/writing-fight-scene-prompts/SKILL.md) | Viết hoặc sửa prompt cho cảnh đánh nhau, giao đấu, đấu phép (MiniMax H3, Seedance, Kling, Veo…), hoặc khi clip đánh nhau ra chậm, bồng bềnh, đứng im, không có hiệu ứng va chạm. |

## Cài đặt

Lấy repo về (repo private, cần quyền đọc):

```bash
gh repo clone chuanman2707/director-skill
```

Rồi chép thư mục skill vào chỗ app đọc skill. Bảng dưới dùng `<skill>` = `skills/writing-fight-scene-prompts`.

| App | Dùng cho mọi dự án (global) | Chỉ một dự án |
|---|---|---|
| Claude Code | `~/.claude/skills/writing-fight-scene-prompts/` | `<dự án>/.claude/skills/writing-fight-scene-prompts/` |
| Codex (CLI, app, IDE) | `~/.agents/skills/writing-fight-scene-prompts/` (bản cũ: `~/.codex/skills/`) | `<dự án>/.agents/skills/writing-fight-scene-prompts/` |
| Antigravity | `~/.gemini/config/skills/writing-fight-scene-prompts/` (bản cũ: `~/.gemini/antigravity/skills/`) | `<dự án>/.agents/skills/writing-fight-scene-prompts/` |

Windows (PowerShell), cài global cho cả ba app:

```powershell
$src = ".\director-skill\skills\writing-fight-scene-prompts"
foreach ($d in "$HOME\.claude\skills", "$HOME\.agents\skills", "$HOME\.gemini\config\skills") {
  New-Item -ItemType Directory -Force $d | Out-Null
  Copy-Item -Recurse -Force $src $d
}
```

macOS / Linux:

```bash
for d in ~/.claude/skills ~/.agents/skills ~/.gemini/config/skills; do
  mkdir -p "$d" && cp -R director-skill/skills/writing-fight-scene-prompts "$d"/
done
```

Mở phiên mới để app nạp skill. Skill tự bật khi được nhờ viết hoặc sửa prompt cảnh đánh nhau. Muốn gọi tay thì gõ `/writing-fight-scene-prompts` trong Claude Code, hoặc nhắc tên skill trong Codex / Antigravity.

Cập nhật: `git pull` trong thư mục repo rồi chép lại.

## Dùng chung với PanelMint MCP

Khi app AI kết nối PanelMint qua MCP, nó viết prompt bằng `update_shot`. Cài skill này vào app đó thì prompt cảnh đánh viết qua MCP theo cùng luật với prompt viết trong PanelMint.

Với MiniMax H3, shot đánh nhau nên chạy trên máy đã nối LoRA Combat-Base-V2. Xem `references/model-notes.md` của skill.
