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
      "Bash(: >*)",
      "Bash(chmod -R 777 *)",
      "Bash(chmod 777 *)",
      "Bash(dd *)",
      "Bash(diskutil erase*)",
      "Bash(git branch -D*)",
      "Bash(git clean -f*)",
      "Bash(git push --force*)",
      "Bash(git push -f *)",
      "Bash(git reset --hard*)",
      "Bash(mkfs*)",
      "Bash(reboot*)",
      "Bash(rm -R *)",
      "Bash(rm -f *)",
      "Bash(rm -fr *)",
      "Bash(rm -r *)",
      "Bash(rm -rf *)",
      "Bash(shutdown*)",
      "Bash(sudo *)",
      "Bash(truncate *)"
    ],
    "defaultMode": "bypassPermissions"
  }
}
```

執行指令（Terminal 貼上即可）：

```bash
mkdir -p ~/.claude
cat > ~/.claude/settings.json << 'EOF'
{
  "permissions": {
    "allow": [],
    "deny": [
      "Bash(: >*)",
      "Bash(chmod -R 777 *)",
      "Bash(chmod 777 *)",
      "Bash(dd *)",
      "Bash(diskutil erase*)",
      "Bash(git branch -D*)",
      "Bash(git clean -f*)",
      "Bash(git push --force*)",
      "Bash(git push -f *)",
      "Bash(git reset --hard*)",
      "Bash(mkfs*)",
      "Bash(reboot*)",
      "Bash(rm -R *)",
      "Bash(rm -f *)",
      "Bash(rm -fr *)",
      "Bash(rm -r *)",
      "Bash(rm -rf *)",
      "Bash(shutdown*)",
      "Bash(sudo *)",
      "Bash(truncate *)"
    ],
    "defaultMode": "bypassPermissions"
  }
}
EOF
echo "settings.json 已寫入完成"
```
