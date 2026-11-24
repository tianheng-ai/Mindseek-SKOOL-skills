# MindSeek AI 學院｜免費技能包

給 MindSeek AI 學院（Skool 社群）會員的 Agent 技能。技能是一份寫給 Agent 看的工作說明書，裝上去之後，它遇到那類任務就會照步驟做，不用你每次重講。

社群：https://www.skool.com/mindseek-ai-7923

## 目前有的技能

| 技能 | 做什麼 | 怎麼叫它 |
|---|---|---|
| handoff（交接單） | 收工前讓 Agent 寫一張交接單，下一個對話貼一行就接著做 | 在對話裡說「寫交接」 |
| humanizer（語氣修整） | 把 AI 寫的稿子改回像人寫的，中英文都能用；不改事實、不亂補數字 | 說「用 humanizer 改這段」，再貼上文字或給檔案 |
| pdf-to-markdown（文件先轉再讀） | PDF、Word、簡報、試算表先在你的電腦上轉成 Markdown 文字檔，Agent 再讀轉好的那一份 | 給它檔案，說「先轉成 Markdown 再讀」 |

pdf-to-markdown 用的轉檔工具是微軟開源的 MarkItDown（MIT 授權），第一次用時 Agent 會幫你裝，檔案不會上傳。

humanizer 改編自 MIT 授權的開源技能，加上中文稿的規則；授權條款在 `skills/humanizer/LICENSE`。

## 怎麼裝

### 用 Claude 桌面版或 Codex（ChatGPT 桌面版）

照社群教室「免費技能包」裡該技能那一頁的「安裝」步驟做：複製頁面最下方的安裝指令，貼進一個新對話送出，Agent 會幫你把技能存到對的位置。裝完開一個新對話才會生效。

### 用 Claude Code

在 Claude Code 的輸入框依序送出這兩行：

```
/plugin marketplace add tianheng-ai/Mindseek-SKOOL-skills
```

```
/plugin install mindseek-skool-skills@mindseek-skool
```

裝完重開 Claude Code。

## 裝完後確認

開一個新對話，問 Agent：

```
你現在有哪些技能可以用？
```

清單裡看得到你裝的技能（例如 handoff、humanizer、pdf-to-markdown）就是裝好了。

## 安全提醒

- 這裡的技能都不會要你輸入密碼或金鑰。
- 技能可以叫 Agent 在你的電腦上做事。只裝你看得懂來源的技能。

## 卡住了

到社群的「每週問答串」留言，附上你的輸入和 Agent 回你的那段話。
