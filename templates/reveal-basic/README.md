# Reveal Basic Template

這是 Reveal.js CDN 版簡報範本，不需要 npm、不需要 build tool，也不需要把 Reveal.js 下載到 repo。

## 建立新簡報

在 repo root 複製範本：

```powershell
Copy-Item -Recurse .\templates\reveal-basic .\New-Talk
```

接著先調整共用樣式路徑，再修改簡報內容：

```text
New-Talk/index.html
```

範本資料夾內的共用樣式路徑是 `../../assets/slide-template.css`；複製到 repo root 的簡報資料夾後，請改成 `../assets/slide-template.css`。

完成後，回到根目錄 `index.html`，在簡報列表新增連到 `./New-Talk/` 的項目。

## 本機預覽

可以直接用瀏覽器開啟：

```text
New-Talk/index.html
```

也可以在 repo root 啟動簡單的 HTTP server：

```powershell
python -m http.server 8000
```

然後開啟：

```text
http://localhost:8000/New-Talk/
```

## 路徑注意事項

- 共用樣式在範本資料夾內使用 `../../assets/slide-template.css`。
- 複製到 repo root 的新簡報資料夾後，請把共用樣式路徑改為 `../assets/slide-template.css`。
- 圖片、CSS、JS 請使用相對路徑，避免 GitHub Pages 子路徑發布時失效。
