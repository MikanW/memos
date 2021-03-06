# 深入理解ES6

## 第一章 变量作用域

### 变量提升
var 声明变量会造成变量提升，不受{}等的作用域范围限制

### 块级作用域
let声明，对所在块级作用域{}外不可见
在不同的块级作用域{}范围中可以使用let声明重名变量，内部块遮蔽外部/全局

### 常量const
const常量声明后不可修改/重新赋值
必须在声明当场初始化
只在当前块级作用域中有效

⚠️注意 如果用const修饰一个对象，对象的属性是可以后续修改的

### 临时死区 （temporal Dead Zone，TDZ）
微妙的概念。
形容js引擎在预编译时已经发现某变量，但该变量是let声明或const，不会被变量提升，则在代码执行到该变量被声明出来之前，它都处于TDZ中。
like《死亡搁浅》里的bb，bb事实上存在于Sam身边，但bb尚未出生。

TDZ的概念只在块级作用域范围内有效。

例：
在{}内typeof一个尚未let声明的变量；//报错，因为变量在TDZ中
在进入{}范围之前，typeof一个在{}内即将被let的变量； //不报错，当前作用域中没有该变量，返回undefined

### 循环变量的块作用域

for循环的循环变量使用let声明，这样子变量在循环之外就访问不到了