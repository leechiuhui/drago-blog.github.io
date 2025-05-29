# Drago Blog

一個基於 Jekyll 的靜態部落格網站。

## 📋 目錄

- [專案介紹](#專案介紹)
- [系統需求](#系統需求)
- [安裝與設定](#安裝與設定)
- [使用方法](#使用方法)
- [專案結構](#專案結構)
- [部署](#部署)
- [貢獻](#貢獻)

## 📖 專案介紹

這是一個使用 Jekyll 框架建立的靜態部落格網站，採用 Minima 主題。Jekyll 是一個簡單、支援部落格的靜態網站生成器，非常適合用於 GitHub Pages。

## 🔧 系統需求

在開始之前，請確保您的系統已安裝以下工具：

- **Ruby** (版本 2.7 或更高)
- **Bundler** (Ruby 套件管理工具)
- **Git**

### 檢查系統環境

```bash
# 檢查 Ruby 版本
ruby --version

# 檢查 Bundler 版本
bundle --version
```

## 🚀 安裝與設定

### 1. 複製專案

```bash
git clone https://github.com/your-username/drago-blog.github.io.git
cd drago-blog.github.io
```

### 2. 安裝依賴

```bash
bundle install
```

### 3. 啟動開發伺服器

```bash
bundle exec jekyll serve
```

成功啟動後，您可以在瀏覽器中訪問：
- **本地網址**: http://localhost:4000

## 💻 使用方法

### 啟動開發環境

```bash
# 啟動開發伺服器（支援即時重載）
bundle exec jekyll serve

# 啟動開發伺服器並監聽所有網路介面
bundle exec jekyll serve --host 0.0.0.0

# 啟動開發伺服器並啟用草稿功能
bundle exec jekyll serve --drafts

# 使用不同端口（如果 4000 端口被佔用）
bundle exec jekyll serve --port 4001
```

### 解決端口衝突問題

如果遇到 `Address already in use - bind(2) for 127.0.0.1:4000` 錯誤：

```bash
# 方法 1: 查找並終止佔用端口的程序
lsof -ti:4000
kill -9 [程序ID]

# 方法 2: 使用不同端口
bundle exec jekyll serve --port 4001

# 方法 3: 強制終止所有 Jekyll 程序
pkill -f jekyll
```

### 建置靜態網站

```bash
# 建置網站到 _site 目錄
bundle exec jekyll build

# 建置並監聽檔案變更
bundle exec jekyll build --watch
```

### 新增文章

1. 在 `_posts/` 目錄中創建新文件
2. 檔名格式：`YYYY-MM-DD-title.markdown`
3. 文件開頭需要包含 Front Matter：

```markdown
---
layout: post
title:  "您的文章標題"
date:   2024-01-01 12:00:00 +0800
categories: jekyll update
---

您的文章內容...
```

### 停止伺服器

在終端機中按 `Ctrl + C` 停止開發伺服器。

## 📁 專案結構

```
drago-blog.github.io/
├── _posts/              # 部落格文章目錄
├── _site/               # 建置後的靜態網站（自動生成）
├── _config.yml          # Jekyll 配置文件
├── Gemfile              # Ruby 依賴管理
├── Gemfile.lock         # 依賴版本鎖定
├── index.markdown       # 首頁
├── about.markdown       # 關於頁面
├── 404.html            # 404 錯誤頁面
└── README.md           # 專案說明文件
```

## 🌐 部署

### GitHub Pages 部署

1. 將專案推送到 GitHub
2. 在 GitHub 倉庫設定中啟用 GitHub Pages
3. 選擇 `main` 分支作為來源
4. 您的網站將自動部署到 `https://your-username.github.io/drago-blog.github.io`

### 手動部署

```bash
# 建置網站
bundle exec jekyll build

# 將 _site 目錄的內容部署到您的伺服器
```

## ⚙️ 配置

主要配置文件為 `_config.yml`，您可以在此修改：

- 網站標題和描述
- 作者資訊
- 社交媒體連結
- 主題設定
- 插件配置

**注意**: 修改 `_config.yml` 後需要重新啟動開發伺服器。

## 🎨 自訂主題

本專案使用 Minima 主題。如需自訂樣式：

1. 創建 `_sass` 目錄
2. 創建 `assets/css/style.scss` 文件
3. 在其中覆寫預設樣式

## 🤝 貢獻

歡迎提交 Issue 和 Pull Request！

1. Fork 此專案
2. 創建您的功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的變更 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 開啟一個 Pull Request

## 📝 授權

此專案採用 MIT 授權 - 詳見 [LICENSE](LICENSE) 文件。

## 🔗 相關連結

- [Jekyll 官方文檔](https://jekyllrb.com/)
- [Minima 主題](https://github.com/jekyll/minima)
- [GitHub Pages 文檔](https://docs.github.com/en/pages)
- [Markdown 語法指南](https://www.markdownguide.org/)

## 📞 聯絡方式

如有任何問題，請透過以下方式聯絡：

- 開啟 [Issue](https://github.com/your-username/drago-blog.github.io/issues)
- 電子郵件：coachsunshinelee@gmail.com

---

⭐ 如果這個專案對您有幫助，請給它一個星星！ 