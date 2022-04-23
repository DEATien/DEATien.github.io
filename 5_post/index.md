# 手把手教你利用Python写DEA模型

:(far fa-bell): **本文带你从零开始完成一个DEA模型的python代码**
<script src="https://kit.fontawesome.com/5519c56e9e.js" crossorigin="anonymous"></script>

### 引言
<i class="fa-solid fa-child-reaching"></i>  **恭喜你成为杜老师师门中的一员！**  

:(fas fa-bolt): 利用编程语言来实现DEA模型是每一个**DEAer**的必备技能，目前市面上有各类DEA计算效率的可视化软件，但是对于免费的软件，可实现的功能十分少，只能简单做CCR 或者 BCC模型，而对于付费的软件呢，又是十分地贵，只能实现主流的已有的模型。如果我们自己对现有的模型进行改动，用这些软件是无法实现的。

<i class="fa-solid fa-graduation-cap"></i>  那么我们就十分有必要自己去实现DEA模型，因此本文将从零开始带你完成一个DEA模型的python代码。由于咱们师门的同学大部分都是利用**Matlab+Yalmip+CPLEX**来完成DEA模型的求解与建模，在此基础上，本文就直接借助CPLEX求解器结合Python语言来展开本教程。

<i class="fa-solid fa-arrow-right-long"></i> 如果你刚进师门的话，请点击一下该链接自行注册下载CPLEX学术版，[点击这里](https://www.ibm.com/cn-zh/products/ilog-cplex-optimization-studio?lnk=STW_CN_STESCH&lnk2=trial_ILOGOptStudio&pexp=def&psrc=none&mhsrc=ibmsearch_a&mhq=cplex)，或者直接联系你的师兄师姐，让他们发送安装给你。 <i class="fa-regular fa-face-grin-squint-tears"></i>

<i class="fa-brands fa-golang"></i> 如果一切准备就绪的话，那让我们开始吧！

### 准备工作
1. Python的下载、安装与配置请大家自行搜索相关教程。
2. 下载后Python后，你还需要安装一个代码编辑器来编写代码，主流的代码编辑器有很多，选择一款喜欢的即可。（例如pycharm等）
3. 安装好后代码编辑器后，需要配置Python环境，网上相关教程有很多，这里也不展开介绍了。
4. 打开系统的cmd窗口，在CMD命令行依次输入：
    ```cmd
    pip install pandas
    ```
- ⇈ `pandas`提供了大量能使我们快速便捷地处理数据的函数和方法，我们主要利用pandas进行数据的读取与索引

    ```cmd
    pip install pyomo
    ```
- ⇈ 一个规划问题建模的python包，你可以理解为类似于yalmip

    ```cmd
    pip install openpyxl
    ```
-  ⇈ `openpyxl`主要是一个用来读写 `Excel 2010 xlsx/xlsm/xltx/xltm` 的 Python 库

5.准备工作就绪了之后，就可以开始我们的建模之路了。在此之前，还是希望同学们先掌握一些Python基本语法再食用本文，包含但不限于Python的基本语句、基本数据结构、函数、类与方法等知识。

### 模型构建
<i class="fa-solid fa-pencil"></i> 我们的实例数据为：[参考实例数据](/测试数据.xlsx)，本文以较为实用的DDF模型为例进行建模，并以Python中**函数**的形式进行代码的编写，请将实例数据与该`.py`文件放在同一个文件夹中。
##### DDF模型
首先，我们给出弱可处置性与CRS假设下DDF模型的数学表达式：
$$
\begin{aligned}
\max \beta \\\\
s.t. & \sum_{j=1}^{n} \lambda_{j} x_{i j} \leq(1-\beta) x_{i0}\\\\
& \sum_{j=1}^{n} \lambda_{j} y_{r j} \geq(1+\beta) x_{r0}\\\\
& \sum_{j=1}^{n} \lambda_{j} u_{t j} =(1-\beta) u_{t0}\\\\
&\lambda \geq 0
\end{aligned}
$$
##### 导入相关库
```python
from pyomo.environ import *  
import pandas as pd
```
##### 定义整体框架
数据的投入为：`输入1，输入2`；产出为：`输出1，输出2，输出3`；非期望产出为：`非期望输出1，非期望输出2`
1. 首先读取相关数据：
```python
data =pd.read_excel('测试数据.xlsx')
```
2. 定义投入产出及相关变量
```python
Input = ['输入1','输入2']
Output = ['输出1','输出2','输出3']
Undesirable_Output =['非期望输出1','非期望输出2']
K = list(range(data.shape[0]))
# K为data的行数，即代表DMU的个数。

`list(range(data.shape[0]))`将其转换为列表形式，如果有5个DMU，则`K = [1,2,3,4,5]`
```
3. 定义求解框架，总共有K个DMU，我们需要对这`K`个DMU进行循环求解，每次求解一个DMU，并记当前求解的DMU为`i`。在此之前，还需要定义一个TE空列表来储存将来的效率值。
```python
TE = [] # 储存将来的效率值
for i in K:
    # 当前求解第i个决策单元
    eff = DDFmodel(i, K, data, Input, Output, Undesirable_Output)
    TE.append(eff) # 记录每次求解的值
data['DDF效率'] = TE # data新增一列，记录为效率值
```
> 其中DDFmodel函数为下一节需要写的函数

4. 综上所述，建立`run()`函数，返回值为`data`
```python
def run():
    data =pd.read_excel('测试数据.xlsx')
    Input = ['输入1','输入2']
    Output = ['输出1','输出2','输出3']
    Undesirable_Output =['非期望输出1','非期望输出2']
    K = list(range(data.shape[0]))
    TE = []
    for i in K:
        eff = DDFmodel(i, K, data, Input, Output, Undesirable_Output)
        TE.append(eff)
    data['DDF效率'] = TE
    return data
```

##### 定义DDF求解模型
本节将讲解`DDFmodel`函数的具体写法，首先我们通过运行`run()`函数，可以为`DDFmodel`函数传入`i, K, data, Input, Output, Undesirable_Output`的值，接下来将搭建模型。
1. 创建求解环境
```python
model = ConcreteModel()
```
2. 创建决策变量  
> DDF模型的决策变量为: $\lambda$与$\beta$，取值范围为0到正无穷
$\lambda \geq 0$
```python
model.lambdas = Var(K, within=NonNegativeReals)
model.beta = Var(within=NonNegativeReals)
```
3. 创建约束条件  
> DDF模型的约束条件为：
$$
\begin{aligned}
& \sum_{j=1}^{n} \lambda_{j} x_{i j} \leq(1-\beta) x_{i0}\\\\
& \sum_{j=1}^{n} \lambda_{j} y_{r j} \geq(1+\beta) x_{r0}\\\\
& \sum_{j=1}^{n} \lambda_{j} u_{t j} =(1-\beta) u_{t0}\\\\
\end{aligned}
$$

**以下代码与上述约束条件一一对应**：
```python
model.constraints = ConstraintList()
for p in Input:
    model.constraints.add(expr=sum(model.lambdas[j] * data.loc[j,p] for j in K) 
                    <= (1-model.beta) * data.loc[i,p])
for q in Output:
    model.constraints.add(expr=sum(model.lambdas[j] * data.loc[j,q] for j in K) 
                    >= (1+model.beta) * data.loc[i,q] )
for u in Undesirable_Output:
    model.constraints.add(expr=sum(model.lambdas[j] * data.loc[j,u] for j in K) 
            == (1-model.beta) * data.loc[i,u])
```
4. 设置求解目标
> 目标函数为$max\beta$
```python
model.obj = Objective(expr=model.beta, sense=maximize)
```
5. 设置求解参数
> 求解器选取为`cplex`，效率值为`eff`
```python
solver = SolverFactory('cplex') # 设定求解器
opt = solver.solve(model) # 进行求解
eff = value(model.obj) # 效率结果为目标函数值
```
6. 综上所述，建立`DDFmocel()`函数，返回值为`eff`
```python
def DDFmodel(i, K, data,Input, Output, Undesirable_Output):
    model = ConcreteModel()
    model.lambdas = Var(K, within=NonNegativeReals)
    model.beta = Var(within=NonNegativeReals)
    model.constraints = ConstraintList()
    for p in Input:
        model.constraints.add(expr=sum(model.lambdas[j] * data.loc[j,p] for j in K) 
                        <= (1-model.beta) * data.loc[i,p])
    for q in Output:
        model.constraints.add(expr=sum(model.lambdas[j] * data.loc[j,q] for j in K) 
                        >= (1+model.beta) * data.loc[i,q] )
    for u in Undesirable_Output:
        model.constraints.add(expr=sum(model.lambdas[j] * data.loc[j,u] for j in K) 
                == (1-model.beta) * data.loc[i,u])
    model.obj = Objective(expr=model.beta, sense=maximize)
    solver = SolverFactory('cplex')
    opt = solver.solve(model)
    eff = value(model.obj)
    return eff
```

##### 函数的进一步调用
<i class="fa-regular fa-face-smile-wink"></i> 我们已经搭建完成好了函数框架，接下来就是调用并储存结果了。
```python
res = run()
print(res) ## 显示最终结果
res.to_excel('Outputddf.xlsx')
```
我们也可以将数据储存为其他的数据格式，可以根据你的需求来储存在不同格式的文件中。

##### 完整代码
<i class="fa-brands fa-microblog"></i> 是不是非常简单，我们已经完成了一个DDF模型的求解代码，以下为完整代码格式：
```python
from pyomo.environ import *  
import pandas as pd

def run():
    data =pd.read_excel('测试数据.xlsx')
    Input = ['输入1','输入2']
    Output = ['输出1','输出2','输出3']
    Undesirable_Output =['非期望输出1','非期望输出2']
    K = list(range(data.shape[0]))
    TE = []
    for i in K:
        eff = DDFmodel(i, K, data, Input, Output, Undesirable_Output)
        TE.append(eff)
    data['DDF效率'] = TE
    return data

def DDFmodel(i, K, data,Input, Output, Undesirable_Output):
    model = ConcreteModel()
    model.lambdas = Var(K, within=NonNegativeReals)
    model.beta = Var(within=NonNegativeReals)
    model.constraints = ConstraintList()
    for p in Input:
        model.constraints.add(expr=sum(model.lambdas[j] * data.loc[j,p] for j in K) 
                        <= (1-model.beta) * data.loc[i,p])
    for q in Output:
        model.constraints.add(expr=sum(model.lambdas[j] * data.loc[j,q] for j in K) 
                        >= (1+model.beta) * data.loc[i,q] )
    for u in Undesirable_Output:
        model.constraints.add(expr=sum(model.lambdas[j] * data.loc[j,u] for j in K) 
                == (1-model.beta) * data.loc[i,u])
    model.obj = Objective(expr=model.beta, sense=maximize)
    solver = SolverFactory('cplex')
    opt = solver.solve(model)
    eff = value(model.obj)
    return eff

res = run()
print(res)
res.to_excel('Outputddf.xlsx')
```


### 写在最后
<i class="fa-regular fa-pen-to-square"></i> 按照这个顺序，相信你已经可以成功复现简单的DEA模型了，其他DEA模型可以采取相似的搭建方式。

<i class="fa-regular fa-paper-plane"></i> 本文是以函数的形式进行代码编写的，而一般来说，我会采用类与方法的形式来进行编写，这样会更方便。其次，**Pyomo+CPLEX**也并不是首选之举，我们也可以调用其他求解器或者调用其他包来书写代码，之后也会出相关进阶教程。

<i class="fa-brands fa-pagelines"></i> 看完本文，有什么问题，或者代码出现了什么BUG，都欢迎及时来找我探讨。 <i class="fa-solid fa-people-group"></i>
