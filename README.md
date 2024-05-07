# 淘宝【Kiki技术站】定制镜像

# 网络下行应用

## ！！！注意！！！

2024年4月15日，luckyant/networkdownload镜像已经上线设备密钥管理。

（1）base版本不受影响；

（2）pro版本、release版本、dev版本，需要获取分发密钥key，才能够正常运行镜像。

## 一、功能版本区分

- base版本：免费版本

```bash
【功能介绍】
仅支持简单的下行功能；
仅支持配置线程th、链接url；
使用客户可自由拉取、运行镜像；
【如需支持】
如需本店提供远程支持，是需要付费的；
具体价格一般按本店最低价1单收取，复杂情况需要按照实际工作量确定。
【TAG】
docker pull luckyant/networkdownload:base
```

- pro版本：增强下行功能，持续更新，按设备进行永久授权，量大优惠

```bash
【授权】
仅对不同设备进行限制，单个设备运行多少个容器不做限制，永久授权；
【定价】
原则上，价格按 1单每设备 收取；
量多优惠，联系店铺
【功能】
列入本店的开发项目，将持续更新维护功能；
支持功能项选择，多种下行模式切换；
支持多种设备芯片架构；
支持对未支持设备新增调试；
【目前开发功能项】
支持远程获取仓库链接自动切换；
支持失效链接自动pass；
...
【TAG】
docker pull luckyant/networkdownload:pro
```
- release版本：客户定制版本

```bash
【授权】
功能一次性永久授权，不做设备限制
【定价】
原则上，价格按2单起步，按定制功能累加原则，原则上价格上不封顶
【功能】
在基础功能上进行定制开发；
支持客户的设定功能；
【TAG】
docker pull luckyant/networkdownload:release-【日期版本号】
```

- dev版本：先行预览版本，未发布，敬请期待

```bash
【授权】
设备+镜像+店铺链接仓库的永久授权模式
【TAG】
docker pull luckyant/networkdownload:dev-【日期版本号】
```

## 二、运行范例

### 2.1 指定网络

```bash
docker network create -d bridge --subnet=192.168.2.0/24 --gateway=192.168.2.1 downloadnet
```
### 2.2 确定环境变量
- 付费秘钥 key=xxxxx
- 并发线程 th=4
- 资源链接 url=xxxxxxxxx
### 2.3 启动下行
```bash
docker run -d \
--restart=always \
--net=downloadnet \
-e key=xxxxx \
-e th=4 \
-e url=xxxxxxxxx \
luckyant/networkdownload:base
```
