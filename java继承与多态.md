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
