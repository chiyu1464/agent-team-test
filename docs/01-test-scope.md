# 01 測試範圍

## 目的

本測試的目的，是協助理解 Agent 工作流的基本概念：

- Agent 分工
- 任務交接
- State 記錄
- Quality Gate 檢查
- 測試後檢討

本測試不以完整自動化為第一目標，而是先驗證流程結構是否可行。

## 測試題目

> 請 Agent 團隊幫我規劃一封給主管的會議邀請信。

## 測試邊界

本測試只處理「會議邀請信」這類簡單任務，不處理大型專案規劃、資料查詢、程式開發或外部系統整合。

## 控制項目

以下項目固定不變：

1. Agent 數量為 5 個。
2. 每個 Agent 必須依 Role Card 執行。
3. 每個 Agent 必須使用標準化輸出模板。
4. 每個 Agent 步驟都應記錄到 Notion State。
5. Quality Agent 必須依 Quality Gate Checklist 判斷 Pass / Fail / Need Revision。

## 使用者輸入項目

以下項目可於正式測試時由使用者提供：

- 會議目的
- 會議對象
- 希望語氣
- 是否已有會議時間
- 是否需要議程
- 最終輸出形式，例如 Email、Teams 訊息、行事曆邀請文字

## 測試策略

第一輪測試採半自動方式：

1. ChatGPT 依 Agent 流程產出內容。
2. 使用者或 ChatGPT 將結果記錄到 Notion。
3. Quality Agent 進行檢查。
4. 測試後依 State 紀錄進行檢討。

## 不在本階段處理的事項

- 自動監控 Notion 狀態
- 自動呼叫下一個 Agent
- API 串接
- n8n / LangGraph / Make 等流程工具
- 完整產品化部署
