学习文档   
https://geek-docs.com/csharp/csharp-tutorial/csharp-datetime.html

### 重要概念
+ DateTime 是我们时间类 与其相关的是TimeSpan 时间间隔

### 本地时间获取
> DateTime xxxx= DateTime.Now;
> DateTime xxxx =DateTime.Utc;


### Unix 时间的计算
> long unixTime =DateTimeOffset.UtcNow.ToUnixTimeSecondes();
+ 本质还是通过UtcNow来获取的


```C#
string startTime = "7:00 AM";
string endTime = "8:30 PM";  //DateTime提供了一个非常强大的Parse 语法分析函数提供转换

            TimeSpan elapsed = DateTime.Parse(endTime).Subtract(DateTime.Parse(startTime));   //TimeDate 可以Subtract计算中间时间
            using System;

            DateTime now = DateTime.Today;
            DateTime borodino_battle = new DateTime(1812, 9, 7);

            TimeSpan diff = now - borodino_battle;  //也可以通过减号直接计算得到TimeSpan

```
### 细节处理
> timeSinceSunset.TotalMinutes / sunsetToSunriseDuration.TotalMinutes;
> 我们这里想要计算两个时间之间的比例,如果你采用minutes 那么计算的是两个时间的秒的部分,而TotalMinuts 代表的是时间的总秒数.

> _CunrentTime.TimeOfDay 当前时间的timespan


