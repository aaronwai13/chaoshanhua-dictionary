# 潮汕話詞庫

一個原生 HTML、CSS、JavaScript 寫成的單頁潮汕話詞庫工具，適合直接放上靜態 hosting 或自己手機主畫面使用。

## 功能

- 詞庫瀏覽、搜尋、分類篩選
- 新增、修改、刪除詞語
- 句子注音，未收錄字詞可即時 quick add
- 分類檢查，一鍵自動修正明顯唔啱的 category
- 直接點按 category 來編輯分類
- 匯出 / 匯入 JSON 備份，方便還原本地資料

## 檔案結構

```text
.
├── index.html
├── manifest.json
└── sw.js
```

## 使用方式

直接打開 [index.html](/Users/kammingwai/Documents/App/chaoshanhua/index.html) 就可以使用。

如果要本地開發，可以在 repo 目錄開一個簡單靜態 server，例如：

```bash
python3 -m http.server 8000
```

之後打開 `http://localhost:8000`。

## 資料儲存

- 所有詞庫資料預設存喺瀏覽器 `localStorage`
- 如果瀏覽器資料被清走，未匯出的自訂詞語會消失
- 建議定期喺 app 內用「匯出詞庫」下載 JSON 備份

## 備份與還原

1. 去「新增」頁
2. 用「匯出詞庫」下載目前詞庫 JSON
3. 要還原時，用「匯入詞庫」揀返備份 JSON

匯入時會自動整理資料：

- 只保留有效的 `zh` / `ro`
- 自動忽略重複字詞
- 保留現有或新加入的 category 名稱

## 分類管理

- 新增詞語時，輸入漢字後會自動建議 category
- 如果建議類別已經存在，會直接沿用
- 如果建議類別未存在，儲存後會自動加入分類選項
- 詞庫頁的「檢查分類」會按內建規則自動修正明顯錯誤分類
- 直接點詞條上的 category badge，可以即場改分類

## 部署

呢個 app 係零 build step，適合：

- GitHub Pages
- Netlify
- Vercel 靜態部署
- 任何可提供靜態檔案的 hosting

## 備註

- app 名稱已統一為「潮汕話詞庫」
- 預設唔使用 custom PWA icon
- service worker 只做基本快取，目標係簡單直接
