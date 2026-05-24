# SPEC-001：簡報資料夾骨架契約

> **版本**：v0.1
> **建立日期**：2026-05-24
> **狀態**：Active

## 目的

定義每份正式簡報資料夾的必要檔案結構、CDN 來源規則與共用樣式引用方式，確保所有簡報在維護與發布上保持一致。

## 資料夾結構

每份正式簡報資料夾 **必須** 包含以下檔案：

```
<Talk-Name>/
├── index.html          ← 簡報入口（Reveal.js 標準結構）
├── assets/
│   └── style.css       ← 該簡報的自訂樣式
└── README.md           ← 簡報說明（主題、講者、日期、備註）
```

### 命名規則

- 資料夾名稱：PascalCase + 連字號，如 `Zerospec-Talk/`、`Git-Basic-Talk/`
- 入口檔固定為 `index.html`
- 自訂樣式固定放 `assets/style.css`

## CDN 來源規則

**統一使用 jsdelivr**：

```
https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.css
https://cdn.jsdelivr.net/npm/reveal.js@5/dist/theme/white.css
https://cdn.jsdelivr.net/npm/reveal.js@5/dist/reveal.js
https://cdn.jsdelivr.net/npm/reveal.js@5/plugin/{name}/{name}.js
```

- 版本：浮動 `@5`（自動取最新 5.x）
- 不使用 `unpkg.com` 或其他 CDN
- 不將 Reveal.js 下載到 repo

## 資源路徑規則

- **所有路徑使用相對路徑**（`./` 或 `../`）
- **禁止**使用 `/` 開頭的 root absolute path
- 原因：GitHub Pages 子路徑 `/<repo-name>/` 會導致 absolute path 失效

## 共用樣式引用

新簡報預設引用 root 共用樣式：

```html
<link rel="stylesheet" href="../assets/slide-template.css">
```

`slide-template.css` 提供 SPEC-002 定義的 Design Tokens 與 utility class。
若簡報需要完全自訂風格，可不引用共用樣式，但需在該簡報的 `README.md` 說明原因。

路徑差異：

| 位置 | 共用樣式路徑 |
| --- | --- |
| `templates/reveal-basic/index.html` | `../../assets/slide-template.css` |
| 複製到 repo root 的 `<Talk-Name>/index.html` | `../assets/slide-template.css` |

## 首頁卡片登錄流程

新增簡報後，**必須** 在 root `index.html` 的 `<section>` 簡報列表區新增卡片：

```html
<a class="slide-card" href="./New-Talk/index.html">
  <span class="slide-meta">分類標籤</span>
  <span class="slide-title">簡報標題</span>
  <span class="slide-status">已建立</span>
</a>
```

同時更新 `<span class="count">` 的數字。

## Reveal.js 初始化

標準初始化設定：

```javascript
Reveal.initialize({
  width: 1920,    // 或 1280（依簡報需求）
  height: 1080,   // 或 720
  hash: true,
  slideNumber: true,
  plugins: []     // 只載入必要 plugin
});
```

- 只載入必要 plugin（Notes、Highlight 等），不需要時不載入
- 投影片內容直接寫 HTML，不使用 Markdown plugin（除非使用者明確要求）

---

## Changelog

| 版本 | 日期 | 說明 |
| --- | --- | --- |
| v0.1 | 2026-05-24 | 初版建立 |
