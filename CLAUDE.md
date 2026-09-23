# CLAUDE.md

## 專案概要

YTLab Studio 的單頁靜態官網，部署在 GitHub Pages（https://ding25025.github.io/ytlab/），來源為 `main` branch 根目錄。push 到 `main` 就會自動部署，沒有 build 步驟，也沒有 CI。

## 檔案

- `index.html`：整個網站。`<style>` 與 `<script>` 都寫在檔案裡，沒有外部 CSS/JS。
- `img/`：App 圖示。`sidebell`、`herbmeet`（哈波蜜）、`FoodEntropy`（食熵）各有 1024×1024 `.png` 原圖與 192×192 `.webp`（網頁使用，顯示為 64/80px）。
- `video/`：展示影片（皆 1920×1080 H.264、無聲）與同名 `_poster.webp` 封面（1280×720，取自第 3 秒標題畫面）：
  - `claim-intro.mp4`（32 秒）：核刪防護區塊（`#product`），三步驟下方全寬。
  - `SideBell_demo.mp4`（64 秒）：SideBell 卡片（整排寬）下半部全寬。
- `README.md`：給人看的專案說明。

## 慣例

- 語系為 `zh-Hant-TW`，網站文案使用繁體中文（台灣用語）。
- 顏色一律用 `:root` 的 CSS 變數（`--ground`、`--ink`、`--accent` 等）。深色模式同時定義在 `@media (prefers-color-scheme:dark)`（搭配 `:root:not([data-theme="light"])`）與 `:root[data-theme="dark"]`，改顏色時兩處都要改。
- 字型：`--serif`（Noto Serif TC）用於標題、`--sans` 用於內文、`--mono` 用於等寬文字，皆從 Google Fonts 載入。
- App 圖示以相對路徑引用 `img/` 下的 WebP（`<img class="appicon" loading="lazy" decoding="async" src="img/xxx.webp">`），不要改回 base64 內嵌，也不要直接引用 1024px PNG。更新或新增圖示時，把 PNG 原圖放進 `img/`，再縮成同名 192×192 WebP（例如用 Pillow：`resize((192,192), LANCZOS)`、`quality=85`）。
- App Store 連結格式為 `https://apps.apple.com/app/idXXXXXXXXXX`，**不要**加地區路徑（例如 `/tw/`）。
- 展示影片一律用 `<figure class="demo">`，內含 `<video … controls muted loop playsinline preload="metadata">` 與 `figcaption` 裡的 `data-act="toggle"`（播放/暫停）、`data-act="restart"`（重新開始）、`data-act="fullscreen"`（全螢幕，iOS 用 `webkitEnterFullscreen`）按鈕。頁面底部的 `<script>` 會自動套用到每個 `figure.demo`：捲進畫面時自動播放、離開時暫停；使用者手動暫停後不再自動播放；`prefers-reduced-motion` 時不自動播放。新增影片只要照同樣結構加 HTML，不用改 JS。影片是 1920×1080 簡報式畫面、字很多，**請給接近內容全寬（≥ 1000px）的版位**，放在半欄內字會小到約 7px 看不清楚。`.demo` 預設配色用於淺色底，放在深色卡片（`.app.feature`）內有另外的覆寫。
- 聯絡方式（`#contact` 區塊）：主要為 Calendly 預約 https://calendly.com/ding25025/30min（新分頁開啟）。網站不公開 email。頁面上的「預約免費核刪健檢」按鈕都連到 `#contact`。

## Git

- commit message 使用繁體中文。
- remote：`origin` → https://github.com/ding25025/ytlab.git
