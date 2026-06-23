# AGENTS.MD

## 專案交接說明

本專案是以 Bootstrap 5 製作的靜態首頁切版，視覺風格參考 Backyard Studio 類型的黑白極簡影像工作室網站。此文件提供後續協作者、維護者或 AI agent 進行修改時的共同規範。

詳細頁面結構與技術規格請參考：

```text
PROJECT_SPEC.md
```

## 維護原則

- 優先維持目前 Bootstrap 5 架構。
- 不要直接修改 `bootstrap-5.3.8-dist/` 內的原始檔。
- 所有自訂樣式集中維護於 `css/custom.css`。
- 修改頁面結構時，請先確認是否會影響 RWD。
- 新增頁面時，請沿用目前的選單、頁尾、CSS 與 JS 引用方式。
- 若新增圖片資源，請統一放入 `images/` 資料夾。

## 主要檔案職責

```text
index.html
```

首頁主要 HTML，包含選單、輪播、關於我們、產品卡片與頁尾。

```text
css/custom.css
```

專案自訂樣式。若要調整品牌色、間距、卡片、頁尾、輪播高度或 RWD，請在此檔案修改。

```text
bootstrap-5.3.8-dist/
```

Bootstrap 5 本地端資源。此資料夾視為第三方套件，不建議修改。

```text
PROJECT_SPEC.md
```

完整交接規格文件，包含目前頁面架構、引用規則、圖片建議與待辦事項。

## 資源引用規範

CSS 引用順序需保持：

```html
<link href="bootstrap-5.3.8-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" href="css/custom.css">
```

JavaScript 請放在 `</body>` 前：

```html
<script src="bootstrap-5.3.8-dist/js/bootstrap.bundle.min.js"></script>
```

若頁面位於子資料夾，需依實際位置調整相對路徑。

## 圖片維護規範

建議圖片集中放置於：

```text
images/
```

建議命名：

```text
hero-01.jpg
hero-02.jpg
about.jpg
product-01.jpg
product-02.jpg
```

維護注意事項：

- 使用小寫英文、數字與連字號命名。
- 避免中文、空白與特殊符號檔名。
- 圖片需補上合適的 `alt` 文字。
- 若要完全離線瀏覽，請避免使用遠端圖片 URL。

## 修改前檢查

修改前請先確認：

- 是否已有相關 class 可沿用。
- 是否需要同步更新 `PROJECT_SPEC.md`。
- 是否會影響手機版導覽、輪播或卡片排列。
- 是否誤改 Bootstrap 原始檔。

## 修改後檢查

修改後建議檢查：

- 首頁是否能正常開啟。
- Navbar 手機版是否能展開。
- Dropdown 是否能正常顯示。
- Carousel 是否能正常切換。
- Card 圖片與文字是否排列正常。
- Footer 在手機版是否不重疊。

## 交接備註

本專案目前以靜態切版為主，沒有建置流程、套件管理器或後端程式。後續若導入 npm、Sass、模板引擎或前端框架，請同步更新此文件與 `PROJECT_SPEC.md`。
