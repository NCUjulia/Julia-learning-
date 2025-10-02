# NCU-Julia-learning-program
這個專案引導你們如何下載Julia以及如何在編譯器Jupyter操作


## 版本與適用性
- 文件日期：初版（V1）。
- 適用系統：Windows、macOS。
- 目標：使初學者可以在 Jupyter 環境使用 Julia。 


## 目錄
1. 下載 Julia
2. 安裝說明（Windows / macOS ）
3. 在 Jupyter 中使用 Julia（安裝 IJulia、啟動 Notebook: Jupyter）

## 1) 下載 Julia
1. 前往 Julia 官方網站下載頁( https://julialang.org/downloads/ )。
2. 選擇對應作業系統的安裝檔（例如 Windows installer、macOS pkg）。
   ![image](https://github.com/NCUjulia/Julia-learning-/blob/main/%E6%9C%AA%E5%91%BD%E5%90%8D(3).png)
   ![image](https://github.com/NCUjulia/Julia-learning-/blob/main/%E6%9C%AA%E5%91%BD%E5%90%8D(3).png)

**提示**：若偏好使用套件管理器（homebrew、apt、dnf 等），也可透過套件管理器安裝（不同發行版命令不同）。

## 2) 安裝說明

### Windows
1. 執行下載的 `.exe` 安裝檔。
2. 依安裝精靈（Installer）步驟完成安裝，並且確認安裝的adress；安裝選項可將 Julia 加入系統 PATH（建議勾選，方便從終端機呼叫 `julia`）。
3. 安裝完成後，在命令提示字元（Command Prompt）或 PowerShell 輸入：

```powershell
julia --version
```

以確認安裝成功。

---

### macOS
1. 檢查macos的硬體設備，查看中央處理器(Intel/M series)
2. 執行下載的 `.dmg` 或 `.pkg`，跟隨指示安裝。
3. 若使用 tarball，可解壓到 `/Applications` 或其他目錄，並建立符號連結（symlink）到 `/usr/local/bin`，以便從終端呼叫 `julia`。
4. 安裝後於 終端(Terminal) 執行：

```bash
julia --version
```

## 3)使用Jupyter編譯器
1. 打開Julia並輸入:

```Julia
julia> using Pkg
julia> Pkg.add("IJulia")
```
2. 下載完IJulia後輸入:

```Julia
julia> using IJulia
julia> notebook()

```
3.透過conda讓Jupyter新增到新路徑

```Julia
install Jupyter via Conda, y/n? [y]: y               #請填y讓Jupyter新增到新路徑
```
