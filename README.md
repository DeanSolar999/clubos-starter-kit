# ClubOS Starter Kit

> 曜日羽球團 Claude Code 環境還原包。新電腦開 Claude Code，把這份 repo 的連結丟給它，照順序跑完就能還原所有設定。

## 使用方式

在新電腦安裝好 Claude Code 後，開啟終端機輸入：

```
claude
```

然後貼上以下指令：

```
請讀取 https://github.com/DeanSolar999/clubos-starter-kit 的 starter-kit 資料夾，依照 01 到 06 的順序幫我完成所有環境設定。
```

Claude Code 會自動依序執行每個步驟。

## 設定項目

| 順序 | 檔案 | 內容 |
|------|------|------|
| 01 | [environment-setup](starter-kit/01-environment-setup.md) | Homebrew、Node.js、GitHub CLI、trash 安裝 |
| 02 | [terminal-config](starter-kit/02-terminal-config.md) | `cc` 快速啟動、防閃爍模式、安全刪除 |
| 03 | [mcp-servers](starter-kit/03-mcp-servers.md) | Firecrawl、Filesystem、Playwright、Google Workspace |
| 04 | [safety-settings](starter-kit/04-safety-settings.md) | 20 條危險指令黑名單、權限模式 |
| 05 | [claude-md](starter-kit/05-claude-md.md) | CLAUDE.md 核心行為指令集 |
| 06 | [memory-restore](starter-kit/06-memory-restore.md) | Memory 系統還原（9 個記憶檔案） |

## 前提條件

- macOS（Apple Silicon 或 Intel）
- Claude Code 已安裝（`npm install -g @anthropic-ai/claude-code`）
- Anthropic Max 或 API Key 已登入

## 注意事項

- `FIRECRAWL_API_KEY` 需自行替換（到 [firecrawl.dev](https://firecrawl.dev) 取得）
- Google Workspace MCP 首次使用需完成 OAuth 授權
- 所有路徑預設為 `/Users/dean/Downloads/Dean agent`，如有變動需調整

## 維護

每次有重大環境變更（新增 MCP、修改 CLAUDE.md、新增 Memory），更新對應檔案後 push 即可。

---

by 曜日羽球團 ClubOS
