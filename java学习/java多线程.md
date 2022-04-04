```java
//整个线程创建流程
private Thread theadA;
theadA= new Thread(new Runnable() {
       // 都来自于 Runnable接口 ，Runnable接口中有创建Thread的函数，用来实例化
 
        int count=0;
       
       
       
        @Override  // 真正线程实现的代码地方就在run 方法中，Start 也是调用run
        public void run() {
            while (true){
            progressBar.setValue(++count);
            try{
                Thread.sleep(100);
                theadB.join();

            }
            catch (Exception e){
                e.printStackTrace();
            }

            if(count ==100)
                break;



        }}
    });

    theadA.start();  //调用run
```


```java
synchronized(Object){
//这里书写我们的线程执行代码

}
```