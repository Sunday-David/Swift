

# 简介

- Swift 学习笔记 + 练习代码。

- 参考资料：
  - [Swift 官方文档](https://docs.swift.org/swift-book/)
  - [cnSwift 翻译组](https://www.cnswift.org)
  - [SwiftGG 翻译组](https://swiftgg.gitbook.io/swift/)


# 开始使用 Swift
## Swift 的一些特性
- 运行设备：手机，台式机，服务器

- 支持代码预览（playgrounds），不编译和运行 Swift 代码，实时查看结果
- 采用现代编程模式，避免编程错误：
  - 变量始终在使用前初始化。
  
  - 检查数组索引超出范围的错误。
  - 检查整数是否溢出。
  - 可选值确保明确处理 nil 值。
  - 内存被自动管理。
  - 错误处理允许从意外故障控制恢复。

## 版本兼容性
-  Xcode 12 默认 Swift 版本 Swift 5.3
-  可以使用 Xcode 12 来构建 Swift 5.3、Swift 4.2 或 Swift 4 写的项目

-  使用 Xcode 12 构建 Swift 4 和 Swift 4.2 代码时，Swift 5.3 的大多数功能都适用。但以下功能仅支持 Swift 5.3 或更高版本:
    - 返回值是不透明类型的函数依赖 Swift 5.1 运行时；
    - try? 表达式不会为已返回可选类型的代码引入额外的可选类型层级。
    - 大数字的整型字面量初始化代码的类型将会被正确推导，例如 UInt64(0xffff_ffff_ffff_ffff) 将会被推导为整型类型而非溢出。

## Swift 之旅
- 国际惯例

```swift
 print("Hello, world!")
```
- 无需在代码结尾写分号
- 无需为输入输出函数，或字符串处理导入一个库
- 无需写 main() 函数，全局作用域中的代码会被自动当做程序的入口点

### 简单值
- 使用 let 声明常量，使用 var 来声明变量

- 常量只能赋值一次，变量可多次赋值
- 常量或者变量的类型必须和赋给它的值一样
- 声明时，要么标注类型，要么赋值（编译器自动推断其类型）
- 值永远不会被隐式转换为其他类型（需要把一个值转换成其他类型，要显式转换）
```Swift
let label = "The width is"
let width = 94
let widthLabel = label + String(width)
```
- 把值转换成字符串的简便方法：在双引号里面，把值写到括号中，并且在括号之前写一个反斜杠（\）。
- 字符串拼接，直接用加号“+”（本质是运算符重载，@inlinable public static func + (lhs: String, rhs: String) -> String）
---
- 使用三个双引号（"""）来包含多行字符串
- 每行行首的缩进会被去除，直到和结尾引号的缩进相匹配

```Swift
let quotation = """
I said "I have \(apples) apples."
And then I said "I have \(apples + oranges) pieces of fruit."
"""
```
---
- 数组和字典，都用方括号[]创建
- 最后一个元素后面允许有个逗号
- var=可变数组,let=不可变数组,字典同理

```Swift
var occupations = [
    "Malcolm": "Captain",
    "Kaylee": "Mechanic",
]
```
- 类型不确定, 创建空数组/空字典, \[type]()

```Swift
let emptyArray = [String]()
let emptyDictionary = [String: Float]()
```
- 类型确定, 给变量赋新值, 或者给函数传参数

```Swift
shoppingList = []
occupations = [:]
```
---

### 控制流
- 包裹条件和循环变量的括号可以省略,但语句体的大括号是必须的
- if 语句中，条件必须是一个【布尔表达式】（不会隐形地与 0 做对比）


### 函数和闭包
### 对象和类
### 枚举和结构体
### 协议和扩展
### 错误处理
### 泛型

## Swift 版本修订记录
[cnSwift](https://www.cnswift.org/document-revision-history)

[SwiftGG](https://swiftgg.gitbook.io/swift/huan-ying-shi-yong-swift/04_revision_history)

[Apple官方](https://docs.swift.org/swift-book/RevisionHistory/RevisionHistory.html)

# Swift 教程
## 基础部分
- Swift 增加了 Objective-C 中没有的高阶数据类型比如元组（Tuple），可用于多返回值的函数。

- Swift 还增加了可选（Optional）类型，用于处理值缺失的情况，它可以用在任何类型上，不仅仅是类。
- Swift 是【类型安全】的语言，可在开发阶段尽早发现并修正错误。

---
### 常量和变量

- 场景：无需多次改变赋值，使用常量；需要多次改变值，使用变量。

- 常量的值一旦设定就不能改变，而变量的值可以随意更改。
### 声明常量和变量
- 用 let 来声明常量，用 var 来声明变量

- 可以在一行中声明多个常量或者多个变量，用逗号隔开：

```Swift
var x = 0.0, y = 0.0, z = 0.0
```

### 类型注解（type annotation）

- 场景：初始值不确定，需要标明数据类型

- 可以在一行中定义多个同样类型的变量，用逗号分割，并在最后一个变量名之后添加类型注解：


```Swift
var red, green, blue: Double
```

> 一般很少写类型注解。在声明常量或者变量赋初始值，Swift 可以推断类型.

### 常量和变量的命名
- 常量和变量名可以包含任何字符，包括 Unicode 字符：

```Swift
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"
```
- 不能包含数学符号，箭头，保留的（或者非法的）Unicode 码位，连线与制表符
- 不能以数字开头，但是可以在常量与变量名的其他地方包含数字。
> 可以使用反引号（`）将关键字包围的方式将其作为名字使用, 应当避免使用关键

### 输出常量和变量
- print(_:separator:terminator:) 函数
- 第一个参数：Any...（可变（数量）参数）
- 第二个参数：分隔符-String，默认值" "
- 第三个参数：终止符-String，默认值"\n" 

---
### 注释
- 单行注释（//）
- 多行注释，/**/
- 多行注释可以嵌套

```Swift
/* 这是第一个多行注释的开头
/* 这是第二个被嵌套的多行注释 */
这是第一个多行注释的结尾 */
```
---
### 分号
- 可用，也可不用
- 一种情况下必须要用分号，即你打算在同一行内写多条独立的语句

```
let cat = "🐱"; print(cat)
```

---
### 整数
- Swift 提供了8、16、32和64位的有符号（正、负、零）和无符号整数类型（正、零）
- 像 Swift 的其他类型一样，整数类型采用大写命名法(capitalized names)。

#### 整数范围
- min 和 max 属性来获取对应类型的最小值和最大值

```Swift
let minValue = UInt8.min  // minValue 为 0，是 UInt8 类型
let maxValue = UInt8.max  // maxValue 为 255，是 UInt8 类型
```

#### Int
- Int，长度与当前平台的原生字长相同：
    - 在32位平台上，Int 和 Int32 长度相同。
    - 在64位平台上，Int 和 Int64 长度相同。
> 这可以提高代码一致性和可复用性

#### UInt
- 在32位平台上，UInt 和 UInt32 长度相同。
- 在64位平台上，UInt 和 UInt64 长度相同。
> 尽量不要使用 UInt, 最好使用 Int, 避免不同类型数字之间的转换

---
### 浮点数

- `Double` 表示64位浮点数，精度至少15位数字。

- `Float` 表示32位浮点数，精度只有6位数字。
  
  > 优先选择 `Double`。

---
### 类型安全和类型推断

- 没有显式指定类型，Swift 会使用*类型推断（type inference）*来选择合适的类型

  ```swift
  let meaningOfLife = 42
  // meaningOfLife 会被推测为 Int 类型
  ```

  ```swift
  let pi = 3.14159
  // pi 会被推测为 Double 类型
  ```

  ```swift
  let anotherPi = 3 + 0.14159
  // anotherPi 会被推测为 Double 类型
  ```

---
### 数值型字面量

- 一个*十进制*数，没有前缀

- 一个*二进制*数，前缀是 `0b`

- 一个*八进制*数，前缀是 `0o`

- 一个*十六进制*数，前缀是 `0x`

  ```swift
  let decimalInteger = 17
  let binaryInteger = 0b10001       // 二进制的17
  let octalInteger = 0o21           // 八进制的17
  let hexadecimalInteger = 0x11     // 十六进制的17	
  ```

  
  
  十进制数的指数为 `exp`，那这个数相当于基数和10^exp 的乘积：
  
- `1.25e2` 表示 1.25 × 10^2，等于 `125.0`。

- `1.25e-2` 表示 1.25 × 10^-2，等于 `0.0125`。

  

十六进制数的指数为 `exp`，那这个数相当于基数和2^exp 的乘积

- `0xFp2` 表示 15 × 2^2，等于 `60.0`。
- `0xFp-2` 表示 15 × 2^-2，等于 `3.75`。



- 整数和浮点数, 都可添加额外的零、下划线

  ```swift
  let paddedDouble = 000123.456
  let oneMillion = 1_000_000
  let justOverOneMillion = 1_000_000.000_000_1
  ```

  

---
### 数值型类型转换

#### 整数转换

- `Int8`  存储数字范围-128`~`127

- `UInt8` 存储数字范围0`~`255

  ```swift
  let cannotBeNegative: UInt8 = -1
  // UInt8 类型不能存储负数，所以会报错
  let tooBig: Int8 = Int8.max + 1
  // Int8 类型不能存储超过最大值的数，所以会报错
  ```

  ```swift
  let twoThousand: UInt16 = 2_000
  let one: UInt8 = 1
  let twoThousandAndOne = twoThousand + UInt16(one)
  ```

  > - `SomeType(ofInitialValue)` 是调用 Swift 构造器并传入一个初始值的默认方法。
  >
  > - 不能传入任意类型的值，只能传入 `UInt16` 内部有对应构造器的值。可以扩展现有的类型, 让它可以接收其他类型的值（包括自定义类型）。请参考 [扩展](#扩展构造器)。

#### 整数和浮点数转换

```swift
let integerPi = Int(pi)
// integerPi 等于 3，所以被推测为 Int 类型
```

- 浮点值会被截断。也就是说 `4.75` 会变成 `4`，`-3.9` 会变成 `-3`。

  > 结合数字类常量和变量不同于结合数字类字面量, 字面量 `3` 可以直接和字面量 `0.14159` 相加，因为数字字面量本身没有明确的类型。它们的类型只在编译器需要求值的时候被推测。

---
### 类型别名

- 使用 `typealias` 关键字来定义类型别名。

  ```swift
  typealias AudioSample = UInt16
  ```

  

---
### 布尔值

- 区别于C和OC，Swift的布尔类型为一种单独类型，更加安全和更高的可读性

- Swift 有一个基本的*布尔（Boolean）类型*，叫做 `Bool`

- Swift 有两个布尔常量，`true` 和 `false`

  ```swift
  let orangesAreOrange = true
  let turnipsAreDelicious = false	
  ```

- 使用非布尔值，Swift 的类型安全机制会报错

```swift
let i = 1
if i {
    // 这个例子不会通过编译，会报错
}
```

- 合法的：

  ```swift
  let i = 1
  if i == 1 {
      // 这个例子会编译成功
  }
  ```

  

---
### 元组（tuples）

- 场景：可将不同数据类型，但同一个功能业务接口的数据，集合在一起

- 元组内的值可以是任意类型，并不要求是相同类型。

  ```swift
  let http404Error = (404, "Not Found")
  // http404Error 的类型是 (Int, String)，值是 (404, "Not Found")
  ```

- 将一个元组的内容分解（decompose）成单独的常量和变量

```swift
let (statusCode, statusMessage) = http404Error
print("The status code is \(statusCode)")
// 输出“The status code is 404”
print("The status message is \(statusMessage)")
// 输出“The status message is Not Found”
```

- 用下划线（`_`）,忽略不需要的值

  ```swift
  let (justTheStatusCode, _) = http404Error
  print("The status code is \(justTheStatusCode)")
  // 输出“The status code is 404”
  ```

- 下标访问（下标从零开始）

  ```swift
  print("The status code is \(http404Error.0)")
  // 输出“The status code is 404”
  print("The status message is \(http404Error.1)")
  // 输出“The status message is Not Found”
  ```

- 定义元祖-给元素命名

```swift
let http200Status = (statusCode: 200, description: "OK")
```

- 命名后的访问

```swift
print("The status code is \(http200Status.statusCode)")
// 输出“The status code is 200”
print("The status message is \(http200Status.description)")
// 输出“The status message is OK”
```

- 使用场景：函数的 多个返回值。[ 函数参数与返回值]（#函数参数与返回值）

> 元组不适合创建复杂数据结构, 可用类或结构体去建模。

---
### 可选类型

- 场景：表示该变量/常量，可能有值，可能没值

- *可选类型（optionals）*处理值可能缺失

> - C 和 Objective-C 没有可选类型这个概念, OC对象用nil，基本数据类型用特殊值（比如 `NSNotFound`）
> - Swift 的可选类型，适用于任意类型

```swift
let possibleNumber = "123"
let convertedNumber = Int(possibleNumber)
// convertedNumber 被推测为类型 "Int?"， 或者类型 "optional Int"
```

- 因构造器可能会失败，所以返回*可选类型*（optional）`Int`，而不是 `Int`。
- 问号暗示表示值为可选类型，可能包含 `Int` 值，可能*不包含值*。（不能包含其他类型值，如 `Bool` 值或 `String` 值。只能是 `Int` ，或什么都没有。）

#### nil

- 场景：可选类型的一个值，表示没有值/值缺失

- 可以给可选变量赋值为 `nil` 来表示它没有值：

```swift
var serverResponseCode: Int? = 404
// serverResponseCode 包含一个可选的 Int 值 404
serverResponseCode = nil
// serverResponseCode 现在不包含值
```

> 非可选类型的常量和变量，不能赋值nil。

- 声明一个可选常量或者变量但是没有赋值，它们会自动被设置为 `nil`：

```swift
var surveyAnswer: String?
// surveyAnswer 被自动设置为 nil
```

> Swift和OC的nil的区别：
>
> - OC ，nil为指针, 指向不存在的对象（只能用于对象类型，不能基本数据类型）
> - Swift，nil是一个值（能用于任意类型）

#### if 语句 +  强制解析

- 场景：只判断可选项是否为空值，不解包

- `if` 语句和 `nil` 比较来判断一个可选值是否包含值

- 使用“相等”(`==`)或“不等”(`!=`)来执行比较

- 可选类型有值，它将不等于 `nil`：

- ```swift
  if convertedNumber != nil {
      print("convertedNumber contains some integer value.")
  }
  // 输出“convertedNumber contains some integer value.”
  ```

- 强制解析/解包（forced unwrapping）：确定有值，可在后面加一个感叹号（`!`）取值。

> 如果没有值，强制解包会报运行时错误.

```swift
if convertedNumber != nil {
    print("convertedNumber has an integer value of \(convertedNumber!).")
}
// 输出“convertedNumber has an integer value of 123.”
```



#### 可选绑定（optional binding）

- 场景：判断可选类型是否有值，并解包使用

- 可选绑定：判断是否有值 --> 有值 --> 解包 + 赋值到常量/变量
- if 和 while 都可以

```swift
// MARK:- 可选绑定 - if
if let atualNumber = Int(possibleNumber) {
    print("if - Int()转换成功, \(atualNumber)")
} else {
    print("if - Int()转换失败")
}

// MARK:- 可选绑定 - while
while let atualNumber = Int(possibleNumber1) {
    print("while - Int()转换成功, \(atualNumber)")
}
```

- 一个 `if` 语句，可包含多个可选绑定或多个布尔条件，用逗号隔开
- 任一可选绑定的值为 `nil`，或任一布尔条件为 `false`，整个 `if` 条件判断为 `false`

```swift
// MARK:- 可选绑定和布尔条件混用
if let firstNumber = Int("4"),
   let secondNumber = Int("42"),
   firstNumber < secondNumber && secondNumber < 100  {
    
    print("--------------------")
    print("\(firstNumber) < \(secondNumber) < 100")
    print("--------------------")
}

// MARK:- 等价于上面
if let firstNumber = Int("4") {
    if let secondNumber = Int("42") {
        if firstNumber < secondNumber && secondNumber < 100 {
            
            print("--------------------")
            print("\(firstNumber) < \(secondNumber) < 100")
            print("--------------------")
        }
    }
}
```

> - if 条件语句创建可选绑定，if 语句中（`body`）中才能获取到值
> - `guard` 语句中创建一个可选绑定，在 `guard` 语句外且在语句后才能获取到值

#### 隐式解析可选类型/隐式解包（implicitly unwrapped optionals）

- 场景：变量/常量明确有值时，减少判断，自动强制解包/解析，提高效率
- 声明方式：可选的类型的后面的问号（`String?`）改成感叹号（`String!`）（相当于把强制解包操作，提前使用）
- 隐式解析可选类型，主要被用在 Swift 中类的构造过程中，请参考 [无主引用以及隐式解析可选属性](#无主引用和隐式解包可选值属性)。

```swift
// MARK:- 可选类型 String 和隐式解析可选类型 String 之间的区别
let possibleString: String? = "An optional string."
let forcedString: String = possibleString! // 需要感叹号来获取值

let possibleString1: String! = "An optional string."
// possibleString1 = nil  // 保留可选类型,可以为nil的特性
let forcedString1: String = possibleString1 // 不需要感叹号
```

```swift
// MARK:- 隐式可选项 -  判断是否有值(跟普通可选类型一样)
if possibleString1  !=  nil {
    print(possibleString1!)
}

// MARK:- 隐式可选项 -  可选项绑定 (跟普通可选类型一样)
if let definiteString =  possibleString1 {
    print(definiteString)
}
```

---
### 错误处理（error handling）



---
### 断言和先决条件
#### 使用断言进行调试
#### 强制执行先决条件

# 基本运算符（Basic Operators）

- 赋值符（`=`）不再有返回值。(避免了手误将（`==`）写成（`=`）不报错的问题)
- 算术运算符（`+`，`-`，`*`，`/`，`%` 等）的结果，会被检查是否值溢出（[实现允许溢出](#溢出运算符)）
- Swift 提供 C 没有的区间运算符，如 `a..<b` 或 `a...b`，表达一个区间内的数值
- 本章节只讲基本运算符，自定义运算符、运算符重载请看[高级运算符](#高级运算符)

## 术语（Terminology）

- *一元*运算符（操作一个目标）
  - 前置运算符：如 `!b`
  - 后置运算符：如 `c!`
- *二元*运算符（操作两个目标）
  - 如 `2 + 3`
- *三元*运算符（操作三个目标）
  - 和 C 语言一样，Swift 只有一个三元运算符，就是三目运算符（`a ? b : c`）

---
## 赋值运算符(Assignment Operator)

- 赋值元祖

```swift
let (x, y) = (1, 2)
// 现在 x 等于 1，y 等于 2
```

- 与 C 语言和 Objective-C 不同，Swift 的赋值操作并不返回任何值
- 避免把 （`==`）错写成（`=`）这类错误的出现

```swift
if x = y {
    // 此句错误，因为 x = y 并不返回任何值
}
```



---
## 算术运算符(Arithmetic Operators)

- （所有数值类型）都支持了四则*算术运算符*
  - 加法（`+`）
  - 减法（`-`）
  - 乘法（`*`）
  - 除法（`/`）
- 加法运算符也可用于 `String` 的拼接：

```swift
"hello, " + "world"  // 等于 "hello, world"
```



### 求余运算符

- 求余(remainder)运算符（`%`）在其他语言也叫*取模(*modulo*)运算符*

```swift
9 % 4    // 等于 1
```

```swift
-9 % 4   // 等于 -1
```

- 对负数 `b` 求余时，`b` 的符号会被忽略。这意味着 `a % b` 和 `a % -b` 的结果是相同的

### 一元负号运算符

```swift
let three = 3
let minusThree = -three       // minusThree 等于 -3
let plusThree = -minusThree   // plusThree 等于 3, 或 "负负3" = 3
```

### 一元正号运算符

```swift
let minusSix = -6
let alsoMinusSix = +minusSix  // alsoMinusSix 等于 -6
```

---
## 组合赋值运算符

- 组合加运算（`+=`）

```swift
var a = 1
a += 2
// a 现在是 3
```

> 复合赋值运算没有返回值，`let b = a += 2` 这类代码是错误

更多 Swift 标准库运算符的信息，请看 [运算符声明](https://developer.apple.com/documentation/swift/operator_declarations)。 ‌

---
## 比较运算符（Comparison Operators）

支持以下的比较运算符：

- 等于（`a == b`）
- 不等于（`a != b`）
- 大于（`a > b`）
- 小于（`a < b`）
- 大于等于（`a >= b`）
- 小于等于（`a <= b`）

```swift
let name = "world"
if name == "world" {
    print("hello, world")
} else {
    print("I'm sorry \(name), but I don't recognize you")
}
// 输出“hello, world", 因为 `name` 就是等于 "world”
```

- 字符串相等判断使用 ==（OC中==，表示两个对象的指针变量指向的地址相同）

---
## 三元运算符（Ternary Conditional Operator）

- 问题 ? 答案 1 : 答案 2
- 缩写形式：

```swift
if question {
    answer1
} else {
    answer2
}
```

- 滥用三元运算符会降低代码可读性，避免在一个复合语句中使用多个三元运算符。

---
## 空合并运算符（Nil Coalescing Operator）

- 场景：设置/返回 可选类型数据没有值/nil时的默认值

- *空合运算符*（`a ?? b`）, a有值就解包，否则返回默认值b。
- a必须是Optional类型，b跟a的存储类型一样（a有值解包后的类型）
- 等价于以下三元运算符的代码：

```swift
a != nil ? a! : b
```

> 如果 `a` 为非空值（`non-nil`），那么值 `b` 将不会被计算。这也就是所谓的*短路求值*。

---
## 区间运算符（Range Operators）

- 几种方便表达一个区间的值的*区间运算符*。

### 闭区间运算符(Closed Range Operator)

- 场景：索引不算0/不是从0开始的情况

- *闭区间运算符*（`a...b`）定义一个包含从 `a` 到 `b`（包括 `a` 和 `b`）的所有值的区间。`a` 的值不能超过 `b`。
- 遍历/迭代

```swift
for index in 1...5 {
    print("\(index) * 5 = \(index * 5)")
}
// 1 * 5 = 5
// 2 * 5 = 10
// 3 * 5 = 15
// 4 * 5 = 20
// 5 * 5 = 25
```



### 半开区间运算符(Half-Open Range Operator)

- 场景：算0的情况

- *半开区间运算符*（`a..<b`）定义一个从 `a` 到 `b` 但不包括 `b` 的区间

```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
for i in 0..<count {
    print("第 \(i + 1) 个人叫 \(names[i])")
}
// 第 1 个人叫 Anna
// 第 2 个人叫 Alex
// 第 3 个人叫 Brian
// 第 4 个人叫 Jack
```



### 单侧区间(One-Sided Ranges)

- 场景：某个元素开始，到最后一个元素结束

- 一侧无限延伸

```swift
for name in names[2...] {
    print(name)
}
// Brian
// Jack

for name in names[...2] {
    print(name)
}
// Anna
// Alex
// Brian
```

- 半开区间操作符也有单侧表达形式

```swift
for name in names[..<2] {
    print(name)
}
// Anna
// Alex
```

- 单侧区间可以在下标里使用
- 查看一个单侧区间是否包含某个特定的值

```swift
let range = ...5
range.contains(7)   // false
range.contains(4)   // true
range.contains(-1)  // true
```



---
## 逻辑运算符（Logical Operators）

- 逻辑运算符操作(修改或合并) 布尔逻辑值 true 和 false
- 与C语言一致
  - 逻辑非（`!a`）
  - 逻辑与（`a && b`）
  - 逻辑或（`a || b`）

### 逻辑非运算符（Logical NOT Operator）

- 直接写在要进行运算的值前边，不加空格，读作 `非 a`

```swift
let allowedEntry = false
if !allowedEntry {
    print("ACCESS DENIED")
}
// 输出“ACCESS DENIED”
```

- 避免使用双重逻辑非运算，或混乱的逻辑语句。

### 逻辑与运算符（Logical AND Operator）

- （`a && b`）表达了只有 `a` 和 `b` 的值都为 `true`

- 如果第一个值为 `false`，那么是不去计算第二个值的，因为它已经不可能影响整个表达式的结果了。这被称做*短路计算（short-circuit evaluation）*。

### 逻辑或运算符（Logical OR Operator）

- 逻辑或运算符（`a || b`）是一个由两个连续的 `|` 组成的中置运算符
- 逻辑或也是「短路计算」的，当左端的表达式为 `true` 时，将不计算右边的表达式了，因为它不可能改变整个表达式的值了。

### 逻辑运算符组合计算（Combining Logical Operators）

```swift
if enteredDoorCode && passedRetinaScan || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// 输出“Welcome!”
```

- 如果我们输入了正确的密码并通过了视网膜扫描，或者我们有一把有效的钥匙，又或者我们知道紧急情况下重置的密码，我们就能把门打开进入。

> Swift 逻辑操作符 `&&` 和 `||` 是左结合的，这意味着拥有多元逻辑操作符的复合表达式，优先计算最左边的子表达式。

### 使用括号来明确优先级(Explicit Parentheses)

- 使用括号来明确优先级，增加代码可读性

```swift
if (enteredDoorCode && passedRetinaScan) || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// 输出“Welcome!”
```



---

# 字符串和字符

- *字符串* String是字符Character的集合
- 通过 `+` 符号就可拼接两个字符串
- 能否更改字符串的值，取决于其被定义为常量还是变量

> Swift 的 `String` 类型与 Foundation `NSString` 类进行了无缝桥接。调用 `NSString` 的方法，无需进行类型转换。
>
> 
>
> 更多关于在 Foundation 和 Cocoa 中使用 `String` 的信息请查看 [*Bridging Between String and NSString*](https://developer.apple.com/documentation/swift/string#2919514)。

## 字符串字面量

- 字符串字面量作为常量或者变量的初始值：

```swift
let someString = "Some string literal value"
```

### 多行字符串字面量

- 用三个双引号引起来的一系列字符

```swift
let quotation = """
The White Rabbit put on his spectacles.  "Where shall I begin,
please your Majesty?" he asked.
 
"Begin at the beginning," the King said gravely, "and go on
till you come to the end; then stop."
"""
```

- 为代码可读性，可在代码里加反斜杠（`\`），对字符串换行（输出的字符串不换行, 且没有反斜杠）

```swift
let softWrappedQuotation = """
The White Rabbit put on his spectacles.  "Where shall I begin, \
please your Majesty?" he asked.

"Begin at the beginning," the King said gravely, "and go on \
till you come to the end; then stop."
"""
```

- 可以在代码中，使用缩进，让代码工整对齐，但字符串里不会有影响

![](https://docs.swift.org/swift-book/_images/multilineStringWhitespace_2x.png)

- 如果你在某行的空格超过了结束的双引号（ """ ），那么这些空格*会*被包含。

### 字符串字面量的特殊字符

- 转义特殊字符  \0 (空字符)， \\ (反斜杠)， \t (水平制表符)， \n (换行符)， \r(回车符)， \" (双引号) 以及 \' (单引号)

- Unicode 标量，写成 `\u{n}`(u 为小写)，其中 `n` 为任意一到八位十六进制数且可用的 Unicode 位码

```swift
let wiseWords = "\"Imagination is more important than knowledge\" - Einstein"
// "Imageination is more important than knowledge" - Enistein
let dollarSign = "\u{24}"             // $，Unicode 标量 U+0024
let blackHeart = "\u{2665}"           // ♥，Unicode 标量 U+2665
let sparklingHeart = "\u{1F496}"      // 💖，Unicode 标量 U+1F496
```

- 多行字符串, 直接使用双引号（`"`）而不必加上转义符（`\`）
- 多行字符串字面量中使用 `"""`, 使用至少一个转义符（`\`）

```swift
let threeDoubleQuotes = """
Escaping the first quote \"""
Escaping all three quotes \"\"\"
"""
```

### 扩展字符串分隔符
- 井号（ # ）包裹，可以使特殊字符不生效

```swift
#"Line 1\nLine 2"#
```

- 使某个特殊字符生效，使用#号标记

```swift
#"Line 1\#nLine 2"#
```

```swift
###"Line1\###nLine2"###
```

- 多行字符串，包含"""

```swift
let threeMoreDoubleQuotationMarks = #"""
Here are three more double quotes: """
"""#
```

## 初始化空字符串

```swift
var emptyString = ""               // 空字符串字面量
var anotherEmptyString = String()  // 初始化方法
// 两个字符串均为空并等价。
```

- 通过检查 `Bool` 类型的 `isEmpty` 属性来判断该字符串是否为空

```swift
if emptyString.isEmpty {
    print("Nothing to see here")
}
// 打印输出：“Nothing to see here”
```

## 字符串可变性

```swift
var variableString = "Horse"
variableString += " and carriage"
// variableString 现在为 "Horse and carriage"

let constantString = "Highlander"
constantString += " and another Highlander"
// 这会报告一个编译错误（compile-time error） - 常量字符串不可以被修改。
```

## 字符串是值类型

- Swift 中 `String` 类型是*值类型*

- 如果你创建了一个新的字符串，那么当其进行常量、变量赋值操作，或在函数/方法中传递时，会进行值拷贝。

## 使用字符

- `for-in` 循环来遍历, 获取字符串中每一个字符的值

```swift
for character in "Dog!🐶" {
    print(character)
}
// D
// o
// g
// !
// 🐶
```

- `Character` 类型

```swift
let exclamationMark: Character = "!"
```

- 字符串可通过值类型为 `Character` 的数组来初始化

```swift
let catCharacters: [Character] = ["C", "a", "t", "!", "🐱"]
let catString = String(catCharacters)
print(catString)
// 打印输出：“Cat!🐱”
```



## 连接字符串和字符

- 通过加法运算符（`+`）相加在一起（或称“连接”）创建一个新的字符串：

```swift
let string1 = "hello"
let string2 = " there"
var welcome = string1 + string2
// welcome 现在等于 "hello there"
```

- 通过加法赋值运算符（`+=`）将一个字符串, 添加到另一个字符串变量上：

```swift
var instruction = "look over"
instruction += string2
// instruction 现在等于 "look over there"
```

> 你不能把 String或者 Character追加到已经存在的 Character变量当中，因为 Character值能且只能包含一个字符。

## 字符串插值

- *字符串插值*：在字符串中插入 常量、变量、字面量、表达式

```swift
let multiplier = 3
let message = "\(multiplier) times 2.5 is \(Double(multiplier) * 2.5)"
// message 是 "3 times 2.5 is 7.5"
```

- 扩展字符串分隔符 使插值符号失效/不生效

```swift
print(#"Write an interpolated string in Swift using \(multiplier)."#)
// 打印 "Write an interpolated string in Swift using \(multiplier)."
```

- 部分生效

```swift
print(#"\(6 * 7)  times  is \#(6 * 7)."#)
// 打印 \(6 * 7)  times  is 42.
```

## Unicode

- Swift 的 `String` 和 `Character` 类型是完全兼容 Unicode 标准的。

### Unicode 标量

- `String` 类型是基于 *Unicode 标量* 建立

- Unicode 标量: 是对应字符或者修饰符的唯一的 21 位数字
- `U+0061` 表示小写的拉丁字母（`LATIN SMALL LETTER A`）（"`a`"）
- `U+1F425` 表示小鸡表情（`FRONT-FACING BABY CHICK`）（"`🐥`"）

```swift
print("\u{0061}")// a
print("--------------------")
print("\u{1F425}")// 🐥
print("--------------------")
```

> Unicode 标量码位位于 U+0000到 U+D7FF或者 U+E000到 U+10FFFF之间。Unicode 标量码位不包括从 U+D800到 U+DFFF的16位码元码位。

- 不是所有的 21 位 Unicode 标量都指定了字符——有些标量是为将来所保留或用于 UTF-16 编码。
- 有了字符的标量通常来说也会有个名字，比如上边例子中的 ` LATIN SMALL LETTER A` 和` FRONT-FACING BABY CHICK `。

### 可扩展的字形群集

- `Character` 类型代表一个*可扩展的字形集*
- 一个可扩展的字形群构成了人类可读的单个字符，它由一个或多个 Unicode 标量的序列组成。

---

- 字母 `é` 代表了一个单一的 Swift 的 `Character` 值, 同时代表了一个可扩展的字形群
- 第一种情况，这个字形群包含一个单一标量
- 第二种情况，它是包含两个标量的字形群

```swift
let eAcute: Character = "\u{E9}"                         // é
let combinedEAcute: Character = "\u{65}\u{301}"          // e 后面加上  ́
// eAcute 是 é, combinedEAcute 是 é
```

---

- 可扩展的字形集:  是一个将许多复杂的脚本字符, 表示为单个字符值的灵活方式

- 朝鲜语字母表的韩语音节能表示为组合或分解的有序排列

```swift
let precomposed: Character = "\u{D55C}"                  // 한
let decomposed: Character = "\u{1112}\u{1161}\u{11AB}"   // ᄒ, ᅡ, ᆫ
// precomposed 是 한, decomposed 是 한
```

---

- 扩展字形集群允许封闭标记的标量 (比如 COMBINING ENCLOSING CIRCLE, 或者说 U+20DD) 作为单一 Character值来圈住其他 Unicode 标量：

```swift
let enclosedEAcute: Character = "\u{E9}\u{20DD}"
// enclosedEAcute 是 é⃝
```

---

- 区域指示符号的 Unicode 标量可以成对组合来成为单一的 Character值，比如说这个 REGIONAL INDICATOR SYMBOL LETTER U ( U+1F1FA)和 REGIONAL INDICATOR SYMBOL LETTER S (U+1F1F8)：

```swift
let regionalIndicatorForUS: Character = "\u{1F1FA}\u{1F1F8}"
// regionalIndicatorForUS 是 🇺🇸
```



## 计算字符数量/字符统计

- Character值的总数，使用字符串的 count属性

```swift
let unusualMenagerie = "Koala 🐨, Snail 🐌, Penguin 🐧, Dromedary 🐪"
print("unusualMenagerie has \(unusualMenagerie.count) characters")
// 打印输出“unusualMenagerie has 40 characters”
```

> 注意: 使用可拓展的字符群集作为 `Character` 值来连接或改变字符串时，并不一定会更改字符串的字符数量。

```swift
var word = "cafe"
print("the number of characters in \(word) is \(word.count)")
// 打印输出“the number of characters in cafe is 4”

word += "\u{301}"    // 拼接一个重音，U+0301

print("the number of characters in \(word) is \(word.count)")
// 打印输出“the number of characters in café is 4”			
```

> - 扩展字形集群能够组合一个或者多个 Unicode 标量。这意味着不同的字符——以及相同字符的不同表示——能够获得不同大小的内存来储存. 特殊的长字符串值，要注意 count属性为了确定字符串中的字符要遍历整个字符串的 Unicode 标量。
> - `count` 属性返回的字符数量并不总是与包含相同字符的 `NSString` 的 `length` 属性相同
> - `NSString` 的 `length` 属性是利用 UTF-16 表示的十六位代码单元数字，而不是 Unicode 可扩展的字符群集

## 访问和修改字符串

- 通过字符串的属性和方法来访问和修改它，当然也可以用下标语法完成

### 字符串索引

- 每一个 `String` 值都有一个关联的索引（*index*）类型，`String.Index`，它对应着字符串中的每一个 `Character` 的位置
- 使用 startIndex属性来访问 String中第一个 Character的位置
- endIndex属性就是 String中最后一个字符后的位置
- endIndex属性并不是字符串下标脚本的合法实际参数。如果String为空，则 startIndex与 endIndex相等。
- 用 index(before:) 和 index(after:) 方法来访问给定索引的前后
- 给定索引更远的索引，你可以使用 index(_:offsetBy:) 方法

```swift
let greeting = "Guten Tag!"
greeting[greeting.startIndex]
// G
greeting[greeting.index(before: greeting.endIndex)]
// !
greeting[greeting.index(after: greeting.startIndex)]
// u
let index = greeting.index(greeting.startIndex, offsetBy: 7)
greeting[index]
// a
```

- 获取越界索引对应的 `Character`，将引发一个运行时错误。

```swift
greeting[greeting.endIndex] // error
greeting.index(after: greeting.endIndex) // error
```

- 用 `indices` 属性会创建一个包含全部索引的范围（`Range`）

```swift
for index in greeting.indices {
   print("\(greeting[index]) ", terminator: "")
}
// 打印输出“G u t e n   T a g ! ”
```

> 可以在任何遵循了 Collection 协议的类型中使用 startIndex 和 endIndex 属性以及 index(before:) ，index(after:) 和 index(_:offsetBy:) 方法。这包括这里使用的 String ，还有集合类型比如 Array ，Dictionary 和 Set

### 插入和删除

- 特定位置插入字符，使用 insert(_:at:)方法
- 插入一个段字符串, 调用 `insert(contentsOf:at:)` 方法

```swift
var welcome = "hello"
welcome.insert("!", at: welcome.endIndex)
// welcome 变量现在等于 "hello!"

welcome.insert(contentsOf:" there", at: welcome.index(before: welcome.endIndex))
// welcome 变量现在等于 "hello there!"
```

- 移除字符，使用 remove(at:)方法
- 移除一小段字符串，removeSubrange(_:) 

```swift
welcome.remove(at: welcome.index(before: welcome.endIndex))
// welcome 现在等于 "hello there"

let range = welcome.index(welcome.endIndex, offsetBy: -6)..<welcome.endIndex
welcome.removeSubrange(range)
// welcome 现在等于 "hello"	
```

> 任意一个确认的并遵循 `RangeReplaceableCollection` 协议的类型里面，可使用 `insert(_:at:)`、`insert(contentsOf:at:)`、`remove(at:)` 和 `removeSubrange(_:)` 方法, 在如上文用在 `String` 中，也用在 `Array`、`Dictionary` 和 `Set` 

### 子字符串

- 使用下标或者 `prefix(_:)` 之类的方法 —— 就可以得到一个 `Substring` 的实例，而非另外一个 `String`
- `Substring` 绝大部分函数都跟 `String` 一样
- 与字符串不同，在字符串上执行动作的话你应该使用子字符串执行短期处理。当你想要把结果保存得长久一点时，你需要把子字符串转换为 String 实例

```swift
let greeting = "Hello, world!"
let index = greeting.index(of: ",") ?? greeting.endIndex
let beginning = greeting[..<index]
// beginning is "Hello"
 
// Convert the result to a String for long-term storage.
let newString = String(beginning)
```

- `Substring` 可以重用原 `String` 的内存空间，或者另一个 `Substring` 的内存空间
- `newString` 是一个 `String` —— 它是使用 `Substring` 创建的，拥有一片自己的内存空间。

![img](https://docs.swift.org/swift-book/_images/stringSubstring_2x.png)

> `String` 和 `Substring` 都遵循 [`StringProtocol`](https://developer.apple.com/documentation/swift/stringprotocol) 协议，这意味着操作字符串的函数使用 `StringProtocol` 会更加方便。你可以传入 `String` 或 `Substring` 去调用函数

## 比较字符串

三种方式比较文本值：字符串字符相等、前缀相等和后缀相等。

### 字符串/字符相等

```swift
let quotation = "We're a lot alike, you and I."
let sameQuotation = "We're a lot alike, you and I."
if quotation == sameQuotation {
    print("These two strings are considered equal")
}
// 打印输出“These two strings are considered equal”
```

- 两个字符串（或者两个字符）的可扩展的字形群集是标准相等，那它们是相等的, 
- 只要可扩展的字形群集有同样的语言意义和外观, 即使它们是由不同的 Unicode 标量构成

---

- 如，`LATIN SMALL LETTER E WITH ACUTE`(`U+00E9`)就是标准相等于 `LATIN SMALL LETTER E`(`U+0065`)后面加上 `COMBINING ACUTE ACCENT`(`U+0301`)

```swift
// "Voulez-vous un café?" 使用 LATIN SMALL LETTER E WITH ACUTE
let eAcuteQuestion = "Voulez-vous un caf\u{E9}?"

// "Voulez-vous un café?" 使用 LATIN SMALL LETTER E and COMBINING ACUTE ACCENT
let combinedEAcuteQuestion = "Voulez-vous un caf\u{65}\u{301}?"

if eAcuteQuestion == combinedEAcuteQuestion {
    print("These two strings are considered equal")
}
// 打印输出“These two strings are considered equal”
```

- 相反，英语中的 `LATIN CAPITAL LETTER A`(`U+0041`，或者 `A`)不等于俄语中的 `CYRILLIC CAPITAL LETTER A`(`U+0410`，或者 `A`)。两个字符看着是一样的，但却有不同的语言意义：

```swift
let latinCapitalLetterA: Character = "\u{41}"

let cyrillicCapitalLetterA: Character = "\u{0410}"

if latinCapitalLetterA != cyrillicCapitalLetterA {
    print("These two characters are not equivalent")
}
// 打印“These two characters are not equivalent”
```

> 在 Swift 中，字符串和字符并不区分地域（not locale-sensitive）。

### 前缀/后缀相等

- `hasPrefix(_:)`/`hasSuffix(_:)` 方法检查字符串是否有特定前缀/后缀，两个方法均接收一个 `String` 类型的参数，并返回一个布尔值

```swift
let romeoAndJuliet = [
    "Act 1 Scene 1: Verona, A public place",
    "Act 1 Scene 2: Capulet's mansion",
    "Act 1 Scene 3: A room in Capulet's mansion",
    "Act 1 Scene 4: A street outside Capulet's mansion",
    "Act 1 Scene 5: The Great Hall in Capulet's mansion",
    "Act 2 Scene 1: Outside Capulet's mansion",
    "Act 2 Scene 2: Capulet's orchard",
    "Act 2 Scene 3: Outside Friar Lawrence's cell",
    "Act 2 Scene 4: A street in Verona",
    "Act 2 Scene 5: Capulet's mansion",
    "Act 2 Scene 6: Friar Lawrence's cell"
]
```

- 用 `hasPrefix(_:)` 方法来计算话剧中第一幕的场景数：

```swift
var act1SceneCount = 0
for scene in romeoAndJuliet {
    if scene.hasPrefix("Act 1 ") {
        act1SceneCount += 1
    }
}
print("There are \(act1SceneCount) scenes in Act 1")
// 打印输出“There are 5 scenes in Act 1”
```

- 用 `hasSuffix(_:)` 方法来计算发生在不同地方的场景数：

```swift
var mansionCount = 0
var cellCount = 0
for scene in romeoAndJuliet {
    if scene.hasSuffix("Capulet's mansion") {
        mansionCount += 1
    } else if scene.hasSuffix("Friar Lawrence's cell") {
        cellCount += 1
    }
}
print("\(mansionCount) mansion scenes; \(cellCount) cell scenes")
// 打印输出“6 mansion scenes; 2 cell scenes”
```

## 字符串的 Unicode 表示形式

- 一个 Unicode 字符串被写进文本文件或者其他储存时，字符串中的 Unicode 标量会用 Unicode 定义的几种 `编码格式`（encoding forms）编码
- 每一个字符串中的小块编码都被称 `代码单元`（code units）, 包括 UTF-8 编码格式（编码字符串为 8 位的代码单元）， UTF-16 编码格式（编码字符串位 16 位的代码单元），以及 UTF-32 编码格式（编码字符串32位的代码单元）

- 访问字符串的 Unicode 表示形式, 利用 `for-in` 来对字符串进行遍历
- 其他三种 Unicode 兼容的方式访问字符串的值
  - UTF-8 代码单元集合（利用字符串的 `utf8` 属性进行访问）
  - UTF-16 代码单元集合（利用字符串的 `utf16` 属性进行访问）
  - 21 位的 Unicode 标量值集合，也就是字符串的 UTF-32 编码格式（利用字符串的 `unicodeScalars` 属性进行访问）
- `D`,`o`,`g`,`‼`(`DOUBLE EXCLAMATION MARK`, Unicode 标量 `U+203C`)和 `🐶`(`DOG FACE`，Unicode 标量为 `U+1F436`)组成的字符串中的每一个字符代表着一种不同的表示

```swift
let dogString = "Dog‼🐶"
```

### UTF-8 表示

- `String` 的 `utf8` 属性可访问它的 `UTF-8` 表示
- 为 `String.UTF8View` 类型的属性，`UTF8View` 是无符号 8 位（`UInt8`）值的集合，每一个 `UInt8` 值都是一个字符的 UTF-8 表示

### UTF-16 表示

- `String` 的 `utf16` 属性来访问它的 `UTF-16` 表示

### Unicode 标量表示

- 你可以通过遍历 `String` 值的 `unicodeScalars` 属性来访问它的 Unicode 标量表示

# 集合类型

- 数组（Array）：有序

- 集合（Set）：无序无重复

- 字典（Dictionary）：无序的键值对

> Swift 的数组、集合和字典类型被实现为*泛型集合*

## 集合的可变性

- let：不可变
- var：增删改查

> 建议-在不需要改变集合的时候创建不可变集合

## 数组（Arrays）

- 有序储存+相同类型的值（相同类型的值可以重复出现。）

> Swift 的 `Array` 类型被桥接到 Foundation 中的 `NSArray` 类。参见 [Bridging Between Array and NSArray](https://developer.apple.com/documentation/swift/array#2846730)。

### 数组的简单语法

- 完整写法为 `Array<Element>`， `Element` 是数组唯一允许存在的数据类型
- 简单写法`[Element]` （推荐）

### 创建一个空数组

```swift
// MARK:- 创建空数组
var someInts =  [Int]()
var someInts2 = Array<Int>()		
```

- 若根据上下文，数组数据类型确定，可直接：`[]`（一对空方括号）

### 创建一个带有默认值的数组

- 创建特定大小+所有数据都被默认

```swift
var threeDoubles = Array(repeating: 0.0, count: 3)
// threeDoubles 是一种 [Double] 数组，等价于 [0.0, 0.0, 0.0]		
```

### 通过两个数组相加创建一个数组

- 加法操作符（`+`）组合相同类型数组（新数组类型从两个数组的数据类型中推断出来）

```swift
var anotherThreeDoubles = Array(repeating: 2.5, count: 3)
// anotherThreeDoubles 被推断为 [Double]，等价于 [2.5, 2.5, 2.5]

var sixDoubles = threeDoubles + anotherThreeDoubles
// sixDoubles 被推断为 [Double]，等价于 [0.0, 0.0, 0.0, 2.5, 2.5, 2.5]
```

### 用数组字面量构造数组

```swift
var shoppingList: [String] = ["Eggs", "Milk"]
// shoppingList 已经被构造并且拥有两个初始项。
```

-  当你用字面量构造-拥有相同类型值数组的时候

```swift
var shoppingList = ["Eggs", "Milk"]
```

### 访问和修改数组

- 数组的方法和属性来访问和修改数组，或者使用下标语法
- 用数组的只读属性 `count`

```swift
print("The shopping list contains \(shoppingList.count) items.")
// 输出“The shopping list contains 2 items.”（这个数组有2个项）
```

- 用布尔属性 `isEmpty` 作为一个缩写形式去检查 `count` 属性是否为 `0`

```swift
if shoppingList.isEmpty {
    print("The shopping list is empty.")
} else {
    print("The shopping list is not empty.")
}
// 打印“The shopping list is not empty.”（shoppinglist 不是空的）
```

- 用 `append(_:)` 在数组后面添加新数据：

```swift
shoppingList.append("Flour")
// shoppingList 现在有3个数据项，似乎有人在摊煎饼
```

- 用加法赋值运算符（`+=`）直接将另一个相同类型数组中的数据添加到该数组后面

```swift
shoppingList += ["Baking Powder"]
// shoppingList 现在有四项了
shoppingList += ["Chocolate Spread", "Cheese", "Butter"]
```

- 用*下标语法*来获取数组中的数据项

```swift
var firstItem = shoppingList[0]
// 第一项是“Eggs”
```

> 注意
>
> 第一项在数组中的索引值是 `0` 而不是 `1`。 Swift 中的数组索引总是从零开始。

- 用下标来改变某个有效索引值对应的数据值：

```swift
shoppingList[0] = "Six eggs"
// 其中的第一项现在是“Six eggs”而不是“Eggs”
```

- 用下标改变多个值，即使新数据和原有数据的数量是不一样的。

- 下面的例子把 `"Chocolate Spread"`、`"Cheese"` 和 `"Butter"` 替换为 `"Bananas"` 和 `"Apples"`

```swift
shoppingList[4...6] = ["Bananas", "Apples"]
// shoppingList 现在有6项
```

- `insert(_:at:)` 方法-在指定索引值之前添加数据

```swift
shoppingList.insert("Maple Syrup", at: 0)
// shoppingList 现在有7项
// 现在是这个列表中的第一项是“Maple Syrup”
```

- 用 `remove(at:)` 方法来移除数组某一项，并且返回这个被移除的数据项（不需要的时候就可以无视它）

```swift
let mapleSyrup = shoppingList.remove(at: 0)
// 索引值为0的数据项被移除
// shoppingList 现在只有6项，而且不包括 Maple Syrup
// mapleSyrup 常量的值等于被移除数据项“Maple Syrup”
```

> 注意索引越界：当 `count` 等于 0 时（说明这是个空数组），最大索引值一直是 `count - 1`，因为数组都是零起索引

- 数据项被移除后数组中的空出项会被自动填补
- 最后一项移除，可以使用 `removeLast()` 方法而不是 `remove(at:)` 方法来避免需要获取数组的 `count` 属性（也会返回被移除的数据项）

```swift
let apples = shoppingList.removeLast()
// 数组的最后一项被移除了
// shoppingList 现在只有5项，不包括 Apples
// apples 常量的值现在等于字符串“Apples”
```

### 数组的遍历

- 用 `for-in` 循环来遍历数组中所有的数据项

```swift
for item in shoppingList {
    print(item)
}
```

- 需要值和索引值，可以使用 `enumerated()` 方法来进行数组遍历
- `enumerated()` 返回一个由索引值和数据值组成的【元组数组】

```swift
for (index, value) in shoppingList.enumerated() {
    print("Item \(String(index + 1)): \(value)")
}
// Item 1: Six eggs
// Item 2: Milk
// Item 3: Flour
// Item 4: Baking Powder
// Item 5: Bananas
```

## 集合（Sets）

- 存储相同类型+没有顺序要求的数据

> 注意 Swift 的 `Set` 类型被桥接到 Foundation 中的 `NSSet` 类。
>
> 关于使用 Foundation 和 Cocoa 中 `Set` 的知识，参见 [Bridging Between Set and NSSet](https://developer.apple.com/documentation/swift/set#2845530)

### 集合类型的哈希值

- 一个类型为了存储在集合中，该类型必须是*可哈希化*的
- 一个哈希值是 `Int` 类型的，相等的对象哈希值必须相同，比如 `a == b`,因此必须 `a.hashValue == b.hashValue`
- Swift 的所有基本类型（比如 `String`、`Int`、`Double` 和 `Bool`）默认都是可哈希化的

### 集合类型语法

- Set<Element>
- 跟数组不同，没有简化形式

### 创建和构造一个空的集合

```swift
var letters = Set<Character>()
print("letters is of type Set<Character> with \(letters.count) items.")
// 打印“letters is of type Set<Character> with 0 items.”
```

- 如果上下文提供了类型信息，比如作为函数的参数或者已知类型的变量或常量，你可以通过一个空的数组字面量创建一个空的集合：

```swift
letters.insert("a")
// letters 现在含有1个 Character 类型的值
letters = []
// letters 现在是一个空的 Set，但是它依然是 Set<Character> 类型
```

### 

```swift
var favoriteGenres: Set<String> = ["Rock", "Classical", "Hip hop"]
// favoriteGenres 被构造成含有三个初始值的集合
```

> `favoriteGenres` 被声明为一个变量（拥有 `var` 标示符）而不是一个常量（拥有 `let` 标示符）,因为它里面的元素将会在之后的例子中被增加或者移除。

- 一个集合类型不能从数组字面量中被直接推断出来，因此 `Set` 类型必须显式声明

### 访问和修改一个集合

- 取一个集合中元素的数量，可以使用其只读属性 `count`
- 布尔属性 `isEmpty` 作为一个缩写形式去检查 `count` 属性是否为 `0`
- `insert(_:)` 方法来添加一个新元素
- `remove(_:)` 删除一个元素（删除它并且返回它的值）若该集合不包含它，则返回 `nil`
- 通过 `removeAll()` 方法删除所有元素

```swift
if let removedGenre = favoriteGenres.remove("Rock") {
    print("\(removedGenre)? I'm over it.")
} else {
    print("I never much cared for that.")
}
// 打印“Rock? I'm over it.”
```

- `contains(_:)` 方法去检查是否包含一个特定的值

```swift
if favoriteGenres.contains("Funk") {
    print("I get up on the good foot.")
} else {
    print("It's too funky in here.")
}
// 打印“It's too funky in here.”
```

### 遍历一个集合

- `for-in` 循环中遍历

```swift
for genre in favoriteGenres {
    print("\(genre)")
}
// Classical
// Jazz
// Hip hop
```

- 特定顺序来遍历一个集合中的值可以使用 `sorted()` 方法，它将返回一个有序数组，这个数组的元素排列顺序由操作符 `<` 对元素进行比较的结果来确定

```swift
for genre in favoriteGenres.sorted() {
    print("\(genre)")
}
// Classical
// Hip hop
// Jazz
```

## 集合操作

- 把两个集合组合到一起
- 判断两个集合共有元素
- 判断两个集合是否全包含，部分包含或者不相交

### 基本集合操作

- 以及通过阴影部分的区域显示两个集合 `a` 和 `b`各种操作的结果：

![集合图解](https://docs.swift.org/swift-book/_images/setVennDiagram_2x.png)

- 使用 `intersection(_:)` 方法根据两个集合的交集创建一个新的集合。// 交集
- 使用 `symmetricDifference(_:)` 方法根据两个集合不相交的值创建一个新的集合。// 并集 - 交集
- 使用 `union(_:)` 方法根据两个集合的所有值创建一个新的集合。// 并集
- 使用 `subtracting(_:)` 方法根据不在另一个集合中的值创建一个新的集合。

```swift
let oddDigits: Set = [1, 3, 5, 7, 9]
let evenDigits: Set = [0, 2, 4, 6, 8]
let singleDigitPrimeNumbers: Set = [2, 3, 5, 7]

oddDigits.union(evenDigits).sorted()
// [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
oddDigits.intersection(evenDigits).sorted()
// []
oddDigits.subtracting(singleDigitPrimeNumbers).sorted()
// [1, 9]
oddDigits.symmetricDifference(singleDigitPrimeNumbers).sorted()
// [1, 2, 9]
```

### 集合成员关系和相等

![img](https://docs.swift.org/swift-book/_images/setEulerDiagram_2x.png)

- 运算符（`==`）来判断两个集合包含的值是否全部相同
- `isSubset(of:)` 方法来判断一个集合中的所有值是否也被包含在另外一个集合中
- 使用 `isSuperset(of:)` 方法来判断一个集合是否包含另一个集合中所有的值。
- 使用 `isStrictSubset(of:)` 或者 `isStrictSuperset(of:)` 方法来判断一个集合是否是另外一个集合的子集合或者父集合并且两个集合并不相等。

- 使用 `isDisjoint(with:)` 方法来判断两个集合是否不含有相同的值（是否没有交集）

```swift
let houseAnimals: Set = ["🐶", "🐱"]
let farmAnimals: Set = ["🐮", "🐔", "🐑", "🐶", "🐱"]
let cityAnimals: Set = ["🐦", "🐭"]

houseAnimals.isSubset(of: farmAnimals)
// true
farmAnimals.isSuperset(of: houseAnimals)
// true
farmAnimals.isDisjoint(with: cityAnimals)
// true
```

## 字典

- 无序的集合
- 所有键的值需要是相同的类型
- 所有值的类型也需要相同

>  Swift 的 `Dictionary` 类型被桥接到 Foundation 的 `NSDictionary` 类。

>  更多关于在 Foundation 和 Cocoa 中使用 `Dictionary` 类型的信息，参见 [Bridging Between Dictionary and NSDictionary](https://developer.apple.com/documentation/swift/dictionary#2846239)。

### 字典类型简化语法

- 用 `Dictionary<Key, Value>` 定义
- 简化可用 `[Key: Value]`

> 字典的 `Key` 类型必须遵循 `Hashable` 协议，就像 `Set` 的值类型。

### 创建一个空字典

```swift
var namesOfIntegers = [Int: String]()
// namesOfIntegers 是一个空的 [Int: String] 字典
```

- 如果上下文已经提供了类型信息，可以使用空字典字面量来创建一个空字典，记作 `[:]` （一对方括号中放一个冒号）

```swift
namesOfIntegers[16] = "sixteen"
// namesOfIntegers 现在包含一个键值对
namesOfIntegers = [:]
// namesOfIntegers 又成为了一个 [Int: String] 类型的空字典
```

### 用字典字面量创建字典

```swift
[key 1: value 1, key 2: value 2, key 3: value 3]
```

```swift
var airports: [String: String] = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]
```

- 键和值都有各自一致的类型，那么就不必写出字典的类型

```swift
var airports = ["YYZ": "Toronto Pearson", "DUB": "Dublin"]
```

- Swift 可以推断出 `[String: String]` 是 `airports` 字典的正确类型

### 访问和修改字典

- 只读属性 `count`

```swift
print("The dictionary of airports contains \(airports.count) items.")
// 打印“The dictionary of airports contains 2 items.”（这个字典有两个数据项）
```

- 布尔属性 `isEmpty` 作为一个缩写形式去检查 `count` 属性是否为 `0`

```swift
if airports.isEmpty {
    print("The airports dictionary is empty.")
} else {
    print("The airports dictionary is not empty.")
}
// 打印“The airports dictionary is not empty.”
```

- 下标语法访问

```swift
airports["LHR"] = "London"
// airports 字典现在有三个数据项
```

- 下标语法来改变特定键对应的值

```swift
airports["LHR"] = "London Heathrow"
// “LHR”对应的值被改为“London Heathrow”
```

- `updateValue(_:forKey:)` 方法可以设置或者更新特定键对应的值（不存在对应值的时候会设置新值或者在存在时更新已存在的值）
- 该方法返回更新值之前的*原值* 的可选类型。这样使得你可以检查更新是否成功。

```swift
if let oldValue = airports.updateValue("Dublin Airport", forKey: "DUB") {
    print("The old value for DUB was \(oldValue).")
}
// 输出“The old value for DUB was Dublin.”
```

- 也可以使用下标语法
- 如果这个字典包含请求键所对应的值，下标会返回一个包含这个存在值的可选类型，否则将返回 `nil`

```swift
if let airportName = airports["DUB"] {
    print("The name of the airport is \(airportName).")
} else {
    print("That airport is not in the airports dictionary.")
}
// 打印“The name of the airport is Dublin Airport.”
```

- 可以使用下标语法通过将某个键的对应值赋值为 `nil` 来从字典里移除一个键值

```
airports["APL"] = "Apple Internation"
// “Apple Internation”不是真的 APL 机场，删除它
airports["APL"] = nil
// APL 现在被移除了
```

- `removeValue(forKey:)` 方法也可以用来在字典中移除键值对
- 在键值对存在的情况下会移除该键值对并且返回被移除的值
- 在没有对应值的情况下返回 `nil`

```swift
if let removedValue = airports.removeValue(forKey: "DUB") {
    print("The removed airport's name is \(removedValue).")
} else {
    print("The airports dictionary does not contain a value for DUB.")
}
// 打印“The removed airport's name is Dublin Airport.”
```

### 字典遍历

- 用 `for-in` 循环来遍历某个字典中的键值对

```swift
for (airportCode, airportName) in airports {
    print("\(airportCode): \(airportName)")
}
// YYZ: Toronto Pearson
// LHR: London Heathrow
```

- 访问 `keys` 或者 `values` 属性，你也可以遍历字典的键或者值

```swift
for airportCode in airports.keys {
    print("Airport code: \(airportCode)")
}
// Airport code: YYZ
// Airport code: LHR


for airportName in airports.values {
    print("Airport name: \(airportName)")
}
// Airport name: Toronto Pearson
// Airport name: London Heathrow
```

- 用某个字典的键集合或者值集合来作为某个接受 `Array` 实例的 API 的参数

- 可以直接使用 `keys` 或者 `values` 属性构造一个新数组

  ```swift
  let airportCodes = [String](airports.keys)
  // airportCodes 是 ["YYZ", "LHR"]
  
  
  let airportNames = [String](airports.values)
  // airportNames 是 ["Toronto Pearson", "London Heathrow"]
  ```

- 可以对字典的 `keys` 或 `values` 属性使用 `sorted()` 方法

# 控制流

## For-In 循环
## While 循环
### While
### Repeat-While

## 条件语句
### Switch
#### 不存在隐式的贯穿
#### 区间匹配
#### 元组
##### 值绑定（Value Bindings）
#### Where
#### 复合型 Cases

### 控制转移语句
#### Continue
##### Break
###### 循环语句中的 break
###### Switch 语句中的 break

##### 贯穿（Fallthrough）
####### 带标签的语句

## 提前退出

## 检测 API 可用性

# 函数
## 函数的定义与调用
## 函数参数与返回值
### 无参数函数
### 多参数函数
### 无返回值函数
### 多重返回值函数
### 可选元组返回类型
### 隐式返回的函数
## 函数参数标签和参数名称
### 指定参数标签
### 忽略参数标签
### 默认参数值
### 可变参数
### 输入输出参数

## 函数类型
### 使用函数类型
### 函数类型作为参数类型
### 函数类型作为返回类型

## 嵌套函数

# 闭包
## 闭包表达式
### 排序方法
### 闭包表达式语法
### 根据上下文推断类型
### 单表达式闭包的隐式返回
### 参数名称缩写
### 运算符方法

## 尾随闭包

## 值捕获

## 闭包是引用类型

## 逃逸闭包

## 自动闭包

# 枚举
## 枚举语法
## 使用 Switch 语句匹配枚举值
## 枚举成员的遍历
## 关联值
## 原始值
### 原始值的隐式赋值
### 使用原始值初始化枚举实例

## 递归枚举

# 类和结构体
## 结构体和类对比
### 类型定义的语法
### 结构体和类的实例
### 属性访问
### 结构体类型的成员逐一构造器

## 结构体和枚举是值类型
## 类是引用类型
### 恒等运算符
### 指针

# 属性
## 存储属性
### 常量结构体实例的存储属性
### 延时加载存储属性
### 存储属性和实例变量

## 计算属性
### 简化 Setter 声明
### 简化 Getter 声明
### 只读计算属性

## 属性观察器

## 属性包装器
### 设置被包装属性的初始值
### 从属性包装器中呈现一个值

## 全局变量和局部变量

## 类型属性
### 类型属性语法
### 获取和设置类型属性的值


# 方法

## 实例方法（Instance Methods）
### self 属性
### 在实例方法中修改值类型
### 在可变方法中给 self 赋值

## 类型方法


# 下标

## 下标语法

## 下标用法

## 下标选项

## 类型下标

# 继承
## 定义一个基类
## 子类生成
## 重写
### 访问超类的方法，属性及下标
### 重写方法
### 重写属
#### 重写属性的 Getters 和 Setters
#### 重写属性观察器
## 防止重写

# 构造过程
## 存储属性的初始赋值
### 构造器
### 默认属性值
## 自定义构造过程
### 形参的构造过程
### 形参命名和实参标签
### 不带实参标签的构造器形参
### 可选属性类型
### 构造过程中常量属性的赋值
## 默认构造器
### 结构体的逐一成员构造器
## 值类型的构造器代理
## 类的继承和构造过程
### 指定构造器和便利构造器
### 指定构造器和便利构造器的语法
### 类类型的构造器代理
### 两段式构造过程
### 构造器的继承和重写
### 构造器的自动继承
### 指定构造器和便利构造器实践
## 可失败构造器
### 枚举类型的可失败构造器
### 带原始值的枚举类型的可失败构造器
### 构造失败的传递
### 重写一个可失败构造器
### init! 可失败构造器
## 必要构造器
## 通过闭包或函数设置属性的默认值

# 析构过程
## 析构过程原理
## 析构器实践

# 可选链
## 使用可选链式调用代替强制解包
## 为可选链式调用定义模型类
## 通过可选链式调用访问属性
## 通过可选链式调用来调用方法
## 通过可选链式调用访问下标
### 访问可选类型的下标
## 连接多层可选链式调用
## 在方法的可选返回值上进行可选链式调用

# 错误处理
## 表示与抛出错误
## 处理错误
### 用 throwing 函数传递错误
### 用 Do-Catch 处理错误
### 将错误转换成可选值
### 禁用错误传递
## 指定清理操作

# 类型转换
## 为类型转换定义类层次
## 检查类型
## 向下转型
## Any 和 AnyObject 的类型转换

# 嵌套类型
## 嵌套类型实践
## 引用嵌套类型

# 扩展
## 扩展的语法
## 计算型属性
## 扩展构造器
## 方法
### 可变实例方法
## 下标
## 嵌套类型

# 协议
## 协议语法
## 属性要求
## 方法要求
## 异变方法要求
## 构造器要求
### 协议构造器要求的类实现
### 可失败构造器要求
## 协议作为类型
## 委托
## 在扩展里添加协议遵循
## 有条件地遵循协议
## 在扩展里声明采纳协议
## 使用合成实现来采纳协议
## 协议类型的集合
## 协议的继承
## 类专属的协议
## 协议合成
## 检查协议一致性
## 可选的协议要求
## 协议扩展
### 提供默认实现
### 为协议扩展添加限制条件

# 泛型
## 泛型解决的问题
## 泛型函数
## 类型参数
## 命名类型参数
## 泛型类型
## 泛型扩展
## 类型约束
### 类型约束语法
### 类型约束实践
## 关联类型
### 关联类型实践
### 扩展现有类型来指定关联类型
### 给关联类型添加约束
### 在关联类型约束里使用协议
## 泛型 Where 语句
## 具有泛型 Where 子句的扩展
## 包含上下文关系的 where 分句
## 具有泛型 Where 子句的关联类型
## 泛型下标

# 不透明类型
## 不透明类型解决的问题
## 返回不透明类型
## 不透明类型和协议类型的区别

# 自动引用计数
## 自动引用计数的工作机制
## 自动引用计数实践
## 类实例之间的循环强引用
## 解决实例之间的循环强引用
### 弱引用
### 无主引用
### 无主引用和隐式解包可选值属性
## 闭包的循环强引用
## 解决闭包的循环强引用
### 定义捕获列表
### 弱引用和无主引用

# 内存安全
## 理解内存访问冲突
### 内存访问性质
## In-Out 参数的访问冲突
## 方法里 self 的访问冲突
## 属性的访问冲突

# 访问控制
## 模块和源文件
## 访问级别
### 访问级别基本原则
### 默认访问级别
### 单 target 应用程序的访问级别
### 框架的访问级别
### 单元测试 target 的访问级别
## 访问控制语法
## 自定义类型
### 元组类型
### 函数类型
### 枚举类型
#### 原始值和关联值
### 嵌套类型
## 子类
## 常量、变量、属性、下标
### Getter 和 Setter
## 构造器
### 默认构造器
### 结构体默认的成员逐一构造器

## 协议
### 协议继承
### 协议遵循

## Extension
### Extension 的私有成员
## 泛型
## 类型别名

# 高级运算符
## 位运算符
### Bitwise NOT Operator（按位取反运算符）
### Bitwise AND Operator（按位与运算符）
### Bitwise OR Operator（按位或运算符）
### Bitwise XOR Operator（按位异或运算符）
### Bitwise Left and Right Shift Operators（按位左移、右移运算符）
#### 无符号整数的移位运算
#### 有符号整数的移位运算
## 溢出运算符
### 数值溢出
## 优先级和结合性
## 运算符函数
### 前缀和后缀运算符
### 复合赋值运算符
### 等价运算符
## 自定义运算符
### 自定义中缀运算符的优先级

# 语言参考

