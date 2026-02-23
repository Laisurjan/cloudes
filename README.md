# 即時互動平台 v2

重新設計的課堂互動系統，支援問答蒐集、文字雲、投票三種題型。

## 主要改進

| 功能 | 說明 |
|------|------|
| **題庫管理** | 以「題庫」為單位組織題目，方便管理不同課程/主題 |
| **Google 登入** | 只有指定帳號 (walala@hlbh.hlc.edu.tw) 可管理 |
| **安全規則** | 學生只能提交回覆，無法刪除或修改資料 |
| **全螢幕模式** | 演示時按 F 鍵切換全螢幕 |
| **暫停作答** | 可隨時暫停/開放學生作答 |
| **90 天 TTL** | 資料保留 90 天（比原本 30 天更長） |

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
git remote add origin https://github.com/YOUR_USERNAME/interactive-platform.git
git push -u origin main
```

然後在 GitHub：
1. **Settings** → **Pages**
2. Source 選擇 `main` branch, `/ (root)` folder
3. 等待部署完成

---

## 使用方式

### 老師

1. 點擊「老師登入」用 Google 帳號登入
2. 建立題庫 → 新增題目
3. 點擊「開始演示」進入展示模式
4. 分享 QR Code 給學生掃描

### 學生

1. 掃描 QR Code 或輸入房號
2. 等待老師選題
3. 提交回答

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
