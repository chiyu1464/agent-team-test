# 03 Standard Output Template

本文件定義所有 Agent 共用的標準化輸出模板。目的在於讓每個 Agent 的輸出都能被下一位 Agent、Notion State 與 Quality Agent 理解。

## 共用模板

```text
Task ID：
Agent Name：
Input Received：
Task Understanding：
Assumptions：
Output：
Issues / Missing Info：
Decision Needed：
Next Agent：
Status：Completed / Failed / Need Review
```

## 欄位說明

| 欄位 | 說明 |
|---|---|
| Task ID | 同一個任務的唯一識別碼，例如 T001 |
| Agent Name | 本次執行的 Agent 名稱 |
| Input Received | 本 Agent 實際收到的輸入 |
| Task Understanding | 本 Agent 對任務的理解 |
| Assumptions | 明確列出本次處理使用了哪些假設 |
| Output | 本 Agent 的主要產出 |
| Issues / Missing Info | 缺少資訊、疑點、風險或未解決問題 |
| Decision Needed | 需要使用者或管理者決策的地方 |
| Next Agent | 下一位應接手的 Agent |
| Status | 本步驟狀態：Completed / Failed / Need Review |

## 使用原則

1. 每個 Agent 都應填寫模板，不應任意改格式。
2. 若無假設，Assumptions 應寫「無」。
3. 若無缺漏，Issues / Missing Info 應寫「無」。
4. 若不需要決策，Decision Needed 應寫「無」。
5. Next Agent 不可空白，若流程結束則寫「User」。
6. Status 應使用固定值，不應自行發明狀態名稱。

## 為什麼需要標準化輸出

標準化輸出能支援三件事：

1. Agent 之間可交接。
2. Notion State 可記錄。
3. Quality Agent 可檢查。

如果輸出格式不固定，流程會變成一般對話，無法形成可管理的 Agent 系統。
