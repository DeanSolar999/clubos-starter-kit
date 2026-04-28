# ClubOS 環境設定指引

> 💡 在全新 Mac 上安裝 Homebrew、Node.js、GitHub CLI 等必要工具。整個流程約 10-15 分鐘，會自動檢查已安裝項目。

---

## Claude Code 執行指令

### A：安裝 Homebrew（如尚未安裝）

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### B：安裝必要工具

```bash
brew install node gh trash
```

### C：登入 GitHub CLI

```bash
gh auth login
```

### D：驗證安裝

```bash
node -v && npm -v && gh --version && trash --version
```

所有指令都應顯示版本號，代表安裝成功。
