# 專案開發與內容規範 (AGENTS.md)

## 1. 專案簡介
這是一個「主題式學習筆記網站」，用來將零散的學習重點整理成結構化、易於閱讀的網頁卡片與文章。

## 2. 技術規範
- 僅使用原生 **HTML5、CSS3 與 Vanilla JavaScript**，嚴禁引入任何前端框架或需要打包編譯的工具，確保可直接部署於 GitHub Pages。
- 所有頁面必須正確引入 `css/style.css`。
- **視覺風格規範**：全站採用深色極客風 ，所有色彩、字體與框線樣式皆由 `css/style.css` 統一控制，新增頁面時不可自行寫入行內樣式 (inline style) 覆蓋全域風格。  

## 3. 資料夾與命名規則
- `index.html`：首頁，展示網站標頭、主題標籤篩選器，以及所有筆記的卡片列表。
- `css/style.css`：全站統一樣式表。
- `notes/`：存放所有獨立筆記頁面。
  - **檔名格式**：`note-流水號.html`（例如：`note-01.html`、`note-02.html`），兩位數遞增。

## 4. 筆記內頁標準結構 (HTML 範本規範)
每篇新增的筆記 (`notes/note-XX.html`) 必須嚴格包含以下區塊：
1. **頂部導覽列**：包含返回首頁連結 (`← 返回筆記總覽`)。
2. **文章標頭 (`<header class="note-header">`)**：包含「分類標籤 (`<span class="tag">`)」、「筆記標題 (`<h1>`)」與「更新日期 (`<time>`)」。
3. **核心摘要區 (`<div class="summary-box">`)**：用 2～3 句話總結這篇筆記的核心概念。
4. **正文內容 (`<div class="note-content">`)**：使用 `<h2>` 區分段落，搭配條列式清單 (`<ul>`) 或程式碼區塊 (`<pre><code>`) 呈現重點。
5. **頁尾 (`<footer>`)**：統一的版權與專案說明。

## 5. 新增筆記的自動化 SOP (支援 Obsidian Markdown)
當使用者在專案根目錄建立好新的 Markdown 筆記（例如 `note-02.md`）並要求「轉成網頁」時，AI 必須依序完成以下兩個步驟：
- **步驟 A**：讀取該 `.md` 檔案的內容，在 `notes/` 資料夾下建立對應編號的 HTML 檔案（例如 `notes/note-02.html`），並套用第 4 點的標準結構排版。
- **步驟 B**：打開 `index.html`，在 `<main class="notes-grid">` 容器的**最上方**插入該篇筆記的 `<a class="note-card">` 卡片，確保最新筆記排在第一位，且 `data-category` 屬性與文章標籤一致。