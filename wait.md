# Selenium中的等待

在使用 Python 的 Selenium 時，等待機制是確保網頁元素已經載入完成後再進行操作的關鍵。Selenium 提供了兩種主要的等待方式：隱性等待和顯性等待。

## 1. 隱性等待（Implicit Wait）
隱性等待會告訴 WebDriver，當找不到元素時，等待一段時間再嘗試查找。在這段時間內，WebDriver 會不斷地嘗試找尋元素，直到找到元素為止或超過設定的時間。這種等待是全局的，一旦設置，會在整個 WebDriver 生命週期中適用於每個元素查找。

```python
from selenium import webdriver

driver = webdriver.Chrome()
driver.implicitly_wait(10)  # 設定隱性等待 10 秒
driver.get("https://example.com")

# 例如：查找元素
element = driver.find_element(By.ID, "element_id")
```

## 2. 顯性等待（Explicit Wait）
顯性等待會根據條件來等待特定元素的出現或狀態。你可以指定一個等待條件，並設置最長等待時間。在條件滿足之前，WebDriver 會每隔一段時間檢查一次。這種等待是局部的，只應用於指定的元素或操作。

常用的等待條件包括：

* `presence_of_element_located`：等待元素出現在 DOM 中，不一定可見。
* `element_to_be_clickable`：等待元素可以被點擊，這意味著元素可見且可點擊。
* `visibility_of_element_located`：等待元素可見，且高度和寬度大於 `0`。

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()
driver.get("https://example.com")

# 顯性等待最多 10 秒，直到元素可被點擊
element = WebDriverWait(driver, 10).until(
    EC.element_to_be_clickable((By.ID, "element_id"))
)
element.click()
```

## 3. 如何判斷元素是否存在或是否可以點擊
在 Selenium 中，你可以使用顯性等待來判斷元素是否存在或可點擊。

* **判斷元素是否存在**： 使用 `presence_of_element_located` 或 `find_elements` 方法，如果元素存在，會返回一個列表，否則返回空列表。
```python
try:
    element = WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.ID, "element_id"))
    )
    print("元素存在")
except TimeoutException:
    print("元素不存在")
```

* **判斷元素是否可點擊**： 使用 `element_to_be_clickable` 方法。
```python
try:
    element = WebDriverWait(driver, 10).until(
        EC.element_to_be_clickable((By.ID, "element_id"))
    )
    print("元素可點擊")
except TimeoutException:
    print("元素不可點擊")
```

這些等待機制能有效幫助處理網頁中元素加載延遲的問題，避免出現 `ElementNotInteractableException` 或 `NoSuchElementException` 等常見錯誤。
