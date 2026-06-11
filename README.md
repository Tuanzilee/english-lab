# English Lab — 個人英文知識庫(GitHub Pages 獨立版)

單一 `index.html`,無 build step,結構與 psy-quiz / stats-quiz 系列相同。

## 部署(與既有 quiz repo 流程相同)

```bash
# 新 repo
gh repo create english-lab --public
git init && git add index.html README.md
git commit -m "feat: English Lab standalone"
git push -u origin main
# Settings → Pages → Deploy from branch → main / root
```

或直接把 `index.html` 丟進任一現有 GitHub Pages repo 的子資料夾,例如 `/english-lab/index.html`。

## 首次使用

1. 開啟頁面 → 導覽列「設定」
2. 貼上 Anthropic API Key(console.anthropic.com 建立;建議獨立 Key + 設花費上限)
3. Key 只存在瀏覽器 localStorage,不在程式碼裡、不會被 commit、不會上傳

## 與 claude.ai artifact 版的差異

| | Artifact 版 | Pages 版 |
|---|---|---|
| 持久化 | claude.ai 帳號儲存 | localStorage(`english-lab:` 前綴)|
| API | 平台代管,免 Key | 自備 Key,直連 Anthropic API |
| max_tokens | 1000 | 4000(長文分析較完整)|
| 備份 | — | 設定面板可匯出/匯入 JSON |

## 注意

- localStorage 綁定瀏覽器+網域:換裝置或清快取會遺失資料,**定期用「匯出資料」備份**(可 commit 進 repo 當版本化備份,但備份檔不含 API Key,安全)
- Tailwind 由 CDN 載入,需要網路
- 模型寫死在 bundle 內的 `claude-sonnet-4-20250514`;要換模型改 `MODEL` 常數後重新打包,或直接跟 Claude 說再幫你出一版
