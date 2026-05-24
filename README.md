# 華藏淨宗學會 — 報餐登記系統（前端）

由 GitHub Pages 託管的純 HTML 前端，後端用 Google Apps Script + Google Sheets。

🍱 **線上網址**：https://xinrong-rgb.github.io/hwadzan-baocan/

## 架構

```
蓮友的瀏覽器
   ↓ (打開 GitHub Pages 上的 HTML)
[https://xinrong-rgb.github.io/hwadzan-baocan/]
   ↓ fetch GET 帶 ?action= 呼叫 API
[Apps Script Web App (匿名公開)]
   ↓ 讀寫
[Google Sheet]
```

## 為什麼分兩邊

Google Apps Script Web App 的 HTML 介面在某些瀏覽器/網路環境會被 Google 自動擋（顯示「找不到網頁」），即使設定為公開匿名。

把 HTML 放到 GitHub Pages 託管後：
- 蓮友打開的是純 HTML，**100% 公開可達**
- 只在背景透過 GET API 呼叫 Apps Script 讀寫資料
- GET 在 Apps Script 匿名部署運作正常（POST 會被 Google redirect 弄壞）

## 更新前端

改完 `index.html` 後：

```bash
git add index.html
git commit -m "update XXX"
git push
```

約 1 分鐘後 GitHub Pages 會更新。

## 後端 Code.gs 在哪

在 Google Drive 的 `第二大腦/my-tools/華藏報餐系統/` 資料夾。
用 [clasp](https://github.com/google/clasp) 管理。

更新後端：

```bash
cd "/path/to/華藏報餐系統"
clasp push --force
clasp deploy --deploymentId AKfycbwGg-Vj-kS7PBm1501NYlRoKhxiBgqjsSjP-cfkvabHiy2CIJjq2NDrQKFvd6MbkC7h --description "..."
```
