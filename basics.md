# Selenium基礎

Selenium 是一個強大的工具，用來自動化網頁瀏覽器的操作。使用 Python 和 Selenium，你可以編寫腳本來模擬使用者在網頁上的各種操作，例如點擊、輸入、選擇等等。以下是 Python 中 Selenium 的基礎操作介紹。

## 1. 安裝 Selenium 和 WebDriver
首先，確保你已經安裝了 Selenium。你可以使用 pip 來安裝：

```bash
pip install selenium
```

另外，你需要下載與你的瀏覽器匹配的 WebDriver。常見的 WebDriver 有：

* **ChromeDriver**（對應 Google Chrome）
* **GeckoDriver**（對應 Mozilla Firefox）
* **EdgeDriver**（對應 Microsoft Edge）

下載後，將 WebDriver 的可執行文件添加到系統的 PATH 中。

## 2. 創建 WebDriver 物件
要開始使用 Selenium，你需要創建一個 WebDriver 物件，這個物件代表一個瀏覽器實例。

```python
from selenium import webdriver

# 使用 Chrome 瀏覽器
driver = webdriver.Chrome()  # 如果 chromedriver 不在 PATH 中，你需要指定它的路徑

# 使用 Firefox 瀏覽器
# driver = webdriver.Firefox()

# 打開一個 URL
driver.get("https://www.example.com")
```

## 3. 查找元素
Selenium 提供多種方法來查找網頁元素。你可以使用元素的 `id`、`name`、`class name`、`tag name`、`link text`、`partial link text`、`CSS selector` 或 `XPath` 來查找它們。

```python
from selenium.webdriver.common.by import By

# 透過 ID 查找
element = driver.find_element(By.ID, "element_id")

# 透過 Name 查找
element = driver.find_element(By.NAME, "element_name")

# 透過 CSS Selector 查找
element = driver.find_element(By.CSS_SELECTOR, ".class_name")

# 透過 XPath 查找
element = driver.find_element(By.XPATH, "//tag[@attribute='value']")
```

你也可以使用 `find_elements` 方法來查找匹配條件的所有元素，該方法會返回一個元素列表。

```python
elements = driver.find_elements(By.CLASS_NAME, "class_name")
```

## 4. 操作元素
找到元素後，你可以對它們進行操作，例如點擊、輸入文本等。
```python
# 點擊一個按鈕
button = driver.find_element(By.ID, "submit_button")
button.click()

# 在文本框中輸入文字
text_field = driver.find_element(By.NAME, "username")
text_field.send_keys("my_username")

# 清除文本框中的文字
text_field.clear()

# 提交表單
form = driver.find_element(By.ID, "form_id")
form.submit()
```

## 5. 等待
Selenium 提供了隱性等待和顯性等待，以處理網頁載入延遲的情況。

* 隱性等待

隱性等待會在每次查找元素時等待指定的時間。
```python
driver.implicitly_wait(10)  # 等待最多 10 秒
```

* 顯性等待

顯性等待會在指定條件滿足時繼續執行。

```python
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# 等待某個元素可被點擊
element = WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.ID, "element_id"))
)
```

## 6. 瀏覽器操作
Selenium 可以控制瀏覽器的基本操作，例如返回、前進、刷新等。

```python
# 返回上一頁
driver.back()

# 前進到下一頁
driver.forward()

# 刷新頁面
driver.refresh()
```

## 7. 獲取網頁信息
你可以從瀏覽器中提取一些信息，比如當前的 URL、頁面標題或頁面的 HTML 內容。

```python
# 獲取當前頁面的 URL
current_url = driver.current_url

# 獲取頁面標題
title = driver.title

# 獲取頁面完整 HTML
page_source = driver.page_source
```

## 8. 關閉瀏覽器
完成操作後，記得關閉瀏覽器以釋放資源。

```python
# 關閉當前窗口
driver.close()

# 關閉所有窗口並退出 WebDriver
driver.quit()
```

## 9. 範例腳本
以下是一個簡單的範例腳本，它會打開 Google，搜尋 "Selenium Python"，並打印結果的第一個標題。

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

# 創建 WebDriver 物件
driver = webdriver.Chrome()

# 打開 Google
driver.get("https://www.google.com")

# 查找搜尋框並輸入關鍵字
search_box = driver.find_element(By.NAME, "q")
search_box.send_keys("Selenium Python" + Keys.RETURN)

# 等待搜尋結果加載
driver.implicitly_wait(10)

# 獲取第一個結果的標題
first_result = driver.find_element(By.CSS_SELECTOR, "h3")
print(first_result.text)

# 關閉瀏覽器
driver.quit()
```

這些就是 Python 中使用 Selenium 的基本操作。Selenium 還提供了更多進階功能，如處理彈出視窗、模擬鍵盤和滑鼠操作、處理多個窗口和框架等。隨著你對 Selenium 的熟悉，你可以更靈活地使用這些功能來自動化網頁操作。
