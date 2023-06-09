# Excel
Excel Files for game datas. Only for self use, datas are mostly gathered by others, only using data for analysing.

## 缺氧（生存、基地建设、资源管理）

**介绍**：对游戏<缺氧>中的机制进行数值分析，主要制定游戏的前中后期侧重点与目标，进行数据的区分。对缺氧中的食物来源（动植物）、制氧、发电等机制进行分析，在多种方式中选择最优解。

**技术总结**：对表格确定重点列，确定一些重要的属性，比如对于食物来源，前期注重获取所需时间、制作食物相比直接吃原材料的精制收益，中期注重食物保鲜问题，后期注重食物的品质，从而在正确的游戏阶段建立对应设施。用深浅颜色使数据属性更加明显。使用了简单的加减乘除运算，数据更多修改为重复多项而非合并项以方便运算、排序。

**感悟**：在这款游戏的食物来源中，动物的“帕库鱼”设计得较为特殊，它具有非常短的从捕捉、到产出第一份食物的时间和很高的食物获取额，在植物只能产出400kcal/周期的时候，它能够产出1866.6kcal/周期。我认为该游戏的动物相关功能比植物相关功能晚出，是在一次更新中加入，这使得策划可能为了减少玩家对于动物的不理睬而加强了其属性，但使得帕库鱼碾压了其他食物获取机制，玩家除了建造帕库鱼养殖模块外几乎不再建造其他种植模块了，而其核心就是多种食物来源没有区分的功能性，比如第一次产出短的动物获取食物量少，适合前期，第一次产出长而获取食物多、或者食物品质高，适合后期，又或者食物有特殊功能，比如无限保鲜、吃了加移速、和其他游戏机制捆绑等，就可能是一种改进的方式。
但在该公司另一款游戏<饥荒>中，也有类似的困境，而策划设计了一些新人物，只能吃素食或者特定的食物，或者对于一种不受重视的食物设计一种全新并且非常强大的获取手段。

## 饥荒联机版（开放世界生存制作）

**介绍**：对<饥荒>中的食谱进行分析，选择其中饱食度、回血、回sanity、以及性价比最高的食物。

**技术总结**：使用多次Excel分列选项来修改游戏源代码，后来转用游戏本体日志输出的形式写Lua脚本（AllMods/Mods_DST/food_helper和../utils）输出数据为Excel格式。

通过选择食物饱食度最高的食物，作为一个基准，计算其减去原材料饱食度的净收益。如果一些食物自身的饱食度已经低于此净收益，则从候选中排除这些食物，最后从六十七种食物中筛选出了十多种食物进行手动计算，得出了性价比最高的食物，却发现前三中两个和不分析时的选择没有区别，而唯一第一名Bonestew由于保质期过短之前被忽略，在具体分析后发现可以通过鱼肉进行制作，而鱼肉通过新出的鱼人屋机制可以大量快速获得。但进一步分析发现鱼人在单级游戏中掉落大鱼肉，在联机版中修改，掉落小鱼肉，从而不能制作，可以通过制作mod修改此机制，但这似乎是官方刻意制作的限制。

**感悟**：在过程中，没有事先对目的进行冷静的规划，导致初期尝试用C++代码自动生成的方式（Cpp_Snow_And_DontStarve/include/Foods.h/funBest()）为各个食物选出一个最优食谱，但忽略了数据量本身不大，用代码的方式如果数据非常多，则更加合适，但在这里用耗费了多天的时间。

## 牧场甜心（角色扮演，模拟经营）

**介绍**：对<牧场甜心>中动物、地图、产品（性价比）等进行数值分析，选取性价比最高的实体。

**技术总结**：对一个表生成多种Excel视图，比如动物表按种类下星级排列，开图鉴表按照动物的星级排列，产物表按动物可得产品排列，其中显示产量最多的动物、每个产物最低星级动物、每级动物能给什么产物等。使用HYPERLINK和VLOOKUP函数建立多个表之间的超链接，从而快速查阅。

**感悟**：Excel非常方便快速修改和查看，但其数据冗余问题难以解决，使用时感觉许多不便，或许需要使用sql数据库进行更加复杂的运算。在该游戏中有三百多种产品，对于策划给每种产品设计区分与功能性有更多的要求，同时玩家在没有深入研究时，对于多种产品如何选择也产生困难，通常需要Excel等工具辅助才能有目的性进行选择。

## 信长之野望·创造（策略、历史）

**介绍**：对信长之野望·创造的修改版游戏<如萌似幻·映雪>进行数值分析，给游戏势力、武将进行加权评分，从而找出一些以前没有被使用、或者有很大成长潜力的实体。

**技术总结**：给实体制定多个属性和各个属性的权值，比如在“势力”表中通过COUNTIF武将表来统计出各个势力的武将数，统计每个武将的基本属性，比如设置“统率”属性若超过89则+10，超过79则+2.5进行分析，将每个武将的各个属性评分再通过SUMPRODUCT加权评分，得到武将的最终评分，将一个势力的所有武将评分相加、以及计算特殊项目得到势力的评分，得出哪些势力被策划设计为必然强大者，哪些势力如果被玩家游玩会发挥出大的潜力等。

**感悟**：使用Excel出现了很多数据冗余问题，而目的的更加复杂也使得需要数据库和代码进行实现。数据的获取产生了困难，有一部分数据是通过查看游戏内容手动输入的，并且游戏没有模组功能，玩家不能修改游戏和查看源代码，数据难以获取使得受到了很多阻力，需要重视。

该游戏中有上千个武将，而游戏的可玩性因为设计了阶段性引导所以很高，在前几次游玩让玩家重视武将的基础属性值，在中度游玩时让玩家重视武将的战法、多进行手动操作，引入特色的PK系统，在玩家游玩多次后让其重视武将的成长类型，也就是哪些武将如果被玩家识别出并且着重培养，就能发挥出潜力，而在AI的情况下不能，也过渡了玩家手动操作的疲劳。在这样数据很多的游戏中，策划对武将多种属性的设计和数值的侧重使得游戏的可玩性非常强。

但游戏初始的面板数据最高为100，在游戏中后期最高为140，使得很多武将在都为110、120时差别感知不明显，有些武将因为获得更多经验属性高，另一些武将基础高但是未获得很多经验就很容易被玩家所忽略了，或者说这一辨别过程因为数据普遍集中在110、120以上而不明显，若能够修改为基础70，上限110，或基础80，上限120可能能更加让玩家感知到，但游戏无法简单地进行修改以进行实验。

希望通过势力评分的机制能够由计算机随机生成出一个新势力，或者以此为参考制定出更智能化的势力AI逻辑，全自动完成游戏的培养。
