# 🚀 Git 版本控制

> 💡 **小提示**：在進行複雜的 Python 專案開發時，良好的版本控制與統一的程式碼風格，能大幅減少後續除錯與整合的痛苦！

---

## Git 專案協作流程

### 1. Clone & Branch

- **將雲端專案複製到本地端**
  ```bash
  git clone https://github.com/GitHub名稱/Repo名稱.git
  ```

- **建立並切換到新分支**
  ```bash
  git checkout -b {your_branch}
  ```
  > 在工程師的世界裡，`{}` 或 `[]` 通常代表這裡需要替換成你自訂的變數名稱。

### 2. Before Code Editing

> ⚠️ **非常重要**：每天開始寫扣前，務必先將主分支的最新進度同步到自己的分支，避免未來的衝突！

- **切換至主分支**
  ```bash
  git checkout master
  ```
- **將 GitHub 上的最新 master 拉到本地端**
  ```bash
  git pull origin master
  ```
- **切換回你的開發分支**
  ```bash
  git checkout {your_branch}
  ```
- **將本地端更新後的 master 進度合併到目前分支**
  ```bash
  git rebase master
  ```

### 3. After Code Editing

- **將所有變更加入暫存區**
  ```bash
  git add .
  ```
- **提交並紀錄本次變更**
  ```bash
  git commit -m "your message"
  ```
- **將本地端的分支推送到 GitHub**
  ```bash
  git push origin {your_branch}
  ```

### 4. Merge Request（MR） / Pull Request（PR）
- 將分支推送到 GitHub 後，即可在 GitHub 發起 **Merge Reques**，請求將 `{your_branch}` 的程式碼合併進 `master` 主分支中。

### 5. 視覺化實戰練習
- **[Learn Git Branching](https://learngitbranching.js.org/)**
  > 🎮  Git 互動學習網站！

---

## 環境設置與隱私保護

### 1. `.gitignore` 檔案忽略清單
> 🛡️ 將所有不能推上 GitHub 的內容寫入 `.gitignore`

- **帳密敏感資料**：`.env`
- **編譯產出**：`/dist`
- **快取檔案**：`.eslintcache`
- **編輯器與 IDE 設定檔**：`.vscode/`, `.DS_Store`
- **Python 依賴與快取目錄**：`__pycache__/`, `venv/`
- **日誌檔案**：`.log`
- **測試覆蓋率報告**：`.coverage`

---

## 程式碼規範 (PEP 8)

### 1. 官方風格指南

- **縮排**：嚴格使用 **4 個空格**，千萬不要使用 Tab。
- **命名方式**：
  - **變數與函數**：`snake_case` (小寫字母加底線)
  - **類別 (Class)**：`PascalCase` (首字母大寫的駝峰式)
  - **常數**：`UPPER_CASE_WITH_UNDERSCORES` (全大寫加底線)
- **行數限制**：每行不超過 79 個字元。

### 2. Pylint
> 🤖 Pylint 就像嚴格的老師，能自動幫你的 Python 程式碼挑錯並打分數。

- **安裝工具**
  ```bash
  pip install pylint
  ```
- **基本檢查**
  ```bash
  pylint your_script.py
  ```
  > 系統會列出所有不符合規範的地方，並給你的程式碼打一個分數 (滿分 10 分)。
- **產生自訂設定檔**
  ```bash
  pylint --generate-rcfile > .pylintrc
  ```
  > 這個指令會自動產生一個名為 `.pylintrc` 的設定檔。當團隊想要微調官方規範時，可以進去修改檢查規則。
- **套用自訂規則進行檢查**
  ```bash
  pylint --rcfile=.pylintrc your_script.py
  ```
  > 執行後，系統就會套用你微調過的 `.pylintrc` 規則來進行評分了！
