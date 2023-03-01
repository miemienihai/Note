## 分为两种敌人
+ 第一种单体伤害 使用OnTriggerenter2D进入函数
+ 第二种站立伤害 使用OnTriggerStay2D 这个函数不断检查是否站在上面,如果是一直调用.
  + 同时 人物你需要设置Sleep Mode 模式为Never Sleep 做到不断的调用刚体组件,发出碰撞. 


## 碰撞伤害解析
+ 分为触发器触发伤害 和碰撞伤害
+  OnTriggerEnter2D  和OnCollisionEnter2D 不同的方式, 前者参数为Collider2D ,后者参数为Collision2D
+  注意他们的后缀,后者需要先调用Collision2Dr.gameObject.GetComponent才能拿到组件