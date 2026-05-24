# docs/ — Slide-Html 文件治理導航

> 本目錄存放 SDD（Specification-Driven Development）相關文件。
> 專案入口：[AGENTS.md](../AGENTS.md)　　專案 README：[README.md](../README.md)

## 文件索引

| 你想做什麼 | 文件 | 狀態 |
| --- | --- | --- |
| 了解系統全貌與模組關係 | [SA-001](./analysis/SA-001_slide-html-architecture.md) | v0.1 |
| 了解簡報資料夾必要結構 | [SPEC-001](./spec/SPEC-001_slide-folder-contract.md) | v0.1 |
| 了解視覺 Design Tokens | [SPEC-002](./spec/SPEC-002_visual-design-tokens.md) | v0.1 |

## 文件類型說明

| 類型 | 用途 | 目錄 |
| --- | --- | --- |
| SA | 系統架構分析（milestone snapshot） | `analysis/` |
| SPEC | 行為契約與介面規格（Source of Truth） | `spec/` |
| ADR | 架構決策紀錄（append-only） | `adr/`（待需要時建立） |

## 維護規則

- SPEC 是新增與維護流程的主要依據；若和既有實作衝突，先確認現況，再修正文件或實作
- 新增 SPEC 後同步更新本文件索引
- ADR 不可修改已決議內容，只能新增 ADR 覆寫
