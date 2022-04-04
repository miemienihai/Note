## 所以对象都继承自他

## 介绍他的几个方法
+ equals() 在拓展Object的equals手法时,看看资料


+ hashcode()   生成一个散列码
  1、HashCode的存在主要是为了查找的快捷性，HashCode是用来在散列存储结构中确定对象的存储地址的

  2、如果两个对象equals相等，那么这两个对象的HashCode一定也相同

  3、如果对象的equals方法被重写，那么对象的HashCode方法也尽量重写

  4、如果两个对象的HashCode相同，不代表两个对象就相同，只能说明这两个对象在散列存储结构中，存放于同一个位置
  5. 如果没有重写HashCode,那么它返回的就是对象地址的hashcode 而不是对象值的hashcode 


  + finalize() 垃圾回收工具
  + 如果你在子类重写,他会调用默认的finalize()函数
  + 当对象指向了null的时候,jvm会调研finalize()