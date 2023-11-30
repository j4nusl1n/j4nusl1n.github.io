---
title: 美股ETF投資人申報NEC退稅分享
tags:
  - 美股投資
  - 報稅
  - 美股ETF
  - 美股退稅
  - 美股ETF退稅
categories:
  - - 美股投資
    - 報稅
date: 2023-11-29 12:32:11
description: 
  分享非美國稅務身份NRA，投資美股ETF如何申請NEC退稅及ITIN號碼
---

![Filing Tax Return Form](https://cdn.statically.io/gh/j4nusl1n/blog-images@master/kelly-sikkema-M98NRBuzbpc-unsplash.hb3ho92g448.webp)

## 前言

> 聲明：
本人沒有任何法律會計或是美國稅法相關背景，英文程度也不算好。
以下內容純屬個人見解及個人做法，純屬記錄個人投資歷程。
歡迎留言交流指正，但相關稅務責任需自負。
>

簡單介紹美股ETF投資人如何填寫表格申請退稅及申請ITIN  
並且附上本人申請退稅流程作為參考

<!--more-->


## 為什麼要退稅

> 以下內容為參考 **[Rib的投資學習筆記](https://ribtw.blogspot.com/)** 的 **[NEC退稅文章](https://ribtw.blogspot.com/2014/04/NEC-Tax-Refund.html)** 後個人整理的概要
若想更詳細了解建議閱讀Rib前輩整理的退稅文章系列
>

非美國投資人(**NRA**)因為必須填寫*W-8BEN*表格給券商，配息前券商會自動依照預扣稅比例(台灣人30%)，從配息中預先扣除後再給投資人。因此其實收到的配息已經是完稅，無需在隔年向IRS報稅。

然而部分配息是有可能屬於**無須課稅**(*Non-taxable*)的種類，如下列提到的幾種項目。

- *Return of Capital* (**ROC**): 配息來自本金
- *Foreign Source Income* (**FSI**): 外國來源收入
- *Qualified Interest Income* (**QII**): 基金配息來自免稅的部分
- *Long/Short-term Capital Gain Distribution* (**L/T CG**, **S/T CG**): 長期/短期資本利得分配

隨著投入本金增長的情況下，配息被預扣稅的數目累積起來也是不可小覷，此時若能透過退稅退回無須課稅的部分自然是最好。

這類的配息再入帳後可以經由再分類的程序，在隔年收到券商提供的**1042-S**表格後，填寫**1040-NR**向IRS申報*Non-Effectively Connected Income* (**NEC**)其中屬於無須扣稅的部分，進而退回多扣除的配息。

## 配息再分類

### 抽取稅務資料

在進行配息再分類前，必須先取得各基金公司(e.g. *Vanguard*, *iShares*)提供的稅務資料，才能釐清各個ETF的配息中哪些部分屬於可退稅的項目。

感謝Rib前輩已經有整理台灣投資人常選擇的基金公司的稅務資料，可以在 **[NEC退稅稅務資料抽取試算表](https://ribtw.blogspot.com/2015/04/tax-info-spreadsheet.html)** 中取得整理過的資料，以下用 *Vanguard* 的[2022稅務資料抽取試算表](https://docs.google.com/spreadsheets/d/1VBE5HgNNarBjUC_n_8vQ04MMCXCodwZ_SkUjesSsoXA/edit?usp=drive_link)作為範例。

![以2022 Vanguard BND/VXUS稅務資料抽取為例](https://cdn.statically.io/gh/j4nusl1n/blog-images@master/1040-NR-tax-return/BND-dividend.9e1klupvom8.webp)*以2022 Vanguard BND/VXUS稅務資料抽取為例*

從範例圖中可以看到，BND的每月配息中幾乎有90%為**QII**、VXUS的配息全數屬於**FSI**。這些配息原本從券商入帳時都會被扣除30%，透過配息再分類的步驟，我們可以將最後計算出來多扣除的部分申請退回。

### 填寫再分類報表

擁有抽取出的稅務資料以後，就能夠以此計算實際收到的配息中屬於免稅的金額。

以Rib前輩製作的[Schwab NEC退稅試算表](https://ribtw.blogspot.com/2017/04/schwab-nec-2016.html)為例，依照文章及試算表指示將稅務資料、券商交易紀錄、券商提供的********1042-S********等資料一一填入對應試算表欄位後，就能產製一份配息再分類報表如下圖。

![配息再分類報表範例](https://cdn.statically.io/gh/j4nusl1n/blog-images@master/1040-NR-tax-return/reclassification.1xpkh76rtkdc.webp)*配息再分類報表範例*

其中會得到四個重要的數字，依序分別為

- *Total Taxable Income*: 應稅收入
- *Total Tax*: 應付稅金
- *Federal Tax Withheld*: 預扣稅
- *Tax Overpaid*: 溢付稅金

之後在填寫**1040-NR**時必須要填在對應的欄位。

## 申請ITIN：填寫W-7

若是第一次向IRS報稅，必須填寫**W-7**表格申請一組個人稅務編號(*Individual Taxpayer Identification Number*, **ITIN**)，此號碼格式與美國的社會安全編號(*Social Security Number*, **SSN**)類似，主要是提供**NRA**報稅時使用。

申請**ITIN**所需文件有下列幾項

- W-7: 申請**ITIN**專用表格([PDF檔案連結](https://www.irs.gov/pub/irs-pdf/fw7.pdf))
- 1040-NR: 申請退稅用表格
- 身分證明文件: **護照正本**或是**外交部認證的護照正影本相符證明**
  - 建議不要使用正本，因為申請完IRS會用平信寄回來容易遺失
  - 外交部認證護照正影本相符證明申請費用*NTD$400*

建議填寫表格時，可以使用支援PDF的網頁瀏覽器(e.g. Chrome, Safari)開啟文件，除了需要簽名的欄位外使用打字方式填寫，以避免人工填寫錯誤。

## 申請退稅：填寫1040-NR

填寫1040-NR時所需要填寫的有三份表格，都能夠在IRS的[1040-NR頁面](https://www.irs.gov/forms-pubs/about-form-1040-nr)中找到。

分別為：

1. 1040-NR 主表 ([1040-NR PDF檔案](https://www.irs.gov/pub/irs-pdf/f1040nr.pdf))
2. Schedule NEC
3. Schedule OI

填寫1040-NR主表時，需注意第一頁上方的年份，若是需要申報更之前年份的退稅，可以在[IRS歷年表格](https://www.irs.gov/prior-year-forms-and-instructions)的頁面搜尋對應關鍵字並開啟文件填寫。

**以下填寫範例為本人經驗，如有其他美國稅務身份或是美國來源收入，請諮詢專業稅務人士！**

![1040-NR表格第一頁](https://cdn.statically.io/gh/j4nusl1n/blog-images@master/1040-NR-tax-return/1040-NR-page1.1qutg649uhxc.webp)*1040-NR表格第一頁*

![Schedule NEC](https://cdn.statically.io/gh/j4nusl1n/blog-images@master/1040-NR-tax-return/schedule-nec.4iud75o85km0.webp)*Schedule NEC*

![1040-NR表格第二頁](https://cdn.statically.io/gh/j4nusl1n/blog-images@master/1040-NR-tax-return/1040-NR-page2.3wsjskyqvbs0.webp)*1040-NR表格第二頁*

![Schedule OI](https://cdn.statically.io/gh/j4nusl1n/blog-images@master/1040-NR-tax-return/schedule-oi.49nizqrig2m0.webp)*Schedule OI*

注意事項：

- *Schedule NEC*上方*Nature of Income*對應為預扣稅比例，台灣投資人NRA身份為30%，若有其他國家稅務身份則需填入對應比例的欄位。
- 主表的第二頁**Direct Deposit**資訊，若是券商有提供可直接入帳的帳戶，可以填寫*Routing Number*及*Account Number*，**IRS**退稅時就會直接匯入填寫的帳戶，否則需要等待IRS退稅支票寄回。
- *Schedule OI*各項目說明，可參考Rib前輩的[填寫說明範例](https://ribtw.blogspot.com/2016/04/1040nr-schedule-oi.html)
  - A~H：攸關投資人的稅籍身份認定，請依個人狀況填寫
  - L：若擁有**與美國有稅務協定的國家的稅籍身份**請照實填寫，必要情況時須額外附上[Form 8833](https://www.irs.gov/forms-pubs/about-form-8833)

## 退稅時程

- 2023-08-30 申請護照正影本相符證明
- 2023-09-01 領取護照正影本相符證明
- 2023-09-05 文件寄出(國際掛號郵資NTD$293)
- 2023-09-07 郵件離開台灣
- 2023-09-08 郵件抵達美國互換局
- 2023-09-18 郵件送達IRS Austin Service Center ITIN Operation
  - 透過USPS Customer Support Email得知送達日期
- 2023-11-01 2022年度退稅入帳(Direct Deposit)
- 2023-11-16 2021年度退稅入帳(Direct Deposit)
- 2023-11-20 收到IRS ITIN通知信(CP565)
  - 2023-10-12 從IRS寄出(從信件內容得知)

---

ref.

- [美國券商NRA投資人NEC退稅總整理](https://ribtw.blogspot.com/2014/04/NEC-Tax-Refund.html)
- [外交部申請出具「護照正影本相符」證明流程圖](https://www.boca.gov.tw/cp-169-3981-7067f-1.html)
