# Claude 分享會內容

# Page 1 首頁

簡報介面：
標題：Claude 使用分享會

---

# Page 2 大綱

- Claude 基礎設置
- 進入實務的範例
- 週進度助手
- Google Sheet 翻譯助手
- 遊戲專案自動更新多語系表
- Cocos MCP 搭建 Unity 介面
- 醞釀中的想法
- Q&A

---

# Page 3 Claude 基礎設置

介紹內容：
- 我的開發環境是 Mac，使用 Homebrew 來安裝 Claude。
- Homebrew 是 Mac 上的套件管理工具，幫助我們更方便地安裝與管理軟體。
- 透過 Homebrew 一行指令就能完成 Claude 的安裝。

簡報介面：
- Homebrew 圖示 [img/homebrew.svg] + Homebrew 簡介
- 安裝 Claude 的指令 + 安裝說明

```bash
brew install claude-code
```

---

# Page 4 開啟 Claude CLI

介紹內容：
- 一般開啟方式：`claude`
- 我推薦使用：`claude --dangerously-skip-permissions`，跳過每次操作的權限確認，工作流程更順暢（僅限個人開發機使用）。
- 額外推薦兩個 Terminal 介面工具：
  - **cmux**：遠端 Server 上的多窗終端管理，適合在編板機上同時跑多個 Claude
  - **BetterAgentTerminal**：本機更好的 Claude CLI 互動介面，可視化對話歷程與工具呼叫

簡報介面：
一般開啟方式：
```bash
claude
```

推薦開啟方式：
```bash
claude --dangerously-skip-permissions
```

cmux、BetterAgentTerminal 的圖示與簡介。

實際操作：
- 開啟編板機的 cmux 介面給觀眾看
- 開啟本機的 BetterAgentTerminal 介面給觀眾看

---

# Page 5 Terminal 介面工具

介紹內容：
- 緊接著上一頁的 cmux / BetterAgentTerminal 簡介，這頁直接放實際介面截圖讓觀眾看清楚兩者長相。

簡報介面：
- 左：cmux 介面截圖 [img/cmux.png] + cmux logo + 簡短說明
- 右：BetterAgentTerminal 介面截圖 [img/BetterAgentTerminal.png] + logo + 簡短說明

---

# Page 6 Claude 記憶機制

介紹內容：
- **Memory 記憶**：你可以主動告訴 Claude 想讓他記住什麼（例如角色、偏好、工作習慣），之後的對話就會沿用這些資訊。
- **CLAUDE.md 專案說明**：使用 `/init` 指令在專案根目錄產生說明文件。如果該資料夾裡面已經有資料了，他會再幫你分析這些資料後，在寫進 CLAUDE.md 裡面。每次開啟 CLI 時自動載入作為上下文。

簡報介面：
- Memory 與 CLAUDE.md 雙卡片對比
- 兩者差異表格（用途、範圍、建立方式）

實際操作：
1. 問 Claude：「你知道我是誰嗎？」
2. 接著問：「你把我的相關資訊都存在哪裡？」
3. 帶聽眾打開 `~/.claude/projects/.../memory/MEMORY.md` 看實際內容
4. 切到 `/Users/pinhsu/Documents/Jenkins Unity包版`，開啟 claude，執行 `/init` 指令

---

# Page 7 進入實務的範例

介紹內容：
> 前面快速帶過了 Claude 的基礎設定。
> 但今天真正想分享的重點不在設定，而是在「**解決問題**」——一個想法從萌芽、執行到產生結果的完整過程。

> 接下來不掉書袋。我們不拆解「Prompt 怎麼寫」，也不解釋什麼是 Context、Plan、Agent，或最近很紅的 Harness。
> 因為很多時候，我們學了一堆 AI 專有名詞，但面對實際工作時，還是不知道能拿它解決什麼問題。

> 這就像是你買了一把最頂級的「鋤頭」，知道怎麼揮動它，但卻不知道這塊田要「種什麼作物」，那麼工具再強大也只是白搭。

> 所以今天只談「真實場景」——當你腦中只有一個模糊的「想法」時，可以如何透過 Claude 一步步把它落地，變成具體的「執行方案」。

簡報介面：
- 兩段引言 + 鋤頭比喻

---

# Page 8 週進度助手

介紹內容：
- **痛點**：每週一開會分享進度，總要花時間回想上週做了什麼。對我來說就像每天早上煩惱「要穿什麼」一樣，耗費不必要的腦力。
- **解決方案**：讓 Claude 自動對接工作軌跡
  - **專案管理**：串接 ClickUp MCP（讀取任務狀態）
  - **程式開發**：抓取 GitLab 紀錄（讀取程式碼提交紀錄）
- 把這兩項資料整合，自動生成週報。我則把思考重心擺在「**這週要做什麼**」。

簡報介面：
- 利用左右對比，或箭頭流程圖呈現自動化過程

實際操作：
- 直接展示生成週報
- 接著展示「來看看誰上週都沒有更新進度」

---

# Page 9 簡單介紹 MCP

介紹內容：
> 簡單來說，MCP 就是 AI 的「萬用轉接頭」。

- **過去**：AI 像被關在房間裡的高智商大腦，無法直接讀取電腦檔案、公司資料庫或各種生產力工具。要讀取這些資料，開發者必須為每一種軟體（Google Drive、Notion、GitHub 等）寫專門的串接程式，非常麻煩。
- **MCP**：定出一個開源的標準通道。只要資料端支援 MCP，AI 就能透過這個通道，直接、安全地讀取外部資料並與之互動。

簡報介面：
- 過去 vs 有了 MCP 的對比卡片
- 常見支援的工具標籤（Google Drive、Notion、GitHub、ClickUp、GitLab、Slack...）

---

# Page 10 Google Sheet 翻譯助手

介紹內容：
- **痛點**：企劃克克在做遊戲的多國語系表，嘗試將所有內容丟給 Gemini，但翻譯結果不理想。所以改為**一句一句**請 AI 翻譯，再**一句一句**貼回 Google Sheet。
- **想法**：
  - 1 款遊戲 × 20 分鐘
  - 10 款遊戲 × 5 種語言 = ? 天
  - 能不能讓 Claude 自動翻譯，直接更新到 Google Sheet？

多國語系表網址：https://docs.google.com/spreadsheets/d/1JAsBa9bzaInqtDErUXCpBY7kSIxlrlXJNJcKvi_9yWA/edit?pli=1&gid=457309023#gid=457309023

簡報介面：
- 標題加上 Google Sheet logo [img/google_sheet_logo.png]
- 左側：痛點 + 想法雙卡片
- 右側：試算表截圖 [img/page9.jpeg]

---

# Page 11 Google Sheet 翻譯助手 — 基礎設置

介紹內容：
1. **建立資料夾 + /init**：建立 `Google Sheet 翻譯助手` 資料夾，開啟 claude 執行 `/init` 產生 CLAUDE.md 說明文件。
2. **放入 JSON 憑證**：之前做 Unity Editor 工具時就知道需要 Google API 憑證，把它一起放進資料夾。
3. **提供 Google Sheet 網址**：告訴 AI 去讀取這份試算表，翻譯缺少的內容（使用者需要先提供基本英文內容，不然 AI 不知道要翻譯什麼）。
4. **驗證 + 補上 CLAUDE.md**：請 AI 翻譯，結果正確後，再請他把流程補進 CLAUDE.md。

> 這個資料夾等於是一個 **AI 的工具箱**，裡面有說明文件、憑證檔案、Google Sheet 的網址。

簡報介面：
- 標題加上 Google Sheet logo [img/google_sheet_logo.png]
- 左側：四個步驟卡片
- 右側：工具箱檔案結構圖

---

# Page 12 Google Sheet 翻譯助手 — 如何讓企劃使用

介紹內容：
- **問題**：現在工具只在我的電腦上，我該怎麼讓企劃使用？
- **解法**：
  - 我們遊戲端有一台編板機，上面已建置一支 Discord Bot。
  - 把 `Google Sheet 翻譯助手` 資料夾放進編板機。
  - Discord Bot 新增一條 `/translate` 指令，企劃用自然語言觸發，例如：「幫我完成 S099 的翻譯」。
- Discord Bot 收到指令後執行：

```javascript
spawn('claude', [
  '--print',
  '--output-format', 'stream-json',
  '--verbose',
  '--dangerously-skip-permissions',
  '--model', 'sonnet',
  userPrompt,   // 企劃輸入的自然語言
], {
  cwd: '/path/to/Google Sheet 翻譯助手',
});
```

- **Bot 不解析參數、不組指令，只負責把企劃的話轉交給 Claude。**
- Claude 啟動後自己讀取該目錄下的 CLAUDE.md，決定怎麼執行翻譯。
- 透過 `stream-json` 監聽輸出，每 5 秒更新一次 Discord 訊息顯示進度。
- 使用者完全不需要學習成本——只要用 `/translate` 加上一句自然語言就行。

簡報介面：
- 標題加上 Discord logo [img/discord_logo.webp]
- 左側：問題 / 解法卡片
- 右側：「Discord Bot 核心程式碼」卡片，包含 spawn 程式碼 + stream-json 進度說明 + 實際 Discord 互動畫面截圖 [img/discord-feedback.png]

---

# Page 13 Google Sheet 翻譯助手 — 校正 AI

介紹內容：
- 剛剛是介紹整體流程，這頁要講過程中我和 AI 的互動。
- 過程中 AI 會有不理想的結果，我會告訴他：「這樣不行，應該怎麼做」，然後請他把這條反饋寫回 CLAUDE.md。
- 之後企劃使用時遇到問題，也用同樣方式校正——AI 的準確性就會逐次提升。

以下為實際的反饋紀錄：

```text
## 使用者反饋紀錄

### 反饋 1：「更新 001 的字串表」不該更新 Common/Dialog
- 錯誤行為：同時更新了 Common_StringTable 和 Dialog_StringTable
- 正確行為：只更新 S001_StringTable（遊戲專屬字串表）
- 規則：當使用者說「更新 XXX 的字串表」，預設只更新該遊戲專屬表，不要連共用表一起更新

### 反饋 2：更新字串表時不該回「翻譯流程已結束」
- 錯誤行為：使用者沒要求翻譯，但 Bot 回「翻譯流程已結束」
- 規則：摘要必須用 `[更新摘要]` 前綴，只有翻譯時才用 `[翻譯摘要]`

### 反饋 3：必須明確列出新增/刪除的 key
- 錯誤行為：只回報「新增 key：1 個」
- 正確行為：回報「新增 key：test」，列出具體名稱
- 規則：在回報中列出每個 key 名稱

### 反饋 4：更新後必須自動推到 git remote
- 錯誤行為：更新後沒有 commit/push
- 規則：除非明確要求 dry-run / 預覽，否則一律加 `--commit` 參數

### 反饋 5：沿用其他表已有的翻譯
- 錯誤行為：每次都重新翻譯，導致同一句話在不同遊戲表出現不同譯法
- 規則：翻譯前先檢查其他遊戲表是否已翻過相同內容；若有，直接沿用，不要重新翻譯
```

簡報介面：
- 四條反饋以卡片並列呈現 + 收尾金句：「每次反饋都寫回 CLAUDE.md → AI 的準確性逐次提升」

---

# Page 14 Google Sheet 翻譯助手 — 成果

介紹內容：
- 這樣企劃就可以花更多時間在**遊戲發想**上，翻譯的工作就交給 AI 處理。
- ……但是我要負責維護 😅（自嘲一下作為段落收尾）

簡報介面：
- 左：企劃使用後開心的照片 [img/happy_man.jpg]
- 右上：主訊息（強調「遊戲發想」「AI」）
- 右中：italic + 表情符號帶出自嘲句「...但是我要負責維護 😅」
- 右下：AI 透過 Google API 編輯試算表的紀錄截圖 [img/ai-editor-google-sheet.png]，作為「AI 真的在做事」的證明

---

# Page 15 遊戲專案自動更新多語系表 — 痛點

介紹內容：
- **接下來想到的問題**：能不能在**不開啟遊戲專案**的情況下，更新遊戲的多語系表？
- **原本的流程**：
  1. 用 Unity 開啟遊戲專案
  2. 到 Google Sheet 下載該遊戲的 CSV 檔案
  3. 開啟 Unity Editor 的多國語系工具，將 CSV 匯入
- 之後做了一個一鍵更新工具，省去下載 CSV 和匯入的動作，但還是要開 Unity。
- **問題**：未來會有很多款遊戲，要一款一款開啟更新，太麻煩。

簡報介面：
- 三步驟流程圖：
  - Step 1：Unity logo [img/unity_logo.avif]
  - Step 2：Google Sheet 截圖 [img/googleSheet.png]
  - Step 3：Unity Localization Tables 截圖 [img/unity-localization-string.png]
- 「問題」區塊：自製一鍵更新工具截圖 [img/unity_editor_tool.png] 作為佐證
- 收尾問題：「能不能不開遊戲專案，就自動更新多語系表？」

---

# Page 16 遊戲專案自動更新多語系表 — 解法

介紹內容：
- 套用前面同樣的模式：
  1. 建立 `string-table-updater` 資料夾，撰寫需求文件
  2. 把資料夾放進編板機
  3. 讓 `/translate` 指令也能呼叫這個功能
- 在 Discord 說一句「幫我更新 Slot014 專案的多語系表」，Bot 就會自動讀取該專案資料、更新多語系表，並推到 Git。

**幕後實際在做什麼（給技術觀眾的補充）**：
1. Discord Bot 收到指令 → spawn Python CLI（`update_string_tables.py`）
2. Python 透過 **Google Sheets API**（service account JWT 認證）抓取試算表內容
3. 直接寫入 Unity 的 `.asset`（YAML）和 `.csv` 檔案 — **完全不需要開啟 Unity**
4. 自動 `git commit + push` 到 SlotFramework submodule

> 一旦建立了「AI 工具 + Discord Bot」這個基礎建設，後續每個自動化都只是加一條指令的事。

簡報介面：
- 上半左：三步驟卡片
- 上半右：「在 Discord 一句話搞定」框（含 Discord logo [img/discord_logo.webp]）
- 中間：「幕後在做什麼」四步流程圖（Discord Bot → Google Sheets API → 改 .asset/.csv → git push）
- 強調金句：「⚡ 全程不需要開啟 Unity」
- 底部：收尾金句

---

# Page 17 Cocos MCP 搭建 Unity 介面

介紹內容：
- **背景**：阿貴想做一個 Cocos 版本，用來比對和 Unity 的差異。
- **想法**：能不能用 MCP 讓 AI 直接在 Cocos 引擎裡搭建介面？
- **流程**：
  1. 先在 Unity 中搭建一個簡易的參考介面
  2. 讓 Claude 下載並設定 Cocos Creator 的 MCP
  3. 叫 AI 在 Cocos 中複刻一樣的介面

實際操作：
- 展示 Unity 中搭建好的介面
- 接著展示 Cocos 中由 AI 搭建的介面

簡報介面：
- 三步驟卡片（Step 1 加 Unity logo [img/unity_logo.avif]、Step 2/3 加 Cocos logo [img/cocos_logo.png]）

---

# Page 18 醞釀中的想法

介紹內容：
- **自動更新多語系素材**：延伸自字串表的功能，去 NAS 抓取該遊戲的多語系素材，自動套用到素材表。未來新增語系（剛好我們快要新增日文）只要做一次初步設定，其他遊戲就能直接套用。
- **自動檢查美術素材完整性**：讓 AI 比對素材清單與實際檔案，找出遺漏。
- **自動填寫遊戲企劃書**：克克之前的構想。我跟他說：「不懂 AI 沒關係，先把你想自動化的內容寫下來，那就是 CLAUDE.md。」讓不懂 AI 的企劃也能先有個行動。
- **新專案自動初始化**：開新遊戲時，請 AI 完成基本的 Loading 介面、核心設定等。讓開發人員更專注在遊戲表演的串接上。

> 有些繁瑣的事情，都可以試著構想——讓 AI 來幫我們完成。

簡報介面：
- 第一個構想「自動更新多語系素材」做為主打卡片，左文右圖（多語系素材表截圖 [img/unity-localization-asset.png]）
- 其餘三個構想排成 3 欄
- 收尾金句

---

# Page 19 彩蛋 — 這份簡報怎麼做出來的？

介紹內容：
- 突然想到——這份簡報整場沒打開過 Keynote，全程跟 Claude 對話完成。
- **流程**：
  1. 先寫 `CLAUDE.md`（每頁要講什麼、放什麼資訊用 markdown 列清楚）
  2. 交給 Claude 寫成 HTML 簡報（一句話就生出 slides.html）
  3. 持續對話微調（色調、排版、補圖、改字、修錯）
  4. 每補一張圖 → Claude 自動判斷該放哪一頁、什麼排版
- **真實對話片段**：
  - 「色調還是太灰暗了」
  - 「又太亮的感覺」
  - 「Page 4 的排版沒有改到」
  - 「Google Sheet logo 長寬比都跑掉了」
- 收尾金句：「**如果連簡報都能這樣做出來，那工作上的繁瑣事更不用說了。**」

簡報介面：
- 左側：4 個步驟卡片描述製作流程
- 右側：仿 chat 對話氣泡（橘色 = 我、米色 = Claude）展示真實對話片段
- 收尾金句框

---

# Page 20 Q&A

> 如果你有重複性的工作，我們可以一起腦力激盪能不能用 Claude 解決。
