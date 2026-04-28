# MCP 伺服器設定

> 💡 在 Claude Code 中安裝 4 個 MCP 伺服器（Firecrawl 網頁爬取、Filesystem 檔案存取、Playwright 瀏覽器自動化、Google Workspace 整合）。設定完成後重啟 Claude Code 生效。

---

## 編輯 ~/.claude.json

編輯你的 Claude Code 設定檔案 `~/.claude.json`，在 `projects` 區段找到 `/Users/dean/Downloads/Dean agent` 的 `mcpServers` 區塊，貼入以下完整配置：

```json
{
  "playwright": {
    "type": "stdio",
    "command": "npx",
    "args": ["-y", "@playwright/mcp@latest"],
    "env": {}
  },
  "google-workspace": {
    "type": "stdio",
    "command": "npx",
    "args": ["-y", "@gws-mcp/server"],
    "env": {}
  },
  "firecrawl": {
    "type": "stdio",
    "command": "npx",
    "args": ["-y", "firecrawl-mcp"],
    "env": {
      "FIRECRAWL_API_KEY": "YOUR_FIRECRAWL_API_KEY"
    }
  },
  "filesystem": {
    "type": "stdio",
    "command": "npx",
    "args": ["-y", "@modelcontextprotocol/server-filesystem", "/Users/dean/Downloads/Dean agent"],
    "env": {}
  }
}
```

## 設定步驟

1. **開啟設定檔案**
   ```bash
   nano ~/.claude.json
   ```

2. **找到 projects 區段**
   尋找 `/Users/dean/Downloads/Dean agent` 對應的 `mcpServers` 區塊

3. **貼入上述 JSON 配置**
   完全替換或追加現有的 MCP 伺服器設定

4. **設定 Firecrawl API 金鑰**（可選，現在或稍後設定）
   - 前往 [firecrawl.dev](https://firecrawl.dev) 註冊並取得 API Key
   - 將 `YOUR_FIRECRAWL_API_KEY` 替換為實際金鑰

5. **重啟 Claude Code**
   ```bash
   # 完全關閉 Claude Code 後重新啟動
   ```

## 驗證安裝

安裝完成後，在 Claude Code 指令列執行測試：

```bash
# Playwright 測試
npx -y @playwright/mcp@latest --help

# Google Workspace 測試
npx -y @gws-mcp/server --help

# Firecrawl 測試（需要 API Key）
npx -y firecrawl-mcp --help

# Filesystem 測試
npx -y @modelcontextprotocol/server-filesystem "/Users/dean/Downloads/Dean agent" --help
```

所有指令都應正常執行，代表 MCP 伺服器已成功安裝。
