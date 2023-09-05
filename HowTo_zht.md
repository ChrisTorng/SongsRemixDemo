# SongsRemix 如何自行製作曲目庫

## 簡介

### 第一次預備
  1. 安裝必要工具
  2. 下載範例曲目庫
  3. 本機測試
  4. 首次發佈

### 之後每一次加曲目
  1. 取得原始音檔
  2. 製作分軌
  3. 製作波形圖
  4. 加入曲目資料
  5. 發佈更新

  以下分段詳細說明。

## 第一次預備

### 安裝必要工具
  * 安裝 [youtube_dl](https://oleksis.github.io/youtube-dl-gui/)
  * 安裝 [Ultimate Voice Remover](https://github.com/anjok07/ultimatevocalremovergui)
    1. 左下扳手圖示 - Additional Settings - Mp3 Bitrate: 128k (與來源檔案一致)
    2. Download Center - 選取 Demucs - 下拉選取 Demucs v4 | htdemucs_6s - 按下載圖示
    3. CHOOSE PROCESS METHOD: Demucs; CHOOSE DEMUCS MODEL: v4 | htdemucs_6s
  * 安裝 [Python](https://www.python.org/)
  * 安裝 [Node.js](https://nodejs.org/)
  * 安裝 [Git](https://git-scm.com/)

### 下載範例曲目庫

### 本機測試
  1. 於範例曲目庫資料夾開啟命令列
  2. 執行 `npm install -g http-server` 安裝 (只需安裝一次)
  3. 執行 `npx http-server --cors -p 3001` 啟動本機網站，或於 Windows 中執行 `run.cmd`
  4. 開啟 [http://localhost:3001](http://localhost:3001) 檢視成果

### 首次發佈
  1. git commit/push

## 之後每一次加曲目

### 取得原始音檔
  1. 執行 youtube_dl - 輸入所有 YouTube 網址 - 選擇輸出資料夾為曲目庫資料夾 - 選擇 mp3 - Add - 右下角 Start
  2. 將所有來源 mp3 檔名變更為預定顯示的文字

### 製作分軌
  1. 執行 Ultimate Voice Remover
  2. Select Input - 選擇所有來源 mp3 檔
  3. Select Output - 選擇曲目庫資料夾
  4. 若有獨立顯示卡 (如電競主機/筆電) 選擇 GPU Conversion 執行快很多。若執行出錯則取消此項
  5. Start Processing

### 重新命名檔名
  2. 於曲目庫資料夾開啟命令列視窗
  3. 執行 `python SongsRename.py`，它會將目前資料夾中所有 mp3 檔，依曲目檔名自動搬移至新建立之資料夾，並僅留樂器名稱檔名 (必須全小寫，不含複數結尾 s)，來源檔案則改名為 original.mp3

### 製作波形圖
  執行 `python waveform.py`，它會自動搜尋所有子資料夾下所有 mp3 未有對應 png 檔者，自動建立對應波形圖

### 加入曲目資料
  1. 編輯曲目庫中 songsList.json
  2. 複製/修改 groups 項目
  3. 更新 `subTitle`。`subTitleUrl` 可事後增加，目前還沒有則清空內容字串
  4. 修改各曲目之 `name` 必須符合資料夾名稱，`youtubeId` 由 YouTube 網址中之 `v=` 參數後取得 
  5. 依第一次本機測試方法確認

### 發佈更新