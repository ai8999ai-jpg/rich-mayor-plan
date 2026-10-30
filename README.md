# 富翁市長遊戲企劃

[線上閱讀](https://ai8999ai-jpg.github.io/rich-mayor-plan/)

共用主版本為本儲存庫 `main` 分支的 `index.html`。網站由 GitHub Pages 從分支根目錄發布，成功推送後自動重新部署。

## 跨裝置編輯流程

1. 每次修改前，先讀取 GitHub 的最新 `main` 與 `index.html`，記下本次編輯的起始版本。
2. 若雲端有更新，先把雲端修改整合進本機副本，再開始編輯；本機未推送的修改先保留並比對。
3. 每次修改企劃內容後，自動更新標題下的「最後編輯時間」，以台灣時間（UTC+8）顯示至秒；本機 HTML、DOCX、純文字與網站發布版使用同一時間，保留單一時間欄位。完成後檢查規則、表格、章節連結、右側目錄與地圖。
4. 推送前再次檢查雲端。若已有其他裝置推送，先整合差異並重新檢查，再推送。
5. 成功推送 `main` 後，GitHub Pages 自動部署；確認部署成功與網站更新後再交付。

使用相同 GitHub 帳號仍需同步同一個儲存庫。各裝置的本機檔案透過讀取、合併及推送銜接。

## 使用 Git 的裝置

第一次取得文件：

```sh
git clone https://github.com/ai8999ai-jpg/rich-mayor-plan.git
cd rich-mayor-plan
```

開始編輯前先檢查工作目錄，妥善保留未提交修改，再同步：

```sh
git status --short
git fetch origin
git pull --ff-only
```

完成並檢查後：

```sh
git diff --check
git add index.html
git commit -m "更新遊戲企劃"
git push origin main
```

推送若被拒絕，重新讀取雲端並合併，完成檢查後再次推送。保留雙方變更及提交歷史，禁止強制推送覆蓋他人內容。

## 使用 GitHub 連接器的裝置

先讀取 `main` 的提交版本與 `index.html` 內容，保留檔案 SHA 作為更新前提。推送前重新讀取；版本改變時先合併，再使用最新且已確認的 SHA 提交。發生版本衝突時，須比對內容後再提交，不能只換 SHA 重送舊內容。

詳細代理工作規則見 [AGENTS.md](AGENTS.md)。本機素材資料夾路徑保留為企劃索引。
