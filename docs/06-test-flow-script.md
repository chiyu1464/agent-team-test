# 06. Test Flow Script

## 測試流程

```text
Step 1：使用者提出原始任務
Step 2：Router Agent 拆解需求、列缺口、指定 Content Agent
Step 3：記錄 Router Agent 輸出到 Notion State
Step 4：Content Agent 根據 Router 輸出寫初稿
Step 5：記錄 Content Agent 輸出到 Notion State
Step 6：Reviewer Agent 審查初稿
Step 7：記錄 Reviewer Agent 輸出到 Notion State
Step 8：Writer Agent 根據初稿與審查意見產出最終版
Step 9：記錄 Writer Agent 輸出到 Notion State
Step 10：Quality Agent 依 Checklist 判斷 Pass / Fail / Need Revision
Step 11：記錄 Quality Agent 輸出到 Notion State
Step 12：使用者進行最終覆核與測試後檢討
```

## 人工流轉版

第一輪建議採人工流轉：

1. 使用者呼叫 Router Agent。
2. 將 Router 輸出貼入 Notion。
3. 使用者將 Router 輸出交給 Content Agent。
4. 將 Content 輸出貼入 Notion。
5. 依序交給 Reviewer、Writer、Quality。

此版本用於測試規則、輸出格式與 State 設計，不測自動化。

## 半自動流轉版

若 ChatGPT 可讀取 Notion，則可嘗試：

1. 由 ChatGPT 讀取 Notion State。
2. 根據目前 Step 與 Status 判斷下一位 Agent。
3. 產出下一步內容。
4. 使用者或 ChatGPT 將結果更新到 Notion。

此版本用於測試 State 是否足夠支持任務接續。

## 未來自動化版

若後續接 n8n、Make、LangGraph 或 API server，流程層工具應負責：

1. 監控 Notion 狀態。
2. 判斷下一位 Agent。
3. 傳遞前一手輸出。
4. 呼叫下一個 Agent。
5. 處理 Fail / Need Revision 分支。
6. 通知使用者最終結果。
