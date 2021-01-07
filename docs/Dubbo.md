# Dubbo

# CS-Dubbo

## 单体架构

![](D:/Code/Typora/docs/Microservice.assets/be01386bf19f71fe8467bf20132bcc0c.png)

![](D:/Code/Typora/media/pictures/Dubbo.assets/d77c37dd3a3a108509e903211a14ff94-1570887088291.png)

## 优缺点

![](../media/pictures/Dubbo.assets/391bfa438a9991af7f55b236c2a73e12.png)

修改后 测试麻烦

迭代困难

修改工具类，其他的模块都受到影响

某个模块扩展扩容起来麻烦

部署和回滚不方便

## 微服务架构引入

## 概念

微服务是指开发一个单个小型的但有业务功能的服务，每个服务都有自己的处理和轻量通讯机制，可以部署在单个或多个服务器上。微服务也指一种种松耦合的、有一定的有界上下文的面向服务架构。也就是说，如果每个服务都要同时修改，那么它们就不是微服务，因为它们紧耦合在一起；如果你需要掌握一个服务太多的上下文场景使用条件，那么它就是一个有上下文边界的服务。

## 架构图

![](../media/pictures/Dubbo.assets/a5ed18885a7240334ad1b8cf16d6f785.png)

![](../media/pictures/Dubbo.assets/4dc25fa09547d7d41812a63e195cfd2b.png)

## 微服务架构设计原则

拆分足够小

服务之间轻量级通信

## 微服务的优点

相对于单体架构，它的主要特点是**组件化、松耦合、自治、去中心化**，体现在以下几个方面：

一组小的服务
服务粒度要小，而每个服务是针对一个单一职责的业务能力的封装，专注做好一件事情。

独立部署运行和扩展

每个服务能够独立被部署并运行在一个进程内。这种运行和部署方式能够赋予系统灵活的代码组织方式和发布节奏，使得快速交付和应对变化成为可能。

独立开发和演化

技术选型灵活，不受遗留系统技术约束。合适的业务问题选择合适的技术可以独立演化。服务与服务之间采取与语言无关的API进行集成。相对单体架构，微服务架构是更面向业务创新的一种架构模式。

独立团队和自治

团队对服务的整个生命周期负责，工作在独立的上下文中，自己决策自己治理，而不需要统一的指挥中心。团队和团队之间通过松散的社区部落进行衔接。

## 微服务的缺点

服务拆分微服务架构可能带来过多的操作。

分布式系统可能复杂难以管理。

因为分布部署跟踪问题难。

分布式事务比较难处理

当服务数量增加，管理复杂性增加。

等

## 微服务拆分思路

### 横向拆分

根据业务来拆分

![](../media/pictures/Dubbo.assets/22e8dba61d1030921e6aed34169e2cdd.png)

### 纵向拆分 

根据层次来拆分

![](../media/pictures/Dubbo.assets/fb0154c9a3d57c61127dae4a3413f9db.png)

## 微服务的选择

下面两个就想当于自配电脑(Dubbo),和品牌电脑的关系(Springcloud)!

### Dubbo （RPC）

#### Dubbo(这个是传输层协议 速度快)

Dubbo是阿里集团开源的一个极为出名的RPC框架，在很多互联网公司和企业应用中广泛使用。协议和序列化框架都可以插拔是及其鲜明的特色。同样的远程接口是基于Java Interface，并且依托于spring框架方便开发。可以方便的打包成单一文件，独立进程运行，和现在的微服务概念一致。所以目前Dubbo是一种广泛使用的微服务架构框架。

#### RPC 

RPC= Remote Process Call 跨进程调用

RPC的本质是提供了一种轻量无感知的跨进程通信的方式，在分布式机器上调用其他方法与本地调用无异（远程调用的过程是透明的，你并不知道这个调用的方法是部署在哪里，通过PRC能够解耦服务）。RPC是根据语言的API来定义的，而不是基于网络的应用来定义的，调用更方便，协议私密更安全、内容更小效率更高。

![](../media/pictures/Dubbo.assets/ac8ff59370709f3755eec59630f93b2e.png)

客户端（Client），服务的调用方。

服务端（Server），真正的服务提供者。

客户端存根，存放服务端的地址消息，再将客户端的请求参数打包成网络消息，然后通过网络远程发送给服务方。

服务端存根，接收客户端发送过来的消息，将消息解包，并调用本地的方法。

基于TCP/IP协议。速度快。

![](../media/pictures/Dubbo.assets/625f185c66747f68f35690b1f7757cc0.png)

### Springcloud （HTTP）

#### Springcloud （HTTP/REST）(这个是应用层协议 速度慢 但是全 想当于品牌电脑)

Spring Cloud来源于Spring，利用Spring Boot进行快捷开发。 Spring
Cloud基本上都是使用了现有的开源框架进行的集成，学习的难度和部署的门槛就比较低，对于中小型企业来说，更易于使用和落地。Spring
Cloud
核心组件Eureka是Netflix开源的一款提供服务注册和发现的产品，它提供了完整的Service
Registry和Service Discovery实现。也是Spring Cloud体系中最重要最核心的组件之一。

#### http

**应用层协议**，简单。

http接口是在接口不多、系统与系统交互较少的情况下，解决信息孤岛初期常使用的一种通信手段；优点就是简单、直接、开发方便。利用现成的http协议
进行传输。

使用Http协议的微服务，通常返回json数据，然后把json转换为对象。

### 小结

RPC服务和HTTP服务还是存在很多的不同点的，一般来说，RPC服务主要是针对大型企业的，而HTTP服务主要是针对小企业的，因为RPC效率更高，而HTTP服务开发迭代会更快。**总之，选用什么样的框架不是按照市场上流行什么而决定的，而是要对整个项目进行完整地评估。**

## 微服务的基本概念

### 服务提供者Provider

提供服务的具体实现。

### 服务调用者Consumer

通过一些框架来调用服务提供者提供的服务

注意：同一个微服务，既可以是provider，也可以是consumer。

## 拓展 阿里架构演变之路

https://segmentfault.com/a/1190000018626163  这是作者原来文章的链接!

下面是从源出处复制过来的!

### 1. 概述

本文以淘宝作为例子，介绍从一百个并发到千万级并发情况下服务端的架构的演进过程，同时列举出每个演进阶段会遇到的相关技术，让大家对架构的演进有一个整体的认知，文章最后汇总了一些架构设计的原则。

### 2. 基本概念

在介绍架构之前，为了避免部分读者对架构设计中的一些概念不了解，下面对几个最基础的概念进行介绍：

- **分布式**
  系统中的多个模块在不同服务器上部署，即可称为分布式系统，如Tomcat和数据库分别部署在不同的服务器上，或两个相同功能的Tomcat分别部署在不同服务器上
- **高可用**
  系统中部分节点失效时，其他节点能够接替它继续提供服务，则可认为系统具有高可用性
- **集群**
  一个特定领域的软件部署在多台服务器上并作为一个整体提供一类服务，这个整体称为集群。如Zookeeper中的Master和Slave分别部署在多台服务器上，共同组成一个整体提供集中配置服务。在常见的集群中，客户端往往能够连接任意一个节点获得服务，并且当集群中一个节点掉线时，其他节点往往能够自动的接替它继续提供服务，这时候说明集群具有高可用性
- **负载均衡**
  请求发送到系统时，通过某些方式把请求均匀分发到多个节点上，使系统中每个节点能够均匀的处理请求负载，则可认为系统是负载均衡的
- **正向代理和反向代理**
  系统内部要访问外部网络时，统一通过一个代理服务器把请求转发出去，在外部网络看来就是代理服务器发起的访问，此时代理服务器实现的是正向代理；当外部请求进入系统时，代理服务器把该请求转发到系统中的某台服务器上，对外部请求来说，与之交互的只有代理服务器，此时代理服务器实现的是反向代理。简单来说，正向代理是代理服务器代替系统内部来访问外部网络的过程，反向代理是外部请求访问系统时通过代理服务器转发到内部服务器的过程。

### 3. 架构演进

#### 3.1 单机架构

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/2664959638-5ca02e1d2e99b_articlex.png)

以淘宝作为例子。在网站最初时，应用数量与用户数都较少，可以把Tomcat和数据库部署在同一台服务器上。浏览器往www.taobao.com发起请求时，首先经过DNS服务器（域名系统）把域名转换为实际IP地址10.102.4.1，浏览器转而访问该IP对应的Tomcat。

> **随着用户数的增长，Tomcat和数据库之间竞争资源，单机性能不足以支撑业务**

#### 3.2 第一次演进：Tomcat与数据库分开部署

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/2571350918-5ca02dfbdc242_articlex.png)

Tomcat和数据库分别独占服务器资源，显著提高两者各自性能。

> **随着用户数的增长，并发读写数据库成为瓶颈**

#### 3.3 第二次演进：引入本地缓存和分布式缓存

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/1088865837-5ca031313f044_articlex.png)

在Tomcat同服务器上或同JVM中增加本地缓存，并在外部增加分布式缓存，缓存热门商品信息或热门商品的html页面等。通过缓存能把绝大多数请求在读写数据库前拦截掉，大大降低数据库压力。其中涉及的技术包括：使用memcached作为本地缓存，使用Redis作为分布式缓存，还会涉及缓存一致性、缓存穿透/击穿、缓存雪崩、热点数据集中失效等问题。

> **缓存抗住了大部分的访问请求，随着用户数的增长，并发压力主要落在单机的Tomcat上，响应逐渐变慢**

#### 3.4 第三次演进：引入反向代理实现负载均衡

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/2872647211-5c95fef4928ad_articlex.png)

在多台服务器上分别部署Tomcat，使用反向代理软件（Nginx）把请求均匀分发到每个Tomcat中。此处假设Tomcat最多支持100个并发，Nginx最多支持50000个并发，那么理论上Nginx把请求分发到500个Tomcat上，就能抗住50000个并发。其中涉及的技术包括：Nginx、HAProxy，两者都是工作在网络第七层的反向代理软件，主要支持http协议，还会涉及session共享、文件上传下载的问题。

> **反向代理使应用服务器可支持的并发量大大增加，但并发量的增长也意味着更多请求穿透到数据库，单机的数据库最终成为瓶颈**

#### 3.5 第四次演进：数据库读写分离

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/1589885053-5c96032e3c356_articlex.png)

把数据库划分为读库和写库，读库可以有多个，通过同步机制把写库的数据同步到读库，对于需要查询最新写入数据场景，可通过在缓存中多写一份，通过缓存获得最新数据。其中涉及的技术包括：Mycat，它是数据库中间件，可通过它来组织数据库的分离读写和分库分表，客户端通过它来访问下层数据库，还会涉及数据同步，数据一致性的问题。

> **业务逐渐变多，不同业务之间的访问量差距较大，不同业务直接竞争数据库，相互影响性能**

#### 3.6 第五次演进：数据库按业务分库

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/250737400-5c9653d44e54e_articlex.png)

把不同业务的数据保存到不同的数据库中，使业务之间的资源竞争降低，对于访问量大的业务，可以部署更多的服务器来支撑。这样同时导致跨业务的表无法直接做关联分析，需要通过其他途径来解决，但这不是本文讨论的重点，有兴趣的可以自行搜索解决方案。

> **随着用户数的增长，单机的写库会逐渐会达到性能瓶颈**

#### 3.7 第六次演进：把大表拆分为小表

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/111902257-5c960f793734f_articlex.png)

比如针对评论数据，可按照商品ID进行hash，路由到对应的表中存储；针对支付记录，可按照小时创建表，每个小时表继续拆分为小表，使用用户ID或记录编号来路由数据。只要实时操作的表数据量足够小，请求能够足够均匀的分发到多台服务器上的小表，那数据库就能通过水平扩展的方式来提高性能。其中前面提到的Mycat也支持在大表拆分为小表情况下的访问控制。

这种做法显著的增加了数据库运维的难度，对DBA的要求较高。数据库设计到这种结构时，已经可以称为分布式数据库，但是这只是一个逻辑的数据库整体，数据库里不同的组成部分是由不同的组件单独来实现的，如分库分表的管理和请求分发，由Mycat实现，SQL的解析由单机的数据库实现，读写分离可能由网关和消息队列来实现，查询结果的汇总可能由数据库接口层来实现等等，这种架构其实是MPP（大规模并行处理）架构的一类实现。

目前开源和商用都已经有不少MPP数据库，开源中比较流行的有Greenplum、TiDB、Postgresql XC、HAWQ等，商用的如南大通用的GBase、睿帆科技的雪球DB、华为的LibrA等等，不同的MPP数据库的侧重点也不一样，如TiDB更侧重于分布式OLTP场景，Greenplum更侧重于分布式OLAP场景，这些MPP数据库基本都提供了类似Postgresql、Oracle、MySQL那样的SQL标准支持能力，能把一个查询解析为分布式的执行计划分发到每台机器上并行执行，最终由数据库本身汇总数据进行返回，也提供了诸如权限管理、分库分表、事务、数据副本等能力，并且大多能够支持100个节点以上的集群，大大降低了数据库运维的成本，并且使数据库也能够实现水平扩展。

> **数据库和Tomcat都能够水平扩展，可支撑的并发大幅提高，随着用户数的增长，最终单机的Nginx会成为瓶颈**

#### 3.8 第七次演进：使用LVS或F5来使多个Nginx负载均衡

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/1157555056-5c965af7a8de0_articlex.png)

由于瓶颈在Nginx，因此无法通过两层的Nginx来实现多个Nginx的负载均衡。图中的LVS和F5是工作在网络第四层的负载均衡解决方案，其中LVS是软件，运行在操作系统内核态，可对TCP请求或更高层级的网络协议进行转发，因此支持的协议更丰富，并且性能也远高于Nginx，可假设单机的LVS可支持几十万个并发的请求转发；F5是一种负载均衡硬件，与LVS提供的能力类似，性能比LVS更高，但价格昂贵。由于LVS是单机版的软件，若LVS所在服务器宕机则会导致整个后端系统都无法访问，因此需要有备用节点。可使用keepalived软件模拟出虚拟IP，然后把虚拟IP绑定到多台LVS服务器上，浏览器访问虚拟IP时，会被路由器重定向到真实的LVS服务器，当主LVS服务器宕机时，keepalived软件会自动更新路由器中的路由表，把虚拟IP重定向到另外一台正常的LVS服务器，从而达到LVS服务器高可用的效果。

此处需要注意的是，上图中从Nginx层到Tomcat层这样画并不代表全部Nginx都转发请求到全部的Tomcat，在实际使用时，可能会是几个Nginx下面接一部分的Tomcat，这些Nginx之间通过keepalived实现高可用，其他的Nginx接另外的Tomcat，这样可接入的Tomcat数量就能成倍的增加。

> **由于LVS也是单机的，随着并发数增长到几十万时，LVS服务器最终会达到瓶颈，此时用户数达到千万甚至上亿级别，用户分布在不同的地区，与服务器机房距离不同，导致了访问的延迟会明显不同**

#### 3.9 第八次演进：通过DNS轮询实现机房间的负载均衡

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/1896228394-5c9662ac87756_articlex.png)

在DNS服务器中可配置一个域名对应多个IP地址，每个IP地址对应到不同的机房里的虚拟IP。当用户访问www.taobao.com时，DNS服务器会使用轮询策略或其他策略，来选择某个IP供用户访问。此方式能实现机房间的负载均衡，至此，系统可做到机房级别的水平扩展，千万级到亿级的并发量都可通过增加机房来解决，系统入口处的请求并发量不再是问题。

> **随着数据的丰富程度和业务的发展，检索、分析等需求越来越丰富，单单依靠数据库无法解决如此丰富的需求**

#### 3.10 第九次演进：引入NoSQL数据库和搜索引擎等技术

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/1190021994-5ca03c930e572_articlex.png)

当数据库中的数据多到一定规模时，数据库就不适用于复杂的查询了，往往只能满足普通查询的场景。对于统计报表场景，在数据量大时不一定能跑出结果，而且在跑复杂查询时会导致其他查询变慢，对于全文检索、可变数据结构等场景，数据库天生不适用。因此需要针对特定的场景，引入合适的解决方案。如对于海量文件存储，可通过分布式文件系统HDFS解决，对于key value类型的数据，可通过HBase和Redis等方案解决，对于全文检索场景，可通过搜索引擎如ElasticSearch解决，对于多维分析场景，可通过Kylin或Druid等方案解决。

当然，引入更多组件同时会提高系统的复杂度，不同的组件保存的数据需要同步，需要考虑一致性的问题，需要有更多的运维手段来管理这些组件等。

> **引入更多组件解决了丰富的需求，业务维度能够极大扩充，随之而来的是一个应用中包含了太多的业务代码，业务的升级迭代变得困难**

#### 3.11 第十次演进：大应用拆分为小应用

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/1992263855-5ca04d46dd717_articlex.png)

按照业务板块来划分应用代码，使单个应用的职责更清晰，相互之间可以做到独立升级迭代。这时候应用之间可能会涉及到一些公共配置，可以通过分布式配置中心Zookeeper来解决。

> **不同应用之间存在共用的模块，由应用单独管理会导致相同代码存在多份，导致公共功能升级时全部应用代码都要跟着升级**

3.12 第十一次演进：复用的功能抽离成微服务

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/651851067-5ca04fe08f7ee_articlex.png)

如用户管理、订单、支付、鉴权等功能在多个应用中都存在，那么可以把这些功能的代码单独抽取出来形成一个单独的服务来管理，这样的服务就是所谓的微服务，应用和服务之间通过HTTP、TCP或RPC请求等多种方式来访问公共服务，每个单独的服务都可以由单独的团队来管理。此外，可以通过Dubbo、SpringCloud等框架实现服务治理、限流、熔断、降级等功能，提高服务的稳定性和可用性。

> **不同服务的接口访问方式不同，应用代码需要适配多种访问方式才能使用服务，此外，应用访问服务，服务之间也可能相互访问，调用链将会变得非常复杂，逻辑变得混乱**

#### 3.13 第十二次演进：引入企业服务总线ESB屏蔽服务接口的访问差异

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/1162448692-5ca052a998911_articlex.png)

通过ESB统一进行访问协议转换，应用统一通过ESB来访问后端服务，服务与服务之间也通过ESB来相互调用，以此降低系统的耦合程度。这种单个应用拆分为多个应用，公共服务单独抽取出来来管理，并使用企业消息总线来解除服务之间耦合问题的架构，就是所谓的SOA（面向服务）架构，这种架构与微服务架构容易混淆，因为表现形式十分相似。个人理解，微服务架构更多是指把系统里的公共服务抽取出来单独运维管理的思想，而SOA架构则是指一种拆分服务并使服务接口访问变得统一的架构思想，SOA架构中包含了微服务的思想。

> **业务不断发展，应用和服务都会不断变多，应用和服务的部署变得复杂，同一台服务器上部署多个服务还要解决运行环境冲突的问题，此外，对于如大促这类需要动态扩缩容的场景，需要水平扩展服务的性能，就需要在新增的服务上准备运行环境，部署服务等，运维将变得十分困难**

#### 3.14 第十三次演进：引入容器化技术实现运行环境隔离与动态服务管理

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/2760745238-5ca055e4b20a9_articlex.png)

目前最流行的容器化技术是Docker，最流行的容器管理服务是Kubernetes(K8S)，应用/服务可以打包为Docker镜像，通过K8S来动态分发和部署镜像。Docker镜像可理解为一个能运行你的应用/服务的最小的操作系统，里面放着应用/服务的运行代码，运行环境根据实际的需要设置好。把整个“操作系统”打包为一个镜像后，就可以分发到需要部署相关服务的机器上，直接启动Docker镜像就可以把服务起起来，使服务的部署和运维变得简单。

在大促的之前，可以在现有的机器集群上划分出服务器来启动Docker镜像，增强服务的性能，大促过后就可以关闭镜像，对机器上的其他服务不造成影响（在3.14节之前，服务运行在新增机器上需要修改系统配置来适配服务，这会导致机器上其他服务需要的运行环境被破坏）。

> **使用容器化技术后服务动态扩缩容问题得以解决，但是机器还是需要公司自身来管理，在非大促的时候，还是需要闲置着大量的机器资源来应对大促，机器自身成本和运维成本都极高，资源利用率低**

#### 3.15 第十四次演进：以云平台承载系统

![clipboard.png](D:/Code/Typora/media/pictures/Dubbo.assets/1409345676-5ca05cae06402_articlex.png)

系统可部署到公有云上，利用公有云的海量机器资源，解决动态硬件资源的问题，在大促的时间段里，在云平台中临时申请更多的资源，结合Docker和K8S来快速部署服务，在大促结束后释放资源，真正做到按需付费，资源利用率大大提高，同时大大降低了运维成本。

所谓的云平台，就是把海量机器资源，通过统一的资源管理，抽象为一个资源整体，在之上可按需动态申请硬件资源（如CPU、内存、网络等），并且之上提供通用的操作系统，提供常用的技术组件（如Hadoop技术栈，MPP数据库等）供用户使用，甚至提供开发好的应用，用户不需要关系应用内部使用了什么技术，就能够解决需求（如音视频转码服务、邮件服务、个人博客等）。在云平台中会涉及如下几个概念：

- **IaaS：**基础设施即服务。对应于上面所说的机器资源统一为资源整体，可动态申请硬件资源的层面；
- **PaaS：**平台即服务。对应于上面所说的提供常用的技术组件方便系统的开发和维护；
- **SaaS：**软件即服务。对应于上面所说的提供开发好的应用或服务，按功能或性能要求付费。

> **至此，以上所提到的从高并发访问问题，到服务的架构和系统实施的层面都有了各自的解决方案，但同时也应该意识到，在上面的介绍中，其实是有意忽略了诸如跨机房数据同步、分布式事务实现等等的实际问题，这些问题以后有机会再拿出来单独讨论**

### 4. 架构设计总结

- **架构的调整是否必须按照上述演变路径进行？**
  不是的，以上所说的架构演变顺序只是针对某个侧面进行单独的改进，在实际场景中，可能同一时间会有几个问题需要解决，或者可能先达到瓶颈的是另外的方面，这时候就应该按照实际问题实际解决。如在政府类的并发量可能不大，但业务可能很丰富的场景，高并发就不是重点解决的问题，此时优先需要的可能会是丰富需求的解决方案。
- **对于将要实施的系统，架构应该设计到什么程度？**
  对于单次实施并且性能指标明确的系统，架构设计到能够支持系统的性能指标要求就足够了，但要留有扩展架构的接口以便不备之需。对于不断发展的系统，如电商平台，应设计到能满足下一阶段用户量和性能指标要求的程度，并根据业务的增长不断的迭代升级架构，以支持更高的并发和更丰富的业务。
- **服务端架构和大数据架构有什么区别？**
  所谓的“大数据”其实是海量数据采集清洗转换、数据存储、数据分析、数据服务等场景解决方案的一个统称，在每一个场景都包含了多种可选的技术，如数据采集有Flume、Sqoop、Kettle等，数据存储有分布式文件系统HDFS、FastDFS，NoSQL数据库HBase、MongoDB等，数据分析有Spark技术栈、机器学习算法等。总的来说大数据架构就是根据业务的需求，整合各种大数据组件组合而成的架构，一般会提供分布式存储、分布式计算、多维分析、数据仓库、机器学习算法等能力。而服务端架构更多指的是应用组织层面的架构，底层能力往往是由大数据架构来提供。
- **有没有一些架构设计的原则？**
  - N+1设计。系统中的每个组件都应做到没有单点故障；
  - 回滚设计。确保系统可以向前兼容，在系统升级时应能有办法回滚版本；
  - 禁用设计。应该提供控制具体功能是否可用的配置，在系统出现故障时能够快速下线功能；
  - 监控设计。在设计阶段就要考虑监控的手段；
  - 多活数据中心设计。若系统需要极高的高可用，应考虑在多地实施数据中心进行多活，至少在一个机房断电的情况下系统依然可用；
  - 采用成熟的技术。刚开发的或开源的技术往往存在很多隐藏的bug，出了问题没有商业支持可能会是一个灾难；
  - 资源隔离设计。应避免单一业务占用全部资源；
  - 架构应能水平扩展。系统只有做到能水平扩展，才能有效避免瓶颈问题；
  - 非核心则购买。非核心功能若需要占用大量的研发资源才能解决，则考虑购买成熟的产品；
  - 使用商用硬件。商用硬件能有效降低硬件故障的机率；
  - 快速迭代。系统应该快速开发小功能模块，尽快上线进行验证，早日发现问题大大降低系统交付的风险；
  - 无状态设计。服务接口应该做成无状态的，当前接口的访问不依赖于接口上次访问的状态。

## Dubbo引入

## Dubbo介绍

<http://dubbo.apache.org/en-us/>

## Spring和Dubbo的结合

### 入门案例

参考文档：<https://dubbo.gitbooks.io/dubbo-user-book/content/quick-start.html>

#### 导包

见资料。

#### 服务提供者 

##### 代码

首先我们在服务端定义一个接口

![](../media/pictures/Dubbo.assets/1ddc209e6ef6a524024997bc53ca3cf1.png)

然后我在服务端提供这个接口的实现

![](../media/pictures/Dubbo.assets/6a7c6b3b2755feb69455529e8497395b.png)

##### 配置

![](../media/pictures/Dubbo.assets/fa1e3e4cc8f504c746e87a1e01ce7286.png)

#### 服务器使用者 

##### 代码

![](../media/pictures/Dubbo.assets/4f4062b2cf24f0b5389881f84d0ad11e.png)

远程调用代码

![](../media/pictures/Dubbo.assets/2ce43942af3f1ff23b44b75314bfd3af.png)

##### 配置

![](../media/pictures/Dubbo.assets/32a3c0f74c325ec723440dcc369cd82c.png)

#### 测试结果

![](../media/pictures/Dubbo.assets/26954a843fb9f74e9cde7c16c19902e4.png)



**这里需要注意的是,这里服务的提供者和服务的消费者名字要一样,不光是接口和类的名字一样,而且包名也要一样!**

![1570800056119](D:/Code/Typora/media/pictures/Dubbo.assets/1570800056119.png)

这里的两个接口必须要一样!

## 架构

![1570802882355](D:/Code/Typora/media/pictures/Dubbo.assets/1570802882355.png)

### 第一种方式直连!相当于没有上面注册!

### 第二种方式用注册中心中的zookepper!

zookepper使用,首先减压!

然后进去目录中,将文件名字修改:

![1570803035936](D:/Code/Typora/media/pictures/Dubbo.assets/1570803035936.png)

因为启动以后会默认找zoo.cfg这个文件!



然后需要启动这的zookeeper,这里需要注意的是,路径不能有中文,目录如果放的太深,或者路径中有其他奇怪字符,这个是运行不了的,会一直报错,提示找不到主类!

![1570804540341](D:/Code/Typora/media/pictures/Dubbo.assets/1570804540341.png)

![1570804910045](D:/Code/Typora/media/pictures/Dubbo.assets/1570804910045.png)

这样就启动成功啦!

这其中遇到一个问题,问题详细信息看error18!

zookeeper会受电脑广播和其他东西的影响!

而且在wins环境下,会运行不稳定!有时候需要耐心一定!

![1570870852064](D:/Code/Typora/media/pictures/Dubbo.assets/1570870852064.png)

出现这个,就意味着成功啦!



### 入门案例分析

## SpringBoot 和 Dubbo的结合

参考文档<https://github.com/alibaba/dubbo-spring-boot-starter>



首先需要导一个包!springboot对dubbo的支持包!上面是github的地址!

### 导包

```xml
<dependency>
    <groupId>com.alibaba.spring.boot</groupId>
    <artifactId>dubbo-spring-boot-starter</artifactId>
    <version>2.0.0</version>
</dependency>
```

Springboot约定大于配置,官方文档中没有配置端口,其实是默认配置了端口,只要不修改端口,默认就是

```xml
spring.application.name=dubbo-spring-boot-starter
spring.dubbo.server=true
spring.dubbo.registry=N/A
```





### 提供者

![](../media/pictures/Dubbo.assets/f0e79697c6c1d5415d3c878f84d3b34c.png)

**注意:这里的Service是dubbo中的!要注意!**

使用之前要导包!

![](../media/pictures/Dubbo.assets/04c8cb6e6104504c76086b191c682e19.png)

配置：

```java
spring.application.name=dubbo-spring-boot-starter
spring.dubbo.protocol.name=dubbo
spring.dubbo.protocol.port=20880
spring.dubbo.server=true
spring.dubbo.registry=N/A
```



### 使用者

也要实现一模一样的接口！

![](../media/pictures/Dubbo.assets/ffd1647ad2a27e2a3cbd4bd9fd668ce0.png)

![](../media/pictures/Dubbo.assets/1e3adc3901c569b59d50e303575ef8a3.png)

然后在main方法里测试！

**注意**:这里要开启功能,需要上面的注解

```java
@EnableDubboConfiguraion
```

![](../media/pictures/Dubbo.assets/8d9f3596a9273968defb166629b682bb.png)

### 测试

先启动服务提供者：

![](../media/pictures/Dubbo.assets/7131d4fb96a772e2ce12dc39c84e0718.png)

在启动使用者：

这行log出现在下面的空行位置

![](../media/pictures/Dubbo.assets/167a3119d6eb87a271d3708cb48dcc61.png)

![](../media/pictures/Dubbo.assets/c7e6d9f38b4ef5eb42001a8ef20f3560.png)



在老师上课的dome中,老师使用了一个公共包common,公共包里面的pom.xml配置,要写成

```xml
<packaging>jar</packaging>
```

公共包里面建放了DemoService接口,那么下面两个中就没有必要放这个接口啦!

但是要导入上面的common包!

```xml
<!--要引入common包里面的包,这里需要引入common包-->
<dependency>
    <groupId>com.cskaoyan</groupId>
    <artifactId>common</artifactId>
    <version>0.0.1-SNAPSHOT</version>
</dependency>
```

这样,下面两个包就可以使用common里面的包啦!

这种导入一个公共包的做法,不容易犯错!



公共类中导入一个依赖,然后下面两个包中都是可以使用的!

![1570882252588](D:/Code/Typora/media/pictures/Dubbo.assets/1570882252588.png)

```xml
<!--这个依赖狭下面两个都需要!-->
<dependency>
    <groupId>com.alibaba.spring.boot</groupId>
    <artifactId>dubbo-spring-boot-starter</artifactId>
    <version>2.0.0</version>
</dependency>
```

这里可以看到下面两个包中已经包含了上面包中的,已经包含了公共包中的依赖!

上面的是直连

如果想让项目变成需要注册的,还需要导入zookeeper

```xml
<!--这个是导入zookeeper的包-->
<dependency>
	<groupId>com.101tec</groupId>
	<artifactId>zkclient</artifactId>
	<version>0.10</version>
</dependency>
```





## 直连提供者

### 介绍

我们刚才使用的微服务的用法，实际上是一种最简单的点对点调用方式。这种方式通常用于测试环境。

在开发及测试环境下，经常需要绕过注册中心，只测试指定服务提供者，这时候可能需要点对点直连，点对点直联方式，将以服务接口为单位，忽略注册中心的提供者列表，A
接口配置点对点，不影响 B 接口从注册中心获取列表。

![](../media/pictures/Dubbo.assets/15adcb224fcef4191f9106fd36f62105.png)

**注意** 为了避免复杂化线上环境，不要在线上使用这个功能，只应在测试阶段使用。

### 弊端

不利于分布式的扩展

## 服务注册和服务发现

### 架构图

这里是长连接!长连接最主要的特点是建立心跳连接!过一会会发射一些数据!

![](../media/pictures/Dubbo.assets/acc8b5168c63f753c642f845b11de339.png)

名词解释：

![](../media/pictures/Dubbo.assets/116873b8f0e64756d54775a4b40c1d82.png)

### ZooKeeper

是一个中间件，负责为分布式系统提供协调服务。服务注册和服务发现。

<https://www.apache.org/dyn/closer.cgi/zookeeper/>

下载路径

下载解压之后

修改一个文件名

zoo_sample.cfg修改为

![](../media/pictures/Dubbo.assets/ec83dfc5f99bf5219216aa4f80d1e1c4.png)

启动：

![](../media/pictures/Dubbo.assets/730080cbd8e58d9bde067d8b0903a607.png)

![](../media/pictures/Dubbo.assets/5bb55b0b35a442e2882accb51ad945dd.png)

## Spring +dubbo项目 如何整合zookeeper

### 导入依赖

\<dependency\>  
\<groupId\>com.101tec\</groupId\>  
\<artifactId\>zkclient\</artifactId\>  
\<version\>0.9\</version\>  
\</dependency\>  
\<dependency\>  
\<groupId\>org.apache.zookeeper\</groupId\>  
\<artifactId\>zookeeper\</artifactId\>  
\<version\>3.4.9\</version\>  
\<type\>pom\</type\>  
\</dependency\>

### 修改服务端

![](../media/pictures/Dubbo.assets/5af9e605d5751eec4aa074727bdb3d79.png)

启动：

没有报错，

Zookeeper那边的命令行会出现一些log

![](../media/pictures/Dubbo.assets/8641ddc536193a03a16a54f50d9e2405.png)

### 修改客户端

![](../media/pictures/Dubbo.assets/a2e28d69a76f38bb32409e87c3202c2f.png)

### 测试

![](../media/pictures/Dubbo.assets/0cb2e6a8664c7ac126ba073055ea1d98.png)

![](../media/pictures/Dubbo.assets/4af8d78e7df99c245100ea374eb7b2e3.png)

## Springboot 和 dubbo项目整合zookeeper

### 服务端

增加了依赖

![](../media/pictures/Dubbo.assets/bb743b6f6d742f4917a9d8d8c19cdc70.png)

修改地址：

spring.application.name=dubbo-spring-boot-starter  
spring.dubbo.server=true  
spring.dubbo.registry=zookeeper://localhost:2181

启动

### 使用端

\<dependency\>  
\<groupId\>com.101tec\</groupId\>  
\<artifactId\>zkclient\</artifactId\>  
\<version\>0.10\</version\>  
\</dependency\>

配置文件：

增加如下：

spring.dubbo.registry=zookeeper://localhost:2181

代码里：

![](../media/pictures/Dubbo.assets/125b23e796ba24d0e683d687662d5e94.png)

### 测试

![](../media/pictures/Dubbo.assets/11c12babf9fd43b68454fbb9403ec29e.png)

这里有一个面试题:

加入zookeeper挂掉以后,Dubbo还能不能正常调用??

可正常调用!因为本地有缓存!

![1570885788370](D:/Code/Typora/media/pictures/Dubbo.assets/1570885788370.png)









## Dubbo负载均衡

## 概念

LoadBalance
中文意思为负载均衡，它的职责是将网络请求，或者其他形式的负载“均摊”到不同的机器上。避免集群中部分服务器压力过大，而另一些服务器比较空闲的情况。通过负载均衡，可以让每台服务器获取到适合自己处理能力的负载。在为高负载服务器分流的同时，还可以避免资源浪费，一举两得。

## 负载均衡策略

![](../media/pictures/Dubbo.assets/dd06bd3a7e584111a4c8a408e78ddba4.png)

### Random

随机加权

RandomLoadBalance
是加权随机算法的具体实现，它的算法思想很简单。假设我们有一组服务器 servers = [A,
B, C]，他们对应的权重为 weights = [5, 3,
2]，权重总和为10。现在把这些权重值平铺在一维坐标值上，[0, 5) 区间属于服务器
A，[5, 8) 区间属于服务器 B，[8, 10) 区间属于服务器
C。接下来通过随机数生成器生成一个范围在 [0, 10)
之间的随机数，然后计算这个随机数会落到哪个区间上。权重越大的机器，在坐标轴上对应的区间范围就越大，因此随机数生成器生成的数字就会有更大的概率落到此区间内。

### RoundRobin

我们有三台服务器 A、B、C。我们将第一个请求分配给服务器 A，第二个请求分配给服务器
B，第三个请求分配给服务器 C，第四个请求再次分配给服务器 A。这个过程就叫做

轮询。轮询是一种无状态负载均衡算法，实现简单，适用于每台服务器性能相近的场景下。

通常我们可以给轮询的机器设置不同的权重，经过加权后，每台服务器能够得到的请求数比例，接近或等于他们的权重比。比如服务器
A、B、C 权重比为 5:2:1。那么在8次请求中，服务器 A 将收到其中的5次请求，服务器 B
会收到其中的2次请求，服务器 C 则收到其中的1次请求。

### LeastActive

LeastActiveLoadBalance
翻译过来是最小活跃数负载均衡。活跃调用数越小，表明该服务提供者效率越高，单位时间内可处理更多的请求。此时应优先将请求分配给该服务提供者。在具体实现中，每个服务提供者对应一个活跃数
active。初始情况下，所有服务提供者活跃数均为0。每收到一个请求，活跃数加1，完成请求后则将活跃数减1。在服务运行一段时间后，性能好的服务提供者处理请求的速度更快，因此活跃数下降的也越快，此时这样的服务提供者能够优先获取到新的服务请求、这就是最小活跃数负载均衡算法的基本思想。

### ConsistentHash

![](../media/pictures/Dubbo.assets/ea1e741ce818c1e439ab913c4c84e620.png)

## 配置

### Random

默认配置

### RoundRobin

#### 客户端配置

客户端服务级别

![](../media/pictures/Dubbo.assets/a4a494abc4050b987ef6ff9c37134c69.png)

该服务的所有方法都使用roundrobin负载均衡。

客户端方法级别

![](../media/pictures/Dubbo.assets/118ad755da8147dcf95f19aa62dd18ff.png)

如

![](../media/pictures/Dubbo.assets/127a68ffe191362a99e5221b6d4e0c97.png)

只有该服务的hello方法使用roundrobin负载均衡。

#### 服务端配置

服务端服务级别

![](../media/pictures/Dubbo.assets/57a0844a42642946790e94fe6b33e488.png)

该服务的所有方法都使用roundrobin负载均衡。

服务端方法级别

![](../media/pictures/Dubbo.assets/27e77f44be552ada54ffea71bdfd543e.png)

只有该服务的该方法使用roundrobin负载均衡。

### LeastActive

### 补充说明

和Dubbo其他的配置类似，多个配置是有覆盖关系的：

1. 方法级优先，接口级次之，全局配置再次之。
2. 如果级别一样，则消费方优先，提供方次之。

所以，上面4种配置的优先级是:

1. 客户端方法级别配置。
2. 客户端接口级别配置。
3. 服务端方法级别配置。
4. 服务端接口级别配置。

## 补充说明

### 启动检查

后面的check = false 就是启动检查!

```java
@Component
public class ThirdService {

    //这句话相当于 url = "dubbo://localhost:20880"
    @Reference(interfaceClass = DemoService.class,check = false)
    DemoService demoService;

    public String sendMsg(String msg){
        return demoService.sendMsg(msg);
    }
}
```

启动检查加了以后,我们不关心现在有没有provider,他会去检查!

### Dubbo的特性

# CS-Guns



## 介绍

<https://gitee.com/naan1993/guns/>

- 快速构建应用系统（后台管理系统）。
- 默认提供了诸多业务系统的基本功能
- 继承了很多优秀的开源框架（开源）
- 可以直接作为一个后台管理系统的脚手架!

## 基本概念

![](../media/pictures/Dubbo.assets/8f6c780959c4b54d2f2ba4678e912817.png)

## 基本使用 

这里开始搭建后台开发的架子。

### 导入guns到IDEA

![](../media/pictures/Dubbo.assets/dab02c1d9a41b181d8710bc7ce9a6ae7.png)

### 如何启动guns项目

#### 运行admin模块

![](../media/pictures/Dubbo.assets/a178f9aaf032b2830966f554dcd3a43c.png)

如何修改数据源？

在Guns-admin模块里 ，有个 配置文件 application.yml

里面默认的数据源配置如下：

![](../media/pictures/Dubbo.assets/07619108db87df25f185a18013636026.png)

修改成我们自己的：

![](../media/pictures/Dubbo.assets/89ede97f1c1d1fcdf78d604efd72cb1d.png)

**spring:**  
**profiles:** local  
**datasource:**  
**url:**
jdbc:mysql://127.0.0.1:3306/guns?autoReconnect=true&useUnicode=true&characterEncoding=utf8&useSSL=false&serverTimezone=UTC  
**username:** root  
**password:** 123456  
**db-name:** guns *\#用来搜集数据库的所有表*  
**filters:** wall,mergeStat

然后启动项目：

登录 用户名 admin 密码 111111 可以成功登录！

项目启动成功！

### 初始化rest项目 （开发主要使用）

新建guns-rest数据库和里面的表

修改guns-rest的配置文件

![](../media/pictures/Dubbo.assets/4cb52dce8dcdca21462f7f9019c73659.png)

报错，因为我们的数据库是mysql8，所以有一个配置字段不一样。

Caused by: com.baomidou.mybatisplus.exceptions.MybatisPlusException: Error:
GlobalConfigUtils setMetaData Fail ! Cause:java.sql.SQLException: The connection
property 'zeroDateTimeBehavior' acceptable values are: 'CONVERT_TO_NULL',
'EXCEPTION' or 'ROUND'. The value 'convertToNull' is not acceptable.

把

zeroDateTimeBehavior=convertToNull

修改为

&zeroDateTimeBehavior=CONVERT_TO_NULL

去掉也可以额的

再次启动

缺少包：

![](../media/pictures/Dubbo.assets/4ae2855b71fd5fa7c8a6ce98e97e5066.png)

导入一个包：

\<dependency\>  
\<groupId\>log4j\</groupId\>  
\<artifactId\>log4j\</artifactId\>  
\<version\>1.2.17\</version\>  
\</dependency\>

访问下测试链接

<http://localhost/auth?userName=admin&password=admin>

返回

**{**"randomKey": "51656p","token": "eyJhbGciOiJIUzUxMiJ9.eyJyYW5kb21LZXkiOiI1MTY1NnAiLCJzdWIiOiJhZG1pbiIsImV4cCI6MTU1NTgyNzI2NCwiaWF0IjoxNTU1MjIyNDY0fQ.xfwl_6937X8T2etvQq6dQLuYb6ezCu4iJsAP0ggWQxn-TRuSJdoUQz0I02z4yNtVKtJbNakMwEolPp_XrbR46w"**}**

说明rest项目启动 OK！

## Rest项目的讲解

### Rest的使用场景

APP开发 后端

前后端分离项目 后端

### Rest新的模块的生成

### 工具的按装

Chrome浏览器的两个插件

RestLet ：类似PostMan，模拟浏览器发请求，跟后端进行交互

FeHelper：优化返回的Json的显示效果

### 基本使用

我们在Rest模块里写一个Rest接口

![](../media/pictures/Dubbo.assets/2a9bd7920f7813c110ef1a937fdaf30b.png)

测试：

![](../media/pictures/Dubbo.assets/67ec53833e12374d957954c3881f6510.png)

如何解决呢？

临时的解决方案：

修改配置文件，关闭鉴权

![](../media/pictures/Dubbo.assets/b1c3e2a952896cdd1b44ae24315b7253.png)

测试:

![](../media/pictures/Dubbo.assets/abe0094bdc581e819951d987450a3cc4.png)

### Rest模块的代码生成

生成工具的路径

![](../media/pictures/Dubbo.assets/1495afee990ef5edce341497764f38ae.png)

步骤：

#### 第一步，准备数据

新建数据库和表。

#### 个性化配置

修改生成代码的输出路径

![](../media/pictures/Dubbo.assets/571e012ddd402ef93dae007ba9589fb9.png)

修改作者

修改数据源配置：

![](../media/pictures/Dubbo.assets/2b761916433447e02e3da361c8dc94e6.png)

修改生成策略 作用的表

![](../media/pictures/Dubbo.assets/51fe4c42da71e48176d5ca19da87e283.png)

修改生成代码的包名：

![](../media/pictures/Dubbo.assets/8a9851260dd0ecae0c618170f242ff13.png)

最后，右键执行测试用例代码：

![](../media/pictures/Dubbo.assets/bd408a2b9d05020774f00010c52a9d9c.png)

成功：

![](../media/pictures/Dubbo.assets/edadf78718f7c269dbcb13406ec29b03.png)

生成之后，注意

![](../media/pictures/Dubbo.assets/24c31648ebc1e8930711fd2d3574c171.png)

这个如果没有放到指定的目录，而是放到modular目录里，项目启动的时候mapper无法自动生成实例，会报找不到实例的错误。

![](../media/pictures/Dubbo.assets/a7db731855aaf8a42e32d6130bc9c215.png)

这里mapper不用自己写实现

然后写代码测试一个 从controller 到service，到dao，出入一个Product

如下：测试插入一个product：

![](../media/pictures/Dubbo.assets/0766564067b558c3cdac95551d3d953a.png)

使用RestLet发请求

![](../media/pictures/Dubbo.assets/dcc02d102b9eb1eaa70f932afaa399a8.png)

代码正确的话，可以看到，product已经插入到数据库，

同时返回响应报文：

![](../media/pictures/Dubbo.assets/865681c44f921c699fdc928a19eb4a9e.png)

说明测试成功！



# Interview

## 1.Dubbo 对其他组件的调用

讲讲Dubbo怎么调用Zookeeper？



## 2.Dubbo协议相关

为什么http调用没有Dubbo快？

Dubbo有几种协议（有一种dubbo协议）

Dubbo用的传输协议是什么

Dubbo有几种协议（有一种dubbo协议）

Dubbo 和普通的 HTTP 有什么区别？你是怎么在dubbo微服务下调试程序的？



## 3.Dubbo分布式事务相关

Dubbo里面是如何管理分布式事务的

分布式事务了解吗，dubbo的源码和底层原理有了解吗？





## 4.Dubbo调用相关

各个服务之间的调用过程

Dubbo如何控制某个服务的优先级？什么加权降权在哪配置？

说一下Dubbo的异步调用。你用的Dubbo是什么版本的？最新版本是什么？

一个服务如何被消费者调用的？



## 5.Dubbo和SpringCloud比较

Dubbo和Springcloud不同点，以及怎么注册服务

介绍自己负责的模块，项目基本架构：spring boot dubbo zookeeper nginx ....   会问服务器几台，

Zookeeper 在项目的作用，问了为什么不用 spring cloud，乱扯一通 dubbo (性能对比)。

简要介绍dubbo 然后了解过spring cloud吗区别在于哪



## 6.Dubbo负载均衡

Dubbo怎么进行负载均衡

你还研究过Dubbo负载均衡？怎么配置的？这是在哪儿看到的？写的时候会有提示？用的是xml配置吗？



## 7.Dubbo服务治理 注册中心

Dubbo管理界面服务治理（注册中心）

如果注册中心挂掉了会怎么样？



## 8.Dubbo组成，原理，架构

Dubbo由哪些组成？

Dubbo原理

说一下Dubbo的架构？



## 9.介绍DUbbo，对Dubbo的理解

Dubbo你怎么理解？(本来想说dubbo的架构，被他打断说先不说架构，先说它的作用。。。)

简要说一下dubbo哪些模块比较重要，dubbo的负载均衡，服务的发现与注册有哪些？



可以了解一些**RPC的知识**，还有zookeeper,还有把**Dubbo的架构图**，**具体的流程**可以看看，到时候也可以说说



## 10.Dubbo线程挂起，超时

Dubbo你们遇到过超时的情况吗，怎么解决的

Dobbu中的如何避免线程长时间的挂起？



## 11.Dubbo序列化 

Dubbo的序列化、通信机制

为什么使用Dubbo的时候能够实例化接口？(因为通过接口创建了一个动态代理对象) dubbo的底层源码有看过吗？











# 网上题

**想往高处走，怎么能不懂 Dubbo？**

Dubbo是国内最出名的分布式服务框架，也是 Java 程序员必备的必会的框架之一。Dubbo 更是中高级面试过程中经常会问的技术，无论你是否用过，你都必须熟悉。

**下面我为大家准备了一些 Dubbo 常见的的面试题，一些是我经常问别人的，一些是我过去面试遇到的一些问题，总结给大家，希望对大家能有所帮助。**

------

## **1、Dubbo是什么？**

Dubbo是阿里巴巴开源的基于 Java 的高性能 RPC 分布式服务框架，现已成为 Apache 基金会孵化项目。

面试官问你如果这个都不清楚，那下面的就没必要问了。

> 官网：http://dubbo.apache.org

## **2、为什么要用Dubbo？**

因为是阿里开源项目，国内很多互联网公司都在用，已经经过很多线上考验。内部使用了 Netty、Zookeeper，保证了高性能高可用性。

使用 Dubbo 可以将核心业务抽取出来，作为独立的服务，逐渐形成稳定的服务中心，可用于提高业务复用灵活扩展，使前端应用能更快速的响应多变的市场需求。

下面这张图可以很清楚的诠释，最重要的一点是，分布式架构可以承受更大规模的并发流量。

![img](../media/pictures/Dubbo.assets/640.webp)

下面是 Dubbo 的服务治理图。

![img](D:/Code/Typora/media/pictures/Dubbo.assets/640.webp)

## **3、Dubbo 和 Spring Cloud 有什么区别？**

两个没关联，如果硬要说区别，有以下几点。

1）通信方式不同

Dubbo 使用的是 RPC 通信，而 Spring Cloud 使用的是 HTTP RESTFul 方式。

2）组成部分不同

![img](D:/Code/Typora/media/pictures/Dubbo.assets/640.webp)

## **4、dubbo都支持什么协议，推荐用哪种？**

- dubbo://（推荐）
- rmi://
- hessian://
- http://
- webservice://
- thrift://
- memcached://
- redis://
- rest://

## **5、Dubbo需要 Web 容器吗？**

不需要，如果硬要用 Web 容器，只会增加复杂性，也浪费资源。

## **6、Dubbo内置了哪几种服务容器？**

- Spring Container
- Jetty Container
- Log4j Container

Dubbo 的服务容器只是一个简单的 Main 方法，并加载一个简单的 Spring 容器，用于暴露服务。

## **7、Dubbo里面有哪几种节点角色？**

![img](../media/pictures/Dubbo.assets/640-1588995722550.webp)

**8、画一画服务注册与发现的流程图**

![img](../media/pictures/Dubbo.assets/640.png)

该图来自 Dubbo 官网，供你参考，如果你说你熟悉 Dubbo, 面试官经常会让你画这个图，记好了。

## **9、Dubbo默认使用什么注册中心，还有别的选择吗？**

推荐使用 Zookeeper 作为注册中心，还有 Redis、Multicast、Simple 注册中心，但不推荐。

## **10、Dubbo有哪几种配置方式？**

1）Spring 配置方式
2）Java API 配置方式

## **11、Dubbo 核心的配置有哪些？**

我曾经面试就遇到过面试官让你写这些配置，我也是蒙逼。。

![img](D:/Code/Typora/media/pictures/Dubbo.assets/640.png)

配置之间的关系见下图。

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

## **12、在 Provider 上可以配置的 Consumer 端的属性有哪些？**

1）timeout：方法调用超时
2）retries：失败重试次数，默认重试 2 次
3）loadbalance：负载均衡算法，默认随机
4）actives 消费者端，最大并发调用限制

## **13、Dubbo启动时如果依赖的服务不可用会怎样？**

Dubbo 缺省会在启动时检查依赖的服务是否可用，不可用时会抛出异常，阻止 Spring 初始化完成，默认 check="true"，可以通过 check="false" 关闭检查。

## **14、Dubbo推荐使用什么序列化框架，你知道的还有哪些？**

推荐使用Hessian序列化，还有Duddo、FastJson、Java自带序列化。

## **15、Dubbo默认使用的是什么通信框架，还有别的选择吗？**

Dubbo 默认使用 Netty 框架，也是推荐的选择，另外内容还集成有Mina、Grizzly。

## **16、Dubbo有哪几种集群容错方案，默认是哪种？**

![img](../media/pictures/Dubbo.assets/640-1588995722584.webp)

## **17、Dubbo有哪几种负载均衡策略，默认是哪种？**

![img](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

## **18、注册了多个同一样的服务，如果测试指定的某一个服务呢？**

可以配置环境点对点直连，绕过注册中心，将以服务接口为单位，忽略注册中心的提供者列表。

## **19、Dubbo支持服务多协议吗？**

Dubbo 允许配置多协议，在不同服务上支持不同协议或者同一服务上同时支持多种协议。

## **20、当一个服务接口有多种实现时怎么做？**

当一个接口有多种实现时，可以用 group 属性来分组，服务提供方和消费方都指定同一个 group 即可。

## **21、服务上线怎么兼容旧版本？**

可以用版本号（version）过渡，多个不同版本的服务注册到注册中心，版本号不同的服务相互间不引用。这个和服务分组的概念有一点类似。

## **22、Dubbo可以对结果进行缓存吗？**

可以，Dubbo 提供了声明式缓存，用于加速热门数据的访问速度，以减少用户加缓存的工作量。

## **23、Dubbo服务之间的调用是阻塞的吗？**

默认是同步等待结果阻塞的，支持异步调用。

Dubbo 是基于 NIO 的非阻塞实现并行调用，客户端不需要启动多线程即可完成并行调用多个远程服务，相对多线程开销较小，异步调用会返回一个 Future 对象。

异步调用流程图如下。

![img](../media/pictures/Dubbo.assets/640-1588995722595.webp)

## **24、Dubbo支持分布式事务吗？**

目前暂时不支持，后续可能采用基于 JTA/XA 规范实现，如以图所示。

![img](../media/pictures/Dubbo.assets/640-1588995722606.webp)

## **25、Dubbo telnet 命令能做什么？**

dubbo 通过 telnet 命令来进行服务治理，具体使用看这篇文章《[dubbo服务调试管理实用命令](https://mp.weixin.qq.com/s?__biz=MzI3ODcxMzQzMw==&mid=2247483709&idx=1&sn=afe0688c184f00902529583a85d90089&scene=21#wechat_redirect)》。

> telnet localhost 8090

## **26、Dubbo支持服务降级吗？**

Dubbo 2.2.0 以上版本支持。

## **27、Dubbo如何优雅停机？**

Dubbo 是通过 JDK 的 ShutdownHook 来完成优雅停机的，所以如果使用 kill -9 PID 等强制关闭指令，是不会执行优雅停机的，只有通过 kill PID 时，才会执行。

## **28、服务提供者能实现失效踢出是什么原理？**

服务失效踢出基于 Zookeeper 的临时节点原理。

## **29、如何解决服务调用链过长的问题？**

Dubbo 可以使用 Pinpoint 和 Apache Skywalking(Incubator) 实现分布式服务追踪，当然还有其他很多方案。

## **30、服务读写推荐的容错策略是怎样的？**

读操作建议使用 Failover 失败自动切换，默认重试两次其他服务器。

写操作建议使用 Failfast 快速失败，发一次调用失败就立即报错。

## **31、Dubbo必须依赖的包有哪些？**

Dubbo 必须依赖 JDK，其他为可选。

## **32、Dubbo的管理控制台能做什么？**

管理控制台主要包含：路由规则，动态配置，服务降级，访问控制，权重调整，负载均衡，等管理功能。

## **33、说说 Dubbo 服务暴露的过程。**

Dubbo 会在 Spring 实例化完 bean 之后，在刷新容器最后一步发布 ContextRefreshEvent 事件的时候，通知实现了 ApplicationListener 的 ServiceBean 类进行回调 onApplicationEvent 事件方法，Dubbo 会在这个方法中调用 ServiceBean 父类 ServiceConfig 的 export 方法，而该方法真正实现了服务的（异步或者非异步）发布。

## **34、Dubbo 停止维护了吗？**

2014 年开始停止维护过几年，17 年开始重新维护，并进入了 Apache 项目。

## **35、Dubbo 和 Dubbox 有什么区别？**

Dubbox 是继 Dubbo 停止维护后，当当网基于 Dubbo 做的一个扩展项目，如加了服务可 Restful 调用，更新了开源组件等。

## **36、你还了解别的分布式框架吗？**

别的还有 Spring cloud、Facebook 的 Thrift、Twitter 的 Finagle 等。

## **37、Dubbo 能集成 Spring Boot 吗？**

可以的，项目地址如下。

> https://github.com/apache/incubator-dubbo-spring-boot-project

## **38、在使用过程中都遇到了些什么问题？**

Dubbo 的设计目的是为了满足高并发小数据量的 rpc 调用，在大数据量下的性能表现并不好，建议使用 rmi 或 http 协议。

## **39、你读过 Dubbo 的源码吗？**

要了解 Dubbo 就必须看其源码，了解其原理，花点时间看下吧，网上也有很多教程，后续有时间我也会在公众号上分享 Dubbo 的源码。

## **40、你觉得用 Dubbo 好还是 Spring Cloud 好？**





