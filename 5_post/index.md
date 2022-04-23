# Malmquist指数分析容易混淆的概念

:(far fa-bell): 本文带你走进Malmquist指数分解的相关术语

### Malmquist指数概念介绍
&ensp;&ensp; Malmquist指数一般是**分析面板数据**的，涉及两个或更多时期的数据，每个 DMU **均有多个时期的投入和产出数值**。但是如果把面板数据拆分成单个年份利用普通的DEA模型来逐年分析，分别得到每年的技术效率值，这是不合理的，因为技术会随着时间而发生变化，**当技术进步是生产率提高的主要推动力的时候，只做技术效率分析是不全面的**。


&ensp;&ensp; Malmquist 全要素生产率指数（Malmquist total factor productivity index，简称 MI）的概念最早源于 Malmquist (1953)，因此将这一类指数命名为 Malmquist 指数。**不同类型的 Malmquist 指数，其区别仅仅是参比不同的前沿。**


:(fas fa-bolt):  **注意**：计算 Malmquist 指数是可以采用不同的距离函数与DEA模型的，**DEA 模型的选择与 Malmquist 指数类型的选择是相互独立的两个问题**。有些文章一提到malmuqist指数就是默认为CCR模型，这是不正确的，Malmquist 指数只是提供了一种指数的表达式，具体的模型选取是自己定的。


### Malmquist指数分解形式
- effch代表技术效率变化
> 全称：technical efficiency change  
> 简称：EC

- techch 代表技术进步/生产技术变化
> 全称：technological change  
> 简称：TC
 
- pech代表纯技术效率变化
> 全称：pure efficiency change or pure technical efficiency change  
> 简称：PEC

- sech代表规模效率变化
> 全称：scale-efficiency change  
> 简称：SEC

- tfpch 代表全要素生产率变化，也就是malmuqist指数  
> 全称：total factor productivity change

它们之间关系是：  
$effch=pech×sech$  
$tfpch=effch×techch$

