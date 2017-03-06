## 在Anaconda@Linux 中安装 TensorFlow 及环境配置

>作者：`小磊`

>时间：`2017/03/05`

>邮箱：`ylxx@live.com`


### 此教程与[TensorFlow官方教程](https://www.tensorflow.org/install/install_linux#InstallingAnaconda)不同之处在于：

1. 在国际网络不稳定的环境下，安装TensorFlow及其依赖环境
2. 在Anaconda中安装 以隔离系统环境

### 此教程需要的基础技能为
1. 了解基础的Linux命令及软件安装配置
2. 能使用`Shadowsocks`访问`google.com`等网站


### 我的环境一览
* `Ubuntu` 16.04 LTS 64bit (Google 官方推荐)
* `TenosorFlow` 1.0 CPU only
* `Anaconda2` with `Python` 2.7.13

### 用户切换为`root`

首先，将当前用户切换为`root`来执行
经验表明 在Ubuntu下，若使用`sudo`，当前的一些环境变量会被改变
为避免不必要的麻烦 建议直接用`root`账户

注意 *若是新安装的Ubuntu 默认没有root密码 通过命令`sudo passwd`设置root密码*

### 安装Anaconda2

在[清华大学镜像站 Anaconda 仓库镜像](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)中下载最新版本且对应你系统的Anaconda2

例如 我的配置在2017/03月 应下载[Anaconda2-4.3.0-Linux-x86_64.sh  ](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda2-4.3.0-Linux-x86_64.sh)


为下载好的`.sh`文件添加执行权限
例如 `chmod +x Anaconda2-4.3.0-Linux-x86_64.sh `

运行`.sh`文件
例如 `./Anaconda2-4.3.0-Linux-x86_64.sh `

按照操作指示一步一步走

安装完成Anaconda2后 测试是否成功 在命令行输入 `conda -V`

出现`conda 4.3.8`类似字样后则成功

若出现`conda：未找到命令`字样

则是 `Anaconda/bin` 文件没有加到PATH 变量

只需修改用户的`~/.bashrc`将`Anaconda/bin`目录添加到`PATH`变量

例如： 将 `export PATH="/home/yl/anaconda/bin:$PATH"`添加到`/root/.bashrc`文件最后

### 获得 tensorflow.whl 文件
[TensorFlow官方教程](https://www.tensorflow.org/install/install_linux#InstallingAnaconda)

由于 https://TensorFlow.org 是由谷歌托管的 而谷歌的绝大多数服务器都被屏蔽了 所以 无法直接访问官网下载所需的 tensorflow.whl

两种方法
1. Windows 下载好后 传给Linux
2. Linux 对终端使用网络代理 走Shadowsocks

#### 1. Windows 下载好后 传给Linux的方法

先在Winows系统下 翻墙访问官网的[The URL of the TensorFlow Python package](https://www.tensorflow.org/install/install_linux#TF_PYTHON_URL) 下载适合你系统环境的 tensorflow.whl 最新版 我的是`Python 2.7 CPU only`

将 tensorflow.whl 传送到Ubuntu下

安装 tensorflow.whl 会需要从包管理服务器`pypi`上下载很多依赖 ，由于中国网络对国际带宽的限制，十次下载 九次失败

所以 下载前 我们得把pip的源换成国内的镜像源 我选择的是阿里云的镜像

创建 `~/.pip/pip.conf`文件(注意 `~/.pip` 是文件夹)
并写下如下配置
```bash
[global]
index-url = https://mirrors.aliyun.com/pypi/simple/
```

可以开始安装了

root 下运行 `pip install --ignore-installed --upgrade`加上 tensorflow.whl的文件名

比如： `pip install --ignore-installed --upgrade tensorflow-1.0.0-cp27-none-linux_x86_64.whl`

就安装完成了


#### 2. Linux 对终端使用网络代理 走Shadowsocks

这个方法请参考这个教程[使用polipo 让Ubuntu 终端  走Shadowsocks 客户端代理](https://jingsam.github.io/2016/05/08/setup-shadowsocks-http-proxy-on-ubuntu-server.html)
让终端翻墙

翻墙访问官网的[The URL of the TensorFlow Python package](https://www.tensorflow.org/install/install_linux#TF_PYTHON_URL)找到适合你系统环境的 tensorflow.whl 最新版链接 我的是`Python 2.7 CPU only`

然后 直接运行 `pip install --ignore-installed --upgrade` 加上tensorflow.whl链接地址

 比如`pip install --ignore-installed --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.0.0-cp27-none-linux_x86_64.whl`


### 安装完成

在root下 输入`spyder`命令打开spyder编辑器
输入
```Python
import tensorflow as tf
print tf.__version__
```
并运行 ，出现版本号则成功












EOF
