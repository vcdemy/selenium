# Selenium使用簡介

在本門課程中，我們會教大家怎麼使用selenium。另外，我們會使用selenium IDE錄製使用者的操作，在將錄製的結果轉換成python的程式碼來使用。

## 關於唯客學院

* [唯客學院網址](https://www.vcdemy.com)
* [唯客學院粉絲專頁](https://www.facebook.com/vcdemy/)
* [唯客學院線上課程](https://vcdemy.teachable.com)

## 新舊版 selenium 使用上的差異

2022年11月4日之後 ，selenium(4.6.0+)有內建 selenium manager，如果在特定的路徑上沒有找到webdriver，selenium會自動幫你下載。

新版的 selenium 沒有 `find_element_by_xxx()` 的方法了，取而代之的是 `find_element(By.XXX)`的方法。

```python
from selenium.webdriver.common.by import By
element = driver.find_element(By.CSS_SELECTOR, "#id")
```

## 課程內容

### 1. Selenium基礎
#### 1.1 安裝與設定
* 安裝 Selenium (pip install selenium) 和瀏覽器驅動程式（如 ChromeDriver）。
* 配置瀏覽器驅動程式並測試是否能正常打開瀏覽器。
#### 1.2 基本操作
* 瀏覽器控制（開啟、關閉、最大化、最小化）。
* 打開網頁 (`driver.get(url)`).
* 查找元素（`find_element` 和 `find_elements`）:
  * 使用不同的方法來查找元素：`By.ID`, `By.NAME`, `By.XPATH`, `By.CSS_SELECTOR`。
### 2. 操作與等待
#### 2.1 元素操作
* 點擊元素 (`element.click()`).
* 輸入文字 (`element.send_keys("text")`).
* 清除文字框 (`element.clear()`).
#### 2.2 等待
* 隱式等待 (`driver.implicitly_wait(time_in_seconds)`).
* 顯式等待 (`WebDriverWait` 和 `expected_conditions`).
* 判斷元素是否存在或可點擊。
### 3. 高級操作與應用
#### 3.1 高級操作
* 滾動頁面 (`driver.execute_script("window.scrollTo(...)")`).
* 處理多個視窗/頁籤。
* 處理彈出視窗和警示對話方塊 (`driver.switch_to.alert`).
#### 3.2 應用練習
* 用上述學習的內容寫一個小專案，例如自動化登入網站或抓取簡單的資料。
* 嘗試處理異常和錯誤，確保程式的穩定性。

## 輔助工具

|工具|說明|
|:--|:--|
|Selenium IDE|可以錄製使用者的操作，再轉換成Python程式的工具。|
|Katalon|Katalon也可以錄製使用者的操作，再轉換成Python程式。之前，Selenium IDE曾經移除export to python code的功能，如果再發生，可以再改用Katalon來錄製使用者的操作。|

## 相關連結

* [selenium官網](https://www.selenium.dev/)
 [Selenium with Python](https://selenium-python.readthedocs.io/)
* [Web Drivers](https://selenium-python.readthedocs.io/installation.html#drivers)
* [Selenium IDE](https://www.selenium.dev/selenium-ide/)
* [Katalon](https://www.katalon.com/)
