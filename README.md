# NCU-Julia-learning-program
這個專案引導你們如何下載Julia以及如何在編譯器Jupyter操作


## 版本與適用性
- 文件日期：初版（V2）。
- 適用系統：Windows、macOS。
- 目標：使初學者可以在 Jupyter 環境使用 Julia。 


## 目錄
### 介紹Julia
&nbsp;&nbsp;&nbsp; 1.1 [下載 Julia](#11-下載-julia)

&nbsp;&nbsp;&nbsp;   1.2 [安裝說明（Windows / macOS ）](#12-安裝說明)

&nbsp;&nbsp;&nbsp;   1.3 [在 Jupyter 中使用 Julia（安裝 IJulia、啟動 Notebook: Jupyter）](#13-下載jupyter編譯器)

&nbsp;&nbsp;&nbsp;   1.4 [認識 Julia 管理套件 ](#14-julia-套件管理package-management)

&nbsp;&nbsp;&nbsp;   1.5 [常用的數學相關 Julia 套件](#15-常用的數學相關-julia-套件)

&nbsp;&nbsp;&nbsp;    1.6 [Julia 教程](#16-julia-教程)

### Jupyter


---
# 介紹Julia

## 1.1 下載 Julia
1. 前往 Julia 官方網站下載頁( https://julialang.org/downloads/ )。
2. 選擇對應作業系統的安裝檔（例如 Windows installer、macOS pkg）。
  



## 1.2 安裝說明

### Windows
1. 執行下載的 `.exe` 安裝檔。
2. 依安裝精靈（Installer）步驟完成安裝，並且確認安裝的adress；安裝選項可將 Julia 加入系統 PATH（建議勾選）。

&nbsp;&nbsp; 3.打開Julia以確認安裝成功。

 

---

### macOS
1. 檢查macos的硬體設備，查看中央處理器的型號(Intel/M series)。
  

2. 執行下載的 `.dmg` 或 `.pkg`，跟隨指示安裝，選擇符合自身型號的處理器檔案來下載，以下載較簡單的.dmg檔為主。
3. 打開Julia圖標並將Julia移動到應用程式(Application)的檔案裡，並觀察Julia檔案的種類是否出現應用程式。
   
4. 安裝後於應用程式內打開或在終端(Terminal) 執行：

```bash
julia --version         
```

## 1.3 下載Jupyter編譯器
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
3. 透過conda讓Jupyter新增到新路徑

```Julia
install Jupyter via Conda, y/n? [y]: y               #請填y讓Jupyter新增到新路徑
```

## 1.4 Julia 套件管理（Package Management）

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
Julia 會自動在此目錄建立：
- Project.toml → 記錄專案需要哪些套件
- Manifest.toml → 記錄套件和其相依版本

如此一來，不管在哪台電腦執行，都能用 instantiate 一鍵重建環境。

---
## 1.5 常用的數學相關 Julia 套件

以下是幾個常用的數學相關 Julia 套件與基本範例:

| 類別 | 套件名稱 | 功能說明 | 範例使用 |
|------|-----------|-----------|-----------|
| **資料處理** | `DataFrames.jl` | 表格資料操作（類似 Excel、Pandas） | `using DataFrames` |
| **資料讀取** | `CSV.jl` | 讀取與寫入 CSV 檔案 | `using CSV` |
| **視覺化** | `Plots.jl` | 畫折線圖、長條圖等各種圖表 | `using Plots; plot([1,2,3],[4,5,6])` |
| **數學計算** | `LinearAlgebra` | 提供線性代數與矩陣運算工具 | `using LinearAlgebra` |
| **統計分析** | `Statistics` | 提供平均值、標準差等統計函式 | `mean([1,2,3,4])` |
| **微分方程** | `DifferentialEquations.jl` | 解常微分方程（ODE/PDE） | `using DifferentialEquations` |

---

### 範例
```julia
# ==========================================
# 資料處理與讀取
# ==========================================
using CSV, DataFrames

# 讀取資料
df = CSV.read("data.csv", DataFrame)

# 顯示前 5 列
println(first(df, 5))
```

```Julia
# ==========================================
# 視覺化
# ==========================================
using Plots

x = 1:10
y = x .^ 2

plot(x, y, label="y = x²", title="簡單的折線圖")
```

```Julia
# ==========================================
# 數學與統計分析
# ==========================================
using LinearAlgebra, Statistics

A = [1 2; 3 4]
v = [5, 6]

println("矩陣乘法: ", A * v)
println("平均值: ", mean([1,2,3,4,5]))
```
## 1.6 Julia 教程
### 線上資源
| 類型 | 名稱 | 連結 |
|------|------|------|
| 官方文件 | Julia 官方說明文件 | [https://docs.julialang.org](https://docs.julialang.org) |
| YouTube 教學 | Julia入門教學 |  [Julia 入門教學影片](https://youtube.com/playlist?list=PLhQ2JMBcfAsiu2BjeDuj0OXxD1Or_FjID) |
---
# Jupyter

1. 透過終端機使用Julia打開Jupyter
```Julia
julia> using IJulia

julia> notebook()
```
2. 介面介紹
<p align="center">
  <img src="https://github.com/NCUjulia/Julia-learning-/blob/main/Jupyter%20file%20introduction.png" width="700">
</p>
<p align="center">
  <img src="https://github.com/NCUjulia/Julia-learning-/blob/jupyter-photo/1%20(1).png" width="700">
</p>
<p align="center">
  <img src="https://github.com/NCUjulia/Julia-learning-/blob/jupyter-photo/open%20note.png" width="700">
</p>

<p align="center">
  <img src="https://github.com/NCUjulia/Julia-learning-/blob/jupyter-photo/%E8%9E%A2%E5%B9%95%E6%93%B7%E5%8F%96%E7%95%AB%E9%9D%A2%202025-10-28%20125528.png" width="700">
</p>
<p align="center">這裡可以使用Julia進行編程</p>
