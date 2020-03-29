### 产生异常原因
- Java 内部错误发生异常，Java 虚拟机产生的异常。
- 编写的程序代码中的错误所产生的异常，例如空指针异常、数组越界异常等。
- 通过 throw 语句手动生成的异常，一般用来告知该方法的调用者一些必要信息。
### java异常处理关键字
1. Java 的异常处理通过 5 个关键字来实现：try、catch、throw、throws 和 finally。try catch 语句用于捕获并处理异常，finally 语句用于在任何情况下（除特殊情况外）都必须执行的代码，throw 语句用于拋出异常，throws 语句用于声明可能会出现的异常。
### java异常处理程序的基本结构
```
try {
    逻辑程序块
} catch(ExceptionType1 e) {
    处理代码块1
} catch (ExceptionType2 e) {
    处理代码块2
    throw(e);    // 再抛出这个"异常"
} finally {
    释放资源代码块
}
```
### 使用try-catch-finally需要注意的几点
1. 异常处理语法结构中只有 try 块是必需的，也就是说，如果没有 try 块，则不能有后面的 catch 块和 finally 块；
2. catch 块和 finally 块都是可选的，但 catch 块和 finally 块至少出现其中之一，也可以同时出现；
3. 可以有多个 catch 块，捕获父类异常的 catch 块必须位于捕获子类异常的后面；
4. 不能只有 try 块，既没有 catch 块，也没有 finally 块；
5. 多个 catch 块必须位于 try 块之后，finally 块必须位于所有的 catch 块之后。
6. finally 与 try 语句块匹配的语法格式，此种情况会导致异常丢失，所以不常见。
### 使用try-catch-finally执行的三种情况
1. 如果 try 代码块中没有拋出异常，则执行完 try 代码块之后直接执行 finally 代码块，然后执行 try catch finally 语句块之后的语句。
2. 如果 try 代码块中拋出异常，并被 catch 子句捕捉，那么在拋出异常的地方终止 try 代码块的执行，转而执行相匹配的 catch 代码块，之后执行 finally 代码块。如果 finally 代码块中没有拋出异常，则继续执行 try catch finally 语句块之后的语句；如果 finally 代码块中拋出异常，则把该异常传递给该方法的调用者。
3. 如果 try 代码块中拋出的异常没有被任何 catch 子句捕捉到，那么将直接执行 finally 代码块中的语句，并把该异常传递给该方法的调用者。
### java声明异常和抛出异常
### java多异常捕获
