# Shot Script Builder

這是一個用 TypeScript + React + Konva.js 製作的鏡頭腳本生成器原型。它可以用拖拉積木的方式安排角色、攝影機、燈光、物件、參考圖、鏡頭時間線，並輸出提案、鏡頭表、AI prompt 和專案 JSON。

## 啟動

最簡單的方式是直接雙擊：

```text
啟動 Shot Builder.bat
```

它會自動安裝需要的套件、啟動本機預覽，並打開瀏覽器。

也可以手動執行：

```bash
npm install
npm run dev
```

網址通常是 `http://127.0.0.1:5173/`。

## 主要功能

- 2D 平面拖拉：角色、攝影機起點/終點/控制點、燈光、燈光目標、場景物件。
- 3D Preview：角色立柱、攝影機路徑、frustum 視錐、spotlight cone、物件方塊、高度 / Z 軸。
- 攝影機視角：可切換 Orbit View / Camera View。
- 鏡頭動畫預覽：Play/Pause 和進度滑桿會沿攝影機路徑播放。
- 3D PNG 截圖：可輸出目前 3D 預覽圖。
- 鏡頭時間線：新增、複製、刪除、拖拉排序 shot。
- 術語自動判斷：依路徑推測 dolly、truck、pan、arc dolly 等鏡頭語法。
- 光錐視覺化：可調光線角度、強度、柔硬度、顏色、高度。
- AI 劇本拆解：貼上劇本或 beat list，自動拆成鏡頭。
- 鏡頭規則資料庫：懸疑、廣告、MV、訪談、動作、產品片各有不同檢查邏輯。
- 鏡頭語法教練：依類型提示構圖、燈光、節奏、產品高光或遮蔽揭露。
- 參考圖匯入：可把 JPG/PNG 匯入目前 shot。
- 完整交付匯出：Word-compatible `.doc`、HTML、CSV、JSON、TXT。
- 自動儲存：專案會存進瀏覽器 localStorage。
- 內建範例專案：用 `Load Sample` 快速載入。

## 新增工作模式

上方模式列現在有五個專用模式：

- Reference Mode：匯入參考圖、加標籤、套用到目前 shot。
- Pitch Mode：把目前專案整理成提案文字，並快速輸出 HTML / Word。
- Shoot Mode：現場拍攝 checklist，可勾選完成 shot 並寫現場備註。
- Continuity Mode：檢查方向、光線跳動、景別節奏、物件消失等連戲問題。
- Mood-to-Shot Mode：輸入情緒關鍵字，自動生成三個可編輯 shot。
- Equipment Mode：選手機、相機、穩定器、滑軌、腳架或空拍，檢查目前鏡頭是否適合。
- Storyboard Mode：輸出可列印分鏡表，包含參考圖、鏡頭資訊、燈光與難度。
- Dashboard：總覽 shot 數、總秒數、場景數、困難鏡頭、缺參考圖、已核准或鎖定數量。
- Scenes：管理場景 / 地點，匯入平面圖，並把目前 shot 指派到場景。
- Schedule：依場景、setup、難度自動產生現場拍攝順序。
- Setups：用 setup ID 把可共用燈位、機位、道具的 shot 分組。
- Review：設定 shot 狀態，包含 draft / review / approved / locked / shot。
- Continuity Snapshot：捕捉目前角色、道具、燈光、鏡頭狀態，方便連戲比對。
- Prompt Coach：檢查 prompt 是否缺少景別、鏡頭、光線、色彩、焦段等資訊。
- Blocking：替每個角色設定走位起點 / 終點，並在 2D 平面圖上顯示走位線。
- Lens：選擇鏡頭組，包含 Phone Wide、Prime Set、Anamorphic、Macro、Telephoto。
- Color：規劃每顆 shot 的主色、輔色、對比、色溫、LUT 和調色備註。
- Client：管理客戶註解、修改狀態、版本紀錄，也能自動命名 shot。
- Compare：A/B 比較兩顆 shot 的構圖縮圖、景別、運鏡、焦段、燈光數與難度。
- Lighting：一鍵套用 Three Point、Low Key、High Key、Product Highlight、Neon MV 燈光預設。
- 語言切換：右上角可切換繁體中文 / English，模式列與新增工具會跟著切換。
- PDF-ready Storyboard：輸出可列印 HTML，打開後用瀏覽器列印成 PDF。
- Call Sheet：輸出拍攝通告單 HTML，包含場景、setup、角色、道具、燈數、難度與狀態。
- Templates：依懸疑、廣告、MV、訪談、動作、產品片快速建立新專案。
- Backup：五個本機備份槽，可保存、還原、清除目前專案。
- Find：依標題、地點、情緒、狀態、setup、運鏡、焦段、角色、道具搜尋 shot。
- Camera Report：輸出攝影報告 HTML，包含運鏡、景別、焦段、高度、鏡頭組與手持狀態。

## Reference Board

每個 shot 現在可以放多張參考圖，並分類成：

- composition
- lighting
- color
- movement
- production

匯入圖片時會同時更新目前 shot 的主參考圖，也會新增到 reference board。這樣你可以把「構圖參考」「打光參考」「色彩參考」分開管理。

## Equipment / Difficulty

Equipment Mode 會依照目前器材判斷鏡頭是否合理：

- Phone
- Mirrorless
- Gimbal
- Slider
- Tripod
- Drone

App 會依運鏡、燈光數量、物件數量、手持、鏡頭長度和器材限制給出 Easy / Medium / Hard。

## 場景與拍攝排程

`Scenes` 模式可以新增場景、修改場景類型，並匯入 JPG/PNG 平面圖。匯入後，平面圖會顯示在 2D blocking 區上方，方便你照房間、街道或棚內配置安排鏡頭。

`Schedule` 模式會用「場景 -> setup -> 難度」排序，不是剪輯順序，而是比較接近現場拍攝順序。`Setups` 模式則會把同一組燈位、機位或道具配置的 shot 放在一起，方便一次拍完。

## Review / Lock

`Review` 模式可以把 shot 標記成：

- draft
- review
- approved
- locked
- shot

也可以一鍵保存 continuity snapshot，記錄角色位置、道具位置、燈光狀態和鏡頭狀態。

## Blocking / Lens / Color / Client

`Blocking` 模式可以為角色設定 start / end mark，2D 圖上會顯示角色走位軌跡。

`Lens` 模式會依鏡頭組檢查焦段是否合理，並可一鍵套用該鏡頭組的焦段。

`Color` 模式可為每顆 shot 設定主色、輔色、對比、色溫、LUT 和備註。

`Client` 模式可新增客戶註解、標記 open / in progress / resolved、保存版本紀錄，並自動生成 shot 名稱。

## Compare / Lighting / Export

`Compare` 模式可以把目前 shot 和另一顆 shot 並排比較，快速看景別、運鏡、焦段、燈光數量和拍攝難度。

`Lighting` 模式提供常用燈光預設，可快速套用到目前 shot，再到右側 inspector 微調燈位、亮度、光錐和顏色。

`Storyboard` 模式現在可以輸出：

- print storyboard HTML
- PDF-ready storyboard HTML
- call sheet HTML
- camera report HTML

PDF-ready 檔案打開後，使用瀏覽器的列印功能選「另存為 PDF」即可。

## Templates / Backup / Find

`Templates` 模式可以快速從類型建立新專案：懸疑、廣告、MV、訪談、動作、產品片。

`Backup` 模式提供 5 個瀏覽器本機備份槽，適合在大改前保存目前版本。

`Find` 模式可搜尋 shot 的標題、地點、情緒、狀態、setup、運鏡、焦段、角色或道具。

## 參考圖資料夾

可以把圖片放進對應資料夾整理：

```text
reference-library/suspense
reference-library/commercial
reference-library/music-video
reference-library/interview
reference-library/action
reference-library/product
```

瀏覽器版目前不能自動掃描本機資料夾，所以正式匯入仍要用 App 裡的 `Reference` 或 `Reference Mode` 匯入按鈕。資料夾先當成你的素材庫分類。

## 範例

- 劇本拆解測試：[examples/sample-scene.txt](examples/sample-scene.txt)
- 匯入範例專案：[examples/sample-project.json](examples/sample-project.json)
- 後續規劃：[ROADMAP.md](ROADMAP.md)

## 小提醒

- 目前 3D 是 proxy 版本，已能表達高度、視錐、燈光 cone 和動畫路徑。
- 如果要變成真正 Three.js 即時 3D 場景，需要能安裝 `three` 套件後再升級。
- `preview.html` 是免安裝快速預覽版；最完整功能在 React App。
