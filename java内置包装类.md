**在 Java 的设计中提倡一种思想，即一切皆对象。但是从数据类型的划分中，我们知道 Java 中的数据类型分为基本数据类型和引用数据类型，但是基本数据类型怎么能够称为对象呢？于是 Java 为每种基本数据类型分别设计了对应的类，称之为包装类（Wrapper Classes），也有地方称为外覆类或数据类型类。**
### 装箱与拆箱
- 基本数据类型转换为包装类的过程称为装箱，例如把 int 包装成 Integer 类的对象；包装类变为基本数据类型的过程称为拆箱，例如把 Integer 类的对象重新简化为 int。
- 手动实例化一个包装类称为手动拆箱装箱。Java 1.5 版本之前必须手动拆箱装箱，之后可以自动拆箱装箱，也就是在进行基本数据类型和对应的包装类转换时，系统将自动进行装箱及拆箱操作，不用在进行手工操作，为开发者提供了更多的方便。例如：
```
public class Demo {
    public static void main(String[] args) {
        int m = 500;
        Integer obj = m;  // 自动装箱
        int n = obj;  // 自动拆箱
        System.out.println("n = " + n);//n = 500
      
        Integer obj1 = 500;
        System.out.println("obj等价于obj1返回结果为" + obj.equals(obj1));//obj等价于obj1返回结果为true
    }
}
```
### 包装类的应用
1. 实现 int 和 Integer 的相互转换
2. 将字符串转换为数值类型
3. 将整数转换为字符串
### Object 是 Java 类库中的一个特殊类，也是所有类的父类。也就是说，Java 允许把任何类型的对象赋给 Object 类型的变量。当一个类被定义后，如果没有指定继承的父类，那么默认父类就是 Object 类。
### `equals`与`==`之间的关系
### 在前面学习字符串比较时，曾经介绍过两种比较方法，分别是==运算符和 equals() 方法，==运算符是比较两个引用变量是否指向同一个实例，equals() 方法是比较两个对象的内容是否相等，通常字符串的比较只是关心内容是否相等。
### getClass() 方法
- getClass() 方法返回对象所属的类，是一个 Class 对象。通过 Class 对象可以获取该类的各种信息，包括类名、父类以及它所实现接口的名字等。
### Integer 类的构造方法(主要有两个)
1. Integer(int value)：构造一个新分配的 Integer 对象，它表示指定的 int 值。
2. Integer(String s)：构造一个新分配的 Integer 对象，它表示 String 参数所指示的 int 值。
### Float类的构造方法(主要有三个)
1. Float(double value)：构造一个新分配的 Float 对象，它表示转换为 float 类型的参数。
2. Float(float value)：构造一个新分配的 Float 对象，它表示基本的 float 参数。
3. Float(String s)：构造一个新分配的 Float 对象，它表示 String 参数所指示的 float 值。
### Double类的构造方法(主要有两个)
1. Double(double value)：构造一个新分配的 Double 对象，它表示转换为 double 类型的参数。
2. Double(String s)：构造一个新分配的 Double 对象，它表示 String 参数所指示的 double 值。
### Number类
- Number 是一个抽象类，也是一个超类（即父类）。Number 类属于 java.lang 包，所有的包装类（如 Double、Float、Byte、Short、Integer 以及 Long）都是抽象类 Number 的子类。
### Character类
- Character 类是字符数据类型 char 的包装类。Character 类的对象包含类型为 char 的单个字段，这样能把基本数据类型当对象来处理，
### Boolean 类的构造方法(主要有两种)
- Boolean(boolean boolValue);
- Boolean(String boolString);
### Byte 类的构造方法(主要有两种)
1. Byte(byte value)
- 通过这种方法创建的 Byte 对象，可以表示指定的 byte 值。例如，下面的示例将 5 作为 byte 类型变量，然后再创建 Byte 对象。
```
byte my_byte = 5;
Byte b = new Byte(my_byte);
```
2. Byte(String s)
- 通过这个方法创建的 Byte 对象，可表示 String 参数所指定的 byte 值。例如，下面的示例将 5 作为 String 类型变量，然后再创建 Byte 对象。
```
String my_byte = "5";
Byte b = new Byte(my_byte);
```
### System 类位于 java.lang 包，代表当前 Java 程序的运行平台，系统级的很多属性和控制方法都放置在该类的内部。由于该类的构造方法是 private 的，所以无法创建该类的对象，也就是无法实例化该类。
