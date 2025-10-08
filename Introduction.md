# 基礎教學

在這裡我們將學習 Julia 中一些基礎的程式。

## 目錄

### 變數與字串
&nbsp;&nbsp;&nbsp; 1.1 Hello world

&nbsp;&nbsp;&nbsp; 1.2 數字與運算

&nbsp;&nbsp;&nbsp; 1.3 變數的類型

---
# 數字與字串

## 1.1 Hello world

在這一章節中，我們將學習如何輸出、什麼是變數以及如何執行簡單的數學運算，並討論「類型」的概念及其在 Julia 中的作用。

在 Julia 中，當我們想要將某個字串或數值輸出時，我們使用 `print` 來輸出。例如：

```Julia
julia> print("Hello world!")
Hello world!
```


## 1.2 數字與運算

在程式設計中，當我們想要給某個資訊 (例如數字) 貼上一個「標籤」時，我們會給它一個名稱，並稱之為**變數**。

當我們想要將某個資料指定成一個變數時，可以這樣輸入：

```Julia
julia> my_university = "NCU"
julia> my_favourite_number = 73
julia> my_favourite_pie = 3.1415
```

我們可以對數字和變數進行數學運算，並將結果指定給新的變數：

```Julia
julia> a = 2
julia> b = 3
julia> sum = a + b   
julia> difference = a - b   
julia> product = a * b  
julia> quotient = b / a   
julia> power = a^3   
julia> modulus = b % a  
```

完整的數學運算列表，參見 [官方指南](https://docs.julialang.org/en/v1/manual/mathematical-operations/index.html)



## 1.3 變數的類型

在編譯的過程中，每個變數都會被指定為一個**類型（type）**，變數的類型可以由程式設計師指定或由編譯器推斷。例如說，每個數字可以被指定為複數 `Complex` 或實數 `Real` ，而在實數中又可以指定為整數 `Int` 或浮點數 `Float64`。

```Julia
julia> a = 2 # here a is a int
julia> b = 2.0 # here b is a float
```

雖然在程式中可以改變變數的值（畢竟它是「變」數），但保持變數的類型穩定是一個良好的程式設計習慣，同時對程式效能也非常重要。

例如說，如果我們先將 `a` 指定為 `a = 42` 這樣的值（ `Int` 類型），那麼之後最好不要再給它一個無法不損失資訊地轉換成整數的新值，例如
`a = 0.42`（ `Float64` 類型），因為如果將 `Float64` 轉換為 `Int` ，小數部分會被截斷。

如果我們知道某個變數之後會需要儲存 `Float64` 類型的值，那麼最好一開始就將它指定為屬於該類型的值。


如果想要知道某個變數的類型，可以使用 `typeof` :

```Julia
julia> typeof(0.1)
Float64

julia> typeof(42)
Int64

julia> typeof("NCU")
String
```

如果有需要，我們可以使用 `convert` 來將一個值從一種類型轉換為另一種類型，例如：

```Julia
julia> convert(Float64, 2)
2.0

julia> a = 2
2

julia> b = convert(Float64, a)
2.0
```


