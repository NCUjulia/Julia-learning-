# NCU-Julia-learning-program
這個專案引導你們如何下載Julia以及如何在編譯器Jupyter操作


## 版本與適用性
- 文件日期：初版（V2）。
- 適用系統：Windows、macOS。
- 目標：使初學者可以在 Jupyter 環境使用 Julia。 


## 目錄
1. 下載 Julia
2. 安裝說明（Windows / macOS ）
3. 在 Jupyter 中使用 Julia（安裝 IJulia、啟動 Notebook: Jupyter）
4. 認識 Julia 

## 1) 下載 Julia
1. 前往 Julia 官方網站下載頁( https://julialang.org/downloads/ )。
2. 選擇對應作業系統的安裝檔（例如 Windows installer、macOS pkg）。
   ![image](https://github.com/NCUjulia/Julia-learning-/blob/main/%E6%9C%AA%E5%91%BD%E5%90%8D(3).png)

**提示**：若偏好使用套件管理器（homebrew、apt、dnf 等），也可透過套件管理器安裝（不同發行版命令不同）。

## 2) 安裝說明

### Windows
1. 執行下載的 `.exe` 安裝檔。
2. 依安裝精靈（Installer）步驟完成安裝，並且確認安裝的adress；安裝選項可將 Julia 加入系統 PATH（建議勾選）。
 ![image](https://github.com/NCUjulia/Julia-learning-/blob/main/%E6%9C%AA%E5%91%BD%E5%90%8D(4).png)
 ![image](https://github.com/NCUjulia/Julia-learning-/blob/main/%E6%9C%AA%E5%91%BD%E5%90%8D(2).png)
 ![image](https://github.com/NCUjulia/Julia-learning-/blob/main/%E6%9C%AA%E5%91%BD%E5%90%8D(1).png)

3.打開Julia以確認安裝成功。
 ![image](https://github.com/NCUjulia/Julia-learning-/blob/main/%E6%9C%AA%E5%91%BD%E5%90%8D(5).png)

---

### macOS
1. 檢查macos的硬體設備，查看中央處理器(Intel/M series)。
 ![image]()  
2. 執行下載的 `.dmg` 或 `.pkg`，跟隨指示安裝。
3. 打開Julia圖標並將Julia移動到應用程式(Application)的檔案裡。
4. 安裝後於應用程式內打開或在終端(Terminal) 執行：

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

## 4） Julia 套件管理（Package Management）

### 為什麼要學套件管理？
Julia 本身只提供最基本的功能。  
若是想畫圖、處理資料、做機器學習或數學模擬等等，就需要安裝外部「套件（Packages）」。

Julia 內建的 **`Pkg` 模組** 負責：
- 安裝套件  
- 更新套件  
- 移除套件  
- 管理不同專案的環境和版本  

---

### 進入 Pkg 模式
在 Julia 互動介面（REPL）中，按下 `]` 鍵即可進入 **Pkg 模式**：  
在這裡輸入以下指令操作套件：

| 指令 | 功能 | 範例 |
|------|------|------|
| `add 套件名` | 安裝套件 | `add Plots` |
| `add 套件名@版本` | 安裝指定版本 | `add DataFrames@1.6.1` |
| `rm 套件名` | 移除套件 | `rm CSV` |
| `update` | 更新所有套件 | `update` |
| `status` | 查看目前套件狀態 | `status` |
| `instantiate` | 根據環境設定重新安裝套件 | `instantiate` |
| `activate 路徑` | 啟用或建立新環境 | `activate .` |

離開 Pkg 模式只要按 **Backspace** 或 `Ctrl + C`。

---

### 在程式中使用 Pkg
除了 REPL 模式，也能在程式中直接使用 `Pkg`：
```julia
using Pkg

Pkg.add("DataFrames")
Pkg.add("Plots")

Pkg.status()
```
### 建立專案環境（Environment）

Julia 支援專案環境，讓每個專案都有獨立的套件版本。
步驟如下：
```Julia
]
activate MyProject
add CSV DataFrames
status
```
