# DIC4 · AI Fitness Coach

**以對話為入口的智慧慢跑教練提案**｜物聯網應用與資料分析期末專題

本專題提出一套結合跑步、天氣、路線與營養資訊的對話式 AI 慢跑教練。使用者可用文字或語音描述跑步安排與飲食需求；系統先確認計算所需的單位、地點與時間，再透過代理人呼叫相關工具，提供有依據的回覆。介面也規劃語音播放與虛擬教練口型同步。

此儲存庫保存研究提案、編譯後的 PDF 與課程參考資料，並非教練應用程式的實作程式碼。提案引用課程專題審查所述的初步展示；目前未附逐次測試紀錄或延遲分布，因此效能數字仍是待驗證的目標。

## 三項核心設計

1. **對話式跑步規劃**：以瀏覽器端 JavaScript 支援文字與語音互動，並規劃語音回覆及虛擬教練口型同步。計算配速時保留輸入單位；資料不足時先詢問，不以猜測補值。
2. **代理人與工具協作**：提案以 FastAPI 提供 REST 與 WebSocket 互動，由 ScopeGuard 檢查請求範圍，再交由單一代理人協調配速、天氣、路線與 MCP 營養工具。工作階段快照保留已確認資料，方便後續對話接續使用。
3. **配額控管與可驗證評估**：在付費模型或工具呼叫前預留用量，完成後依實際使用結算；未知用量的逾時請求保留預留額，等待對帳。評估規劃比較表單、雲端代理人與本機代理人，檢查任務正確率、完成率、Token 用量及回覆時間。

## 評估規劃

提案建議每個情境及設定至少重複 30 次，分別報告冷啟動、暖啟動、逾時與失敗。頁面查詢 P95 低於 2 秒、語音回覆起始時間 P95 低於 12 秒是**預定目標，不是已量測的結果**。情境涵蓋配速計算、缺少單位、過期天氣資料、路線查詢逾時、營養資訊來源、配額競爭、重連去重與語音播放。

## 版本與專題資料

| 文件／版本 | 內容 |
| --- | --- |
| [修改前：`main` 分支](https://github.com/HitomiHuang/ICEIB2027/tree/main) · [`main.tex`](https://github.com/HitomiHuang/ICEIB2027/blob/main/main.tex) | Overleaf 原始主檔，保留作為修改前版本 |
| [修改後：`main_verified` 分支](https://github.com/HitomiHuang/ICEIB2027/tree/main_verified) · [`main_verified.tex`](https://github.com/HitomiHuang/ICEIB2027/blob/main_verified/main_verified.tex) · [提案 PDF](https://github.com/HitomiHuang/ICEIB2027/blob/main_verified/main_verified.pdf) | 修訂後提案與編譯檔 |
| [GitHub 版本差異](https://github.com/HitomiHuang/ICEIB2027/compare/main...main_verified) | 比較修改前 `main` 與修改後 `main_verified` |
| [Overleaf 專題](https://www.overleaf.com/project/6b06bc99ca959ab6ca74f713) | 線上 LaTeX 專案（依 Overleaf 權限存取） |
| [`main_revised.tex`](https://github.com/HitomiHuang/ICEIB2027/blob/main_verified/main_revised.tex) | 修訂草稿 |
| [`main_five_pages.tex`](https://github.com/HitomiHuang/ICEIB2027/blob/main_verified/main_five_pages.tex) · [PDF](https://github.com/HitomiHuang/ICEIB2027/blob/main_verified/main_five_pages.pdf) | 五頁版本草稿 |
| [課程提案解析](https://github.com/HitomiHuang/ICEIB2027/blob/main/myRef/AI%E6%95%99%E7%B7%B4%E6%8F%90%E6%A1%88%E8%A7%A3%E6%9E%90.pdf) | 課程規範對照與提案解析 |
| [A–Z 大綱範例](https://github.com/HitomiHuang/ICEIB2027/blob/main/myRef/A2Z%20outline%20example.pdf) | 提案撰寫參考 |
| [AI Fitness Coach 概念圖](https://github.com/HitomiHuang/ICEIB2027/blob/main/myRef/AI_Fitness_Coach.png) | 專題概念與系統示意 |

## 編譯提案

使用含 IEEEtran、TikZ、algorithmic 等套件的 LaTeX 環境，以 pdfLaTeX 編譯兩次：

```bash
pdflatex main_verified.tex
pdflatex main_verified.tex
```

`main_verified.pdf` 是本儲存庫提供的編譯版本；若修改 `.tex`，請重新編譯以更新 PDF。
