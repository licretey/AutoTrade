+ ubuntu22 安装vnpy

+ ta-lib

  + 安装miniconda

  + ```
    wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
    
    bash Miniconda3-latest-Linux-x86_64.sh
    ```

  + 安装ta-lib

    ```
    conda install -c conda-forge ta-lib;
    ```

+ vnpy安装

+ pip环境安装

+ ```
  pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
  ```

+ 

+ vnpy库安装

+ 

+ sudo bash install.sh python3



+ [Ubuntu安装vnpy参考](https://www.vnpy.com/forum/topic/30172-zui-xiang-xi-ubuntushang-vnpy3-0an-zhuang-zhi-nan-jie-he-guan-fang-wen-dang-ji-zi-ji-cai-guo-de-keng-xi-wang-dui-da-jia-you-bang-zhu)

### 关于Ubuntu 安装的调整

一键安装过程整体分为3步：

1. Ubuntu 需要准备 gcc 环境，

```shell
sudo apt update # 更新信息
sudo apt install build-essential  # 安装 gcc
```

2. 利用 conda 构建环境，例如

```shell
conda create -n vnpy3 python=3.10  #喜欢的也可以用 python=3.9
conda activate vnpy3 # 激活环境准备安装下面的东西
```

3.下载安装ta-lib库， 记得要先完成第2步，否则不知道装哪里去了，

```shell
TA_Lib    # install from src for linux
wget http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz
tar xf ta-lib-0.4.0-src.tar.gz
cd ta-lib
./configure --prefix=/usr
make
sudo make install
pip install TA-Lib
```

4. 安装requirements.txt文件内的相关依赖库；这个步骤可以省略， 因为pip 会根据第三步重新匹配相应的基础环境。

5. 安装VeighNa本身。这次系统重构后，可以让用户根据自己的需求灵活选择所需的功能，故不同的功能模块需要独立安装。一个典型的安装组合如下， 利用 sqlite存放tushare的数据，所有功能都装上，有点贪心。其实不做期货的就可以用用装期货模块：

```shell
pip install vnpy vnpy_ctastrategy vnpy_ctabacktester vnpy_spreadtrading vnpy_optionmaster vnpy_portfoliostrategy vnpy_algotrading vnpy_scripttrader vnpy_paperaccount vnpy_chartwizard vnpy_portfoliomanager vnpy_rpcservice vnpy_datamanager vnpy_datarecorder vnpy_excelrtd vnpy_riskmanager vnpy_webtrader vnpy_rest vnpy_websocket vnpy_sqlite vnpy_mysql vnpy_tushare vnpy_ctp
```

特别提醒，若是在虚拟机上运行，请把内存调至4G以上，否则会报错内存不足。