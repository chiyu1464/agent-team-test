# 05. Quality Gate Checklist

Quality Gate 用來判斷 Agent 流程是否可以交付，不只是判斷文字寫得好不好。

## A. 格式完整性

| 檢查項目 | 通過標準 |
|---|---|
| 是否有 Task ID | 必須有 |
| 是否有 Agent Name | 必須有 |
| 是否有 Input Received | 必須說明收到什麼 |
| 是否有 Output | 必須有實質產出 |
| 是否有 Status | 必須標示完成、失敗、需修改或需使用者補充 |
| 是否有 Next Agent / Next Step | 必須能交接 |

## B. 任務理解

| 檢查項目 | 通過標準 |
|---|---|
| 是否符合使用者原始任務 | 不可偏離主題 |
| 是否自行擴張需求 | 不可加入未要求的大型假設 |
| 是否列出必要假設 | 有假設就要明講 |
| 是否標示缺少資訊 | 缺資訊不可假裝完整 |

## C. Agent 職責邊界

| 檢查項目 | 通過標準 |
|---|---|
| Router 是否只拆任務 | 不應寫正式內容 |
| Content 是否只產出初稿 | 不應自行判斷通過 |
| Reviewer 是否只審查 | 不應直接產出最終稿 |
| Writer 是否整合意見 | 不應忽略 Reviewer |
| Quality 是否只判斷可交付 | 不應重寫整篇內容 |

## D. 內容品質

| 檢查項目 | 通過標準 |
|---|---|
| 語氣是否適合主管 | 應正式、禮貌、簡潔 |
| 目的是否清楚 | 主管一看就知道為何開會 |
| 行動要求是否明確 | 知道要出席、回覆或確認時間 |
| 資訊是否足夠 | 至少包含目的、對象、議題、時間或待確認事項 |
| 是否可直接使用 | 最終版應可貼到 email、Teams 或行事曆邀請中 |

## E. State 品質

| 檢查項目 | 通過標準 |
|---|---|
| 是否記錄前一手輸出 | 下一位 Agent 可追溯 |
| 是否更新狀態 | 不可停留在錯誤狀態 |
| 是否保存完整輸出 | 不只保存摘要 |
| 是否記錄失敗原因 | 失敗時需可診斷 |
| 是否指定下一步 | 流程不可中斷 |

## Quality Agent 固定輸出

```text
Task ID：
Agent Name：Quality Agent
Quality Result：Pass / Fail / Need Revision
Failed Items：
Reason：
Required Fix：
Return To：
Can Proceed：Yes / No
Status：Completed
```
