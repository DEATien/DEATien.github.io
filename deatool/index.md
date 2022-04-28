# Deatool使用指南


<script src="https://kit.fontawesome.com/5519c56e9e.js" crossorigin="anonymous"></script>
### 版本更新信息


#### 相关信息介绍

- <i class="fa-regular fa-bell"></i> 请点击此链接进入Pypi官网的deatool主页面：[deatool主页](https://pypi.org/project/deatool/) 
- <i class="fa-regular fa-bell"></i> 请点击此链接进入deatool的下载量统计页面：[deatool下载量统计页面](https://pypistats.org/packages/deatool) 
#### 最新版本更新内容
<i class="fa-solid fa-champagne-glasses"></i> 版本更新时间：2022年4月29日  
<i class="fa-solid fa-check"></i> 完善了Pypi官网的deatool包的相关信息，包括且不限于License、操作系统、Python需求版本、官方操作等信息。  
<i class="fa-solid fa-check"></i> 优化了deatool的运行方式，摒弃了传统的通过导入Python包、运行模块才能显示界面的操作，可以直接在`cmd`命令行输入`deatool`来运行本软件，详情请见`运行Deatool`章节。  
<i class="fa-solid fa-check"></i>  优化了相关代码信息。  
<i class="fa-solid fa-check"></i> 更改了DDF在强可处置性假设下的模型错误。  

### 安装Deatool
- 首先需要您电脑内装有Python，且版本号低于3.9
- 在CMD命令行输入：

    ```cmd
    pip install deatool
    ```
    **由于需要安装相关依赖库，可能需要一段时间，请您耐心等待安装完成**

### 运行Deatool
- 可以选用以下两种方式打开Deatool
1. 在CMD命令行输入：

    ```cmd
    python -m deatool
    ```
2. [**推荐**]直接在CMD命令行输入：
    ```cmd
    deatool
    ```


- 顺利的话将会出现如下Deatool图形交互界面：
<img src="\images\desplay.png" width = "500" height = "300" alt="图片无法加载" align=center /></img>

### Deatool功能介绍
恭喜您已经成功打开了Deatool，接下来将向您介绍这个Python库的功能：
- 计算CCR模型、BCC模型、SBM模型、DDF模型的效率值
- 针对以上模型可以选取不同的规模报酬性，分别是：CRS（constant returns to scale），VRS（variable returns to scale）
- 选择CCR模型，会自动输出CCR、BCC模型下的效率值，并判断规模报酬情况
- 针对DDF模型可以选取不同的方向并设置对非期望产出的处置性
- 针对SBM模型可以输出相应指标的改进量（投入冗余与产出不足）
- 可以处理包含非期望产出的模型
- 可以选取不同的主流处理器，目前支持：Gurobi，Cplex，Glpk，请根据您的求解器安装情况来选取求解器

### Deatool使用流程

1. 点击“导入表格”([参考实例数据](/测试数据.xlsx))，请注意表格的导入形式为：

    | DMU名称 | 投入 | 产出 |非期望产出|
    | :------: | :------: | :------: | :------: |
     DMU1 | xxx | xxx | xxx |
     ... | ... | ... |... |
     DMUn | xxx | xxx | xxx|
2. 正确导入表格后，会在右边栏出现表格内容
3. 选择需要测算模型，默认**CCR模型**
4. 选择规模报酬性，默认**CRS**
5. 如果选择是DDF模型，请选择合适的方向；若选择的是CCR或SBM模型，“请选择方向”一栏**默认**即可
6. 填写投入变量的个数，如果有2个投入，请填写阿拉伯数字“**2**”，**不要写多余的字**
7. 填写产出变量的个数，同上
8. 填写非期望产出变量的个数，同上，需注意无非期望产出的话，默认即可
9. 选择合适的求解器，默认为**Gurobi**
10. 点击“开始计算”，右边栏出现计算过程信息
11. 最下面出现计算结果的表格，点击“**结果保存**”，结果将会储存在与你导入数据的**同一个文件夹**内

#### 简单操作演示
:(fas fa-desktop): 以SBM模型为例，数据[同上](/测试数据.xlsx)，包含2个投入，3个期望产出，2个非期望产出：
<iframe height="500" width="700" src="\演示.gif"></iframe>
  
### Deatool注意事项

- 如果数据表格导入有误，将会出现“**Error:数据读取有误，请检查数据**”的字样，那么请您重新检查数据格式
- 数据正常导入后，点击'开始计算'后若出现“**出错，请检查步骤是否正确**”，那么请您检查是否按照上述步骤进行操作，可能的问题为变量个数填写错误或您的电脑内没有装您选取的求解器，请您重新选取求解器
- 建议您使用**Gurobi**求解器，求解速度最快
- 在导入数据后，您可以多次测算模型，并通过最下方查看计算的结果
- 如果您需要保存数据，请务必按下“**结果保存**”键，否则不会对结果进行保存
- 如果您在使用中出现了什么问题，请及时联系我的微信，也欢迎您对后续的功能进行建议

### Support or Contact
:(fas fa-comments): Wechat：:(fas fa-address-card): yomamalielie
