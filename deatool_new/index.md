# Deatool新版使用指南


<script src="https://kit.fontawesome.com/5519c56e9e.js" crossorigin="anonymous"></script>
### 版本更新信息


#### 相关信息介绍

- <i class="fa-regular fa-bell"></i> 请点击此链接进入Pypi官网的deatool主页面：[deatool主页](https://pypi.org/project/deatool/) 
- <i class="fa-regular fa-bell"></i> 请点击此链接进入deatool的下载量统计页面：[deatool下载量统计页面](https://pypistats.org/packages/deatool) 
#### 最新版本更新内容

<i class="fa-solid fa-champagne-glasses"></i> **版本更新时间：2022年4月30日**  
<i class="fa-solid fa-check"></i> 重新复写了全部模型代码，**更快更高更强**  
<i class="fa-solid fa-check"></i> 无需安装额外求解器，**一键式搞定**  
<i class="fa-solid fa-check"></i> 引出了超多全新功能，包括求解超效率模型、动态Malmquist指数  
<i class="fa-solid fa-check"></i> 优化了软件显示界面，全面优化提示信息，便于您更好找到使用过程中的错误  
<i class="fa-solid fa-check"></i> 优化了deatool软件说明书，便于您更快上手版本软件  
<i class="fa-solid fa-check"></i> 软件的使用功能设定了不同权限，请通过输入`key`进行激活  
<i class="fa-solid fa-check"></i> 为网站引入了新logo <i class="fa-regular fa-face-grin-squint"></i>

----
<i class="fa-solid fa-champagne-glasses"></i> **版本更新时间：2022年4月26日**  
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
- 如果您曾经安装过deatool，那么请参照如下命令获取最新版本：

    ```cmd
    pip install --upgrade deatool
    ```
    **Note：由于需要安装相关依赖库，可能需要一段时间，请您耐心等待安装完成**

### 运行Deatool
- <i class="fa-brands fa-envira"></i> 可以选用以下两种方式打开Deatool
1. [**推荐**]直接在CMD命令行输入：
    ```cmd
    deatool
    ```
2. 在CMD命令行输入：

    ```cmd
    python -m deatool
    ```
- 顺利的话将会出现如下Deatool图形交互界面：
<img src="\images\display_new.png" width = "500" height = "300" alt="图片无法加载" align=center /></img>

### Deatool功能介绍
<i class="fa-solid fa-compass"></i> 恭喜您已经成功打开了Deatool，接下来将向您介绍这个Python库的功能：
- 计算CCR模型、BCC模型、SBM模型、DDF模型的效率值
- 针对以上模型可以选取不同的规模报酬性，分别是：CRS（constant returns to scale），VRS（variable returns to scale）
- 选择CCR模型，会自动输出CCR、BCC模型下的效率值，并判断规模报酬情况（无需额外选择VRS假设）
- 选择CCR-Mlamquist模型，会自动输出TFP变化率、效率变化、纯技术效率变动、规模效率变动、技术变化指标（无需额外选择VRS假设）
- 针对DDF模型可以选取不同的方向并设置对非期望产出的处置性
- 针对SBM模型/SBM超效率模型可以输出相应指标的改进量（投入冗余与产出不足）
- 可以处理包含非期望产出的模型

### Deatool使用流程
#### 基础效率模型与超效率模型
1. 点击“导入表格”([参考实例数据](/测试数据.xlsx))，请注意表格的导入形式为：

    | DMU名称 | 投入 | 产出 |非期望产出|
    | :------: | :------: | :------: | :------: |
     DMU1 | xxx | xxx | xxx |
     ... | ... | ... |... |
     DMUn | xxx | xxx | xxx| 

> **请严格按照投入、产出、非期望产出的顺序进行存放数据**  
1. 正确导入表格后，会在右边栏出现表格内容
2. 选择需要测算模型，默认**CCR模型**
3. 选择规模报酬性，默认**CRS**
4. 如果选择是DDF模型，请选择合适的方向；若选择的是CCR或SBM模型，“请选择方向”一栏**默认**即可
5. 填写投入变量的个数，如果有2个投入，请填写阿拉伯数字“**2**”，**不要写多余的字**
6. 填写产出变量的个数，同上
7. 填写非期望产出变量的个数，同上，需注意无非期望产出的话，默认即可
8. 点击“开始计算”，右边栏出现计算过程信息
9. 最下面出现计算结果的表格，点击“**结果保存**”，结果将会储存在与你导入数据的**同一个文件夹**内
10. 若测算超效率模型，步骤同上，需注意需要将选项卡切换到`超效率模型`

#### 动态效率模型（Malmquist指数）
1. 切换选项卡为`Malmquist指数`
1. 点击“导入表格”([参考实例数据](/测试数据.xlsx))，请注意表格的导入形式为：

    | DMU名称 | 投入 | 产出 |
    | :------: | :------: | :------: |
     DMU1_period1 | xxx | xxx |
     ... | ... | ... |
     DMUn_period1 | xxx | xxx |dea
     ... | ... | ... |
     DMU1_periodk | xxx | xxx |
     ... | ... | ... |
     DMUn_periodk | xxx | xxx |

> **目前动态效率模型暂不支持包含非期望产，请严格按照投入、产出的顺序进行存放数据**  
1. 正确导入表格后，会在右边栏出现表格内容
2. 选择需要测算模型，默认**CCR Malmquist 指数模型**
3. 选择规模报酬性，默认**CRS**
4. 如果选择是DDF模型，请选择合适的方向；若选择的是CCR或SBM模型，“请选择方向”一栏**默认**即可
5. 填写投入变量的个数，如果有2个投入，请填写阿拉伯数字“**2**”，**不要写多余的字**
6. 填写产出变量的个数，同上
7. 填写测算期数，同上
8. 点击“开始计算”，右边栏出现计算过程信息
9. 最下面出现计算结果的表格，点击“**结果保存**”，结果将会储存在与你导入数据的**同一个文件夹**内

#### 简单操作演示
:(fas fa-desktop): 以SBM模型为例，数据[同上](/测试数据动态.xlsx)，包含2个投入，3个期望产出，2个非期望产出：
<iframe src="\演示_new.gif"  height="330" width="480" alt="图片无法加载" align=center /></iframe>
  
### Deatool注意事项

- 如果数据表格导入有误，将会出现`Error:数据读取有误，请检查数据`的字样，那么请您重新检查数据格式
- 一定要注意数据 <i class="fa-solid fa-file-circle-check"></i> 的正确格式，确保数据准确无误，否则计算结果将出错
- 数据正常导入后，点击`开始计算`后若出现`出错，请检查步骤是否正确`，那么请您检查是否按照上述步骤进行操作
- 在导入数据后，您可以多次测算模型，并通过最下方查看计算的结果
- 请注意使用DDF模型时必须选取方向，如果不选取方向将无法进行求解 <i class="fa-regular fa-face-sad-tear"></i> 
- 如在使用除DDF外的模型时选取了方向,会给出`warning`信息，不影响求解，会默认更改为`无方向`
- 在使用`Malmquist模型`时务必正确填写`期数`，如果不填写期数将无法进行求解 <i class="fa-regular fa-face-sad-tear"></i> 
- 使用超效率模型时，会由于模型不可行的问题导致无法产生最优解，会在表格里进行标注`infeasible`
- 如果您需要保存数据，请务必按下“**结果保存**”键，否则不会对结果进行保存
- 如果您在使用中出现了什么问题，请及时联系我的微信，也欢迎您对后续的功能进行建议 <i class="fa-regular fa-envelope"></i>
- 解释权归作者所有，本软件禁止任何读者擅自修改后进行重新发布 <i class="fa-regular fa-face-smile-wink"></i>  

### 软件激活
<i class="fa-solid fa-battery-empty"></i>  目前试用版本提供了普通效率模型的测算，已经可以满足很多同学的日常科研需求  
<i class="fa-solid fa-battery-full"></i>  如果您需要使用超效率模型与Malmquist模型，请及时联系我，我将为您提供`License`

### Support or Contact
:(fas fa-comments): Wechat：:(fas fa-address-card): yomamalielie
