# Shot Script Builder

Shot Script Builder 是一個給導演、攝影、創作者使用的視覺化鏡頭腳本與分鏡規劃工具。它支援 2D blocking、3D / Three.js 預覽、運鏡設計、燈光配置、參考圖管理、拍攝排程、通告單、分鏡匯出、AI prompt 準備與專案管理。

English: Shot Script Builder is a visual shot script and storyboard planning tool for directors, cinematographers, and creators.

## 啟動

Windows 可直接雙擊：

```text
啟動 Shot Builder.bat
```

或手動執行：

```bash
npm install
npm run dev
```

網址通常是：

```text
http://127.0.0.1:5173/
```

## GitHub Pages

本專案已加入 GitHub Pages Actions 設定。上傳到 GitHub 後：

1. 到 repo 的 `Settings`
2. 進入 `Pages`
3. `Build and deployment` 選 `GitHub Actions`
4. push 到 `main`

部署完成後網址會是：

```text
https://pijiawei03281.github.io/shot-script-builder/
```

詳細步驟見 [docs/github-pages.md](docs/github-pages.md)。

## 主要功能

- 2D 平面拖拉：角色、攝影機路徑、燈光、燈光目標、場景物件。
- Proxy 3D Preview：角色立柱、攝影機路徑、視錐、燈光 cone、物件方塊。
- True Three.js Preview：WebGL 場景，顯示角色、物件、燈光、攝影機路徑。
- 鏡頭時間線：新增、複製、刪除、拖拉排序 shot。
- Undo / Redo：保留最近 50 次專案變動。
- Onboarding：第一次打開顯示中英新手教學。
- 繁體中文 / English 切換。
- Access Mode：高對比、大字體、減少動畫、強化鍵盤焦點、色盲友善標記。
- 螢幕閱讀器摘要：提供目前 shot 的文字摘要，包含鏡頭、角色、燈光、道具。
- AI 劇本拆解：貼上劇本或 beat list，自動拆成 shot。
- 鏡頭規則資料庫：懸疑、廣告、MV、訪談、動作、產品片。
- Reference Board：每個 shot 可放多張參考圖，分成構圖、燈光、色彩、運鏡、production。
- Reference Pack Import：一次匯入多張 JPG/PNG。
- Equipment Mode：手機、相機、穩定器、滑軌、腳架、空拍。
- Difficulty Meter：依運鏡、燈光、物件、器材限制判斷 Easy / Medium / Hard。
- Blocking Mode：角色走位起點 / 終點，2D 圖上顯示走位線。
- Lens Mode：Phone Wide、Prime Set、Anamorphic、Macro、Telephoto。
- Color Mode：主色、輔色、對比、色溫、LUT、調色備註。
- Client Mode：客戶註解、修改狀態、版本紀錄、自動命名 shot。
- Compare Mode：A/B 比較兩顆 shot。
- Lighting Presets：Three Point、Low Key、High Key、Product Highlight、Neon MV。
- Scenes：場景 / 地點管理，匯入平面圖。
- Schedule：依場景、setup、難度產生現場拍攝順序。
- Setups：把可共用燈位 / 機位 / 道具配置的 shot 分組。
- Review：draft / review / approved / locked / shot 狀態。
- Continuity Snapshot：保存角色、道具、燈光、鏡頭狀態。
- Project Library：本機專案庫，可另存、載入、刪除專案。
- Backup：5 個本機備份槽。
- Templates：依類型快速建立新專案。
- Find：依標題、地點、情緒、狀態、setup、運鏡、焦段、角色、道具搜尋。

## 匯出

支援：

- project JSON
- current scene JSON
- current shot JSON
- full ZIP package
- Word-compatible `.doc`
- proposal HTML
- print storyboard HTML
- PDF-ready storyboard HTML
- call sheet HTML
- camera report HTML
- shot list CSV
- plain text

PDF-ready storyboard 打開後，用瀏覽器列印並選「另存為 PDF」即可。

## 測試

```bash
npm run typecheck
npm run build
npm test
```

`npm test` 會執行型別檢查與正式打包。

## 無障礙

`Access` 模式提供：

- High contrast / 高對比
- Large text / 大字體
- Reduce motion / 減少動畫
- Strong focus outline / 強化鍵盤焦點
- Color-safe marks / 色盲友善標記
- Screen reader scene summary / 螢幕閱讀器鏡頭摘要

狀態訊息也加入 `aria-live`，螢幕閱讀器可以讀到匯入、儲存、錯誤等提示。

## 參考圖資料夾

你可以把素材整理在：

```text
reference-library/suspense
reference-library/commercial
reference-library/music-video
reference-library/interview
reference-library/action
reference-library/product
```

瀏覽器不能自動掃描本機資料夾，所以正式匯入仍需用 App 裡的 `Reference` 或 `Import reference pack`。

## 範例

- 劇本拆解測試：[examples/sample-scene.txt](examples/sample-scene.txt)
- 匯入範例專案：[examples/sample-project.json](examples/sample-project.json)
- 後續規劃：[ROADMAP.md](ROADMAP.md)

## 備註

- `dist/`、`node_modules/`、`.npm-cache/` 不需要上傳 GitHub。
- 本機資料存在瀏覽器 localStorage，換瀏覽器或清除資料前請先匯出 project JSON 或 ZIP。
