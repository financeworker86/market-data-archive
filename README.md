# market-data-archive

公開 CSV 資料封存庫，透過 GitHub Actions 從 [`financeworker86/tw-market-index-tracker`](https://github.com/financeworker86/tw-market-index-tracker) 自動同步所有資料夾內的 `.csv` 檔案，並保留來源 repository 的目錄結構。

## 資料目錄

同步完成後，CSV 會保留原始路徑，例如：

```text
Bond/data/*.csv
data/*.csv
data/IS/*.csv
data/mops_material_news/*.csv
data/stock_day/*.csv
```

## 同步方式

- 排程：每日台灣時間 07:30（UTC 23:30）自動執行。
- 手動：進入 **Actions → Sync CSV files → Run workflow**。
- 同步規則：新增與更新來源 CSV；來源已刪除的 CSV 也會自封存庫刪除。
- 非 CSV 檔案不會由同步工作複製。

## 直接下載

可透過 GitHub Raw URL 讀取資料：

```text
https://raw.githubusercontent.com/financeworker86/market-data-archive/main/<CSV 原始路徑>
```

例如：

```text
https://raw.githubusercontent.com/financeworker86/market-data-archive/main/data/tw_market_index.csv
```

## 注意事項

本 repository 僅作資料封存與研究用途。資料可能有延遲、缺漏或後續修訂；使用前請自行核對原始資料來源及其使用條款。
