# Laravel Vue Todo App

這是一個使用 Vue 3 和 Laravel 10.* 實現的待辦事項管理系統。專案實現了待辦事項的基本 CRUD（創建、讀取、更新、刪除）操作，並與數據庫進行交互。

## 功能

- 創建新的待辦事項
- 查看所有待辦事項列表
- 更新現有待辦事項的狀態或內容
- 刪除不需要的待辦事項

## 技術

- 後端: Laravel 10.*
- 前端: Vue 3
- 數據庫: MySQL (或者您使用的其他數據庫)
- API: RESTful API

## 安裝

1. 複製儲存庫:
   ```
   git clone https://github.com/your-username/your-repo-name.git
   ```
2. 進入項目目錄:
   ```
   cd your-repo-name
   ```
3. 安裝 PHP 依賴:
   ```
   composer install
   ```
4. 安裝 JavaScript 依賴:
   ```
   npm install
   ```
5. 複製 `.env.example` 到 `.env` 並配置您的環境:
   ```
   cp .env.example .env
   ```
6. 生成應用密鑰:
   ```
   php artisan key:generate
   ```
7. 運行數據庫遷移:
   ```
   php artisan migrate
   ```

## 使用

1. 啟動 Laravel 開發服務器:
   ```
   php artisan serve
   ```
2. 在另一個終端窗口，啟動 Vue 開發服務器:
   ```
   npm run dev
   ```
3. 在瀏覽器中訪問 `http://localhost:8000`