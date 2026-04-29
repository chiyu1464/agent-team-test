# 07. Pass / Fail Criteria

## 測試通過標準

符合以下條件，視為本輪測試 Pass：

1. 5 個 Agent 都能依照 Role Card 工作。
2. 每個 Agent 都使用標準化輸出模板。
3. 每個 Agent 步驟都能在 Notion State 中形成一筆紀錄。
4. 每一步都能追溯前一手輸入。
5. 每一步都有明確 Next Agent 或 Next Step。
6. 最終會議邀請信可直接使用，或只需小幅人工修改。
7. Quality Agent 的判斷有明確理由，不只是主觀評語。
8. 測試後可以從 State 看出哪個步驟穩定、哪個步驟需要修正。

## 測試失敗標準

出現以下任一情況，視為 Fail 或 Need Revision：

1. Agent 任務混淆，例如 Reviewer 直接重寫最終稿。
2. Router 沒有清楚指定下一步。
3. Content Agent 自行補入重大未確認假設。
4. Writer 忽略 Reviewer 的重大修正意見。
5. Quality Agent 沒有依 Checklist 檢查。
6. 輸出格式不固定，導致無法寫入 State。
7. Notion State 無法還原整個流程。
8. 最終輸出不可直接使用，且缺口未被揭露。

## 測試結果分類

| 結果 | 定義 |
|---|---|
| Pass | 流程可跑通，輸出可交付，State 可追蹤 |
| Need Revision | 流程大致可跑通，但部分 Agent 或欄位需修正 |
| Fail | 流程中斷、角色混亂、State 無法支持交接，或最終輸出不可用 |

## 主要觀察指標

| 指標 | 觀察重點 |
|---|---|
| 角色邊界穩定性 | Agent 是否做自己該做的事 |
| 輸出格式穩定性 | 是否能持續符合模板 |
| State 可追蹤性 | 是否能還原任務流轉過程 |
| Quality Gate 有效性 | 是否能指出具體問題與退回對象 |
| 人工介入程度 | 哪些地方仍需人手動判斷或修補 |
