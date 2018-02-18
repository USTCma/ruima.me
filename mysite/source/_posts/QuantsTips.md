title: Quant资料整理
date: 2017-10-03 16:54:00
tags: [摘要,Quant,理财]
categories: '摘要'
description: 
---

最近，我下载了App Store财务分类下，有银行管存<sup>[1]</sup>的所有的互金产品，包括爱钱进、悟空理财、PPmoney，好规划等等。我发现大部分理财产品新人礼包的综合年利率都能达到10%以上，但是要么只能维持一个月、要么就是有定额限制。在收益驱动下，我又开始接触且慢和魔方理财，受这些量化投资APP的启发，自己慢慢开始琢磨一些策略，所以整理出一些Quant<sup>[2]</sup>资源。

## 国内在线量化平台

[BigQuant](https://bigquant.com/) - 你的人工智能量化平台

[镭矿](http://www.raquant.com/) - 基于量化回测平台

[果仁网](http://guorn.com/) - 回测量化平台

[京东量化](http://quant.jd.com/) - 算法交易和量化回测平台

[优矿](http://uqer.io/home/) - 通联量化实验室

[Ricequant](http://www.ricequant.com/) - 量化交易平台

[况客](http://qutke.com/) - 基于R语言量化回测平台

## 相关平台

[掘金量化](http://www.myquant.cn/) - 支持C/C++、C#、MATLAB、Python和R的量化交易平台

[DigQuant](http://www.digquant.com.cn/) - 提供基于matlab量化工具

[SmartQuant](http://www.smartquant.cn/) - 策略交易平台

[OpenQuant](http://github.com/QuantBox/OpenQuant-Esunny) - 基于C#的开源量化回测平台

## 开源框架

[Pandas](http://github.com/pandas-dev/pandas) - 数据分析包

[Zipline](http://github.com/quantopian/zipline) - 一个Python的回测框架

[vnpy](http://github.com/vnpy/vnpy) - 基于python的开源交易平台开发框架

[tushare](http://pypi.python.org/pypi/tushare/) - 财经数据接口包

[easytrader](http://github.com/shidenggui/easytrader) - 进行自动的程序化股票交易

[pyalgotrade](http://github.com/gbeced/pyalgotrade) - 一个Python的事件驱动回测框架

[pyalgotrade-cn](http://github.com/Yam-cn/pyalgotrade-cn) - Pyalgotrade-cn在原版pyalgotrade的基础上加入了A股历史行情回测，并整合了tushare提供实时行情。

[zwPython](http://github.com/ziwang-com/) - 基于winpython的集成式python开发平台

[quantmod](http://github.com/joshuaulrich/quantmod) - 量化金融建模

[rqalpha](http://github.com/ricequant/rqalpha/) - 基于Python的回测引擎

[quantdigger](http://github.com/QuantFans/quantdigger) - 基于python的量化回测框架

[pyktrader](http://github.com/harveywwu/pyktrader) - 基于pyctp接口，并采用vnpy的eventEngine，使用tkinter作为GUI的python交易平台

[QuantConnect/Lean](http://github.com/QuantConnect/Lean) - Lean Algorithmic Trading Engine by QuantConnect (C#, Python, F#, VB, Java)

[QUANTAXIS](http://github.com/yutiansut/QUANTAXIS) - 量化金融策略框架

## 库

[pandas](http://pandas.pydata.org/) - Python做数据分析的基础

[pyql](http://github.com/enthought/pyql) - Cython QuantLib wrappers

[ffn](http://pmorissette.github.io/ffn/quick.html) - 绩效评估

[ta-lib](http://github.com/mrjbq7/ta-lib): Python wrapper for TA-Lib (http://ta-lib.org/). - 技术指标

[StatsModels](http://statsmodels.sourceforge.net/): Statistics in Python — statsmodels documentation - 常用统计模型

[arch](http://github.com/bashtage/arch): ARCH models in Python - 时间序列

[pyfolio](http://github.com/quantopian/pyfolio): Portfolio and risk analytics in Python - 组合风险评估

[twosigma/flint](http://github.com/twosigma/flint): A Time Series Library for Apache Spark - Apache Spark上的时间序列库

## 数据源

[TuShare](http://tushare.org/) - 中文财经数据接口包

[Quandl](http://www.quandl.com/) - 国际金融和经济数据

[Wind资讯-经济数据库](http://www.wind.com.cn/NewSite/edb.html) - 收费

[东方财富 Choice金融数据研究终端](http://choice.eastmoney.com/Product/index.html) - 收费

[iFinD 同花顺金融数据终端](http://www.51ifind.com/) - 收费

[朝阳永续 Go-Goal数据终端](http://www.go-goal.cn/) - 收费

[天软数据](http://www.tinysoft.com.cn/TSDN/HomePage.tsl) - 收费

[国泰安数据服务中心](http://www.gtarsc.com/) - 收费

[锐思数据](http://www.resset.cn/) - 收费

[恒生API](http://open.hscloud.cn/) - 收费

[Bloomberg API](http://www.bloomberglabs.com/api/libraries/) - 收费

[数库金融数据和深度分析API服务](http://developer.chinascope.com/) - 收费

[Historical Data Sources](http://quantpedia.com/Links/HistoricalData) - 一个数据源索引

[预测者网](http://www.yucezhe.com/) - 收费

[巨潮资讯](http://www.cninfo.com.cn/cninfo-new/index) - 收费

[通联数据商城](http://www.datayes.com/) - 收费

[通达信](http://www.tdx.com.cn/) - 免费

## 数据库

manahl/arctic: High performance datastore for time series and tick data - 基于mongodb和python的高性能时间序列和tick数据存储

kdb | The Leader in High-Performance Tick Database Technology | Kx Systems - 收费的高性能金融序列数据库解决方案

MongoDB Blog - 用mongodb存储时间序列数据

InfluxDB – Time-Series Data Storage | InfluxData - Go写的分布式时间序列数据库

OpenTSDB/opentsdb: A scalable, distributed Time Series Database. - 基于HBase的时间序列数据库

kairosdb/kairosdb: Fast scalable time series database - 基于Cassandra的时间序列数据库

SQLite Home Page

## 网站、论坛、社区、博客

[BigQuant量化社区](http://community.bigquant.com/)

[算法组_新浪微博](http://weibo.com/u/3183064657%3Ftopnav%3D1%26wvr%3D6%26topsug%3D1)

[海洋部落](http://www.oceantribe.org/xf/index.php)

[水木社区](http://www.newsmth.net/)

[（经管之家）人大经济论坛](http://bbs.pinggu.org/forum-2166-1.html)

[清华大学学生经济金融论坛](http://forum.thuquant.com/)

[Code4Quant](http://code.tradeclassroom.com/)

[量化交易 - 热门问答 - 知乎](https://www.zhihu.com/topic/19815465/hot)

[集思录 - 低风险投资 - 集思录](http://www.jisilu.cn/)

[雪球 - 聪明的投资者都在这里](http://xueqiu.com/%23/)

[myquant/strategy: 掘金策略集锦](http://github.com/myquant/strategy/)

[芝诺量化交易,程序化交易](http://www.zenotrade.com/)

[统计之都 (Capital of Statistics)](http://cos.name/)

[中国量化投资学会](http://www.chinaqi.org/default.php)

[宽客 (Quant) - 索引 - 知乎](https://www.zhihu.com/topic/19557481)

[faruto的博客](http://blog.sina.com.cn/s/blog_4cf8aad30102e5dh.html)

[david自由之路](http://blog.sina.com.cn/financialindependence)

[债券的大拿没钱又丑](http://wangzhai2008.blog.hexun.com/)

[期货用来复盘的blog](http://huzi2010.blog.hexun.com/)

[股海泛舟 - 股海范舟](http://xman707.blog.163.com/)

[带头大哥777的博客](http://dtdg777.blog.163.com/)

## 交易API

[上海期货信息技术有限公司CTP API](http://www.sfit.com.cn/5_2_DocumentDown.htm) - 期货交易所提供的API

[飞马快速交易平台](http://www.cffexit.com.cn/static/3000201.html) - 上海金融期货信息技术有限公司 - 飞马

[大连飞创信息技术有限公司](http://www.dfitc.com.cn/portal/cate%3Fcid%3D1364967839100%231) - 飞创

[vnpy](http://github.com/vnpy/vnpy) - 基于python的开源交易平台开发框架

[QuantBox/XAPI2](http://github.com/QuantBox/XAPI2) - 统一行情交易接口第2版

[easytrader](http://github.com/shidenggui/easytrader) - 提供券商华泰/佣金宝/银河/广发/雪球的基金、股票自动程序化交易，量化交易组件

[IB API | Interactive Brokers](http://www.interactivebrokers.com.hk/cn/index.php%3Ff%3D5234%26ns%3DT) - 盈透证券的交易API

## 书籍

《投资学》第6版[美]兹维·博迪.文字版 

《打开量化投资的黑箱》 里什·纳兰

《宽客》[美] 斯科特·帕特森（Scott Patterson） 著；译科，卢开济 译

《解读量化投资：西蒙斯用公式打败市场的故事》 忻海 

《Trends in Quantitative Finance》 Frank J. Fabozzi, Sergio M. Focardi, Petter N. Kolm

《漫步华尔街》麦基尔

《海龟交易法则》柯蒂斯·费思

《交易策略评估与最佳化》罗伯特·帕多

《统计套利》 安德鲁·波尔《信号与噪声》纳特•西尔弗

《期货截拳道》朱淋靖

《量化投资—策略与技术》 丁鹏

《量化投资—以matlab为工具》 李洋faruto

《量化投资策略:如何实现超额收益Alpha》 吴冲锋

《中低频量化交易策略研发（上）》 杨博理

《走出幻觉走向成熟》 金融帝国

《通往财务自由之路》范K撒普

《以交易为生》 埃尔德

《超越技术分析》图莎尔·钱德

《高级技术分析》布鲁斯·巴布科克

《积极型投资组合管理》格里纳德，卡恩

《金融计量学:从初级到高级建模技术》 斯维特洛扎

《投资革命》Bernstein

《富可敌国》Sebastian Mallaby

《量化交易——如何建立自己的算法交易事业》欧内斯特·陈

《聪明的投资者》 巴菲特

《黑天鹅·如何应对不可知的未来》 纳西姆·塔勒布

《期权、期货和其他衍生品》 约翰·赫尔

《Building Reliable Trading Systems: Tradable Strategies That Perform As They Backtest and Meet Your Risk-Reward Goals》 Keith Fitschen

《Quantitative Equity Investing》by Frank J. Fabozzi, Sergio M. Focardi, Petter N. Kolm
Barra USE3 handbook

《Quantitative Equity Portfolio Management》 Ludwig Chincarini

《Quantitative Equity Portfolio Management》 Qian & Hua & Sorensen

----
[1]银行管存：银行存管是由银行管理资金，平台管理交易，做到资金与交易的分离，使得平台无法直接接触资金，避免客户资金被直接挪用。[查询地址](http://www.p2peye.com/platform/bank/)
[2]Quant：宽客，设计并实现金融的数学模型（主要采用计算机编程），包括衍生品定价，风险估价或预测市场行为等。
