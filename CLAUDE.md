# CLAUDE.md — 呆一布 AI 共學實驗室・講義專案指引

> 這份檔案（`CLAUDE.md`）是給 AI（Claude Cowork）與人類協作者看的「專案憲法」。
> 動手做任何事之前，先讀這份，再讀 `log.md`（近期會影響決策的變更）。
> 有任何慣例改變，請同步更新這份與 `log.md`。

---

## 一、我們在做什麼

政大「呆一布 AI 共學實驗室」（DiveAI）製作各種 **AI 相關的教學講義**，給同學使用。

- 講義一律是 **HTML + CSS + JavaScript** 格式（不是 PDF、不是投影片檔）。
- 每份講義 **self-contained**：一個資料夾、主檔叫 `index.html`、用到的素材都 copy 進自己的 `assets/`，用相對路徑引用。可以單獨打開、單獨分享、單獨部署。
- 調性沿用 DiveAI 品牌：**日系淡雅可愛**——低彩度粉彩、大量留白、圓潤造型、柔和陰影、吉祥物「呆一布」陪伴。中文一律 **全形標點**（，。、：「」！？）。

吉祥物設定（講義語氣可帶入）：**呆一布是一隻呆萌機器人**——它要人給輸入、輸出和範例，不會自己搞定一切。認識它、不怕它，還能一起完成事情。

---

## 二、兩種產物：互動學習頁 vs 翻頁簡報

這個專案同時做兩種東西，**動工前先確定是哪一種**（不確定就問使用者）：

### A. 互動式學習頁（「講義」本體）
給同學**自己讀、自己操作**的網頁。特徵：
- **可捲動**的長頁面（不是一頁一頁翻），像一份會動的講義。
- 可嵌入 **互動 demo、可調參數的小工具、隨堂練習、可展開的解答**。
- 目標是「學生自學也看得懂、能動手玩」。
- 何時用：概念教學、動手做單元、課後自學材料。

### B. 翻頁式簡報（slides）
上課時老師投影、`←` `→` 或空白鍵翻頁的 self-contained HTML。
- 直接沿用 `diveai-slides` skill 的三款風格與骨架（見下）。
- 何時用：課堂講述、對外介紹、工作坊開場。

### C. PowerPoint 檔（`.pptx`）
老師要**在 PowerPoint／Keynote 裡自己改**、投影機播放的簡報檔。
- 一律從 `ppt/diveai-ocean-template.pptx` 長出來（骨架＝`reference/投影片範本.pptx`），成品放 `ppt/<slug>.pptx`。
- 作法與色票見 `diveai-pptx` skill。
- 何時用：要交給別人接手編輯、要離線播放、要沿用既有 PPT 教材時。

> 三種都用 DiveAI 品牌色票、字體、吉祥物素材；差別在**版型與互動**：A 是可捲動可操作的學習頁，B 是固定 16:9 翻頁網頁，C 是可編輯的 PowerPoint 檔。

**人工定稿成品放 `ppt-final/`**：以上 A／B／C 是「可再生成」的產物；老師在 Keynote／PowerPoint 裡**親手精修定稿**後的最終檔（`.key` 與匯出的 `.pdf`）另存在 `ppt-final/<slug>/`，檔名用英文 slug。這是「人手最後定稿、要一起上 GitHub」的成品層，**AI 不自動覆蓋**。相對地 `ppt/<slug>.pptx` 是 AI 用 diveai-pptx 生成、可再重跑的版本。

---

## 三、資料夾結構

> **此資料夾就是 GitHub repo 的根目錄**（org：`diveai-lab`）。要上 GitHub Pages，所以 **URL 會用到的路徑一律用英文小寫、連字號**；中文名只留在 `ideas/`、`slide-notes/` 這類不會出現在網址的內容稿裡也儘量避免。

```
呆一布講義/                    （= repo 根，GitHub Pages 網站根）
├── index.html            ← 講義總目錄首頁（列出所有講義，連到各 lessons/…）
├── README.md             ← repo 說明
├── .nojekyll             ← 讓 GitHub Pages 不跑 Jekyll（純靜態站必備）
├── .gitignore            ← 忽略 .DS_Store、_to_delete/ 等
├── CLAUDE.md             ← 本檔（專案指引）
├── log.md                ← 變更紀錄
├── assets/               ← 首頁用的圖（logo.png、dive.png）
├── shared-assets/        ← 共用素材庫（吉祥物、logo、人物貼圖）※製作時複製到各講義，勿直接改原檔
├── ideas/                ← 想法／學生版內容（.md），檔名用英文 slug（如 intro-assignment.md）
├── slide-notes/          ← 逐頁內容稿（.md），檔名用英文 slug
├── reference/           ← 外來參考檔（老師既有的投影片範本等），只讀不改
├── ppt/                 ← PowerPoint 成品與範本：diveai-ocean-template.pptx ＋各講義 <slug>.pptx
├── ppt-final/           ← 人工定稿成品：老師在 Keynote 精修後的 .key ＋匯出 PDF（每份講義一個 <slug>/ 子資料夾）
└── lessons/              ← 實際成品（HTML）：每份講義一個英文 slug 子資料夾
    └── <english-slug>/       如 intro-assignment/
        ├── index.html
        └── assets/           ← 這份講義自帶的素材（從 shared-assets/ copy 過來並改英文檔名）
```

**命名：每份講義用英文 slug**（小寫、連字號），三處一致：`lessons/<slug>/`、`ideas/<slug>.md`、`slide-notes/<slug>.md`。首份：`intro-assignment`（入門作業）。

**素材庫 `shared-assets/`**（共用來源，製作時複製到各講義的 `assets/`，不要直接改動原檔；檔名皆英文）：
- 吉祥物：`dive_plush.png`（3D 絨毛版）、`dive_2d.png`（2D 版）、`dive_logo_mark.png`、Logo：`logo.png`
- DIVE 表情組：`dive_wave / dive_explain / dive_happy / dive_thinking / dive_confused / dive_cheer`（`dive_*.png`）、`DIVE QA01/02.png`
- 各角色表情貼圖：`girl_hy_*`、`mc01_*`、`salima_*`（老師）、`tng_*`、`toto_*`、`wenwen_simple_*`（問問）、`yenlung_*`、`boy0*`、`girl0*` 等（多為**透明背景**）
- 這些是「小圖貼」，用來讓講義有溫度、標示角色對話、當段落插圖。

**GitHub Pages**：repo push 到 `diveai-lab` 後，在 Settings → Pages 把來源設為 `main` 分支根目錄。網址會像 `https://diveai-lab.github.io/<repo>/`（首頁）、`https://diveai-lab.github.io/<repo>/lessons/intro-assignment/`（各講義）。

---

## 四、工作流程：內容先行（鐵則，不可略過）

做任何講義／簡報，**一律先產出 `slide-notes/<slug>.md`（投影片最終逐頁內容），才開始做 HTML**。沒有這份 .md 就不動手生成成品——這是硬性規定，不是預設值。

兩份 .md 的分工要分清楚：

- `ideas/<slug>.md`＝**設計稿**：每頁的目的、互動怎麼帶、分鐘數、給帶課者看的說明。
- `slide-notes/<slug>.md`＝**最終分頁稿**：投影片上**真正會出現的文字**，一頁一段，逐頁對應成品。

流程：

1. **想法 → 內容稿**：從 `ideas/<slug>.md` 的構想，先在 `slide-notes/<slug>.md` 寫出**逐頁/逐段的文字內容**（標題、重點、範例、練習、對話），交使用者討論修改。內容稿開頭記：`形式(A互動頁/B簡報)`、`用途`、`成品路徑`、`狀態`、`頁數/段數`；待補處用 `✏️` 標記。
2. **定稿後生成**：使用者說「定稿」，才依內容稿與指定風格，在 `lessons/<slug>/` 生成 `index.html` 與 `assets/`。生成後把內容稿狀態改成 ✅ 定稿。
3. **要修改**：回 `slide-notes/<slug>.md` 改文字，再重新生成。
4. **加進首頁**：新講義做好後，在根目錄 `index.html` 的「講義庫」加一張卡片，連到 `lessons/<slug>/`。

**「直接做」不等於跳過 .md**：使用者說「直接做」時，可以不停下來等討論，但仍要**先把 `slide-notes/<slug>.md` 逐頁寫完**，再接著生成 HTML（同一輪做完即可）。

若成品已存在卻缺內容稿（歷史遺留），**先依成品逐頁回寫**補上 `slide-notes/<slug>.md`，之後的修改都從那份稿開始。

---

## 五、每份講義：獨立資料夾 + self-contained（定案）

- 路徑：`lessons/<slug>/index.html`，主檔一律叫 `index.html`。
- 圖片以**網頁尺寸**處理（人物約高 600–680px、logo 約寬 440px；透明去背、裁掉多餘空白），不要直接塞原尺寸大圖。
- **存法（標準）：資料夾 + assets/**。每個講義用到的圖，一律 **copy 一份進 `lessons/<slug>/assets/`**（不共用 `shared-assets/`），並改成好引用的英文檔名（`logo.png`、`dive_wave.png`、`teacher.png`…），`index.html` 以相對路徑 `assets/xxx.png` 引用。
  - 理由：整個 `lessons/<slug>/` 資料夾**可以直接整包提供給同學**、丟 GitHub Pages、寄給別人都不破圖，維護時也不牽動別的講義。**這是本專案的定案做法。**
- 想在 Cowork 對話裡預覽時，可另外產一份「圖片 base64 內嵌的單檔」給預覽用，但**存進專案的正本一律是資料夾 + assets/**。
- 首份參考實作：`lessons/intro-assignment/index.html` + `lessons/intro-assignment/assets/`。
- 拿不到某素材時，**不要破圖**：標題改純文字「DiveAI ・ 呆一布 AI」，吉祥物槽位留空。

---

## 六、品牌規範（沿用 diveai-slides，勿改）

**色票**（CSS 變數）：
```
--cream:#FBF7EF 米白底   --cream2:#F3ECDC 暖米
--sky:#8FCFE2 天藍(吉祥物主色)  --sky-soft:#D6EEF6 淺天藍  --blue:#5FA8C4 中藍(重點)
--navy:#2E5C74 深藍(標題/文字)  --blush:#F4B3BE 腮紅粉  --blush-soft:#FBDDE2
--teal:#7CCBC9 湖水綠  --yellow:#F7E6A8 螢光黃(僅手帳風)  --ink:#3C4B55 內文
```

**字體**（Google Fonts）：標題/英數用 `M PLUS Rounded 1c`，中文內文用 `Noto Sans TC`。

**三款風格**（本專案已做出實際模版，見 `lessons/intro-assignment/` 為 C 風格的參考實作；互動學習頁沿用同一套色票與元件語彙）：
- **A 雲朵天空風**：天空漸層＋雲朵＋漂浮小點＋吉祥物探頭。用於介紹、募資、提案、願景、對外形象。
- **B 卡片清爽風**：頂部品牌帶＋白色資訊卡＋卡片左側彩色條。用於計畫書、資料密度高的正式簡報、對評審。
- **C 手帳貼紙風**：點點方格紙＋紙膠帶＋虛線便利貼＋對話框＋貼紙徽章＋螢光筆底線。用於工作坊、教學、學生作業、科普。

**PPT（`.pptx`）另有一套預設**：**A 海洋潛水風**——標題字 `Noto Sans TC Bold`、內文字 `Yuanti TC Bold`，背景 `#F4FAFC`、標題條 `#8FCFE2`、頁尾帶 `#5FA8C4`、標籤藥丸 `#2E5C74`。完整色票（8 組卡片色、狀態色、圖表色序）在 `diveai-pptx` skill 的 `references/palette.md`；備援有 B 奶油手帳風、C 薄荷清爽風。網頁講義維持下面的預設。

> **★ 網頁講義預設模版：C 手帳貼紙風。** 沒有特別指定時，講義／簡報一律用 C。A、B 保留給對外形象與正式計畫型簡報，需要時再指定。

**每張投影片固定用到的人物**：DIVE 表情版（`dive_wave` 揮手＝標題、`dive_explain` 解說＝內頁、`dive_happy` 開心＝結尾）為主；配角可換其他人物（老師、同學），用「對話框＋名牌」帶出，示範不一定都是 DIVE。

不確定風格 → 預設 C；場合明顯偏正式再考慮 A／B。

---

## 七、互動學習頁的額外慣例

- **可捲動**為主，段落之間留白充足；重要互動可用「卡片」框起來。
- 互動 demo / 小工具用**原生 JS**，寫在同一個 `index.html` 裡（single-file，除非使用者另有要求）。
- **瀏覽器儲存注意**：在對話中預覽時 `localStorage / sessionStorage` 不保證可用——互動狀態一律存記憶體（JS 變數）即可；真的要持久化再另外討論。
- 練習題可用「點擊展開解答」；參數可用 slider / 輸入框即時反映。
- 手機也要能看：用相對單位、`max-width:100%`、flex/grid，避免整頁橫向捲動。
- 一樣 self-contained：外部只允許 Google Fonts，其餘 CSS/JS 內嵌、圖放自己的 `assets/`。

---

## 八、命名慣例

- **一律英文小寫 slug**（用連字號，不用空白或中文；因為會出現在 GitHub Pages 網址）。
- 講義資料夾：`lessons/<slug>/`，主檔一律 `index.html`。
- 內容稿：`slide-notes/<slug>.md`；想法／學生版：`ideas/<slug>.md`。三處 slug 一致。
- 各講義自帶素材檔名求好引用：`logo.png`、`dive_wave.png`、`teacher.png`…

---

## 九、log.md 的用途

`log.md` 記錄**「會改變未來檔案」的變更或決策**——例如：改了品牌色、換了資料夾慣例、定了某個新元件規格、清理/整併素材、某份講義定稿。目的是讓下一次（不管是人還是 AI）接手時，知道現在的規則跟當初可能不一樣。格式見 `log.md` 開頭。

---

## 十、給 AI 的重點提醒

1. **先讀 CLAUDE.md 與 log.md**，再動工。動工前先確認要做 A 互動頁、B 翻頁簡報 還是 C PowerPoint 檔（`.pptx` 走 `diveai-pptx` skill）。
2. **內容先行（鐵則）**：一定先有 `slide-notes/<slug>.md` 的逐頁最終文字，才生成 HTML；說「直接做」也只是不等討論，稿還是要先寫。`ideas/` 是設計稿、`slide-notes/` 是投影片實際文字，兩者不可混用。
3. **色票、字體勿改**；中文全形標點。
4. **每份講義 self-contained**：素材 copy 進自己的 `assets/`，相對路徑引用，拿不到就留空不破圖。
5. **不要直接改 `shared-assets/` 原檔**（那是共用來源庫）。
6. **檔名／資料夾一律英文 slug**（GitHub Pages 網址友善）；新講義記得加進首頁 `index.html`。
7. 有影響未來的改動 → 記進 `log.md`。

---

## 待辦 / 觀察

- repo 已建立：`https://github.com/diveai-lab/diveai-lessons`。GitHub Pages 待開（Settings → Pages，來源 `main` 根目錄）。
- `ppt/` 另有兩款備援風格 `style-b-cream-note.pptx`、`style-c-mint-clean.pptx`，確認不需要後可刪。
- `_to_delete/`（舊 AGENT.md、compare.html）確認無誤後可整個刪掉；已加入 `.gitignore` 不會上傳。
