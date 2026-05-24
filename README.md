# Corey Slides

集中管理 Corey 的 HTML 技術簡報，可透過 GitHub Pages 直接發布。

## 簡報列表

| 簡報 | 主題 | 狀態 |
| --- | --- | --- |
| [Zerospec-Talk](./Zerospec-Talk/) | ZeroSpec：讓 AI 看得懂專案的 Layer 0 方法庫 | 已建立 |

## 快速開始

### 新增簡報

```powershell
# 1. 複製範本
Copy-Item -Recurse .\templates\reveal-basic .\New-Talk

# 2. 修改共用樣式路徑，再修改簡報內容
#    templates/reveal-basic/ 內預設是 ../../assets/slide-template.css
#    複製到 repo root 後需改成 ../assets/slide-template.css
code .\New-Talk\index.html

# 3. 回到根目錄 index.html，在簡報列表新增卡片連結
```

### 本機預覽

```powershell
python -m http.server 8000
```

開啟 `http://localhost:8000/` 即可瀏覽首頁與各簡報。

## GitHub Pages 發布

**Settings → Pages → Deploy from a branch → `main` / `/ (root)`**

發布後網址：

```
https://<username>.github.io/Slide-Html/
https://<username>.github.io/Slide-Html/Zerospec-Talk/
```

## 專案結構

```
Slide-Html/
├── index.html              ← 首頁（簡報導覽列表）
├── assets/
│   ├── site.css            ← 首頁樣式
│   └── slide-template.css  ← 簡報共用樣式（Design Tokens）
├── templates/
│   └── reveal-basic/       ← 新簡報起手範本
├── Zerospec-Talk/          ← 正式簡報
│   ├── index.html
│   ├── assets/style.css
│   └── README.md
├── docs/                   ← SDD 文件
│   ├── README.md
│   └── spec/
├── AGENTS.md               ← AI／協作者規範
└── README.md               ← 本文件
```

## 資料夾命名規則

- 使用英文、數字與連字號
- PascalCase 加連字號：`Zerospec-Talk/`、`Git-Basic-Talk/`
- 每個正式簡報資料夾必須有 `index.html`

## 技術約束摘要

- **Reveal.js 5 CDN**（`cdn.jsdelivr.net/npm/reveal.js@5/`），不下載到 repo
- **純靜態**：無 npm、無 build pipeline、無後端
- **相對路徑**：所有資源引用使用 `./` 或 `../`，不使用 `/` 開頭
- **視覺風格**：淺灰底 `#F7F9FA` + cyan 強調色 `#4EC5D4` + 深色 code block

完整規範與產生指引請見 [AGENTS.md](./AGENTS.md)。

## 文件導航

| 你想做什麼 | 先讀這裡 |
| --- | --- |
| 新增或修改簡報前的規範 | [AGENTS.md](./AGENTS.md) |
| 查看文件治理與 SPEC | [docs/README.md](./docs/README.md) |
| 複製起手範本 | [templates/reveal-basic/](./templates/reveal-basic/) |
| 參考既有正式簡報 | [Zerospec-Talk/](./Zerospec-Talk/) |
