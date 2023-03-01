+ c#的继承关系类似于 c++中的 class Zilei: public 父类
+ c#需要重写的函数用到的两个参数  abstract 和virtual 还有 Overiade
```C#
public class song {

protected void abstract Miege(int 123){};         //声明他以后你必须要去实现
protected void virtual Miege (int 123,int 124){};  // 只有写他你才能覆写


}

public class Songsan:song
{
void override Miege(int 123){};                    //明确写明白我这个是继承


}

```

+ 每个c#对象都继承自Object 所以 c#中的类隐式继承Objcet 即使你写了一个空类,他都继承了下面的这些方法
   + 如果你没有实现Tostring 默认返回的是这个类名称
   + 三种Euqals 方法 静态RefernceEquals(引用是否相等)
   + 哈希值 和类型返回
   + Finalize 好像跟内存释放十分贴切
   + 
```C#
公共 ToString 方法将 SimpleClass 对象转换为字符串表示形式，返回完全限定的类型名称。 在这种情况下，ToString 方法返回字符串“SimpleClass”。

三个用于测试两个对象是否相等的方法：公共实例 Equals(Object) 方法、公共静态 Equals(Object, Object) 方法和公共静态 ReferenceEquals(Object, Object) 方法。 默认情况下，这三个方法测试的是引用相等性；也就是说，两个对象变量必须引用同一个对象，才算相等。

公共 GetHashCode 方法：计算允许在经哈希处理的集合中使用类型实例的值。

公共 GetType 方法：返回表示 SimpleClass 类型的 Type 对象。

受保护 Finalize 方法：用于在垃圾回收器回收对象的内存之前释放非托管资源。

受保护 MemberwiseClone 方法：创建当前对象的浅表复制。


```

+ abstract 写在类的前面(注意) 表明这是一个抽象类,不能够实例化,我们一直说抽象类的实例化没有任何意义`
  + 那如果抽象类中在去写abstract 那么这个就是抽象类中 继承类必须去实现的方法
+ sealde 写在类的前面说明这个类你后面不能够在继承了.

