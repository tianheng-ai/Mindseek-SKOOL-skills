# Mindseek-SKOOL-skills 專案卡

<!--
agent 每次在這個 repo 開工都會讀這份。誰讀哪裡：
- dev-task 第 2 步（preflight）抓「事實」裡分支那一行，當作開分支與 PR 的 base——那一行的字樣不要改，
  只把角括號佔位換成真的分支名（例如 main 或 staging）；沒換的話 preflight 會提醒你還沒填。
- dev-task 第 5 步（驗證）照「指令」那一節跑 typecheck／lint／test／build，貼實際輸出當合併閘門。
- 「本專案鐵律」「下結論前的查證規則」由 agent 自己讀，動手和下結論之前照做。
CLAUDE.md 只有一行 @AGENTS.md，讓 Claude 讀同一份。
-->

## 事實

- 整合分支：`main`（功能分支一律從這裡開、PR 一律合回這裡）
- 正式分支：同上（合併進 main 就是發布：會員從 GitHub 公開 repo 直接下載技能檔，沒有建置與部署）
- 部署：無。公開 repo https://github.com/tianheng-ai/Mindseek-SKOOL-skills 本身就是發布點；Claude Code 會員用 `/plugin marketplace add tianheng-ai/Mindseek-SKOOL-skills` 安裝
- 資料層：無
- 併行工作台 Issue：#1（`setup-repo.sh` 建的那一個）

## 指令

- dev：無
- typecheck：無　lint：無　test：無　build：無
- 這個 repo 沒有程式碼，只有技能說明檔（SKILL.md）、README 與外掛 manifest。驗收方式見「下結論前的查證規則」。

## 本專案鐵律

- 這是公開 repo，會員和任何人都看得到：只放免費給 MindSeek AI 學院會員的技能。內部決策紀錄、腳本、客戶資料、付費課內容、行銷技能包不准放進來。
- 改編自別人開源的技能：原本的 LICENSE 檔一起放進該技能資料夾，不准拿掉。
- 新增或改名技能時，`README.md` 的技能表與 `.claude-plugin/plugin.json`、`.claude-plugin/marketplace.json` 的說明一起改。
- Skool 頁面上的安裝指令寫死了技能檔路徑 `skills/<技能名>/SKILL.md`：已上架的技能不准搬家或改資料夾名。
- 技能內容寫給非工程師的會員用：不准要求 git、終端機指令或 API 金鑰。

## 下結論前的查證規則

回答「會員裝不裝得到、裝到的是哪一版」之前，先跑完下列查證，只讀本機檔不准下結論：

- 用公開網址抓一次檔案，跟 repo 裡的版本比對：`curl -sL https://raw.githubusercontent.com/tianheng-ai/Mindseek-SKOOL-skills/main/skills/<技能名>/SKILL.md`
- 兩個 json 要能解析：`python3 -m json.tool .claude-plugin/plugin.json`、`python3 -m json.tool .claude-plugin/marketplace.json`

## 既知陷阱

- 整個 repo 就是一個外掛（marketplace 的 `source: "./"`），會員用 Claude Code 安裝時會拿到 repo 裡所有檔，包括這份專案卡與流程範本；給會員看的東西寫在 README，不寫在這裡。

## 流程

動程式碼一律先載入 `dev-task` 技能，照它的七步走；本專案的差異：沒有 CI、沒有建置，閘門①②以「json 能解析＋公開網址抓得到」代替。

（檔尾的「專案能力」一節由能力問卷產生，改 `.devkit.json` 後重跑 `devkit.py render`，不要手改。）

<!-- devkit:start（由 devkit.py render 產生：改 .devkit.json 後重跑，不要手改這一節）-->
## 專案能力

整合分支 `main`，正式分支 `main`。清單在 `.devkit.json`。

| 能力 | 狀態 | 怎麼用／理由 |
|---|---|---|
| 埋點 | 不採用 | 沒有網站或程式，只有技能說明檔 |
| 架構關卡：擋 | 採用 | 超標檔變大、新檔放在地圖外、函式超過上限都會被擋；例外用 `arch-exception.sh` 登記理由 |
| CI 跑資料庫測試 | 不採用 | 沒有資料庫也沒有測試 |
| PR 閘門 | 不採用 | 沒有程式碼，沒有型別檢查、lint、build 可跑 |
| 資料庫隔離 | 不採用 | 不適用：沒有資料庫 |
| migration 檢查 | 不採用 | 沒有資料庫 migration |
| 每晚全套 | 不採用 | 沒有測試 |
| repo 內專案記憶 | 不採用 | 公開 repo 會員看得到，內部決策與交接記在 Obsidian 腦子的 Skool 建置紀錄 |
| 錯誤追蹤（Sentry） | 不採用 | 沒有網站或程式 |
| 測試站＋正式站 | 不採用 | 沒有部署；合併進 main 就是發布，會員直接從公開 repo 下載 |
| Supabase migration 帳本 | 不採用 | 不用 Supabase |
| 測試三層 | 不採用 | 沒有測試檔；驗收是 json 能解析＋公開網址抓得到 |
| Vercel：功能分支不部署 | 不採用 | 不用 Vercel |
<!-- devkit:end -->
