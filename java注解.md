### java注解常见作用
1. 生成帮助文档。这是最常见的，也是 Java 最早提供的注解。常用的有 @see、@param 和 @return 等；
2. 跟踪代码依赖性，实现替代配置文件功能。比较常见的是 Spring 2.5 开始的基于注解配置。作用就是减少配置。现在的框架基本都使用了这种配置来减少配置文件的数量；
3. 在编译时进行格式检查。如把 @Override 注解放在方法前，如果这个方法并不是重写了父类方法，则编译时就能检查出。
### 注解示例
- Java 中 @Override 注解是用来指定方法重写的，只能修饰方法并且只能用于方法重写，不能修饰其它的元素。它可以强制一个子类必须重写父类方法或者实现接口的方法。
```
override注解示例
public class Person {
    private String name = "";
    private int age;
    ...
    @Override
    public String t0String() { //toString()
        return "Person [name=" + name + ", age=" + age + "]";
    }
}
```
- Java 中 @Deprecated 可以用来注解类、接口、成员方法和成员变量等，用于表示某个元素（类、方法等）已过时。当其他程序使用已过时的元素时，编译器将会给出警告。
```
@Deprecated注解示例
@Deprecated
public class Person {
    @Deprecated
    protected String name;
    private int age;
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public int getAge() {
        return age;
    }
    public void setAge(int age) {
        this.age = age;
    }
    @Deprecated
    public void setNameAndAge(String name, int age) {
        this.name = name;
        this.age = age;
    }
    @Override
    public String toString() {
 
 return "Person [name=" + name + ", age=" + age + "]";
    }
}
```
- Java 中的 @SuppressWarnings 注解指示被该注解修饰的程序元素（以及该程序元素中的所有子元素）取消显示指定的编译器警告，且会一直作用于该程序元素的所有子元素。例如，使用 @SuppressWarnings 修饰某个类取消显示某个编译器警告，同时又修饰该类里的某个方法取消显示另一个编译器警告，那么该方法将会同时取消显示这两个编译器警告。
```
@SuppressWarnings注解示例
public class HelloWorld {
    @SuppressWarnings({ "deprecation" })
    public static void main(String[] args) {
        Person p = new Person();
        p.setNameAndAge("C语言中文网", 20);
        p.name = "Java教程";
    }
}
```
- 可用 @SafeVarargs 注解抑制编译器警告
```
public class HelloWorld {
    public static void main(String[] args) {
        // 传递可变参数，参数是泛型集合
        display(10, 20, 30);
        // 传递可变参数，参数是非泛型集合
        display("10", 20, 30); // 没有@SafeVarargs会有编译警告
    }
    @SafeVarargs
    public static <T> void display(T... array) {
        for (T arg : array) {
            System.out.println(arg.getClass().getName() + "：" + arg);
        }
    }
}
```
- 在学习 Lambda 表达式时，我们提到如果接口中只有一个抽象方法（可以包含多个默认方法或多个 static 方法），那么该接口就是函数式接口。@FunctionalInterface 就是用来指定某个接口必须是函数式接口，所以 @FunInterface 只能修饰接口，不能修饰其它程序元素。
```
@FunctionalInterface注解示例
@FunctionalInterface
public interface FunInterface {
    static void print() {
        System.out.println("C语言中文网");
    }
    default void show() {
        System.out.println("我正在学习C语言中文网Java教程");
    }
    void test(); // 只定义一个抽象方法
}
```
- 元注解是负责对其它注解进行说明的注解，自定义注解时可以使用元注解。Java 5 定义了 4 个注解，分别是 @Documented、@Target、@Retention 和 @Inherited。Java 8 又增加了 @Repeatable 和 @Native 两个注解。这些注解都可以在 java.lang.annotation 包中找到。
### 自定义注解
- 声明自定义注解使用 @interface 关键字（interface 关键字前加 @ 符号）实现。定义注解与定义接口非常像，如下代码可定义一个简单形式的注解类型。
