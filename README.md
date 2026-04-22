# 韓幣小錢包 ♡ KRW Wallet PWA

粉紫色系的韓幣轉台幣計算機，可以加到手機桌面像原生 App 一樣使用，離線也能用。

## 檔案結構

```
krw-twd-pwa/
├── index.html          # 主頁面（UI + 換算邏輯）
├── manifest.json       # PWA 設定
├── sw.js               # Service Worker（離線快取）
└── icons/
    ├── icon.svg              # 原始向量圖
    ├── icon-maskable.svg     # Android 自適應圖示
    ├── icon-192.png          # Android 一般
    ├── icon-512.png          # Android 大尺寸
    ├── icon-maskable-512.png # Android 自適應
    ├── apple-touch-icon.png  # iOS 圖示（180x180）
    └── favicon-32.png        # 瀏覽器 tab 圖示
```

## 部署到 GitHub Pages（推薦）

1. 在 GitHub 建立新的 repo，例如 `krw-wallet`
2. 把整個資料夾內容 push 上去：
   ```bash
   cd krw-twd-pwa
   git init
   git add .
   git commit -m "init 韓幣小錢包"
   git branch -M main
   git remote add origin https://github.com/AileenMeow/krw-wallet.git
   git push -u origin main
   ```
3. 到 repo 的 **Settings → Pages**，Source 選 `main` branch 的 root，儲存
4. 等 1-2 分鐘，網址會是 `https://aileenmeow.github.io/krw-wallet/`

## 加到手機桌面

### iPhone (Safari)
1. 用 Safari 開啟網址（必須是 Safari，不能用 Chrome）
2. 點下方分享按鈕 ↗
3. 選「加入主畫面」
4. 改名「韓幣錢包」或保持預設
5. 桌面就會出現圖示，點開是全螢幕、無網址列

### Android (Chrome)
1. 用 Chrome 開啟網址
2. 右上角三個點選單
3. 選「加到主畫面」或「安裝應用程式」
4. 完成

## 功能

- 雙向即時換算（韓幣 ↔ 台幣）
- 匯率固定 1 KRW = 0.0215 TWD
- 8 個常用金額快捷按鈕（飯糰、咖啡、拉麵、韓服、烤肉、KTX、住宿、演唱會）
- 輸入千分位自動格式化
- 點擊快捷按鈕有震動回饋（手機限定）
- 支援深色模式（跟隨系統設定）
- 完全離線可用

## 調整匯率

如果要改匯率，打開 `index.html` 找到：
```js
const RATE = 0.0215;
```
改成你要的數字，並同步更新 header 的 `rate-badge` 顯示文字。

改完後因為 Service Worker 有快取，手機可能要：把 App 從桌面刪掉 → 重新加一次，或清瀏覽器快取。

## 樣式客製

所有顏色在 `index.html` 的 `:root` 區塊，主要變數：
- `--purple-400: #C4A7E7` — 主紫色
- `--pink-400: #F472B6` — 粉紅點綴
- `--korea-red: #CD2E3A` — 韓國國旗紅
- `--korea-blue: #0047A0` — 韓國國旗藍

首爾玩得開心 ♡
