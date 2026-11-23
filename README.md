# 🎮 Super Cloud SNES | 超任雲端極速模擬器

[![WebAssembly](https://img.shields.io/badge/WebAssembly-Snes9x-blue.svg)](https://emulatorjs.org)
[![Cloudflare Pages](https://img.shields.io/badge/Deploy-Cloudflare%20Pages-orange.svg)](https://pages.cloudflare.com)
[![Vercel](https://img.shields.io/badge/Deploy-Vercel-black.svg)](https://vercel.com)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

一個現代化、跨平台、打開瀏覽器即可**即刻暢玩 60FPS** 的超級任天堂（SNES / SFC）雲端模擬器。
具備類似 Nintendo Switch / Netflix 的頂級暗色封面牆介面、預載精選遊戲庫、支援自備 ROM 拖曳即玩、藍牙/USB 實體手把隨插即用、手機虛擬搖桿與雲端存檔管理。

---

## ✨ 核心特色

1. **⚡ 零安裝、全平台跨端遊玩**：
   - 支援 Windows / Mac / Linux 桌面瀏覽器。
   - 支援 iPhone / iPad (Safari) 與 Android 手機，可「加入主畫面」全螢幕無邊框執行。
   - 支援客廳智慧電視 / Apple TV 瀏覽器，大螢幕暢快回味。
2. **🎮 實體手把隨插即用 (Web Gamepad API)**：
   - 完美相容 PS5 / PS4 DualSense、Xbox Series / One、Switch Pro Controller、8BitDo 手把，按鍵自動對齊。
3. **🕹️ 手機/平板自適應觸控搖桿**：
   - 行動裝置自動喚出半透明十字鍵（D-Pad）、經典 SFC 四色菱形動作按鍵（ABXY）與 L/R 雙肩鍵，並具備震動觸覺回饋（Haptic Feedback）。
4. **💾 自動存檔與進度管理**：
   - 記憶卡電池存檔（SRAM）與即時狀態（Save State）自動儲存於瀏覽器 IndexedDB。
   - 支援一鍵備份匯出全部進度（JSON）與還原匯入。
5. **📺 CRT 復古掃描線濾鏡**：
   - 一鍵開啟 90 年代老電視顯像管掃描線（Scanlines）光學質感。
6. **🚀 預載遊戲庫 + 自備 ROM 拖曳即玩**：
   - 預先打包 4 款經典 Homebrew 完整遊戲（《超首領外傳》、《星際獵鷹》、《斯基普與夥伴們》、《噴射王牌》），免下載秒開。
   - 內建 10 款傳世經典（超時空之鑰繁中、瑪利歐世界、洛克人 X、三角神力、快打旋風 2 等）專屬卡帶插槽，隨時拖曳 `.sfc` / `.smc` / `.zip` 立即開打。

---

## 🕹️ 操作按鍵說明

### 鍵盤 1P 預設鍵位
| 超任手把按鍵 | 鍵盤預設鍵位 |
| :--- | :--- |
| **方向十字鍵 (D-Pad)** | <kbd>↑</kbd> <kbd>↓</kbd> <kbd>←</kbd> <kbd>→</kbd> |
| **B 鍵 (跳躍/取消)** | <kbd>Z</kbd> |
| **A 鍵 (攻擊/確認)** | <kbd>X</kbd> |
| **Y 鍵 (奔跑/蓄力)** | <kbd>A</kbd> |
| **X 鍵 (特殊攻擊)** | <kbd>S</kbd> |
| **L 肩鍵** | <kbd>Q</kbd> |
| **R 肩鍵** | <kbd>W</kbd> |
| **SELECT** | <kbd>Shift</kbd> |
| **START** | <kbd>Enter</kbd> |

### 快捷輔助功能
- **F2**：快速即時存檔（Quick Save）
- **F4**：快速載入進度（Quick Load）
- **Backspace（長按）**：時光倒帶（Rewind）
- **Space（長按）**：2x 狂飆加速（Fast Forward）
- **F11**：全螢幕無邊框切換

---

## ☁️ 雲端一鍵部署指南

本專案為**純前端靜態與 WebAssembly 架構**，可完全免費託管於任何雲端平台：

### 方案 A：Cloudflare Pages（推薦 · 全球 CDN + 零流量費）
1. 將本專案資料夾推送到您的 GitHub / GitLab 倉庫。
2. 登入 [Cloudflare Dashboard](https://dash.cloudflare.com/) 點選 **Workers & Pages** -> **Create application** -> **Pages**。
3. 連結您的 GitHub 倉庫。
4. 設定參數：
   - **Framework preset**: `None`
   - **Build command**: （留空）
   - **Build output directory**: `.`
5. 點擊 **Save and Deploy**，30 秒內即可獲得專屬網址（例如 `https://snes-station.pages.dev`）！

### 方案 B：Vercel
1. 登入 [Vercel](https://vercel.com/) 點選 **Add New...** -> **Project**。
2. 匯入本專案 GitHub 倉庫。
3. 保持預設設定，點選 **Deploy** 即刻上線！

### 方案 C：GitHub Pages
1. 在 GitHub 倉庫進入 **Settings** -> **Pages**。
2. **Source** 選擇 `Deploy from a branch`。
3. **Branch** 選擇 `main` / `root (/)`，點擊 Save 即可。

---

## 📁 擴充自訂遊戲庫指南

若想在遊戲選單中增加自己的預設遊戲，只需編輯 `data/games.json`：

```json
{
  "id": "my-cool-game",
  "title": "我的遊戲名稱",
  "region": "TW/HK",
  "language": "繁體中文版",
  "year": 1995,
  "genre": "RPG",
  "category": ["chinese", "rpg"],
  "players": 1,
  "preloaded": true,
  "cover": "assets/covers/my_game.svg",
  "rom": "assets/roms/my_game.sfc",
  "size": "2.0 MB",
  "description": "遊戲簡介說明..."
}
```

將對應的封面圖片放入 `assets/covers/`，ROM 檔案放入 `assets/roms/` 即可！

---

## 💻 本機即時測試運行

本機測試可透過任何輕量 HTTP 伺服器啟動：

```bash
# 方式 1：使用 Python 內建伺服器
python -m http.server 8080

# 方式 2：使用 Node.js
npx serve -l 8080 .
```

開啟瀏覽器前往 `http://localhost:8080` 即可暢玩！
