# Selenium IDE 使用簡介

Selenium IDE 是一個非常友好的工具，特別適合初學者和那些希望快速創建自動化測試的人。它是一個瀏覽器擴展。以下是使用 Selenium IDE 的基本步驟和功能介紹：

## 1. 安裝 Selenium IDE

請連線至 [Selenium IDE](https://www.selenium.dev/selenium-ide/)安裝對應的擴展。

## 2. 啟動 Selenium IDE

安裝擴展後，你可以通過點擊瀏覽器工具欄上的 Selenium IDE 圖標來啟動它。啟動後，你會看到一個新的視窗，這就是 Selenium IDE 的主界面。

## 3. 創建新專案
在 Selenium IDE 中，測試用例和測試套件都存儲在專案中。要開始一個新的測試專案：

1. 點擊 "Create a new project"。
2. 輸入專案名稱。
3. 開始錄製測試用例。

## 4. 錄製測試
錄製是 Selenium IDE 的核心功能，它能自動記錄你在瀏覽器中的操作，並生成對應的 Selenium 指令。

1. 在專案創建後，Selenium IDE 會自動進入錄製模式。輸入目標網址後，點擊 "Start recording"。
2. 當你在瀏覽器中進行點擊、輸入、選擇等操作時，Selenium IDE 會自動記錄下這些操作。
3. 完成錄製後，回到 Selenium IDE 視窗，點擊 "Stop recording"。

## 5. 編輯測試用例
錄製完成後，你可以在 Selenium IDE 中查看和編輯測試用例。測試用例由一系列步驟組成，每一步驟都有三個部分：

* **Command**：要執行的指令（如 `click`, `type`, `open` 等）。
* **Target**：目標元素的定位方法（如 XPath, CSS 選擇器等）。
* **Value**：操作時所需的值（如在輸入框中輸入的文字）。

你可以手動添加、編輯或刪除步驟，來修改或優化你的測試用例。

## 6. 執行測試
編輯完測試用例後，你可以通過點擊 "Play" 按鈕來執行測試。Selenium IDE 會根據你定義的步驟在瀏覽器中自動重現這些操作。

* **Play current test case**：執行當前選中的測試用例。
* **Play all test cases in suite**：執行當前測試套件中的所有測試用例。

## 7. 驗證測試結果
Selenium IDE 可以幫助你驗證操作的結果。例如，你可以使用 `assert` 或 `verify` 指令來檢查特定元素是否存在，或者元素的屬性或文字是否符合預期。

```python
assertText | css=#element_id | Expected Text
```

* **assertText**：檢查指定元素中的文字是否與預期值匹配。
* **verifyElementPresent**：檢查指定元素是否存在。

## 8. 輸出測試腳本
Selenium IDE 支持將錄製的測試用例導出為不同編程語言的腳本，如 Java, Python, JavaScript 等。這樣，你可以在 Selenium WebDriver 中進一步使用這些腳本。

* 點擊 "File" 菜單，選擇 "Export"。
* 選擇目標語言（如 Python）。
* 將腳本保存到本地文件。

## 9. 進階功能
* **測試套件**：你可以將多個測試用例組合成一個測試套件，並一次性運行它們。
* **變數**：Selenium IDE 支持使用變數來存儲和傳遞數據，這對於動態測試非常有用。
* **條件語句和迴圈**：你可以在測試用例中添加條件語句（如 if-else）和迴圈來控制測試的執行流程。

## 10. 範例
以下是一個簡單的測試範例，該範例會打開 Google，搜尋 "Selenium IDE"，並驗證結果頁面是否包含預期的文字。

1. 打開 Selenium IDE，創建一個新專案。
2. 錄製操作：打開 `https://www.google.com`，在搜尋框中輸入 "Selenium IDE"，並按下回車鍵。
3. 驗證操作：檢查結果頁面是否包含 "Selenium IDE" 的文字。

完成後，你可以點擊 "Play" 按鈕來執行測試，驗證測試結果是否正確。

## 總結
Selenium IDE 是一個功能強大且易於使用的工具，特別適合用來快速創建和運行自動化測試。它提供了直觀的錄製功能、可編輯的測試用例、以及將測試導出為腳本的能力。隨著你對 Selenium IDE 的熟悉，你可以進一步利用它的進階功能來創建更複雜的測試。
