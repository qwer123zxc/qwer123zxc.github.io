---
layout: post
title:  "cdnDocuments"
date:   2025-03-19 10:23:52 +0800
categories: jekyll update
---


# 控制台
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503191745343.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503191748484.png)
- 数据概览、财务运营



### 新增账户
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211552858.png)

> 邮箱手机号不做真实验证, 账号使用邮箱和密码登录


### 分配订单套餐
- 分配套餐
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211524597.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211532609.png)

> 也可以在客户管理中订单详情中新增套餐



### 设置套餐流量和带宽限制

- 订单管理 -> 编辑订单 -> 修改套餐
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211926317.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211927531.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211928438.png)



### 添加站点

![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211717847.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211726733.png)
- 选择套餐, 添加域名信息和源站
    - 源站ip是http或者https, 需要设置正确,否则会导致回源失败
    - 选择跟随需要和实际回源和访问端口情况确认


### 站点域名申请证书
- 单域名证书申请
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211749589.png)
- 供应商二选一即可
> 申请失败可以检查下报错信息, 查看域名是否解析到我们CDN站点cname值, 其他错误可以选择重新申请尝试

- 泛解析域名证书申请
    - 需要新增域名商DNS账户, 下边以Cloudflare列举
    - 登录cloudflare,生成密钥API
    <img src="https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211811497.png" alt="create API" width="200px"/>
    ![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211819003.png)
    - 注意API密钥权限设置，否则可能导致申请失败
    ![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211825494.png)
    > 其他平台同理设置
    - 新增DNS账户
    ![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211829898.png)
    - 填入API
    ![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211831225.png)
    > 泛解析证书申请支持以下域名平台API

    ![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211832981.png)
    - 最后在申请证书页面, 选择DNS账户申请
    ![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211837033.png)


### 安装新节点

- 节点服务器系统Centos7.9, 执行一键安装脚本, 无需其他操作, 脚本执行完成后节点机器信息自动更新到节点列表
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211844810.png)
- 选择新安装节点 -> 初始化配置
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211850171.png)
- 添加节点到已有线路组 -> 解析 -> 绑定新节点 -> 添加到解析线路池 -> 加入节点具体ip到线路池 -> 批量解析
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211852663.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211854491.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211856639.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211859654.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211901045.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211904190.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211904335.png)
> 状态没有变化时, 可能是显示状态为更新, 点击刷新


### 设置域名跳转

- 相关站点管理 -> 高级WAF -> 高级配置 -> 重定向 -> 创建WAF规则
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211911377.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211913639.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211918599.png)

### 设置站点防火墙

- 设置普通防火墙
    - 查找相关域名站点
    - 管理 -> 高级WAF -> 强制人机验证和CC防护 -> 保存
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211034210.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211041583.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211042948.png)

- 根据攻击设置URL拦截
    - 查看高访问量URL: 统计分析 -> 访问日志 -> 搜索相关域名 -> 查看访问URL
    - 设置防火墙: 站点防火墙设置 -> 高级配置 -> 创建WAF规则
> 查看到的URL为/transform.php, 如图所示设置防火墙时value值在后边加上完整的访问路径

![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211054909.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211102353.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211111382.png)


### 防火墙屏蔽地区国家

- 选择站点 -> 管理 -> 创建WAF规则
    - 匹配类型选择: 国家/地区ISO代码
    - value规则
        - =: 与value值相同国际则执行操作
        - !=: 排除value值后其他国家都执行操作
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503240955387.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503240957315.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503241052136.png)

> 拦截方式可选择其他, 时间也可根据情况自定义设置

> [国家ISO代码查询](https://zh.wikipedia.org/wiki/ISO_3166-1)



## 日志查看
### 查看CC攻击

- 可以根据域名, 客户ID等搜索, 注意时间段选择
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503211933977.png)


### 访问日志
- 查看已添加站点的请求ip和URL, 已经响应时间和源站流量
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503241227637.png)


### 拦截日志
- 查看被拦截的访问详细信息
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503241237272.png)


### 拉黑日志
- 为站点设置防火墙后会拉黑处理ip, 查看相关站点的已经拉黑信息
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503241239265.png)
> 如果存在防火墙策略误拉黑ip, 可以在黑名单搜索到ip释放


## 线路管理
### 更改换线路组
- 订单 -> 订单管理 -> 修改线路 -> 选择套餐确认
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503241420689.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503241421484.png)
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503241422908.png)


 ## 系统维护
 ### 系统设置
 - 配置站点端口
    - Http端口: 用户源站为http自定义端口(非80端口)
    - Https端口: 用户源站为https自定义端口(非443端口)
    - 4层转发端口:使用TCP/UDP转发时需要使用
![](https://picstorehouse.oss-cn-chengdu.aliyuncs.com/img/202503241507322.png)
> 图上所示的是已经填加到设置里边的端口范围, 如果使用未在范围内的端口添加站点可能无法使用,需要手动添加下端口
