# 夢境影像製作公司 Bootstrap 5 切版規格

## 專案目的

本專案以 Bootstrap 5 製作「夢境影像 Dream Creation Studio」品牌官網，網站定位為紀錄式品牌內容與《品牌人物誌》的品牌形象、案例展示與適配通話入口。視覺以深墨藍、暖白、低飽和金與灰綠呈現節制、可信的紀錄式內容；商業形象影片、音樂錄影帶、社群短影音與活動紀錄保留為延伸影像形式。

## 目前檔案結構

```text
WEB/
├── index.html
├── commercial.html
├── inquiry.html
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

2. 品牌主張首屏
   - 單一主張：「把看不見的努力，拍成被相信的理由。」
   - 主 CTA 為「預約 30 分鐘品牌故事適配通話」
   - 目前沿用遠端示意照片，正式品牌照片待補

3. 問題與品牌解法
   - 「被看見，不等於被理解」問題區
   - 四項原則：人物理解、證據敘事、透明管理、多平台交付

4. 招牌商品與延伸形式
   - 《品牌人物誌》為第一層招牌商品
   - 商業影片、音樂錄影帶、社群短影音、活動紀錄為延伸服務

5. 合作流程
   - 五步：適配與需求摘要、診斷與證據地圖、企劃與拍攝、紙上剪輯與審核、交付與使用建議

6. 適合對象與最終 CTA
   - 行銷／專案負責人
   - 創辦人／品牌主理人
   - 補充可能不適合的合作情境
   - 統一導向 `inquiry.html`

7. FAQ 與採購判斷
   - 適配通話適用情境
   - 腳本、時程、修改、價格因素與延伸形式說明
   - 所有承諾保留為適配後確認，不把假設價格或固定時程當成公開事實

8. 頁尾資訊
   - 社群連結
   - 品牌架構
   - 延伸影像形式
   - 版權宣告

## 影像作品集

`commercial.html` 為完整影像作品集頁面，分類包含商業影片、音樂錄影帶、社群短影音與活動紀錄。作品卡目前以「正式作品影片待補」標示尚未提供的真實內容；取得正式素材後，應補上影片縮圖、客戶或專案名稱、製作內容、正式影片網址及可公開的專案成果。

## 專案詢價頁

`inquiry.html` 為獨立專案詢價頁，可透過查詢參數預選服務，例如：

```text
inquiry.html?service=brand-profile
inquiry.html?service=diagnosis
inquiry.html?service=commercial
inquiry.html?service=music-video
inquiry.html?service=social-video
inquiry.html?service=event-record
```

適配通話表單會先詢問角色、觸發事件、服務方向、預算、使用場景、時程與決策階段，作為是否適合進一步對話的判斷資料；目前仍只做前端驗證，不會送出資料。

`goal.html` 為詢價完成與 Google Ads 轉換頁。詢價表單通過驗證後會建立唯一交易編號、將待轉換狀態暫存在 `sessionStorage`，再跳轉至完成頁。完成頁只有在網址交易編號與待轉換狀態相符時才送出轉換，避免直接瀏覽完成頁造成誤記。

目前表單只進行前端驗證，不會將資料送出裝置。正式上線前必須串接安全的表單收件服務或後端 API，並在 API 確認收件成功後才跳轉至 `goal.html`。

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
    hero-intro
    hero-intro-content
    section-kicker
    section-pad
    problem-section
    problem-list
    principle-grid
    principle-card
    display-title
    lead-copy
    product-section
    product-feature
    deliverable-list
    service-card
    section-heading
    process-section
    process-grid
    fit-section
    fit-card-muted
    faq-section
    faq-list
    final-cta
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

目前首頁仍有遠端示意圖片，正式品牌照片與案例素材確認授權後再改成本地端圖片，建議新增：

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
  - 調整首屏內容與導覽高度

- `max-width: 575.98px`
  - 調整手機版首屏與 CTA 排列
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

首頁目前以《品牌人物誌》作為招牌商品，四項形式保留為延伸服務；按鈕連至適配通話頁並帶入方向：

```text
《品牌人物誌》
品牌故事診斷
商業形象影片
音樂錄影帶
社群短影音
活動紀錄
```

## 第二階段：信任與採購內容

目前首頁已補上「適合／不適合」判斷與 FAQ，說明腳本準備、時程、修改、價格影響因素及延伸影像形式。這些內容是採購判斷基準，不代表固定報價、保證時程或結果承諾；正式範圍需經適配與工時核算確認。

## GA4 追蹤

所有主要頁面均載入 GA4 `G-04LJ9PZG1F` 與 Google Ads `AW-18338774301` 的 Google tag。首頁延伸服務按鈕使用 `select_content` 事件；首頁各主要 CTA 使用 `fit_call_click` 事件。`inquiry.html` 通過表單驗證後跳轉至 `goal.html`；完成頁使用 `generate_lead` 事件並送出 Google Ads 轉換事件 `AW-18338774301/9Lo6CIjaj9ccEJ36zahE`。每次詢問會產生唯一 `transaction_id`。

目前以 `form_status: demo_validated` 標示仍是展示流程；正式串接收件服務後，應只在收件 API 回傳成功後建立待轉換狀態並前往完成頁。Google Ads 後台也應將此轉換動作命名為「詢價送出」或「潛在客戶」，避免將詢價誤解為已付款購買。

## 待辦建議

- 取得授權後，將目前遠端示意圖片替換為 `images/` 內的正式作品圖片
- 補上首頁《品牌人物誌》的真實案例、人物照片與可公開證言
- 決定正式預約工具或安全表單收件端點，完成後才將展示流程改為正式轉換
- 補齊正式公司資訊、電話、Email 與服務地區
- 取得正式社群帳號後再確認社群連結與貼文內容
- 補上正式作品影片、客戶名稱與可公開成果
- 加入完整隱私權政策與個資使用說明
- 如需 icon，可下載 Bootstrap Icons 至本地端後引用
- 可依實際品牌需求調整 Logo、字體與色彩
