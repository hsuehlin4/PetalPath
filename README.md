# 🌸 PetalPath 
**The Native macOS Location Injector for iOS.**

PetalPath 是一款專為 macOS 開發的原生應用程式，旨在透過 USB 連線為 iPhone 提供精準、穩定且流暢的 GPS 位置模擬服務。無論是進行適位性服務（LBS）的開發測試，或是探索地理資訊應用的更多可能性，PetalPath 都能讓您的裝置在數位地圖上自由穿梭。


---

## ✨ 核心特色 (Features)

* macOS 原生開發：採用 Swift 編寫，具備流暢的使用者介面與極低的系統資源占用。
* USB / WiFi 雙模連線：支援 USB 實體連線與 WiFi 無線連線，配對後無需插線即可使用。
* 即時座標同步：在 macOS 地圖上標定目標，即刻將虛擬 GPS 訊號同步至行動裝置。
* 路徑模擬模式：支援多點路徑規劃，模擬真實的移動路徑與速度（步行/騎行/開車）。
* 隱私與安全：無需越獄（Jailbreak），在標準 iOS 環境下即可運作。

---

## 🛠️ 系統需求

| 項目 | 需求 |
|---|---|
| Mac 作業系統 | macOS 13 Ventura 以上 |
| iPhone 系統 | iOS 16 以上（GPS 注入需要 Developer Mode） |
| Python | 3.10 以上 |
| 連接方式 | USB（首次配對）或 WiFi（配對後同網段可用）|

---

## 🚀 安裝步驟

### 1. 安裝 Python 套件

```bash
pip3 install "pymobiledevice3>=4.14.0"
```

或使用 requirements.txt：

```bash
pip3 install -r requirements.txt
```

> 建議使用 [pyenv](https://github.com/pyenv/pyenv) 管理 Python 版本，避免系統 Python 衝突。

### 2. iPhone 前置設定（一次性）

1. 開啟 iPhone 的**開發者模式**：
   設定 → 隱私權與安全性 → 開發者模式 → 開啟
2. 透過 USB 連接 iPhone 到 Mac
3. iPhone 出現「信任此電腦？」提示時，點選**信任**並輸入密碼

#### 選用：開啟 WiFi 無線連線

完成上方 USB 配對後，可啟用 WiFi 連線，之後無需插線即可使用：

1. 保持 USB 連接，開啟 Mac 上的 **Finder**
2. 在側邊欄「位置」下方點選你的 iPhone
3. 點選上方的「**一般**」標籤頁
4. 向下捲動，勾選「**在 Wi-Fi 上顯示此 [裝置名稱]**」
5. 點選右下角「**套用**」

設定完成後，只要 Mac 與 iPhone 連接至**同一個 Wi-Fi 網路**，PetalPath 即可自動偵測並透過 WiFi 連線，無需傳輸線。

> **⚠️ iOS 17+ 使用 WiFi 的注意事項**
>
> iOS 17 以上的裝置需要 GPS 隧道（tunneld）才能注入位置。由於 tunneld 目前透過 USB 建立隧道，**首次切換 WiFi 前需完成以下步驟**：
>
> 1. 先以 **USB 連接** iPhone，開啟 PetalPath
> 2. 輸入管理員密碼，等待左側顯示「**GPS 隧道已就緒**」
> 3. **拔掉 USB**，iPhone 自動切換為 WiFi 連線
> 4. 此時 tunneld 隧道仍維持運作，即可正常使用 GPS 注入
>
> 若直接以 WiFi 連線（未先插 USB），app 會顯示「tunneld 正在運行，但此裝置不在隧道清單」，需按照上述步驟重新操作。

### 3. 安裝 PetalPath

1. 下載最新版 `PetalPath.app`
2. 將 `PetalPath.app` 拖曳到 `/Applications` 資料夾
3. 首次開啟時，若出現「無法驗證開發者」提示：
   系統設定 → 隱私權與安全性 → 點選「仍要開啟」

---

## 📱 iOS 17+ 額外說明

iOS 17 以上使用新的 `DeveloperModeRemoteServerService` 機制，需要背景隧道服務（tunneld）才能注入 GPS。

- 首次啟動 GPS 注入時，PetalPath 會請求**管理員密碼**以啟動 tunneld，這是正常行為
- tunneld 啟動後，左側狀態列會顯示「GPS 隧道已就緒」
- 若使用 WiFi 連線，請參考上方「[WiFi 無線連線注意事項](#選用開啟-wifi-無線連線)」的操作流程

---

## 💻 使用方式

1. 開啟 PetalPath，左側裝置列表會自動偵測已連接的 iPhone
2. 在地圖上點選目標位置，或在輸入框輸入經緯度，或使用「貼上位置」貼上座標
3. 點選「移動位置」即完成 GPS 注入
4. 點選「清除位置」恢復正常 GPS

---

## ⚠️ 免責聲明 (Disclaimer)

1. 本專案僅供軟體開發測試與教育研究用途。
2. 使用者在利用本工具進行位置模擬時，請務必遵守第三方服務（如 AR 遊戲、地圖工具等）的使用條款（ToS）。
3. 開發者對於因不當使用本工具而導致的帳號停權、損害或法律責任概不負責。

---

## 🧑🏻‍💻 作者 (Author)

**Lawrence.Shih** 

<small>一個因為家人需求而下班也要為愛開發的 Data Engineer</small> 

* **Contact** - [GitHub](https://github.com/hsuehlin4) | [Personal Website](https://github.com/hsuehlin4)

---

> 如果您覺得 PetalPath 對您有幫助，歡迎給個 ⭐ Star 支持！
