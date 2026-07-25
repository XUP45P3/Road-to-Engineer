# 🐍 Anaconda 虛擬環境指令

> 💡 **小提示**：在終端機中執行指令時，請確保已經安裝並初始化過 Anaconda。

---

## 一般環境管理

### 1. 查詢與切換環境

- **列出所有虛擬環境**
  ```bash
  conda env list
  ```
  > 🔍 清單中帶有 `*` 記號的，就是你目前正在使用的環境。

- **進入指定的虛擬環境**
  ```bash
  conda activate your_env_name
  ```
  > 切換成功後，終端機最前面的提示字元會變成 `(your_env_name)`。

- **退出當前的虛擬環境**
  ```bash
  conda deactivate
  ```
  > 退出成功後，終端機最前面的提示字元會恢復成預設的 `(base)`。

### 2. 建立與刪除環境

- **複製現有環境** (將 `base` 裡的所有套件複製到新環境)
  ```bash
  conda create --name your_env_name --clone base
  ```

- **徹底刪除指定環境**
  ```bash
  conda remove --name your_env_name --all
  ```
  > ⚠️ 參數 `--all` 非常重要！它不僅會刪除環境名稱，還會把裡面安裝過的套件、殘留檔案清得一乾二淨。

---

## 建立特定條件的新環境

### 1. 指定 Python 版本

- **指定「主版本號」** (系統會自動抓取 3.9 系列的最新小版本)
  ```bash
  conda create --name your_env_name python=3.9
  ```

- **指定「絕對版本號」與大禮包**
  ```bash
  conda create --name your_full_env python=3.9.13 anaconda
  ```
  > 📦 結尾加上 `anaconda` 是一個超級組合包指令，系統會一次把幾百個資料科學常用的套件全部安裝進新環境裡，省去逐一安裝的麻煩。

---

## 進階實用技巧

### 1. 讓 Windows 支援 Linux 指令
在 Windows 系統的 Conda 環境中安裝以下套件後，你的 Windows 終端機就能聽懂並執行常見的 Linux 指令 (如 `ls`, `grep`, `rm` 等)：

```bash
conda install m2-base m2-coreutils
```

---

## 套件與依賴管理

### 1. 查看已安裝套件

- **列出目前環境中所有套件 (Conda 方式)**
  ```bash
  conda list
  ```

- **列出目前環境中所有套件 (Pip 方式)**
  ```bash
  pip list
  ```

- **列出套件與精確版本號** (適合直接閱讀)
  ```bash
  pip list --format=freeze
  ```

### 2. 安裝與移除單一套件

- **安裝指定套件**
  ```bash
  conda install numpy
  ```

- **安裝「指定絕對版本號」的套件**
  ```bash
  pip install pandas==1.4.4
  ```

- **移除指定套件**
  ```bash
  conda remove numpy
  ```
  *(💡 若當初是使用 pip 安裝的套件，請改用 `pip uninstall 套件名稱` 來移除)*

### 3. 匯出與還原專案環境 (業界實戰常用)

> 💡 **小提示**：在進行團隊協作或專案交接時，將環境設定檔完整匯出是非常重要的好習慣，這能確保每個人的執行環境完全一致。

- **匯出 Pip 需求清單 (`requirements.txt`)**
  ```bash
  pip freeze > requirements.txt
  ```
  > 📄 `pip freeze` 會輸出精確的版本清單，透過 `>` 將其導出成 txt 檔案，是業界最通用的 Python 專案交接格式。

- **匯出 Conda 完整環境設定 (`environment.yml`)**
  ```bash
  conda env export --no-builds > environment.yml
  ```
  > 🌍 加上 `--no-builds` 參數非常關鍵！它可以讓使用不同系統（Mac、Linux、Windows）的組員也能順利還原環境。

- **一鍵還原 Conda 環境**
  ```bash
  conda env create -f environment.yml
  ```
  > 🪄 `-f` 代表 file (檔案)。這行指令能根據 `environment.yml` 自動建立一個全新的虛擬環境，並把所有套件一次裝好，省去一個個 `conda install` 的麻煩。
