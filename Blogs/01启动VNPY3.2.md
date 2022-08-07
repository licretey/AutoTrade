## 命令行启动

+ 安装python3.10

+ win下下载zip文件后解压

+ 进入`examples\veighna_trader`下执行`python3 run.py`

## Pycharm启动

+ 使用Pycharm打开项目时会创建虚拟环境，可建可不建

+ 假如创建了虚拟环境，则会根据requirements.txt创建环境，但vnpy部分模块并没有导入，故需要将如下模块目录加入到requirements.txt文件中去

```textile
vnpy==3.2.0
vnpy-algotrading==1.0.2
vnpy-chartwizard==1.0.2
vnpy-ctabacktester==1.0.7
vnpy-ctastrategy==1.1.0
vnpy-ctp==6.5.1.12
vnpy-ctptest==6.5.1.5
vnpy-da==1.12.1
vnpy-datamanager==1.0.5
vnpy-datarecorder==1.0.3
vnpy-esunny==1.0.2.2.5
vnpy-excelrtd==1.0.1
vnpy-femas==1.0.1
vnpy-hft==1.0.1
vnpy-hts==1.0.1
vnpy-hx==1.0.0
vnpy-ib==9.81.1.2
vnpy-ifind==1.0.0
vnpy-mini==1.5.6.6
vnpy-mongodb==1.0.3
vnpy-mysql==1.0.1
vnpy-optionmaster==1.0.4
vnpy-ost==2.0.1.2
vnpy-paperaccount==1.0.1
vnpy-portfoliomanager==1.0.1
vnpy-portfoliostrategy==1.0.1
vnpy-postgresql==1.0.0
vnpy-rest==1.0.3
vnpy-riskmanager==1.0.3
vnpy-rohon==6.5.1.5
vnpy-rpcservice==1.0.1
vnpy-rqdata==2.9.48.2
vnpy-scripttrader==1.0.1
vnpy-sec==1.0.2
vnpy-sopt==3.5.5.1
vnpy-sopttest==3.5.5.1
vnpy-spreadtrading==1.1.4
vnpy-sqlite==1.0.0
vnpy-taos==1.0.0
vnpy-tap==9.0.2
vnpy-timescaledb==1.0.0
vnpy-tinysoft==2021.6.17.2
vnpy-tqsdk==2.8.6
vnpy-tts==6.5.1.3
vnpy-tushare==1.2.64.3
vnpy-udata==2021.12.24
vnpy-uft==3.7.2.4.3
vnpy-websocket==1.0.2
vnpy-webtrader==1.0.4
vnpy-wind==1.0.1
vnpy-xtp==2.2.32.2.0
```

> + 启动Bug1
> 
> # 手动修改文件下的配置如下
> 
> # x.to_pydatetime() for x in cn_calendar.precomputed_holidays()
> 
> + 启动Bug2：numpy版本不兼容
> 
> # ImportError: cannot import name 'ZoneInfo' from 'vnpy.trader.utility'
> 
> # 最新版本要和vnpy的dev分支代码一起使用，所以降级 vnpy_tts 为6.5.1.3即可
> 
> pip uninstall vnpy_tts
> pip install vnpy_tts==6.5.1.3
> 
> + 启动Bug4：tab-lib
> 
> 到[网站Archived: Python Extension Packages for Windows](https://www.lfd.uci.edu/~gohlke/pythonlibs/#ta-lib)下载对应的wsl文件，然后`pip install xxx.wsl`

## 相关配置

+ win下vnpy启动后会在用户目录下创建隐藏目录，包含各种日志、配置等信息
+ 如目录`C:\Users\xxxPC\.vntrader`，内容如下

![](.\images\2022-08-07-13-58-54-image.png)

## 数据库配置文件

+ `.vntrader\vt_setting.json`文件是用户全局配置的数据库设置



## 之前的环境脚本

```shell
pip install vnpy_ctastrategy
pip install vnpy_ctabacktester
pip install vnpy_spreadtrading
pip install vnpy_algotrading 
pip install vnpy_optionmaster 
pip install vnpy_portfoliostrategy 
pip install vnpy_scripttrader 
pip install vnpy_chartwizard 
pip install vnpy_rpcservice 
pip install vnpy_excelrtd 
pip install vnpy_datamanager 
pip install vnpy_datarecorder 
pip install vnpy_riskmanager 
pip install vnpy_webtrader 
pip install vnpy_portfoliomanager 
pip install vnpy_paperaccount
pip install vnpy-rqdata
# 安装数据库模块
pip install importlib
# 我使用的是pg
pip install vnpy-postgresql
# 安装驱动
pip install psycopg2
pip install vnpy-sqlite


# 手动修改文件下的配置如下
# x.to_pydatetime() for x in cn_calendar.precomputed_holidays()

# 放弃1.25版numpy
pip uninstall numpy
pip install numpy

# ImportError: cannot import name 'ZoneInfo' from 'vnpy.trader.utility'
# 最新版本要和vnpy的dev分支代码一起使用，所以降级 vnpy_tts 为6.5.1.3即可
pip uninstall vnpy_tts
pip install vnpy_tts==6.5.1.3


pip install -r requirementsSupply.txt -i https://pypi.tuna.tsinghua.edu.cn/simple/



```