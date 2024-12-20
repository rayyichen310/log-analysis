# 日誌分析工具包

## 概述

**日誌分析工具包** 是一套用於解析、分析及視覺化 Linux 系統日誌文件的 Python 工具，此工具包旨在幫助使用者監控系統活動、識別潛在的安全威脅，並深入了解系統性能。

本工具包採用 Jupyter Notebook (`.ipynb`) 的形式，將不同功能的程式碼分布於不同的儲存格中，方便使用者逐步執行和分析。

## 功能

1. **日誌解析**：
   - 解析一般系統日誌，提取日期時間、主機名、程序名稱及訊息內容。
   - 解析 SSH 登入失敗日誌，提取來源 IP、用戶名及地理位置資訊。

2. **日誌篩選**：
   - 根據使用者指定的天數範圍過濾日誌。
   - 匯總並顯示每個程序的日誌出現次數。

3. **詳細查看**：
   - 讓使用者選擇特定程序，查看該程序在指定時間範圍內的所有日誌條目。

4. **可視化分析**：
   - 生成各類統計圖表，如柱狀圖和折線圖，展示程序活動、來源 IP、用戶名及地理位置分布等。

5. **結果保存**：
   - 將分析結果保存為 CSV 文件，便於後續查閱或報告製作。
   - 將生成的圖表保存為 PNG 圖片檔案。

## 前提條件

確保您的系統已安裝以下軟體和 Python 套件：

- **Python 3.6 或更高版本**
- **Jupyter Notebook**
- **必要的 Python 套件**：
  - `pandas`
  - `matplotlib`
  - `seaborn`
  - `ipinfo`

您可以使用以下命令安裝所需套件：

```bash
pip install pandas matplotlib seaborn ipinfo
```

## 安裝

1. **克隆儲存庫**

   ```bash
   git clone https://github.com/yourusername/log-analysis-toolkit.git
   cd log-analysis-toolkit
   ```



## 使用方法

### 1. 日誌解析

在 Notebook 的第一個儲存格中，執行程式碼以解析日誌文件。此部分負責讀取日誌文件並將其轉換為結構化的 DataFrame。

### 2. 通用日誌分析

在第二個儲存格中，執行程式碼以進行通用日誌分析。此部分包括：

- 讓使用者選擇要查看的天數範圍（默認為全部日誌）。
- 根據選擇的天數範圍過濾日誌。
- 匯總並顯示每個程序的日誌出現次數。
- 讓使用者選擇特定程序，查看詳細日誌條目。
- 可選：將選定程序的日誌保存為 CSV 文件。
- 可選：生成並保存柱狀圖展示前20個程序的日誌出現次數。

### 3. SSH 日誌分析

在第三個儲存格中，執行程式碼以專注於 SSH 登入失敗日誌的分析。此部分包括：

- 解析 SSH 日誌，提取來源 IP、用戶名及地理位置資訊。
- 設定 IPInfo 的訪問令牌以獲取地理位置。
- 進行多維度的統計分析，包括每日登入失敗次數、來源 IP 統計、用戶名統計、時間分布分析及來源國家統計。
- 生成並保存相關的可視化圖表。
- 將分析結果保存為 CSV 文件。

## 配置

### IPInfo 訪問令牌

SSH 日誌分析需要使用 IPInfo 服務來獲取 IP 地址的地理位置資訊。請按照以下步驟獲取並配置您的訪問令牌：

1. **獲取訪問令牌**：
   - 註冊並登錄 [ipinfo.io](https://ipinfo.io/)。
   - 在帳戶儀表板中找到您的訪問令牌。

2. **配置訪問令牌**：
   - 在 Notebook 的 SSH 日誌分析儲存格中，找到以下行：
   
     ```python
     access_token = 'YOUR_IPINFO_ACCESS_TOKEN'  # 替換為您的 ipinfo access token
     ```
   
   - 將 `'YOUR_IPINFO_ACCESS_TOKEN'` 替換為您自己的訪問令牌：
   
     ```python
     access_token = 'your_actual_access_token_here'
     ```

## 輸出

### 通用日誌分析

- **CSV 文件**：
  - `selected_program_logs.csv`：包含選定程序的詳細日誌。

- **可視化圖表**：
  - `program_summary_top20.png`：展示前20個程序的日誌出現次數的柱狀圖。

### SSH 日誌分析

- **CSV 文件**：
  - `daily_login_failures.csv`：每日 SSH 登入失敗次數。
  - `ip_failures.csv`：來源 IP 地址的登入失敗次數（前10名）。
  - `user_failures.csv`：目標用戶名的登入失敗次數（前10名）。
  - `hourly_failures.csv`：按小時分布的登入失敗次數。
  - `country_failures.csv`：來源國家的登入失敗次數（前10名）。

- **可視化圖表**：
  - `daily_login_failures.png`：每日 SSH 登入失敗次數的折線圖。
  - `top10_ip_failures.png`：前10個來源 IP 地址的登入失敗次數柱狀圖。
  - `top10_user_failures.png`：前10個目標用戶名的登入失敗次數柱狀圖。
  - `hourly_login_failures.png`：按小時分布的登入失敗次數柱狀圖。
  - `top10_countries_failures.png`：前10個來源國家的登入失敗次數柱狀圖。



## 授權

本專案採用 [MIT 許可證](LICENSE)。

