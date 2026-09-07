# 會議記錄產生器 / Meeting Minutes Generator

一個純前端（不需要伺服器）的網頁工具，讓你透過點選欄位與選項、搭配最少量的文字輸入，快速產生 **英文版** 或 **繁體中文版** 的會議記錄，並直接複製到 **Outlook 郵件** 中分享給同事。

A client-side only web tool (no backend/server required) that lets you build meeting minutes mostly by clicking fields and options, with minimal typing, then copy a formatted **English** or **Traditional Chinese** version straight into an **Outlook email**.

## 功能 Features

- **會議日期 Meeting Date** — 西元年月日日期選擇器 (Gregorian date picker)
- **會議主旨 Meeting Subject** — 單行文字輸入
- **與會人員 Attendees** — 點選職務類別（Manager / Sales / Sales Manager / PM / SW Engineer / HW Engineer / FPGA Engineer / FAE / Avnet Design Service Team / Customer / Other）+ 輸入姓名與公司名稱，可新增多位
- **會議內容 Meeting Content** — 條列式重點，逐項新增，支援換行
- **待辦事項 Action Items** — 事項文字 + 從與會人員中選擇負責人（下拉選單）+ 期限日期選擇器（皆為選填）
- **其他補充項目 Additional Notes** — 自由文字欄位
- **即時預覽 Live Preview** — 表單右側即時顯示目前已輸入的內容
- **複製到 Outlook 郵件 Copy for Outlook Email** — 分別按鈕複製英文版與繁體中文版的郵件格式內容（表格式排版、樣式全部內嵌，符合 Outlook 桌面版的渲染限制），複製後直接貼到 Outlook 新郵件中即可保留表格與排版
- **草稿自動儲存 Autosave draft** — 內容自動儲存在瀏覽器 localStorage，重新整理頁面不會遺失（點「清除表單」可重設）
- **完全本機運作 Fully client-side** — 不會將任何資料上傳到伺服器

## 使用方式 How to use

1. 直接用瀏覽器開啟 `index.html`，或用任何靜態網頁伺服器（GitHub Pages、`npx serve`、`python3 -m http.server` 等）架設後開啟。
2. 依序填寫「會議日期」「會議主旨」「與會人員」「會議內容」「待辦事項」「其他補充項目」。
3. 右側「預覽」區塊會即時顯示目前內容。
4. 按下「複製英文版」或「複製繁體中文版」，內容會自動複製到剪貼簿（若瀏覽器不允許自動複製，會跳出視窗讓你手動按 Ctrl+C / Cmd+C 複製）。
5. 到 Outlook 開一封新郵件，貼上（Ctrl+V / Cmd+V）即可，表格與排版會保留。
6. 若要重新開始，按左上角「清除表單」。

## 技術說明 Tech notes

- 純 HTML / CSS / JavaScript（無框架、無建置流程），可直接開啟或部署到任何靜態網站空間。
- Outlook 郵件內容採用表格式排版、樣式全部寫在標籤內（inline style），字型使用 Outlook 看得懂的 Microsoft JhengHei / Calibri / Arial —— 因為 Outlook 桌面版是用 Word 的排版引擎渲染郵件，不支援 CSS Grid/Flexbox，也不會套用網頁字型。
- 中文字型（畫面上的介面文字）使用 Google Fonts 的 Noto Sans TC（需要網路連線載入字型；若完全離線環境，瀏覽器會退回系統預設字型渲染中文）。
- 檔案結構：
  - `index.html` — 頁面結構
  - `style.css` — 樣式
  - `app.js` — 表單邏輯、預覽渲染、Outlook 郵件格式產生與複製邏輯
