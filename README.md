# 會議記錄產生器 / Meeting Minutes Generator

一個純前端（不需要伺服器）的網頁工具，讓你透過點選欄位與選項、搭配最少量的文字輸入，快速產生 **英文版** 或 **繁體中文版** 的會議記錄 PDF，方便分享給同事。

A client-side only web tool (no backend/server required) that lets you build meeting minutes mostly by clicking fields and options, with minimal typing, then export a formatted **English** or **Traditional Chinese** PDF to share with colleagues.

## 功能 Features

- **會議日期 Meeting Date** — 西元年月日日期選擇器 (Gregorian date picker)
- **會議主旨 Meeting Subject** — 單行文字輸入
- **與會人員 Attendees** — 點選職務類別（Manager / Sales / PM / SW Engineer / HW Engineer / FPGA Engineer / Mechanical Engineer / QA Engineer / Marketing / Customer / Other）+ 輸入姓名，可新增多位
- **會議內容 Meeting Content** — 條列式重點，逐項新增
- **待辦事項 Action Items** — 事項文字 + 從與會人員中選擇負責人（下拉選單）+ 期限日期選擇器（皆為選填）
- **其他補充項目 Additional Notes** — 自由文字欄位
- **即時預覽 Live Preview** — 表單右側即時顯示目前已輸入的內容
- **雙語 PDF 匯出 Bilingual PDF export** — 分別按鈕輸出英文版與繁體中文版 PDF（職務名稱、章節標題會依語言顯示對應翻譯；使用者輸入的文字內容原樣呈現）
- **草稿自動儲存 Autosave draft** — 內容自動儲存在瀏覽器 localStorage，重新整理頁面不會遺失（點「清除表單」可重設）
- **完全本機運作 Fully client-side** — 不會將任何資料上傳到伺服器；PDF 產生函式庫已內建於專案中（`vendor/html2pdf.bundle.min.js`），開啟頁面後即可離線使用

## 使用方式 How to use

1. 直接用瀏覽器開啟 `index.html`，或用任何靜態網頁伺服器（GitHub Pages、`npx serve`、`python3 -m http.server` 等）架設後開啟。
2. 依序填寫「會議日期」「會議主旨」「與會人員」「會議內容」「待辦事項」「其他補充項目」。
3. 右側「預覽」區塊會即時顯示目前內容。
4. 按下「產生英文版 PDF」或「產生繁體中文版 PDF」，瀏覽器會自動下載對應的 PDF 檔案。
5. 若要重新開始，按左上角「清除表單」。

## 技術說明 Tech notes

- 純 HTML / CSS / JavaScript（無框架、無建置流程），可直接開啟或部署到任何靜態網站空間。
- PDF 匯出使用 [html2pdf.js](https://github.com/eKoopmans/html2pdf.js)（已 vendor 於 `vendor/` 目錄，離線可用）；中文字型使用 Google Fonts 的 Noto Sans TC（需要網路連線載入字型；若完全離線環境，瀏覽器會退回系統預設字型渲染中文）。
- 檔案結構：
  - `index.html` — 頁面結構
  - `style.css` — 樣式（含表單樣式與 PDF 版面樣式）
  - `app.js` — 表單邏輯、預覽渲染、PDF 產生邏輯
  - `vendor/html2pdf.bundle.min.js` — PDF 產生函式庫（本地端，離線可用）
