# 🛒 Vue 3 購物車練習專案

> Vue 3 + Vite + Bootstrap 5 實作的商品列表與購物車功能練習

## 📖 專案說明

本專案為 Vue 3 的課堂作業，練習以下核心概念：

- **元件拆分**：將頁面功能拆分為 `ProductList`、`CartList`、`NotificationList` 三個子元件
- **Props / Emits**：父子元件之間的資料傳遞與事件通信
- **provide / inject**：跨層元件共享通知狀態與方法
- **`ref` 響應式資料**：管理商品清單、購物車內容

## ✨ 功能特色

- 📦 **商品列表**：以卡片方式展示商品名稱、描述、價格與圖片
- 🛒 **購物車**：加入商品、重複加入自動累加數量、計算小計、移除商品
- 🔔 **通知提示**：加入 / 移除購物車時，右上角顯示 Toast 通知，3 秒後自動消失

## 🗂️ 專案結構

```
vue-homework1/
├── src/
│   ├── components/
│   │   ├── ProductList.vue      # 商品列表元件
│   │   ├── CartList.vue         # 購物車元件
│   │   └── NotificationList.vue # Toast 通知元件
│   ├── App.vue                  # 根元件（狀態管理、provide/inject）
│   └── main.js                  # 應用程式入口
├── index.html
├── vite.config.js
└── package.json
```

## 🔧 技術棧

| 技術 | 版本 | 用途 |
|------|------|------|
| [Vue 3](https://vuejs.org/) | ^3.5 | 前端框架（Composition API） |
| [Vite](https://vite.dev/) | ^8.0 | 建置工具 / 開發伺服器 |
| [Bootstrap](https://getbootstrap.com/) | ^5.3 | UI 樣式框架 |
| [ESLint](https://eslint.org/) | ^10 | 程式碼品質檢查 |
| [Prettier](https://prettier.io/) | 3.x | 程式碼格式化 |
| [Oxlint](https://oxc.rs/docs/guide/usage/linter) | ~1.60 | 高速 Lint 輔助工具 |

## 🚀 快速開始

### 環境需求

- Node.js `^20.19.0` 或 `>=22.12.0`

### 安裝與啟動

```sh
# 安裝相依套件
npm install

# 啟動開發伺服器（含 Hot Reload）
npm run dev
```

開啟瀏覽器前往 `http://localhost:5173`

### 其他指令

```sh
# 建置正式版本
npm run build

# 預覽正式建置結果
npm run preview

# 執行 Lint 並自動修正
npm run lint

# 格式化 src/ 下的程式碼
npm run format
```

## 🧩 元件說明

### `App.vue`（根元件）

- 定義商品清單 `products`（`ref`）與購物車 `carts`（`ref`）
- 提供 `addCart`、`removeCart` 方法給子元件使用
- 透過 `provide` 注入通知狀態 `notificationState` 與 `showNotification` 方法

### `ProductList.vue`

- 接收 `products` prop，以 Bootstrap Card 渲染商品列表
- 點擊「加入購物車」時透過 `emit` 通知父元件，並觸發通知提示

### `CartList.vue`

- 接收 `carts` prop，渲染購物車清單與各項小計
- 點擊「移除」時透過 `emit` 通知父元件，並觸發通知提示
- 購物車為空時顯示提示文字

### `NotificationList.vue`

- 透過 `inject` 取得通知狀態
- 使用 Bootstrap Toast 樣式在右上角顯示操作回饋，3 秒後自動隱藏

## 💡 Vue 3 重點概念對照

| 概念 | 使用位置 |
|------|----------|
| `ref()` | `App.vue` — `products`、`carts`、`notificationState` |
| `provide()` | `App.vue` — 注入通知相關狀態與方法 |
| `inject()` | `ProductList.vue`、`CartList.vue`、`NotificationList.vue` |
| `defineProps()` | `ProductList.vue`、`CartList.vue` |
| `defineEmits()` | `ProductList.vue`、`CartList.vue` |
| `v-for` / `v-if` | 各子元件渲染列表與條件顯示 |

## 🛠️ 推薦開發環境

- **編輯器**：[VS Code](https://code.visualstudio.com/) + [Vue - Official](https://marketplace.visualstudio.com/items?itemName=Vue.volar) 擴充套件（請停用 Vetur）
- **瀏覽器除錯**：
  - Chrome / Edge：[Vue.js devtools](https://chromewebstore.google.com/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)
  - Firefox：[Vue.js devtools](https://addons.mozilla.org/en-US/firefox/addon/vue-js-devtools/)
