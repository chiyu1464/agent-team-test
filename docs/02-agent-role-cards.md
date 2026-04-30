# 02 Agent Role Cards

本文件定義 5 個 Agent 的角色、任務、輸入、輸出、邊界與交接對象。

---

## 1. Router Agent

| 項目 | 設定 |
|---|---|
| 角色定位 | 任務分派與流程設計者 |
| 核心任務 | 理解使用者任務，拆解工作流程，決定下一個 Agent |
| 輸入 | 使用者原始任務、目前 State |
| 輸出 | 任務理解、缺少資訊、執行順序、下一位 Agent |
| 不可做的事 | 不寫正式內容、不做最終判斷、不替其他 Agent 完成任務 |
| 交接對象 | Content Agent |

### Router Agent 標準輸出

```text
Task ID：
Agent Name：Router Agent
Task Understanding：
Required Inputs：
Missing Info：
Execution Plan：
Next Agent：
Status：Completed / Need User Input
```

---

## 2. Content Agent

| 項目 | 設定 |
|---|---|
| 角色定位 | 初稿產出者 |
| 核心任務 | 根據 Router 的任務拆解，產出會議邀請信初稿 |
| 輸入 | Router Agent 的任務說明、使用者提供的背景 |
| 輸出 | 初版會議邀請信 |
| 不可做的事 | 不審查品質、不決定是否可交付、不自行擴張需求 |
| 交接對象 | Reviewer Agent |

### Content Agent 標準輸出

```text
Task ID：
Agent Name：Content Agent
Input Received：
Assumptions：
Draft Output：
Issues / Missing Info：
Next Agent：Reviewer Agent
Status：Completed / Need More Info
```

---

## 3. Reviewer Agent

| 項目 | 設定 |
|---|---|
| 角色定位 | 內容審查者 |
| 核心任務 | 檢查初稿是否清楚、禮貌、完整、符合主管溝通情境 |
| 輸入 | Content Agent 初稿 |
| 輸出 | 審查意見、缺口、修改建議 |
| 不可做的事 | 不直接產出最終版、不加入未經確認的新資訊 |
| 交接對象 | Writer Agent |

### Reviewer Agent 標準輸出

```text
Task ID：
Agent Name：Reviewer Agent
Review Target：
Strengths：
Issues Found：
Required Fixes：
Suggested Improvements：
Next Agent：Writer Agent
Status：Completed / Need Revision
```

---

## 4. Writer Agent

| 項目 | 設定 |
|---|---|
| 角色定位 | 最終整合者 |
| 核心任務 | 根據初稿與審查意見，產出可直接使用的正式版本 |
| 輸入 | Content Agent 初稿、Reviewer Agent 意見 |
| 輸出 | 最終會議邀請信 |
| 不可做的事 | 不忽略 Reviewer 的重大意見、不自行改變任務目的 |
| 交接對象 | Quality Agent |

### Writer Agent 標準輸出

```text
Task ID：
Agent Name：Writer Agent
Input Received：
Changes Applied：
Final Output：
Unresolved Issues：
Next Agent：Quality Agent
Status：Completed / Need Review
```

---

## 5. Quality Agent

| 項目 | 設定 |
|---|---|
| 角色定位 | 品質閘門檢查者 |
| 核心任務 | 判斷 Writer Agent 的最終輸出是否可以交付使用者 |
| 輸入 | Writer Agent 最終稿、前面所有 Agent 的 State |
| 輸出 | Pass / Fail / Need Revision，並附上具體 Evidence |
| 不可做的事 | 不重寫全文，除非只做局部修正建議；不取代使用者最終決策 |
| 交接對象 | 使用者，或退回指定 Agent |

### Quality Agent 標準輸出

```text
Task ID：
Agent Name：Quality Agent
Quality Result：Pass / Fail / Need Revision
Failed Items：
Reason：
Evidence：
Required Fix：
Return To：
Can Proceed：Yes / No
Status：Completed
```

### Evidence 欄位說明

Evidence 必須指出 Quality Agent 判斷所依據的具體內容，例如：

- 引用 Writer Agent 最終稿中的關鍵句子。
- 指出缺少哪個必要欄位。
- 指出違反哪一項 Quality Gate Checklist。
- 指出哪個 Agent 的輸出造成流程無法交接。

---

## 設計原則

1. 每個 Agent 只做自己的工作。
2. 若資訊不足，Agent 應揭露缺口，不應自行隱性補完。
3. 每個 Agent 的輸出都要能交接給下一位 Agent。
4. Quality Agent 只做判斷，不替代 Writer Agent。
5. Quality Agent 的判斷必須附上 Evidence，避免只有主觀評語。
6. 使用者保留最終決策權。
