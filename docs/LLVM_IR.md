## 常用LLVM IR指令解释

---

### 终结指令 LLVM IR 指令

- ret 函数的返回指令<br>
    对应C/C++的`return`<br>
    1. 需要指定返回值的类型和值的ret指令(可以返回一整个结构体)
    2. 无返回值的ret指令

- br 分支指令<br>
    对应C/C++的`if`<br>
    > 分为非条件分支和条件分支指令
    1. 无条件分支指令类似于x86的`jmp`指令
    2. 条件分支类似于x86汇编的`jnz`或`je`指令

- 补充:比较指令 
    1. icmp:整数或指针的比较指令<br>
        cond 条件可为: eq 相等 ｜ ne 不相等 | ugt 无符号大于 | ...
    2. fcmp:浮点数的比较指令<br>
        cond 条件可为: oeq 相等并且两个操作数不可为NAN ｜ ueq 相等 | ...<br>
        > o的意思就是ordered 意思是两个操作数都不可为NAN 否则返回false

- switch 分支指令<br>
    可以看作是br指令的升级版 支持的分支更多<br>
    相当于C/C++的`switch`指令<br>

### 二元运算 LLVM IR 指令

- add 整数的加法指令<br>
    对应C/C++的`+`

- sub 整数的减法指令<br>
    对应C/C++的`-`

- mul 整数的乘法指令<br>
    对应C/C++的`*`

- udiv 无符号整数除法指令<br>
    对应C/C++的`/`<br>
    如果有exact(精确)关键字修饰 则如果op1不是op2的倍数 则出错

- sdiv 有符号的整数除法指令<br>
    对应C/C++的`/`<br>
    如果有exact(精确)关键字修饰 则如果op1不是op2的倍数 则出错

- urem 无符号整数的取余数指令<br>
    对应C/C++`%`

- srem 有符号整数的取余指令<br>
    对应C/C++`%`

### 按位二元运算 LLVM IR 指令

- shl 整数左移指令<br>
    对应C/C++的`<<`

- lshr 整数逻辑右移指令<br>
    对应C/C++的`>>`<br>
    右移指定位数后 左侧补0
    > 不管里面的操作数是有符号的还是无符号的 <br>
    > 统一当成无符号的数进行处理 -- 逻辑右移

- ashr 整数的算术右移指令<br>
    对应C/C++的`>>`<br>
    右移指定位数后 左侧补符号位<br>
    > 负数补1 正数补0

- and 整数的按位运算指令<br>
    对应C/C++的`&`

- or 整数的按位或运算指令<br>
    对应C/C+的`|`

- xor 整数的按位异或运算指令<br>
    对应C/C++的`^`

### 内存访问和寻址操作

- alloca 内存分配指令<br>
    在栈中分配一段空间并获得指向改空间的指针<br>
    对应C/C++的`malloc`

- store 内存储存指令<br>
    向指针指向的内存中存储数据<br>
    类似于C/C++中的指针解引用后的赋值操作

- load 内存读取指令<br>
    从指针指向的内存中读取数据<br>
    类似于C/C++中的指针解引用操作

### 类型转化操作

- trunc ... to 截断指令<br>
    将一种变量截断为另一种变量<br>
    对应C/C++中大类型向小类型的强制转化<br>
    > long --> int

- zext ... to 零拓展指令<br>
    将一种类型的变量拓展为另一种变量 高位补0<br>
    对应C/C++中小类型向大类型的强制转化<br>
    > int --> long

- sext ... to <br>




---

## 个人笔记