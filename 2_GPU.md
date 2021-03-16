# GPU

*仅介绍少数用于深度学习的GPU，其他关于GPU的知识暂不介绍*


&nbsp;
## GPU的种类（N和A）

显卡无论是Nvidia还是AMD，都有游戏显卡、计算卡和专业图形卡之分，Nvidia还有TITAN系列显卡

由于AMD没有CUDA，只能用OpenCL，且效率很低，因此极不建议用A卡，GCN架构的显卡（比如RX580、Radeon 7、Vega64支持使用ROCm进行部分的深度学习计算，但是RX5700XT和RX6900XT不支持）

&nbsp;

**常见的显卡架构**

|  显卡架构   |    游戏显卡    |               TITAN                |             计算卡             |     专业图形卡      |
| :---------: | :------------: | :--------------------------------: | :----------------------------: | :-----------------: |
| Maxwell架构 |  GTX980Ti 6GB  |            TITAN X 12GB            |         Tesla M40 24GB         |  Quadro M6000 12GB  |
| Pascal架构  | GTX1080Ti 11GB | TITAN X(Pascal) 12GB,TITAN Xp 12GB | Tesla P100 16GB,Tesla P40 24GB |  Quadro P6000 24GB  |
|  Volta架构  |       -        |          TITAN V 12/32GB           |     Tesla V100(S) 16/32GB      |  Quadro GV100 32GB  |
| Turing架构  | RTX2080Ti 11GB |           TITAN RTX 24GB           |         Tesla T4 16GB          | Quadro RTX8000 48GB |
| Ampere架构  |  RTX3090 24GB  |                 -                  | NVIDIA A100 40/80GB,NVIDIA A40 48GB | NVIDIA RTX A6000 48GB |

图形卡和游戏卡、TITAN的规格差不多，如RTX8000基本上就是TITAN RTX的显存增大版，但价格往往贵了很多，因此买2张TITAN RTX比1张RTX 8000更划算

&nbsp;

**游戏显卡部分（推荐）**

对于同系列的显卡，可以通过CUDA核心进行简单的性能比较，比如2张GTX1660Ti约等于1张RTX2080Super

|      NVIDIA       | CUDA核心/Tensor核心及数量 |    价格     |
| :---------------: | :-----------------------: | :---------: |
|     MX250 2GB     |       GP108，384个        |             |
|     MX350 2GB     |    GP107-670-A1，640个    |             |
|   GTX1050Ti 4GB   |       GP107，768个        |   749-949   |
|    GTX1650 4GB    |    TU117-300-A1，896个    |  799-1199   |
|    MX450 2GB    |      TU117，1024个      |             |
| GTX1650 Super 4GB |  TU116-250-KA-A1，1280个  |  1069-1499  |
| GTX1660/Super 6GB |   TU116-300-A1，1408个    |  1299-1999  |
|   GTX1660Ti 6GB   |   TU116-400-A1，1536个    |  1749-2299  |
|    RTX2060 6GB    | TU106-200A-KA-A1，1920个  |  1899-2899  |
| RTX2060 Super 8GB |   TU106-410-A1，2176个    |  2459-3599  |
|    RTX2070 8GB    |   TU106-400A-A1，2304个   |    停产     |
| RTX2070 Super 8GB |   TU104-410-A1，2560个    |  3459-4799  |
|    RTX2080 8GB    |   TU104-400A-A1，2944个   |    停产     |
| RTX2080 Super 8GB |   TU104-450-A1，3072个    |    停产     |
|  RTX2080Ti 11GB   | TU102-300A-K1-A1，4352个  |    停产     |
|  TITAN RTX 24GB   |   TU102-400-A1，4608个    | 19999-22999 |
|   TITAN V 12GB    |   GV100-400-A1，5120个    |             |
| Quadro GV100 32GB |       GV100，5120个       |             |

&nbsp;

注意：30系全部都是向上进风（即显卡的风扇吸风）
|    NVIDIA    | CUDA核心/Tensor核心及数量 | 价格 |
| :----------: | :-----------------------: | :--: |
| RTX 3060 12G  |    GA106-300-A1，3840个** |  2499+    |
| RTX 3060Ti 8G  |         GA104-200-A1，4864个**          |  2999+    |
| RTX 3070 8G  |         GA104-300-A1，5888个**          |  3899+    |
| RTX 3080 10G |         GA102-200-K1-A1，8704个**          |   5499+   |
| RTX 3090 24G |         GA102-300-A1，10496个**         |   11999+   |
| NVIDIA RTX A6000 48G |         GA102，10752个**         | 48800 |

&nbsp;

注意：

**1、对于10系（包括TITAN Xp，TITAN X，GP100，Telsa P40）或更古老的显卡来说，CUDA核心不能简单叠加，需要考虑显存带宽、散热之类的**

**2、对于30系显卡，8704个CUDA实际上是4352个FP32单元和4352个INT32单元，其中INT32单元也可以当FP32单元使用，所以看起来相对于20系，CUDA核心翻倍了。但实际上INT32单元的效率并没有FP32单元效率高。因此CUDA核心并不能简单翻倍计算，其CUDA数量不能和20系进行比较。（3080大概比2080Ti快了40%-60%）**

3、深度学习主要是看显存，其次是看CUDA核心的数量（如GTX1080Ti 11G有3584个CUDA核心，TITAN Xp 12G有3840个CUDA核心，GTX980Ti 6G有2816个CUDA核心），然后是看显卡带宽（如RTX3070比RTX2080Ti多支持一个PCIe4.0）

4、支持PCIe 4.0的显卡有：Ampere架构的全部显卡（RTX3090、A100、A6000），但需要主板和CPU均支持PCIe 4.0，显卡才能运行在PCIe 4.0的设置下。目前已知的只有Z590和X570、B550支持PCIe4.0，部分Z490支持PCIe 4.0但需要刷BIOS，目前已知只有11代酷睿、3000系锐龙、5000系锐龙、3000系的线程撕裂者和Zen2架构的霄龙支持PCIe4.0

5、显存决定了能否运行，而CUDA核心数量、显存频率、显存种类、显卡带宽决定了运行速度

6、10系和20系移动端显卡和台式机的显卡性能基本一致，9系和30系的不一样

（个别显卡只有笔记本才有，比如GTX1650Ti，以及MaxQ显卡，MaxQ显卡规模一样，但被设置了更低的功耗墙，因此跑深度学习时较同样的桌面级显卡要差一些）

&nbsp;

**旧显卡：**

9系显卡包括：GTX950，GTX960，GTX970，GTX980，GTX980Ti，GTX TITAN X

10系显卡包括：GT1030，GTX1050，GTX1050Ti，GTX1060，GTX1070，GTX1070Ti，GTX1080，GTX1080Ti，TITAN X（Pascal），TITAN Xp

16系显卡包括：GTX1650，GTX1650Super，GTX1660，GTX1660Super，GTX1660Ti

20系显卡包括：RTX2060，RTX2060Super，RTX2070，RTX2070Super，RTX2080，RTX2080Super，RTX2080Ti，TITAN RTX


&nbsp;

**TITAN系列显卡（推荐）**

TITAN系列显卡是从7系显卡开始的一系列高端显卡

7系：GTX TITAN 6G CUDA 2688，GTX TITAN Black 6G CUDA 2880，GTX TITAN Z 12G 5760

9系：GTX TITAN X 12G CUDA 3072

10系：TITAN X（Pascal）12G 3584，TITAN Xp 12G 3840

20系：TITAN RTX 24G 4608，TITAN V 12G 5120，TITAN V CEO Edition 32G 5120（就是32GB显存版本的TITAN V）


&nbsp;

**计算卡**

7系：Tesla K80 24G CUDA 4992

9系：Tesla M40 12G/24G CUDA 3072，Tesla M4 4G CUDA 1024

10系：Tesla P100 16G CUDA 3584，Tesla P40 24G CUDA 3840，Tesla P4 8G CUDA 2560

20系：Tesla T4 16G CUDA 2560，Tesla V100 16G/32G CUDA 5120

30系：NVIDIA A100 40/80GB CUDA 6912，NVIDIA A40 48GB CUDA 10752，NVIDIA RTX A6000 48G CUDA 10752


&nbsp;

**图形卡**

图形卡不建议购买，除非是预算有很多，但PCIe数量极其有限

RTX 8000 48G，RTX 6000 24G和TITAN RTX 24G的CUDA一致

RTX 5000 16G和RTX 2080S 8G的CUDA一致

RTX 4000 8G，RTX 3000M 6G和RTX 2070 8G的CUDA一致

T2000M 4G和MX450 2G的CUDA一致

T1000M 4G的CUDA数量为768个




&nbsp;
部分TITAN、计算卡、图形卡的价格：

**TITAN V 12GB**：21999

**RTX8000 48GB**：59000；**RTX6000 24GB**：41999；**RTX5000 16GB**：20580；

**RTX4000 8GB**：7789

**Tesla V100 16G**：44999；**Tesla V100 32G**：61999；**Tesla P100 16GB**：29999；

**Tesla T4 16GB**：15499；**Tesla P4 8G**：13999；**Tesla P40 24G**：44599；

**Quadro GV100 32G**：68999


&nbsp;
## GPU的搭配（主板、CPU、硬盘、网卡、散热、机箱、电源）

**0显卡**

多路显卡推荐双槽位的显卡，已知的有：

全部的公版卡（注意RTX3090公版是三槽卡）

**华硕（ASUS）TURBO-RTX2080TI-11GD6-DL**

**技嘉（GIGABYTE）RTX2080Ti TURBO 11G**

**技嘉（GIGABYTE）RTX3090 TURBO 24G**



&nbsp;

**1 主板**

主板最好是选供电高端的，具体如何挑选请看主板篇

另外记得，例如X570，Z490这种主流游戏主板，最多接2张显卡，X299，TRX40，X399，C246，C422这些高端主板，最多接4张显卡，C612，C621，C622，最多接6张显卡


&nbsp;

**2 CPU**

CPU使用参考第一个文档


&nbsp;

**3 硬盘**

对于大数据集，使用固态硬盘能加速数据读取速度，就目前来看是选SATA还是选M.2，对GPU影响不大

不过选机械硬盘肯定要慢一点（大部分模型都卡在“读”上）


&nbsp;

**4 网卡**

能用外置网卡就用外置网卡，GPU对集成网卡的散热有一定影响


&nbsp;

**5 散热**

GPU的散热有两种，涡轮散热和风扇散热。计算卡和图形卡基本上是涡轮散热，因此基本是一张卡2槽位，ATX主板可以放下4张卡

使用风扇散热的可能要2.5-3槽位，因此一个ATX主板将只能放下2-3张卡

对于深度学习而言，涡轮散热比风扇散热好


&nbsp;

**6 机箱**

尽可能选体积大的机箱，比如追风者P600这种


&nbsp;

**7 电源**

单卡电源不得小于650w，双卡电源不得小于850w，三卡电源不得小于1200w

四卡电源不得小于2000w，八卡电源不得小于2000w*2

&nbsp;
## 多路GPU

**SLI有无帮助？**

无，SLI是两张卡交叉渲染（SLI一般是游戏显卡支持，比如980Ti和1080Ti或者早期的TITAN，比如TITAN V和TITAN Xp）


**NVLink有无帮助？**

有，但支持NVLink的显卡很少，而且通常的NVLink最多支持2张显卡。检查显卡是否支持NVLink需要去官网查询（一般是图形卡和TITAN支持）

https://en.wikipedia.org/wiki/NVLink 可通过此网站查阅NVLink的适配性和带宽，游戏卡中仅有2080，2080S，2080Ti，3090支持NVLink

一般而言NVLink要远远快于PCIe 4.0x16


**一般情况下的三卡以及更多的卡怎么进行数据交换呢？**

走PCIe通道，注意有些PCIe是CPU直连，有些是PCH扩展出来的，因此进行数据交换的时候PCIe通道的数量可能是瓶颈

&nbsp;
## GPU的软件适配（深度学习的特点）

在跑深度学习的时候，尽可能的关掉后台程序


&nbsp;
## GPU的注意事项（N卡和CUDA）

不要爆显存，不要超频


&nbsp;
## GPU的价格（选购和捡垃圾）

20系显卡选购的时候注意不要低于上面的参考价格，那基本上是各种矿卡、来路不明的二手显卡

GPU的品牌厂家：

超一线：公版显卡

一线品牌：华硕，技嘉，微星，EVGA，丽台

二线品牌：七彩虹，索泰，影驰，耕升，铭瑄，讯景，映众，

三线品牌：盈通，昂达，翔升，华擎，映泰（三线品牌可能会阉割显存）

垃圾品牌：铭影，小影霸，铭速，精影


&nbsp;
二手显卡推荐GTX1070Ti，GTX1080Ti，GTX1070，GTX980Ti
