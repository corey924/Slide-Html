# Corey Slides

這個 repo 用來集中管理多份 HTML 技術簡報，未來可透過 GitHub Pages 從 `main` branch 的 repo root 直接發布。

每份簡報都是一個獨立資料夾，資料夾內放自己的 `index.html`。目前不使用 npm、不建立 build pipeline，也不把 Reveal.js 下載到 repo；簡報範本預設使用 Reveal.js CDN。

## 資料夾命名規則

- 使用英文、數字與連字號。
- 使用 PascalCase 或清楚的主題名稱，例如 `Zerospec-Talk/`、`Git-Basic-Talk/`、`AI-SA-Workflow/`。
- 每份正式簡報資料夾都要包含 `index.html`。
- 圖片、CSS、JS 請使用相對路徑，避免使用 `/` 開頭的 root absolute path。
- `Zerospec-Talk/` 已建立正式簡報入口頁，可從根目錄首頁開啟。

## 新增簡報流程

新增或修改簡報前，請先閱讀 `AGENTS.md`。該檔案記錄此 repo 給 AI 與協作者使用的簡報產生規範，包含純靜態技術約束、投影優先的視覺原則，以及未來簡報預設採用的淺底技術文件風格。

1. 複製範本資料夾：

   ```powershell
   Copy-Item -Recurse .\templates\reveal-basic .\New-Talk
   ```

2. 修改 `New-Talk/index.html` 的標題、投影片內容與 speaker notes。

3. 視需要在簡報中引用共用樣式：

   ```html
   <link rel="stylesheet" href="../assets/slide-template.css">
   ```

4. 回到根目錄 `index.html`，在簡報列表新增 `./New-Talk/` 連結。

## 本機預覽

可以直接用瀏覽器開啟根目錄的 `index.html`。

若要用本機 HTTP server 預覽，請在 repo root 執行：

```powershell
python -m http.server 8000
```

然後開啟：

```text
http://localhost:8000/
http://localhost:8000/templates/reveal-basic/
http://localhost:8000/New-Talk/
```

## GitHub Pages 發布設定

到 GitHub repo 設定：

```text
Settings -> Pages -> Build and deployment -> Deploy from a branch -> main -> / root
```

發布後預期網址格式：

```text
https://<github-username>.github.io/Slide-Html/
https://<github-username>.github.io/Slide-Html/<Talk-Folder>/
```

## 注意事項

- 不要放公司內部敏感資訊、客戶資料、未公開架構圖或內部截圖。
- 圖片、CSS、JS 都請使用相對路徑。
- 每份正式簡報資料夾都要有 `index.html`。
- 若未來需要更複雜互動，再考慮 npm / Vite；不要一開始就把靜態簡報 repo 複雜化。
