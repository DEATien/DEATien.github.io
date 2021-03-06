# Dea模型规模报酬的分析


:(fas fa-bolt): 本文将带您了解生产中的规模问题

:(far fa-bell): DEA模型中的**规模报酬**是老生常谈的话题了，那么什么是规模收益呢？读完以下文章，相信你一定会有一个清楚的认识。

### 生产函数中的规模报酬
#### 什么是规模收益
> 规模收益要探讨的问题是：当所有投入要素的使用量都按同样的比例增加时，这种增加会对总产量有什么影响。假定 L单位的劳力和 K单位的资本结合可以生产 Q单位产品，即 L+K→Q。规模收益问题要探讨的是：如果 L和 K都增加 a倍，产量 Q将发生什么变化，即 aL+aK→？。
#### 规模收益的三种类型
假定 aL+aK→bQ，那么，根据 b的值的大小，我们可以把规模收益分为三种类型。
1. 第一种类型：b>a，即产量增加的倍数，大于投入要素增加的倍数。譬如，人工和资本增加 1倍，能使产量增加 2倍。这种类型叫做规模收益递增（Increasing Return to Scale）。
2. 第二种类型：b=a，即产量增加的倍数，等于投入要素增加的倍数。譬如，人工和资本增加1倍，产量也增加1倍。这种类型叫规模收益不变（Constant Return to Scale）。
3. 第三种类型：b<a，即产量增加的倍数，小于投入要素增加的倍数。譬如，人工和资本增加 2倍，却只能使产量增加 1倍。这种类型叫规模收益递减（Decreasing Return to Scale）。

当改变生产规模时，随着生产规模从小变大，一般会先后经历规模收益递增、不变和递减三个阶段。之所以会出现这样三个阶段，是因为在不同的阶段，有不同的因素在起作用。

#### 规模收益变化在实际中的例子
- 促使规模收益递增的因素

> 如果原来生产规模较小，现在增加生产规模，这时会使规模收益递增。这是因为有以下因素在起作用。（1）工人可以专业化。在小企业中，一个工人可能要做好几种作业；在大企业中工人多，就可以分工分得更细，实行专业化。这样就有利于工人提高技术熟练程度，有利于提高劳动生产率。（2）可以使用专门化的设备和较先进的技术。小企业因为产量少，只能采用通用设备。大企业实行大量生产，有利于采用专用设备和较先进的技术。（3）大设备单位能力的制造和运转费用通常比小设备要低。例如，大高炉比小高炉、大型电机比小型电机单位能力的制造成本和运转成本要低。（4）生产要素具有不可分割性。例如，一座 1000吨的高炉，由于不可分割，除非产量达到1000吨，否则就不能充分利用。（5）其他因素。如大规模生产便于实行联合化和多种经营；便于实行大量销售和大量采购（可以节省购、销费用）；等等。

- 促使规模收益不变的因素

> 规模收益递增的趋势不可能是无限的，当生产达到一定规模之后，上述促使规模收益递增的因素会逐渐不再起作用。例如，工人分工如果过窄，就会导致工人工作单调，影响工人的积极性。设备生产率的提高，最终也要受当前技术水平的限制。所以，通常工厂总会有一个最优规模。对公司来说，当工厂达到最优规模时，再扩大生产，它就采用建若干个规模基本相同的工厂的办法。这时，规模收益基本处于不变阶段。这个阶段往往可以经历相当长一个时期，但最终它要进入规模收益递减阶段。

- 促使规模收益递减的因素

> 导致规模收益递减的因素主要是管理问题。企业规模越大，对企业各方面业务进行协调的难度也会越大。许多专家认为，由于高级经理人员很少接触基层，中间环节太多，就必然会造成文牍主义和官僚主义，使管理效率大大降低，这就促使规模收益递减。

以上内容选自[智库](https://wiki.mbalib.com/wiki/%E8%A7%84%E6%A8%A1%E6%94%B6%E7%9B%8A)，
相信大家已经了解了什么是规模报酬了。那么在DEA理论中，规模报酬应该如何判断呢，接下来让我们走进下一节。

### DEA中规模报酬的判断方法
:(far fa-gem): 一般来说，在不同的生产规模下，规模报酬将会随之改变。我们是可以通过CRS模型的计算结果来判断所有决策单元所处的规模报酬情况的，具体而言：
- 生产规模小时，投入产出比会随着规模增加而迅速提升，称为规模报酬递增（lncreasing Returns to Scale, IRS）
  > $\sum_{j=1}^{n} \lambda_{j} \leq 1$，则该决策单元为"规模报酬递增"
- 当生产达到高峰期时，产出与规模成正比而达到最适生产规模，称为规模报酬固定（Constant Returns to Scale, CRS）；
  > $\sum_{j=1}^{n} \lambda_{j} = 1$，则该决策单元为"规模报酬不变"
- 当生产规模过于庞大时，产出减缓，则称为规模报酬递减（Decreasing Returns to Scale, DRS），也就是投入增加时，产出增加的比例会少于投入增加的比例。
  > $\sum_{j=1}^{n} \lambda_{j} \geq 1$，则该决策单元为"规模报酬递减"

:(far fa-lightbulb): 由上可知，我们可以通过CRS模型来判断VRS模型中各个DMU所处的规模收益状态，但是需要注意的是，**线性规划往往有多个最优解**，所以对于某个DMU，$\sum_{j=1}^{n} \lambda_{j}$的值可能并不唯一。如果这样的话，按照上述方法就可能造成错误的判断。那么接下来引入一个新的判断方法：
- 如果规模效率<1，并且在任一最优解中，$\sum_{j=1}^{n} \lambda_{j} \leq 1$，则该决策单元为"规模报酬递增"
- 如果规模效率=1，则说明该决策单元为"规模报酬不变"
- 如果规模效率<1，并且在任一最优解中，$\sum_{j=1}^{n} \lambda_{j} \geq 1$，则该决策单元为"规模报酬递减"

### DEA中规模报酬的选择
:(fas fa-bolt): 如果在研究中，我们已经知道了哪些DMU处于什么阶段（IRS,CRS,DRS），那么我们就可以分别建立不同的模型（NDRS模型,CRS模型,NIRS模型）。但是在实际中，我们往往并不清楚DMU当前所处的规模报酬情况，所以一般选择VRS模型来计算效率值。
