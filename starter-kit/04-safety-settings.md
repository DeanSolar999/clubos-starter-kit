> 💡 這份設定會告訴 Claude Code 哪些指令絕對不能執行，例如強制刪除檔案、強制推送 Git、格式化硬碟等。
> 💡 `defaultMode: bypassPermissions` 表示平常操作不會一直跳出確認視窗，但黑名單裡的危險指令仍會被擋住。
> 💡 將以下 JSON 內容存入 `~/.claude/settings.json`，重啟 Claude Code 後生效。

---

將以下內容寫入 `~/.claude/settings.json`（若檔案已存在請先備份）：

```json
{
  "permissions": {
    "allow": [],
    "deny": [
      "Bash(rm -rf *)",
      "Bash(rm -r *)",
      "Bash(rm -fr *)",
      "Bash(rm -R *)",
      "Bash(rm -f *)",
      "Bash(: >*)",
      "Bash(truncate *)",
      "Bash(dd *)",
      "Bash(git push --force*)",
      "Bash(git push -f *)",
      "Bash(git push origin --delete*)",
      "Bash(git reset --hard*)",
      "Bash(git clean -f*)",
      "Bash(git branch -D*)",
      "Bash(git checkout .)",
      "Bash(git checkout -- .)",
      "Bash(git restore .)",
      "Bash(git rebase*)",
      "Bash(git stash drop*)",
      "Bash(sudo *)",
      "Bash(chmod 777 *)",
      "Bash(chmod -R 777 *)",
      "Bash(killall *)",
      "Bash(diskutil erase*)",
      "Bash(mkfs*)",
      "Bash(reboot*)",
      "Bash(shutdown*)",
      "Bash(npm publish*)"
    ],
    "defaultMode": "bypassPermissions"
  }
}
```

### 黑名單分類說明（28 條）

| 分類 | 指令 | 風險 |
|------|------|------|
| 檔案毀損 | `rm -rf/-r/-fr/-R/-f` | 遞迴或強制刪除，無法復原 |
| | `: >` / `truncate` | 清空檔案內容 |
| | `dd` | 低階磁碟寫入 |
| Git 不可逆 | `git push --force/-f` | 覆蓋遠端歷史 |
| | `git push origin --delete` | 刪除遠端分支 |
| | `git reset --hard` | 丟棄所有未 commit 修改 |
| | `git clean -f` | 刪除未追蹤檔案 |
| | `git branch -D` | 強制刪除分支 |
| | `git checkout .` / `git restore .` | 丟棄所有未暫存修改 |
| | `git rebase` | 改寫 commit 歷史 |
| | `git stash drop` | 丟棄暫存工作 |
| 系統提權 | `sudo` | 提權執行 |
| | `chmod 777` | 開放所有權限 |
| | `killall` | 終止所有匹配程序 |
| 系統毀損 | `diskutil erase` / `mkfs` | 格式化磁碟 |
| | `reboot` / `shutdown` | 重啟或關機 |
| 外部發佈 | `npm publish` | 發佈到公開 registry |

### 設計原則

- **黑名單模式**：只封鎖不可逆或影響外部的指令，其餘全部放行
- `kill <PID>`（單一程序）保留手動確認，不直接封鎖
- `cat .env`（除錯用）、`gh pr create`（按需使用）不列入黑名單
- 新增危險指令時，需同步更新三處：`settings.json` → `CLAUDE.md` → 本檔案

---

執行指令（Terminal 貼上即可）：

```bash
mkdir -p ~/.claude
cat > ~/.claude/settings.json << 'SETTINGS_EOF'
{
  "permissions": {
    "allow": [],
    "deny": [
      "Bash(rm -rf *)",
      "Bash(rm -r *)",
      "Bash(rm -fr *)",
      "Bash(rm -R *)",
      "Bash(rm -f *)",
      "Bash(: >*)",
      "Bash(truncate *)",
      "Bash(dd *)",
      "Bash(git push --force*)",
      "Bash(git push -f *)",
      "Bash(git push origin --delete*)",
      "Bash(git reset --hard*)",
      "Bash(git clean -f*)",
      "Bash(git branch -D*)",
      "Bash(git checkout .)",
      "Bash(git checkout -- .)",
      "Bash(git restore .)",
      "Bash(git rebase*)",
      "Bash(git stash drop*)",
      "Bash(sudo *)",
      "Bash(chmod 777 *)",
      "Bash(chmod -R 777 *)",
      "Bash(killall *)",
      "Bash(diskutil erase*)",
      "Bash(mkfs*)",
      "Bash(reboot*)",
      "Bash(shutdown*)",
      "Bash(npm publish*)"
    ],
    "defaultMode": "bypassPermissions"
  }
}
SETTINGS_EOF
echo "✅ settings.json 已寫入完成（28 條黑名單）"
```
