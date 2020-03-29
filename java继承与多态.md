### java类的封装的具体步骤
1. 修改属性的可见性来限制对属性的访问，一般设为 private。
2. 为每个属性创建一对赋值（setter）方法和取值（getter）方法，一般设为 public，用于属性的读写。
3. 在赋值和取值方法中，加入属性控制语句（对属性值的合法性进行判断）。
4. 举个例子
```
public class Employee {
    private String name; // 姓名
    private int age; // 年龄
    private String phone; // 联系电话
    private String address; // 家庭住址
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
        // 对年龄进行限制
        if (age < 18 || age > 40) {
            System.out.println("年龄必须在18到40之间！");
            this.age = 20; // 默认年龄
        } else {
            this.age = age;
        }
    }
    public String getPhone() {
        return phone;
    }
    public void setPhone(String phone) {
        this.phone = phone;
    }
    public String getAddress() {
        return address;
    }
    public void setAddress(String address) {
        this.address = address;
    }
}
```
### Java 中的继承就是在已经存在类的基础上进行扩展，从而产生新的类。已经存在的类称为父类、基类或超类，而新产生的类称为子类或派生类。在子类中，不仅包含父类的属性和方法，还可以增加新的属性和方法。
- 继承语法
```
修饰符 class class_name extends extend_class {
    // 类的主体
}
```
### 使用继承的注意点
1. 子类一般比父类包含更多的属性和方法。
2. 父类中的 private 成员在子类中是不可见的，因此在子类中不能直接使用它们。
3. 父类和其子类间必须存在“是一个”即“is-a”的关系，否则不能用继承。但也并不是所有符合“is-a”关系的都应该用继承。例如，正方形是一个矩形，但不能让正方形类来继承矩形类，因为正方形不能从矩形扩展得到任何东西。正确的继承关系是正方形类继承图形类。
4. Java 只允许单一继承（即一个子类只能有一个直接父类），C++ 可以多重继承（即一个子类有多个直接父类）。
### super关键字
- 由于子类不能继承父类的构造方法，因此，如果要调用父类的构造方法，可以使用 super 关键字。super 可以用来访问父类的构造方法、普通方法和属性。
- super 关键字的功能：
1. 在子类的构造方法中显式的调用父类构造方法
2. 访问父类的成员方法和变量。
- super 关键字可以在子类的构造方法中显式地调用父类的构造方法，基本格式如下：
- super(parameter-list);
### super调用父类构造方法例子
```
public class Person {
    public Person(String name, int age) {
    }
    public Person(String name, int age, String sex) {
    }
}
------------------------------------------------------------------
public class Student extends Person {
    public Student(String name, int age, String birth) {
        super(name, age); // 调用父类中含有2个参数的构造方法
    }
    public Student(String name, int age, String sex, String birth) {
        super(name, age, sex); // 调用父类中含有3个参数的构造方法
    }
}
```
### super访问父类成员例子
```
- 父类调用成员属性
class Person {
    int age = 12;
}
class Student extends Person {
    int age = 18;
    void display() {
        System.out.println("学生年龄：" + super.age);
    }
}
class Test {
    public static void main(String[] args) {
        Student stu = new Student();
        stu.display();
    }
}
- 父类调用成员函数
class Person {
    void message() {
        System.out.println("This is person class");
    }
}
class Student extends Person {
    void message() {
        System.out.println("This is student class");
    }
    void display() {
        message();
        super.message();
    }
}
class Test {
    public static void main(String args[]) {
        Student s = new Student();
        s.display();
    }
}
```
### super和this的区别
**this 指的是当前对象的引用，super 是当前对象的父对象的引用。**
1. super 关键字的用法：
- super.父类属性名：调用父类中的属性
- super.父类方法名：调用父类中的方法
- super()：调用父类的无参构造方法
- super(参数)：调用父类的有参构造方法
2. this 关键字的用法：
- this.属性名：表示当前对象的属性
- this.方法名(参数)：表示调用当前对象的方法
3. 子类和父类中变量或方法名称相同时，用 super 关键字来访问。可以理解为 super 是指向自己父类对象的一个指针。在子类中调用父类的构造方法。
4. this 是自身的一个对象，代表对象本身，可以理解为 this 是指向对象本身的一个指针。在同一个类中调用其它方法。
5. this 和 super 不能同时出现在一个构造方法里面，因为 this 必然会调用其它的构造方法，其它的构造方法中肯定会有 super 语句的存在，所以在同一个构造方法里面有相同的语句，就失去了语句的意义，编译器也不会通过。
6. this( ) 和 super( ) 都指的是对象，所以，均不可以在 static 环境中使用，包括 static 变量、static 方法和 static 语句块。
从本质上讲，this 是一个指向对象本身的指针, 然而 super 是一个 Java 关键字。
### 对象类型转换
**对象类型转换，是指存在继承关系的对象，不是任意类型的对象。当对不存在继承关系的对象进行强制类型转换时，会抛出 Java 强制类型转换（java.lang.ClassCastException）异常。**
1. 向上转型
- 父类引用指向子类对象为向上转型
- 语法格式为`fatherClass obj = new sonClass();`
2. 向下转型
- 子类对象指向父类引用为向下转型
- 语法格式为`sonClass obj = (sonClass) fatherClass;`
### 方法重载如果同一个类中包含了两个或两个以上方法名相同的方法，但形参列表不同，这种情况被称为方法重载（overload）。
- 方法重载的要求是两同一不同：同一个类中方法名相同，参数列表不同。至于方法的其他部分，如方法返回值类型、修饰符等，与方法重载没有任何关系。
### 方法重写
1. 在子类中如果创建了一个与父类中相同名称、相同返回值类型、相同参数列表的方法，只是方法体中的实现不同，以实现不同于父类的功能，这种方式被称为方法重写（override），又称为方法覆盖。
2. 遵循规则
- 参数列表必须完全与被重写的方法参数列表相同。
- 返回的类型必须与被重写的方法的返回类型相同（Java1.5 版本之前返回值类型必须一样，之后的 Java 版本放宽了限制，返回值类型必须小于或者等于父类方法的返回值类型）。
- 访问权限不能比父类中被重写方法的访问权限更低（public>protected>default>private）。
- 重写方法一定不能抛出新的检査异常或者比被重写方法声明更加宽泛的检査型异常。例如，父类的一个方法声明了一个检査异常 IOException，在重写这个方法时就不能抛出 Exception，只能拋出 IOException 的子类异常，可以抛出非检査异常。
- 重写的方法可以使用 @Override 注解来标识。
- 父类的成员方法只能被它的子类重写。
- 声明为 final 的方法不能被重写。
- 声明为 static 的方法不能被重写，但是能够再次声明。
- 构造方法不能被重写。
- 子类和父类在同一个包中时，子类可以重写父类的所有方法，除了声明为 private 和 final 的方法。
- 子类和父类不在同一个包中时，子类只能重写父类的声明为 public 和 protected 的非 final 方法。
- 如果不能继承一个方法，则不能重写这个方法。
### java多态
1. 多态性是面向对象编程的又一个重要特征，它是指在父类中定义的属性和方法被子类继承之后，可以具有不同的数据类型或表现出不同的行为，这使得同一个属性或方法在父类及其各个子类中具有不同的含义。
2. 实现多态的三个条件
- 继承：在多态中必须存在有继承关系的子类和父类。
- 重写：子类对父类中某些方法进行重新定义，在调用这些方法时就会调用子类的方法。
- 向上转型：在多态中需要将子类的引用赋给父类对象，只有这样该引用才既能可以调用父类的方法，又能调用子类的方法。
###  Java instanceof 关键字的几种用法
1. 声明一个 class 类的对象，判断 obj 是否为 class 类的实例对象（很普遍的一种用法）
```
Integer integer = new Integer(1);
System.out.println(integer instanceof  Integer);    // true
```
2. 声明一个 class 接口实现类的对象 obj，判断 obj 是否为 class 接口实现类的实例对象
```
Java 集合中的 List 接口有个典型实现类 ArrayList。
public class ArrayList<E> extends AbstractList<E>
        implements List<E>, RandomAccess, Cloneable, java.io.Serializable

所以我们可以用 instanceof 运算符判断 ArrayList 类的对象是否属于 List 接口的实例，如果是返回 true，否则返回 false。
ArrayList arrayList = new ArrayList();
System.out.println(arrayList instanceof List);    // true

或者反过来也是返回 true
List list = new ArrayList();
System.out.println(list instanceof ArrayList);    // true
```
3. obj 是 class 类的直接或间接子类
```
Person p1 = new Person();
Person p2 = new Man();
Man m1 = new Man();
System.out.println(p1 instanceof Man);    // false
System.out.println(p2 instanceof Man);    // true
System.out.println(m1 instanceof Man);    // true
```
### Java 语言提供了两种类，分别为具体类和抽象类。
1. 在面向对象的概念中，所有的对象都是通过类来描绘的，但是反过来，并不是所有的类都是用来描绘对象的，如果一个类中没有包含足够的信息来描绘一个具体的对象，那么这样的类称为抽象类。
2. 语法格式
```
<abstract>class<class_name> {
    <abstract><type><method_name>(parameter-iist);
}
其中，abstract 表示该类或该方法是抽象的；class_name 表示抽象类的名称；method_name 表示抽象方法名称，parameter-list 表示方法参数列表。
```
3. 抽象方法的三个特征
- 抽象方法没有方法体
- 抽象方法必须存在于抽象类中
- 子类重写父类时，必须重写父类所有的抽象方法
4. 抽象类的定义和使用规则
- 抽象类和抽象方法都要使用 abstract 关键字声明。
- 如果一个方法被声明为抽象的，那么这个类也必须声明为抽象的。而一个抽象类中，可以有 0~n 个抽象方法，以及 0~n 个具体方法。
- 抽象类不能实例化，也就是不能使用 new 关键字创建对象。
### java接口
1. 抽象类是从多个类中抽象出来的模板，如果将这种抽象进行的更彻底，则可以提炼出一种更加特殊的“抽象类”——接口（Interface）。接口是 Java 中最重要的概念之一，它可以被理解为一种特殊的类，不同的是接口的成员没有执行体，是由全局常量和公共的抽象方法所组成。
2. Java 接口的定义方式与类基本相同，不过接口定义使用的关键字是 interface
```
定义语法
[public] interface interface_name [extends interface1_name[, interface2_name,…]] {
    // 接口体，其中可以包含定义常量和声明方法
    [public] [static] [final] type constant_name = value;    // 定义常量
    [public] [abstract] returnType method_name(parameter_list);    // 声明方法
}
//语法说明
public 表示接口的修饰符，当没有修饰符时，则使用默认的修饰符，此时该接口的访问权限仅局限于所属的包；
interface_name 表示接口的名称。接口名应与类名采用相同的命名规则，即如果仅从语法角度来看，接口名只要是合法的标识符即可。如果要遵守 Java 可读性规范，则接口名应由多个有意义的单词连缀而成，每个单词首字母大写，单词与单词之间无需任何分隔符。
extends 表示接口的继承关系；
interface1_name 表示要继承的接口名称；
constant_name 表示变量名称，一般是 static 和 final 型的；
returnType 表示方法的返回值类型；
parameter_list 表示参数列表，在接口中的方法是没有方法体的。
注意：一个接口可以有多个直接父接口，但接口只能继承接口，不能继承类。
```
3. 接口的限制特征
- 具有 public 访问控制符的接口，允许任何类使用；没有指定 public 的接口，其访问将局限于所属的包。
- 方法的声明不需要其他修饰符，在接口中声明的方法，将隐式地声明为公有的（public）和抽象的（abstract）。
- 在 Java 接口中声明的变量其实都是常量，接口中的变量声明，将隐式地声明为 public、static 和 final，即常量，所以接口中定义的变量必须初始化。
- 接口没有构造方法，不能被实例化。
4. 实现接口
- 接口的主要用途就是被实现类实现，一个类可以实现一个或多个接口，继承使用 extends 关键字，实现则使用 implements 关键字。因为一个类可以实现多个接口，这也是 Java 为单继承灵活性不足所作的补充。
```
实现语法
<public> class <class_name> [extends superclass_name] [implements interface1_name[, interface2_name…]] {
    // 主体
}
语法说明
public：类的修饰符；
superclass_name：需要继承的父类名称；
interface1_name：要实现的接口名称。
```
5. 实现接口需要的注意
- 实现接口与继承父类相似，一样可以获得所实现接口里定义的常量和方法。如果一个类需要实现多个接口，则多个接口之间以逗号分隔。
- 一个类可以继承一个父类，并同时实现多个接口，implements 部分必须放在 extends 部分之后。
- 一个类实现了一个或多个接口之后，这个类必须完全实现这些接口里所定义的全部抽象方法（也就是重写这些抽象方法）；否则，该类将保留从父接口那里继承到的抽象方法，该类也必须定义成抽象类。
### java内部类
1. 在类内部可定义成员变量和方法，且在类内部也可以定义另一个类。如果在类 Outer 的内部再定义一个类 Inner，此时类 Inner 就称为内部类（或称为嵌套类），而类 Outer 则称为外部类（或称为宿主类）。
2. 内部类拥有外部类的所有元素的访问权限。
3. 内部类的特点
- 内部类仍然是一个独立的类，在编译之后内部类会被编译成独立的.class文件，但是前面冠以外部类的类名和$符号。
- 内部类不能用普通的方式访问。内部类是外部类的一个成员，因此内部类可以自由地访问外部类的成员变量，无论是否为 private 的。
- 内部类声明成静态的，就不能随便访问外部类的成员变量，仍然是只能访问外部类的静态成员变量。
4. 关于内部类的说明
- 外部类只有两种访问级别：public 和默认；内部类则有 4 种访问级别：public、protected、 private 和默认。
- 在外部类中可以直接通过内部类的类名访问内部类。
- InnerClass ic = new InnerClass();    // InnerClass为内部类的类名
- 在外部类以外的其他类中则需要通过内部类的完整类名访问内部类。
- Test.InnerClass ti = newTest().new InnerClass();    // Test.innerClass是内部类的完整类名
- 内部类与外部类不能重名。
5. 内部类的分类
- 实例内部类
```
public class Outer {
    class Inner1 {
    }
    Inner1 i = new Inner1(); // 不需要创建外部类实例
    public void method1() {
        Inner1 i = new Inner1(); // 不需要创建外部类实例
    }
    public static void method2() {
        Inner1 i = new Outer().new inner1(); // 需要创建外部类实例
    }
    class Inner2 {
        Inner1 i = new Inner1(); // 不需要创建外部类实例
    }
}
class OtherClass {
    Outer.Inner i = new Outer().new Inner(); // 需要创建外部类实例
}
```
- 静态内部类
```
public class Outer {
    static class Inner {
        int a = 0;    // 实例变量a
        static int b = 0;    // 静态变量 b
    }
}
class OtherClass {
    Outer.Inner oi = new Outer.Inner();
    int a2 = oi.a;    // 访问实例成员
    int b2 = Outer.Inner.b;    // 访问静态成员
}
-----------------------------------------------
public class Outer {
    int a = 0;    // 实例变量
    static int b = 0;    // 静态变量
    static class Inner {
        Outer o = new Outer;
        int a2 = o.a;    // 访问实例变量
        int b2 = b;    // 访问静态变量
    }
}
```
- 局部内部类
1. 局部内部类与局部变量一样，不能使用访问控制修饰符（public、private 和 protected）和 static 修饰符修饰。
2. 局部内部类只在当前方法中有效。
3. 局部内部类中不能定义 static 成员。
4. 局部内部类中还可以包含内部类，但是这些内部类也不能使用访问控制修饰符（public、private 和 protected）和 static 修饰符修饰。
5. 在局部内部类中可以访问外部类的所有成员。
6. 在局部内部类中只可以访问当前方法中 final 类型的参数与变量。如果方法中的成员与外部类中的成员同名，则可以使用 <OuterClassName>.this.<MemberName> 的形式访问外部类中的成员。

```
    public class Test {
    int a = 0;
    int d = 0;
    public void method() {
        int b = 0;
        final int c = 0;
        final int d = 10;
        class Inner {
            a2 = a;    // 访问外部类中的成员
            // int b2 = b;    // 编译出错
            int c2 = c;    // 访问方法中的成员
            int d2 = d;    // 访问方法中的成员
            int d3 = Test.this.d;    //访问外部类中的成员
        }
        Inner i = new Inner();
        System.out.println(i.d2);    // 输出10
        System.out.printIn(i.d3);    // 输出0
    }
    public static void main(String[] args) {
        Test t = new Test();
        t.method();
    }
}
```
### java匿名类
1. 匿名类是指没有类名的内部类，必须在创建时使用 new 语句来声明类。
2. 两种实现方法
- 继承一个类，重写其方法。
- 实现一个接口（可以是多个），实现其方法。
```
public class Out {
    void show() {
        System.out.println("调用 Out 类的 show() 方法");
    }
}
public class TestAnonymousInterClass {
    // 在这个方法中构造一个匿名内部类
    private void show() {
        Out anonyInter = new Out() {
            // 获取匿名内部类的实例
            void show() {
                System.out.println("调用匿名类中的 show() 方法");
            }
        };
        anonyInter.show();
    }
    public static void main(String[] args) {
        TestAnonymousInterClass test = new TestAnonymousInterClass();
        test.show();
    }
}
```
3. 匿名类特点
- 匿名类和局部内部类一样，可以访问外部类的所有成员。如果匿名类位于一个方法中，则匿名类只能访问方法中 final 类型的局部变量和参数。
```
public static void main(String[] args) {
    int a = 10;
    final int b = 10;
    Out anonyInter = new Out() {
        void show() {
            // System.out.println("调用了匿名类的 show() 方法"+a);    // 编译出错
            System.out.println("调用了匿名类的 show() 方法"+b);    // 编译通过
        }
    };
    anonyInter.show();
}
```
- 匿名类中允许使用非静态代码块进行成员初始化操作。
```
Out anonyInter = new Out() {
    int i; {    // 非静态代码块
        i = 10;    //成员初始化
    }
    public void show() {
        System.out.println("调用了匿名类的 show() 方法"+i);
    }
};
```
- 匿名类的非静态代码块会在父类的构造方法之后被执行。
### java新特性
1. Java 中局部内部类和匿名内部类访问的局部变量必须由 final 修饰，以保证内部类和外部类的数据一致性。但从 Java 8 开始，我们可以不加 final 修饰符，由系统默认添加，当然这在 Java 8 以前的版本是不允许的。Java 将这个功能称为 Effectively final 功能。
### java的lambda表达式
1. Lambda 表达式（Lambda expression）是一个匿名函数，基于数学中的λ演算得名，也可称为闭包（Closure）。现在很多语言都支持 Lambda 表达式，如 C++、C#、Java、 Python 和 JavaScript 等。
