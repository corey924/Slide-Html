# SPEC-002：簡報視覺 Design Tokens

> **版本**：v0.1
> **建立日期**：2026-05-24
> **狀態**：Active
> **實作位置**：`assets/slide-template.css`

## 目的

定義所有簡報共用的 Design Tokens（色票、字級、元件 class），確保風格一致性與投影可讀性。

## 投影優先原則

所有視覺決策以「後排能讀清楚」為最高判斷：

- 預設淺底深字（高對比、偏大字級）
- 避免整份簡報黑底（除非場地條件可控）
- 避免低對比灰字、太細字重
- 避免投影失真的色彩組合（紅字配暗底、藍字配黑底）

## 色票

### CSS Custom Properties

| Token | 值 | 用途 |
| --- | --- | --- |
| `--slide-bg` | `#f7f9fa` | 簡報背景 |
| `--slide-text` | `#172033` | 主要文字 |
| `--slide-muted` | `#526173` | 次要文字（仍保留足夠對比） |
| `--slide-line` | `#d7e2e8` | 分隔線、邊框 |
| `--slide-accent` | `#4ec5d4` | 強調色（標題線、重點字、標籤） |
| `--slide-accent-strong` | `#116d78` | 深強調色（文字用） |
| `--slide-accent-soft` | `#e4f8fb` | 淺強調底（highlight 背景） |
| `--slide-panel` | `#ffffff` | 卡片 / 面板底色 |
| `--slide-panel-strong` | `#e9f6f8` | 強調面板底色 |
| `--slide-code-bg` | `#111827` | Code block 深色背景 |
| `--slide-code-text` | `#edf5f7` | Code block 文字色 |
| `--slide-warn` | `#fff7dc` | 警示 / 注意區塊底色 |

### 使用原則

- 強調色 `--slide-accent` 少量使用，不大面積鋪底
- Code block 深底是唯一允許的深色區域，讓淺底簡報保有工程師技術感
- 卡片與表格：8px 以內圓角、淡邊線（`--slide-line`）、不過度陰影

## 字級建議

| 元素 | 建議 font-size | 備註 |
| --- | --- | --- |
| h1 | 2.35em | 封面標題 |
| h2 | 1.65em | 頁面標題（含底線） |
| h3 | 0.84em | 卡片內標題 |
| p / li | 0.72em | 內文 |
| .lead | 0.84em | 頁面引言 |
| .footer-line | 0.56em | 頁尾補充 |
| .note | 0.5em | 小字註釋 |
| code (block) | 0.58em | 程式碼 |

## 元件 Class

### Grid 佈局

| Class | 效果 |
| --- | --- |
| `.grid-2` | 兩欄 grid |
| `.grid-3` | 三欄 grid |

### 卡片與區塊

| Class | 用途 |
| --- | --- |
| `.card` | 白底卡片（8px 圓角 + 淡邊線 + 微陰影） |
| `.note` | 小字註釋段落 |
| `.note-box` | 黃底警示區塊（左邊 6px 金色邊線） |
| `.metric` | 大數字強調（2.05em bold） |
| `.footer-line` | 頁尾分隔線 + 次要文字 |
| `.lead` | 頁面引言（0.84em、max-width 860px） |
| `.muted` | 次要灰色文字 |
| `.highlight` | 行內強調（accent soft 底色 + accent 文字） |
| `.code-caption` | code block 下方說明文字 |

### 使用範例

```html
<div class="grid-3">
  <div class="card">
    <h3>標題</h3>
    <p>說明文字</p>
  </div>
  <div class="card">...</div>
  <div class="card">...</div>
</div>

<p class="footer-line">補充資訊或引用來源</p>
```

---

## Changelog

| 版本 | 日期 | 說明 |
| --- | --- | --- |
| v0.1 | 2026-05-24 | 初版建立；tokens 來源為 AGENTS.md + Zerospec-Talk 實作 |
