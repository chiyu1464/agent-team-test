# 04. Notion State Schema

## 設計原則

Notion State 用來記錄每次 Agent 執行步驟，不只是保存文件。建議採用：

> 一個 Agent 步驟 = Notion 中一筆紀錄

同一個 Task ID 底下會有多筆 Step 紀錄。

## 建議欄位

| 欄位 | 類型 | 必要性 | 用途 |
|---|---|---:|---|
| Task ID | Text | 必要 | 串接同一任務 |
| Step ID | Number / Text | 必要 | 表示第幾個 Agent 步驟 |
| 任務名稱 | Title | 必要 | 任務主題 |
| 原始指令 | Text | 必要 | 保存使用者最初要求，避免後續偏離 |
| 當前負責 Agent | Select | 必要 | 記錄本步驟負責 Agent |
| 前一手輸出連結 | URL / Relation | 必要 | 指向上一個 Agent 的輸出 |
| Input Received | Text | 必要 | 本 Agent 實際收到的輸入 |
| Output Full | Text / Page | 必要 | 保存完整輸出 |
| 輸出摘要 | Text | 必要 | 供人類與 Router 快速理解 |
| 狀態 | Select | 必要 | 待處理／進行中／完成／失敗／需修改 |
| 失敗原因 | Text | 必要 | 任務失敗時記錄原因 |
| Decision Needed | Text | 建議 | 需要使用者決策的地方 |
| 下一步 | Text | 必要 | 下一步應做什麼 |
| Next Agent | Select | 必要 | 下一位接手 Agent |
| Quality Result | Select | 必要 | Pass / Fail / Need Revision / Not Checked |
| Return To Agent | Select | 建議 | 若未通過，應退回哪個 Agent |
| 是否需人工介入 | Checkbox | 建議 | 測試流程自動化程度 |
| 人工介入原因 | Text | 建議 | 記錄人類介入的原因 |
| 輸出是否可交接 | Select | 建議 | Yes / No / Partially |
| 改進建議 | Text | 建議 | 測試後調整依據 |
| 更新時間 | Last edited time | 必要 | 追蹤狀態變化 |
| 版本 | Number / Text | 必要 | 避免覆蓋與混淆 |

## 狀態建議選項

```text
待處理
進行中
完成
失敗
需修改
需使用者補充
```

## Quality Result 建議選項

```text
Not Checked
Pass
Fail
Need Revision
```

## 範例

| Task ID | Step ID | Agent | Status | Quality Result |
|---|---:|---|---|---|
| T001 | 1 | Router Agent | 完成 | Not Checked |
| T001 | 2 | Content Agent | 完成 | Not Checked |
| T001 | 3 | Reviewer Agent | 完成 | Not Checked |
| T001 | 4 | Writer Agent | 完成 | Not Checked |
| T001 | 5 | Quality Agent | 完成 | Pass |
