### 定义字符串
1. 直接定义 `String str = "Hello Java";`或`String str;str = "Hello Java";`
2. 使用 String 类定义 `String str1 = new String("Hello Java");`
### String转换为int
1. Integer.parseInt(str)
2. Integer.valueOf(str).intValue()
### int转换为String
1. String s = String.valueOf(i);
2. String s = Integer.toString(i);
3. String s = "" + i;
### valueOf() 、parse()和toString()
### java字符串拼接
1. 直接使用连接运算符`+`
2. 使用concat方法 `字符串 1.concat(字符串 2);`
3. 连接其他数据类型
### 获取字符串长度 `字符串名.length();`
### 大小写转换 `字符串名.toLowerCase();字符串名.toUpperCase()`
### 去除字符串中的空格 `字符串名.trim()`
### 提取子字符串 `1. substring(int beginIndex) 形式或2. substring(int beginIndex，int endIndex) 形式`
### 分割字符串
1. str.split(String sign)
2. str.split(String sign,int limit)
### 替换字符串 `字符串.replace(String oldChar, String newChar)`
1. replaceFirst() 方法
- replaceFirst() 方法用于将目标字符串中匹配某正则表达式的第一个子字符串替换成新的字符串，其语法形式如下：
- 字符串.replaceFirst(String regex, String replacement)
2. replaceAll() 方法
- replaceAll() 方法用于将目标字符串中匹配某正则表达式的所有子字符串替换成新的字符串，其语法形式如下：
- 字符串.replaceAll(String regex, String replacement)
### 字符串的比较
1. equals() 方法
- equals() 方法将逐个地比较两个字符串的每个字符是否相同。如果两个字符串具有相同的字符和长度，它返回 true，否则返回 false。对于字符的大小写，也在检查的范围之内。
2. equalsIgnoreCase() 方法
- equalsIgnoreCase() 方法的作用和语法与 equals() 方法完全相同，唯一不同的是 equalsIgnoreCase() 比较时不区分大小写。
3. compareTo() 方法
- 通常，仅仅知道两个字符串是否相同是不够的。对于排序应用来说，必须知道一个字符串是大于、等于还是小于另一个。一个字符串小于另一个指的是它在字典中先出现。而一个字符串大于另一个指的是它在字典中后出现。字符串（String）的 compareTo() 方法实现了这种功能。
### 根据字符查找
**String 类的 indexOf() 方法和 lastlndexOf() 方法用于在字符串中获取匹配字符（串）的索引值。**
1. indexOf() 方法
- indexOf() 方法用于返回字符（串）在指定字符串中首次出现的索引位置，如果能找到，则返回索引值，否则返回 -1。
2. lastlndexOf() 方法
- lastIndexOf() 方法用于返回字符（串）在指定字符串中最后一次出现的索引位置，如果能找到则返回索引值，否则返回 -1。
3. 根据索引查找
- String 类的 charAt() 方法可以在字符串内根据指定的索引查找字符，该方法的语法形式如下：
- 字符串名.charAt(索引值)
