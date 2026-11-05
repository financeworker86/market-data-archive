# market-data-archive

公開 CSV 資料封存庫，透過 GitHub Actions 從 [`financeworker86/financial-data-pipeline`](https://github.com/financeworker86/financial-data-pipeline) 自動同步所有資料夾內的 `.csv` 檔案，並保留來源 repository 的目錄結構。

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

- 自動：由來源庫的每日總控在所有必要抓取階段成功後觸發，使用該批次的固定 commit SHA。
- 手動：進入 **Actions → Sync CSV files → Run workflow**。
- 同步規則：新增與更新來源 CSV；來源已刪除的 CSV 也會自封存庫刪除；沿用既有規則，排除檔名含 `listings` 的 CSV。
- 同步工作只複製 CSV，明確排除 `.json`、`.jsonl`；財報來源索引、更正紀錄與掛牌狀態來源檔僅留在來源庫。

## 本機更新

本機 `market-data-archive` 透過原週一至週五 06:00 排程，在雲端封存完成後拉取更新。設定、驗收及本機輔助程式放在 `.local/archive-sync/`，以本機 Git 排除規則維持不追蹤，不上傳 GitHub。

Perplexity Project 上傳已停用；原 `market-data-sync` 工具移除後，封存資料由本機此 repository 保存。

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
