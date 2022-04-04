## Integer String等
+ 包装类一旦构造就不能改变,
+ 同时不能继承(final)包装类
+ ArrayList< class > ArrayList这个数组实例化的时候 class 肯定接受的是java中的对象,所以,基本类型int ArrayList<int> 不成立,但是虽然调用ArrayList<Interger> 方便,但是不如int []数组效率高

## 自动装箱和拆箱
+ int 和Interger之间的转换是编译器自动进行的,非常顺滑,
+ 自动装箱和拆箱这是编译器的操作,
+ 记住 Integer包装类他们的值不能改变的