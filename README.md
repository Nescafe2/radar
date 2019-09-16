# 风控引擎（Radar）
## 项目介绍
### 实时风控引擎，实时可配置，规则配置即时生效。 开箱即用！！！开箱即用！！！开箱即用！！！
### a real-time risk analysis engine, real-time update risk rule, real-time effect, anti-fraud transaction  is perfect, project code  is Radar, like the code, Radar like an eyes which look the transaction automatic. 

## 背景
  伴随着移动互联网的高速发展，羊毛党快速崛起，从一平台到另一个平台，所过之处一地鸡毛，这还不是最可怕的，
  随之而来的黑产令大部分互联网应用为之胆寒，通常新上线的APP的福利比较大，风控系统不完善，BUG 被发现的频率也比较高，
  黑产利用BUG短时间给平台带来了巨大的损失，某多多的（100元测试优惠券，一夜损失上百万W）就是一例。 
  针对这一现象， 拥有一款实时的风控引擎是所有带有金融性质的APP 的当务之急，
  Radar 应景而生，Radar本来是笔者前公司的一个内部项目，公司现在不复存在，考虑到项目本身的价值，
  现在使用Springboot进行升级，并删除了很多本地化功能，只保留风控引擎核心，更具通用型，二次开发成本低。

## 项目架构

前后端分离架构

后端技术框架： SpringBoot + Mysql +  MongoDB + Redis + Groovy 

前端技术框架： React(SPA) 

## 技术选型
Springboot：笔者是java 出生， 选择 Springboot 理所当然，全家桶确实方便。

mysql ： 本项目中关系数据库的作用不大，主要用于存放 风险模型的元信息。

MongoDB： 用于存放事件JSON， 提供基本统计学计算（例如：max, min, sum, avg, ），
复杂的统计学概念（sd,variance, etc...）在内存中计算。

Redis： 提供缓存支持

Groovy： 脚本引擎，风控规则最后都生成 groovy 脚本， 可以动态配置，即时生效。

## 名词解释
### Model: 模型
 用户行为事件， 例如：注册，登录，购买，提现。。。
### PreItem: 预处理 
 像IP，手机号码段等事件属性，可能无法直接计算，通过预处理插件 转换成 其他格式，
  例如:ip 可以通过IP 插件变成位置和地址
### Abstraction: 特征
特征工程，例如用户小时交易次数，IP 一天交易金额，设备一小时交易次数。。。
### Adaptation: 机器学习模型适配器
 使用训练好的机器学习模型，进行检测
### Activation: 策略（翻译不恰当）
一个模型可以定义多个 activation,每个activation都可以独立配置规则，
例如，用户注册行为， 可以定义：异常注册， 垃圾注册， 可以输出多个activation。
### Rule: 规则
在计算 abstraction 和 activation 之前，需要先检查数据是否正常，检查就是按照rule 进行检测。

---
## Manual
### 安装部署
    
    mvn install 
    # 运行服务端 
    cd radar-admin 
    java -jar radar-admin.jar
    # 运行引擎端
    cd radar-engine
    java -jar radar-engine.jar


### 模型配置
![主页](https://github.com/wfh45678/radar/blob/master/resources/images/01.png)
![字段管理](https://github.com/wfh45678/radar/blob/master/resources/images/03.png)
![规则管理](https://github.com/wfh45678/radar/blob/master/resources/images/07.png)
![构建模型](https://github.com/wfh45678/radar/blob/master/resources/images/08.png)

### 三方系统对接风控EngineAPI
![API DOC](https://github.com/wfh45678/radar/blob/master/resources/images/09.png)
![事件提交](https://github.com/wfh45678/radar/blob/master/resources/images/10.png)
---

## Contact to

 Mail to wfh45678@163.com , QQ 240159429 
