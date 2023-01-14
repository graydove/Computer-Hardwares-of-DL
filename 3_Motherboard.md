# 主板

*仅介绍少数用于深度学习的主板，其他关于主板的知识暂不介绍*

深度学习所用的主板关键在于供电和稳定性，今后遇到新主板，也是优先考察供电规模和电气元件的稳定性

不要买特别便宜的主板（日常低于2100元，618低于1900元的），长时间工作容易烧电容

Z890和X770主板需要重新检查主板的用户手册，与本说明不兼容，旧主板参考另一个文档

主板供电天梯可以百度或者关注陈chen辉hui@哔哩哔哩

**附件中的主板供电天梯图均转自陈chen辉hui@哔哩哔哩**

&nbsp;

## 主板的挑选1

主板根据CPU也分为桌面级的芯片组主板、HEDT的芯片组主板、服务器的芯片组主板、工作站的芯片组主板

根据大小，可以分为ITX，M-ATX，ATX，E-ATX大致四种（DTX归类到ITX，其他比E-ATX更大的主板需要特制的机箱，一般需要定制化购买）

**不推荐ITX和M-ATX主板，不推荐DTX主板**

桌面级和HEDT级别的主板建议只在华硕，微星，华擎三家中挑选

&nbsp;

### 桌面级

**Intel**：

Z690（对应12代酷睿）

Z790（对应13代酷睿）

C246（对应Xeon-E2000系列，基本上是9代酷睿的换皮货）

**AMD**：

X570(S)，B550（对应3000系锐龙和5000系锐龙）

X670E，X670（对应7000系锐龙）

&nbsp;

### 桌面级主板最低要求

（双显卡，不推荐单显卡的主板，绝大部分只能提供单显卡的主板，供电都很拉跨，水冷主板不推荐，除了  PRO WS X570-ACE也不推荐三显卡）：

**Intel**：

Core i9-12900K最多提供20条PCIE，其他的是南桥提供的。

Core i9-13900K最多提供20条PCIE，其他的是南桥提供的。

&nbsp;

#### Z690芯片组

（支持12代，13代酷睿，以下推荐主板的内存均为DDR5）

| 品牌 | 型号                               | 供电    | PCIE*（多卡模式）    |
| ---- | ---------------------------------- | ------- | -------------------- |
| 华硕 | ROG MAXIMUS Z690 HERO              | 20 90A  | x8(G5),x8(G5),x4(G3) |
| 华硕 | ROG MAXIMUS Z690 EXTREME GLACIAL** | 24 105A | x8(G5),x8(G5)        |
| 华硕 | ROG MAXIMUS Z690 EXTREME**         | 24 105A | x8(G5),x8(G5)        |
| 华硕 | ROG MAXIMUS Z690 FORMULA           | 20 105A | x8(G5),x8(G5),x4(G3) |
| 微星 | MEG Z690 ACE                       | 19 105A | x8(G5),x8(G5),x4(G4) |
| 微星 | MEG Z690 UNIFY(X)                  | 19 105A | x8(G5),x8(G5),x4(G4) |
| 微星 | MPG Z690 CARBON WIFI               | 18 75A  | x8(G5),x8(G5),x4(G3) |
| 微星 | MPG Z690 FORCE WIFI                | 18 75A  | x8(G5),x8(G5),x4(G3) |
| 华擎 | Z690 Taichi                        | 20 105A | x8(G5),x8(G5),x4(G4) |

&nbsp;

#### Z790芯片组

（支持12代，13代酷睿，以下推荐主板的内存均为DDR5）

| 品牌 | 型号                       | 供电    | PCIE*（多卡模式）     |
| ---- | -------------------------- | ------- | --------------------- |
| 华硕 | ROG MAXIMUS Z790 EXTREME** | 24 105A | x8(G5),x8(G5)         |
| 华硕 | ROG MAXIMUS Z790 HERO      | 20 90A  | x8(G5),x8(G5)         |
| 华硕 | PROART Z790-CREATOR WIFI   | 16 70A  | x8(G5),x8(G5)         |
| 微星 | MEG Z790 GODLIKE**         | 26 105A | x16(G5),x8(G5)        |
| 微星 | MEG Z790 ACE**             | 24 105A | x16(G5),x8(G5),x4(G4) |
| 华擎 | Z790 Taichi Carrara**      | 24 105A | x8(G5),x8(G5)         |
| 华擎 | Z790 Taichi                | 24 105A | x8(G5),x8(G5)         |

*G3代表PCIe 3.0, G4和G5类推

**E-ATX主板

&nbsp;

**AMD**：

**Ryzen 9 5950X最多提供24条PCIE，其中有4条固定给M.2固态硬盘。**

#### X570芯片组和B550芯片组

（支持Ryzen 3000系列和Ryzen 5000系列，内存均为D4）

| 品牌 | 型号                            | 供电    | PCIE**（多卡模式） |
| ---- | ------------------------------- | ------- | ------------------ |
| 华硕 | ROG Crosshair VIII Extreme***   | 18 90A  | x8,x8              |
| 华硕 | ROG Crosshair VIII Dark Hero    | 7x2 90A | x8,x8,x4           |
| 华硕 | ROG Crosshair VIII Hero（WiFi） | 7x2 60A | 7x2 60A            |
| 华硕 | ROG Crosshair VIII Formula      | 7x2 60A | 7x2 60A            |
| 华硕 | ROG Strix B550-XE Gaming        | 7x2 90A | x8,x8,x4           |
| 华硕 | ROG Strix B550-E                | 7x2 60A | x8,x8,x4           |
| 华硕 | ROG Strix X570-E Gaming WiFi II | 6x2 60A | x8,x8,x4           |
| 华硕 | ROG Strix X570-F Gaming         | 4x3 50A | x8,x8,x4           |
| 华硕 | Pro WS X570-Ace*                | 6x2 60A | x8,x8,x8           |
| 微星 | MEG X570 Godlike***             | 7x2 70A | x8,x4,x4,x4        |
| 微星 | MEG B550 Unify                  | 14 90A  | x16                |
| 微星 | MEG B550 Unify-X                | 14 90A  | x16                |
| 微星 | MEG X570S Ace Max               | 16 90A  | x8,x8,x4           |
| 微星 | MEG X570 Ace                    | 6x2 60A | x8,x8,x4           |
| 微星 | MEG X570S Unify-X Max           | 16 90A  | x8,x8,x4           |
| 微星 | MEG X570 Unify                  | 6x2 60A | x8,x8,x4           |
| 微星 | MEG X570S Carbon Max Wifi       | 14 75A  | x16,x4             |
| 微星 | MPG X570S Edge Max Wifi         | 12 75A  | x16,x4             |
| 微星 | Prestige X570 Creation          | 7x2 60A | x8,x8,x4           |
| 微星 | MAG X570S Tomahawk Max Wifi     | 6x2 60A | x16,x4             |
| 华擎 | B550 Taichi                     | 7x2 50A | x8,x8,x4           |
| 华擎 | X570 Taichi                     | 6x2 50A | x8,x8,x4           |

*第二根槽只能放单槽卡或者是双槽卡

**均为PCIe 4.0

***E-ATX主板

其他的主板可以查看附件中的主板供电天梯来查看

&nbsp;

#### X670(E)芯片组和B650芯片组

（支持Ryzen 7000系列）

| 品牌 | 型号                          | 供电    | PCIE（多卡模式）     |
| ---- | ----------------------------- | ------- | -------------------- |
| 华硕 | ROG CROSSHAIR X670E EXTREME*  | 20 110A | x8(G5),x8(G5),x4(G4) |
| 华硕 | ROG CROSSHAIR X670E HERO      | 18 110A | x8(G5),x8(G5)        |
| 华硕 | ROG STRIX X670E-E GAMING WIFI | 18 110A | x8(G5),x8(G5)        |
| 华硕 | ProArt X670E-CREATOR WIFI     | 16 70A  | x8(G5),x8(G5)        |
| 微星 | MEG X670E GODLIKE*            | 24 105A | x8(G5),x8(G5),x4(G5) |
| 微星 | MEG X670E ACE*                | 22 90A  | x8(G5),x8(G5),x4(G5) |
| 微星 | MPG X670E CARBON WIFI         | 18      | x8(G5),x8(G5),x4(G5) |
| 华擎 | X670E Taichi Carrara*         | 24 105A | x8(G5),x8(G5)        |
| 华擎 | X670E Taichi*                 | 24 105A | x8(G5),x8(G5)        |





### HEDT

**Intel**：

X299（对应7，9，10代酷睿X系列），包括X299X

该主板按CPU的PCIe数量进行分类，其中lane是PCIe通道的总数：

**7代Core-X处理器：**

i5-7640X（4c8t，16lane），i7-7740X（4c8t，16lane），i7-7800X（6c12t，28lane）

i7-7820X（8c16t，28lane），i9-7900X（10c20t，44lane），i9-7920X（12c24t，44lane）

i9-7940X（14c28t，44lane），i9-7960X（16c32t，44lane），i9-7980XE（18c36t，44lane）

**9代Core-X处理器：**

i7-9800X（8c16t，44lane，参考价格2599元），i9-9820X（10c20t，44lane），i9-9900X（10c20t，44lane）

i9-9920X（12c24t，44lane），i9-9940X（14c28t，44lane），i9-9960X（16c32t，44lane）

i9-9980XE（18c36t，44lane，参考价格9999元）

**10代Core-X处理器：**

i9-10900X（10c20t，48lane，参考价格4399元），i9-10920X（12c24t，48lane，参考价格5799元），i9-10940X（14c28t，48lane，参考价格6599元），i9-10980XE（18c36t，48lane，参考价格12999元）

&nbsp;

**AMD**：

X399（对应1-2代线程撕裂者），X399逐渐退市，供电比较合适的是X399 Taichi和X399 Creation

TRX40（对应3代线程撕裂者）

Threadripper全系都提供64lane

**1代Threadripper：**

TR 1900X（8c16t），TR 1920X（12c24t），TR 1950X（16c32t）

**2代Threadripper（带W的不推荐）：**

TR 2920X（12c24t），TR 2950X（16c32t）

**3代Threadripper（带W的不推荐）：**

TR 3960X（24c48t，参考价格10699元），TR 3970X（32c64t，参考价格15299元），TR 3990X（64c128t，参考价格29999元）

&nbsp;

### HEDT主板最低要求

（双显卡，3-4张显卡需要显卡的槽位支持）：

**Intel**：

| 品牌 | 型号                  | 供电    | 28lane*   | 44lane        | 48lane        | 价格 |
| :--- | :-------------------- | :------ | --------- | ------------- | ------------- | ---- |
| 华硕 | Prime X299-A II       | 8x2 60A | x16,x8    | x16,x16,x8    | x16,x16,x8    | 3299 |
| 华硕 | ROG Strix X299-E      | 7 60A   | x16,x8    | x16,x16,x8    | x16,x16,x8    | 3999 |
| 华硕 | ROG R6E               | 8x2 70A | x16,x8,x4 | x16,x16,x4    | x16,x16,x8    | 7999 |
| 华硕 | WS X299 SAGE          | ？8 70A |           |               |               | 4999 |
| 技嘉 | X299X Designare 10G** | 6x2 70A | x16,x8,x4 | x16,x8,x16,x4 | x16,x8,x16,x8 | 7698 |
| 技嘉 | X299X Aorus Master    | 6x2 60A | x16,x8,x4 | x16,x8,x16,x8 | x16,x8,x16,x8 | 4998 |
| 微星 | X299 PRO**            | 8 50A   | x16,x4,x8 | x16,x4,x16,x8 | x16,x8,x16,x8 | 2599 |
| 微星 | Creator X299          | 12 90A  | x8,x8,x8  | x8,x8,x16,x8  | x8,x8,x16,x8  | 6999 |
| 华擎 | X299 Taichi CLX       | 6x2 60A | x16,x8    | x16,x16,x8    | x16,x16,x8    | 3699 |

*16lane的i7-7740X等CPU在任意X299上都能且仅能提供x8,x8的通道

**第二根PCIE槽只能插入单槽卡，如RTX4000 8G，Tesla T4 16G

**AMD**：

| 品牌 | 型号                         | 供电    | PCIE          | 价格 |
| ---- | ---------------------------- | ------- | ------------- | ---- |
| 华硕 | ROG Zenith II Extreme Alpha* | 8x2 90A | x16,x8,x16,x8 | 9999 |
| 华硕 | ROG Zenith II Extreme*       | 8x2 70A | x16,x8,x16,x8 | 9999 |
| 华硕 | ROG Strix TRX40-XE           | 8x2 90A | x16,x16       | 4799 |
| 华硕 | ROG Strix TRX40-E Gaming     | 8x2 60A | x16,x16       |      |
| 技嘉 | TRX40 Aorus Xtreme           | 16 70A  | x16,x8,x16,x8 | 8898 |
| 技嘉 | TRX40 Designare              | 16 70A  | x16,x8,x16,x8 | 6888 |
| 技嘉 | TRX40 Aorus Master*          | 16 70A  | x16,x8,x16,x8 | 5999 |
| 技嘉 | TRX40 Aorus Pro WiFi*        | 12 70A  | x16,x8,x16,x8 | 4998 |
| 微星 | Creator TRX40*               | 16 70A  | x16,x8,x16,x8 | 7777 |
| 微星 | TRX40 Pro 10G*               | 6x2 90A | x16,x8,x16,x8 | 4999 |
| 华擎 | TRX40 Taichi                 | 6x2 90A | x16,x16,x16   | 3899 |

*第二根PCIE槽只能插入单槽卡，如RTX4000 8G，Tesla T4 16G

&nbsp;

## 主板的搭配

### 1 显卡

对于常见的2.5槽显卡和3槽显卡，普通的ATX和EATX主板只能安装2-3张显卡

当显卡位2槽卡时，可以安装3-4张显卡，更多的显卡需要4U机箱和专门的服务器，最多可以安装10张显卡

&nbsp;

几乎全部的X570和Z690主板不管有几个PCIe x16的槽，都只能最多提供2个PCIe x8的槽

极少数的X570，比如华硕(ASUS) PRO WS X570-ACE，可以在不插M.2固态的前提下，提供3个PCIe x8的槽

&nbsp;

**主板必须给每张显卡提供至少PCIE x8的通道，无论是PCIE 4.0还是PCIE 3.0**

&nbsp;

### 2 CPU

**双路GPU对应的CPU，核心不能少于6个，线程不能少于12个**

**三路GPU对应的CPU，核心不能少于8个，线程不能少于16个**

&nbsp;

### 3 内存

对于部分服务器主板，需要购买ECC REG内存，不推荐在X570和TRX40上用ECC内存，可能有兼容性的问题

&nbsp;

### 4 硬盘

部分M.2会占用SATA，而更多的时候会占用PCIE。不要在一张Z490或X570主板上安装2块或更多的M.2固态硬盘

&nbsp;

### 5 机箱

不要买不能安装ATX主板的机箱

&nbsp;

### 6 关于PCIE 4.0

TITAN RTX，RTX2080Ti，Tesla T4，Tesla V100都是PCIE 3.0的显卡，因此无论主板给它们PCIE 4.0 x4还是PCIE 4.0 x8，它们表现出来的速度都是PCIE 3.0 x4和PCIE 3.0 x8

已知的支持PCIE 4.0的显卡有：

AMD显卡：RX5000系列、Radeon VII、Radeon Instinct MI50、MI60、MI100或更新的显卡

Nvidia显卡：RTX30系列、NVIDIA A100 40/80GB、RTX A6000 48GB或更新的显卡

Intel的主板需要至少要Z590才会开放PCIE 4.0的支持。

AMD的主板需要至少X570、B550、TRX40、WRX80才支持PCIE 4.0。

&nbsp;

## 主板的挑选2

除了普通的桌面级主板和HEDT主板外，还有工作站主板和服务器主板

Intel这边的主流工作站主板是Xeon W-2100系列和Xeon W-2200系列的C422主板和Xeon W-3100系列和Xeon W-3200系列的C621，C622主板

AMD这边的主流工作站主板是TR 2970WX和TR 2990WX对应的X399主板和TR Pro 3945WX到TR Pro 3995 WX对应的疑似SP3接口的主板

Intel这边的服务器主板包括LGA3647接口和LGA4189接口，前者对应Xeon Scalable第1-2代，后者对应Xeon Scalable第3代（可能也兼容第4代），LGA3647基本上都是C621和C622

AMD这边的服务器主板是SP3接口的主板，零售的很少

&nbsp;

### 工作站级

工作站级基本上可以约等于功耗更高的HEDT级主板，这些主板的供电不一定是最好的，但一定是最稳的。由于工作站级的主板需要和CPU一同考虑并购买，下面介绍几个笔者见过的稳定组合。

&nbsp;

#### ROG Dominus Extreme和Xeon W-3175X

&nbsp;

Xeon W-3175X为28核心，56线程，48条PCIE，TDP是255w

主板最多提供x16,x8,x16,x8的搭配，单显卡需要搭配750w电源，双显卡需要搭配1000w电源，三显卡1200w，四显卡1600w。

&nbsp;

#### Supermicro X11SRA-F和Xeon W-2191B

&nbsp;

2191B是2195的Apple定制版本，18核心，36线程，48条PCIE，TDP是140w

超微是服务器主板的一线品牌，单路主板X11SRA-F可以最多提供x8,x16,x16的搭配，电源参考6139组合

这块主板比较便宜，不到2500元，性价比比较高，芯片组为C422

&nbsp;

#### Gigabyte C246-WU4和Core i9-9900K

&nbsp;

实验室的一台机器

9900K，8核心16线程，16条PCIE，TDP是95w，因此最多接x8,x8

这块主板能提供的最多提供x8,x4,x4，该主板目前所能搭配的最好处理器为Core i9-9900KS和Xeon E-2288G，均为16lanes的处理器

&nbsp;

### 服务器级

&nbsp;

#### ASUS WS C621E SAGE和Dual Xeon Gold 6139

（Dual代表双路）

&nbsp;

6139是6140的QS版本CPU，18核心，36线程，48条PCIE，TDP是140w

双路主板可以最多提供x16,x16,x16,x16的搭配，单显卡需要1000w电源，双显卡需要1600w电源，三显卡2000w，四显卡需要双路1200w

&nbsp;

#### AS Rock EPC621D6I和Xeon Platinum 8175M

&nbsp;

8175M是8168的QS版本CPU，24核心，48线程，48条PCIE，TDP是205w

这是个单路的C621服务器主板，且是ITX主板，仅能安装一张显卡，电源参考3175X组合

&nbsp;

## 思考题

1：通过查找主板的用户手册，补全WS X299 SAGE的28lane的三路显卡信息，44lane和48lane的四路显卡信息

2：如果X299X Aorus Master和i7-7800X搭配3张TITAN RTX显卡进行训练，每张显卡允许最大PCIe通道为PCIe 3.0 x16，请问第三张TITAN RTX显卡的实际使用的PCIe通道是多少？

3：现有三张支持PCIE 3.0的2080Ti，均为2.5槽卡，请给出最便宜的三卡配置单，包括主板、CPU，要求CPU不少于8核心

4：现有四张支持PCIE 4.0的GA100，均为2槽卡，请给出最便宜的四卡配置单，包括主板、CPU，要求CPU不少于10核心
