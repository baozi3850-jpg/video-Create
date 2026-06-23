# Backyard Studio Bootstrap 5 切版規格

## 專案目的

本專案依照 `https://www.backyardstudioco.com/` 的 UI/UX 視覺風格進行首頁切版，使用 Bootstrap 5 作為版面架構，並以獨立自訂 CSS 檔維護客製化樣式，方便後續新增頁面與交接維護。

## 目前檔案結構

```text
WEB/
├── index.html
├── PROJECT_SPEC.md
├── bootstrap-5.3.8-dist/
│   ├── css/
│   │   └── bootstrap.min.css
│   └── js/
│       └── bootstrap.bundle.min.js
└── css/
    └── custom.css
```

## 技術架構

- HTML5
- Bootstrap 5.3.8 本地端檔案
- 自訂 CSS：`css/custom.css`
- JavaScript：使用 Bootstrap Bundle，本地端引用

## 首頁區塊順序

首頁 `index.html` 由上到下包含以下區塊：

1. 選單
   - 使用 Bootstrap `navbar`
   - 固定於頁面上方
   - 含品牌識別、主要導覽、下拉選單

2. 輪播圖
   - 使用 Bootstrap `carousel`
   - 共 5 張輪播圖
   - 含左右切換按鈕與指示點

3. 關於我們
   - 左側圖片
   - 右側文字
   - 使用 Bootstrap `row`、`col-lg-6`

4. 產品介紹
   - 共 4 個產品模組
   - 使用 Bootstrap `card`
   - 桌機版一列 4 欄，平板版一列 2 欄

5. 頁尾資訊
   - 社群連結
   - 公司資訊
   - 服務項目
   - 版權宣告

## CSS 引用規則

所有頁面應依照以下順序引用 CSS：

```html
<link href="bootstrap-5.3.8-dist/css/bootstrap.min.css" rel="stylesheet">
<link rel="stylesheet" href="css/custom.css">
```

Bootstrap 必須先載入，自訂 CSS 必須後載入，才能覆蓋 Bootstrap 預設樣式。

## JavaScript 引用規則

所有需要 Bootstrap 互動元件的頁面，應在 `</body>` 前引用：

```html
<script src="bootstrap-5.3.8-dist/js/bootstrap.bundle.min.js"></script>
```

目前使用到的 Bootstrap 互動元件：

- Navbar collapse
- Dropdown
- Carousel

## 自訂 CSS 維護規範

自訂樣式統一放在：

```text
css/custom.css
```

請不要直接修改：

```text
bootstrap-5.3.8-dist/
```

原因：

- 保留 Bootstrap 原始檔案完整性
- 方便未來升級 Bootstrap
- 避免多人維護時樣式來源混亂

## 命名原則

目前主要自訂 class：

```text
studio-nav
hero-carousel
section-kicker
section-pad
about-section
about-image
display-title
lead-copy
product-section
section-heading
product-card
site-footer
footer-brand
footer-copy
social-links
footer-title
footer-list
copyright
```

後續新增樣式時，建議：

- 優先沿用 Bootstrap class
- 需要客製化時再新增自訂 class
- 自訂 class 使用語意化命名
- 避免使用過於籠統的名稱，例如 `.box`、`.text`、`.item`

## 圖片維護規則

目前頁面仍有遠端圖片路徑，若要改成本地端圖片，建議新增：

```text
images/
```

建議命名方式：

```text
images/
├── hero-01.jpg
├── hero-02.jpg
├── hero-03.jpg
├── hero-04.jpg
├── hero-05.jpg
├── about.jpg
├── product-01.jpg
├── product-02.jpg
├── product-03.jpg
└── product-04.jpg
```

產品卡片圖片範例：

```html
<img src="images/product-01.jpg" class="card-img-top" alt="商業形象影片">
```

維護注意事項：

- 圖片檔名建議使用小寫英文與連字號
- 避免中文檔名與空白
- 圖片比例建議保持一致，產品卡片建議使用橫式圖片
- `alt` 文字需描述圖片內容，方便無障礙與 SEO

## RWD 設計

目前 `css/custom.css` 已包含 RWD 設定：

- `max-width: 991.98px`
  - 調整手機和平板選單
  - 調整輪播高度

- `max-width: 575.98px`
  - 調整手機版輪播高度
  - 頁尾版權資訊改為上下排列

後續維護時，建議沿用 Bootstrap 斷點：

```text
sm: 576px
md: 768px
lg: 992px
xl: 1200px
xxl: 1400px
```

## 新增頁面建議

新增頁面時，建議複製 `index.html` 的基本結構：

```html
<!doctype html>
<html lang="zh-Hant">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link href="bootstrap-5.3.8-dist/css/bootstrap.min.css" rel="stylesheet">
    <link rel="stylesheet" href="css/custom.css">
  </head>
  <body>
    <!-- navbar -->

    <!-- page content -->

    <!-- footer -->

    <script src="bootstrap-5.3.8-dist/js/bootstrap.bundle.min.js"></script>
  </body>
</html>
```

共用元件建議：

- 選單
- 頁尾
- 品牌識別
- 社群連結

## 交接注意事項

- Bootstrap 使用本地端檔案，不使用 CDN
- 自訂樣式集中於 `css/custom.css`
- 不建議修改 Bootstrap 原始檔
- 後續圖片若要離線使用，請統一放入 `images/`
- 若新增其他頁面，請保持 CSS 與 JS 引用路徑一致
- 若頁面放在子資料夾，需調整相對路徑，例如 `../css/custom.css`

## 待辦建議

- 將目前遠端圖片全部替換為本地 `images/` 圖片
- 補齊正式公司資訊、地址、電話與 Email
- 將社群連結替換為正式 URL
- 如需 icon，可下載 Bootstrap Icons 至本地端後引用
- 可依實際品牌需求調整 Logo、字體與色彩
