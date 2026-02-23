# 即時互動平台 v2

重新設計的課堂互動系統，支援多種題型與精美的蘋果風格介面。

## 主要功能

### 題型支援

| 題型 | 說明 |
|------|------|
| **問答蒐集** | 學生自由回答，支援按讚投票功能 |
| **文字雲** | 將回答以視覺化文字雲呈現 |
| **投票（單選/多選）** | 支援單選或多選的選項投票 |
| **評分量表** | 1-10 分的滑桿評分 |
| **排序題** | 拖曳排序選項，支援取消選擇 |

### 系統特色

| 功能 | 說明 |
|------|------|
| **題庫管理** | 以「題庫」為單位組織題目，方便管理不同課程/主題 |
| **Google 登入** | 只有指定帳號 (walala@hlbh.hlc.edu.tw) 可管理 |
| **安全規則** | 學生只能提交回覆，無法刪除或修改資料 |
| **全螢幕模式** | 演示時按 F 鍵切換全螢幕 |
| **暫停作答** | 可隨時暫停/開放學生作答 |
| **90 天 TTL** | 資料保留 90 天 |
| **字體縮放** | A-/A+ 按鈕調整介面文字大小 (60%-200%) |
| **響應式設計** | 自動適應電腦、平板、投影等不同裝置 |
| **匯出報表** | 一鍵匯出 XLSX 格式報表 |
| **匯入題庫** | 支援 XLSX/CSV 格式匯入題目 |
| **蘋果風格介面** | 毛玻璃效果 (Glassmorphism) 精美設計 |

---

## 部署步驟

### 1. 設定 Firebase Firestore 規則

1. 前往 [Firebase Console](https://console.firebase.google.com/)
2. 選擇專案 `ai-test-ac0b6`
3. 進入 **Firestore Database** → **規則**
4. 將 `firestore.rules` 的內容貼上，點擊「發布」

### 2. 啟用 Google 登入

1. 在 Firebase Console 進入 **Authentication** → **Sign-in method**
2. 啟用 **Google** 提供者
3. 設定專案名稱和支援電子郵件

### 3. 部署到 GitHub Pages

```bash
# 建立新倉庫或使用現有倉庫
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/Laisurjan/cloudes.git
git push -u origin main
```

然後在 GitHub：
1. **Settings** → **Pages**
2. Source 選擇 `main` branch, `/ (root)` folder
3. 等待部署完成

**線上網址**: https://laisurjan.github.io/cloudes/

---

## 使用方式

### 老師

1. 點擊「老師登入」用 Google 帳號登入
2. 建立題庫 → 新增題目
3. 點擊「開始演示」進入展示模式
4. 分享 QR Code 給學生掃描
5. 可隨時切換題目、暫停作答、清除回覆

### 學生

1. 掃描 QR Code 或輸入房號
2. 填寫基本資料（如老師有開啟）
3. 等待老師選題後提交回答

### 快捷鍵

| 按鍵 | 功能 |
|------|------|
| **F** | 切換全螢幕模式 |
| **←** / **→** | 上一題 / 下一題 |
| **ESC** | 退出全螢幕 |

---

## 匯入格式說明

### XLSX/CSV 格式

| 欄位 | 說明 |
|------|------|
| 題目 | 題目內容（必填） |
| 類型 | qa / wordcloud / poll / rating / ranking |
| 選項 | 各選項以分號「;」分隔 |
| 多選 | TRUE 或 FALSE（僅投票題適用） |

**範例**:
```
題目,類型,選項,多選
你覺得今天的課程如何？,qa,,
用一個詞形容今天的心情,wordcloud,,
你最喜歡哪種教學方式？,poll,講述;討論;實作;遊戲,FALSE
請為課程評分,rating,,
請排序學習優先順序,ranking,理論;實作;測驗;討論,
```

---

## 檔案結構

```
interactive-platform/
├── index.html       # 主程式（單一 HTML 檔案）
├── firestore.rules  # Firebase 安全規則
└── README.md        # 說明文件
```

---

## 技術架構

- **前端**: 純 HTML/CSS/JavaScript（無框架）
- **後端**: Firebase Firestore（即時資料庫）
- **認證**: Firebase Authentication（Google 登入）
- **部署**: GitHub Pages（靜態網站）
- **匯出**: XLSX.js 函式庫
- **UI 風格**: Apple Glassmorphism（毛玻璃效果）

---

## 瀏覽器支援

- Chrome 76+
- Firefox 70+
- Safari 14+
- Edge 79+

*需支援 CSS `backdrop-filter` 屬性才能完整呈現毛玻璃效果*
