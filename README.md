# Agent Team Test

本 repo 用於保存一個小型多 Agent 團隊測試的設定文件。目標不是建立完整自動化系統，而是先驗證 Agent 是否能做到：分工、交接、狀態記錄、品質檢查與測試後檢討。

## 測試目標

測試題目暫定為：

> 請 Agent 團隊幫我規劃一封給主管的會議邀請信。

此題目刻意保持簡單，目的是觀察 Agent 流程，而不是挑戰複雜內容產出。

## 系統分工

```text
GitHub = 穩定規則與版本控管
Notion = 任務狀態與測試紀錄
ChatGPT = 讀取規則、執行 Agent 流程、協助檢討
```

## Repo 結構

```text
agent-team-test/
├─ README.md
├─ docs/
│  ├─ 01-test-scope.md
│  ├─ 02-agent-role-cards.md
│  ├─ 03-standard-output-template.md
│  ├─ 04-notion-state-schema.md
│  ├─ 05-quality-gate-checklist.md
│  ├─ 06-test-flow-script.md
│  ├─ 07-pass-fail-criteria.md
│  └─ 08-test-retrospective-template.md
├─ examples/
│  └─ meeting-invitation-test-case.md
└─ logs/
   └─ test-run-001.md
```

## 核心原則

1. Agent 不是聊天角色扮演，而是可交接的工作單元。
2. 每個 Agent 必須有清楚職責邊界。
3. 每個 Agent 都必須使用標準化輸出模板。
4. Notion State 採「一個 Agent 步驟一筆紀錄」。
5. Quality Agent 只做品質判斷，不取代內容產出者。
6. 第一輪測試以半自動為主，不追求完整自動化。

## 覆核重點

請依序覆核：

1. `docs/02-agent-role-cards.md`：Agent 職責是否清楚且不重疊。
2. `docs/03-standard-output-template.md`：輸出欄位是否足夠支援交接。
3. `docs/04-notion-state-schema.md`：State 欄位是否足夠追蹤流程。
4. `docs/05-quality-gate-checklist.md`：品質檢查是否具體、可執行。
5. `docs/06-test-flow-script.md`：測試流程是否能被逐步執行。
6. `docs/07-pass-fail-criteria.md`：成功與失敗標準是否清楚。
7. `docs/08-test-retrospective-template.md`：是否能支援測試後檢討。
