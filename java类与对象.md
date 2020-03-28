### java语言是单继承的(一个子类只能有一个父类)C++是多继承的(一个子类可以有多个父类)
### java语言的基本封装单位是类，Java 提供了私有和公有的访问模式，类的公有接口代表外部的用户应该知道或可以知道的每件东西，私有的方法数据只能通过该类的成员代码来访问，这就可以确保不会发生不希望的事情。
### java多态性 面向对象的多态性，即“一个接口，多个方法”。多态性体现在父类中定义的属性和方法被子类继承后，可以具有不同的属性或表现方式。多态性允许一个接口被多个同类使用，弥补了单继承的不足。
### 类是对象的抽象，对象是类的具体。
### 类是描述了一组有相同特性（属性）和相同行为（方法）的一组对象的集合。
### 对象或实体所拥有的特征在类中表示时称为类的属性。
### 对象执行的操作称为类的方法。
### 类是构造面向对象程序的基本单位
### 定义类的完整语法
```
[public][abstract|final]class<class_name>[extends<class_name>][implements<interface_name>] {
    // 定义属性部分
    <property_type><property1>;
    <property_type><property2>;
    <property_type><property3>;
    …
    // 定义方法部分
    function1();
    function2();
    function3();
    …
}
提示：上述语法中，中括号“[]”中的部分表示可以省略，竖线“|”表示“或关系”，例如 abstract|final，说明可以使用 abstract 或 final 关键字，但是两个关键字不能同时出现。
public：表示“共有”的意思。如果使用 public 修饰，则可以被其他类和程序访问。每个 Java 程序的主类都必须是 public 类，作为公共工具供其他类和程序使用的类应定义为 public 类。
abstract：如果类被 abstract 修饰，则该类为抽象类，抽象类不能被实例化，但抽象类中可以有抽象方法（使用 abstract 修饰的方法）和具体方法（没有使用 abstract 修饰的方法）。继承该抽象类的所有子类都必须实现该抽象类中的所有抽象方法（除非子类也是抽象类）。
final：如果类被 final 修饰，则不允许被继承。
class：声明类的关键字。
class_name：类的名称。
extends：表示继承其他类。
implements：表示实现某些接口。
property_type：表示成员变量的类型。
property：表示成员变量名称。
function()：表示成员方法名称。
```
### java类的命名规则
1. 类名应该以下划线（_）或字母开头，最好以字母开头。
2. 第一个字母最好大写，如果类名由多个单词组成，则每个单词的首字母最好都大写。
3. 类名不能为 Java 中的关键字，例如 boolean、this、int 等。
4. 类名不能包含任何嵌入的空格或点号以及除了下划线（_）和美元符号（$）字符之外的特殊字符。
### 创建一个新的类，就是创建一个新的数据类型。实例化一个类，就是得到类的一个对象。
### 声明成员变量的语法如下：
```
[public|protected|private][static][final]<type><variable_name>
- public、protected、private：用于表示成员变量的访问权限。
- static：表示该成员变量为类变量，也称为静态变量。
- final：表示将该成员变量声明为常量，其值无法更改。
- type：表示变量的类型。
- variable_name：表示变量名称。
```
### 声明成员方法的语法
```
public class Test {
    [public|private|protected][static]<void|return_type><method_name>([paramList]) {
        // 方法体
    }
}
- public、private、protected：表示成员方法的访问权限。
- static：表示限定该成员方法为静态方法。
- final：表示限定该成员方法不能被重写或重载。
- abstract：表示限定该成员方法为抽象方法。抽象方法不提供具体的实现，并且所属类型必须为抽象类。
```
### this 关键字是 Java 常用的关键字，可用于任何实例方法内指向当前对象，也可指向对其调用当前方法的对象，或者在需要当前类型对象引用时使用。
### java创建对象的方法，一共四种
1. 使用 new 关键字创建对象
- 类名 对象名 = new 类名()；
2. 调用 java.lang.Class 或者 java.lang.reflect.Constuctor 类的 newlnstance() 实例方法
```
java.lang.Class Class 类对象名称 = java.lang.Class.forName(要实例化的类全称);
类名 对象名 = (类名)Class类对象名称.newInstance();
```
3. 调用对象的 clone() 方法
- 类名对象名 = (类名)已创建好的类对象名.clone();
4. 调用 java.io.ObjectlnputStream 对象的 readObject() 方法
### 创建对象的示例代码
```
public class Student implements Cloneable {   
    // 实现 Cloneable 接口
    private String Name;    // 学生名字
    private int age;    // 学生年龄
    public Student(String name,int age) {    
        // 构造方法
        this.Name = name;
        this.age = age;
    }
    public Student() {
        this.Name = "name";
        this.age = 0;
    }
    public String toString() {
        return"学生名字："+Name+"，年龄："+age;
    }
    public static void main(String[] args)throws Exception {
        System.out.println("---------使用 new 关键字创建对象---------");
       
        // 使用new关键字创建对象
        Student student1 = new Student("小刘",22);
        System.out.println(student1);
        System.out.println("-----------调用 java.lang.Class 的 newInstance() 方法创建对象-----------");
       
        // 调用 java.lang.Class 的 newInstance() 方法创建对象
        Class c1 = Class.forName("Student");
        Student student2 = (Student)c1.newInstance();
        System.out.println(student2);
        System.out.println("-------------------调用对象的 clone() 方法创建对象----------");
        // 调用对象的 clone() 方法创建对象
        Student student3 = (Student)student2.clone();
        System.out.println(student3);
    }
}
```
### 匿名对象
```
public class Person {
    public String name; // 姓名
    public int age; // 年龄
    // 定义构造方法，为属性初始化
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    // 获取信息的方法
    public void tell() {
        System.out.println("姓名：" + name + "，年龄：" + age);
    }
    public static void main(String[] args) {
        new Person("张三", 30).tell(); // 匿名对象
    }
}
```
### java访问对象的属性和行为
- 对象名.属性(成员变量)    // 访问对象的属性
- 对象名.成员方法名()    // 访问对象的方法
### 对象被当作垃圾回收的情况
1. 对象的引用超过其作用范围
2. 对象被赋值为 null
### 在 Java 虚拟机的堆区，每个对象都可能处于以下三种状态之一。
1. 可触及状态：当一个对象被创建后，只要程序中还有引用变量引用它，那么它就始终处于可触及状态。
2. 可复活状态：当程序不再有任何引用变量引用该对象时，该对象就进入可复活状态。在这个状态下，垃圾回收器会准备释放它所占用的内存，在释放之前，会调用它及其他处于可复活状态的对象的 finalize() 方法，这些 finalize() 方法有可能使该对象重新转到可触及状态。
3. 不可触及状态：当 Java 虚拟机执行完所有可复活对象的 finalize() 方法后，如果这些方法都没有使该对象转到可触及状态，垃圾回收器才会真正回收它占用的内存。
### 类注释
- 类注释一般必须放在所有的“import”语句之后，类定义之前，主要声明该类可以做什么，以及创建者、创建日期、版本和包名等一些信息。以下是一个类注释的模板。
```
/**
 * @projectName（项目名称）: project_name
 * @package（包）: package_name.file_name
 * @className（类名称）: type_name
 * @description（类描述）: 一句话描述该类的功能
 * @author（创建人）: user 
 * @createDate（创建时间）: datetime  
 * @updateUser（修改人）: user 
 * @updateDate（修改时间）: datetime
 * @updateRemark（修改备注）: 说明本次修改内容
 * @version（版本）: v1.0
 */
```
### 方法注释
```
/**
 * @param num1: 加数1
 * @param num2: 加数2
 * @return: 两个加数的和
 */
public int add(int num1,int num2) {
    int value = num1 + num2;
    return value;
}
```
### 字段注释
```
/**
 * 用户名
 */
public String name;
```
### 访问控制符
- 类的访问控制符只能是空或者 public，方法和属性的访问控制符有 4 个，分别是 public、 private、protected 和 friendly，其中 friendly 是一种没有定义专门的访问控制符的默认情况。

| 访问范围 | private | friendly(默认) | protected | public |
| :----: | :----: | :----: | :----: | :----: |
| 同一个类 | 可访问 | 可访问 | 可访问 | 可访问 |
| 同一包中的其他类 | 不可访问 | 可访问 | 可访问 | 可访问 |
| 不同包中的子类 | 不可访问 | 不可访问 | 可访问 | 可访问 |
| 不同包中的非子类 | 不可访问 | 不可访问 | 不可访问 | 可访问 |
