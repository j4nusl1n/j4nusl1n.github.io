---
title: Selenium 網頁爬蟲簡單分享 in Python
date: 2023-03-21 23:20:41
tags: [python,selenium,crawler,web crawler,網頁爬蟲]
categories:
    - [技術分享, 爬蟲]
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

- Chrome: <https://sites.google.com/a/chromium.org/chromedriver/downloads>
- Firefox: <https://github.com/mozilla/geckodriver/releases>
- Edge: <https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/>
- Safari: <https://webkit.org/blog/6900/webdriver-support-in-safari-10/>

後續範例皆使用 Chrome 瀏覽器

## Selenium 示範

下面為一段簡單的範例程式碼  

```python
from selenium import webdriver

# specify the path to the browser driver executable
browser = webdriver.Chrome('/path/to/chromedriver')

# navigate to a webpage
browser.get('https://www.example.com')

# find an element by its CSS selector and click on it
button = browser.find_element_by_css_selector('#my-button')
button.click()

# fill out a form and submit it
input_field = browser.find_element_by_css_selector('#my-input')
input_field.send_keys('Hello, World!')
submit_button = browser.find_element_by_css_selector('#submit-button')
submit_button.click()

# extract information from the page
heading = browser.find_element_by_css_selector('h1').text
paragraphs = browser.find_elements_by_css_selector('p')
for p in paragraphs:
    print(p.text)

# close the browser window
browser.quit()

```

在這個範例中，我們使用了 Selenium 驅動了 Chrome 瀏覽器，執行時會自動開啟一個瀏覽器畫面。  
接著我們開啟 <https://www.example.com>，並且使用 CSS 選擇器選定一個按鈕點擊它。  
再來繼續使用 CSS 選擇器找到文字框，輸入 `Hello, World!`，找到送出按鈕送出表單。  
接下來再取得網頁中標題`h1`以及文字段落`p`，並且印出所有文字段落內的文字。  
最後在結束前，別忘了使用`quit()`關閉瀏覽器。  
以上範例只是個參考，讓大家能夠大略上理解，如何透過 Selenium 操控瀏覽器將瀏覽網頁行為自動化。  

接著會再介紹如何應用 Selenium 的其他功能，以便應付更複雜的情境。

## 如何等待特定條件滿足後接續執行

如果我們需要等待網頁DOM元件產生之後再爬取資料的話，與其直接用`time.sleep()`的方式，更應該善用Selenium自帶的`WebDriverWait`類別及`expected_conditions`模組，來幫助我們寫出更有效率的爬蟲  

`WebDriverWait`是一個能夠等待特定條件達成後，才接著繼續執行後續程式的類別。  `expected_conditions`模組中有各種條件功能，能夠結合上面的類別，以便完成整個等待的過程。  

下面是個簡單的範例程式碼，讓爬蟲等待網頁中特定DOM元件完成顯示之後，再點擊此元件：

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# create a new Chrome browser instance
browser = webdriver.Chrome()

# navigate to the desired webpage
browser.get('https://www.example.com')

# wait for the element with ID "my_element" to become visible
wait = WebDriverWait(browser, 10)
element = wait.until(EC.visibility_of_element_located((By.ID, 'my_element')))

# do something with the element
element.click()

# close the browser window
browser.quit()
```

首先爬蟲開啟一個Chrome並且連到 <https://www.example.com>  
接著建立一個`WebDriverWait`物件，並且設定最大等待時間10秒  

再來使用 `expected_conditions` 模組中的 `visibility_of_element_located`去偵測指定DOM元件是否已經顯示在網頁中。這個函式需要一個參數去指定要偵測的DOM元件，這邊使用的是DOM的ID `my_element`  

`WebDriverWait`的`until`會等到條件滿足，或者是超過最大等待時間。若是條件滿足的話，則會回傳`visibility_of_element_located`中指定的元件，好讓我們能對此元件做互動  

## 擷取網頁回傳資料

有時候我們如果在爬取網頁時，需要擷取特定Http Request回傳的資料時，這時候我們就可以利用 Selenium 的 `get_log` 方法來達成目的  
下面為簡單的程式範例

```python
from selenium import webdriver
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities

# configure Google Chrome logging preference to all logs
# always use copy() to create a new desired capabilities
# to avoid the side effects of altering the Global class instance.
dc = DesiredCapabilities.CHROME.copy()
dc["goog:loggingPrefs"] = {"performance": "ALL"}

# Launch the browser and navigate to the page you want to capture network response logs from
driver = webdriver.Chrome(
    desired_capabilities=dc,
)
driver.get('https://www.example.com')

# Retrieve the browser's logs
logs = driver.get_log('performance')

# Filter out the network response logs from the browser logs
network_logs = [log for log in logs if 'Network.response' in log['message']]

```

在上述程式碼中，我們依序做了下面幾件事:

1. 設定Chrome記錄所有log並開啟瀏覽器
2. 開啟我們想要抓取資料的網址
3. 使用 `get_log()` 並且傳入參數 `'performance'`，讀取所有類型為performance的瀏覽器記錄
4. 記錄的`message`中帶有 `Network.response` 的留下，剩餘的濾掉

透過以上過程，我們可以取得網頁的Http response記錄  

下一段我們使用 `execute_cdp_command` 方法來取得資料

```python
# continue from codes above
import json

for log in network_logs:
    # parse JSON strings in log['message']
    msg = json.loads(log['message'])['message']

    # check if method is Network.responseReceived
    if msg["method"] == "Network.responseReceived":
        # use Selenium execute_cdp_cmd to retrieve respnose data
        data = driver.execute_cdp_cmd(
            "Network.getResponseBody",
            {"requestId": msg["params"]["requestId"]},
        )
        print(data)
```

接續前面取得的 `network_logs`，我們接著後續步驟取得回傳資料

1. 記錄的 `message` 欄位，其中資料為JSON string，因此使用 `json.loads()` 解析成 `dict` 格式並且留下 `message` 存到變數 `msg`
2. 檢查 `msg['method']` 是否為 `Network.responseReceived`
3. 使用 `execute_cdp_cmd()` 透過 Chrome DevTools Protocol 的 [Network.getResponseBody](https://chromedevtools.github.io/devtools-protocol/tot/Network/#method-getResponseBody) 指令，取得回傳資料

以上範例簡單演練了如何取得網頁Http Response的資料，好讓我們能使用回傳資料做後續處理

## (Optional) 使用套件管理瀏覽器驅動

由於前述的瀏覽器驅動需要依照使用者安裝的瀏覽器，去選擇下載對應版本的驅動，因此可以額外使用 python 套件 `Web Driver Manager` 去自動下載新的瀏覽器驅動。適合在本機開發時若是瀏覽器時常更新版本的話，就不需要手動去下載新的驅動

```shell
pip3 install webdriver-manager
```

```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
from webdriver_manager.core.utils import ChromeType

chrome_type = ChromeType.GOOGLE
browser = webdriver.Chrome(
    service=Service(
        ChromeDriverManager(chrome_type=chrome_type).install()
    ),
)
```
