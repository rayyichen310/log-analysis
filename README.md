# Log Analysis Toolkit

## Overview

The **Log Analysis Toolkit** is a set of Python tools designed for parsing, analyzing, and visualizing Linux system log files. This toolkit aims to help users monitor system activities, identify potential security threats, and gain deeper insights into system performance.

The toolkit is implemented in the form of Jupyter Notebooks (`.ipynb`), with different functionalities distributed across separate cells, allowing users to execute and analyze step-by-step easily.

## Features

1. **Log Parsing**:
   - Parses general system logs, extracting date and time, hostname, program name, and message content.
   - Parses SSH login failure logs, extracting source IP, username, and geographic location information.

2. **Log Filtering**:
   - Filters logs based on user-specified date ranges.
   - Aggregates and displays the number of log entries for each program.

3. **Detailed Viewing**:
   - Allows users to select specific programs to view all log entries for that program within a specified time range.

4. **Visual Analysis**:
   - Generates various statistical charts, such as bar charts and line graphs, to display program activities, source IPs, usernames, and geographic distribution.

5. **Result Saving**:
   - Saves analysis results as CSV files for future reference or report creation.
   - Saves generated charts as PNG image files.

## Prerequisites

Ensure that your system has the following software and Python packages installed:

- **Python 3.6 or higher**
- **Jupyter Notebook**
- **Required Python Packages**:
  - `pandas`
  - `matplotlib`
  - `seaborn`
  - `ipinfo`

You can install the required packages using the following command:

```bash
pip install pandas matplotlib seaborn ipinfo
```

## Installation

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/log-analysis-toolkit.git
   cd log-analysis-toolkit
   ```

## Usage

### 1. Log Parsing

In the first cell of the Notebook, execute the code to parse the log files. This section is responsible for reading the log files and converting them into a structured DataFrame.

### 2. General Log Analysis

In the second cell, execute the code to perform general log analysis. This section includes:

- Allowing the user to select the number of days to view (default is all logs).
- Filtering logs based on the selected number of days.
- Aggregating and displaying the number of log entries for each program.
- Allowing the user to select specific programs to view detailed log entries.
- Optional: Saving the selected program's logs as a CSV file.
- Optional: Generating and saving a bar chart displaying the top 20 programs by log entry count.

### 3. SSH Log Analysis

In the third cell, execute the code to focus on the analysis of SSH login failure logs. This section includes:

- Parsing SSH logs to extract source IPs, usernames, and geographic location information.
- Setting up the IPInfo access token to obtain geographic locations.
- Performing multidimensional statistical analysis, including daily login failure counts, source IP statistics, username statistics, time distribution analysis, and source country statistics.
- Generating and saving relevant visual charts.
- Saving analysis results as CSV files.

## Configuration

### IPInfo Access Token

SSH log analysis requires the use of the IPInfo service to obtain geographic location information for IP addresses. Follow these steps to obtain and configure your access token:

1. **Obtain Access Token**:
   - Register and log in to [ipinfo.io](https://ipinfo.io/).
   - Find your access token in the account dashboard.

2. **Configure Access Token**:
   - In the SSH Log Analysis cell of the Notebook, locate the following line:
   
     ```python
     access_token = 'YOUR_IPINFO_ACCESS_TOKEN'  # Replace with your ipinfo access token
     ```
   
   - Replace `'YOUR_IPINFO_ACCESS_TOKEN'` with your actual access token:
   
     ```python
     access_token = 'your_actual_access_token_here'
     ```

## Outputs

### General Log Analysis

- **CSV Files**:
  - `selected_program_logs.csv`: Contains detailed logs of the selected program.

- **Visual Charts**:
  - `program_summary_top20.png`: Bar chart showing the top 20 programs by log entry count.

### SSH Log Analysis

- **CSV Files**:
  - `daily_login_failures.csv`: Daily SSH login failure counts.
  - `ip_failures.csv`: Login failure counts by source IP address (top 10).
  - `user_failures.csv`: Login failure counts by target username (top 10).
  - `hourly_failures.csv`: Login failure counts distributed by hour.
  - `country_failures.csv`: Login failure counts by source country (top 10).

- **Visual Charts**:
  - `daily_login_failures.png`: Line chart showing daily SSH login failure counts.
  - `top10_ip_failures.png`: Bar chart showing login failure counts for the top 10 source IP addresses.
  - `top10_user_failures.png`: Bar chart showing login failure counts for the top 10 target usernames.
  - `hourly_login_failures.png`: Bar chart showing login failure counts distributed by hour.
  - `top10_countries_failures.png`: Bar chart showing login failure counts for the top 10 source countries.

## License

This project is licensed under the [MIT License](LICENSE).

---
---


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

