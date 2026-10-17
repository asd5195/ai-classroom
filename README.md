# 15 分鐘 AI 小課堂

學員免登入，透過 GitHub Pages 看課程並下載教材。純 HTML、CSS、JavaScript，不需要 Supabase、伺服器或安裝套件。

## 管理員機制

管理權限由 GitHub 儲存庫控制。`admin.html` 是公開的編輯輔助頁，**不是受保護的後端**。任何人可以在自己的瀏覽器編輯草稿，但只有儲存庫擁有者或你授權的協作者可以在 GitHub 提交變更、影響公開網站。

發布流程：管理頁填寫課程 → 匯出 courses.json → 登入 GitHub 上傳附件與更新檔 → Commit changes → 等待 Pages 部署。

不在網站內存密碼或 Token。GitHub 登入與權限檢查均由 GitHub 負責。這個版本不提供在管理頁按一下就直接上傳到 GitHub 的功能。

## 第一次上線（使用 GitHub 網頁操作）

1. 在 GitHub 建立新的儲存庫，例如 `ai-classroom`。若使用 GitHub Free，請選 Public。勾選建立 README，使用 `main` 分支。
2. 解壓縮本套件，進入網站資料夾。將其中的 `index.html`、`admin.html`、`style.css`、`common.js`、`app.js`、`admin.js`、`assets` 與 `data` 拖曳至 GitHub 的 **Add file → Upload files**。不要把 ZIP 本身或外層網站資料夾當作首頁上傳。完成後按 **Commit changes**。
3. `.nojekyll` 若因隱藏檔沒被上傳，可在 GitHub 用 **Add file → Create new file** 建立同名空白檔。此專案使用一般靜態檔，沒有建置依賴。
4. 進入 **Settings → Pages**。Source 選 **Deploy from a branch**，Branch 選 **main**，資料夾選 **/(root)**，按 Save。
5. 等部署完成，使用 Pages 頁面顯示的網址。一般專案網址形式是 `https://你的帳號.github.io/ai-classroom/`；以 GitHub 實際顯示的網址為準。
6. 開啟網站，核對兩堂課與三份 PPT 連結。管理頁為同一網址下的 `admin.html`。

官方說明：
- https://docs.github.com/en/pages/quickstart
- https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## 日後新增一堂課

1. 進入「課程管理」。第一次使用時展開設定，填寫 `帳號/儲存庫` 及分支（預設 main）。GitHub Pages 一般網址會自動帶入儲存庫。
2. 每次開啟會讀取目前公開的課程清單。如先前有本機草稿，可選擇「恢復本機草稿」。不同電腦的草稿不會同步。
3. 點「新增課程」，填入堂次、名稱、簡介、目標、步驟、練習及提示詞。教學步驟與練習每行以 `標題｜內容` 填寫。
4. 選擇狀態：草稿只留本機；即將上線會公開顯示已填內容；已開放顯示為可進入的課程。
5. 教材可選檔帶入名稱，但此時**尚未上傳**。按 GitHub 教材資料夾連結，將檔案上傳到 `assets` 並提交變更。建議使用英文或數字檔名，例如 `lesson-03.pptx`。
6. 教材欄位填 `assets/lesson-03.pptx`，或可公開存取的 https 連結。管理頁不會驗證遠端檔案是否存在，發布後請實際開啟一次。
7. 按「匯出公開課程 courses.json」。下載檔若被瀏覽器命名成 `courses (1).json`，請先改回 `courses.json`。
8. 開啟 GitHub 的 `data` 上傳頁，用新檔取代原來的 `data/courses.json`，按 Commit changes。
9. 到 Actions 確認部署結果，再重新整理學員頁。

## 檔案與草稿

- 課程與排序：`data/courses.json`。
- 教材：`assets/`。
- 草稿：這台電腦、此瀏覽器的 localStorage。清除瀏覽資料會失去草稿，請用「備份所有草稿」保留。
- 完整備份包含未發布資料，**請勿上傳到公開儲存庫**。可透過匯入功能恢復。
- 公開課程匯出會排除狀態為 draft 的課程。若手動把草稿寫入 GitHub 的 JSON，資料仍可被直接讀取，隱藏畫面不等於保密。
- 本網站與教材是公開的。「有連結就能看」不是存取限制，也可能被搜尋引擎發現。
- 刪除課程後，原附件仍在 GitHub。若也要刪除附件，需在 GitHub 另外處理；舊提交歷史也可能保留資料。請只上傳允許公開的內容。

## 內附內容

- 第一堂：PPT 切檔工具，含提示詞與 20 頁教材對應的練習。
- 第二堂：機密資訊應用 AI 的課程預告。
- `assets/lesson-01.pptx`：先前製作的課堂 PPT。此檔原操作說明以 8 頁示範為例，本網站練習已改用新製作的 20 頁檔。可編輯 PPT 後替換此檔，讓上課投影片與網站一致。
- `assets/practice-fixed-20.pptx`：每人 4 頁，共 5 人。
- `assets/practice-custom-20.pptx`：每人依序 3、5、2、6、4 頁，共 5 人。

## 本機預覽（選用）

直接雙擊 HTML 可能因瀏覽器安全限制無法讀取 JSON。若已有 Python，可在此資料夾執行 `python -m http.server 8000`，再開啟 `http://localhost:8000/`。日常使用直接開 GitHub Pages 即可，不需要安裝 Python。

## 協作與版本

多人管理時，發布前請先讀取網站最新課程，避免舊草稿覆蓋其他人的修改。提交後可利用 GitHub 歷史記錄比較與還原。若分支有保護規則，請依 GitHub 提示建立 Pull Request 並合併後發布。
