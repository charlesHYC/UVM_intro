# UVM 入門筆記

一份給 UVM 初學者的單頁教學文件，從一套 8 個 lab 的實作教材反推出
**UVM 的架構、資料流、資料型態，以及新手最容易踩的坑**。



## 線上閱讀

**<https://charleshyc.github.io/UVM_intro/>**

> 若連結還打不開，到 repo 的 **Settings → Pages**，Source 選 `main` / `/ (root)`，
> 等一兩分鐘即可。

或者 clone 下來用瀏覽器直接開 `index.html` —— 這份文件是**單一自我包含的 HTML**，
inline CSS / JS / SVG，零外部資源，離線也能讀。

```bash
git clone git@github.com:charlesHYC/UVM_intro.git
open UVM_intro/index.html          # macOS
```

## 內容

| 章 | 主題 | 重點 |
|---|---|---|
| 1 | 為什麼需要 UVM | 30 行的 hello world vs 420 行的完整 TB，多出來的東西買到了什麼 |
| 2 | Interface：class 與 module 的交界 | static module 世界 vs dynamic class 世界；`interface` / `modport` / `virtual interface` 是唯一通道 |
| 3 | 架構全景圖 | test → env → agent → driver / sequencer / monitor，外掛 scoreboard 與 coverage |
| **4** | **Datapath** | 一筆 transaction 從產生到被檢查走過的 8 站，每站標明「資料此刻在哪、是什麼型態」 |
| **5** | **資料型態總覽** | `uvm_object` vs `uvm_component` 兩大家族、建構子簽章、註冊巨集、`new()` vs `type_id::create()`、參數化型別、`logic`/`bit`、`===`/`==`、`<=`/`=` |
| 6 | Phase 機制 | 執行順序、function phase 不可耗時、objection 與 drain time |
| 7 | TLM | `analysis_imp` / `uvm_subscriber` / `uvm_tlm_analysis_fifo` 三種接法與適用時機 |
| 8 | config_db | `set` / `get` 四個參數逐一拆解，以及三種讓它失敗的錯法 |
| 9 | Factory 與 Override | 不改架構就替換行為，以及 override 失效的原因 |
| 10 | Functional Coverage | covergroup / coverpoint / bins / cross、用覆蓋率當停止條件 |
| 11 | 換一個協定會變什麼 | 從 adder 換到 APB：架構不動，只改四個地方；附時序圖與 SVA |
| **12** | **初學者地雷清單** | 15 條「症狀 → 原因 → 正解」 |
| 13 | 執行速查 | `make` vs `make run` 的坑、runtime 參數、verbosity、從 log ID 反查元件 |
| 14 | Lab 學習地圖 | 哪個 lab 對應哪一章觀念 |

含 5 張手繪 inline SVG 圖：元件樹、transaction datapath、phase 時間軸、
TLM 三種型態、APB 時序波形。

## 關於範例

文中所有程式碼片段取自一套 UVM 1.2 / VCS 課程教材的 lab（DUT 為 7-bit 加法器，
最後一個 lab 換成 APB slave）。**教材原始碼不在本 repo 內**，這裡只放整理後的文件。

## 技術細節

- 單一 `index.html`，約 95 KB，無任何外部依賴（無 CDN、無字型、無圖檔）
- 深色 / 淺色主題自動跟隨系統
- 手寫的極簡 SystemVerilog 語法上色（純 inline JS）
