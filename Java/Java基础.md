# 一、数据类型

## 包装类型

byte：Java中最小的数据类型，在内存中占8位(bit)，即1个字节，取值范围-128~127，默认值0

short：短整型，在内存中占16位，即2个字节，取值范围-32768~32717，默认值0

int：整型，用于存储整数，在内在中占32位，即4个字节，取值范围-2147483648~2147483647，默认值0

long：长整型，在内存中占64位，即8个字节-2^63~2^63-1，默认值0L

float：浮点型，在内存中占32位，即4个字节，用于存储带小数点的数字（与double的区别在于float类型有效小数点只有6~7位），默认值0

double：双精度浮点型，用于存储带有小数点的数字，在内存中占64位，即8个字节，默认值0

char：字符型，用于存储单个字符，占16位，即2个字节，取值范围0~65535，默认值为空

boolean：布尔类型，占1个字节，用于判断真或假（仅有两个值，即true、false），默认值false


Java中的数据类型分为引用数据类型和基本数据类型。

   引用数据类型分3种：类，接口，数组；

   基本数据类型又分布尔类型和数值类型；

       布尔类型：boolean（逻辑型） trure or false默认是false；

       数值类型分定点类型和浮点类型；

           定点类型分整数类型和字符型；

## 编译、反编译
- 编译：javac Main.java
- 查看反编译：javap -c Main

## 自动拆装箱

- [自动拆装箱细节](https://www.cnblogs.com/qcblog/p/7670159.html)
- 编译级别的动作
- 自动装箱过程是通过调用valueOf方法实现（如Integer.valueOf(10)）
- 而拆箱过程是通过调用包装器的 xxxValue方法实现（如Integer.intValue(a)）。

- 编译后能看到真实的调用，反编译代码：javac Main.java javap -c Main
```Java
Integer i = 10;//装箱
int n = i;//拆箱
```

```Java
Compiled from "Main.java"
public class Main {
  public Main();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public static void main(java.lang.String[]);
    Code:
       0: bipush        10
       2: invokestatic  #2                  // Method java/lang/Integer.valueOf:(I)Ljava/lang/Integer;
       5: astore_1
       6: aload_1
       7: invokevirtual #3                  // Method java/lang/Integer.intValue:()I
      10: istore_2
      11: return
}
```

## 缓存池

new Integer(123)和Integer.valueOf(123)，valueOf运用了cache缓存池

Integer a = 123;//自动用了装箱，valueOf

基本类型对应的缓存池如下：
- boolean values true and false
- byte values all bytes -128 and 127
- short values between -128 and 127
- int values between -128 and 127
- char values 127 char，0-127， range \u0000 and \u007F

## 负数存储

- 正数在计算机中是以原码形式存在的；
- 负数在计算机中是以其补码形式存在的，就是负数的绝对值的原码转为二进制再按位取反后加1。
- 负数2的补码就是最方便的方式。它的便利体现在，所有的加法运算可以使用同一种电路完成。无论是加负数或者加正数
- 相当于分成了-Y=0-Y，11111111 - Y + 1，借位，分成了两步
- （~a）先把a变为-a，-a - 1 = （~a）;

## todo
### 编码的字符集
### char需要进一步了解编码格式\u代表什么