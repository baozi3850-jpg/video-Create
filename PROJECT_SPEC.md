# 夢境影像製作公司 Bootstrap 5 切版規格

## 專案目的

本專案以 Bootstrap 5 製作「夢境影像 Dream Creation Studio」品牌官網，網站定位為影像製作公司的品牌形象、作品展示與專案詢價入口。視覺採用黑色電影感、金色點綴與夢境語意元素，主要服務包含商業形象影片、音樂錄影帶、社群短影音與活動紀錄。

## 目前檔案結構

```text
WEB/
├── index.html
├── commercial.html
├── goal.html
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

## GitHub 儲存庫

目前專案遠端儲存庫：

```text
HTTPS: https://github.com/baozi3850-jpg/video-Create.git
SSH:   git@github.com:baozi3850-jpg/video-Create.git
```

## 首頁區塊順序

首頁 `index.html` 由上到下包含以下區塊：

1. 選單
   - 使用 Bootstrap `navbar`
   - 固定於頁面上方
   - 含「夢境影像製作公司」品牌識別、主要導覽、下拉選單

2. 輪播圖
   - 使用 Bootstrap `carousel`
   - 共 5 張輪播圖
   - 含左右切換按鈕與指示點

3. 關於我們
   - 左側圖片
   - 右側文字
   - 使用 Bootstrap `row`、`col-lg-6`

4. 影像製作服務
   - 共 4 個產品/服務模組
   - 使用 Bootstrap `card`
   - 桌機版一列 4 欄，平板版一列 2 欄

5. 頁尾資訊
   - 社群連結
   - 公司資訊
   - 服務項目
   - 版權宣告

## 影像作品集

`commercial.html` 為完整影像作品集頁面，分類包含商業影片、音樂錄影帶、社群短影音與活動紀錄。作品卡目前以「正式作品影片待補」標示尚未提供的真實內容；取得正式素材後，應補上影片縮圖、客戶或專案名稱、製作內容、正式影片網址及可公開的專案成果。

## 專案詢價頁

`goal.html` 已由購買完成頁改為專案詢價頁，可透過查詢參數預選服務，例如：

```text
goal.html?service=commercial
goal.html?service=music-video
goal.html?service=social-video
goal.html?service=event-record
```

目前表單只進行前端驗證，不會將資料送出裝置。正式上線前必須串接安全的表單收件服務或後端 API，並設定通知信箱、垃圾訊息防護與正式隱私權政策。

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

## 目前服務項目

首頁目前使用 4 個服務卡片，按鈕均連至專案詢價頁並帶入服務類型：

```text
商業形象影片
音樂錄影帶
社群短影音
活動紀錄
```

## GA4 追蹤

首頁服務按鈕使用 `select_content` 事件。詢價表單通過前端驗證並顯示成功狀態後，使用 `generate_lead` 事件並送出 Google Ads 轉換事件 `AW-18338774301/kPNICJ3o-NYcEJ36zahE`。每次詢價會產生唯一 `transaction_id`，並使用 `sessionStorage` 避免同一頁面工作階段重複記錄。

目前以 `form_status: demo_validated` 標示仍是展示流程；正式串接收件服務後，應將 `trackInquiryConversion()` 移至收件 API 回傳成功之後才呼叫。Google Ads 後台也應將此轉換動作命名為「詢價送出」或「潛在客戶」，避免將詢價誤解為已付款購買。

## 待辦建議

- 取得授權後，將目前遠端示意圖片替換為 `images/` 內的正式作品圖片
- 補齊正式公司資訊、電話、Email 與服務地區
- 取得正式社群帳號後再加入社群連結，避免使用空白或示範 URL
- 串接詢價表單的正式收件服務與成功頁
- 補上正式作品影片、客戶名稱與可公開成果
- 加入完整隱私權政策與個資使用說明
- 如需 icon，可下載 Bootstrap Icons 至本地端後引用
- 可依實際品牌需求調整 Logo、字體與色彩
