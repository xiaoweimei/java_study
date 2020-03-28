### java math类的常用方法
1， 静态常量
- Math 类中包含 E 和 PI 两个静态常量
2. 求最大值、最小值、绝对值
- Math.max()\Math.min()\Math.abs()
3. 取整运算
- Math.ceil(a) 大于或等于a的最小整数
- Math.floor(a) 小于或等于a的最大整数
- Math.rint(a) 返回最接近a的整数值，如果有两个同样接近的整数，则结果取偶数
- Math.round(a) 将a加上1/2后返回最接近的整数
### java生成随机数
1. 一种是调用 Math 类的 random() 方法
- random() 方法只能产生 double 类型的 0~1 的随机数。
2. 一种是使用 Random 类
- Random 类提供了丰富的随机数生成方法，可以产生 boolean、int、long、float、byte 数组以及 double 类型的随机数
### java数字格式化
- 数字的格式在解决实际问题时使用非常普遍，这时可以使用 DedmalFormat 类对结果进行格式化处理。例如，将小数位统一成 2 位，不足 2 位的以 0 补齐。
### java日期时间
**Date 类主要封装了系统的日期和时间的信息，Calendar 类则会根据系统的日历来解释 Date 对象。**
```
Date date1 = new Date();    // 调用无参数构造函数
System.out.println(date1.toString());    // 输出：Wed May 18 21:24:40 CST 2016
Date date2 = new Date(60000);    // 调用含有一个long类型参数的构造函数
System.out.println(date2);    // 输出：Thu Jan 0108:01:00 CST 1970
```
