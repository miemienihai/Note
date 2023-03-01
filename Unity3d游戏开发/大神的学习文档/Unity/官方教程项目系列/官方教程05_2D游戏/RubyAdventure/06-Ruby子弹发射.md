### 子弹发射原理
+  1. 子弹的复制创造 Instantiate,第一参数 创建的GameObject对象, 第二 产生的位置, 第三 四元函数 这里是不可旋转 
  ```c
  Instantiate(_PerhabGameObject, _rigidbody2d.position + Vector2.up * 0.5f, Quaternion.identity)
  ```

 +   2.子弹的发射(本质是我们给子弹刚体施加一个力,所以发射这个属于物理系统层面)
    + 值得注意的是子弹刚体组件的初始化 是在awake中,也建议这样书写.

+  3. 子弹碰撞的问题
   + 我们值得注意的是子弹往往从主角身上产生,所以他会与主角先发生碰撞,然后消失,这样是不对的,通过设置Layer 自定义他们的物理适用的层级
   + 子弹与子弹也记得取消.
+  4. 子弹输入的问题
   + 这个就跟按键获取方式有关联了,我们想要按下一个发射一个,同时这个获取写在Update中,FixUpadte 会因为获取次数太低,而导致按键不灵敏.
   + Input.GetKeyDown(KeyCode.X)