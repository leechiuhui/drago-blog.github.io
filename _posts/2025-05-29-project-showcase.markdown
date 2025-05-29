---
layout: post
title: "Drago Blog：個人部落格建置專案"
date: 2024-12-19 15:00:00 +0800
categories: [專案, 技術]
tags: [Jekyll, GitHub Pages, 部落格, 開源]
---

# Drago Blog 專案介紹

這是我的第一個 Jekyll 部落格專案，從零開始建置到部署的完整記錄。

## 🎯 專案目標

建立一個功能完整、設計美觀的個人部落格，用於：
- 記錄學習過程和技術筆記
- 分享專案開發經驗
- 建立個人品牌和作品集

## 🛠️ 技術棧

### 前端技術
- **Jekyll** - 靜態網站生成器
- **Liquid** - 模板語言
- **Markdown** - 內容撰寫
- **SCSS** - 樣式預處理器

### 部署與工具
- **GitHub Pages** - 免費託管
- **Git** - 版本控制
- **VS Code** - 開發環境

## ✨ 主要功能

### 已實現功能
- ✅ 響應式設計
- ✅ 文章分類系統
- ✅ 標籤雲功能
- ✅ 站內搜尋
- ✅ RSS 訂閱
- ✅ SEO 優化

### 計劃中功能
- 🔄 評論系統
- 🔄 深色模式
- 🔄 文章目錄
- 🔄 閱讀時間估算
- 🔄 相關文章推薦

## 📊 專案統計

```
總文件數：15+
程式碼行數：1000+
開發時間：3 天
部署平台：GitHub Pages
```

## 🚀 部署流程

1. **本地開發**
   ```bash
   bundle exec jekyll serve
   ```

2. **版本控制**
   ```bash
   git add .
   git commit -m "更新內容"
   git push origin main
   ```

3. **自動部署**
   - GitHub Pages 自動檢測更新
   - 約 1-5 分鐘完成部署

## 💡 開發心得

### 遇到的挑戰
1. **baseurl 配置問題**：本地和線上環境的路徑差異
2. **樣式載入問題**：CSS 資源路徑設定
3. **中文字體顯示**：跨平台字體兼容性

### 解決方案
1. 正確設定 `_config.yml` 中的 baseurl
2. 使用相對路徑和 Liquid 變數
3. 設定字體堆疊和 fallback

### 學到的技能
- Jekyll 靜態網站開發
- Liquid 模板語法
- GitHub Pages 部署
- 響應式網頁設計

## 🔗 相關連結

- **專案倉庫**：[GitHub](https://github.com/leechiuhui/drago-blog.github.io)
- **線上網站**：[Drago Blog](https://leechiuhui.github.io/drago-blog.github.io/)
- **技術文檔**：[Jekyll 官網](https://jekyllrb.com/)

## 📝 後續計劃

1. **功能擴展**：添加更多互動功能
2. **內容豐富**：定期發布高質量文章
3. **性能優化**：提升載入速度和 SEO
4. **社群建立**：與讀者互動交流

---

這個專案讓我深入了解了靜態網站的開發流程，也為未來的技術分享奠定了基礎。期待在這個平台上記錄更多的學習旅程！ 