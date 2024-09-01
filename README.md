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
