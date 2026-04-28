# 終端機快捷設定

> 💡 在 `~/.zshrc` 中設定 `cc` 快速啟動別名，並啟用防閃爍模式。同時將 `rm` 改為垃圾桶操作，避免誤刪。

---

## 寫入 ~/.zshrc 的內容

將以下內容複製並貼入 `~/.zshrc` 檔案（如已有內容則追加到最後）：

```bash
# ClubOS Claude Code 快速啟動
alias cc='cd "/Users/dean/Downloads/Dean agent" && CLAUDE_CODE_NO_FLICKER=1 claude'

# 安全刪除 - rm 改用垃圾桶（可還原）
export PATH="/opt/homebrew/opt/trash/bin:$PATH"
alias rm='trash'
alias rm!='/bin/rm'
```

## 執行方式

1. 開啟終端機
2. 執行編輯命令：
   ```bash
   nano ~/.zshrc
   ```
3. 將上述內容貼入檔案末尾
4. 按 `Ctrl + O` 儲存，`Ctrl + X` 結束
5. 執行以下指令立即生效：
   ```bash
   source ~/.zshrc
   ```

## 驗證設定

執行以下指令，應該會進入 `/Users/dean/Downloads/Dean agent` 資料夾並啟動 Claude Code：

```bash
cc
```

此時終端機不會出現閃爍，也可直接使用 `rm filename` 安全刪除檔案（檔案進入垃圾桶，可還原）。
