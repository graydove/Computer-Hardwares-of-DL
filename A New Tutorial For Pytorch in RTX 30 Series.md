# 个人深度学习工作站配置指南

配置时间：2020.12.15

此时pytorch官方刚刚发布了支持RTX3090和cuDNN 8.0.5的pytorch1.7.1版本，因此比较适合装机。



## 0 前言

VCB的群里兴起了一股使用先马趣造机箱来装机的潮流，因此我也想试试，看看这个机箱能不能满足“实习生级”的装机和运行。实际上是可以的，只是未来如果要再加1张3090是要换机箱、主板、电源了。



## 1.硬件篇

- **CPU**：i3-10100F（4核心8线程）
- **显卡GPU**：影驰RTX3090金属大师OC 24G
- **内存**：金士顿骇客神条DDR4 2666 32G x4共128G
- **主板**：技嘉B460M Aorus Elite
- **固态硬盘**：2TB英睿达MX500 + 1TB英睿达MX500 + 512GB三星970EVO
- **机械硬盘**：西部数据蓝盘4TB
- **电源**：酷冷至尊V750 SFX 750w电源
- **散热器**：大镰刀S950M下压式散热器
- **机箱**：先马趣造

主板图片，可以看到主板的扩展性就单张卡而言基本上足够了。

![image-20201215210410321](https://i.loli.net/2020/12/15/DUmg4rYW7vQyxVF.png)



吐槽：

关于CPU：这CPU性能够么？基本上是足够的，如果不够后期还可以升级到10700F和10900F

关于内存：有必要用128GB么？自从用了某个占用100GB的算法之后，就有一种内存不足恐惧症

关于固态硬盘：为什么要这么多固态？2TB是日常跑的时候用的，1TB是备份盘，512G是用来加速机械硬盘

关于机械硬盘：用来存数据，多媒体领域的数据集动不动就100GB-200GB，6TB以上的硬盘太吵了

关于电源：由于显卡长度有318mm，使用ATX电源需要用胶带固定，SFX电源不用

关于散热器：随便买的散热器，下压式的可以保证机箱内的风道是从上到下的垂直方向

关于机箱：如果不用底部风扇（其实个人感觉没什么用，用了猫头鹰的A12-25发现都没怎么降低温度），最多可以接3个3.5寸硬盘和2个SATA硬盘



## 2.系统篇

教程仅适用于Ubuntu18.04，Ubuntu16和20并不适用

### 2.1 安装Ubuntu 18.04.5 LTS系统

之所以选择18.04而不是20.04是因为不熟悉python3.8，另外貌似有个程序在ubuntu20下兼容性不好

安装操作系统不再详述，找个网络环境好一点的地方和时间段安装就可以



### 2.2 **配置国内镜像软件源**

这是必须的，不然apt-fast也救不了你

1. 备份原来的源：

```shell
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

2. 将源的内容设置为阿里云镜像：

```shell
sudo vim /etc/apt/sources.list
```

内容改为：

```shell
deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
```

3. 更新软件列表：

```shell
sudo apt update
sudo apt upgrade
```



### **2.3 安装Python和pip**

暂时没有安装其他的python，可以直接使用python3.6.9

Ubuntu系统默认自带python，有版本需求的话也可以自己安装一下（不安装也行因为后面会安装conda环境）：

```shell
sudo apt install python3
sudo apt install python3-pip
```

不管是不是自己安装的python，替换python的pip源建议是一定操作一下的，pip安装速度会快很多：

```shell
cd ~
mkdir .pip
sudo vim ~/.pip/pip.conf
```

改为以下内容（这里用的清华源，也可以试一下阿里、豆瓣等源）：

```shell
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple/ 
[install]
trusted-host = pypi.tuna.tsinghua.edu.cn
```



### **2.4 配置SSH**

```shell
sudo apt-get install openssh-server
```

并用以下命令启动

```shell
/etc/init.d/ssh start
```



## **3. DL开发环境配置篇**

### **3.1 安装Nvidia显卡驱动**

安装显卡驱动有两种方式

方法1：用界面安装

进入系统的图形桌面，打开`Software & Updates`软件，可以看到标签栏有一个`Additional Drivers`：

![2020-12-16 21-48-07 的屏幕截图](https://i.loli.net/2020/12/16/JGkl1ZoMmEz2XdH.png)

选择第一个安装Nvidia官方驱动（第二个是开源驱动）即可，根据网络情况稍等大概十分钟，安装完重启服务器。

重启完之后更新一下软件：

```shell
sudo apt update
sudo apt upgrade
```

这里会连带Nvidia的驱动一起升级一遍，更新到最新的驱动；更新完可能会出现nvidia-smi命令报错，再重启一下就解决了。

方法2：

```shell
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-driver-455
```



### **3.2 安装CUDA**

卸载之前版本的CUDA，直接去`/usr/local`里删掉之前的CUDA文件夹就可以了

**按照前面的方法重新安装显卡驱动**，安装好了之后开始安装CUDA：

去官网下载cuda安装包：[CUDA Toolkit 11.0 Download | NVIDIA Developer](https://link.zhihu.com/?target=https%3A//developer.nvidia.com/cuda-11.0-download-archive)，相关选项如下（根据实际情况选择）：

![image-20201215205514510](https://i.loli.net/2020/12/15/xHCFQDq4jnmXBRT.png)

如果显卡是RTX3090，RTX3080，RTX3070，RTX3060Ti等，用CUDA11.0

（虽然理论上支持SM86核心更好的其实应该是CUDA11.1）

1. 运行下面的命令进行安装：

```shell
chmod +x cuda_11.0.2_450.51.05_linux.run
sudo sh ./cuda_11.0.2_450.51.05_linux.run
```

**PS：注意在安装CUDA的时候不要安装驱动，任何时候都是这样的**

要记住安装位置，默认是安装在/usr/local/cuda-9.0文件夹下。

配置环境变量，运行如下命令打开profile文件

```shell
sudo vi /etc/profile
```

2. 打开文件后在文件末尾添加路径，也就是安装目录，命令如下：

```shell
export CUDA_HOME=/usr/local/cuda-11.0
export LD_LIBRARY_PATH=${CUDA_HOME}/lib64
export PATH=${CUDA_HOME}/bin:${PATH}
```

然后使其生效

```shell
source ~/.bashrc
```

之后重启电脑：

```shell
sudo reboot
```

3. 测试CUDA的Samples例子

```shell
cd /usr/local/cuda/samples/1_Utilities/deviceQuery
sudo make
./deviceuery
```

如果成功，应该显示显卡信息：

![image-20201216220212570](https://i.loli.net/2020/12/16/DnLsC5EeAmiwBHq.png)



### **3.3 安装cuDNN**

去[cuDNN Download](https://developer.nvidia.com/rdp/cudnn-download)下载cuDNN，要注册NVIDIA账号。

**当前唯一的选择是cuDNN  v8.0.5**

![image-20201216220846961](https://i.loli.net/2020/12/16/x7eEIz1vwXYsirJ.png)

重命名为：`cudnn-11.0-linux-x64-v8.0.5.39.tgz`

下载cuDNN后解压，解压到：`/usr/local/cuda/`

```shell
sudo tar zxf cudnn-11.0-linux-x64-v8.0.5.39.tgz -C /usr/local/
```



### **3.4 安装Conda环境**

不同的训练框架和版本可能会需要不同的python版本相对应，而且有的包比如numpy也对版本有要求，所以比较优雅的方法是给每个配置建立一个**虚拟的python环境**，在需要的时候可以随时切换，而不需要的时候也能删除不浪费磁盘资源，那在这方面conda是做得最好的。

下面介绍怎么安装conda：

1. 在Anaconda官网下载Linux安装包：[Anaconda | Individual Edition](https://link.zhihu.com/?target=https%3A//www.anaconda.com/products/individual)
2. 运行下面的命令安装：

```shell
chmod +x Anaconda3-2020.11-Linux-x86_64.s
./Anaconda3-2020.11-Linux-x86_64.sh
```

一路按ENTER确认，然后根据提示输入yes

然后会询问你是否要初始化conda，输入yes确认，重开终端窗口之后，就可以看到conda环境可用了（base代表默认环境）：

<img src="https://i.loli.net/2020/12/16/UCx5ARqVgQnfuXD.png" alt="image-20201216221156245" style="zoom: 50%;" />

**conda的使用方法网上搜一下有很多，这里就不赘述了。**

conda配置源：

```shell
sudo vim ~/.condarc
```

配置文件改为：

```shell
channels:
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo/
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
    - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
show_channel_urls: true
```

  然后重启即可



PS：如果不想每次重启之后都要进入base环境，可以在重启后输入：

```sh
conda config --set auto_activate_base false
```



### **3.5 Pytorch测试（pip）**

可以用

```shell
pip install torch==1.7.1+cu110 torchvision==0.8.2+cu110 torchaudio===0.7.2 -f https://download.pytorch.org/whl/torch_stable.html
```

或者（已经假设换好pip源了）

```shell
pip install torch==1.7.1 torchvision==0.8.2 torchaudio===0.7.2
```

正常情况下的pytorch测试结果：

![image-20201216222015460](https://i.loli.net/2020/12/16/KaMEFHSLG27Tfdy.png)

这是因为CUDA11.0和RTX3090等显卡的兼容性还不够好，这种情况下使用pytorch可能会出现其他的问题



### 3.6 Pytorch测试（conda）

可以用

```shell
conda install pytorch torchvision torchaudio cudatoolkit=11.0 -c pytorch
```

或者（已经假设换好conda源了）

```shell
conda install pytorch torchvision torchaudio cudatoolkit=11.0
```

正常情况下的pytorch测试结果：

![image-20201216222730396](https://i.loli.net/2020/12/16/hVFci6pt3YHj8nL.png)

这里没有pip的问题，说明是正常的



如果有问题，请输入`python3 -m torch.utils.collect_env`自查一下

正常应该是：

![image-20201219232959278](https://i.loli.net/2020/12/19/D8YXlHG4hEzMPJN.png)

注意图里的cuda，cudnn，pytorch版本



## 后记

Caffe、Tensoflow（2.3.1）在RTX3090的测试都还没成功...不知道什么时候可以出新的版本
