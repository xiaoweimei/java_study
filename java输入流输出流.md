### 三个系统流
1. System.in：标准输入流，默认设备是键盘。
2. System.out：标准输出流，默认设备是控制台。
3. System.err：标准错误流，默认设备是控制台。
### java中常见编码说明
1. ISO8859-1：属于单字节编码，最多只能表示 0~255 的字符范围。
2. GBK/GB2312：中文的国标编码，用来表示汉字，属于双字节编码。GBK 可以表示简体中文和繁体中文，而 GB2312 只能表示简体中文。GBK 兼容 GB2312。
3. Unicode：是一种编码规范，是为解决全球字符通用编码而设计的。UTF-8 和 UTF-16 是这种规范的一种实现，此编码不兼容 ISO8859-1 编码。Java 内部采用此编码。
4. UTF：UTF 编码兼容了 ISO8859-1 编码，同时也可以用来表示所有的语言字符，不过 UTF 编码是不定长编码，每一个字符的长度为 1~6 个字节不等。一般在中文网页中使用此编码，可以节省空间。
