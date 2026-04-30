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
| Evidence | Text | 必要 | 記錄 Quality Agent 判斷依據或關鍵證據 |
| Return To Agent | Select | 建議 | 若未通過，應退回哪個 Agent |
| Source Document Version | Text | 必要 | 記錄本次執行依據的 GitHub 規則文件版本、commit SHA 或 tag |
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

## Evidence 欄位使用原則

Evidence 用於保留判斷依據，特別是 Quality Agent 做出 Pass / Fail / Need Revision 時，應寫明依據。可包含：

1. 引用前一手 Agent 的具體輸出片段。
2. 指出缺少哪個必要欄位。
3. 指出違反哪一項 Quality Gate Checklist。
4. 指出流程交接失敗的具體原因。

## Source Document Version 欄位使用原則

Source Document Version 用於記錄本次測試依據的 GitHub 規則版本。建議填寫：

```text
GitHub commit SHA / tag / version note
```

例如：

```text
commit: 88c368e
```

這能避免未來規則文件更新後，無法判斷某次測試是依據哪一版規則執行。

## 範例

| Task ID | Step ID | Agent | Status | Quality Result | Source Document Version |
|---|---:|---|---|---|---|
| T001 | 1 | Router Agent | 完成 | Not Checked | commit: 88c368e |
| T001 | 2 | Content Agent | 完成 | Not Checked | commit: 88c368e |
| T001 | 3 | Reviewer Agent | 完成 | Not Checked | commit: 88c368e |
| T001 | 4 | Writer Agent | 完成 | Not Checked | commit: 88c368e |
| T001 | 5 | Quality Agent | 完成 | Pass | commit: 88c368e |
