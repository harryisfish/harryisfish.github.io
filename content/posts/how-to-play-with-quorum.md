---
title: "How to Play With Quorum"
date: 2022-11-11T14:31:56+08:00
draft: false

tags: ["quorum", "rum", "rumsystem", "golang", "server", "p2p", "social_media", "blockchain"]
---

# Quorum 是什么

Quorum 是 [Rum System](https://rumsystem.net) 的具体实现，它能让你自己搭建一个可以立即使用的节点并让你方便地和其他节点交换信息。全过程不依赖中心化服务器（商）。

# 这篇文章的目的

这个项目还在持续开发中，所以各方面资料较少，所以这里我想分享一个相对方便的上手方式。

# 环境准备
- 一台联网的电脑
- Golang 1.18.5 (其他版本我没测试过，理论上 1.13 以上都没问题)
# 获取 Quorum
## 如果你要编译（可以跳过）：
```bash
$ git clone https://github.com/rumsystem/quorum.git
$ cd quorum
$ make buildall
```
检查一下 /dist 文件夹下有无生成各平台的二进制可执行文件
如果你编译了，那么下面的所有 go run ./cmd/main.go 都可以替换为 ./quorum

运行前，可以先看看 [API 文档](https://rumsystem.github.io/quorum-api/#/)

Quorum 本身是一套自动的程序，但是它如何与使用者交互呢？
在它运行的时候，会启动一个 HTTP 服务器，监听一个指定的本地端口（启动 Quorum 的时候会作为参数传给它），所有的操作都被封装 为 HTTP 请求。
如果想要了解 Quorum 的运行效果，通过 HTTP 与它交互是不可避免的，所以我建议你在启动 Quorum 前，先去下载一个 [APIFOX](https://www.apifox.cn/)。
然后可以把官方生成的接口文档的 swagger.json 按照这个教程导入到自己本地的 APIFOX 并自动保持更新。
这样不仅能够查阅到最新的 API 和用法，还能通过 APIFOX 的接口调试功能很方便地与本地的 Quorum 节点（马上我们就会尝试启动它们）交互。

启动节点

接下来，你会启动三个节点：
```
bootstrap node 类似于 BT 网络上的 Tracker
owner node
user node
```
事实上，后两者是同等级的，只是名字不一样。
官方的教程在这, 接下来我直接复制过来：
# Setup local test network

cd to quorum souce code path and create config/ dir
```
mkdir -p config
start bootstrap node

go run cmd/main.go -bootstrap -listen /ip4/0.0.0.0/tcp/10666 -logtostderr=true
```

output:
```
I0420 14:58:47.719592     332 keys.go:47] Load keys from config
I0420 14:58:47.781916     332 main.go:64] Host created, ID:<QmR1VFquywCnakSThwWQY6euj9sRBn3586LDUm5vsfCDJR>, Address:<[/ip4/172.28.230.210/tcp/10666 /ip4/127.0.0.1/tcp/10666]>
Record <HOST_ID>, for example:
QmR1VFquywCnakSThwWQY6euj9sRBn3586LDUm5vsfCDJR
```

# Start owner node
```
go run cmd/main.go -peername owner -listen /ip4/127.0.0.1/tcp/7002 -apilisten :8002 -peer /ip4/127.0.0.1/tcp/10666/p2p/<QmR1VFquywCnakSThwWQY6euj9sRBn3586LDUm5vsfCDJR> -configdir config -datadir data -keystoredir ownerkeystore  -jsontracer ownertracer.json -debug=true
```
>PS: 这里有个小坑，启动指令里面的 HOST_ID 部分是不需要加 <> 的，原文意思是这个地方需要替换，要替换为你启动 bootstrap 是得到的 HOST_ID。
>你只需要形如：go run cmd/main.go -peername owner -listen /ip4/127.0.0.1/tcp/7002 -apilisten :8002 -peer /ip4/127.0.0.1/tcp/10666/p2p/QmR1VFquywCnakSThwWQY6euj9sRBn3586LDUm5vsfCDJR -configdir config -datadir data -keystoredir ownerkeystore -jsontracer ownertracer.json -debug=true 即可。后面的指令也同理。这里提出以防呆。


For the first time, user will be asked to input a password for the node, if not given, a password will be created for the node
After a password is created, next time user will be asked to input the password to open node.
env RUM_KSPASSWD can be used to input node password, like:
```
RUM_KSPASSWD=<node_passwor> go run cmd/main.go...
Start user node

go run cmd/main.go -peername user -listen /ip4/127.0.0.1/tcp/7003 -apilisten :8003 -peer /ip4/127.0.0.1/tcp/10666/p2p/<QmR1VFquywCnakSThwWQY6euj9sRBn3586LDUm5vsfCDJR> -configdir config -datadir data -keystoredir userkeystore  -jsontracer usertracer.json -debug=true
```
# 三个节点是什么样子的结构？

owner 节点和 user 节点都连接到了 bootstrap 节点，bootstrap 节点帮助两个节点互相发现，之后，这两个节点就可以互传消息。

启动节点之后，怎么用 APIFOX 交互？

打开你的 APIFOX，右上角可以配置环境。
在新窗口可以复制三个测试环境，分别改名字，对应三个节点。
依照启动节点的参数，可以配置默认服务的前置 URL 分别为：
```
Onewr：https://127.0.0.1:8002
User: https://127.0.0.1:8003
```
这样，只要切换不同的环境，你就能操作节点。

我推荐你先从 Node 系的接口开始测试，然后可以试试自己建组（Group）并生成种子，让另一个节点加入，最后都两个节点都在组里发发消息。

# 写在最后

其实 Quorum 的应用开发思路很清晰，只需要在你的程序运行时同时启动 Quorum，指定好交互端口，在自己的应用内封装好 HTTP 请求，就可像数据库一样读写（分享）数据。

如果你找到了这篇文的错误，欢迎你指出；如果你有任何关于 Quorum 的事情想和我讨论，我也同样欢迎。

我的 Mixin ID：37206436
我的邮箱： tymon42@outlook.com