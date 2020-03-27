### JDK、JRE、JVM三者关系
1. JDK（Java Development Kid，Java 开发开源工具包），是针对 Java 开发人员的产品，是整个 Java 的核心，包括了 Java 运行环境 JRE、Java 工具和 Java 基础类库。
- JDK(开发工具包)
2. JRE（Java Runtime Environment，Java 运行环境）是运行 JAVA 程序所必须的环境的集合，包含 JVM 标准实现及 Java 核心类库。
- JRE(运行环境)运行时类库
3. JVM（Java Virtual Machine，Java 虚拟机）是整个 Java 实现跨平台的最核心的部分，能够运行以 Java 语言写作的软件程序。
- JAVA虚拟机
4. JDK=JRE+多种Java开发工具
5. JRE=JVM+各种类库
6. 这三者的关系是一层层的嵌套关系。JDK>JRE>JVM
### java新手常见问题
1. 大小写问题，java严格区分大小写
2. 路径里包含空格的问题
3. main方法的问题，如果需要用 java 命令直接运行一个 Java 类，这个 Java 类必须包含 main 方法，这个 main 方法必须使用 public 和 static 来修饰，必须使用 void 声明该方法的返回值，而且该方法的参数类型只能是一个字符串数组，而不能是其他形式的参数。对于这个 main 方法而言，前面的 public 和 static 修饰符的位置可以互换，但其他部分则是固定的。
