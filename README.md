# 富翁市長遊戲企劃

[線上閱讀](https://ai8999ai-jpg.github.io/rich-mayor-plan/)

本儲存庫以企劃文件為主，採 Git 同步與推送。收到使用者「改完」或推送指示後才發布；推送成功就回報，網站由既有 GitHub Pages 背景自動更新。

## 檔案

| 路徑 | 用途 |
| --- | --- |
| index.html | 主企劃共用閱讀版 |
| stock-guide.html | 股票系統圖解與完整參數 |
| *.pdf | 已上傳的企劃規格與原始參考 |
| sources/*.docx | 可編輯 Word 企劃副本 |
| sources/*.txt | 純文字企劃副本 |
| AGENTS.md | AI 編輯、同步與推送規範 |

美術原始檔、模型、Unity 與遊戲程式不納入本倉庫。Git 只同步已加入並提交的檔案，不會自動同步桌面其他資料夾。

## 本機位置與首次取得

本機 Git 根目錄為 `C:/Users/User/Desktop/自己做大富翁/01_遊戲企劃/github-pages`。

其他裝置第一次取得：

```sh
git clone https://github.com/ai8999ai-jpg/rich-mayor-plan.git
cd rich-mayor-plan
```

每台裝置須有 Git，以及對此儲存庫有寫入權限的 GitHub 登入；登入由 Git Credential Manager 處理。

## 修改前

```sh
git status --short
git fetch origin
git log --oneline HEAD..origin/main
```

工作區乾淨且可快轉時：

```sh
git merge --ff-only origin/main
```

也可在乾淨工作區直接使用 `git pull --ff-only`，一次完成抓取與整合。有本機草稿或分支分岔時，先保留內容、比對再合併。使用 stash 保存時先 apply 還原，確認無遺漏後才移除暫存；不要直接覆蓋本機修改。

## 編輯與副本

修改規則後同步相關 HTML、Word、純文字與股票說明，並更新同一批文件的台灣編輯時間。桌面父目錄的 Word／純文字與 sources 同名檔案需同步。雲端新版也必須整合回本機副本，不能用舊匯出檔覆蓋。

## 收到「改完」或推送指示後

先同步副本、再次 fetch 並整合雲端，檢查實際差異，再提交本次明確檔案。例如只修改主企劃與其副本時：

```sh
git fetch origin
git diff --check
git diff --stat
git add -- index.html sources/商店合成與市長選舉遊戲企畫書_規則定案版.docx sources/遊戲企劃_純文字版.txt
git diff --cached --stat
git commit -m "更新遊戲企劃"
git push origin main
```

其他檔案（如股票說明、PDF、操作文件）依本次修改明確加入，不直接全選整個資料夾。GitHub 拒絕推送時重新讀取與合併，禁止強制覆蓋。推送成功即完成，不等待或驗證部署。

完整規則見 [AGENTS.md](AGENTS.md)。
