---
thresholds:
  file_lines: 500       # 單檔超過即超標（健檢與三道關卡都用）
  function_lines: 80    # 單一函式（健檢與推送前檢查用）
  fan_in: 25            # 被幾個檔依賴（只有健檢用）
checkup:
  last_date: 2026-11-21
  last_commit: c3f1f70c896165f7e484a2352dd7271fb05bb717
  every_prs: 10         # 近 30 天合併量很少，取下限 10
  every_days: 14
---

# 系統地圖

這份地圖寫給 agent：開工前查「新功能該放哪一區」，健檢與關卡照它判斷有沒有放錯。
只寫不常變的事；細節看程式。每區一句話講清楚它管什麼、不管什麼。

這個 repo 是公開的會員技能庫：只放免費給 MindSeek AI 學院會員的技能，沒有程式碼。
整個 repo 就是一個 Claude Code 外掛（`source: "./"`），會員安裝時會拿到 repo 裡所有檔。

## 分區

每列一區。「對外入口」寫別區只能從哪些檔進來（路徑或 glob，多個用「、」分隔；不限就寫 —）。
「可以依賴哪些區」寫地圖上其他區的路徑（多個用「、」分隔；都不行就寫 無）——寫了地圖上沒有的區，健檢會停下來點名。

| 路徑 | 負責什麼 | 不放什麼 | 對外入口 | 可以依賴哪些區 |
|---|---|---|---|---|
| `skills/**` | 每個技能一個資料夾，`SKILL.md` 是本體；改編自開源技能的附原授權檔 | 內部決策紀錄、腳本、客戶資料、付費課內容、只給團隊用的規則 | `skills/*/SKILL.md` | 無 |
| `.claude-plugin/**` | 外掛與 marketplace 的名稱、說明；新增技能時說明要跟著加 | 技能內容本身 | — | `skills/**` |

## 新功能放哪

- 新增一個免費技能 → `skills/<技能名>/SKILL.md`，同時更新 `README.md` 的技能表與 `.claude-plugin/` 兩個 json 的說明
- 改編自別人開源的技能 → 同上，並把原本的 LICENSE 放進該技能資料夾
- 給會員看的安裝說明 → `README.md`（Skool 頁面的教學不放這裡）

## 已知超標檔

| 路徑 | 行數 | 燈號 | 拆分票 |
|---|---|---|---|

## 排除

- `**/node_modules/**`
- `**/dist/**`
- `**/build/**`
- `**/.next/**`
- `**/vendor/**`
- `**/__pycache__/**`
- `**/.venv/**`
- `**/migrations/**`
- `**/alembic/versions/**`
- `**/fixtures/**`
- `**/__fixtures__/**`
- `**/testdata/**`
- `**/__snapshots__/**`
- `**/*.generated.*`
- `**/database.types.ts`
- `**/tests/**`
- `**/test/**`
- `**/__tests__/**`
- `**/e2e/**`
- `**/*.test.*`
- `**/*.spec.*`
- `**/test_*.py`
- `**/*_test.py`
- `**/*_test.go`
