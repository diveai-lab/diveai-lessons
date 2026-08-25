# log.md — 變更紀錄

> 這裡記錄**會改變未來檔案的變更或決策**：改了品牌規則、換了資料夾慣例、
> 定了新的元件/風格規格、清理或整併素材、某份講義定稿等。
> 目的是讓下次接手的人或 AI，知道現在的規則跟當初可能不一樣。
>
> **格式**：最新的放最上面。每筆一段：
>
> ```
> ## YYYY-MM-DD ｜ <一句話標題>
> - 改了什麼：
> - 為什麼 / 影響到哪些未來檔案：
> - 誰：
> ```

---

## 2026-08-25 ｜ 慣例升級：投影片一律先寫「最終分頁 .md」才動手做
- 改了什麼：CLAUDE.md 第四節從「內容先行（預設）」改為 **「內容先行（鐵則，不可略過）」**——以後做任何講義／簡報，**一定要先產出 `slide-notes/<slug>.md`（投影片上真正會出現的逐頁文字），才開始生成 HTML**。並明確區分兩份 .md：`ideas/<slug>.md` 是**設計稿**（每頁目的、互動怎麼帶、分鐘數，給帶課者看）、`slide-notes/<slug>.md` 是**最終分頁稿**（投影片實際文字，逐頁對應成品）。「直接做」只代表不停下來等討論，**稿還是要先寫**（同一輪寫完再生成）。第十節重點提醒同步改寫。
- 同時做了：依成品 `lessons/intro-deeplearning/index.html` 逐頁回寫出 `slide-notes/intro-deeplearning.md`（23 頁：S1–S11 ＋ 中場休息頁 ＋ S12–S22），補齊這份講義缺的內容稿。S22 三枚章戳（課程連結／YouTube／免費工具）仍為佔位，已用 ✏️ 標記待補。
- 為什麼 / 影響到哪些未來檔案：**推翻**先前「使用者說直接做就可略過階段一」的例外。日後每份講義三處齊全（`ideas/` → `slide-notes/` → `lessons/`）；要修改任何講義，一律先改 `slide-notes/<slug>.md` 再重新生成。若遇到成品已存在卻缺內容稿，先依成品逐頁回寫再改。
- 誰：yenlung + Claude Cowork

## 2026-08-23 ｜ 第二份講義 intro-deeplearning 完成（完整 23 頁＋兩份學習單）
- 改了什麼：`lessons/intro-deeplearning/`——《一起潛進 AI！》互動工作坊**完整版**（S1–S22＋中場，共 23 張，手帳風）＋兩份 A4 可列印學習單：`worksheet-softmax.pdf`（配 S10）、`worksheet-agent-rolecard.pdf`（配 S19 真人 Agent 班遊，含角色分配與工具呼叫記錄表）。逐頁規劃在 `ideas/intro-deeplearning.md`。已加進首頁 `index.html` 講義庫卡片。
- 慣例：**可列印素材（學習單等）放進該講義資料夾**（`lessons/<slug>/worksheet-*.pdf`），跟簡報一起 self-contained。
- 誰：yenlung + Claude Cowork

## 2026-08-23 ｜ 重組為 GitHub Pages 結構（英文路徑）
- 改了什麼：資料夾整理成 GitHub repo（org `diveai-lab`）。改名：`slides/`→`lessons/`、`入門作業`→`intro-assignment`、`slides_note/`→`slide-notes/`、`asset/`→`shared-assets/`（4 個中文吉祥物檔→英文）、內容稿 .md→英文 slug。新增：根 `index.html`（講義總目錄首頁）、`README.md`、`.nojekyll`、`.gitignore`、`assets/`（首頁圖）。stray `assets/compare.html` 移到 `_to_delete/`。CLAUDE.md 全面改用英文路徑並加 Pages 說明。
- 為什麼 / 影響到哪些未來檔案：URL 會用到的路徑一律英文小寫連字號（Pages 網址友善）。**命名慣例改變**：講義三處用同一英文 slug（`lessons/<slug>/`、`ideas/<slug>.md`、`slide-notes/<slug>.md`），新講義要加進首頁卡片。
- 誰：yenlung + Claude Cowork

## 2026-08-23 ｜ 定案存法：資料夾 + assets/（推翻前一版的單檔內嵌）
- 改了什麼：使用者確認每個簡報都要**自帶 `assets/` 資料夾**（圖 copy 進去、相對路徑引用），整包才能直接提供給同學。CLAUDE.md 第五節改為「資料夾 + assets/」是唯一正本做法；單檔 base64 只用於對話預覽。`slides/入門作業/` 已改成 index.html + assets/（6 張圖）。
- 為什麼 / 影響到哪些未來檔案：**推翻** 08-23 稍早「單檔內嵌為簡報預設」的決定。日後所有簡報一律輸出資料夾 + assets/。
- 誰：yenlung + Claude Cowork

## 2026-08-23 ｜ 入門作業內容微調（問句化、用詞定調）
- 改了什麼：六題全部改成明確問句（學生一看就知道要答什麼）；第 2 題流程圖從「輸入→AI 學到的規則→輸出」改為「輸入→呆一布→輸出」，並加註「不用教統計／關鍵字，只決定輸入與輸出」；第 3 題定調用「幻覺」為主詞（不再用「想像」）。同步更新 `ideas/…學生版.md`、`slides/入門作業/index.html`、`slides_note/入門作業.md`。
- 為什麼 / 影響到哪些未來檔案：**用詞慣例**——講 AI 學習時用「輸入→呆一布→輸出」把中間當黑盒（避免學生誤解要教演算法）；LLM 生成一律稱「幻覺」。之後的講義沿用。
- 誰：yenlung + Claude Cowork

## 2026-08-23 ｜ 完成首份簡報 slides/入門作業/；確立「單檔內嵌」為簡報預設存法
- 改了什麼：(1) 依 `ideas/呆一布AI共學_入門作業_學生版.md` 做出 10 頁手帳風簡報 `slides/入門作業/index.html`，逐頁稿見 `slides_note/入門作業.md`。(2) CLAUDE.md 第五節新增兩種 self-contained 存法：**A 單檔 base64 內嵌（簡報預設）** 與 B 資料夾+assets/；簡報一律用 A（能在對話裡預覽、不破圖）。
- 為什麼 / 影響到哪些未來檔案：日後簡報預設輸出單一 `index.html`（圖片內嵌）；互動頁或需手動抽換圖時才用 B。
- 誰：yenlung + Claude Cowork

## 2026-08-23 ｜ 定案專案預設模版：C 手帳貼紙風
- 改了什麼：確定三款簡報模版（A 雲朵天空風／B 卡片清爽風／C 手帳貼紙風）中，**C 手帳貼紙風為預設**。沒有特別指定時一律用 C；A、B 保留給對外形象與正式計畫型簡報。第一份參考實作為 `slides/入門作業/`。
- 為什麼 / 影響到哪些未來檔案：日後生成講義／簡報若未指定風格，直接套 C。CLAUDE.md 第六節已更新。
- 誰：yenlung + Claude Cowork

## 2026-08-22 ｜ 專案指引檔更名為 CLAUDE.md
- 改了什麼：把 `AGENT.md` 更名為 `CLAUDE.md`（符合原本習慣），內容不變，內部引用一併更新。
- 為什麼 / 影響到哪些未來檔案：日後提到專案指引一律指 `CLAUDE.md`；舊的 `AGENT.md` 已移除。
- 誰：yenlung + Claude Cowork

## 2026-08-22 ｜ 建立專案指引與本 log.md
- 改了什麼：新增專案指引（現為 `CLAUDE.md`）與 `log.md`（本檔）。確立兩項慣例：(1) 講義同時有「A 互動式學習頁」與「B 翻頁式簡報」兩種產物；(2) 每份講義獨立資料夾、主檔 `index.html`、素材 copy 進自己的 `assets/`，完全 self-contained。
- 為什麼 / 影響到哪些未來檔案：作為所有講義製作的共同規則來源；日後 `slides/<主題>/` 下的成品都依此結構與品牌規範產出。
- 誰：yenlung + Claude Cowork

## 2026-08-22 ｜ 待整併：`asset/` 與 `assets/` 名稱易混淆
- 改了什麼：（尚未動手）記錄觀察——根目錄同時有素材庫 `asset/`（吉祥物/logo/貼圖）與一個小寫 `assets/`（內含 `compare.html`）。
- 為什麼 / 影響到哪些未來檔案：兩者名稱只差一個 s，容易引用錯；建議把 `assets/compare.html` 移走或整併，確認後再更新此筆。
- 誰：Claude Cowork（提醒）
