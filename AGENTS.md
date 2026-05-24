# Slide-Html Agent Instructions

這個 repo 是 Corey 用來集中管理多份 HTML 技術簡報的純靜態網站，可透過 GitHub Pages 從 `main` branch 的 repo root 發布。

未來 AI 或協作者新增簡報時，請先遵守本檔案，再依個別簡報需求調整。

## 文件導航

| 你想做什麼 | 先讀這裡 |
| --- | --- |
| 簡報資料夾必要結構、CDN、路徑規則 | `docs/spec/SPEC-001_slide-folder-contract.md` |
| 視覺 Design Tokens、色票、元件 class | `docs/spec/SPEC-002_visual-design-tokens.md` |
| 文件治理與索引 | `docs/README.md` |

## 基本技術約束

- 每份簡報放在 repo root 下的一個獨立資料夾，例如 `Zerospec-Talk/`、`Git-Basic-Talk/`。
- 每份正式簡報資料夾都要有自己的 `index.html`。
- 使用 Reveal.js CDN（統一使用 `cdn.jsdelivr.net/npm/reveal.js@5/`）；不要把 Reveal.js 下載到 repo。
- 不建立 npm 專案，不執行 `npm init`，不產生 `package.json` 或 `node_modules/`。
- 不使用 Vite、React、Webpack、後端服務或 build step。
- 所有資源路徑使用相對路徑；不要使用 `/` 開頭的 root absolute path。
- 除非使用者明確要求，不要加入搜尋、列印樣式、主題切換、複雜動畫或其他非簡報核心功能。

## 簡報內容原則

- 預設使用台灣正體中文，語氣要像台灣軟體工程師的技術分享，不要翻譯腔。
- 每張投影片只傳達一個重點，文字量要少，避免做成文章頁。
- 優先使用清楚的標題、短句、列表、表格、流程與 code block。
- 不要做成產品行銷頁；視覺要服務技術溝通。
- 不要加入無來源的量化宣稱。
- 不要放公司內部敏感資訊、客戶資料、未公開架構圖、私有專案名稱或內部截圖。

## 投影優先的視覺規則

投影環境通常比個人螢幕更不穩定：亮度、對比、環境光、投影機品質都會影響可讀性。未來產生簡報時，以「後排能讀清楚」作為優先判斷。

- 預設採用淺底深字：例如 `#F7F9FA` 或接近白的淺灰底，搭配深灰文字。
- 避免整份簡報預設黑底；黑底只適合低光源、投影條件可控、視覺衝擊優先的場景。
- 不把黑底或白底視為絕對規則；實際選擇以場地與可讀性為準。
- 使用高對比、偏大的字級，避免低對比灰字與太細的字重。
- 避免紅字配暗底、藍字配黑底等投影上容易失真的組合。
- Code block 可以使用深底，讓淺底簡報仍保有工程師技術感與視覺焦點。
- 強調色要少量使用；預設可使用 `#4EC5D4` 作為標題線、重點字、標籤或關鍵數字。

## 建議樣式方向

新簡報預設走「淺灰底技術文件感 + cyan 強調色 + 深色 code block」：

- 背景：`#F7F9FA` 或 `#F4F7F8`
- 主要文字：深灰，例如 `#172033`
- 次要文字：中灰，但仍要保留足夠對比
- 強調色：`#4EC5D4`，避免大面積使用
- Code block：深色背景、淺色文字、清楚邊界
- 卡片與表格：8px 以內圓角、淡邊線、不要過度陰影

## Reveal.js 實作偏好

- `index.html` 使用 Reveal.js 標準結構：`.reveal`、`.slides`、每張投影片一個 `<section>`。
- 投影片內容直接寫在 HTML；不要使用 markdown plugin，除非使用者明確要求。
- 只載入必要 plugin；沒有 speaker notes、code highlight 等需求時不要載入。
- 自訂樣式放在簡報資料夾的 `assets/style.css`，避免大量 inline style。
- 分欄與卡片優先使用清楚的 class，例如 `.grid-2`、`.grid-3`、`.card`、`.metric`、`.note`。

## 建立新簡報前檢查

- 是否真的需要新資料夾，而不是更新既有簡報？
- 是否有 `index.html`、必要的 `assets/style.css`、簡短 `README.md`？
- 是否能直接用瀏覽器開啟，不需要安裝套件？
- 是否所有資源路徑都能在 GitHub Pages 子路徑下運作？
- 是否符合投影可讀性，而不是只在筆電螢幕上好看？
