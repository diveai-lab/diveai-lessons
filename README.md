# 呆一布 AI 共學實驗室・講義庫

國立政治大學「呆一布 AI 共學實驗室」（**DiveAI**）給同學的 AI 講義與作業。
每一份講義都是純 HTML / CSS / JavaScript，打開瀏覽器就能看、`←` `→` 或空白鍵翻頁。

## 線上瀏覽

透過 GitHub Pages：

- 首頁（講義目錄）：`https://diveai-lab.github.io/<repo>/`
- 入門作業：`https://diveai-lab.github.io/<repo>/lessons/intro-assignment/`

> 把 `<repo>` 換成這個 repo 的名字。開啟方式：repo → **Settings → Pages** → Source 選 `main` 分支、根目錄，存檔等一兩分鐘即可。

## 資料夾結構

```
├── index.html          講義總目錄首頁
├── assets/             首頁用的 logo / 吉祥物
├── lessons/            各講義成品（每份一個英文 slug 資料夾，自帶 assets/）
│   └── intro-assignment/    入門作業（10 頁手帳風簡報）
├── shared-assets/      共用素材庫（吉祥物、logo、人物貼圖）
├── ideas/              想法／學生版內容稿（.md）
├── slide-notes/        逐頁內容稿（.md）
├── CLAUDE.md           專案指引（給協作者與 AI）
└── log.md              變更紀錄
```

## 新增一份講義

1. `ideas/<slug>.md` 寫構想 → `slide-notes/<slug>.md` 寫逐頁稿。
2. 在 `lessons/<slug>/` 產出 `index.html`，用到的圖 copy 進 `lessons/<slug>/assets/`（相對路徑引用，整包 self-contained）。
3. 在根目錄 `index.html` 的「講義庫」加一張卡片，連到 `lessons/<slug>/`。

命名一律用**英文小寫 slug**（連字號），因為會出現在網址裡。細節見 `CLAUDE.md`。

## 授權與素材

講義內容供教學使用。吉祥物 **DIVE（呆一布）** 與相關角色圖為實驗室素材，請勿另作商業用途。

—— Dive into AI 🐳
