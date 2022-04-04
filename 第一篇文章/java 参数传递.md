## 参数传递在java
### 总的来说还是c++的思想
1. 如果是int这种基本类型,我们认为 让在方法的传递时是以值进行传递,
2. 如果是引用类型,传递就是引用类型,这与c++的内涵一样,参数依然可以改变原来指向的变量.
3. 有的说引用类型,也是以值传递. 参数都重新赋给了另一个变量,当然无法改变原来的值,所以有了值传递的错觉,
```java
public static void changeData(StringBuffer strBuf) {

           strBuf = new StringBuffer("Hi ");
           strBuf.append("World!");

    }
```