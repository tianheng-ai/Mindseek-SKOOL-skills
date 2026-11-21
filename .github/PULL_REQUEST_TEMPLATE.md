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

這個 repo 沒有程式、沒有建置，閘門照專案卡 AGENTS.md：

- [ ] `claude plugin validate .` 通過，看得到每個技能
- [ ] `python3 -m json.tool` 讀得懂 `.claude-plugin/plugin.json` 與 `marketplace.json`
- [ ] 新增或改名技能：README 技能表與兩個 json 的說明已同步
- [ ] 合併後：用公開網址抓一次 `skills/<技能名>/SKILL.md`，跟 repo 版本一致

## 營運影響

- 會員要不要重裝：<不用／要——Skool 頁面怎麼通知>
- 回滾方式：<怎麼還原>
