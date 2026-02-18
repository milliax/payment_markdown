# 藍新金流服務平台

## 線上交易─幕前支付

## 技術串接手冊

### 標準版

文件版本號：NDNF-1.1.9

(文件為藍新科技股份有限公司版權所有)

**版本異動表**

| 文件版本號 | 修改內容 | 日期 |
|-----------|---------|------|
| NDNF-1.0.0 | 初版 | 2022/05/ |
| NDNF-1.0.1 | **4.2.1 請求參數** - 參數 BankType 移除 Taishin=台新銀行 | 2022/06/ |
| NDNF-1.0.2 | **4.2.1 請求參數** - 調整參數 CVSCOM 之訂單金額限制、新增參數 LgsType 店到店支援超商 **5. 錯誤代碼表** - 新增MPG05006/MPG05007/MPG05008/MPG **附錄1 測試區腳本** - 調整參數 CVSCOM 之測試交易注意事項說明 | 2022/07/28 |
| NDNF-1.0.3 | **4.1.1 AES256加密** - 調整內容說明 **4.2.1 請求參數** - 調整參數 WEBATM 及 TradeLimit 之說明 **4.6 電子錢包退款** - 調整Alipay/WeChat/LINE Pay之退款規則 **其他** - 新增4.1.3 Form Post / 4.1.4 AES256解密 / 4.1.5 CheckValue、新增6.常見問題 | 2022/09/21 |
| NDNF-1.0.4 | **4.3.2 回應參數** - 新增參數 TradeStatus 之狀態代碼、調整參數CloseAmt/CloseStatus/BackBalance/BackStatus/Inst/InstFirst/InstEach之型態 **6. 常見問題** - 更新 MPG 交易[NPA-F01]之常見問題 **附錄1 測試區腳本** - 更新 LINE Pay 測試說明 | 2022/12/ |
| NDNF-1.0.5 | **4.2.1 請求參數** - 調整參數ReturnURL/NotifyURL/CustomerURL/ClientBackURL/ImageUrl 之型態 | 2022/12/21 |
| NDNF-1.0.6 | **4.2.1 請求參數** - 新增LgsType支援超商：萊爾富、OK mart、調整WEBATM/VACC/TAIWANPAY單筆金額上限說明 **4.2.2 回應參數-支付完成** - 新增超商物流StoreType回傳參數：[萊爾富]、[OK mart] **4.2.3 回應參數-取號完成** - 新增超商物流StoreType回傳參數：[萊爾富]、[OK mart] **4.3.2 回應參數** - 新增超商取貨付款StoreType回傳參數：[萊爾富]、[OK mart] | 2022/12/30 |
| NDNF-1.0.7 | **4.2.1 請求參數** - 參數 BankType 移除 FirstBank=第一銀行、調整參數BankType之說明 | 2023/07/ |
| NDNF-1.0.8 | **4.APIs** - 更新範例程式 **4.2.1 請求參數** - 新增［CREDITAE 美國運通卡］ **附錄1 測試區腳本** - 新增[美國運通測試卡號] | 2023/09/28 |
| NDNF-1.0.9 | **4.2.1 請求參數** - 新增FULA **4.2.2 回應參數-支付完成** - 新增PaymentType回傳參數: [FULA]、新增參數Inst **附錄1 測試區腳本** - 新增 Fula付啦 測試說明 | 2023/11/01 |
| NDNF-1.1.0 | **4.2.2 回應參數-支付完成** - 新增收單金融機構AuthBank回傳參數：[LINEBank] **4.3.2 回應參數** - 新增收單金融機構AuthBank回傳參數：[LINEBank] | 2024/01/18 |
| NDNF-1.1.1 | **4.3.2 回應參數** - 新增支付方式PaymentType回傳參數：[FULA]、新增BNPL先買後付回傳參數 **5. 錯誤代碼表** - 新增TRA20028/1114-1133/2101 **其他** - 新增4.7 BNPL先買後付退款、新增附錄2 Fula交易狀態代碼 | 2024/03/07 |
| NDNF-1.1.2 | **4.2.1 請求參數** - 新增BITOPAY、取消參數LoginType **4.2.2 回應參數-支付完成** - 新增PaymentType回傳參數: [BITOPAY]、新增BitoPay回傳參數：[PayAmt]、[CryptoCurrency]、[CryptoAmount]、[CryptoRate] **5. 錯誤代碼表** - 新增MPG03010/MPG03011回傳參數[BITOPAY]、刪除MPG01001錯誤代碼 **附錄1 測試區腳本** - 新增BitoPay測試說明 | 2024/03/ |
| NDNF-1.1.3 | 調整第11頁［圖5 信用卡交易狀態圖］ | 2024/04/23 |
| NDNF-1.1.4 | **4.2.1 請求參數** - 新增APPLEPAY、新增ExpireTime、參數TokenTermDemand新增4=信用卡到期日與安全碼皆非必填、調整信用卡記憶卡號參數說明 **4.2.2 回應參數-支付完成** - 新增PaymentMethod回傳參數: [APPLEPAY] **4.2.3 回應參數-取號完成** - 新增ExpireTime **附錄1 測試區腳本** - 新增Apple Pay測試說明 | 2024/08/26 |
| NDNF-1.1.5 | **4.2.1 請求參數** - 新增InstFlag支援8期(限閘道商店使用) | 2024/08/28 |
| NDNF-1.1.6 | **4.2.1 請求參數** - 移除FULA參數、程式版本號欄位升為2.2版、新增訂單細項欄位參數 **4.2.2 回應參數-支付完成** - 移除Fula回傳參數: [Inst]、[PayAmt]、新增回傳發卡行資訊 **4.7 BNPL先買後付取消交易/退款[NPA-B07]** - 移除此API **5. 錯誤代碼表** - 移除1114/1115/1117-1133/2101、新增MPG01028、MPG01029、MPG **附錄1 測試區腳本** - 移除Fula付啦測試說明 **附錄2 Fula交易狀態代碼** - 移除Fula交易狀態代碼 | 2024/10/18 |
| NDNF-1.1.7 | **4.2.2 回應參數-支付完成** - 新增收單金融機構AuthBank回傳參數：[SinoPac] **4.3.2 回應參數** - 新增收單金融機構AuthBank回傳參數：[SinoPac] | 2025/1/3 |
| NDNF-1.1.8 | **4.2.1 請求參數** - 新增WalletDisplayMode **5. 錯誤代碼表** - 新增TRA | 2025/2/10 |
| NDNF-1.1.9 | **4.2.1 請求參數** - 程式版本號欄位升為2.3版、BankType新增支援KGI=凱基銀行、新增參數SourceType/SourceBankId/SourceAccountNo/TWQR/TWQR_LifeTime、移除ezPay參數、PHP程式範例更改 **4.2.2 回應參數-支付完成** - ChannelID更改型態與備註說明、PaymentMethod更改備註說明 **4.2.3 回應參數-取號完成** - 新增參數ExpireTime **4.3 單筆交易查詢** - 新增參數SourceBankId/SourceAccountNo **4.6 電子錢包退款** - 新增TWQR退款規則 **4.6.1 請求參數** - PaymentType更改備註說明 **5. 錯誤代碼表** - 新增MPG02007/MPG02008/MPG02009/MPG、TRA10031更改備註說明 **附錄1 測試區腳本** - 移除ezPay、新增TWQR | 2025/07/22 |

## 目錄

- 1. 簡介
- 2. 詞彙一覽表
- 3. 交易流程
  - 3.1 即時支付交易流程
  - 3.2 非即時支付交易流程
- 4. APIs
  - 4.1 加解密方式
    - 4.1.1 AES256加密
    - 4.1.2 SHA256
    - 4.1.3 Form Post
    - 4.1.4 AES256解密
    - 4.1.5 CheckCode
    - 4.1.6 CheckValue
  - 4.2 MPG 交易[NPA-F01]
    - 4.2.1 請求參數
    - 4.2.2 回應參數-支付完成
    - 4.2.3 回應參數-取號完成
  - 4.3 單筆交易查詢[NPA-B02]
    - 4.3.1 請求參數
    - 4.3.2 回應參數
  - 4.4 取消授權[NPA-B01]
    - 4.4.1 請求參數
    - 4.4.2 回應參數
  - 4.5 請退款/取消請退款[NPA-B031 ~ 34]
    - 4.5.1 請求參數
    - 4.5.2 回應參數
  - 4.6 電子錢包退款[NPA-B06]
    - 4.6.1 請求參數
    - 4.6.2 回應參數
- 5. 錯誤代碼表
- 6. 常見問題
- 附錄1 測試區腳本

## 1. 簡介

此份串接手冊主要針對藍新金流**線上交易幕前支付的**場域，說明**交易、單筆交易查詢、取消授權、請退款/取消請退款、電子錢包退款**之API介接規格說明。

## 2. 詞彙一覽表

| 名稱 | 說明 |
|------|------|
| 藍新金流 | 藍新金流提供金流服務給商店，並提供付款頁面給消費者進行付款 |
| 會員 | 使用藍新金流服務之會員，一個會員可以建立多間商店 |
| 商店 | 會員建立使用藍新金流服務之網路商店 |
| 消費者 | 向**商店**購買商品或服務之付款方，可能為商店之會員 |
| MPG | Multiple Payment Gateway 是藍新金流提供的RWD頁面，使用於線上交易的幕前情境供消費者進行付款 |
| 即時支付 | 包含信用卡、電子錢包、以及WebATM。消費者可直接於MPG頁面完成付款行為 |
| 非即時支付 | 包括超商代碼、超商條碼、超商取貨付款、以及ATM。消費者於MPG頁面完成取號後，需要另外至超商或是實體ATM完成付款行為 |
| 幕前 | 指商店向藍新金流發動API後，藍新金流以RWD頁面來提供交易流程 |
| 幕後 | 指商店向藍新金流發動API後，藍新金流執行後再以JSON或String方式回傳執行結果 |
| 會員專區 | 涵蓋藍新收款會員的各項商店、銷售紀錄、金流等功能。登入網址為 https://www.newebpay.com/ |
| 收單機構 | 提供商店信用卡交易清算服務之銀行 |

## 3. 交易流程

本章節介紹包含**即時支付**與**非即時支付**之交易流程。

### 3.1 即時支付交易流程

即時支付涵蓋了各項信用卡工具（也包括 Apple Pay、Google Pay、Samsung Pay）、電子錢包（TWQR、簡單付支付寶、簡單付微信支付、玉山Wallet、台灣Pay、LINE Pay、BitoPay等）、以及WebATM。

其API交易流程如下：（對應圖2. 即時支付交易流程）

1. 消費者在商店網頁完成購物，並開始結帳
2. 商店向藍新金流發動MPG交易API（參照4.2 MPG交易[NPA-F01]）
3. 藍新金流將商店網頁轉導至藍新付款頁面(MPG)，提供消費者進行付款流程（參照圖3 藍新金流MPG付款頁面）
4. 消費者於MPG選擇支付方式並輸入卡號等必要資訊
5. 藍新金流將交易資訊傳送至收單機構
6. 若為**3D**交易，付款頁面將轉導至銀行3D驗證頁面
7. 消費者於3D驗證頁面輸入OTP驗證碼
8. 若為**錢包**交易，收單機構回覆收款QR Code
9. 藍新金流在頁面上顯示QR Code
10. 消費者以錢包APP掃碼QR Code完成付款
11. 若為**WebATM**交易，將轉導至收單機構付款頁面
12. 消費者依畫面指示操作完成付款
13. 收單機構處理交易扣款
14. 收單機構將交易結果回傳至藍新金流
15. 藍新金流透過NotifyURL背景通知商店付款結果（欲接收背景通知付款結果，請在會員專區設定NotifyURL）
16. 藍新金流將頁面轉導至付款完成頁面（參照圖4. MPG付款完成頁面）

> 若付款完成後欲引導消費者回商店網頁，請至會員專區設定ReturnURL（目前玉山Wallet及台灣Pay不支援導頁）

交易成立後，即可用訂單編號來發動**單筆查詢API**（參照4.3 單筆交易查詢[NPA-B02]），取得交易(TradeStatus)、請款(CloseStatus)、以及退款狀態(BackStatus)。

針對各類交易的狀態圖請參照：圖5 信用卡交易狀態圖、圖6 錢包交易狀態圖、圖7 WebATM交易狀態圖。

### 3.2 非即時支付交易流程

非即時支付涵蓋了超商代碼、超商條碼、超商取貨付款及ATM轉帳。

其交易流程如下：（請參照圖8. 非即時支付交易流程）

1. 消費者在商店網頁完成購物，並開始結帳
2. 商店向藍新金流發動MPG交易API（參照4.2 MPG交易[NPA-F01]）
3. 藍新金流將商店網頁轉導至藍新付款頁面(MPG)，提供消費者進行付款流程（參照圖3 藍新金流MPG付款頁面）
4. 消費者於MPG選擇支付方式後送出交易
5. 藍新金流將交易資訊傳送至收單機構或超商
6. 收單機構或超商將取號資訊回傳至藍新金流
7. 藍新金流將取號資訊提供至消費者（藍新金流會將取號資訊導回商店設定的CustomerURL；若CustomerURL為空值時，則會顯示在藍新金流結果頁）
8. 消費者至超商、實體ATM、或操作網路銀行完成付款
9. 收單機構或超商將付款結果回傳至藍新金流（ATM/超商代碼為即時回傳）
10. 藍新金流透過NotifyURL背景通知商店付款結果

## 4. APIs

本章節將依序介紹發動交易前的加解密方式，以及**交易(MPG)**、**查詢(Query)**、**取消授權(Cancel)**、**請/退款(Close)**，**電子錢包退款(wallet refund)**，共計五支API介接規格，以及發動時機。

### 4.1 加解密方式

發動API時會使用到包括AES256、SHA256、CheckCode等產生方式，分述如下。

#### 4.1.1 AES256加密

**Step 0: 準備基本要素**

1. 於藍新金流平台已建立商店，並已啟用支付工具
2. 將商店之API串接金鑰(Hash Key, Hash IV)及商店代號(Merchant ID)複製至原始碼

PHP範例如下：

```php
$key = "Fs5cX1TGqYM2PpdbE14a9H83YQSQF5jn";
$iv = "C6AcmfqJILwgnhIP";
$mid = "MS127874575";
```

**Step 1: 生成請求字串**

此步驟請參考各支API說明帶入必要參數，並以http encode方式生成URL字串。

以MPG交易為範例（參考4.2.1章節）產生請求字串，PHP範例如下：

```php
$data1 = http_build_query(array(
    'MerchantID' => $mid,
    'RespondType' => 'String',
    'TimeStamp' => time(),
    'Version' => '2.0',
    'MerchantOrderNo' => 'Vanespl_ec_' . time(),
    'Amt' => '30',
    'ItemDesc' => 'test',
    'NotifyURL' => 'https://webhook.site/97c6899f-077b-4025-9948-9ee96a38dfb7',
));
```

執行完成後，`$data1` 內容如下：

```
MerchantID=MS127874575&RespondType=String&TimeStamp=1695795410&Version=2.0&MerchantOrderNo=Vanespl_ec_1695795410&Amt=30&ItemDesc=test&NotifyURL=https%3A%2F%2Fwebhook.site%2Fd4db5ad1-2278-466a-9d66-78585c0dbadb
```

**Step 2: 將請求字串加密**

為防止信用卡號等重要交易訊息洩漏，需於加密前使用商店之Hash Key及Hash IV對上述字串執行AES-256-CBC（使用PKCS7填充），並將結果轉換至十六進制。

由於PHP中的openssl_encrypt函數已提供帶有OPENSSL_RAW_DATA的PKCS7，PHP範例如下：

```php
$edata1 = bin2hex(openssl_encrypt($data1, "AES-256-CBC", $key, OPENSSL_RAW_DATA, $iv));
```

執行完成後，`$edata1` 加密後內容如下：

```
f79eac33c4f3245d58f17b544c5d38b09457a6d77e77bae6f10fcc7236fe153ccef1a80001c0746afc063a7570f80ad970d8a32c72332c9ec5547410188007876bdca2bafa52d07d31b6b183f2204d6e4feee6d245e286ab198cf95422ad5843c7696fc943cbb65979ad207607d4b5d97dac4a90ccd5e7a37adb7d7062e838be09d94e8c5dfa145c048e17feabe58c2e310792f0f50f5af32961ffb07ff6649ae1021ad558242551de5f09316e3182e198775e5d1ad5b66a70be290004de750fa85d86b0c2f087b40005d89e048be2ab6fd83f1c522494c093426a10a1f73fe4
```

#### 4.1.2 SHA256

**Step 3: 將AES加密字串產生檢查碼**

1. 於加密字串**前**加上：`HashKey=(the HashKey)&`
2. 於加密字串**後**加上：`&HashIV=(the HashIV)`

以下為PHP範例：

```php
$hashs = "HashKey=" . $key . "&" . $edata1 . "&HashIV=" . $iv;
```

執行完成後，字串 `$hashs` 內容如下：

```
HashKey=Fs5cX1TGqYM2PpdbE14a9H83YQSQF5jn&f79eac33c4f3245d58f17b544c5d38b09457a6d77e77bae6f10fcc7236fe153ccef1a80001c0746afc063a7570f80ad970d8a32c72332c9ec5547410188007876bdca2bafa52d07d31b6b183f2204d6e4feee6d245e286ab198cf95422ad5843c7696fc943cbb65979ad207607d4b5d97dac4a90ccd5e7a37adb7d7062e838be09d94e8c5dfa145c048e17feabe58c2e310792f0f50f5af32961ffb07ff6649ae1021ad558242551de5f09316e3182e198775e5d1ad5b66a70be290004de750fa85d86b0c2f087b40005d89e048be2ab6fd83f1c522494c093426a10a1f73fe4&HashIV=C6AcmfqJILwgnhIP
```

將字串使用SHA256壓碼轉換為大寫，以下為PHP範例：

```php
$hash = strtoupper(hash("sha256", $hashs));
```

執行完成後，`$hash` 內容如下：

```
84E4D9F96537E029F8450BE1E759080F9AF6995921B7F6F9AAFDDD2C36E7B287
```

#### 4.1.3 Form Post

**Step 4: 發布請求**

參考各支API之請求參數章節，將**加密後**及**不須加密的參數**以HTML Form形式組合，並發佈於對應的API URL。以下為以MPG交易API為範例的PHP/HTML Form。

上述範例中，按下"submit"送出表單後，即進入交易畫面（參照圖3）。

**Step 5: 結果**

消費者完成支付後，藍新金流透過NotifyURL回傳已加密字串給商店，範例如下：

```
Status=SUCCESS&MerchantID=MS127874575&Version=2.0&TradeInfo=ee11d1501e6dc8433c75988258f2343d11f4d0a423be672e8e02aaf373c53c2363aeffdb4992579693277359b3e449ebe644d2075fdfbc10150b1c40e7d24cb215febefdb85b16a5cde449f6b06c58a5510d31e8d34c95284d459ae4b52afc1509c2800976a5c0b99ef24cfd28a2dfc8004215a0c98a1d3c77707773c2f2132f9a9a4ce3475cb888c2ad372485971876f8e2fec0589927544c3463d30c785c2d3bd947c06c8c33cf43e131f57939e1f7e3b3d8c3f08a84f34ef1a67a08efe177f1e663ecc6bedc7f82640a1ced807b548633cfa72d060864271ec79854ee2f5a170aa902000e7c61d1269165de330fce7d10663d1668c711571776365bfdcd7ddc915dcb90d31a9f27af9b79a443ca8302e508b0dbaac817d44cfc44247ae613075dde4ac960f1bdff4173b915e4344bc4567bd32e86be7d796e6d9b9cf20476e4996e98ccc315f1ed03a34139f936797d971f2a3f90bc18f8a155a290bcbcf04f4277171c305bf554f5cba243154b30082748a81f2e5aa432ef9950cc9668cd4330ef7c37537a6dcb5e6ef01b4eca9705e4b097cf6913ee96e81d0389e5f775&TradeSha=C80876AEBAC0036268C0E240E5BFF69C0470DE9606EEE083C5C8DD64FDB3347A
```

#### 4.1.4 AES256解密

**Step 6: 將加密字串進行解密**

使用商店之API串接金鑰(Hash Key, Hash IV)進行AES256解密，請注意需要先除去PKCS7的Padding後再進行AES解密運算。PHP範例如下：

```php
<?php
$key = "Fs5cX1TGqYM2PpdbE14a9H83YQSQF5jn";
$iv = "C6AcmfqJILwgnhIP";

$data1 = "ee11d1501e6dc8433c75988258f2343d11f4d0a423be672e8e02aaf373c53c2363aeffdb4992579693277359b3e449ebe644d2075fdfbc10150b1c40e7d24cb215febefdb85b16a5cde449f6b06c58a5510d31e8d34c95284d459ae4b52afc1509c2800976a5c0b99ef24cfd28a2dfc8004215a0c98a1d3c77707773c2f2132f9a9a4ce3475cb888c2ad372485971876f8e2fec0589927544c3463d30c785c2d3bd947c06c8c33cf43e131f57939e1f7e3b3d8c3f08a84f34ef1a67a08efe177f1e663ecc6bedc7f82640a1ced807b548633cfa72d060864271ec79854ee2f5a170aa902000e7c61d1269165de330fce7d10663d1668c711571776365bfdcd7ddc915dcb90d31a9f27af9b79a443ca8302e508b0dbaac817d44cfc44247ae613075dde4ac960f1bdff4173b915e4344bc4567bd32e86be7d796e6d9b9cf20476e4996e98ccc315f1ed03a34139f936797d971f2a3f90bc18f8a155a290bcbcf04f4277171c305bf554f5cba243154b30082748a81f2e5aa432ef9950cc9668cd4330ef7c37537a6dcb5e6ef01b4eca9705e4b097cf6913ee96e81d0389e5f775";

// 去除padding副程式
function strippadding($string) {
    $slast = ord(substr($string, -1));
    $slastc = chr($slast);
    $pcheck = substr($string, -$slast);
    if (preg_match("/$slastc{" . $slast . "}/", $string)) {
        $string = substr($string, 0, strlen($string) - $slast);
        return $string;
    } else {
        return false;
    }
}

// 主程式
$edata1 = strippadding(openssl_decrypt(hex2bin($data1), "AES-256-CBC", $key, OPENSSL_RAW_DATA|OPENSSL_ZERO_PADDING, $iv));
echo "解密後資料=[" . $edata1 . "]<br>";
?>
```

解密結果如下（請參照4.2.2 回應參數-支付完成）：

```
Status=SUCCESS&Message=%E6%8E%88%E6%AC%8A%E6%88%90%E5%8A%9F&MerchantID=MS127874575&Amt=30&TradeNo=23092714215835071&MerchantOrderNo=Vanespl_ec_1695795668&RespondType=String&IP=123.51.237.115&EscrowBank=HNCB&PaymentType=CREDIT&RespondCode=00&Auth=115468&Card6No=400022&Card4No=1111&Exp=2609&AuthBank=KGI&TokenUseStatus=0&InstFirst=0&InstEach=0&Inst=0&ECI=&PayTime=2023-09-27+14%3A21%3A59&PaymentMethod=CREDIT
```

#### 4.1.5 CheckCode

為驗證結果中所得到的CheckCode之正確性，可參考下列範例生成一組CheckCode，來確認是否與結果中的CheckCode一致。

**CheckCode產生規則：**

1. 將回傳資料其中的四個欄位，分別是Amt(金額)、MerchantID(商店代號)、MerchantOrderNo(商店訂單編號)、TradeNo(藍新金流交易序號)，且照英文字母A~Z排序，若第一字母相同比較第二字母，以此類推，並用&符號串聯起來
2. 將串聯後的字串**前**加上：`HashIV=`(商店專屬加密HashIV值)
3. 將串聯後的字串**後**加上：`&HashKey=`(與商店專屬加密HashKey值)
4. 將串聯後的字串用SHA256壓碼後轉大寫

以下為PHP範例：

```php
$check_code = array(
    "MerchantID" => 'MS12345678',
    "Amt" => '10',
    "MerchantOrderNo" => 'MyCompanyOrder_1638423361',
    "TradeNo" => '21120214151152468'
);
ksort($check_code);
$check_str = http_build_query($check_code);
$CheckCode = "HashIV=" . $iv . "&$check_str&HashKey=" . $key . "";
$CheckCode = strtoupper(hash("sha256", $CheckCode));
```

#### 4.1.6 CheckValue

當商店發動**單筆交易查詢(Query)**時，需生成一組CheckValue，可參考下列範例：

**CheckValue產生規則：**

1. 將三個請求參數，分別是Amt(金額)、MerchantID(商店代號)、MerchantOrderNo(商店訂單編號)，且照英文字母A~Z排序，若第一字母相同比較第二字母，以此類推，並用&符號串聯起來
2. 將串聯後的字串**前**加上：`IV=`(商店專屬加密HashIV值)
3. 將串聯後的字串**後**加上：`&Key=`(與商店專屬加密HashKey值)
4. 將串聯後的字串用SHA256壓碼後轉大寫

以下為PHP範例：

```php
$hashs = "IV=" . $iv . "&" . $data1 . "&Key=" . $key;
$hash = strtoupper(hash("sha256", $hashs));
```

### 4.2 MPG 交易[NPA-F01]

- 測試串接網址：https://ccore.newebpay.com/MPG/mpg_gateway
- 正式串接網址：https://core.newebpay.com/MPG/mpg_gateway

#### 4.2.1 請求參數

Post參數說明：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| MerchantID | 商店代號 | V | String(15) | 藍新金流商店代號 |
| TradeInfo | 交易資料AES加密 | V | | 1.將交易資料參數（下方列表中參數）透過商店Key及IV進行AES加密 2.範例請參考4.1.1 AES256 |
| TradeSha | 交易資料SHA256加密 | V | | 1.將交易資料經過上述AES加密過的字串，透過商店Key及IV進行SHA256加密 2.範例請參考4.1.2 SHA256 |
| Version | 串接程式版本 | V | String(5) | 2.3 |
| EncryptType | 加密模式 | | Int(1) | 設定加密模式。1=加密模式AES/GCM；0或者未有此參數=原加密模式AES/CBC/PKCS7Padding |

TradeInfo內含參數欄位如下：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| MerchantID | 商店代號 | V | String(15) | 藍新金流商店代號 |
| RespondType | 回傳格式 | V | String(6) | JSON或是String |
| TimeStamp | 時間戳記 | V | String(50) | 自從Unix紀元（格林威治時間1970年1月1日00:00:00）到當前時間的秒數，若以PHP程式語言為例，即為呼叫time()函式所回傳值。例：2014-05-15 15:00:00這個時間的時間戳記為1400137200。*須確實帶入自Unix紀元到當前時間的秒數以避免交易失敗。(容許誤差值120秒) |
| Version | 串接程式版本 | V | String(5) | 2.3 |
| LangType | 語系 | | String(5) | 1.設定MPG頁面顯示的文字語系：英文版=en、繁體中文版=zh-tw、日文版=jp 2.當未提供此參數或此參數數值錯誤時，將預設為繁體中文版 |
| MerchantOrderNo | 商店訂單編號 | V | String(30) | 1.商店自訂訂單編號，限英、數字、"_"格式，例：201406010001 2.長度限制為30字元 3.同一商店中此編號不可重覆 |
| Amt | 訂單金額 | V | Int(10) | 1.純數字不含符號，例：1000 2.幣別：新台幣 |
| ItemDesc | 商品資訊 | V | String(50) | 1.限制長度為50字元 2.編碼為Utf-8格式 3.請勿使用斷行符號、單引號等特殊符號，避免無法顯示完整付款頁面 4.若使用特殊符號，系統將自動過濾 |
| TradeLimit | 交易有效時間 | | Int(3) | 1.於交易有效時間內未完成交易，則視為交易失敗 2.僅可接受數字格式 3.秒數下限為60秒，小於60秒以60秒計算 4.秒數上限為900秒，大於900秒以900秒計算 5.若未帶此參數，或是為0時，會視作為不啟用交易限制秒數 |
| ExpireDate | 繳費有效期限 | | String(10) | 1.僅適用於非即時支付 2.格式為date('Ymd')，例：20140620 3.此參數若為空值，系統預設為7天。自取號時間起算至第7天23:59:59。例：2014-06-23 14:35:51完成取號，則繳費有效期限為2014-06-29 23:59:59 4.可接受最大值為180天 |
| ExpireTime | 繳費截止時間 | | String(6) | 1.僅適用於超商代碼繳費，凱基銀行(ATM) 2.格式為date('His')，例：235959 3.此參數若為空值，系統預設為235959 4.建議最小值設定在1小時以上，避免付款人來不及於期限內付款 |
| ReturnURL | 支付完成返回商店網址 | | String(200) | 1.交易完成後，以Form Post方式導回商店頁面 2.若支付工具為玉山Wallet、台灣Pay或本欄位為空值，於交易完成後，消費者將停留在藍新金流付款或取號結果頁面 3.只接受80與443 Port |
| NotifyURL | 支付通知網址 | | String(200) | 1.以幕後方式回傳給商店相關支付結果資料；請參考4.2.2 回應參數-支付完成 2.只接受80與443 Port |
| CustomerURL | 商店取號網址 | | String(200) | 1.系統取號後以form post方式將結果導回商店指定的網址，請參考4.2.3 回應參數-取號完成 2.此參數若為空值，則會顯示取號結果在藍新金流頁面 |
| ClientBackURL | 返回商店網址 | | String(200) | 1.在藍新支付頁或藍新交易結果頁面上所呈現之返回鈕，我方將依據此參數之設定值進行設定，引導商店消費者依以此參數網址返回商店指定的頁面 2.此參數若為空值時，則無返回鈕 |
| Email | 付款人電子信箱 | | String(50) | 於交易完成或付款完成時，通知付款人使用 |
| EmailModify | 付款人電子信箱是否開放修改 | | Int(1) | 1.設定於MPG頁面，付款人電子信箱欄位是否開放讓付款人修改。1=可修改、0=不可修改 2.當未提供此參數時，將預設為可修改 |
| OrderComment | 商店備註 | | String(300) | 1.限制長度為300字 2.若有提供此參數，將會於MPG頁面呈現商店備註內容 |
| CREDIT | 信用卡一次付清啟用 | | Int(1) | 1.設定是否啟用信用卡一次付清支付方式。1=啟用、0或者未有此參數=不啟用 |
| APPLEPAY | Apple Pay啟用 | | Int(1) | 1.設定是否啟用Apple Pay支付方式。1=啟用、0或者未有此參數=不啟用 |
| ANDROIDPAY | Google Pay啟用 | | Int(1) | 1.設定是否啟用Google Pay支付方式。1=啟用、0或者未有此參數=不啟用 |
| SAMSUNGPAY | Samsung Pay啟用 | | Int(1) | 1.設定是否啟用Samsung Pay支付方式。1=啟用、0或者未有此參數=不啟用 |
| LINEPAY | LINE Pay | | Int(1) | 1.設定是否啟用LINE Pay支付方式。1=啟用、0或者未有此參數，即代表不開啟 |
| ImageUrl | LINE Pay產品圖檔連結網址 | | String(200) | 1.LINE Pay啟用時，會員(商店)視需求傳遞此參數 2.此連結的圖檔將顯示於LINE Pay付款前的產品圖片區，若無產品圖檔連結網址，會使用藍新系統預設圖檔 3.圖片建議使用84*84像素 4.檔案類型僅支援jpg或png |
| InstFlag | 信用卡分期付款啟用 | | String(18) | 1.此欄位值=1時，即代表開啟所有分期期別，且不可帶入其他期別參數 2.此欄位值為下列數值時，即代表開啟該分期期別：3=分3期、6=分6期、8=分8期(閘道商店使用)、12=分12期、18=分18期、24=分24期、30=分30期 3.同時開啟多期別時，將此參數用","(半形)分隔，例如：3,6,12 4.此欄位值=0或無值時，即代表不開啟分期 |
| CreditRed | 信用卡紅利啟用 | | Int(1) | 1.設定是否啟用信用卡紅利支付方式。1=啟用、0或者未有此參數=不啟用 |
| UNIONPAY | 信用卡銀聯卡啟用 | | Int(1) | 1.設定是否啟用銀聯卡支付方式。1=啟用、0或者未有此參數=不啟用 |
| CREDITAE | 信用卡美國運通卡啟用 | | Int(1) | 1.設定是否啟用美國運通卡支付方式。1=啟用、0或者未有此參數=不啟用 |
| WEBATM | WEBATM啟用 | | Int(1) | 1.設定是否啟用WEBATM支付方式。1=啟用、0或者未有此參數，即代表不開啟 2.當訂單金額超過49,999元或消費者使用手機裝置付款時，即使啟用WebATM，MPG支付頁仍不會顯示此支付方式 3.若只有啟用WebATM，消費者於MPG支付頁無法點選此支付方式 |
| VACC | ATM轉帳啟用 | | Int(1) | 1.設定是否啟用ATM轉帳支付方式。1=啟用、0或者未有此參數，即代表不開啟 2.當該筆訂單金額超過49,999元時，即使此參數設定為啟用，MPG付款頁面仍不會顯示此支付方式選項 |
| BankType | 金融機構 | | String(26) | 1.指定銀行對應參數值如下：BOT=台灣銀行、HNCB=華南銀行、KGI=凱基銀行(僅支援ATM轉帳) 2.若未帶值，則預設值為支援所有指定銀行 3.此為[WEBATM]與[ATM轉帳]可供付款人選擇轉帳銀行，將顯示於MPG頁上。為共用此參數值，無法個別分開指定 4.可指定1個以上的銀行，若指定1個以上，則用半形[,]分隔，例如：BOT,HNCB |
| SourceType | 指定消費者轉帳銀行代號 | | Int(1) | 1.當智慧ATM2.0「繳費帳號必填設定」功能為啟用時，此欄位必填，值需帶1或2 2.當智慧ATM2.0「繳費帳號必填設定」功能為關閉時，此欄位為選填：0或未帶=關閉、1=啟用(銀行代碼及帳戶不可修改)、2=啟用(銀行代碼及帳戶可修改)、3=啟用(凱基時會出現匯款帳號欄位，不可修改)、4=啟用(凱基時會出現匯款帳號欄位，可修改) 3.智慧ATM2.0「繳費帳號必填設定」功能：若要啟用需申請開通 |
| SourceBankId | 指定轉帳的銀行代碼 | | String(3) | SourceType帶1或3時必填。有帶值會顯示在匯款帳號欄位中的銀行代碼 |
| SourceAccountNo | 指定轉帳的銀行帳號 | | String(16) | SourceType帶1或3時必填。有帶值會顯示在匯款帳號欄位中的銀行帳號 |
| CVS | 超商代碼繳費啟用 | | Int(1) | 1.設定是否啟用超商代碼繳費支付方式。1=啟用、0或者未有此參數，即代表不開啟 2.當該筆訂單金額小於30元或超過2萬元時，即使此參數設定為啟用，MPG付款頁面仍不會顯示此支付方式選項 |
| BARCODE | 超商條碼繳費啟用 | | Int(1) | 1.設定是否啟用超商條碼繳費支付方式。1=啟用、0或者未有此參數，即代表不開啟 2.當該筆訂單金額小於20元或超過4萬元時，即使此參數設定為啟用，MPG付款頁面仍不會顯示此支付方式選項 |
| ESUNWALLET | 玉山Wallet | | Int(1) | 1.設定是否啟用玉山Wallet支付方式。1=啟用、0或者未有此參數，即代表不開啟 |
| TAIWANPAY | 台灣Pay | | Int(1) | 1.設定是否啟用台灣Pay支付方式。1=啟用、0或者未有此參數，即代表不開啟 2.當該筆訂單金額超過49,999元時，即使此參數設定為啟用，MPG付款頁面仍不會顯示此支付方式選項 |
| BITOPAY | BitoPay | | Int(1) | 1.設定是否啟用BitoPay支付方式。1=啟用、0或者未有此參數，即代表不開啟 2.當該筆訂單金額小於100元或超過49,999元時，即使此參數設定為啟用，MPG付款頁面仍不會顯示此支付方式選項 |
| CVSCOM | 物流啟用 | | Int(1) | 1.使用前，須先登入藍新金流會員專區啟用物流並設定退貨門市與取貨人相關資訊。1=啟用超商取貨不付款、2=啟用超商取貨付款、3=啟用超商取貨不付款及超商取貨付款、0或者未有此參數，即代表不開啟 2.當該筆訂單金額大於2萬元時，因金額限制關係，無法使用物流服務 |
| TWQR | TWQR | | Int(1) | 1.設定是否啟用TWQR/簡單付電子錢包支付方式。1=啟用、0或者未有此參數，即代表不開啟 |
| TWQR_LifeTime | QR Code有效秒數 | | Int(7) | 以此秒數產生TWQR到期時間，未帶則預設300秒(1天86400秒)，最高上限31天(2678400秒) |
| EZPWECHAT | 簡單付微信支付 | | Int(1) | 1.設定是否啟用簡單付微信支付支付方式。1=啟用、0或者未有此參數，即代表不開啟 |
| EZPALIPAY | 簡單付支付寶 | | Int(1) | 1.設定是否啟用簡單付支付寶支付方式。1=啟用、0或者未有此參數，即代表不開啟 |
| LgsType | 物流型態 | | String(3) | 1.帶入參數值說明：B2C＝大宗寄倉(目前僅支援7-ELEVEN)、C2C＝店到店(支援7-ELEVEN、全家、萊爾富、OK mart) 2.若商店未帶入此參數，則系統預設值說明如下：a.系統優先啟用[B2C大宗寄倉] b.若商店設定中未啟用[B2C大宗寄倉]則系統將會啟用[C2C店到店] c.若商店設定中，[B2C大宗寄倉]與[C2C店到店]皆未啟用，則支付頁面中將不會出現物流選項 |
| WalletDisplayMode | 電子支付模式 | | Int(1) | 設定是否指定電子支付工具（包含：LINE Pay、玉山Wallet、台灣Pay）的付款方式。1=固定顯示QR Code，無論用戶設備類型，始終顯示QR Code供掃描支付。0或者未有此參數，根據用戶的設備自動選擇支付方式，行動裝置跳轉至對應APP，桌面瀏覽器顯示QR Code |
| OrderDetail | 訂單細項 | | array | 1.此為備用欄位，可不輸入 2.本欄位為存放訂單細項資訊。送入資料為JSON陣列型態，所包含欄位請參考下表 |

OrderDetail所包含欄位：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| ItemName | 品名 | V | String(20) | 該品項名稱 |
| ItemAmt | 品項金額 | V | Int(10) | 1.大於0之正整數 2.全部的品項金額加總需等於訂單總金額。如金額不符將會被拒絕交易 |
| ItemType | 品項性質 | V | Int(1) | 1=一般商品、2=票券、3=儲值金 |
| ItemOrderNo | 品項編號 | V | String(20) | 輸入品項編號，同一訂單中的品項編號不得重複 |

**注意事項：**

1. 當下列所有參數CREDIT、APPLEPAY、ANDROIDPAY、SAMSUNGPAY、InstFlag、CreditRed、UNIONPAY、CREDITAE、WEBATM、VACC、CVS、BARCODE、CVSCOM、ESUNWALLET、TAIWANPAY、LINEPAY、EZPAY、EZPWECHAT、EZPALIPAY、BITOPAY皆未以API指定啟用時，則以商店設定值為準。
2. 可依下列方式來設定NotifyURL及ReturnURL：(1)API參數設定：每筆交易建立時以API參數提供。(2)商店於藍新金流平台設定：於藍新金流平台【會員中心】單元，【商店管理】目錄【商店資料設定】子目錄，於該商店詳細資料中設定API應用URL。(3)當兩種方式皆有設定時，會以API參數設定為主。
3. ReturnURL與NotifyURL均會攜帶回應參數回傳，請勿設定相同網址進而造成交易誤判。例：ReturnURL與NotifyURL設定相同網址，則該網址會接收到兩次付款完成資訊，但實際付款完成只有一次，將會影響商店出貨及帳務的正確性。

**PHP程式範例：**

```php
<?php
$key = "Fs5cX1TGqYM2PpdbE14a9H83YQSQF5jn";
$iv = "C6AcmfqJILwgnhIP";
$mid = "MS127874575";

$data1 = http_build_query(array(
    'MerchantID' => $mid,
    'TimeStamp' => time(),
    'Version' => '2.0',
    'RespondType' => 'JSON',
    'MerchantOrderNo' => "test0315001" . time(),
    'Amt' => '30',
    'VACC' => '1',
    'EZPALIPAY' => '0',
    'WEBATM' => '1',
    'CVS' => '1',
    'CREDIT' => '1',
    'NotifyURL' => 'https://webhook.site/97c6899f-077b-4025-9948-9ee96a38dfb7',
    'InstFlag' => '0',
    'ItemDesc' => 'test',
));

echo "Data=[" . $data1 . "]<br><br>";

$edata1 = bin2hex(openssl_encrypt($data1, "AES-256-CBC", $key, OPENSSL_RAW_DATA, $iv));
$hashs = "HashKey=" . $key . "&" . $edata1 . "&HashIV=" . $iv;
$hash = strtoupper(hash("sha256", $hashs));
?>
```

```html
<form method=post action="https://ccore.newebpay.com/MPG/mpg_gateway">
MID: <input name="MerchantID" value="<?=$mid?>" readonly><br>
Version: <input name="Version" value="2.0" readonly><br>
TradeInfo: <input name="TradeInfo" value="<?=$edata1?>" readonly><br>
TradeSha: <input name="TradeSha" value="<?=$hash?>" readonly><br>
<input type=submit>
</form>
```

**國民旅遊卡參數說明：**

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| NTCB | 信用卡國民旅遊卡交易註記 | | Int(1) | 1.註記此筆交易是否為國民旅遊卡交易。1=國民旅遊卡交易、0或者未有此參數=非國民旅遊卡交易 |
| NTCBLocate | 旅遊地區代號 | | String(3) | 旅遊地區代號，請參考旅遊地區代號對照表。例：如旅遊地區為台北市則此欄位為001 |
| NTCBStartDate | 國民旅遊卡起始日期 | | String(10) | 格式為：YYYY-MM-DD，例：2015-01-01 |
| NTCBEndDate | 國民旅遊卡結束日期 | | String(10) | 格式為：YYYY-MM-DD，例：2015-01-01 |

**旅遊地區代號對照表：**

| 旅遊地區代號 | 旅遊地區 | 旅遊地區代號 | 旅遊地區 |
|------------|---------|------------|---------|
| 001 | 台北市 | 016 | 台南市 |
| 002 | 基隆市 | 018 | 高雄市 |
| 003 | 新北市 | 020 | 屏東縣 |
| 004 | 宜蘭縣 | 021 | 台東縣 |
| 005 | 新竹市 | 022 | 花蓮縣 |
| 006 | 新竹縣 | 023 | 澎湖縣 |
| 007 | 桃園縣 | 024 | 金門縣 |
| 008 | 苗栗縣 | 025 | 連江縣 |
| 009 | 台中市 | 026 | 南海諸島 |
| 011 | 彰化縣 | 027 | 釣魚台列嶼 |
| 012 | 南投縣 | 028 | 屏東縣琉球鄉離島 |
| 013 | 嘉義市 | 029 | 台東縣綠島、蘭嶼 |
| 014 | 嘉義縣 | | |
| 015 | 雲林縣 | | |

**信用卡記憶卡號參數說明：**

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| TokenTerm | 付款人綁定資料 | V | String(20) | 1.可對應付款人之資料，用於綁定付款人與信用卡卡號時使用，例：會員編號、Email 2.限英、數字，「.」、「_」、「@」、「-」格式 |
| TokenTermDemand | 指定付款人信用卡快速結帳必填欄位 | | Int(1) | 可指定付款人需填寫的信用卡資訊：1=必填信用卡到期日與安全碼、2=必填信用卡到期日、3=必填安全碼、4=信用卡到期日與安全碼皆非必填。未有此參數或帶入其他無效參數，系統預設為參數1 |

**注意事項：**

1. 同一個會員中，各間商店的TokenTerm不可重複。
2. 銀聯卡交易及美國運通卡僅支援以下參數值：1=必填信用卡到期日與安全碼、3=必填安全碼。
3. 藍新金流僅保留最近一次加入記憶卡號且成功交易之卡號資料。

#### 4.2.2 回應參數-支付完成

適用交易類別：

1. 即時支付：信用卡、Apple Pay、Google Pay、Samsung Pay、WebATM、簡單付電子錢包、簡單付支付寶、簡單付微信支付、玉山Wallet、台灣Pay、LINE Pay、BitoPay
2. 非即時支付：超商代碼、超商條碼、超商取貨付款、ATM

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Status | 回傳狀態 | String(10) | 1.若交易付款成功，則回傳SUCCESS 2.若交易付款失敗，則回傳錯誤代碼。錯誤代碼請參考5.錯誤代碼表 |
| MerchantID | 商店代號 | String(20) | 商店代號 |
| TradeInfo | 交易資料AES加密 | | 1.將交易資料參數透過商店Key及IV進行AES加密 2.範例請參考4.1.1 AES256 |
| TradeSha | 交易資料SHA256加密 | | 1.將交易資料經過上述AES加密過的字串，透過商店Key及IV再進行SHA256加密 2.範例請參考4.1.2 SHA256 |
| Version | 串接程式版本 | String(5) | 串接程式版本 |
| EncryptType | 加密模式 | Int(1) | 1.若商店設定EncryptType為1，則會回傳此參數 2.若商店設定EncryptType為0或未有此參數，則不會回傳此參數 |

TradeInfo內含參數欄位如下：

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Status | 回傳狀態 | String(10) | 1.若交易付款成功，則回傳SUCCESS 2.若交易付款失敗，則回傳錯誤代碼 |
| Message | 回傳訊息 | String(50) | 文字，敘述此次交易狀態 |
| Result | 回傳參數 | | 當RespondType為JSON時，回傳參數會放至此陣列下 |

**所有支付方式共同回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| MerchantID | 商店代號 | String(15) | 藍新金流商店代號 |
| Amt | 交易金額 | Int(10) | 1.純數字不含符號，例：1000 2.幣別：新台幣 |
| TradeNo | 藍新金流交易序號 | String(20) | 藍新金流在此筆交易成功時所產生的序號 |
| MerchantOrderNo | 商店訂單編號 | String(30) | 商店自訂訂單編號 |
| PaymentType | 支付方式 | String(10) | 該筆交易之支付方式 |
| RespondType | 回傳格式 | String(10) | JSON格式 |
| PayTime | 支付完成時間 | DateTime | 1.回傳格式為：2014-06-25 16:43:49 2.當使用超商取貨服務時，本欄位的值會以空值回傳 |
| IP | 交易IP | String(15) | 付款人取號或交易時的IP |
| EscrowBank | 款項保管銀行 | String(10) | 1.該筆交易款項保管銀行 2.如商店是直接與收單機構簽約的閘道模式，當使用信用卡支付時，本欄位的值會以空值回傳 3.HNCB=華南銀行 |

**信用卡支付回傳參數（一次付清、分期、紅利、DCC、Apple Pay、Google Pay、Samsung Pay、國民旅遊卡、銀聯、AE）：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| AuthBank | 收單金融機構 | String(10) | Esun=玉山銀行、Taishin=台新銀行、CTBC=中國信託銀行、NCCC=聯合信用卡中心、CathayBK=國泰世華銀行、Citibank=花旗銀行、UBOT=聯邦銀行、SKBank=新光銀行、Fubon=富邦銀行、FirstBank=第一銀行、LINEBank=連線商業銀行、SinoPac=永豐銀行 |
| CardBank | 發卡金融機構 | String(10) | 由收單機構所回應的發卡行，如發卡行非中華民國設立之銀行，則回傳空白 |
| RespondCode | 金融機構回應碼 | String(5) | 1.由收單機構所回應的回應碼 2.若交易送至收單機構授權時已是失敗狀態，則本欄位的值會以空值回傳 |
| Auth | 授權碼 | String(6) | 1.由收單機構所回應的授權碼 2.若交易送至收單機構授權時已是失敗狀態，則本欄位的值會以空值回傳 |
| Card6No | 卡號前六碼 | String(6) | 1.信用卡卡號前六碼 2.若交易送至收單機構授權時已是失敗狀態，則本欄位的值會以空值回傳 |
| Card4No | 卡號末四碼 | String(4) | 1.信用卡卡號後四碼 2.若交易送至收單機構授權時已是失敗狀態，則本欄位的值會以空值回傳 |
| Inst | 分期-期別 | Int(10) | 信用卡分期交易期別 |
| InstFirst | 分期-首期金額 | Int(10) | 信用卡分期交易首期金額 |
| InstEach | 分期-每期金額 | Int(10) | 信用卡分期交易每期金額 |
| ECI | ECI值 | String(2) | 1.3D回傳值eci=1,2,5,6，代表為3D交易 2.若交易送至收單機構授權時已是失敗狀態，則本欄位的值會以空值回傳 |
| TokenUseStatus | 信用卡快速結帳使用狀態 | Int(1) | 0=該筆交易為非使用信用卡快速結帳功能、1=該筆交易為首次設定信用卡快速結帳功能、2=該筆交易為使用信用卡快速結帳功能、9=該筆交易為取消信用卡快速結帳功能 |
| RedAmt | 紅利折抵後實際金額 | Int(5) | 1.扣除紅利交易折抵後的實際授權金額 2.僅有使用紅利折抵交易時才會回傳此參數 |
| PaymentMethod | 交易類別 | String(15) | CREDIT=台灣發卡機構核發之信用卡、FOREIGN=國外發卡機構核發之卡、UNIONPAY=銀聯卡、APPLEPAY=ApplePay、GOOGLEPAY=GooglePay、SAMSUNGPAY=SamsungPay、DCC=動態貨幣轉換、GOOGLEPAY_FOREIGN=GooglePay(國外卡)、SAMSUNGPAY_FOREIGN=SamsungPay(國外卡)、APPLEPAY_FOREIGN=ApplePay(國外卡) |
| DCC_Amt | 外幣金額 | Float | DCC動態貨幣轉換交易才會回傳的參數。註：僅支援台新銀行一次付清之代收商店 |
| DCC_Rate | 匯率 | Float | DCC動態貨幣轉換交易才會回傳的參數 |
| DCC_Markup | 風險匯率 | Float | DCC動態貨幣轉換交易才會回傳的參數 |
| DCC_Currency | 幣別 | String(4) | DCC動態貨幣轉換交易才會回傳的參數。例如：USD、JPY、MOP |
| DCC_Currency_Code | 幣別代碼 | Int(4) | DCC動態貨幣轉換交易才會回傳的參數。例如：MOP=446 |

**WEBATM、ATM繳費回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| PayBankCode | 付款人金融機構代碼 | String(10) | 由代收款金融機構所回應的付款人金融機構代碼 |
| PayerAccount5Code | 付款人金融機構帳號末五碼 | String(5) | 1.由代收款金融機構所回應的付款人金融機構帳號末五碼 2.若收款金融機構無回覆則回傳空值 |

**超商代碼繳費回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| CodeNo | 繳費代碼 | String(30) | 繳費代碼 |
| StoreType | 繳費門市類別 | Int(1) | 1=7-11統一超商、2=全家便利商店、3=OK便利商店、4=萊爾富便利商店 |
| StoreID | 繳費門市代號 | String(10) | 繳費門市代號（全家回傳門市中文名稱） |

**超商條碼繳費回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Barcode_1 | 第一段條碼 | String(20) | 繳費條碼第一段條碼資料 |
| Barcode_2 | 第二段條碼 | String(20) | 繳費條碼第二段條碼資料 |
| Barcode_3 | 第三段條碼 | String(20) | 繳費條碼第三段條碼資料 |
| RepayTimes | 付款次數 | Int(3) | 條碼繳費付款次數 |
| PayStore | 繳費超商 | String(8) | SEVEN=7-11、FAMILY=全家、OK=OK超商、HILIFE=萊爾富 |

**超商物流回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| StoreCode | 超商門市編號 | String(10) | 取貨門市編號 |
| StoreName | 超商門市名稱 | String(15) | 取貨門市中文名稱 |
| StoreType | 超商類別名稱 | String(10) | 回傳[全家]、[7-ELEVEN]、[萊爾富]、[OK mart] |
| StoreAddr | 超商門市地址 | String(100) | 取貨門市地址 |
| TradeType | 取件交易方式 | Int(1) | 1=取貨付款、3=取貨不付款 |
| CVSCOMName | 取貨人 | String(20) | 取貨人姓名 |
| CVSCOMPhone | 取貨人手機號碼 | String(10) | 取貨人手機號碼 |
| LgsNo | 物流寄件單號 | String(20) | 即寄件代碼 |
| LgsType | 物流型態 | String(3) | 回傳B2C、C2C |

**跨境支付回傳參數（包含簡單付電子錢包、簡單付微信支付、簡單付支付寶）：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| ChannelID | 跨境通路類型 | String(15) | ALIPAY=支付寶、WECHATPAY=微信支付、ACCLINK=約定連結帳戶、CREDIT=信用卡、CVS=超商代碼、P2GEACC=簡單付電子帳戶轉帳、VACC=ATM轉帳、WEBATM=WebATM轉帳、TWQR=TWQR跨機構 |
| ChannelNo | 跨境通路交易序號 | String(32) | 為該筆交易於跨境通路的交易序號 |

**玉山Wallet回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| PayAmt | 實際付款金額 | Int(10) | 該交易實際付款的金額 |
| RedDisAmt | 紅利折抵金額 | Int(5) | 若有使用紅利則會回傳本欄資訊 |

**台灣Pay回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| PayAmt | 實際付款金額 | Int(10) | 該交易實際付款的金額 |

**BitoPay回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| PayAmt | 實際付款金額 | Int(10) | 該交易實際付款的金額 |
| CryptoCurrency | 加密貨幣代號 | String(10) | BTC=比特幣、ETH=以太幣、USDT=泰達幣 |
| CryptoAmount | 加密貨幣數量 | String(60) | 使用者支付的加密貨幣數量，例：1.123456 |
| CryptoRate | 加密貨幣匯率 | String(60) | 使用者支付的加密貨幣匯率，例：1.123456 |

#### 4.2.3 回應參數-取號完成

適用交易類別：超商代碼、超商條碼、超商取貨付款、ATM

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Status | 回傳狀態 | String(10) | 1.若交易取號成功，則回傳SUCCESS 2.若交易取號失敗，則回傳錯誤代碼 |
| MerchantID | 商店代號 | String(20) | 藍新金流商店代號 |
| TradeInfo | 交易資料AES加密 | | 1.將交易資料參數透過商店Key及IV進行AES加密 2.範例請參考4.1.1 AES256 |
| TradeSha | 交易資料SHA256加密 | | 1.將交易資料經過上述AES加密過的字串，透過商店Key及IV再進行SHA256加密 2.範例請參考4.1.2 SHA256 |
| Version | 串接程式版本 | String(5) | 串接程式版本 |

TradeInfo內含參數欄位如下：

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Status | 回傳狀態 | String(10) | 1.若取號成功，則回傳SUCCESS 2.若取號失敗，則回傳錯誤代碼 |
| Message | 回傳訊息 | String(50) | 文字，敘述此次交易狀態 |
| Result | 回傳參數 | | 當RespondType為JSON時，回傳參數會放至此陣列下 |

**ATM、超商代碼、超商條碼、超商取貨付款共同回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| MerchantID | 商店代號 | String(15) | 藍新金流商店代號 |
| Amt | 支付金額 | Int(10) | 本次交易金額 |
| TradeNo | 藍新金流交易序號 | String(20) | 藍新金流在此筆交易取號成功時所產生的序號 |
| MerchantOrderNo | 商店訂單編號 | String(30) | 1.商店自訂訂單編號 2.同一商店中此編號不可重覆 |
| PaymentType | 支付方式 | String(10) | 該筆交易之支付方式 |
| ExpireDate | 繳費截止日期 | DateTime | 回傳格式為yyyy-mm-dd。註：超商取貨付款不回傳此參數 |
| ExpireTime | 繳費截止時間 | String(6) | 回傳格式為date('His')，例：235959 |

**ATM回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| BankCode | 金融機構代碼 | String(10) | 1.若取號成功，此欄位呈現數值 2.若取號失敗，此欄位呈現空值 |
| CodeNo | 繳費代碼 | String(30) | 1.若取號成功，此欄位呈現數值 2.若取號失敗，此欄位呈現空值 |

**超商代碼回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| CodeNo | 繳費代碼 | String(30) | 1.若取號成功，此欄位呈現數值 2.若取號失敗，此欄位呈現空值 |

**超商條碼回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Barcode_1 | 第一段條碼 | String(20) | 1.若取號成功，此欄位呈現數值 2.若取號失敗，此欄位呈現空值 |
| Barcode_2 | 第二段條碼 | String(20) | 1.若取號成功，此欄位呈現數值 2.若取號失敗，此欄位呈現空值 |
| Barcode_3 | 第三段條碼 | String(20) | 1.若取號成功，此欄位呈現數值 2.若取號失敗，此欄位呈現空值 |

**超商物流回傳參數：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| StoreCode | 超商門市編號 | String(10) | 取貨門市編號 |
| StoreName | 超商門市名稱 | String(15) | 取貨門市中文名稱 |
| StoreType | 超商類別名稱 | String(10) | 回傳[全家]、[7-ELEVEN]、[萊爾富]、[OK mart] |
| StoreAddr | 超商門市地址 | String(100) | 取貨門市地址 |
| TradeType | 取件交易方式 | Int(1) | 1=取貨付款、3=取貨不付款 |
| CVSCOMName | 取貨人 | String(20) | 取貨人姓名 |
| CVSCOMPhone | 取貨人手機號碼 | String(10) | 取貨人手機號碼 |
| LgsNo | 物流寄件單號 | String(20) | 即寄件代碼 |
| LgsType | 物流型態 | String(3) | 回傳B2C、C2C |

### 4.3 單筆交易查詢[NPA-B02]

- 測試串接網址：https://ccore.newebpay.com/API/QueryTradeInfo
- 正式串接網址：https://core.newebpay.com/API/QueryTradeInfo

#### 4.3.1 請求參數

Post參數說明：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| MerchantID | 商店代號 | V | String(15) | 藍新金流商店代號。1.若要用複合式商店代號(MS5開頭)，則[Gateway]參數為必填 2.若沒有帶[Gateway]，則查詢一般商店代號 |
| Version | 串接程式版本 | V | String(5) | 1.3 |
| RespondType | 回傳格式 | V | String(6) | JSON或是String |
| CheckValue | 檢查碼 | V | String(255) | 請參考4.1.6 CheckValue |
| TimeStamp | 時間戳記 | V | String(50) | 自從Unix紀元到當前時間的秒數。*須確實帶入(容許誤差值120秒) |
| MerchantOrderNo | 商店訂單編號 | V | String(30) | 商店自訂訂單編號 |
| Amt | 訂單金額 | V | Int(10) | 此次交易的總金額，例：1000 |
| Gateway | 資料來源 | + | String(10) | 預設為空值。1.若為複合式商店(MS5開頭)，此欄位為必填 2.複合式商店查詢請固定填入：Composite 3.若沒有帶[Gateway]或是帶入其他參數值，則查詢一般商店代號 |

#### 4.3.2 回應參數

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Status | 回傳狀態 | String(10) | 1.若查詢成功則回傳SUCCESS 2.若查詢失敗則回傳錯誤代碼 |
| Message | 回傳訊息 | String(30) | 文字，敘述此次交易查詢的狀態 |
| Result | 回傳內容 | | 若查詢成功，該筆交易詳細資訊會放到此欄位 |

Result內含參數欄位如下：

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| MerchantID | 商店代號 | String(15) | 藍新金流商店代號 |
| Amt | 交易金額 | Int(10) | 此筆訂單之交易金額 |
| TradeNo | 藍新金流交易序號 | String(20) | 藍新金流交易序號 |
| MerchantOrderNo | 商店訂單編號 | String(30) | 商店訂單編號 |
| TradeStatus | 支付狀態 | String(1) | 0=未付款、1=付款成功、2=付款失敗、3=取消付款、6=退款 |
| PaymentType | 支付方式 | String(10) | CREDIT=信用卡付款、VACC=銀行ATM轉帳付款、WEBATM=網路銀行轉帳付款、BARCODE=超商條碼繳費、CVS=超商代碼繳費、LINEPAY=LINE Pay付款、ESUNWALLET=玉山Wallet、TAIWANPAY=台灣Pay、CVSCOM=超商取貨付款、FULA=Fula付啦 |
| CreateTime | 交易建立時間 | DateTime | 回傳格式為：2014-06-25 16:43:49 |
| PayTime | 支付完成時間 | DateTime | 回傳格式為：2014-06-25 16:43:49 |
| CheckCode | 檢核碼 | Hash | 請參考4.1.5 CheckCode |
| FundTime | 預計撥款日 | Date | 回傳格式為：2014-06-25 |
| ShopMerchantID | 實際交易商店代號 | String(15) | *此參數限複合式商店的交易回傳使用 |

**註1. 信用卡專屬欄位：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| RespondCode | 金融機構回應碼 | String(10) | 由金融機構所回應的回應碼 |
| Auth | 授權碼 | String(10) | 由金融機構所回應的授權碼 |
| ECI | ECI | String(1) | 1.3D回傳值eci=1,2,5,6，代表為3D交易 2.若授權時已是失敗狀態，則回傳空值 |
| CloseAmt | 請款金額 | String(10) | 此筆交易設定的請款金額 |
| CloseStatus | 請款狀態 | String(1) | 0=未請款、1=等待提送請款至收單機構、2=請款處理中、3=請款完成 |
| BackBalance | 可退款餘額 | String(10) | 1.若此筆交易未發動退款，回傳值為可退款金額 2.若此筆交易已發動退款，回傳值為可退款餘額 |
| BackStatus | 退款狀態 | String(1) | 0=未退款、1=等待提送退款至收單機構、2=退款處理中、3=退款完成 |
| RespondMsg | 授權結果訊息 | String(50) | 文字，銀行回覆此次信用卡授權結果狀態 |
| Inst | 分期-期別 | String(3) | 信用卡分期交易期別 |
| InstFirst | 分期-首期金額 | String(10) | 信用卡分期交易首期金額 |
| InstEach | 分期-每期金額 | String(10) | 信用卡分期交易每期金額 |
| PaymentMethod | 交易類別 | String(15) | CREDIT=台灣發卡機構核發之信用卡、FOREIGN=國外發卡機構核發之卡、NTCB=國民旅遊卡、UNIONPAY=銀聯卡、APPLEPAY=ApplePay、GOOGLEPAY=GooglePay、SAMSUNGPAY=SamsungPay |
| Card6No | 信用卡前6碼 | String(6) | 信用卡卡號前六碼 |
| Card4No | 信用卡後4碼 | String(4) | 信用卡卡號後四碼 |
| AuthBank | 收單金融機構 | String(10) | Esun=玉山銀行、Taishin=台新銀行、CTBC=中國信託銀行、NCCC=聯合信用卡中心、CathayBK=國泰世華銀行、Citibank=花旗銀行、UBOT=聯邦銀行、SKBank=新光銀行、Fubon=富邦銀行、FirstBank=第一銀行、LINEBank=連線商業銀行、SinoPac=永豐銀行 |

**註2. 超商代碼、超商條碼、超商取貨付款、LINE Pay、ATM、WebATM專屬欄位：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| PayInfo | 付款資訊 | String(50) | 1.超商代碼時為繳款代碼 2.條碼時為三段條碼用逗號組合 3.ATM轉帳時為金融機構的轉帳帳號，例：(031)1234567890 |
| ExpireDate | 繳費有效期限 | Datetime | 回傳格式為yyyy-mm-dd hh:mm:ss |
| SourceBankId | 指定轉帳的銀行代碼 | String(3) | 只有智慧ATM2.0會有的參數 |
| SourceAccountNo | 指定轉帳的銀行帳號 | String(16) | 只有智慧ATM2.0會有的參數 |
| OrderStatus | 交易狀態 | Int(1) | 0=未付款、1=已付款、2=訂單失敗、3=訂單取消、6=已退款、9=付款中，待銀行確認。串接程式版本需為1.3版（以上）才會回傳此欄位 |

**註3. 超商取貨付款專屬欄位：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| StoreType | 超商類別名稱 | String(10) | 回傳[全家][統一][萊爾富][OK mart] |
| StoreCode | 超商門市編號 | String(10) | 取貨門市編號 |
| StoreName | 超商門市名稱 | String(15) | 取貨門市中文名稱 |
| LgsNo | 物流訂單編號 | String(20) | 寄件代碼 |
| LgsType | 物流型態 | String(3) | B2C=大宗寄倉、C2C=店到店 |

**註4. 電子錢包專屬欄位：**

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| RespondCode | 金融機構回應碼 | String(10) | 由金融機構所回應的回應碼 |
| CloseAmt | 請款金額 | Int(10) | 此筆交易設定的請款金額 |
| CloseStatus | 請款狀態 | Int(1) | 0=未請款、1=請款申請中、2=請款處理中、3=請款完成、4=請款失敗 |
| BackBalance | 可退款餘額 | Int(10) | 1.若此筆交易未發動退款，回傳值為可退款金額 2.若此筆交易已發動退款，回傳值為可退款餘額 3.目前不支援LINE Pay |
| BackStatus | 退款狀態 | Int(1) | 0=未退款、1=退款申請中、2=退款處理中、3=退款完成、4=退款失敗 |
| RespondMsg | 授權結果訊息 | String(50) | 文字，銀行回覆此次電子錢包授權結果狀態 |
| PaymentMethod | 交易類別 | String(15) | LINEPAY=LINE Pay付款、ESUNWALLET=玉山Wallet、TAIWANPAY=台灣Pay |
| AuthBank | 收單金融機構 | String(10) | Linepay=LINE Pay、Esun=玉山銀行 |

### 4.4 取消授權[NPA-B01]

- 測試串接網址：https://ccore.newebpay.com/API/CreditCard/Cancel
- 正式串接網址：https://core.newebpay.com/API/CreditCard/Cancel

#### 4.4.1 請求參數

Post參數說明：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| MerchantID_ | 商店代號 | V | String(10) | 藍新金流商店代號 |
| PostData_ | 加密資料 | V | text | 請參考4.1.1 AES256 |

PostData_內含參數欄位說明：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| RespondType | 回傳格式 | V | String(5) | String或是JSON |
| Version | 串接程式版本 | V | String(5) | 1.0 |
| Amt | 取消授權金額 | V | Int(10) | 純數字不含符號，需與授權金額相同 |
| MerchantOrderNo | 商店訂單編號 | + | String(30) | 與藍新金流交易序號二擇一填入 |
| TradeNo | 藍新金流交易序號 | + | String(17) | 與商店訂單編號二擇一填入 |
| IndexType | 單號類別 | V | Int(1) | 只限定填數字1或2。1=使用商店訂單編號、2=使用藍新金流交易單號 |
| TimeStamp | 時間戳記 | V | String(30) | 自從Unix紀元到當前時間的秒數。*須確實帶入(容許誤差值120秒) |

#### 4.4.2 回應參數

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Status | 回傳狀態 | String(10) | 1.若取消授權程序成功，則回傳SUCCESS 2.若此筆交易取消授權需由金融機構批次處理，則回傳代碼：TRA20001 3.若失敗則回傳錯誤代碼 |
| Message | 回傳訊息 | String(30) | 文字，敘述此次取消授權狀態 |
| Result | 回傳資料 | Array | 內容格式為陣列 |

Result欄位內含參數如下：

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| MerchantID | 商店代號 | String(15) | 商店代號 |
| TradeNo | 藍新金流交易序號 | String(20) | 藍新金流交易序號 |
| Amt | 交易金額 | Int(15) | 本次交易金額 |
| MerchantOrderNo | 商店訂單編號 | String(30) | 商店訂單編號 |
| CheckCode | 檢核碼 | Hash | 請參考4.1.5 CheckCode |

### 4.5 請退款/取消請退款[NPA-B031 ~ 34]

- 測試串接網址：https://ccore.newebpay.com/API/CreditCard/Close
- 正式串接網址：https://core.newebpay.com/API/CreditCard/Close

#### 4.5.1 請求參數

對應圖5信用卡交易狀態圖，此API共具有下列功能：信用卡**請款**(功能編號B031)、信用卡**退款**(功能編號B032)、信用卡**取消請款**(功能編號B033)、信用卡**取消退款**(功能編號B034)

Post參數說明：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| MerchantID_ | 商店代號 | V | String(15) | 藍新金流商店代號 |
| PostData_ | 加密資料 | V | text | 請參考4.1.1 AES256 |

PostData_欄位內含參數說明：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| RespondType | 回傳格式 | V | String(5) | String或是JSON |
| Version | 串接程式版本 | V | String(5) | 1.1 |
| Amt | 請退款金額 | V | Int(10) | 1.純數字不含符號 2.一次付清(含三大Pay/國外卡)：可整筆及部分金額請款及退款 3.分期付款及紅利折抵：僅可整筆金額請款及退款 4.銀聯卡：僅可整筆金額請款，可整筆及部分金額退款 |
| MerchantOrderNo | 商店訂單編號 | V | String(30) | 1.同一商店中此編號不可重覆 2.只接受英文或數字與底線 |
| TimeStamp | 時間戳記 | V | String(30) | 自從Unix紀元到當前時間的秒數。*須確實帶入(容許誤差值120秒) |
| IndexType | 選用單號類別 | V | Int(1) | 1.只能填數字1或2：1=選用商店訂單編號、2=選用藍新金流交易序號 2.當選用其中一種單號類別時，該種單號不可空白 |
| TradeNo | 藍新金流交易序號 | V | String(20) | 藍新金流平台交易序號 |
| CloseType | 請款或退款 | V | Int(1) | 請款B031/取消請款B033時請填1、退款B032/取消退款B034時請填2 |
| Cancel | 取消請款或退款 | | Int(1) | 配合CloseType欄位，欲發動取消請款(B033)或取消退款(B034)時此欄請填1 |

#### 4.5.2 回應參數

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Status | 回傳狀態 | String(10) | 1.若請退款成功則回傳SUCCESS 2.若失敗則回傳錯誤代碼 |
| Message | 回傳訊息 | String(30) | 文字，敘述此次請退款訊息 |
| Result | 回傳資料 | JSON | JSON |

Result欄位內含參數說明：

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| MerchantID | 商店代號 | String(15) | 商店代號 |
| Amt | 請退款金額 | Int(10) | 本次交易請退款金額 |
| TradeNo | 藍新金流交易序號 | String(20) | 藍新金流平台交易序號 |
| MerchantOrderNo | 商店訂單編號 | String(30) | 商店訂單編號 |

### 4.6 電子錢包退款[NPA-B06]

各項電子錢包退款規則如下：

**玉山Wallet：**

1. 交易完成10分鐘後得以發動退款
2. 退款期限為交易完成後日曆日89天內，提出申請
3. 商店於00:00:00~23:59:59發動的退款，玉山銀行將於次日00:00:00進行前一日之交易退款清算作業
4. 支援多次部分退款
5. 退款金額將依據商店之撥款天期，於會員餘額扣除該筆退款金額，退款時所扣除之金額不再另含手續費

**台灣Pay：**

1. 交易完成10分鐘得以發動退款
2. 發動退款時，商店當日之銷售金額需大於等於退款金額，方可執行退款
3. 退款期限為交易完成後日曆日29天內，提出申請
4. 上游銀行每日00:00:00進行前一日之交易請退款作業
5. 僅提供全額退款
6. 退款金額將依據商店之撥款天期扣除，退款時所扣除之金額不再另含手續費

**LINE Pay：**

1. 依據LINE PAY政策規定，退款在交易日起60天內進行退款，支援多次部分退款

**ezPay/Alipay/WeChat：**

1. 依據ezPay政策規定，退款在交易日起89天內進行退款，支援多次部分退款

**TWQR：**

1. 不限退款次數
2. 退款有效期限為請款日起算89個日曆日（款項認列時間以收單機構為準）
3. 退款金額必須小於等於交易金額
4. 款項優先退款至買家的儲值帳戶，若儲值帳戶額度超過限額，將會退回至買家設定的退款金融機構帳戶
5. ［退款］一經發動，系統立即執行退款作業，無法取消退款作業

#### 4.6.1 請求參數

- 測試串接網址：https://ccore.newebpay.com/API/EWallet/refund
- 正式串接網址：https://core.newebpay.com/API/EWallet/refund

Post參數說明：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| UID_ | 商店代號 | V | String(15) | 藍新金流商店代號 |
| Version_ | 串接程式版本 | V | String(5) | 1.1 |
| EncryptData_ | 加密資料 | V | text | 請參考4.6電子錢包退款 |
| RespondType_ | 回傳格式 | V | String(15) | JSON |
| HashData_ | 雜湊資料 | V | Text | 請參考4.6電子錢包退款 |

EncryptData_內含參數說明：

| 參數名稱 | 參數中文名稱 | 必填 | 型態 | 備註 |
|----------|------------|------|------|------|
| MerchantOrderNo | 商店訂單編號 | V | String(30) | 1.同一商店中此編號不可重覆 2.只接受英文或數字與底線 |
| Amount | 退款金額 | V | Int(10) | 1.此筆訂單欲退款的交易金額 2.純數字不含符號 3.退款金額需小於或等於訂單完成金額 4.台灣Pay退款金額須等於訂單金額 |
| TimeStamp | 時間戳記 | V | String(50) | 自從Unix紀元到當前時間的秒數。*須確實帶入(容許誤差值120秒) |
| PaymentType | 付款方式 | V | String | 玉山Wallet=ESUNWALLET、LINE Pay=LINEPAY、台灣Pay=TAIWANPAY、TWQR=TWQR、Alipay支付寶=EZPALIPAY、WeChat微信=EZPWECHAT |

#### 4.6.2 回應參數

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| Status | 回傳狀態 | String(10) | 1.若退款成功則回傳1000 2.若失敗則回傳錯誤代碼 3.錯誤代碼請參考5.錯誤代碼表 |
| Message | 回傳訊息 | String(30) | 文字，敘述此次退款訊息 |
| EncryptData | 加密資料 | Text | 請參考4.6電子錢包退款 |
| HashData | 雜湊資料 | Text | 請參考4.6電子錢包退款 |
| UID | 商店代號 | String(15) | 藍新金流商店代號 |
| Version | 串接程式版本 | String(5) | 1.0 |

EncryptData內含參數說明：

| 參數名稱 | 參數中文名稱 | 型態 | 備註 |
|----------|------------|------|------|
| TradeNo | 藍新金流交易序號 | String(20) | 藍新金流平台交易序號 |
| BankMessage | 銀行回傳訊息 | String(30) | 文字，敘述此次退款訊息 |
| BankCode | 銀行回傳代碼 | String(10) | 文字，此次退款訊息的銀行代碼 |
| MerchantOrderNo | 商店訂單編號 | String(30) | 退款的商店訂單編號 |
| RefundAmount | 退款金額 | Int(10) | 本次交易退款金額 |
| RefundDate | 退款日期 | String(19) | 執行退款日期，回傳格式：YYYY-MM-DD HH24:MI:SS，例：2021-12-09 14:29:55 |

## 5. 錯誤代碼表

| 錯誤代碼 | 錯誤原因 | 備註 |
|---------|---------|------|
| MPG01002 | 時間戳記不可空白 | TimeStamp |
| MPG01005 | TokenTerm不可空白/設定錯誤 | TokenTerm |
| MPG01008 | 分期參數設定錯誤 | InstFlag |
| MPG01009 | 商店代號不可空白 | MerchantID |
| MPG01010 | 程式版本設定錯誤 | MPG |
| MPG01011 | 回傳規格設定錯誤 | RespondType |
| MPG01012 | 商店訂單編號不可空白/設定錯誤 | MerchantOrderNo：限英數字、底線，長度30字 |
| MPG01013 | 付款人電子信箱設定錯誤 | Email |
| MPG01014 | 網址設定錯誤 | ReturnURL、NotifyURL、CustomerURL、ClientBackURL |
| MPG01015 | 訂單金額不可空白/設定錯誤、此筆交易超過商店單筆金額限制，請與商店連繫 | Amt |
| MPG01016 | 檢查碼不可空白 | CheckValue |
| MPG01017 | 商品資訊不可空白 | ItemDesc |
| MPG01018 | 繳費有效期限設定錯誤 | ExpireDate |
| MPG01023 | 交易加密資料不可空白 | TradeInfo |
| MPG01024 | 交易加密SHA資料不可空白 | TradeSha |
| MPG01025 | 金融機構格式錯誤 | 僅接受大小寫英文&半形逗號，參數大小寫有區分 |
| MPG01026 | 金融機構格式錯誤，不接受XXX參數 | 帶入的銀行有誤，請勿帶入不支援之銀行 |
| MPG01027 | 一銀維護中，請選擇其他金融機構 | 該時段為第一銀行的維護時間，請指定其他銀行 |
| MPG01028 | 訂單細項格式錯誤 | |
| MPG01029 | 訂單金額與訂單細項總金額不相符 | |
| MPG01030 | 訂單細項品項編號不可重複 | |
| MPG02001 | 檢查碼錯誤 | CheckValue |
| MPG02002 | 查無商店開啟任何金流服務 | |
| MPG02003 | 支付方式未啟用，請洽客服中心 | |
| MPG02004 | 匯率時間戳記不存在，請確認／已過匯率鎖定時限，請重新交易／送出後檢查，交易失敗，頁面超過180秒 | |
| MPG02005 | 驗證資料錯誤(來源不合法) | |
| MPG02006 | 信用卡收單機構系統發生異常，請洽客服中心 | |
| MPG02007 | 本商店強制指定需檢核轉出行，請先啟用智慧ATM2.0服務 | 若「智慧ATM2.0繳費帳號必填設定」為啟用狀態，但對應支付工具未啟用，則無法操作 |
| MPG02008 | SourceType參數錯誤，本商店強制指定需檢核轉出行 | 若「智慧ATM2.0繳費帳號必填設定」為啟用狀態，且SourceType值非2，則會觸發錯誤 |
| MPG02009 | 不可修改銀行代號與帳號時，須提供指定轉帳的銀行代號與帳號 | 當SourceType為2，若未帶入銀行帳號參數（SourceBankId、SourceAccountNo），則會提示錯誤 |
| MPG02010 | 此版本不支援，請升級至v2.3 | |
| MPG03001 | FormPost加密失敗 | |
| MPG03002 | 拒絕交易 | IP |
| MPG03003 | IP交易次數限制 | N分鐘內不可交易達M次 |
| MPG03004 | 商店狀態已被暫停或是關閉，無法進行交易 | |
| MPG03005 | 回傳參數資料不存在/解密失敗 | |
| MPG03006 | 回傳參數資料不存在/解密失敗 | |
| MPG03007 | 該筆訂單交易資訊不存在，請重新交易／(物流服務)查無此商店代號 | TradeInfo裡的MerchantID參數與回傳MerchantID參數不一致 |
| MPG03008 | 已存在相同的商店訂單編號 | |
| MPG03009 | 交易失敗／交易資料SHA256檢查不符合／交易資料TradeInfo解密失敗／EncryptType參數值錯誤／銀行回覆此筆交易授權失敗原因 | |
| MPG03010 | 驗證資料不存在或錯誤 | 玉山Wallet、台灣Pay及BitoPay的錯誤代碼 |
| MPG03011 | 訂單資料已不存在，請重新交易 | 玉山Wallet、台灣Pay及BitoPay的錯誤代碼 |
| MPG05001 | 未有信用卡驗證資料／信用卡驗證資料解密失敗 | |
| MPG05002 | 信用卡卡號長度不足／未有商店代號／本商店不支援此信用卡付款，請改用其它發卡行所核發之信用卡 | |
| MPG05003 | 此信用卡不支援一次付清／分期付款／紅利付款，請改用其他支付方式 | |
| MPG05004 | 發卡行暫時無法提供信用卡分期付款服務 | |
| MPG05005 | 警示交易 | |
| MPG05006 | 物流設定參數[LgsType]錯誤 | 限輸入C2C或B2C |
| MPG05007 | 請開啟其他支付方式，才能使用超商取貨不付款服務 | |
| MPG05008 | 因金額限制關係，無法使用物流服務 | 訂單金額需小於20,000元 |
| MPG05009 | 超商取貨服務未啟用[服務型態]請洽客服中心 | 服務型態：取貨付款、取貨不付款 |
| ACC10005 | 會員已被暫時停權/永久停權，請洽藍新金流客服中心查詢 | |
| MEM40008 | 必填欄位資料不可空白 | 會提示空白欄位 |
| MEM40012 | 必填欄位資料傳遞錯誤 | PostData_空白 |
| MEM40013 | 必填欄位資料不齊全 | 會提示空白欄位 |
| MEM40014 | 傳送時間錯誤 | |
| NOR1001 | 連線異常 | |
| TRA10001 | 商店資料取得失敗 | |
| TRA10003 | 金額必須為數字 | |
| TRA10008 | 資料加密錯誤 | PostData_解密失敗 |
| TRA10009 | 商店代號不可空白 | |
| TRA10012 | 商店代號停用 | |
| TRA10013 | 商店信用卡資格停用 | |
| TRA10015 | 網路連線失敗 | |
| TRA10018 | 資料不足 | |
| TRA10021 | 查無該筆交易或該筆交易不為信用卡交易 | |
| TRA10026 | 此訂單非授權成功狀態，不可請款 | |
| TRA10027 | 此訂單已申請過請款，不可重覆請款 | |
| TRA10028 | 請退款金額超過授權金額，請確認 | |
| TRA10029 | 請款超過授權日N天，已不得請(退)款 | |
| TRA10030 | 請款/退款資料新增失敗／模擬信用卡請款失敗 | |
| TRA10031 | 銀聯卡交易只接受全額請款 | |
| TRA10032 | 單號類型只能為數字1或2 | IndexType：數字1為商店訂單編號、數字2為交易序號 |
| TRA10033 | 選擇使用商店自訂單號不可空白 | |
| TRA10035 | 該交易非授權成功或已請款完成狀態，請確認 | |
| TRA10036 | RespondType欄位資料格式錯誤／已超過剩餘可退款金額，請確認 | |
| TRA10037 | 商家自訂單號錯誤，只允許英數字及_符號 | |
| TRA10038 | 選擇使用系統單號格式錯誤 | |
| TRA10039 | 退款金額已超過請款金額，請確認 | |
| TRA10041 | 網址格式錯誤 | |
| TRA10045 | 該筆交易正在退款中或退款失敗 | |
| TRA10046 | 該筆交易撥款狀態異常，無法執行退款 | |
| TRA10047 | 該交易不為授權成功狀態，不可放棄授權／該筆交易尚未發動撥款，無法執行退款 | |
| TRA10048 | 該交易正在請款狀態 | |
| TRA10049 | 該交易正在退款狀態 | |
| TRA10050 | 金額不符 | |
| TRA10051 | 取消授權失敗 | |
| TRA10054 | 檢查碼CheckValue有錯誤 | |
| TRA10058 | 動態貨幣轉換交易只接受全額請款 | |
| TRA10070 | 銀聯卡交易無需請款 | |
| TRA10071 | 因查無交易資料次數已達上限，已鎖定交易查詢功能，請待四小時解鎖 | |
| TRA10077 | 只能退未撥金額 | |
| TRA10094 | 資料取消失敗 | |
| TRA10095 | 此筆交易已過關帳時間，不可取消 | |
| TRA10678 | 銀聯卡退款失敗 | |
| TRA10675 | 紅利交易只接受全額請退款 | |
| TRA10702 | 因達到執行請退款筆數上限，您的商店暫時無法使用本功能，請待1小時後解鎖 | |
| TRA11002 | 因失敗過多您的商店暫時無法使用本功能，請待4小時解鎖 | |
| TRA20001 | 金融機構取消授權批次處理中 | 此交易取消授權，需由金融機構批次處理 |
| TRA20002 | 查無交易資料 | |
| TRA20004 | 商店訂單編號重覆 | |
| TRA20011 | 該筆交易已請款 | |
| TRA20027 | 此訂單已申請過退款，退款中 | |
| TRA20028 | 可退款金額不足 | 請查看常見問題 https://www.newebpay.com/website/Page/content/faq |
| TRA40014 | TimeStamp欄位錯誤 | |
| 1101 | 退款失敗 | |
| 1102 | 查無商店 | |
| 1103 | 查無訂單資料 | |
| 1104 | 訂單狀態不為可退款狀態 | |
| 1105 | 可退金額不足 | |
| 1106 | 錢包類型不符 | |
| 1107 | 尚未請款 | |
| 1108 | 僅支援全額退款 | |
| 1109 | 退款交易申請中，請稍後 | |
| 1110 | 商店支付方式未啟用 | |
| 1111 | 查詢商店閘道設定，查無資料 | |
| 1116 | 可退款金額不足 | 請查看常見問題 https://www.newebpay.com/website/Page/content/faq |
| 2100 | 最低金額為1 | The Amount minimum is 1 |
| 4101 | EncryptData_不可為空白 | |
| 4102 | HashData_不可為空白 | |
| 4103 | HashData_資料檢查不符合 | |
| 4104 | 加密資料有誤，請確認Hash_Key與Hash_IV是否正確 | |
| 4105 | TimeStamp為空 | |
| 4106 | UID_不可為空白 | |
| 9000 | 網路連線失敗 | |

---

## 6. 常見問題

### MPG交易 [NPA-F01]

**Q: 出現「MPG01002 時間戳記不可空白」錯誤訊息之原因？**

A1: 串接版本建議升版至 2.0

A2: 請檢查帶入之參數名稱、格式、大小寫是否與文件上一致

A3: 請檢查串接 API 網址是否混淆正式/測試區

**Q: 出現「MPG02004 頁面已逾時失效，請重新確認」錯誤訊息之原因？**

A1: 產生 Timestamp 後，請在 120 秒內發動 API

A2: 請檢查帶入之參數名稱或規則是否與文件上一致，或是參數加解密是否正確

A3: 請檢查 EncryptType 參數值，若用 AES GCM 方式加密，參數請帶 `1`，若用 AES256 方式加密，參數請帶 `0`

**Q: 出現「MPG02005 驗證資料錯誤(來源不合法)」錯誤訊息之原因？**

A: 依據資訊安全規範，禁用以 iframe 或 proxy 或幕後 Http Post 方式等使用 MPG 支付頁（包含產生及 submit），請以 HTML Form Post（前景方式）進入 MPG 支付頁

**Q: 常常收不到藍新金流回傳之交易結果（Notify）？**

A1: 請檢查發動 API 時是否有帶入 NotifyURL 參數

A2: 請確認是否有收到藍新金流所寄發的「Notify 觸發失敗通知信」，信件上有說明觸發失敗的原因

A3: 藍新金流只認定 Http = 200 才視為 Notify 成功，且有 Retry 機制；若 Retry 三次皆無收到 Http = 200，則 Notify 失敗。針對此情況，請檢查網站防火牆設定

A4: 非即時支付之交易，須等繳費且銀行銷帳完成後，藍新金流才會回傳 Notify

**Q: 測試區測試 WebATM 時，出現「送出後檢查，WebATM 銀行別錯誤」錯誤訊息之原因？**

A: 測試區 WebATM 模擬交易僅支援華南銀行，第一銀行及台灣銀行不支援

### 單筆交易查詢 [NPA-B02]

**Q: 錯誤訊息「TRA10021 查無該筆交易」與「TRA10071 因查無交易資料次數已達上限，已鎖定交易查詢功能，請待 4 小時解鎖」，兩者差別為何？**

A1: 當商店查詢錯誤的商店訂單編號時，藍新金流會回傳錯誤訊息 TRA10021

A2: 當商店於 1 小時內查詢錯誤的商店訂單編號次數過多，藍新金流會回傳錯誤訊息 TRA10071，並鎖定查詢功能 4 小時

**Q: 出現「MEM40013 必填欄位資料不齊全」錯誤訊息之原因？**

A1: 請以 HTML Form Post 方式執行 API

A2: 請以 http encode 方式產生請求字串

A3: 請檢查發動 API 時是否有帶入所有必填參數

### 取消授權 [NPA-B01] & 請退款/取消請退款 [NPA-B31~34]

**Q: 為什麼發動取消授權或是請退款/取消請退款 API 會失敗？**

A1: 可參照圖 5 信用卡交易狀態圖，來確認發動 API 之時機點是否正確

A2: 若是發動請退款/取消請退款 API，須留意 CloseType 及 Cancel 參數值：若為請退款，無須帶入 Cancel 參數；若為取消請退款，則須帶入 Cancel 參數

**Q: 出現「TRA10702 因達到執行請退款筆數上限，您的商店暫時無法使用本功能，請待 1 小時後解鎖」錯誤訊息之原因？**

A: 當商店於 1 小時內執行請退款次數過多，藍新金流會回傳錯誤訊息 TRA10702，並鎖定請退款功能 1 小時

### 電子錢包退款 [NPA-B06]

**Q: 為什麼發動電子錢包退款 API 會失敗？**

A1: 請注意不同於其他 API 皆使用 http Encode 產生請求字串，發動此 API 需使用 JSON Encode

A2: 可參照 4.6 電子錢包退款 [NPA-B06] 之電子錢包退款規則說明，來確認發動 API 之時機點是否正確

---

## 附錄 1 測試區腳本

| 代碼 | 中文名稱 | 測試交易注意事項 |
|------|----------|-----------------|
| CREDIT | 信用卡 | 1. 測試環境僅接受以下的測試卡號：<br>`4000-2211-1111-1111`（一次付清＋分期付款）<br>`4003-5511-1111-1111`（紅利折抵）<br>`3760-000000-00006`（美國運通卡）<br>2. 測試卡號有效月年及卡片背面末三碼，請任意填寫<br>3. 以測試授權碼來模擬付款完成，並未實際發動至收單機構<br>4. 銀聯卡交易不開放測試 |
| CreditRed | 紅利折抵 | 同上（使用紅利折抵測試卡號） |
| WEBATM | WebATM | 1. 測試區將直接模擬交易完成並傳送交易完成訊息<br>2. 僅支援華南銀行 |
| VACC | ATM轉帳 | 可測試是否取號並回傳正常，可至［會員專區/銷售記錄查詢］中針對該筆測試交易執行［模擬觸發］，系統將立刻傳送付款完成訊息至 NotifyURL |
| CVS | 超商代碼繳費 | 同 VACC |
| BARCODE | 超商條碼繳費 | 同 VACC |
| CVSCOM | 物流服務 | 1. 測試環境可測試物流訂單收單與透過列印寄貨單介面列印寄貨單/取得寄件代碼<br>2. 實際包裹貨態改變，需在正式環境並實際進行包裹交寄 |
| APPLEPAY | Apple Pay | 請使用真實之信用卡號，至 Apple 裝置上進行綁定與支付測試 |
| ANDROIDPAY | Google Pay | 請使用真實之信用卡號，至 Android 裝置上進行綁定與支付測試 |
| SAMSUNGPAY | Samsung Pay | 請使用真實之信用卡號，至 Samsung 裝置上進行綁定與支付測試 |
| LINEPAY | LINE Pay | 1. 測試交易引導至 LINE Pay 畫面後，登入或掃描 QR Code 後進行付款動作<br>2. 測試交易不支援［模擬觸發］ |
| ESUNWALLET | 玉山Wallet | 1. 僅能產出 QR Code 由網頁端點擊［模擬成功］或［模擬失敗］進行測試，無法使用［玉山Wallet］APP 進行掃碼測試<br>2.［模擬失敗］一律回傳 MPG03009 之錯誤訊息 |
| TAIWANPAY | 台灣Pay | 1. 僅能產出 QR Code 由網頁端點擊［模擬成功］或［模擬失敗］進行測試，無法使用［台灣Pay］APP 或其他支援銀行之 APP 進行掃碼測試<br>2.［模擬失敗］一律回傳 MPG03009 之錯誤訊息 |
| BITOPAY | BitoPay | 1. 僅能產出 QR Code 由網頁端點擊［模擬成功］或［模擬失敗］進行測試，無法使用［BitoPro］APP 進行掃碼測試<br>2.［模擬失敗］一律回傳 MPG03009 之錯誤訊息 |
| TWQR | TWQR | 測試交易引導至 ezPay 畫面後，僅能產出測試用 QR Code，無需使用 APP 進行掃碼測試；畫面靜置 30 秒後，系統即完成交易 |
| EZPWECHAT | 簡單付微信支付 | — |
| EZPALIPAY | 簡單付支付寶 | — |