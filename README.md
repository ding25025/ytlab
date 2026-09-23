# YTLab Studio

YTLab Studio 的官方網站：健保核刪防護、醫療資訊顧問（FHIR、臨床系統整合），以及自行開發的 App。

🔗 網站：https://ding25025.github.io/ytlab/

## 網站內容

| 區塊 | 錨點 | 說明 |
| --- | --- | --- |
| 核刪防護 | `#product` | 健保申報預檢服務 |
| 顧問服務 | `#services` | FHIR 資料轉換、診所流程自動化、臨床系統整合 |
| App 產品 | `#apps` | SideBell 隨身鈴、哈波蜜、食熵 |
| 關於我們 | `#about` | |
| 聯絡 | `#contact` | [Calendly 預約 30 分鐘](https://calendly.com/ding25025/30min) |

## App

| App | App Store |
| --- | --- |
| SideBell 隨身鈴 | https://apps.apple.com/app/id6799201744 |
| 哈波蜜 | https://apps.apple.com/app/id6787411907 |
| 食熵 | https://apps.apple.com/app/id6793926521 |

## 專案結構

不需要 build：

- `index.html`：整個網站，CSS 與 JS 都寫在檔案裡。字型從 Google Fonts 載入。
- `video/`：核刪防護介紹影片、SideBell 展示影片與封面圖。
- `img/`：App 圖示。`*.png` 為 1024×1024 原圖，網頁使用由原圖縮成的 192×192 `*.webp`。

## 本機預覽

```sh
open index.html
# 或
python3 -m http.server 8000   # 開啟 http://localhost:8000
```

## 部署

網站透過 GitHub Pages 發佈，來源為 `main` branch 根目錄。push 到 `main` 後約一分鐘會自動更新。
