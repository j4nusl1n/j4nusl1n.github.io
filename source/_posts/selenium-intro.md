---
title: Selenium 網頁爬蟲簡單分享 in Python
date: 2023-03-21 23:20:41
tags: [python,selenium,crawler,web crawler]
---

## 什麼是 Selenium？

**Selenium** 網頁爬蟲是一種透過程式模仿人類操作瀏覽器的方式，例如點擊連結、填入文字框等等，以便取得網頁中的資料  

<!--more-->

## 如何安裝使用 Selenium

以下程式範例使用 Python 3.8，環境設定的部分暫不贅述  

### 安裝 Selenium
```shell
pip install selenium
```

### 安裝瀏覽器驅動(Web driver)

要讓 Selenium 操作瀏覽器時，需要安裝對應的瀏覽器驅動，下列為幾種常用的瀏覽器驅動，可以依照個人喜好挑選

- Chrome: https://sites.google.com/a/chromium.org/chromedriver/downloads
- Firefox: https://github.com/mozilla/geckodriver/releases
- Edge: https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/
- Safari: https://webkit.org/blog/6900/webdriver-support-in-safari-10/

後續範例皆使用 Chrome 瀏覽器

### (Optional) Web Driver Manager

由於前述的瀏覽器驅動需要依照使用者安裝的瀏覽器，去選擇下載對應版本的驅動，因此可以額外使用 python 套件 `Web Driver Manager` 去自動下載新的瀏覽器驅動。適合在本機開發時若是瀏覽器時常更新版本的話，就不需要手動去下載新的驅動

```shell
pip3 install webdriver-manager
```

## Selenium 示範

下面為一段簡單的範例程式碼  

```python
from selenium import webdriver

# specify the path to the browser driver executable
driver = webdriver.Chrome('/path/to/chromedriver')

# navigate to a webpage
driver.get('https://www.example.com')

# find an element by its CSS selector and click on it
button = driver.find_element_by_css_selector('#my-button')
button.click()

# fill out a form and submit it
input_field = driver.find_element_by_css_selector('#my-input')
input_field.send_keys('Hello, World!')
submit_button = driver.find_element_by_css_selector('#submit-button')
submit_button.click()

# extract information from the page
heading = driver.find_element_by_css_selector('h1').text
paragraphs = driver.find_elements_by_css_selector('p')
for p in paragraphs:
    print(p.text)

# close the browser window
driver.quit()

```

在這個範例中，我們使用了 Selenium 驅動了 Chrome 瀏覽器，執行時會自動開啟一個瀏覽器畫面。  
接著我們開啟 [https://www.example.com](https://www.example.com)，並且使用 CSS 選擇器選定一個按鈕點擊它。  
再來繼續使用 CSS 選擇器找到文字框，輸入 `Hello, World!`，找到送出按鈕送出表單。  
接下來再取得網頁中標題`h1`以及文字段落`p`，並且印出所有文字段落內的文字。  
最後在結束前，別忘了使用`quit()`關閉瀏覽器。  
以上範例只是個參考，讓大家能夠大略上理解，如何透過 Selenium 操控瀏覽器將瀏覽網頁行為自動化。  
接著會再介紹如何應用 Selenium 的其他功能，以便應付更複雜的情境

