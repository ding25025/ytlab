# CLAUDE.md

## 專案概要

YTLab Studio 的單頁靜態官網，部署在 GitHub Pages（https://ding25025.github.io/ytlab/），來源為 `main` branch 根目錄。push 到 `main` 就會自動部署，沒有 build 步驟，也沒有 CI。

## 檔案

- `index.html`：整個網站。`<style>` 與 `<script>` 都寫在檔案裡，沒有外部 CSS/JS。
- `img/`：App 圖示。`sidebell`、`herbmeet`（哈波蜜）、`FoodEntropy`（食熵）各有 1024×1024 `.png` 原圖與 192×192 `.webp`（網頁使用，顯示為 64/80px）。
- `README.md`：給人看的專案說明。

## 慣例

- 語系為 `zh-Hant-TW`，網站文案使用繁體中文（台灣用語）。
- 顏色一律用 `:root` 的 CSS 變數（`--ground`、`--ink`、`--accent` 等）。深色模式同時定義在 `@media (prefers-color-scheme:dark)`（搭配 `:root:not([data-theme="light"])`）與 `:root[data-theme="dark"]`，改顏色時兩處都要改。
- 字型：`--serif`（Noto Serif TC）用於標題、`--sans` 用於內文、`--mono` 用於等寬文字，皆從 Google Fonts 載入。
- App 圖示以相對路徑引用 `img/` 下的 WebP（`<img class="appicon" loading="lazy" decoding="async" src="img/xxx.webp">`），不要改回 base64 內嵌，也不要直接引用 1024px PNG。更新或新增圖示時，把 PNG 原圖放進 `img/`，再縮成同名 192×192 WebP（例如用 Pillow：`resize((192,192), LANCZOS)`、`quality=85`）。
- App Store 連結格式為 `https://apps.apple.com/app/idXXXXXXXXXX`，**不要**加地區路徑（例如 `/tw/`）。
- 聯絡信箱：`contact@iairtw.com`（`#contact` 區塊，有複製按鈕）。

## Git

- commit message 使用繁體中文。
- remote：`origin` → https://github.com/ding25025/ytlab.git
