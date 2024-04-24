# CS3311 Lab6

## 標題：延續Lab2,3課程內容，於Raspberry Pi 4上進行實作

> 教材編輯者：陳昱丞 ||
> 課程講解：張黛妤（代班）||
> 範例程式編輯：陳昱丞、陳宥云

> ***last updated: 2024/04/24***

---

## README.md 目錄

1. [實驗步驟](#實驗步驟)
2. [評分和繳交格式](#評分和繳交格式)
3. [常見問題](#常見問題)

---

## 實驗步驟

1. Raspberry Pi 4 刷機
    - 到[Raspberry Pi Imager](https://www.raspberrypi.com/software/)下載匹配自己作業系統之版本
        - 開啟Raspberry Pi Imager，點選對應Raspberry Pi OS安裝之版本
            - Operating system：Raspberry Pi OS(64bits)
            - Raspberry Pi Device:Raspberry Pi 4
            - Storage: xxxx Media(MicroSD)
        - 將MicroSD卡放置到Rpi4**背面**，並接上電源線、螢幕連接線、鍵盤、滑鼠後，開機
    - 開機後，會進行一系列初始化設定（設定名稱、密碼、時區等資訊）
    - 將Rpi4連接到網際網路（建議個人熱點，較穩定）

2. Arduino IDE 安裝（可參考Lab2,3教材，此部分簡略說明）
    - 下載所需之環境
        - Environment:Arduino IDE
        - Board manger:ESP32manger
        - Library:DHT11
    - [範例檔案 ESP32_send_to_server.ino](ESP32_send_to_server.ino，)
        - 修改對應的網路資訊（SSID、Password、ServerIP）
    - [在rpi4安裝Arduino IDE bash file SetupArduinoIDE.sh](./SetupArduinoIDE.sh)

3. 運行Flask server，執行 [RESTful API](https://zh.wikipedia.org/zh-tw/%E8%A1%A8%E7%8E%B0%E5%B1%82%E7%8A%B6%E6%80%81%E8%BD%AC%E6%8D%A2)
    - 在終端機中執行`app.py`啟動server
    - 從Console中確認資料是否正確傳輸到rpi4之server

4. 成果示意圖
![成果示意圖1](./figures/DHT11toServer.gif)
![成果示意圖2](./figures/StartServer.gif)

---

## 評分和繳交格式

> 可參考助教提供sourcecode，但直接複製貼上者零分計算!
> 請自行發揮介面設計和資料呈現方式，善用ChatCGPT。

### 評分

1. 基本分(60％)(承Lab2,3實作內容)
    - **20%** ESP32傳輸溫濕度（在Arduino IDE中SerialPort觀測量測到之數據）
    - **20%** 使用Flask製作前端頁面（Frontend&UI）
    - **20%** 使用Flask製作後端API設計（Backend）

2. 進階分(40%)
    - **20%** 呈現即時數據表現（每五秒更新一次數據）
    - **20%** 可觀看過去某個時間區段資料

3. 加分(10%)
    - 根據文件整理、程式運行情形，酌量給予加分
    - *備註：此作業最多100分，超過100分者，仍以100分為計*

### 繳交格式

請附上兩個部分:**說明文件**和**完整程式碼壓縮檔**

1. **說明文件**，
    - 格式：markdown language(如[Notion](https://www.notion.so/)或[HackMD](https://hackmd.io/))請繳交.md檔，抑或是輸出成PDF
    - 要點一：請依評分項，分別進行說明（若有使用ChatGPT，也可以**整理後**附上）
    - 要點二：成果展示（.GIF）、畫面錄影（可上傳至YT，並附上**可點閱**之影片連結）、截圖

2. **完整程式碼**
    - 途徑一：使用**Github連結**（需設為公開，助教才能閱覽）
    - 途徑二：壓縮程式碼，上傳至**iLearning系統**，Lab6

---

## 常見問題

1. 無法正常將DHT11感測器之溫濕度資料，透過ESP32呈現在Arduino IDE中之Serial Port？
    - 請先查閱Lab2,3教材，完成該課程之進度，再接續。
2. 執行`python app.py`後，遇到Permission error
    - 調整`app.py`中，執行flask server之port（如:5000）
