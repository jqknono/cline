# 使用 Cline 安裝基本開發工具 | 新手程式設計師

當您開始編碼時，您需要在電腦上安裝一些基本的開發工具。Cline 可以幫助您以安全、引導的方式安裝所有您需要的工具。

## 基本工具

以下是您進行開發所需的核心工具：

-   **Homebrew**：適用於 macOS 的套件管理器，可輕鬆安裝其他工具
-   **Node.js & npm**：JavaScript 和網頁開發所需
-   **Git**：用於追蹤代碼變更和與他人協作
-   **Python**：許多開發工具使用的程式語言
-   **其他實用工具**：如 wget 和 jq 等，用於下載檔案和處理數據的工具

## 讓 Cline 安裝所有工具

複製此提示並貼到 Cline 中：

```bash
你好 Cline！我需要幫助設置我的 Mac 進行軟體開發。請幫我安裝基本的開發工具，如 Homebrew、Node.js、Git、Python，以及任何其他常用的編碼工具？我希望你能一步一步引導我，解釋每個工具的作用，並確保一切都正確安裝。
```

## 將會發生什麼

1. Cline 將首先安裝 Homebrew，這就像是開發工具的「應用商店」
2. 使用 Homebrew，Cline 接著會安裝其他基本工具，如 Node.js 和 Git
3. 對於每個安裝步驟：
    - Cline 會向您展示它想要執行的確切命令
    - 您需要在命令執行前批准
    - Cline 會驗證每個安裝是否成功

## 這些工具為什麼重要

-   **Homebrew**：讓您在 Mac 上輕鬆安裝和更新開發工具
-   **Node.js & npm**：用於：
    -   使用 React 或 Next.js 建構網站
    -   執行 JavaScript 代碼
    -   安裝 JavaScript 套件
-   **Git**：幫助您：
    -   保存代碼的不同版本
    -   與其他開發人員協作
    -   備份您的工作
-   **Python**：用於：
    -   執行開發腳本
    -   數據處理
    -   機器學習項目

## 注意事項

-   安裝過程是互動式的 - Cline 將引導您完成每一步
-   某些安裝可能需要輸入您的電腦密碼。當提示時，螢幕上不會顯示任何輸入的字符。這是正常的，是保護您密碼的安全功能。只要輸入您的密碼並按 Enter 鍵。

**範例：**

```bash
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
密碼：
```

_在這裡輸入您的密碼，即使螢幕上不會顯示任何東西。完成後按 Enter 鍵。_

-   所有命令都會在執行前向您展示以供批准
-   如果遇到任何問題，Cline 將幫助您進行故障排除

## 新手程式設計師的額外提示

### 了解終端機

**終端機**是一個應用程式，您可以在其中輸入命令與電腦互動。在 macOS 上，您可以通過 Spotlight 搜索「終端機」來打開它。

**範例：**

```bash
$ open -a Terminal
```

### 了解 VS Code 功能

#### VS Code 中的終端機

VS Code 中的**終端機**允許您直接從編輯器中執行命令。您可以通過 `查看 > 終端機` 或按下 `` Ctrl + ` `` 來打開它。

**範例：**

```bash
$ node -v
v16.14.0
```

#### 文檔視圖
**文件檢視**是您編輯程式碼檔案的地方。您可以點擊螢幕左側的**檔案總管**面板來開啟檔案。

#### 問題區段

VS Code中的**問題**區段會顯示您的程式碼中的任何錯誤或警告。您可以點擊燈泡圖示或前往`檢視 > 問題`來存取它。

### 常見功能

-   **命令列介面 (CLI)**：這是一個基於文字的介面，您可以在其中輸入命令來與您的電腦互動。起初看似令人生畏，但它是開發者的強大工具。
-   **權限**：有時，您需要為某些應用程式或命令授予權限。這是一項安全措施，確保只有受信任的應用程式才能對您的系統進行更改。

## 後續步驟

安裝這些工具後，您將準備好開始編碼！返回[針對新程式設計師的Cline入門指南](../getting-started-new-coders/README.md)繼續您的旅程。