# SETUP.md — 新電腦接手這個專案的清單

> 換一台電腦（或第一次在某台電腦）開始做「呆一布講義」時，照這份從上往下做一次。
> 目的：讓每台電腦上的 Claude 看到**一樣的檔案、一樣的規則、一樣的工具**，避免「這台做出來怎麼不一樣」。
> 日常規則看 `CLAUDE.md`，目前進度看 `NOTES.md`，歷史決策看 `log.md`。

---

## 一、讓檔案到位（Dropbox）

- [ ] 安裝 Dropbox、登入，**等同步完成**（圖示顯示「已同步」）再開始。
- [ ] 在 `Dropbox/Claude Cowork/呆一布講義` 上按右鍵 →「**設為可離線使用**」（Make available offline）。設成「僅線上」的話，Claude 讀不到檔案內容。
- [ ] 看一下有沒有「衝突的副本」（conflicted copy）或 Dropbox 同步錯誤，有就先處理。

各台電腦上的路徑不同，但是**同一份檔案**：

| 電腦 | 專案路徑 |
|---|---|
| iMac | `/Volumes/iMac eHD/Dropbox/Claude Cowork/呆一布講義` |
| Windows 主機 | `C:\Users\<使用者>\Dropbox\Claude Cowork\呆一布講義`（Git Bash：`/c/Users/<使用者>/Dropbox/Claude Cowork/呆一布講義`） |
| 其他電腦 | 填在這裡：`…` |

## 二、Git：其他電腦「什麼都不要做」

- `.git` 只存在 iMac，已排除 Dropbox 同步，所以**其他電腦的這個資料夾裡本來就沒有 `.git`，這是正常的**。
- ❌ 不要在其他電腦這個資料夾裡 `git init` 或 `git clone`。
- 要 commit / push 時，回 iMac 做（細節見 `CLAUDE.md` 第十節）。

## 三、安裝 Claude 並對齊

- [ ] 安裝 **Claude Desktop**，用同一個帳號登入，連接上面那個專案資料夾。
- [ ] 若要用 **Claude Code**：安裝後先 `claude update`，讓版本跟其他電腦一致。Windows 上用 **Git Bash** 跑（直接用 Windows 路徑，跟 Claude Desktop 看到同一批檔案）。
- [ ] 確認帳號裡的 skills 可用：`diveai-slides`（網頁簡報）、`diveai-pptx`（PowerPoint）、`diveai-docs`（文件）。
- [ ] 個人層級的 `~/.claude/CLAUDE.md`（若有）跟其他電腦保持一致。**跟本專案有關的規則一律寫進專案的 `CLAUDE.md`**，不要只寫在某台電腦的個人設定裡。

## 四、執行環境與字型

- [ ] **Python 3 ＋ `python-pptx`**（生成 `ppt/*.pptx` 用）：`pip install python-pptx`
- [ ] **字型**：
  - `Noto Sans TC`（PPT 標題、網頁內文）——Mac / Windows 都要裝。
  - `Yuanti TC`（PPT 內文）——**macOS 內建，Windows 沒有**。在 Windows 打開 `.pptx` 會被換成別的字型，版面可能跑掉；**PPT 的定稿檢查請在 Mac 上做**。
  - 網頁講義的 `M PLUS Rounded 1c`、`Noto Sans TC` 走 Google Fonts，不用安裝。
- [ ] `ppt-final/` 裡的 `.key` 只能在 Mac 的 Keynote 開；其他電腦看同資料夾的 `.pdf`。

## 五、檔名規則（Mac 建檔、Windows 也要能同步）

- 會進網址的路徑一律**英文小寫 slug**（見 `CLAUDE.md` 第八節），這點已經避開大部分問題。
- 其他檔名避免半形 `\ / : * ? " < > |`、結尾空格或句點；中文標點用全形沒問題。
- 偶爾在 Mac 上檢查（沒有輸出＝沒問題）：

  ```bash
  cd "/Volumes/iMac eHD/Dropbox/Claude Cowork/呆一布講義"
  find . -path ./.git -prune -o -mindepth 1 \( -name '*[:*?"<>|\\]*' -o -name '* ' -o -name '*.' \) -print
  ```

## 六、Windows 常開主機（遠端用 Claude 的那台）額外設定

- [ ] 關掉自動睡眠（設定 → 系統 → 電源 → 睡眠「永不」；或 `powercfg /change standby-timeout-ac 0`）。
- [ ] Dropbox、Claude Desktop 設為**開機自動啟動**。
- [ ] 設好 Windows Update 的「使用時間」，避免半夜重開機後 App 沒開。
- 從手機或其他地方用 claude.ai 開對話，就會透過這台存取專案。

## 七、第一次對話：先暖身確認

在新電腦開第一個對話時，先貼這段：

```
請讀 CLAUDE.md、NOTES.md、log.md 最上面三筆，
摘要這個專案目前的狀態、規則和待辦事項，先不要改任何檔案。
```

摘要跟你的認知對不上 → 代表檔案裡少寫了什麼，當場補進 `CLAUDE.md` 或 `NOTES.md`。

## 八、使用時的鐵則

- **同一時間只在一台電腦改檔案。** 兩台同時改同一個檔案，Dropbox 會產生衝突副本。
- 每次工作結束前，對 Claude 說：「**更新 NOTES.md**」（做到哪、下次從哪開始）。
- 「以後都要這樣」的事 → 「**加進 CLAUDE.md，並記進 log.md**」。
