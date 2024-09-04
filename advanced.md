# 進階操作

在 Selenium 中，高級操作可以讓你更靈活地控制瀏覽器，處理更複雜的情境，比如滾動頁面、處理多個視窗或頁籤，以及應對彈出視窗和警示對話方塊。以下是這些操作的詳細說明：

## 1. 滾動頁面
在自動化測試中，滾動頁面是非常常見的操作，特別是當你需要加載懶加載的內容或操作不在視窗範圍內的元素時。

### 滾動到頁面的底部

你可以使用 JavaScript 指令來滾動頁面。以下是滾動到頁面底部的範例：
```python
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")
```

### 滾動到特定元素

你也可以滾動到頁面中的特定元素：
```python
element = driver.find_element(By.ID, "element_id")
driver.execute_script("arguments[0].scrollIntoView();", element)
```

`arguments[0]` 指的是 `execute_script` 裡面傳給 javascript 的第一個 `argument`，也就是 `element`。

### 滾動特定的距離

你也可以滾動一個特定的距離（例如，垂直滾動 1000 像素）：
```python
driver.execute_script("window.scrollBy(0, 1000);")
```

## 2. 處理多個視窗或頁籤
在現代網頁中，經常會有打開新視窗或新頁籤的情況。Selenium 提供了處理多個視窗和頁籤的方法。

### 獲取所有視窗的句柄
每個視窗或頁籤在 Selenium 中都有一個唯一的句柄。你可以通過 window_handles 來獲取所有視窗的句柄。

```python
# 獲取當前所有視窗的句柄
handles = driver.window_handles
```

### 切換到新視窗或頁籤
假設你開啟了一個新視窗或頁籤，可以使用句柄切換到它：

```python
# 獲取當前視窗的句柄
main_window = driver.current_window_handle

# 打開新視窗/頁籤後，切換到新視窗/頁籤
new_window = driver.window_handles[-1]
driver.switch_to.window(new_window)
```

### 關閉視窗並切換回主視窗
```python
# 關閉當前視窗
driver.close()

# 切換回主視窗
driver.switch_to.window(main_window)
```

## 3. 處理彈出視窗和警示對話方塊
在 Selenium 中，處理 JavaScript 產生的彈出視窗（例如 `alert`、`confirm` 或 `prompt`）是常見需求。你可以使用 `switch_to.alert` 來處理這些彈出視窗。

### 接受彈出視窗
如果你需要點擊 "確定" 按鈕來接受彈出視窗：

```python
alert = driver.switch_to.alert
alert.accept()
```

### 取消彈出視窗
如果你需要點擊 "取消" 按鈕來關閉彈出視窗：
```python
alert = driver.switch_to.alert
alert.dismiss()
```

### 獲取彈出視窗的文字
你可以提取彈出視窗中的文字內容：
```python
alert = driver.switch_to.alert
alert_text = alert.text
print(alert_text)
```

### 在提示框中輸入文字
如果彈出視窗是 prompt 對話框，你可以向其中輸入文字：
```python
alert = driver.switch_to.alert
alert.send_keys("Your input text")
alert.accept()
```

## 範例整合
以下是一個整合範例，演示如何在同一腳本中使用滾動、切換視窗和處理彈出視窗：

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

# 創建 WebDriver 物件
driver = webdriver.Chrome()

# 打開一個示例頁面
driver.get("https://example.com")

# 滾動到頁面底部
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")

# 點擊打開新視窗的鏈接
driver.find_element(By.LINK_TEXT, "Open new window").click()

# 切換到新視窗
new_window = driver.window_handles[-1]
driver.switch_to.window(new_window)

# 在新視窗中操作 (例如，點擊一個按鈕)
driver.find_element(By.ID, "button_in_new_window").click()

# 模擬處理彈出視窗
alert = driver.switch_to.alert
print(alert.text)  # 打印彈出視窗的文字
alert.accept()     # 接受彈出視窗

# 關閉新視窗
driver.close()

# 切換回主視窗
driver.switch_to.window(driver.window_handles[0])

# 完成操作後，關閉瀏覽器
driver.quit()
```

這些進階操作能幫助你處理更複雜的網頁場景，使自動化測試更具穩定性和靈活性。
