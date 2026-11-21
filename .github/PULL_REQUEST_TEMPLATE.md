<!--
`## Scope` 是併行協定的認領機制，不是文件。SessionStart hook 會讀每個 open PR
的這個區塊，把 `touches` 注入所有新 session 的開場 context；PreToolUse 的
scope-guard 會攔下對別人已認領檔案的寫入。沒有這個區塊的 PR，別的 agent 只會
看到「範圍不明」，等於沒有佔到坑。

範圍由 agent 自己推導，不要問人檔案路徑。開工時先粗宣告（模組級，寧可過
大不要不足），計畫定案後精確化並回來把 provisional 改成 false。中途要碰計畫外
的檔，先更新這裡再動手。用 dev-task 的 start-task.sh 開工會自動填好。
-->

## Scope
task: <一句白話的任務描述>
touches: <會寫入的路徑 glob，逗號分隔>
avoid: <明知有風險但這輪不碰的檔案>
exclusive: none
provisional: true
session: <ListAgents 顯示的本 session 名稱>
started: <UTC 時間，如 2026-08-26T22:10Z>

## 為什麼

<解決什麼問題。沒有問題就不該有這個 PR。>

## 這個 PR 做了什麼

<改了什麼，重要的設計決定，以及有沒有改到 public contract。>

## 驗證

<貼實際輸出，不是「應該會過」。>

- [ ] verify:migrations（若專案有）
- [ ] typecheck
- [ ] lint
- [ ] test
- [ ] build
- [ ] UI 改動：已用瀏覽器實走過每個改動畫面與斷點（**測試綠不等於做完**）
- [ ] 新增使用者可觸發的動作：本 PR 已帶對應埋點事件

## 營運影響

- migration：<無／有——合併後如何上線、是否要先套 DB>
- 環境變數：<無／新增了什麼>
- 相依套件：<無／新增或升級了什麼>
- 回滾方式：<怎麼關掉或還原>
