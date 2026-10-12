# 透明時刻 Clear Moment｜AI 售後服務夥伴 Demo

2026 和泰 AI 黑客松提案「運用 AI 再造 TOYOTA 下一代顧客售後服務體驗」的互動 Demo，可以配合簡報逐頁演示。

**線上展示：** https://leolo1205.github.io/toyota-ai-hackathon-demo/

> 本 Demo 為參賽提案的概念示意，**非 TOYOTA／和泰汽車官方服務**。畫面中的車輛資料、保養紀錄、報價、知識庫、服務據點與電話皆為虛構；介面僅參考現行系統的版型，未使用官方商標與插圖。AI 產生的內容為預先寫好的示範文字，不會呼叫任何 AI 服務，也不需要帳號。

## 提案的三項功能

| 功能 | 嵌入的現有系統 | Demo 中的位置 |
|---|---|---|
| ① AI 維修翻譯官 | 服務廠平板工單、官方 LINE | 專員口述檢查結果 → AI 產生白話說明 → 車主在 LINE 確認施作、追問；複雜問題轉專員；中間報告線上確認 |
| ② 智慧客休體驗 | My TOYOTA App | 今日回廠進度與等待建議、車況圖解、個人化用車知識 |
| ③ 個人化售後關懷 | App 保修紀錄、官方 LINE | 交車服務摘要、交車後關懷與 AI 分流、用車小叮嚀、保養提醒與一鍵預約 |

畫面中有紫框和「提案」標籤的是本提案新增的功能；勾選「聚焦提案功能」時，現行系統的介面會變淡。

## 操作方式

- 鍵盤 `←` `→`（或簡報遙控器的上一頁、下一頁）切換場景，也可以用上方的進度條或選單。
- 每一幕上方會顯示對應的簡報頁碼、「現行做法 → 提案」，以及要操作的地方（閃爍紫框）。
- 按「▶ 自動執行這一步」會自動完成該幕的操作。
- 建議用瀏覽器全螢幕（F11）演示，1366×768 以上的螢幕可以一頁放下。

## 直接跳到指定場景

在網址後面加上 `#代號`，打開就會停在那一幕，可以設成簡報上的超連結。

| 簡報頁 | 場景 | 代號 |
|---|---|---|
| P5 | 導覽 | `#intro` |
| P6 | ① 專員口述、AI 白話說明、LINE 確認施作 | `#voice` `#translate` `#card` |
| P7 | ① 追問、轉專員、中間報告 | `#ask` `#escalate` `#extra` |
| P8 | ② 回廠進度、車況圖解、用車知識 | `#progress` `#car` `#know` |
| P9 | ③ 服務摘要、保修紀錄、3 天關懷、小叮嚀、一鍵預約 | `#summary` `#record` `#care3` `#tip` `#remind` |
| P13 | 總結 | `#end` |

例如：https://leolo1205.github.io/toyota-ai-hackathon-demo/#translate

## 檔案結構

```
index.html   整個 Demo（HTML、CSS、JavaScript 都在這一個檔案）
.nojekyll    讓 GitHub Pages 直接提供靜態檔案
README.md    本說明
```

不需要安裝或建置。下載 `index.html` 後用瀏覽器直接打開，也可以離線使用（沒有網路時字型會改用系統字型）。

## 程式說明

`index.html` 的 `<script>` 主要分成以下幾段：

- **示範資料**：車輛、保養紀錄、工單報價、知識庫與三種檢查情境（`V`、`HISTORY`、`QUOTE`、`KB`、`SCEN`）。
- **示範內容產生**：依檢查數值產生白話說明、服務摘要、知識卡（`fbTranslate`、`fbSummary`、`fbKnowledge`），追問依關鍵字回覆（`fbAnswer`）。
- **模擬 AI**：按下按鈕後先顯示「產生中」，再顯示預先寫好的內容（`fake`、`doTranslate`、`doAsk` 等）。
- **場景**：每一幕的標題、對應簡報頁、現行與提案對照、要閃爍的元素（`SCENES`、`goScene`）。
- **畫面**：平板工單（`tablet`、`tabContent`）、官方 LINE（`lineChat`、`liffBook`）、My TOYOTA App（`appHome`、`appProgress`、`appRecords`）。

實際導入時，「模擬 AI」這段會換成串接大型語言模型、知識庫檢索（RAG）與工單系統 API。
