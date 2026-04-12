<div align="center">

<h1>Awesome Architecture Patterns</h1>

[![Awesome](https://img.shields.io/badge/Awesome-列表-green?style=for-the-badge&logo=awesome-lists&logoColor=white)](https://github.com/kbtale/awesome-architecture-patterns)
[![License](https://img.shields.io/badge/许可证-MIT-blue?style=for-the-badge&logo=open-source-initiative&logoColor=white)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-欢迎-brightgreen?style=for-the-badge&logo=github&logoColor=white)](CONTRIBUTING.zh.md)

<br>

[![English](https://img.shields.io/badge/-English-blue?style=for-the-badge&logoColor=white)](README.md)
[![Español](https://img.shields.io/badge/-Español-red?style=for-the-badge&logoColor=white)](README.es.md)
[![中文](https://img.shields.io/badge/-中文-orange?style=for-the-badge&logoColor=white)](README.zh.md)

</div>

> [!NOTE]
> 此中文翻译由 AI 自动生成。如果您发现任何不准确之处，诚挚欢迎您提交 Pull Request (PR) 协助改进与修复，非常感谢。

> [!TIP]
> 使用本 README 右上角的 **目录 (Table of Contents)** 菜单可以快速在各架构层级和模式之间切换。

软件架构与设计模式的多层分类法。本仓库旨在对软件工程的基础组件进行分类，从宏观的云拓扑到微观的对象交互，同时也涵盖了横向关注点（Cross-Cutting Concerns）和高层企业架构框架。

我的目标是为每种架构模式及其变体建立一个集中的资源、文档和实现示例索引。

## 参考资料

本汇编汇总并组织了多部软件工程经典著作和行业标准中的概念：
* **Pattern-Oriented Software Architecture (POSA)** - Frank Buschmann, Regine Meunier, Hans Rohnert, Peter Sommerlad, Michael Stal.
* **The C4 Model** (软件架构可视化) - Simon Brown.
* **Enterprise Integration Patterns** - Gregor Hohpe, Bobby Woolf.
* **Design Patterns: Elements of Reusable Object-Oriented Software (GoF)** - Erich Gamma, Richard Helm, Ralph Johnson, John Vlissides.
* **Domain-Driven Design (DDD)** - Eric Evans.
* **Clean Architecture** - Robert C. Martin.

## 目录

* [第一层：系统架构模式](#第一层系统架构模式)
* [第二层：企业集成模式](#第二层企业集成模式)
* [第三层：应用架构模式](#第三层应用架构模式)
* [第四层：软件设计模式](#第四层软件设计模式)
* [横切架构关注点](#横切架构关注点)
* [企业架构框架](#企业架构框架)

## 第一层：系统架构模式

本层涉及系统的高层结构及其部署方式。涵盖了如何将应用程序分解为多个部分，并将其分布在网络中。无论是使用单体架构还是微服务，这些模式都负责管理扩展、区域故障以及大规模数据处理。

### 核心应用部署拓扑

定义应用程序的主要功能单元如何在底层基础设施上进行打包、扩展和部署的广泛结构范式。

<details>
<summary><strong>Monolithic Architecture (单体架构):</strong> 一种统一的模型，将整个应用程序作为一个单元进行构建、打包和部署。</summary>

从历史上看，单体架构只是在分布式云计算普及之前构建软件的通用方式。从 UI 渲染到数据库访问的每个组件都共享相同的内存空间和部署流。虽然在微服务兴起期间因容易演变成纠缠不清的“大泥球”而饱受诟病，但该模式已经复兴（通常被称为“宏伟的单体”/Majestic Monolith），因为企业意识到单进程架构显著降低了除超大型工程团队外所有人的运营复杂性、网络延迟和基础设施成本。

- **示例:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): GitLab 的核心单体应用，主要基于 Ruby on Rails 构建。
  - [discourse/discourse](https://github.com/discourse/discourse): 广泛使用的开源讨论平台单体应用。
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): 去中心化社交网络的核心服务器应用。
- **资源:**
  - [MonolithFirst](https://martinfowler.com/bliki/MonolithFirst.html) (Martin Fowler): 论述为什么从单体开始通常是最佳方法的一篇文章。
  - [The Majestic Monolith](https://m.signalvnoise.com/the-majestic-monolith/) (DHH): Ruby on Rails 创始人论述单体架构优势的观点。

</details>

<details>
<summary><strong>Modular Monolith Architecture (模块化单体架构):</strong> 一种内部结构化为基于业务能力的模块的单体应用，允许将来提取为微服务。</summary>

这种模式是对分布式微服务运营压力的一种务实反应。它将领域驱动设计 (DDD) 的严格限界上下文应用到单个部署单元中。团队可以在孤立的模块中独立工作，通过函数调用而非不稳定的网络请求进行通信，从而避免了管理网络故障、最终一致性或复杂的 Kubernetes 集群。Shopify 等科技巨头证明了，通过严格的静态分析工具，单体代码库可以在不退化为紧耦合乱局的情况下扩展到数千名开发人员。

- **示例:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): 实现电子商务领域模块化单体的全面 TypeScript 参考应用。
  - [danilofes/modular-monolith-architecture](https://github.com/danilofes/modular-monolith-architecture): 展示在线商店模块化单体的 Java/Spring Boot 参考应用。
- **资源:**
  - [Deconstructing the Monolith](https://shopify.engineering/deconstructing-monolith-designing-software-that-grows) (Shopify Engineering): 关于 Shopify 转向模块化单体架构的详细案例分析。
  - [Modular Monolith: A Middle Ground to Microservices](https://www.infoq.com/articles/modular-monolith-architecture/): 探讨这种混合方法优点的技术概述。

</details>

<details>
<summary><strong>Microservices Architecture (微服务架构):</strong> 将应用程序分解为小型、松耦合、可独立部署的服务，每个服务拥有自己的数据库。</summary>

微服务兴起于 2010 年代初，由 Netflix 和 Amazon 等呈指数级增长的公司推动，成为了云原生时代的定义性架构。其主要驱动力是组织扩展。通过将系统分解为隔离的服务，独立团队可以无需与中央发布经理协调即可部署代码。虽然它解决了组织的瓶颈，但在分布式数据事务、网络可靠性和可观察性方面引入了巨大的技术复杂性。

- **示例:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Google 用于 Kubernetes 和 gRPC 的 11 层多语言参考应用 (Online Boutique)。
  - [dotnet/eShop](https://github.com/dotnet/eShop): 微软官方的 .NET 多平台微服务参考应用。
- **资源:**
  - "Building Microservices: Designing Fine-Grained Systems" (Sam Newman): 关于微服务设计、部署和维护的奠基性著作。
  - [Microservices - A Definition of This New Architectural Term](https://martinfowler.com/articles/microservices.html) (James Lewis 和 Martin Fowler): 对该模式的原始形式化定义。

</details>

<details>
<summary><strong>Service-Oriented Architecture (SOA, 面向服务架构):</strong> 粗粒度的、可重用的服务通过通信协议提供业务功能，通常由企业服务总线 (ESB) 协调。</summary>

SOA 在 2000 年代初期主导了企业领域，是微服务的前身。尽管在表面上与微服务相似，但 SOA 专注于使用标准化协议（通常是 SOAP 和 XML）在整个企业中集成单体企业应用（如 ERP 和 CRM）。它高度依赖于“智能管道”：集中的企业服务总线 (ESB)，负责人处理路由、消息转换和安全性。

- **资源:**
  - [Service-Oriented Architecture](https://en.wikipedia.org/wiki/Service-oriented_architecture): 维基百科上关于其历史、核心原则和组件的概述。
  - [SOA vs Microservices: What's the Difference?](https://www.ibm.com/topics/soa-vs-microservices): IBM 关于这些相关但截然不同的架构风格演变的分析。

</details>


### 云原生与分布式计算模式

管理在不可靠网络上运行的数百或数千个节点之间的一致性、可用性和分区的结构协议。

<details>
<summary><strong>Serverless Architecture (无服务器架构):</strong> 一种执行模型，云提供商在其中分配机器资源，根据请求自动按需运行代码，并管理服务器的生命周期。</summary>

这种架构不仅是简单的托管，还消除了一切资源管理的负担。开发人员只需上传代码块（函数），由事件触发执行。它提供了极高的弹性扩展能力，因为基础设施可以根据实时需求从零扩展到数千个实例。虽然它是极佳的成本节约工具，但它会将开发人员锁定在特定提供商的生态系统中，并引入了“冷启动”延迟问题。

- **示例:**
  - [aws-samples/aws-serverless-shopping-cart](https://github.com/aws-samples/aws-serverless-shopping-cart): 展示如何使用 AWS Lambda、DynamoDB 和 API Gateway 构建完整的购物车服务。
  - [vercel/next.js](https://github.com/vercel/next.js): 尽管它是一个框架，但其架构针对无服务器环境（如 Vercel）的部署进行了深度优化，将路由透明地转换为独立边缘函数。
- **资源:**
  - [Serverless Architectures](https://martinfowler.com/articles/serverless.html) (Mike Roberts): 关于无服务器定义、优势和权衡的详细文章。
  - [The Serverless Guide](https://www.serverless.com/learn/overview/): 介绍各个云提供商平台及其优势的广泛指南。

</details>

<details>
<summary><strong>Edge Computing Architecture (边缘计算架构):</strong> 将计算和数据存储带到离数据源或用户更近的地方，以提高响应速度并节省带宽。</summary>

通过在边缘节点（如蜂窝基站、IoT 设备或 CDN 节点）处理数据，边缘架构显著降低了往返中央数据中心相关的延迟。这对于自动驾驶、虚拟现实和工业自动化等实时性要求极高的场景至关重要。它还能在将大型数据集发送到云端进行长期存储前执行本地过滤，从而降低网络成本。

- **示例:**
  - [cloudflare/workers-sdk](https://github.com/cloudflare/workers-sdk): 允许开发人员在全球边缘运行 JavaScript、Rust 和 Wasm，利用 Cloudflare 庞大的全球网络。
  - [edgexfoundry/edgex-go](https://github.com/edgexfoundry/edgex-go): 用于工业物联网边缘计算的开源、供应商中立、高度模块化的中间件框架。
- **资源:**
  - [What is Edge Computing?](https://www.cloudflare.com/learning/serverless/glossary/what-is-edge-computing/): Cloudflare 关于边缘计算基础知识、应用场景和优势的解释。
  - [Hitchhiker's Guide to Edge Computing](https://www.section.io/blog/hitchhikers-guide-to-edge-computing/): 涵盖从延迟优势到编排架构等核心概念的深入文章。

</details>

<details>
<summary><strong>Peer-to-Peer (P2P) Architecture (对等架构):</strong> 这是一个由相互通信的等价点组成的网络。节点之间不通过中心服务器直接分配工作。</summary>

与向中央资源请求数据的标准模型不同，P2P 系统将客户端和服务器的角色合并到每一个节点（Peer）中。这些系统具有极高的弹性和抗审查能力，因为不存在单点故障。由于没有集中的权限机构，P2P 架构必须实施复杂的共识协议和分布式哈希表 (DHT) 来管理成员身份和数据检索。它是文件共享网络、视频会议系统和区块链的基础。

- **示例:**
  - [libp2p/go-libp2p](https://github.com/libp2p/go-libp2p): P2P 网络栈的参考实现，驱动了 IPFS（星际文件系统）和 Eth2（以太坊 2.0）。
  - [transmission/transmission](https://github.com/transmission/transmission): 实现 BitTorrent 协议的广泛使用的开源客户端。
- **资源:**
  - [Peer-to-Peer Networks](https://en.wikipedia.org/wiki/Peer-to-peer): 深入研究 P2P 网络的设计细节。
  - [An Introduction to Distributed Systems](https://www.amazon.com/Distributed-Systems-Principles-Andrew-Tanenbaum/dp/1543057381) (Andrew S. Tanenbaum): 讨论大规模分布式拓扑中对等通信的经典著作。

</details>

<details>
<summary><strong>Client-Server Architecture (客户端-服务器架构):</strong> 这是一个计算架构，其中发送请求的被称为客户端，提供服务的被称为服务器。</summary>

互联网最基础的架构模型。它建立在分工明确的基础上：服务器是持有状态并控制对资产访问的强大中央权限机构。这种不对称的结构使得安全性、一致性和管理变得更加容易。由于所有客户端必须连接到服务器进行协调，它在处理过载流量时容易出现可扩展性瓶颈。

- **示例:**
  - [postgres/postgres](https://github.com/postgres/postgres): 典型的数据库服务器，通过结构化查询协议监听和响应来自数千个客户端的并发数据请求。
  - [nginx/nginx](https://github.com/nginx/nginx): 处理数百万入站 HTTP 连接请求并将静态资源或连接转发给其他后端服务器的中央服务器模块。
- **资源:**
  - [Client-Server Model](https://en.wikipedia.org/wiki/Client%E2%80%93server_model): 关于分工和通信协议的维基百科概述。

</details>

<details>
<summary><strong>Multi-Tier (N-Tier) Architecture (多层架构):</strong> 物理/逻辑上的分层。典型的结构包括：表现层、应用层和数据层。</summary>

多层架构是为了解决将整个系统构建为一个单体应用所带来的管理挑战。N-Tier 最常见的形式是 3 层架构，通常包含位于其自身服务器或集群中的表现层（Web 端）、逻辑层（应用服务器）和数据层（数据库）。这允许独立扩展每一层：如果用户增多，可以增加 Web 服务器而不必动数据库。它是大多数传统企业 Java/C# 以及早期的 LAMP 栈系统的核心结构标准。

- **示例:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): 虽然它由微服务组成，但其核心拓扑仍然通过明确定义的表现层、计算层和持久层来组织处理流程，代表了现代云原生的 N-Tier 方法。
- **资源:**
  - [N-tier architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/n-tier): 微软 Azure 关于多层系统分层、可扩展性和部署的详细指南。

</details>


### 以数据为中心的架构模式

组织数据库系统、数据流和分析层的模型，其性能和结构完全由数据资产的组织方式驱动。

<details>
<summary><strong>Database Systems Architecture (数据库系统架构):</strong> 多个独立计算单元（如传统的 3 层应用）访问的集中式数据存储。</summary>

这是一种以可靠、集中的数据库管理系统为核心应用的架构。多个应用实例或服务连接到这个共享数据库以读取、写入和操作数据。数据库本身作为整个分布式系统的唯一事实来源，负责管理并发性、事务完整性和安全性。

- **示例:**
  - [postgres/postgres](https://github.com/postgres/postgres): PostgreSQL 的核心仓库，代表了集中式关系型数据库系统的黄金标准。
  - [mysql/mysql-server](https://github.com/mysql/mysql-server): MySQL 的核心仓库，在传统 Web 架构中作为集中式数据存储被广泛使用。
- **资源:**
  - "Database System Concepts" (Abraham Silberschatz, Henry F. Korth 和 S. Sudarshan): 详细阐述数据库管理系统架构的权威学术教科书。
  - [Architecture of a Database System](https://dsf.berkeley.edu/papers/fntdb07-architecture.pdf) (Joseph M. Hellerstein, Michael Stonebraker 和 James Hamilton): 探讨关系数据库引擎构建方式的深入论文。

</details>

<details>
<summary><strong>Data Mesh (数据网格):</strong> 一种去中心化的社会技术架构，将数据视为产品，由领域团队拥有并提供数据服务。</summary>

这是一种分散化的数据架构方法，将责任直接分配给生成数据的具体业务领域。每个领域团队拥有自己的数据流水线，并将其数据作为功能完整的“产品”服务于组织的其他部分。联合治理结构确保这些不同的数据产品在更广泛的企业范围内保持互操作性和安全性。

- **示例:**
  - *示例说明:* Data Mesh 是一种去中心化的社会技术组织范式，而非一种简单的软件应用。它规定了企业内不同的领域团队如何治理和共享数据。因为它主要涉及数据所有权的架构重组，高度依赖于内部治理和各种工具，因此没有单一的开源应用代码库能代表 Data Mesh。不过，以下示例展示了实现细节：
    - [Data-Mesh-Manager/data-mesh-architecture-examples](https://github.com/Data-Mesh-Manager/data-mesh-architecture-examples): 用于实现去中心化数据产品的架构蓝图和基础设施示例合集。
- **资源:**
  - [How to Move Beyond a Monolithic Data Lake to a Distributed Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html) (Zhamak Dehghani): 介绍 Data Mesh 范式的原始文章。
  - "Data Mesh: Delivering Data-Driven Value at Scale" (Zhamak Dehghani): 详述实现 Data Mesh 所需的组织变革和技术细节的著作。

</details>

<details>
<summary><strong>Data Fabric (数据织物/数据编织):</strong> 一种架构，跨混合云和多云环境提供统一的数据平面。</summary>

这种架构利用机器学习和元数据在大容量的异构系统和云提供商之间自动发现、连接和保护数据。它创建了一个统一的虚拟化数据层，允许用户和应用直接跨所有物理位置和存储格式访问信息。

- **示例:**
  - *示例说明:* Data Fabric 是一种概念性的企业级集成策略，利用 AI 和元数据来整合跨多个私有云和公有云的数据。它是通过部署数十个互联的治理、编录和虚拟化平台来实现的。作为一个宏观 IT 策略，没有单一的开源应用能代表 Data Fabric。不过，以下示例展示了实现细节：
    - [GoogleCloudPlatform/dataplex-blueprints](https://github.com/GoogleCloudPlatform/dataplex-blueprints): 使用 Google Cloud Dataplex 构建智能数据织物的基础设施即代码和配置示例。
- **资源:**
  - [What is a Data Fabric?](https://www.ibm.com/topics/data-fabric) (IBM): 对数据织物组成部分的清晰定义和概述。
  - [What is a Data Fabric?](https://www.sap.com/insights/what-is-a-data-fabric.html) (SAP): 详述数据织物概念、核心组件以及它如何跨环境统一数据管理的分析。

</details>


### 事件、消息与通信拓扑

分布式模型模型，规定了异构服务如何交换信息、对状态更改作出反应以及动态管理请求路由。

<details>
<summary><strong>Event-Driven Architecture (Macro) (基于事件的架构):</strong> 这是一个组件对在网络中广播的状态更改（事件）做出反应的分布式系统，而不是依靠直接的请求/响应。</summary>

一种高度解耦的拓扑，围绕状态更改的生产、检测和消费构建。服务将事件发布到中央代理或事件总线。订阅的服务监听这些事件并异步触发其隔离的业务逻辑。它用于构建高响应、高扩展性的系统，其中不可预测的流量峰值由队列吸收，以保护下游数据库。

- **示例:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): “微服务架构设计模式”一书的参考应用，完全基于事件驱动架构构建，使用 Sagas 和事务性发件箱（Transactional Outboxes）。
  - [aws-samples/aws-serverless-airline-booking](https://github.com/aws-samples/aws-serverless-airline-booking): 在 AWS 上构建的完整无服务器应用，通过 EventBridge 使用事件驱动架构协调不同的预订服务。
- **资源:**
  - [What is an Event-Driven Architecture?](https://aws.amazon.com/event-driven-architecture/) (AWS): 关于事件驱动系统的组件和优势指南。
  - "Designing Event-Driven Systems" (Ben Stopford): 关于构建以事件为中心的架构的详细著作。

</details>

<details>
<summary><strong>Process Communication (Communicating Processes) Architecture (过程通信架构):</strong> 独立的过程通过像 sockets、消息队列或共享内存这样的通道进行通信。</summary>

这是一种核心并发模型，其中应用被分解为隔离的、并发执行的过程，通过彼此传递消息来协调工作。通过确保过程仅通过严格定义的通道分享显式传递的消息，系统防止了竞态条件和复杂的锁定机制。它是高并发系统（如电信交换机、聊天服务器和分布式数据库）的架构基础。

- **示例:**
  - [rabbitmq/rabbitmq-server](https://github.com/rabbitmq/rabbitmq-server): 尽管它被当作消息中介使用，但其内部架构是 Erlang Actor 模型的典型示例，使用数千个隔离的、通过通信过程管理高并发。
  - [syncthing/syncthing](https://github.com/syncthing/syncthing): 用 Go 编写的持续文件同步程序，内部架构围绕着通信顺序进程 (CSP)，使用 goroutines 和 channels 在同步操作之间安全传递消息。
- **资源:**
  - [Communicating Sequential Processes](http://www.usingcsp.com/cspbook.pdf) (C.A.R. Hoare): 定义 CSP 架构风格的核心计算机科学论文。
  - [The Actor Model](https://doc.akka.io/docs/akka/current/typed/guide/actors-intro.html) (Akka): 解释并发过程如何通过消息传递进行通信的文档。

</details>

<details>
<summary><strong>Service Mesh Architecture (服务网格架构):</strong> 这是一个专门的基础设施层，用于在微服务架构中管理服务端到端的通信，通常使用 sidecar proxy 这种形式。在不改变其应用代码的情况下处理路由、安全和可观测等。</summary>

一种运维拓扑，将网络层从应用代码中抽象出来。重试逻辑、双向 TLS 加密和分布式追踪等网络能力由部署在每个服务实例旁边的 sidecar 代理处理。这些相互连接的代理形成的 Web 网络组成了“网格”，并由中央控制平面控制。它是维护大型 Kubernetes 集群中安全性、可观测性和流量控制的关键。

- **示例:**
  - [istio/istio/tree/master/samples/bookinfo](https://github.com/istio/istio/tree/master/samples/bookinfo): 官方多语言参考应用，专门设计用于演示跨不同语言后端的服务网格流量路由、故障注入和指标展示。
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Google 的 11 层应用 (Online Boutique)，明确被设计部署在服务网格中以处理服务间通信。
- **资源:**
  - [What is a Service Mesh?](https://www.redhat.com/en/topics/microservices/what-is-a-service-mesh) (Red Hat): 对数据平面、控制平面和 sidecar 代理概念的清晰描述。
  - "Istio Up and Running" (Lee Calcote 和 Zack Butcher): 实现服务网格架构的实践指南。

</details>

<details>
<summary><strong>API Gateway / Backends for Frontends (BFF) Architecture (API 网关 / BFF 架构):</strong> 这是一个单一的入口点 (gateway) 或多个特定的后端的(BFF) 客户端。其处理路由、组合以及 API 跨层级等关注点。</summary>

一种用于抽象后端微服务复杂性的结构化模式。API 网关是一个反向代理，将多个微服务调用聚合成一个单一响应，处理身份验证、流量限制和请求路由。**Backends for Frontends (BFF)** 变体更进一步，为不同的 UI 客户端（例如，移动端 API 与桌面 Web API 分开）创建专用、独立的网关。这确保了客户端接收到其特定界面格式所需的精确数据。

- **示例:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): 微软的参考微服务应用，实现了 BFF 模式，为其 Web UI 和移动端客户端提供了完全独立的网关路由配置。
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): 提供一个专用的 `frontend` 服务作为单一 API 网关，协调对各后端服务（购物车、产品目录、货币等）的调用以渲染最终 Web 视图。
- **资源:**
  - [Pattern: Backends For Frontends](https://samnewman.io/patterns/architectural/bff/) (Sam Newman): BFF 架构模式的原始定义和深度探讨。
  - [API Gateway Pattern](https://microservices.io/patterns/apigateway.html) (Chris Richardson): 详细分析在分布式架构中使用统一 API 网关的优势和权衡。

</details>


### 并发、状态与事务拓扑

便于复杂的管理状态、高吞吐量的并行性以及没有传统锁定瓶颈的分布式事务的范例。

<details>
<summary><strong>Actor Model Architecture (参与者模式架构):</strong> 这是一个并发计算的概念模型，其中“参与者”是通用的基元。它可以修改自身。其本身的状态也只能通过异步消息传递进行通信（例如 Erlang，Akka）。</summary>

一种高并发拓扑，系统由数千或数万个被称为“Actor”的独立、轻量级实体组成。每个 Actor 严格封装其私有状态和执行线程。由于 Actor 之间从不共享内存，且仅通过彼此的消息邮箱发送异步消息进行交互，系统消除了对传统线程锁（Locks）和互斥体（Mutexes）的需求。它是高并发、容错系统（如多人游戏服务器和电信交换机）的首选架构。

- **示例:**
  - [ornicar/lila](https://github.com/ornicar/lila): Lichess.org 的核心后端应用。使用 Scala 和 Akka 框架构建，在没有锁定瓶颈的情况下处理数百万个并发国际象棋比赛、玩家状态和实时 Websocket 连接。
  - [rabbitmq/rabbitmq-server](https://github.com/rabbitmq/rabbitmq-server): 广泛使用的消息中介，原生使用 Erlang 开发。其内部架构是 Actor 模式的教科书级实现，数百万个轻量级 Actor 进程并发处理排队、路由和状态管理。
- **资源:**
  - [The Actor Model in 10 Minutes](https://www.brianstorti.com/the-actor-model/) (Brian Storti): 关于 Actor 如何 manage 状态、并发性及消息邮箱的通俗解释。
  - "Reactive Messaging Patterns with the Actor Model" (Vaughn Vernon): 深入探讨使用基于 Actor 的并发机制构建企业系统。

</details>

<details>
<summary><strong>Space-Based Architecture (Tuple Space) (基于空间的架构):</strong> 使用分布式共享内存来避免数据库瓶颈。根据高容量、可变流量进行水平扩展。</summary>

这种架构旨在消除作为性能瓶颈的数据库。应用不再通过网络查询中心数据库，而是将数据分区并保存在跨活动处理单元集群的内存中。应用逻辑及其操作的数据共存于同一内存 (RAM，即“空间”) 中。它通过启动更多处理单元进行水平扩展，使其在处理不可预测流量峰值的系统中非常有效，如高频交易平台、票务系统和实时竞价引擎。

- **示例:**
  - *示例说明:* Space-Based Architecture 更多是一种企业部署拓扑，而非单一的应用设计。它是通过将业务逻辑直接部署到分布式内存数据网格 (IMDG) 中间件中实现的。因为它高度依赖于跨集群编排这些专门的网格引擎（如 Apache Ignite 或 Hazelcast），目前还没有单一的可部署开源业务应用仓库能完全、原生代表这一拓扑。
- **资源:**
  - [Space-Based Architecture Pattern](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch04.html) (Mark Richards): 关于处理单元、虚拟化中间件和数据网格的权威架构解释。
  - [Tuple Space](https://en.wikipedia.org/wiki/Tuple_space): 对演变为现代基于空间的架构的核心分布式计算概念的概述。

</details>

<details>
<summary><strong>Saga Architecture (Saga 架构):</strong> 管理分布式微服务事务，使用带有补偿动作的本地事务序列。</summary>

这是一种分布式事务模式，解决了维护跨多个独立数据库的一致性难题。由于松耦合的微服务无法共享单一组件的 ACID 数据库事务，Saga 将大型业务事务分解为一系列较小的、本地化的步骤。如果下游某个步骤失败，系统执行一系列“补偿事务”（Rollbacks）来撤销之前的步骤。它能在不依赖双阶段提交 (2PC) 等同步、分布式锁定协议的情况下实现最终一致性。

- **示例:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): 微服务的终极参考应用，旨在演示复杂的“Food to Go”订单管理系统中的 Saga 编排（Choreography）和协调（Orchestration）。
  - [berndruecker/trip-booking-saga-java](https://github.com/berndruecker/trip-booking-saga-java): 一个纯业务应用，演示了旅游预订 Saga（依次预订航班、酒店和汽车），并突出了当远程预订失败时如何执行补偿动作。
- **资源:**
  - [Pattern: Saga](https://microservices.io/patterns/data/saga.html) (Chris Richardson): 关于 Sagas 中协调与编排定义的行业标准。
  - [Saga distributed transactions](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/saga/saga) (Microsoft Azure): 关于在云原生微服务中实现 Saga 模式的实践指南。

</details>


### 知识、人工智能与控制系统架构

专门用于自主推理、推理、模式识别和物理硬件管理的宏观结构。

<details>
<summary><strong>Agentic Architecture (Multi-Agent Systems) (智能体架构 / 多智能体系统):</strong> 这是一个正在兴起的由 AI 驱动的拓扑。在这个拓扑中，自治系统（智能体）使用大语言模型（LLM）进行推理、计划和执行行动。通常这些智能体是通过协作来实现复杂目标的。</summary>

一种重度依赖大型语言模型 (LLMs) 作为中央推理引擎的动态拓扑。不同于遵循确定的硬编码路径，系统定义高层目标，并为“智能体”配备工具（计算器、网络搜索、API 访问）。这些智能体会自主规划执行步骤、反映中间结果，并与其他专门的智能体通信以解决复杂的开放式问题。它代表了从指令式编程向目标驱动、自治编排的转变。

- **示例:**
  - [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT): 非常流行的开源应用，作为一个自治智能体，它将 LLM 的思考链接起来，独立完成用户定义的目标。
  - [OpenBMB/ChatDev](https://github.com/OpenBMB/ChatDev): 一个虚拟软件公司应用，多个不同的 AI 智能体（如 CEO、程序员和审计员）协同工作，根据单一提示词自主构建软件。
- **资源:**
  - [LLM Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/) (Lilian Weng): 关于智能体规划、内存和工具使用的权威技术剖析。
  - [AutoGPT Documentation](https://docs.agpt.co/): 用于构建自治智能体循环的实用实现指南。

</details>

<details>
<summary><strong>Blackboard Architecture (黑板架构):</strong> 多个专门的子系统协作处理一个共享的数据结构（黑板），这在 AI 和模式识别中非常常见。</summary>

一种早期的 AI 模式，用于处理语音识别或蛋白质结构建模等复杂、非确定的问题。它有一个全局中心内存空间（黑板）和一系列独立、专门的知识库（“专家”）。不存在规定操作序列的中央控制流。每个专家不断监控黑板。当专家发现它可以处理的数据时，它会向黑板更新部分解决方案，从而触发其他专家贡献，直至最终方案产生。

- **示例:**
  - [stanfordnlp/CoreNLP](https://github.com/stanfordnlp/CoreNLP): 斯坦福核心 NLP 应用使用了一个深受黑板模式启发的流水线。共享的 `Annotation` 对象（即黑板）被传递并被独立的标注器（词性标注、命名实体识别、句法分析专家）修改，以构建完整的语言分析结果。
- **资源:**
  - [Blackboard System](https://en.wikipedia.org/wiki/Blackboard_system): 对控制、黑板和知识源的概述。
  - "Pattern-Oriented Software Architecture, Volume 1" (POSA): 包含黑板模式最权威的正式定义。

</details>

<details>
<summary><strong>Rule-Based System Architecture (基于规则的系统架构):</strong> 这是一个应用于专家系统的知识库。其推理引擎会应用一系列规则从中得出结论。</summary>

经典符号 AI 的核心模式，通常被称为“专家系统”。它严格分离了业务逻辑（规则）和执行控制（推理引擎）。领域专家定义一个广泛的、包含“如果-那么” (IF-THEN) 事实及条件的知识库。推理引擎随后根据这些规则动态评估入站数据，触发适用规则以推导出新事实或执行动作。它非常适用于决策逻辑必须严格可审计的复杂合规、医疗诊断和自动核保系统。

- **示例:**
  - [eslint/eslint](https://github.com/eslint/eslint): 纯粹的规则驱动应用。核心引擎根据数百个独立的、可插拔的规则评估抽象语法树 (AST)，从而推断代码质量并触发警告。
  - [Yelp/elastalert](https://github.com/Yelp/elastalert): 该应用通过根据用户定义的大量规则字典持续评估数据，向 Elasticsearch 产生的异常发出警告。
- **资源:**
  - [Rule-Based System](https://en.wikipedia.org/wiki/Rule-based_system): 关于推理引擎和专家系统的概述。
  - "Expert Systems: Principles and Programming" (Joseph C. Giarratano 和 Gary D. Riley): 设计基于规则的架构的经典教科书。

</details>

<details>
<summary><strong>Closed-Loop Control Architecture (Process Control) (闭环控制架构 / 过程控制):</strong> 通过传感器和执行器（例如恒温器、巡航控制以及嵌入式系统）来管理物理工程的过程。</summary>

一种绑定物理世界的架构，在一个持续、无限的循环中运行，以维持所需的物理状态。它依靠传感器读取系统的当前状态，将读数与设定的期望值进行比较以计算误差值，并立即向物理执行器发送纠正命令。系统完全依赖此持续反馈循环来适应外部物理干扰。它是工业机器人、自动驾驶车辆和空调系统 (HVAC) 的主导软件架构。

- **示例:**
  - [ArduPilot/ardupilot](https://github.com/ArduPilot/ardupilot): 非常流行的开源自动驾驶软件套件，精确地围绕高频闭环 PID 控制器构建，以维护飞行器的稳定性。
  - [commaai/openpilot](https://github.com/commaai/openpilot): 开源自动驾驶应用，使用闭环控制架构根据实时摄像头和雷达反馈持续调整车辆的转向和加速。
- **资源:**
  - [Control Theory](https://en.wikipedia.org/wiki/Control_theory): 介绍反馈循环基础数学和核心概念的文章。
  - "Feedback Control of Dynamic Systems" (Gene F. Franklin): 详述闭环软硬件系统设计的标准工程教材。

</details>

<details>
<summary><strong>Real-Time Architecture (实时架构):</strong> 响应时间是至关重要的，并且必须得到保证的系统（例如：航空电子设备、医疗设备）。</summary>

一种由确定的、严格的时间约束而非单纯吞吐量定义的架构。在实时架构中，哪怕计算出正确的响应结果，但如果响应过时，也会被视为整个系统的彻底失败。为了满足这些严格的反应期限，这类系统使用专门的实时操作系统 (RTOS)，避开不可预测垃圾回收带来的停顿，并严格划分内存。它们对于心脏起搏器、防抱死刹车系统和轨道卫星等安全关键型硬件至关重要。

- **示例:**
  - [PX4/PX4-Autopilot](https://github.com/PX4/PX4-Autopilot): 针对 RTOS（如 NuttX）量身打造的开源飞行控制应用，以确保无人机电机控制的严格确定性时序。
  - [nasa/cFS](https://github.com/nasa/cFS): 由 NASA 开发的核心飞行系统 (Core Flight System)，是一个被真实太空任务使用的实时软件框架，在处理延迟可能导致任务失败的任务中使用。
- **资源:**
  - [Real-Time Computing](https://en.wikipedia.org/wiki/Real-time_computing): 对硬实时 (hard)、准实时 (firm) 和软实时 (soft) 约束的概述。
  - "Real-Time Systems Design and Analysis" (Phillip A. Laplante): 指导如何在软件架构中构建确定性的教材。

</details>


### 系统迁移与混合拓扑

用于桥接不同计算环境或逐步淘汰单体老旧系统的转换或复合架构模型。

<details>
<summary><strong>Strangler Fig Architecture (绞杀者模式):</strong> 通过在旧系统周围构建新系统，并逐步将功能重定向，从而逐步替换老旧系统。</summary>

一种用于安全现代化陈旧单体系统 (Legacy) 的迁移模式。在老旧应用前端放置一个路由外观。随着开发团队构建新的、现代化的服务，外观层拦截请求并将其重定向到新服务，同时将剩余的未迁移流量导向老旧系统。随着时间推移，新系统在旧系统周围“生长”，接管其所有功能，直至老旧系统可以被安全退役。

- **示例:**
  - *示例说明:* Strangler Fig 是一种应用于现有私有企业代码库的过渡性迁移策略，而非一个独立的最终架构状态。因为它描述了重写和从特定老旧系统重定向流量的动态过程，没有原生构建为“绞杀者应用”的单一开源业务应用。不过，以下示例展示了实现细节：
    - [aws-samples/strangler-fig-pattern-using-amazon-api-gateway](https://github.com/aws-samples/strangler-fig-pattern-using-amazon-api-gateway): 展示如何使用 API Gateway 逐步在老旧服务和现代服务之间重定向流量的实用实现。
- **资源:**
  - [StranglerFigApplication](https://martinfowler.com/bliki/StranglerFigApplication.html) (Martin Fowler): 创造该术语并描述此迁移策略的原始文章。
  - [Legacy Architecture Modernization](https://www.redhat.com/en/topics/cloud-native-apps/what-is-strangler-pattern): 红帽 (Red Hat) 关于绞杀者模式实现步骤、优势和风险的详细指南。

</details>

<details>
<summary><strong>Sidecar Architecture (边车架构):</strong> 部署在主应用旁的辅助组件，通常处理像日志、安全或网络等此类外部任务。</summary>

边车架构将支持性的基础设施任务从主应用核心逻辑中分离出来。辅助组件（即边车）在与主应用相同的生命周期中运行，通常位于同一个容器 Pod 或物理服务器中。主应用不需要知道辅助组件的存在。它被广泛用于将监控代理、授权层、日志聚合器或微服务代理连接到复杂的分布式系统。

- **示例:**
  - [envoyproxy/envoy](https://github.com/envoyproxy/envoy): 一个高性能代理，最常作为边车部署在微服务旁边，处理所有进出的网络流量、遥测和安全性。
  - [dapr/dapr](https://github.com/dapr/dapr): 分布式应用运行时。它通过边车模式工作，为应用提供即时状态管理、发布/订阅和秘密（Secret）管理等能力，而无需应用引用库。
- **资源:**
  - [Sidecar Pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/sidecar): 微软关于分离基础设施关注点和通过边车扩展遗留应用的指南。

</details>


### 韧性与容错模式

旨在通过优雅地降级功能而非由于级联网络故障或过载而崩溃，从而维护系统可用性的协议。

<details>
<summary><strong>Bulkhead Pattern (隔板模式):</strong> 隔离系统组件。这样如果一个组件发生故障，其他组件仍能继续运行。其概念源于船舶的隔板（舱室）。</summary>

一种旨在防止级联故障的隔离模式。通过在物理或逻辑上划分消费资源（如线程池、内存和连接），它确保一个区域的过载或失败不会消耗掉整个系统的所有可用资源。例如，如果后端一个特定的支付服务变慢并占用了所有可用线程，隔板将确保单独的目录查询服务仍然拥有自己的独立线程池供正常操作。

- **示例:**
  - [Netflix/Hystrix](https://github.com/Netflix/Hystrix): (虽然已进入维护模式但仍具教育意义) 这是一个延迟和容错库，通过线程池划分提供了工业级的隔板模式实现。
  - [resilience4j/resilience4j](https://github.com/resilience4j/resilience4j): 现代 Java 容错库。它提供了强大的隔板模块，允许开发人员为并发调用设置限制并进行隔离。
- **资源:**
  - [Bulkhead architecture pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/bulkhead): 详细说明线程池隔离、服务分区和资源管理的指南。
  - [Fault Tolerance Patterns](https://www.architecture-patterns.net/fault-tolerance/): 关于构建弹性分布式系统、隔板模式和避免全系统故障的更广泛分析。

</details>

<details>
<summary><strong>Circuit Breaker (熔断器):</strong> 核心设计模式，防止故障级联并给子系统恢复的时间。</summary>

分布式系统的安全阀。由于分布式网络中的故障通常是暂时性的，快速重复尝试调用失败的服务会加重其负担，甚至可能拖垮调用者。熔断器会监控失败情况并在达到阈值时“跳闸”（Trip），阻止后续所有调用。处于“开启”状态时，它会立即向调用者返回预定义的错误值，让发生故障的服务有时间恢复，而不是被更多请求淹没。

- **示例:**
  - [resilience4j/resilience4j](https://github.com/resilience4j/resilience4j): 目前最先进的熔断器模式实现库，功能包括基于计数的浮动窗口和失败阈值判定。
  - [go-kit/kit](https://github.com/go-kit/kit): 为 Go 开发者提供了熔断器中间件，强调作为处理网络调用的核心、组合式步骤来构建它。
- **资源:**
  - [CircuitBreaker](https://martinfowler.com/bliki/CircuitBreaker.html) (Martin Fowler): 关于由于快速重发失败请求而导致软件雪崩的风险分析。
  - [Making the Netflix API Resilient](https://netflixtechblog.com/making-the-netflix-api-resilient-73f1396b7975): 全面解读 Netflix 如何利用熔断器来维护其千万亿级流媒体服务的高可用。

</details>

<details>
<summary><strong>Retries and Backoff Patterns (重试与退避模式):</strong> 核心架构设计，在故障后重新尝试失败的操作之前增加延迟。</summary>

一种利用分布式网络系统中许多故障都是瞬时故障（如网络闪断或服务器瞬间在高负载下扩缩容）这一事实的策略。与其在第一次失败时就报错，系统会尝试重新连接。**退避 (Backoff)** 指在每次重试间增加延迟时间（通常是指数级增加），以给予下游组件处理积压和消减流量高峰的机会，防止所谓的“惊群效应”。

- **示例:**
  - [grpc/grpc-go](https://github.com/grpc/grpc-go): gRPC 的核心 Go 实现，内置了复杂的退避服务，能处理连接重试策略，并带有抖动 (Jitter) 功能以分散重试请求。
  - [cockroachdb/cockroach](https://github.com/cockroachdb/cockroach): 该数据库广泛采用指数级退避重试来管理高度分布式的分布式锁和副本一致性冲突。
- **资源:**
  - [Exponential Backoff and Jitter](https://aws.amazon.com/blogs/architecture/exponential-backoff-and-jitter/) (AWS): 论述添加随机“抖动”如何极大提高高规模并发系统中备份恢复性能的文章。
  - [Retries and Timeouts](https://www.sqlite.org/howtocorrupt.html): 介绍如何利用重试机制来保证即使由于其他分布式节点写入而导致锁定时，数据写入依然具有鲁棒性。

</details>

<br>

[![回到顶部](https://img.shields.io/badge/-回到顶部-6f42c1?style=for-the-badge&logoColor=white)](#目录)


## 第二层：企业集成模式

集成是让不同服务和旧系统相互对话的“粘合剂”。本层不关注内部逻辑，而是处理服务之间的数据移动、转换和同步。它提供了消息传递、网关和分布式任务（Saga）模式，确保网络延迟或局部故障不会破坏整个企业系统的运行。

### 消息通道模式

核心结构，定义了应用程序注入和使用解耦信息的虚拟路径。

<details>
<summary><strong>Point-to-Point Channel (点对点通道):</strong> 分发消息，确保任何给定消息只有一个接收者消费。一旦被读取，消息将从通道中移除。</summary>

一种用于分发离散工作单元的消息传递拓扑。发送者将消息放入特定通道（通常是队列）。虽然多个并发接收者（工作进程）可以监听同一通道，但通道确保只有一个接收者能成功消费并处理任何给定的消息。这不仅支持了负载均衡，还通过将任务分配给可用资源实现了高效的任务分发。

- **示例:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): 大量依靠点对点通道（通过 Sidekiq 和 Redis）将异步的重型后台作业（如媒体处理和联邦推送）分发给单个可用的工作实例。
  - [getsentry/sentry](https://github.com/getsentry/sentry): 核心 Sentry 应用使用点对点任务队列（通过 Celery）将数百万个传入的崩溃报告路由到可用处理器进行存储和聚合。
- **资源:**
  - [Point-to-Point Channel](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PointToPointChannel.html) (Gregor Hohpe): 原始的企业集成模式定义及其中间件实现细节。
  - [RabbitMQ Queues Tutorial](https://www.rabbitmq.com/tutorials/tutorial-two-python): 演示如何跨多个工作进程分配任务（点对点模型）的实践指南。

</details>

<details>
<summary><strong>Publish-Subscribe Channel (发布-订阅通道):</strong> 同时向多个活跃订阅者广播单个事件。</summary>

一种用于事件通知而非任务分发的拓扑。发送者（发布者）向特定主题或通道广播消息。该消息的副本会立即递交给当前正在监听该通道的每一个接收者（订阅者）。它实现了极高的系统解耦，因为发布者不需要知道订阅者的身份或数量，非常适合处理 UI 更新、日志记录和多触点通知。

- **示例:**
  - [discourse/discourse](https://github.com/discourse/discourse): 使用高度活跃的发布-订阅通道（通过 Redis Pub/Sub）向所有并发连接的 Web 客户端广播实时 UI 更新（如新帖子、系统通知）。
  - [RocketChat/Rocket.Chat](https://github.com/RocketChat/Rocket.Chat): 开源通信平台。严重依赖发布/订阅架构（基于 Meteor/DDP 协议）瞬間向房间内的所有活跃用户广播聊天消息。
- **资源:**
  - [Publish-Subscribe Channel](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html) (Gregor Hohpe): 解释发布者与多个接收者之间单向解耦的核心模式定义。
  - [Google Cloud Pub/Sub Overview](https://cloud.google.com/pubsub/docs/overview): 现代云原生发布/订阅架构的应用案例与架构优势。

</details>

<details>
<summary><strong>Dead Letter Channel (死信通道):</strong> 一个专用通道，消息系统将无法成功投递或处理的消息路由至此。</summary>

异步系统的关键错误处理拓扑。当消息遇到终结性错误（如由于逻辑错误达到最大重试次数、由于过期超过生存时间 TTL 或架构验证失败）时，消息中间件会自动将其从活跃队列中移除并路由到特定的死信通道。这允许开发人员对损坏的消息进行事后分析、手动修复并在不干扰主处理流的情况下重新排队。

- **资源:**
  - [Dead Letter Channel](https://www.enterpriseintegrationpatterns.com/patterns/messaging/DeadLetterChannel.html) (Gregor Hohpe): 隔离失败消息以供后续检查的核心逻辑。
  - [Understanding Amazon SQS dead-letter queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues.html): 云架构中实现死信队列的具体配置与实践细节。

</details>

<details>
<summary><strong>Guaranteed Delivery (保证交付):</strong> 使用内置的持久化存储机制，即使系统或网络在投递前崩溃，消息也不会丢失。</summary>

一种在高度不稳定的环境中防止数据丢失的服务质量 (QoS) 拓扑。当发送方发出消息时，消息基础设施会强制将消息写入非易失性的物理磁盘存储，然后才向发送方返回确认成功。如果中间件崩溃，消息仍完整保留在存储中，并在系统恢复在线后立即重新投递。这对于订单处理或金融交易等不可丢失的数据流至关重要。

- **资源:**
  - [Guaranteed Delivery](https://www.enterpriseintegrationpatterns.com/patterns/messaging/GuaranteedMessaging.html) (Gregor Hohpe): 交付安全与系统性能之间的架构权衡及持久化策略。
  - [RabbitMQ Reliability Guide](https://www.rabbitmq.com/docs/reliability): 关于实现发布者确认和磁盘持久化以保证消息交付的技术文档。

</details>


### 消息路由模式

根据上下文、规则或内容决定消息到达最终目的地的具体路径的机制。

<details>
<summary><strong>Content-Based Router (基于内容的路由):</strong> 检查消息内容，并根据该数据将其路由到特定的目标通道。</summary>

消息传递拓扑的逻辑调度台。发送者无需知道具体哪个下游队列应该处理特定任务，只需发布到中央路由器即可。路由器解析传入消息的负载或标头（例如检查“客户级别”或“地区”字段），并根据预定义的逻辑将其重定向到最合适的频道。这简化了发送方的逻辑，并将生产者与消费者的具体类型解耦。

- **示例:**
  - [home-assistant/core](https://github.com/home-assistant/core): 在其事件总线中大量使用基于内容的路由。核心引擎不断评估来自物理传感器的状态更改事件负载，并根据精确数据（例如：如果温度 > 70 度）将其分流到特定的自动化处理通道。
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): 开源 Git 服务。使用基于内容的路由来检查入站 Webhook 的负载内容，并根据事件类型（推送、拉取请求、发布）将其分派给不同的 Runner 队列。
- **资源:**
  - [Content-Based Router](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ContentBasedRouter.html) (Gregor Hohpe): 驱动数据决策的消息路由核心概念。
  - [AWS EventBridge Content Filtering](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-patterns.html): 根据 JSON 负载内容进行事件路由的实践文档。

</details>

<details>
<summary><strong>Message Filter (消息过滤器):</strong> 根据特定标准评估消息，如果不符合要求则将其从通道中丢弃。</summary>

一种保护性的路由机制，防止下游组件被无关数据淹没。过滤器位于通道上方并检查每条通过的消息。如果消息符合过滤标准，则可以无缝通过到达输出通道；如果失败，则消息被悄悄丢弃。该模式被广泛用于日志聚合、安全监控和大规模遥测数据的初步筛选。

- **示例:**
  - [fail2ban/fail2ban](https://github.com/fail2ban/fail2ban): 这是一个极具攻击性的消息过滤器安全应用。它持续解析海量的服务器日志文件，悄悄丢弃正常流量日志，仅允许并针对指示恶意身份验证失败的日志行执行操作。
  - [pi-hole/pi-hole](https://github.com/pi-hole/pi-hole): 一个网络级应用。纯粹作为 DNS 请求的消息过滤器，悄悄丢弃（并重定向至黑洞）与已知广告域匹配的查询，而允许合法的 Web 请求通过。
- **资源:**
  - [Message Filter](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Filter.html) (Gregor Hohpe): 从数据流中消除不需要的消息的模式正式定义。

</details>

<details>
<summary><strong>Recipient List (接收者列表):</strong> 检查传入消息，并将其转发给动态确定的接收者列表。</summary>

一种智能、精准的广播模式。不同于标准的发布-订阅频道（盲目广播给所有听众），接收者列表会根据消息内容或外部状态，在运行时动态计算“谁”应该接收消息。这是一种有针对性的分散-聚合机制，常用于需要根据用户偏好动态调整交付方式的通知系统和复杂的多级审批工作流。

- **示例:**
  - [novuhq/novu](https://github.com/novuhq/novu): 开源通知基础设施应用。它通过接收单一的入站触发器（如“重置密码”），并根据用户偏好表动态计算正确的交付通道（电子邮件、短信、推送等），原生实现了接收者列表模式。
- **资源:**
  - [Recipient List](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RecipientList.html) (Gregor Hohpe): 动态、选择性广播背后的架构理论与设计重点。

</details>

<details>
<summary><strong>Splitter (消息分解器):</strong> 拆分单一组合消息为多个独立消息以支持独立处理。</summary>

一种用于并行化工作和处理大型数据负载的结构模式。当系统收到大型批处理文件或包含数十个子条目的订单时，由单个工作进程处理整个块是低效的。分解器拦截组合消息，将其拆分为离散的原子单元，并将每个单元作为独立消息发布到处理队列中，从而允许一个并发工作进程池同时处理这些部分。

- **示例:**
  - [airbytehq/airbyte](https://github.com/airbytehq/airbyte): 开源数据集成平台。使用拆分机制获取海量的批量 API 响应（如拉取整个 CRM 数据库），并将其拆分为独立记录的 JSON 消息，以便进行独立的下游处理和正规化。
- **资源:**
  - [Splitter Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Sequencer.html) (Gregor Hohpe): 分解组合负载以提高并发性的核心逻辑。

</details>

<details>
<summary><strong>Aggregator (消息聚合器):</strong> 收集并合并多个相关的、较小的消息为一个单一的详细消息。</summary>

分解器的功能逆过程。这是一种高度有状态的路由模式，它缓冲传入的消息，直到满足特定的完成条件（例如：等待订单的所有 5 个条目全部到达，或者等待一个 10 秒的时间窗口关闭）。一旦条件触发，它会将缓冲的消息编译为单一、统一的负载并发送到下游。它常用于批量数据库写入和合并来自多个下游服务的 API 响应。

- **示例:**
  - [prometheus/prometheus](https://github.com/prometheus/prometheus): 时序监控应用使用聚合架构来每秒摄取数千个独立的遥测指标，在将其写入磁盘前将其缓冲并压缩为极其高效的块。
  - [getsentry/sentry](https://github.com/getsentry/sentry): Sentry 依靠复杂的聚合逻辑，将来自损坏客户端应用的数千个完全相同的独立错误消息分组为用户面板上一个单一、连贯的“Issue”。
- **资源:**
  - [Aggregator Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Aggregator.html) (Gregor Hohpe): 管理状态和关联 ID 以重构消息的策略。

</details>

<details>
<summary><strong>Resequencer (重排器/重序器):</strong> 缓冲乱序消息，并按正确的原始顺序将它们发布到下游。</summary>

一种用于校正分布式系统中由于网络延迟或并发导致的时间顺序问题的有状态缓冲区。由于消息到达目的地的时间可能与生成的原始顺序不同，重排器会暂时在内存中保持入站消息序列。它检查负载上的序列 ID 或时间戳，并在且仅在满足预定的顺序链时，才按原定时间顺序将其分发到最终目的地。

- **示例:**
  - [jitsi/jitsi-videobridge](https://github.com/jitsi/jitsi-videobridge): WebRTC 兼容的视频路由。其内部架构高度依赖实时重排缓冲区来捕捉高度碎片化的入站 UDP 视频包，并在渲染视频帧给最终用户前将其重新排列回正确的序列。
- **资源:**
  - [Resequencer Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Resequencer.html) (Gregor Hohpe): 序列间隙管理和时间缓冲背后的理论。

</details>

<details>
<summary><strong>Routing Slip (路由单):</strong> 在消息负载中附加一系列路由指令，以便消息知晓下一个目的地。</summary>

一种分布式协调模式，行程单随数据一起传输。与中央控制器协调复杂流转不同，初始发送者在消息本身附带一份处理步骤清单（路由单）。当一个处理节点完成任务时，它检查消息上的路由单，确定下一个目的地并直接转发。这显著降低了由于中央协调器瓶颈导致的网络拥塞。

- **示例:**
  - [Netflix/conductor](https://github.com/Netflix/conductor): 尽管作为协调器运行，其 Task 执行模型模仿了路由单范式：状态和顺序路由上下文随任务一起传递，因此分布式执行节点可以知晓当前的流水线状态，而无需平凡查询中央数据库。
- **资源:**
  - [Routing Slip Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RoutingTable.html) (Gregor Hohpe): 解耦工作流编排与逻辑实现的正式定义。

</details>

<details>
<summary><strong>Throttler (节流阀):</strong> 限制消息流向接收者的速率。以防止其过载</summary>

一种流量控制机制，通常用于强制执行服务质量 (QoS) 或服务水平协议 (SLAs)。如果发送方的消息以超高峰值速率到达，节流阀会对其进行缓冲，并以恒定的、受控的速率（例如每秒 100 条）将其释放到后端的脆性系统（如陈旧的数据库或高带宽消耗的 API）。这保护了关键系统免受意外流量突发的破坏。

- **示例:**
  - [discourse/discourse](https://github.com/discourse/discourse): 实现了多层节流逻辑，以限制新帖子发布和 API 请求的频率，有效防止恶意爬虫或由于瞬间突发事件拖垮底层的 Ruby/Postgres 环境。
- **资源:**
  - [Throttling pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/throttling) (Microsoft Azure): 构建韧性分布式系统时实施速率限制和节流的实践指南。

</details>

<details>
<summary><strong>Load Balancer (负载均衡器):</strong> 分发入站消息到多个接收者实例以优化资源并平衡负载。</summary>

水平扩展架构的核心基础设施。它位于服务集群的前方，作为唯一的流量入口，根据预定义的算法（如轮询 Round Robin、最少连接或地理位置）将请求分发给各个健康的服务实例。如果某个接收器失败，负载均衡器会自动检测并将其从路由池中剔除，确保整个系统的高可用性。

- **示例:**
  - *示例说明:* 负载均衡器通常被视为独立的基础设施组件（如 HAProxy 或 Nginx），应用通常部署在它们后。
    - [terraform-google-modules/terraform-google-lb](https://github.com/terraform-google-modules/terraform-google-lb): 提供在 Google Cloud 平台上自动化配置高效负载均衡架构的基础设施即代码模组。
- **资源:**
  - [What is Load Balancing?](https://www.cloudflare.com/learning/performance/what-is-load-balancing/): Cloudflare 官方解释。涵盖了 L4 和 L7 负载均衡算法及其实际应用场景。

</details>


### 消息转换模式

在消息负载发送到接收者之前，通过更改、丰富或标准化负载来解耦发送者与接收者的数据格式。

<details>
<summary><strong>Envelope Wrapper (信封包装器):</strong> 在不改变原始负载的情况下，将现有数据包装在符合标准的、标准化的消息信封中。</summary>

该模式用于在不修改原始负载本身的情况下，将其封装在消息基础设施所需的标准化元数据结构（信封）中。信封通常包含路由信息、签名、关联 ID 或安全属性。这允许底层传输层成功地路由和跟踪消息，而其本质上完全不需要理解信封内部的业务数据负载。

- **示例:**
  - [matrix-org/synapse](https://github.com/matrix-org/synapse): Matrix 联合协议实现。它将端到端加密的聊天数据报文（Payload）封装在标准化的 JSON 结构信封中，以便跨不同服务器节点的联邦网络进行路由。
  - [letsencrypt/boulder](https://github.com/letsencrypt/boulder): 证书签发应用。将其证书签名请求 (CSR) 封装在 JWS (JSON Web Signature) 信封中，确保在传输过程中的完整性和不可篡改性。
- **资源:**
  - [Envelope Wrapper](https://www.enterpriseintegrationpatterns.com/patterns/messaging/EnvelopeWrapper.html) (Gregor Hohpe): 用于封装业务数据的各种技术实现方案与权衡。

</details>

<details>
<summary><strong>Content Enricher (内容富化器):</strong> 拦截消息并访问外部数据源，追加缺失信息后再发送。</summary>

常用于源系统由于极简设计导致数据不完整的情况。中间件拦截消息，提取关键标识符（如 `user_id`），查询外部数据库或第三方 API 以检索该实体的完整上下文（如电子邮件、会员计划状态或历史偏好），将其合并到负载中，然后才分发到最终目的地。这能显著减轻源系统的逻辑深度。

- **示例:**
  - [getsentry/sentry](https://github.com/getsentry/sentry): 错误监控应用。它拦截原始的内存崩溃转储，通过查询已知的元数据服务追加：地理位置、用户详细画像和特定的库版本信息。
  - [matomo-org/matomo](https://github.com/matomo-org/matomo): 网站分析应用。在持久化之前的转换流水线中，它会根据入站 IP 地址查询 GeoIP 数据库，从而富化访客的地理位置数据。
- **资源:**
  - [Content Enricher](https://www.enterpriseintegrationpatterns.com/patterns/messaging/DataEnricher.html) (Gregor Hohpe): 拦截、访问外部资源并合并数据的架构原理。

</details>

<details>
<summary><strong>Content Filter (内容过滤器):</strong> 隔离移除消息中不必要或敏感的数据以简化传输逻辑或增强安全性。</summary>

内容富化器的逆模式。它从原始消息中主动移除特定的非必要字段。其目的通常是为了减少带宽（数据最小化原则）或提高合规性及安全性（例如在将日志发送到外部 S3 存储前，移除其中的信用卡号、密码或个人敏感信息 PII）。

- **示例:**
  - [getsentry/sentry](https://github.com/getsentry/sentry): 在客户端 SDK 与服务器接收端两处都使用了严格的内容过滤器。通过“数据过滤规则（Data Scrubbing）”在传输前识别并剥离错误信息中可能携带的密码或令牌字段。
  - [nextcloud/server](https://github.com/nextcloud/server): 在其外部 API 返回数据前，使用内容过滤器剥离所有内部文件物理路径或特定的数据库映射 ID，以防止内部服务器结构泄露。
- **资源:**
  - [Content Filter](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ContentFilter.html) (Gregor Hohpe): 精简与保护数据负载。

</details>

<details>
<summary><strong>Claim Check (提取码/票据模式):</strong> 存储大型消息负载到外部数据库。仅通过消息总线传递一个简短的唯一标识符。</summary>

该模式旨在防止大型二进制对象（如高清视频、超大图像或日志压缩包）阻塞低吞吐量的消息 Broker 通道。发送方将大文件上传到对象存储（如 AWS S3），并将生成的下载凭据/ID（Claim Check）放到队列中。接收方收到 ID 后从持久存储中自主拉取数据。这保证了消息队列的轻量与高效。

- **示例:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): 当用户上传媒体附件时，系统将文件存入云存储，而仅传递轻量的 UUID 通过 Redis 队列进行后续的转码异步任务处理。
- **资源:**
  - [Claim Check Pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/claim-check): 构建高性能分布式系统时解决大型消息投递问题的最佳实践指南。

</details>

<details>
<summary><strong>Normalizer (规整器):</strong> 这是一个数据转换器。它能将异构的消息格式转换为一个标准的消息格式。以便接收器进行处理。</summary>

一种专门用于集成多个“各言其辞”的服务组件的模式。规整器识别入站消息的不同格式（如 XML、JSON、协议缓冲区或专有 CSV），并将它们映射到一个统一的、全企业通用的规范数据模型中。这消除了下游接收器处理数十种格式变体的开发成本。

- **示例:**
  - [airbytehq/airbyte](https://github.com/airbytehq/airbyte): 能接入几百个不同的数据源。每个连接器都作为规整器，将来自 Salesforce、GitHub 或 Zendesk 的异构 API 响应翻译为标准的 JSON 记录格式存入数据湖。
  - [huginn/huginn](https://github.com/huginn/huginn): 该应用允许创建从多样化的 Web 钩子、网页和 RSS 源抓取数据的 Agent。其核心架构能将这些不规律的数据统一规整为平台内部的标准事件格式。
- **资源:**
  - [Normalizer](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Normalizer.html) (Gregor Hohpe): 异构数据转换架构的基础。

</details>


### 消息端点模式

连接应用程序内部代码与外部消息传递系统的接口，规定了注入与消费数据的精确行为。

<details>
<summary><strong>Polling Consumer (轮询式消费者):</strong> 主动定期检查频道，看看是否有消息被分发。以便检索</summary>

这是一种由接收器（Consumer）主控的模式。消费者按需或定时（例如每 500 毫秒一次）轮询消息频道。这为受限的应用代码提供了卓越的流控能力：它永远不会由于消息过多而崩溃，因为它只在由于负载允许时才会请求消息。然而，该模式由于非连续性检查会引入显著的处理延迟，并由于频繁的“空转”请求而浪费 CPU 周期。

- **示例:**
  - [discourse/discourse](https://github.com/discourse/discourse): 其后台作业框架 Sidekiq 采用长轮询模式不断检查 Redis 列表，以获取需要通过异步执行的延迟任务（如奖章授予或摘要邮件发送）。
- **资源:**
  - [Polling Consumer Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PollingConsumer.html): 轮询频率与处理实时性之间的架构平衡方案。

</details>

<details>
<summary><strong>Event-Driven Consumer (事件驱动型消费者):</strong> 主动、实时反应式操作。消费者的反应根据消息推送频道的情况而定。一旦有消息推送，该消费者就会进行处理。</summary>

一种典型的“推（Push）”模型 point-to-point 连接。消费者进程保持挂起，直至消息 Broker 主动为其注入一条消息，从而立即触发一个回调函数或线程生命周期。这种模式能实现最低的处理延迟（毫秒级），并由于在空闲时不消耗 CPU 轮询周期而极为高效，但它要求消费者必须具备应对突发瞬时流量峰值的能力。

- **示例:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): 其入站钩子及其通知子系统完全。基于事件驱动模式构建：一旦外部消息到达 API Gateway 或 Socket，会立即唤醒对应的协程处理该消息，而非定时检查数据库。
- **资源:**
  - [Event-Driven Consumer](https://www.enterpriseintegrationpatterns.com/patterns/messaging/EventDrivenConsumer.html) (Gregor Hohpe): 实现实时响应的反应式通信架构设计。

</details>

<details>
<summary><strong>Competing Consumers (竞争消费者模式):</strong> 多个消费者从单一频道消费消息。以此来增加处理量。</summary>

解决大规模分布式系统吞吐量瓶颈的首选模式。多个完全相同的消费者实例同时监听同一个消息频道（通常是一个点对点队列）。消息系统逻辑层确保每一条消息仅会被其中的某 *一个* 消费者成功获取并独占。这允许系统通过简单地启动更多的工作进程副本来线性扩展处理能力，同时通过在处理失败时将消息返回队列实现了卓越的故障冗余。

- **示例:**
  - [getsentry/sentry](https://github.com/getsentry/sentry): 维护着一个庞大的、由上百个 Celery 工作进程实例组成的资源池。它们“竞争”同一个中央任务队列的处理权，从而能跨计算节点并行消化每秒数以万计的错误报告。
- **资源:**
  - [Competing Consumers Pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/competing-consumers): 云环境中实现作业排队、工作负载均衡以及处理节点弹性扩缩容的深度指南。

</details>

<details>
<summary><strong>Message Dispatcher (消息分发器/调度器):</strong> 一个协调组件。其负责消费消息，并根据情况，将消息分发给多个处理线程或处理器。进一步处理。</summary>

一个位于外部消息系统与应用核心执行逻辑之间的协调层。它首先从公共频道消费所有入站消息，并根据内部资源可用性或特定的消息优先级，动态地将每一条消息指派给内部的一个专用工作线程或特定的处理器逻辑。这不仅保持了外部连接逻辑的单一性，还通过负载均衡优化了内部多核处理器的利用率。

- **示例:**
  - [Netflix/conductor](https://github.com/Netflix/conductor): 其核心控制器充当消息调度器。它从工作队列拉取待处理任务，并根据工作流图定义，将其精确分发到专门负责该任务类型的外部分布式工作节点上。
- **资源:**
  - [Message Dispatcher](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageDispatcher.html): 处理高容量点对点消息交付的内部调度逻辑。

</details>

<details>
<summary><strong>Idempotent Receiver (幂等接收器):</strong> 这种模式确保无论同一个消息收到多少次。该模式都会保证一致的操作结果。</summary>

分布式系统中应对“至少一次交付（At-least-once delivery）”语义的必备模式。在网络不稳定或处理超时导致重发的情况下，同一消息可能被递送多次。幂等接收器通过检查消息上的唯一 UUID 或事务 ID，并在执行更新前核对“已处理”状态，从而确保即使消息被重复消费，其最终产生的副作用（如数据库扣款或文件写入）也只发生且仅发生一次。

- **示例:**
  - [cockroachdb/cockroach](https://github.com/cockroachdb/cockroach): 其分布式写操作实现是严格幂等的。每一笔事务都会附带版本戳，数据库接收器会忽略重复的、已根据其版本确定处理完成的写入指令，从而维护集群内的数据零损坏。
- **资源:**
  - [Idempotent Receiver](https://www.enterpriseintegrationpatterns.com/patterns/messaging/IdempotentReceiver.html): 关于解决重复消息投递导致的逻辑不一致和数据双重入账的技术实现。

</details>

<details>
<summary><strong>Transactional Outbox Pattern (事务性发件箱模式):</strong> 在同一数据库事务中。通过将消息保存到特定的“发件箱（outbox）”表中，确保数据库更新与发出消息之间的原子性。</summary>

一种用于在没有两阶段提交 (2PC) 的情况下保持服务间最终一致性的数据同步模式。当服务更新自己的数据库时，它会在同一个数据库事务中，在对应的 `outbox` 表中插入一条消息记录。一个独立的后台过程会监控该表，并在检测到记录后可靠地将其发布到最终的消息 Broker。这消除了数据库已更新但消息未发出的各种“静默失败”可能性。

- **示例:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): 提供了完整的 Spring Boot 发件箱模式实现。它在处理客户订单的同时写入表记录，确保后续的任务微服务定能收到订单创建成功的事件通知。
- **资源:**
  - [Transactional Outbox Pattern](https://microservices.io/patterns/data/transactional-outbox.html): 微服务环境下实现跨进程通信原子性的标准模式定义。

</details>


### 消息管理与维护模式

旨在管理、监控和动态测试生产环境中流经集成系统的流量的运维模式。

<details>
<summary><strong>Control Bus (控制总线):</strong> 一个用于系统管理的特定通讯。它负责在系统组件之间传输管理消息。以改变系统的工作方式等。</summary>

一种管理大规模分布系统的“后门”通信层。它严格独立于传输业务数据的“数据总线（Data Bus）”。架构师通过控制总线向运行中的各个服务节点发送特定的管理指令，例如：动态调整连接池大小、启用/禁用特定的路由过滤器、请求实时的健康报告或在不下线应用的情况下分发新的配置属性。

- **示例:**
  - [istio/istio](https://github.com/istio/istio): Istio 的控制平面（Control Plane）本质上就是一个极其复杂的控制总线架构。它通过下发 xDS 策略指令实时更改全球数千个 Enovy 数据平面代理的路由规则、熔断阈值和安全设置。
- **资源:**
  - [Control Bus Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ControlBus.html): 管理分布式流水线组件运行状态的解耦式架构。

</details>

<details>
<summary><strong>Detour (迂回路由):</strong> 根据特殊的预定义条件，临时地绕道并将消息转发到一个特定的处理节点上。</summary>

这种模式用于临时性地干预消息流向。例如，对于需要深度安全审计的特定账户交易，或者是由于需要对特定地区的流量进行 A/B 测试或灰度发布。它允许系统在检测到符合路由单定义之外的特殊标头时，将消息在到达主接收者前，先透明地“绕道”经过一个特定的验证或处理服务，处理完后再返回原路由路径。

- **示例:**
  - [envoyproxy/envoy](https://github.com/envoyproxy/envoy): 广泛利用迂回过滤机制，根据请求中的 HTTP 标头将一小部分特定流量重定向到 Shadow（阴影）集群进行生产环境下的数据采集和性能测绘。
- **资源:**
  - [Detour](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Detour.html): 用于测试、验证与监控的入站消息流临时干预逻辑。

</details>

<details>
<summary><strong>Message Store (消息存储模式):</strong> 主动捕捉在消息通道流过的每一条信息，并将其存入一个持久化的数据库。以便后续进行审计、报表分析或异常排查。</summary>

一种高度可见的运维模式。它在消息通过路由器或中转站时异步地捕获并归档每一条原始报文。这不同于发送方的持久化保证，消息存储库作为一个宏观层面的档案库，不仅能支持法务级别的审计追踪，还能支持离线的批处理分析，并在下游系统崩溃后，根据存档重新回放（Replay）特定时间段的所有消息以完成数据恢复。

- **示例:**
  - [grafana/loki](https://github.com/grafana/loki): 作为一个横向关注点集成的系统，它专门针对大规模分布式环境中的“消息存储”场景设计，捕捉所有容器的 stdout 并允许通过关联 ID 高效率地检索历史流。
- **资源:**
  - [Message Store Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageStore.html): 在解耦的异步系统中维护数据完整性与可追溯性的审计基础架构。

</details>

<details>
<summary><strong>Smart Proxy (智能代理):</strong> 自动处理请求与响应之间的关联 ID。以此来让发送方能准确识别对应请求的回复。</summary>

在处理大量异步请求-响应通信时，由于多条回复可能乱序到达，发送方无法知晓哪条回复对应哪个请求。智能代理作为一个透明的中介层，它自动在入站请求上注入唯一的关联 ID，并跟踪这些 ID 的生命周期。当相应的响应到达时，代理利用该 ID 将回复精确地路由回正在阻塞等待的对应原始会话，从而在异步基础设施上模拟了简单的同步语义。

- **示例:**
  - [istio/istio](https://github.com/istio/istio): 控制平面中的各种适配器模块充当智能代理，在处理来自数千个 Sidecar 的遥测数据上报时，负责将复杂的异步身份认证回调与其原始的控制平面请求进行精密的关联映射。
- **资源:**
  - [Smart Proxy](https://www.enterpriseintegrationpatterns.com/patterns/messaging/SmartProxy.html): 管理异步响应关联、处理连接超时及保证事务完整性的中间层设计。

</details>

<details>
<summary><strong>Test Message (测试消息模式):</strong> 发送特殊的测试负载到生产环境的消息通路。以此来自动验证各组件及其路径的健康与连通性。</summary>

一种持续交付与自动化运维的主动手段。通过向生产环境的消息网格定时注入一种带有“测试”标记的特殊消息负载（类似于网络探测包 Ping），该消息会按原定路由经过所有真实节点。特定的终点组件或测试 Agent 会捕捉到该消息并上报执行时长和成功率，同时确保这些测试数据不会被写入生产业务数据库。它对验证复杂的发布策略和防火墙规则变更极为有效。

- **示例:**
  - [netflix/zuul](https://github.com/netflix/zuul): Netflix 的网关框架大量使用这种合成测试流量（Synthetic Traffic）来实时审计其庞大 AWS 区域间路由配置的连通性能，并作为自动扩缩容的决策参考。
- **资源:**
  - [Test Message Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/TestMessage.html): 在大规模关键任务系统中实现“金丝雀”观测与端到端健康监测的技术实现。

</details>

<details>
<summary><strong>Channel Purger (频道扫描程序/清道夫):</strong> 一个运维工具。用于从生产环境的频道中快速移除所有残留的消息。以便系统能从一个已知干净的状态开始运行。</summary>

一种应急处理工具。在由于错误的代码补丁导致队列中积压了数百万条损坏的消息，或者是需要将整个生产环境重置为一致的开发/测试初始状态时，清道夫会直接连接频道，在不关停应用进程的情况下，以前所未有的速度扫描并删除所有存在的活动报文。这对于清理溢出的垃圾队列以防止 Broker 内存耗尽至关重要。

- **资源:**
  - [Channel Purger Architecture](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ChannelPurger.html): 快速重置消息通路、清理数据残留以及维护中间件稳定性所需的运维流水线。

</details>


<br>

[![回到顶部](https://img.shields.io/badge/-回到顶部-6f42c1?style=for-the-badge&logoColor=white)](#目录)



## 第三层：应用架构模式

本层关注单个应用或服务内部的组织方式。其主要目标是将业务逻辑从框架、数据库和 UI 中分离出来。像“整洁架构”或“六边形架构”这样的模式能保持核心代码易于测试，并使得在不改变应用工作方式的情况下更换数据库成为可能。

### 表现层 / UI 架构模式

规定用户界面如何组织以及它们如何与底层业务逻辑通信的模式。

<details>
<summary><strong>Model-View-Controller (MVC):</strong> 将用户界面分为模型 (Model - 数据)、视图 (View - 展示) 和控制器 (Controller - 逻辑) 三个部分。</summary>

将数据表示与用户交互解耦的经典模式。模型管理数据和业务规则，视图显示信息，而控制器拦截用户输入以更新模型。它是现代 Web 开发的核心，允许用户界面和核心业务逻辑独立演进。

- **示例:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): 在现实世界的服务器端渲染应用中，使用 Ruby on Rails 实现 MVC 模式的主要示例。
  - [moodle/moodle](https://github.com/moodle/moodle): 使用 MVC 架构管理复杂学生数据和课程展示的开源学习平台。
- **资源:**
  - [GUI Architectures](https://martinfowler.com/eaaDev/uiArchs.html) (Martin Fowler): 深入探讨 MVC 及其变体的演变。

</details>

<details>
<summary><strong>Model-View-Presenter (MVP):</strong> 表演者（Presenter）处理所有 UI 逻辑，使视图（View）变为被动的。</summary>

MVC 的衍生模式，其中 Presenter 扮演中间人的角色。在 MVP 中，视图是“被动”的；它不直接监听模型。相反，Presenter 从模型检索数据、进行格式化，并精确指示视图应该显示什么。这通过消除对 UI 框架的直接依赖，增强了 UI 逻辑的可测试性。

- **示例:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): 历史上在其核心 Android Activity 中使用 MVP，以将加密逻辑从系统级 UI 代码中隔离出来。
- **资源:**
  - [Model-View-Presenter](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter): 关于 Supervising Controller 和 Passive View 变体的概述。

</details>

<details>
<summary><strong>Model-View-ViewModel (MVVM):</strong> 支持视图（View）和视图模型（ViewModel）之间的双向数据绑定。</summary>

一种用于数据绑定技术的模式。ViewModel 为视图提供专门的数据模型，包含“视图状态”（如输入验证或按钮状态）。通过双向绑定，UI 的更改会更新 ViewModel，而 ViewModel 的更改会刷新 UI，无需手动操作 DOM 或组件。

- **示例:**
  - [kiwix/kiwix-android](https://github.com/kiwix/kiwix-android): 一个实现 MVVM 的开源离线阅读器，使用 Android 架构组件将库状态绑定到 UI。
  - [Anki-Android/Anki-Android](https://github.com/ankidroid/Anki-Android): 广泛使用的闪存卡应用，使用 MVVM 管理复杂的卡片复习和牌组管理状态。
- **资源:**
  - [WPF Apps With The MVVM Design Pattern](https://learn.microsoft.com/en-us/archive/msdn-magazine/2009/february/patterns-wpf-apps-with-the-mvvm-design-pattern) (Microsoft): 推广 MVVM 的核心文章。

</details>

<details>
<summary><strong>Flux / Redux Architecture:</strong> 用于客户端应用程序的单向数据流。</summary>

一种用于管理单页面应用 (SPA) 状态的模式。它强制执行严格的单向数据循环：动作（Actions）发送到中央调度器（Dispatcher），调度器更新存储（Store），随后存储通知视图重新渲染。这种显式且顺序的状态管理实现了可预测的调试和状态跟踪。

- **示例:**
  - [zulip/zulip-mobile](https://github.com/zulip/zulip-mobile): 在移动客户端中使用 Redux 为所有聊天消息和用户在线状态管理单一事实来源。
  - [wordpress-mobile/WordPress-Android](https://github.com/wordpress-mobile/WordPress-Android): 采用基于 Flux 的架构 (FluxC) 来管理移动应用中的内容同步。
- **资源:**
  - [Flux Concepts](https://facebookarchive.github.io/flux/docs/in-depth-overview/): 定义单向数据流的原始文档。

</details>

<details>
<summary><strong>Micro Frontends Architecture (微前端架构):</strong> 将 Web 应用程序拆分为独立的各种前端模块。</summary>

一种将微服务扩展到前端的组织和技术模式。将一个大型应用分解为由不同团队开发和部署的、基于功能的独立模块。这些模块在运行时进行集成，为用户呈现无缝的体验。

- **示例:**
  - [openmrs/openmrs-esm-core](https://github.com/openmrs/openmrs-esm-core): 开源医疗记录系统的核心前端，基于微前端架构构建，允许模块化的医院个性化定制。
- **资源:**
  - [Micro Frontends](https://martinfowler.com/articles/micro-frontends.html) (Cam Jackson): 关于组合和集成策略的技术指南。

</details>


### 以领域为中心 / 分层架构

定义内部层级的宏观结构，旨在将核心业务领域从基础设施层隔离出来的模式。

<details>
<summary><strong>Hexagonal Architecture (Ports and Adapters) (六边形架构 / 端口与适配器):</strong> 通过端口和适配器隔离核心领域逻辑。</summary>

一种将业务逻辑视为应用核心，并将其与外部关注点隔离的架构风格。通信通过“端口”（接口）进行，而“适配器”负责连接具体技术（如数据库或 API）。这实现了极高的可测试性，并允许在不影响核心业务逻辑的情况下更换具体技术实现。

- **示例:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): 展示了严格的领域隔离和业务逻辑保护的 TypeScript 参考应用。
- **资源:**
  - [Hexagonal architecture](https://alistair.cockburn.us/hexagonal-architecture/) (Alistair Cockburn): 定义该术语的原始文章。

</details>

<details>
<summary><strong>Clean Architecture (整洁架构):</strong> 强制执行“依赖规则”的同心圆结构。</summary>

分层模式的精华，将代码组织成同心圆，其依赖关系严格指向内部。最内层包含稳定的业务规则（Entities），而最外层处理框架和驱动。这能防止外部工具的更改强制导致核心业务规则发生变化。

- **示例:**
  - [android10/Android-CleanArchitecture](https://github.com/android10/Android-CleanArchitecture): 为移动开发实现整洁架构原则的经典参考应用。
  - [ivanpaulovich/clean-architecture-manga](https://github.com/ivanpaulovich/clean-architecture-manga): 一个遵循严格整洁架构规则来管理图书系统的 .NET 实现。
- **资源:**
  - [The Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) (Robert C. Martin): 概述各层级和依赖规则的权威文章。

</details>

<details>
<summary><strong>Onion Architecture (洋葱架构):</strong> 领域模型位于核心，依赖关系指向内部。</summary>

这种架构将领域模型置于中心，被领域服务、应用服务和基础设施所包围。它依赖于“依赖反转”：核心定义接口，而外层实现它们，从而使应用体现的是业务领域而非技术栈。

- **示例:**
  - [jasontaylordev/CleanArchitecture](https://github.com/jasontaylordev/CleanArchitecture): 拥有中心领域核心的洋葱式分层 .NET 行业标准模板。
- **资源:**
  - [The Onion Architecture](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/) (Jeffrey Palermo): 定义该架构及其层级的原始系列博文。

</details>


### 数据源与对象关系模式

管理内存中的应用对象与底层数据库或持久化层如何交互的模式。

<details>
<summary><strong>Repository Pattern (存储库模式):</strong> 在领域层和数据映射层之间充当中介。</summary>

作为业务逻辑与数据库之间的“守门员”抽象层。它为访问领域对象定义了类似集合的接口（如 `Add`, `Find`），隐藏了数据检索的细节。这不仅促进了业务逻辑中的“持久化透明性”，还简化了通过内存实现进行的单元测试。

- **示例:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): 每个领域聚合都有对应的 Repository 接口，并在基础设施层实现，以将领域与数据库隔离。
  - [android10/Android-CleanArchitecture](https://github.com/android10/Android-CleanArchitecture): 使用 Repository 模式协调来自本地缓存和远程网络源的数据检索。
- **资源:**
  - [The Repository Pattern](https://martinfowler.com/eaaCatalog/repository.html) (Martin Fowler): 该模式的标准定义。

</details>

<details>
<summary><strong>Active Record:</strong> 包装数据库行、封装数据和行为的对象。</summary>

一种数据模型对象包含管理自身持久化（保存、更新、删除）逻辑的模式。每个实例直接对应数据库中的一行。它针对快速开发和以 CRUD 为主的应用进行了优化。

- **示例:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Ruby on Rails 应用，其核心实体（用户、状态）同时包含业务数据和持久化逻辑。
  - [discourse/discourse](https://github.com/discourse/discourse): 使用 Active Record 管理其论坛状态和用户交互。
- **资源:**
  - [Active Record](https://martinfowler.com/eaaCatalog/activeRecord.html) (Martin Fowler): 关于该模式结构和权衡的概述。

</details>


### 状态管理与数据流模式

定义应用程序状态如何变更、存储和传播的模式。

<details>
<summary><strong>CQRS (Command Query Responsibility Segregation) (命令查询职责分离):</strong> 将数据修改与数据检索分离。</summary>

一种将传统的 CRUD 模型拆分为“命令”（Command - 修改状态）和“查询”（Query - 返回数据）的架构。这允许应用的读写端独立进行优化和扩展，对于写逻辑和读需求存在显著差异的复杂领域非常有效。

- **示例:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): 其订单微服务使用 MediatR 库严格分离了入站 REST 命令与数据库查询。
  - [kgrzybek/modular-monolith-with-ddd](https://github.com/kgrzybek/modular-monolith-with-ddd): 在业务模块中强制执行 CQRS，将写模型实体与读模型 DTO 分离。
- **资源:**
  - [CQRS](https://martinfowler.com/bliki/CQRS.html) (Martin Fowler): 定义该模式的核心文章。

</details>

<details>
<summary><strong>Event Sourcing (事件溯源):</strong> 将状态存储为不可变的事件序列。</summary>

事件溯源不存储当前状态，而是将每一个改变状态的操作记录为不可变的、具有历史意义的事件。当前状态通过回放整个事件日志来导出。这创建了可靠的审计追踪，并允许重建任意时间点的系统状态。

- **示例:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): 会计服务将财务交易存储为一系列事件，而非覆盖数据库行。
  - [ornicar/lila](https://github.com/ornicar/lila): Lichess 服务器通过回放玩家步数的顺序、不可变日志来导出棋局状态。
- **资源:**
  - [Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html) (Martin Fowler): 关于应用状态回放的详细分解。

</details>


### 并发与性能模式

专注于高吞吐量和低延迟执行的模式。

<details>
<summary><strong>LMAX Disruptor Pattern:</strong> 基于共享内存环形缓冲区的高性能线程间消息传递库。</summary>

一种专注于高吞吐量和低延迟执行的模式。

- **示例:**
  - [LMAX-Exchange/disruptor](https://github.com/LMAX-Exchange/disruptor): 高性能线程间消息传递库 Disruptor 的核心仓库。
  - [apache/logging-log4j2](https://github.com/apache/logging-log4j2): 现实世界的高性能系统示例，内部使用 Disruptor 来处理极端吞吐量的异步日志记录。
- **资源:**
  - [The LMAX Disruptor](https://lmax-exchange.github.io/disruptor/): 关于环形缓冲区架构的官方技术文档。

</details>

<details>
<summary><strong>Software Transactional Memory (STM, 软件事务内存):</strong> 类似于数据库事务的并发控制。</summary>

允许开发人员将对共享内存的多次更改组合成一个原子事务。如果发生冲突，事务会自动重试。这消除了死锁风险，并提供了手动内存锁管理的更安全替代方案。

- **示例:**
  - [metabase/metabase](https://github.com/metabase/metabase): 依靠 Clojure 原生的 STM 来安全地跨并发用户会话管理全局应用配置。
- **资源:**
  - [Software Transactional Memory](https://en.wikipedia.org/wiki/Software_transactional_memory): 内存事务的技术概述。

</details>


### 系统连通性模式

规定应用程序如何处理网络依赖和同步的模式。

<details>
<summary><strong>Offline-First Architecture (离线优先架构):</strong> 优先针对本地数据库进行操作。</summary>

一种应用默认读写本地存储的设计范式，从而实现即时的响应速度。当网络连接可用时，后台同步会将本地数据与远程服务器进行对账，并负责处理所需的冲突解决。

- **示例:**
  - [standardnotes/app](https://github.com/standardnotes/app): 对本地存储进行写入以实现无缝离线使用，并在后台将加密后的负载同步到服务器的笔记应用。
  - [logseq/logseq](https://github.com/logseq/logseq): 完全在本地文件上离线运行，使用后台同步进程与远程仓库协调。
- **资源:**
  - [Offline First](https://offlinefirst.org/): 为断网环境构建应用的社区原则。

</details>

<details>
<summary><strong>Optimistic UI (乐观 UI):</strong> 假设网络请求成功，立即更新界面。</summary>

一种前端模式，通过在用户操作时（即服务器响应前）立即更新 UI 来掩盖延迟。如果后台请求失败，本地状态会回滚并通知用户。

- **示例:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): 当用户“收藏”一条动态时会立即更新 UI，在服务器确认前就增加本地计数器。
  - [zulip/zulip-mobile](https://github.com/zulip/zulip-mobile): 在聊天信息流中立即显示已发送消息，在得到服务器确认前显示处于挂起状态。
- **资源:**
  - [True Lies Of Optimistic User Interfaces](https://www.smashingmagazine.com/2016/11/true-lies-of-optimistic-user-interfaces/): 关于该模式的心理学和技术回滚机制。

</details>


### 移动架构模式

针对移动设备生命周期和路由约束的框架与方法论。

<details>
<summary><strong>VIPER:</strong> 将逻辑、UI 和路由隔离到独立的组件中。</summary>

一种用于 iOS 的模块化架构，将业务逻辑和路由从 View Controller 中移除。导航被隔离在 Router 中，业务规则在 Interactor 中，从而允许在不包含 UI 组件的情况下进行单元测试。

- **示例:**
  - *示例说明:* VIPER 主要用于大规模的商业企业应用。参考实现通常见于架构模板，而非开源的消费者端代码库。
- **资源:**
  - [Architecting iOS Apps with VIPER](https://www.objc.io/issues/13-architecture/viper/): 将该模式引入 iOS 社区的文章。

</details>

<details>
<summary><strong>RIBs:</strong> 由路由状态驱动的业务逻辑树。</summary>

一种业务逻辑（Interactors）独立于视图层次结构运行的架构。无论视图当前是否挂载，业务过程都可以存在并路由数据，专为大型工程团队和复杂的状态管理而设计。

- **示例:**
  - *示例说明:* RIBs 是用于 Uber 等超大规模应用的专用架构。开源的 `uber/RIBs` 仓库提供了框架和文档，而非具体的消费者端实现。
- **资源:**
  - [RIBs - Uber's cross-platform architecture](https://github.com/uber/RIBs): 关于分离视图树与逻辑树的技术文档。

</details>


### 测试双倍模式 (Test Double Patterns)

在自动化测试中使用的特殊对象，通过模拟依赖项来隔离代码。

<details>
<summary><strong>Stub (打桩/存根):</strong> 在测试期间为调用提供硬编码的回答。</summary>

存根为被测系统提供一致的数据（如硬编码特定的服务响应），从而将测试从外部 API 的变动中隔离出来。

- **示例:**
  - [discourse/discourse](https://github.com/discourse/discourse): 对外部提供商的成功响应进行硬编码，以便在没有网络调用的情况下验证应用逻辑。
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): 模拟 Git 仓库状态，以便在不需要实际磁盘重负载操作的情况下测试 UI 逻辑。
- **资源:**
  - [Mocks Aren't Stubs](https://martinfowler.com/articles/mocksArentStubs.html) (Martin Fowler): 深入探讨基于状态的测试与基于交互的测试的区别。

</details>

<details>
<summary><strong>Fake (伪造对象):</strong> 可运行但不适合生产环境的实现。</summary>

伪造对象是真实系统的轻量级版本（如内存数据库），在测试周期中表现得像生产系统，但执行速度更快。

- **示例:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): 在集成测试中使用内存中数据库提供程序，以避免 SQL Server 的开销。
  - [metabase/metabase](https://github.com/metabase/metabase): 在测试期间采用内存 H2 数据库来模拟数据仓库环境。
- **资源:**
  - [Testing with Fakes](https://github.com/google/googletest/blob/main/docs/gmock_cook_book.md#fakes): 关于使用简化实现以提高效率的文档。

</details>

<br>

[![回到顶部](https://img.shields.io/badge/-回到顶部-6f42c1?style=for-the-badge&logoColor=white)](#目录)



## 第四层：软件设计模式

这些是代码的“底层基础”——解决常见编码问题的简单方案。如果说架构处理整个系统的布局，那么设计模式处理的是每个组件如何构建和连接。这涵盖了经典的面向对象设置、函数式编程以及安全多任务处理模式。

### 创建型模式 (Creational Patterns)

*将实例化过程抽象化的模式，使系统独立于其对象的创建、组合和表示方式*

<details>
<summary><strong>Singleton (单例模式):</strong> 将类限制为单个实例，并为其提供全局访问点。</summary>

通过将类限制为单个实例来跨整个应用协调状态的模式。常用于全局配置、数据库连接池或硬件管理器。虽然它对中心化控制非常有效，但它创建了全局状态，如果不通过依赖注入管理，可能会使单元测试变得更加困难。

- **示例:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): 为核心系统管理器（如 `DatabaseFactory` 和 `ApplicationContext` 提供者）使用单例，提供对关键加密存储的中心化访问。
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): 采用单例来管理全局系统设置和功能标志，为跨并发 Web 请求的应用行为提供单一事实来源。
- **资源:**
  - [Singleton Pattern](https://refactoring.guru/design-patterns/singleton): Refactoring Guru 关于实现策略和常见陷阱的技术分解。
  - [Singleton Design Pattern](https://sourcemaking.com/design_patterns/singleton): SourceMaking 关于模式结构和线程安全考虑的分析。

</details>

<details>
<summary><strong>Factory Method (工厂方法模式):</strong> 定义一个创建对象的接口，但允许子类改变所创建对象的类型。</summary>

一种将实例化逻辑委托给子类的模式。应用代码调用的不是特定类的“new”，而是工厂方法。这使系统能够与具体类型保持解耦，从而更轻松地扩展新类型。

- **示例:**
  - [moodle/moodle](https://github.com/moodle/moodle): 使用工厂方法实例化各种插件类型和活动模块，允许核心引擎在无需知晓具体实现的情况下管理多样化内容。
  - [metabase/metabase](https://github.com/metabase/metabase): 使用工厂方法创建特定的数据库驱动实例（如 Postgres vs MySQL），具体取决于用户的连接配置。
- **资源:**
  - [Factory Method](https://refactoring.guru/design-patterns/factory-method): Refactoring Guru 关于解耦创建者与产品的视觉指南。
  - [Factory Method Pattern](https://sourcemaking.com/design_patterns/factory_method): SourceMaking 提供的结构 UML 图和实现检查清单。

</details>

<details>
<summary><strong>Abstract Factory (抽象工厂模式):</strong> 定义一个接口，用于在不指定具体类的情况下创建相关对象的家族。</summary>

工厂模式的扩展，将相关的工厂组合在一起。它允许一个系统在不依赖产品创建、组合和表示细节的情况下运行。当系统必须配置有多个产品家族之一（如不同的 UI 主题或不同的存储后端）时特别有用。

- **示例:**
  - [tryghost/ghost](https://github.com/tryghost/ghost): 为其存储层实现抽象工厂，根据环境配置提供本地文件存储、S3 存储或其他云提供商的相关对象。
  - [home-assistant/core](https://github.com/home-assistant/core): 使用抽象工厂为特定的硬件集成生成实体家族（传感器、灯、开关），确保同一供应商的所有组件共享一致的内部逻辑。
- **资源:**
  - [Abstract Factory](https://refactoring.guru/design-patterns/abstract-factory): Refactoring Guru 详述的产品家族和工厂接口解释。
  - [Abstract Factory Design Pattern](https://sourcemaking.com/design_patterns/abstract_factory): SourceMaking 对模式目的和适用性的深入探讨。

</details>

<details>
<summary><strong>Builder (生成器/建造者模式):</strong> 将复杂对象的构建与其表示分离。</summary>

一种针对需要多个步骤或大量参数进行初始化的对象的模式。相比于拥有数十个参数的“重叠构造函数”，Builder 允许你以可读的、分步的方式仅设置所需的特定值，最后再产出成品对象。

- **示例:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): 依赖生成器模式构建复杂对象（如 `Notification` 记录或 `Message` 负载），以便在传输前设置众多可选字段。
  - [getsentry/sentry](https://github.com/getsentry/sentry): 在其事件处理流水线中使用生成器，在保存到数据库前将分散的遥测数据组装成复杂的崩溃报告事件。
- **资源:**
  - [Builder Pattern](https://refactoring.guru/design-patterns/builder): Refactoring Guru 提供的分步对象构建的实际案例。
  - [Builder Design Pattern](https://sourcemaking.com/design_patterns/builder): SourceMaking 关于如何解析复杂表示的概述。

</details>

<details>
<summary><strong>Prototype (原型模式):</strong> 通过复制现有对象来创建新对象。</summary>

一种用于在从头创建新对象成本过高或过于复杂时使用的模式。系统不进行全量初始化，而是通过克隆现有的“原型”实例来获取对象。常用于包含大量仅少数属性不同的相似对象的系统中。

- **示例:**
  - [moodle/moodle](https://github.com/moodle/moodle): 当复制课程或活动模板时实现原型克隆，允许教师在不重新执行所有设置逻辑的情况下基于现有结构创建新课程。
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): 在仓库镜像过程中使用原型模式进行内部对象克隆，确保仓库元数据对象能根据现有模板高效创建。
- **资源:**
  - [Prototype Pattern](https://refactoring.guru/design-patterns/prototype): Refactoring Guru 提供的深拷贝与浅拷贝解释。
  - [Prototype Design Pattern](https://sourcemaking.com/design_patterns/prototype): SourceMaking 关于原型注册表性能优势的研究。

</details>

<details>
<summary><strong>Object Pool Pattern (对象池模式):</strong> 维护一组已初始化的、可重用的对象以优化性能。</summary>

一种在创建对象成本过高（如数据库连接或网络套接字）时的性能优化模式。对象在使用后不被销毁，而是返回“池”中供下一个请求者重复使用。这减少了频繁分配内存和垃圾回收的开销。

- **示例:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): 管理高效的数据库连接池和工作线程池，以在无须重复实例化导致的延迟下处理数以千计的并发聊天消息。
  - [discourse/discourse](https://github.com/discourse/discourse): 在其后台任务处理和数据库连接中使用内部池，确保高流量论坛应用能维持稳定的资源使用。
- **资源:**
  - [Object Pool Pattern](https://sourcemaking.com/design_patterns/object_pool): SourceMaking 关于通过池化管理资源生命周期的理论。
  - [Object Pool](https://en.wikipedia.org/wiki/Object_pool_pattern): 维基百科上关于生命周期管理和池大小设置的概述。

</details>


### 结构型模式 (Structural Patterns)

*处理如何组合类和对象以形成更大结构的模式*

<details>
<summary><strong>Adapter (适配器模式):</strong> 通过将不兼容的对象包装在适配器中，使其不兼容的接口能够协同工作。</summary>

一种在两个不同接口之间充当“翻译器”的模式。它允许系统在无需更改核心代码的情况下使用外部库或老旧组件，从而防止在与第三方 API 交互时污染领域模型。

- **示例:**
  - [home-assistant/core](https://github.com/home-assistant/core): 使用适配器使数千种不同的智能家居硬件协议符合标准化的内部实体模型（如灯、开关和传感器）。
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): 依靠存储适配器将通用的附件指令翻译为不同云提供商（如 S3, Google Cloud, OpenStack Swift）所需的特定 API 请求。
- **资源:**
  - [Adapter Pattern](https://refactoring.guru/design-patterns/adapter): Refactoring Guru 关于类适配器和对象适配器的技术概述。
  - [Adapter Design Pattern](https://sourcemaking.com/design_patterns/adapter): SourceMaking 关于模式实现和意图的指南。

</details>

<details>
<summary><strong>Bridge (桥接模式):</strong> 将抽象与其实现解耦，使两者可以独立变化。</summary>

当组件有多个独立的变化维度时，用于避免类层级结构爆炸的模式。该模式将一个维度提取到单独的对象层级中，使两者可以并行扩展而不互相影响。

- **示例:**
  - [metabase/metabase](https://github.com/metabase/metabase): 将数据查询的抽象表示与跨数十种不同数据库执行该查询所需的具体实现分离。
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): 将“文件后端”抽象概念与在本地磁盘、S3 或 MinIO 进行读写的具体实现分离。
- **资源:**
  - [Bridge Pattern](https://refactoring.guru/design-patterns/bridge): Refactoring Guru 提供的如何将大型类拆分为独立层级的解释。
  - [Bridge Design Pattern](https://sourcemaking.com/design_patterns/bridge): SourceMaking 提供的模式结构分解。

</details>

<details>
<summary><strong>Composite (组合模式):</strong> 将对象组合成树形结构来表示“部分-整体”的层次结构，使客户端能以一致的方式对待单个对象和组合对象。</summary>

一种允许像对待单个实例一样对待对象集合的模式。用于构建分层结构（如文件系统、UI 组件树），其中一组子项能以与单个项相同的方式响应命令。

- **示例:**
  - [moodle/moodle](https://github.com/moodle/moodle): 将复杂的课程结构（分类、子类、模块）表示为可统一导航和渲染的组合树。
  - [standardnotes/app](https://github.com/standardnotes/app): 管理分层的笔记组织，其中父容器和单个笔记能一致地响应同步和元数据操作。
- **资源:**
  - [Composite Pattern](https://refactoring.guru/design-patterns/composite): Refactoring Guru 关于构建递归对象结构的视觉指南。
  - [Composite](https://en.wikipedia.org/wiki/Composite_pattern): 维基百科上关于该模式在树形数据结构中作用的概述。

</details>

<details>
<summary><strong>Decorator (装饰器模式):</strong> 动态地为对象附加额外的职责，提供了一种比继承更灵活的扩展功能的方案。</summary>

一种允许在不影响同类其他对象的情况下，静态或动态地为单个对象添加行为的模式。它将原始对象包装在“装饰器”类中，维持原接口的同时在方法调用前后添加新逻辑。

- **示例:**
  - [discourse/discourse](https://github.com/discourse/discourse): 频繁使用装饰器为核心用户或帖子模型动态添加功能（由活动插件触发），而无需修改基础 Ruby 类。
  - [spree/spree](https://github.com/spree/spree): 依靠装饰器允许开发人员在不改变底层框架代码的情况下，扩展核心电商实体（如订单、装运）的业务逻辑。
- **资源:**
  - [Decorator Pattern](https://refactoring.guru/design-patterns/decorator): Refactoring Guru 关于如何在运行时附加新行为的指南。
  - [Decorator Design Pattern](https://sourcemaking.com/design_patterns/decorator): SourceMaking 对基于包装器扩展的分析。

</details>

<details>
<summary><strong>Facade (外观模式):</strong> 统一的一套接口的子系统。定义一个简化接口，使其更易于使用。</summary>

通过隐藏子系统的复杂性来使其易于使用的接口。它为一组复杂的类定义了单一入口点，从而降低了学习曲线并减少了系统间的依赖。

- **示例:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): 实现外观服务来包装复杂的 Git 操作和内部 RPC 调用，为 Web 应用提供简单的仓库管理 API。
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): 为通知子系统提供外观，使应用通过一个接口触发警报，而无需管理具体的推送协议。
- **资源:**
  - [Facade Pattern](https://refactoring.guru/design-patterns/facade): Refactoring Guru 关于使客户端免收复杂库依赖影响的解析。
  - [Facade](https://en.wikipedia.org/wiki/Facade_pattern): 维基百科上关于简化接口设计的概述。

</details>

<details>
<summary><strong>Flyweight (享元模式):</strong> 通过共享来高效支持大量细粒度对象，从而最小化内存占用。</summary>

一种注重数据共享的节内存模式。它将“内部状态”（所有对象相同的数据）提取到共享的享元对象中，而“外部状态”（唯一数据）单独存储，从而支持成千上万个对象仅占用极少内存。

- **示例:**
  - [ornicar/lila](https://github.com/ornicar/lila): 在 Lichess 的数百万场活跃对局中共享不可变的棋盘配置和棋子表示，以最小化服务器内存消耗。
  - [plausible/analytics](https://github.com/plausible/analytics): 在高流量分析事件流中对常见的浏览器和系统类型使用共享元数据字符串。
- **资源:**
  - [Flyweight Pattern](https://refactoring.guru/design-patterns/flyweight): Refactoring Guru 提供的海量对象系统内存管理技术。
  - [Flyweight Design Pattern](https://sourcemaking.com/design_patterns/flyweight): SourceMaking 关于高效状态共享的指南。

</details>

<details>
<summary><strong>Proxy (代理模式):</strong> 为另一个对象定义一个替代者或占位符，以控制对其的访问。</summary>

代理对象充当原始对象的中间人。可用于延迟初始化（推迟昂贵对象创建）、访问控制（转发前校验权限）或请求的日志记录和缓存。

- **示例:**
  - [tryghost/ghost](https://github.com/tryghost/ghost): 采用代理对象拦截数据库请求，从而在请求到达持久层前提供验证和内部缓存层。
  - [nextcloud/server](https://github.com/nextcloud/server): 使用代理代表外部存储挂载上的文件，仅在文件被明确访问时才发起昂贵的网络认证和连接。
- **资源:**
  - [Proxy Pattern](https://refactoring.guru/design-patterns/proxy): Refactoring Guru 关于通过替代者控制原始对象访问的解析。
  - [Proxy Design Pattern](https://sourcemaking.com/design_patterns/proxy): SourceMaking 关于替代者和占位符对象的实现策略。

</details>


### 行为型模式 (Behavioral Patterns)

*关注对象间算法和职责分配的模式*

<details>
<summary><strong>Strategy (策略模式):</strong> 定义一系列算法，将每一个算法封装起来，并使它们在运行时可以互换。</summary>

当应用需要在运行时选择不同的执行方式时使用的模式。系统调用的不是硬编码算法，而是策略对象，允许如在不改变存储代码的情况下无缝切换本地存储策略或云存储策略。

- **示例:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): 联邦引擎使用不同的交付策略，根据帖子优先级和网络状态选择后台推送或立即交付。
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): 采用策略模式处理多种身份验证方式（密码、LDAP, OAuth2, SSH 等）。
- **资源:**
  - [Strategy Pattern](https://refactoring.guru/design-patterns/strategy): Refactoring Guru 关于运行时切换算法的技术。
  - [Strategy Design Pattern](https://sourcemaking.com/design_patterns/strategy): SourceMaking 关于封装算法家族的指南。

</details>

<details>
<summary><strong>State (状态模式):</strong> 当一个对象的内部状态改变时，允许其改变其行为，使其看起来像是改变了类。</summary>

将特定于状态的行为封装到独立类中的模式。对象将工作委托给状态对象，而不是包含巨大的条件块。当状态切换时，对象更换其内部的状态对象，从而改变行为。

- **示例:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): 使用状态对象管理合并请求 (Merge Request) 的复杂转换（如草稿、已打开、已合并、已关闭）并执行相应的规则。
  - [spree/spree](https://github.com/spree/spree): 依靠状态模式管理订单的结算周期，确保支付、配送和完成步骤按序进行。
- **资源:**
  - [State Pattern](https://refactoring.guru/design-patterns/state): Refactoring Guru 关于如何将有限状态机实现为对象的指南。
  - [State Design Pattern](https://sourcemaking.com/design_patterns/state): SourceMaking 提供的状态驱动行为转换分析。

</details>

<details>
<summary><strong>Observer (观察者模式):</strong> 定义对象间的一对多依赖关系，以便当一个对象状态改变时，所有依赖者都会收到通知并自动更新。</summary>

用于创建订阅机制的模式。一个主体对象维护一个观察者列表。当主体状态改变，列表中的观察者会自动收到通知。这是响应式 UI 和事件驱动系统的核心模式。

- **示例:**
  - [home-assistant/core](https://github.com/home-assistant/core): 完全基于观察者模式构建，一旦物理传感器报告状态改变，中央总线会立即通知所有组件和 UI 仪表板。
  - [discourse/discourse](https://github.com/discourse/discourse): 当有新帖子或涉及用户时，使用观察者模式触发通知、邮件和 UI 更新。
- **资源:**
  - [Observer Pattern](https://refactoring.guru/design-patterns/observer): Refactoring Guru 关于实现基于订阅的事件通知的指南。
  - [Observer Design Pattern](https://sourcemaking.com/design_patterns/observer): SourceMaking 关于主体与观察者关系的分解。

</details>

<details>
<summary><strong>Chain of Responsibility (责任链模式):</strong> 沿着处理器链传递请求，每个处理器决定是处理该请求还是将其传给链中的下一个处理器。</summary>

将请求发送者与接收者解耦的模式。允许请求有多次处理机会，而发送者无需知晓最终的具体处理者。常用于请求处理流水线、中间件和插件系统。

- **示例:**
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): 在到达核心逻辑前使用责任链中间件处理 HTTP 请求的身份验证、日志及 CSRF 防护。
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): 插件系统实现责任链，使各个活动插件能在消息保存前对其进行拦截和修改。
- **资源:**
  - [Chain of Responsibility](https://refactoring.guru/design-patterns/chain-of-responsibility): Refactoring Guru 关于基于处理器的请求处理技术概述。
  - [Chain of Responsibility Design Pattern](https://sourcemaking.com/design_patterns/chain_of_responsibility): SourceMaking 提供的模式意图和结构参与者分解。

</details>

<details>
<summary><strong>Command (命令模式):</strong> 将请求封装为对象，从而允许将客户端参数化（如队列、请求和操作）。</summary>

将特定请求或动作转化为包含其执行所需所有信息的独立对象的模式。这允许应用延迟执行、存入队列或保存历史记录以支持撤销/重做功能。

- **示例:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): 将后台任务封装为命令对象，使重型操作如仓库归档能在 Web 主线程外异步且独立执行。
  - [zulip/zulip](https://github.com/zulip/zulip): 依靠命令对象处理聊天消息，以便在隔离、可测试的方式下处理复杂交付逻辑。
- **资源:**
  - [Command Pattern](https://refactoring.guru/design-patterns/command): Refactoring Guru 关于封装动作及撤销/重做支持的指南。
  - [Command Design Pattern](https://sourcemaking.com/design_patterns/command): SourceMaking 关于调用者与接收者关系的技术分析。

</details>

<details>
<summary><strong>Iterator (迭代器模式):</strong> 定义一种顺序访问聚合对象元素的方法，而无需暴露其底层表示。</summary>

将集合的遍历逻辑提取到称为迭代器的独立对象中的模式。允许客户端在不知道数据具体存储方式（数组、链表或远程数据库）的情况下进行步进。

- **示例:**
  - [moodle/moodle](https://github.com/moodle/moodle): 使用迭代器遍历大量课程记录，以便在不一次性加载整个集合的情况下处理大数据。
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): 实现迭代器以遍历 Git 提交历史和文件树，提供统一的仓库访问方式。
- **资源:**
  - [Iterator Pattern](https://refactoring.guru/design-patterns/iterator): Refactoring Guru 提供的遍历复杂集合的视觉指南。
  - [Iterator Design Pattern](https://sourcemaking.com/design_patterns/iterator): SourceMaking 提供的遍历逻辑与实现解耦的指南。

</details>

<details>
<summary><strong>Mediator (中介者模式):</strong> 定义一个封装一组对象如何交互的对象，通过保持对象不显式引用彼此来促进松耦合。</summary>

将应用各组件间通信中心化的模式。对象不再直接对手，而是全部通过中央中介者进行，从而方便在单一位置修改通信逻辑。

- **示例:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): 当数据库状态改变时，使用中介者协调不同 Fragment 与 Activity 间的 UI 更新。
  - [zulip/zulip](https://github.com/zulip/zulip): 采用中介者模式协调服务器逻辑与各连接客户端间的实时事件交付。
- **资源:**
  - [Mediator Pattern](https://refactoring.guru/design-patterns/mediator): Refactoring Guru 关于如何减少类之间混乱依赖的解析。
  - [Mediator Design Pattern](https://sourcemaking.com/design_patterns/mediator): SourceMaking 对中心化与分布式通信的分析。

</details>

<details>
<summary><strong>Memento (备忘录模式):</strong> 在不破坏封装性的前提下，捕捉并外部化对象的内部状态，以便之后可以将对象恢复到该状态。</summary>

用于实现对象状态检查点的模式。允许保存并随后恢复对象状态，这对于实现撤销/重做或会话恢复且不暴露内部细节至关重要。

- **示例:**
  - [standardnotes/app](https://github.com/standardnotes/app): 实现备忘录概念来为笔记内容拍摄快照，允许用户查看和恢复之前的加密版本。
  - [logseq/logseq](https://github.com/logseq/logseq): 使用备忘录式状态管理处理撤销/重做操作，确保复杂编辑能安全逆转。
- **资源:**
  - [Memento Pattern](https://refactoring.guru/design-patterns/memento): Refactoring Guru 关于保存与恢复对象快照的技术。
  - [Memento Design Pattern](https://sourcemaking.com/design_patterns/memento): SourceMaking 关于为状态恢复捕捉内部状态的指南。

</details>

<details>
<summary><strong>Template Method (模板方法模式):</strong> 在操作中定义算法的骨架，将某些步骤延迟到子类中，而不改变算法结构。</summary>

在基类中定义标准流程步骤，但将某些具体步骤的实现留给子类的模式。这能确保始终遵循整体工作流，同时允许特定部分实现自定义。

- **示例:**
  - [moodle/moodle](https://github.com/moodle/moodle): 为活动模块提供基类，定义评分和提交的标准生命周期，允许每个子模块实现具体逻辑。
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): 在后台 worker 基类中使用模板方法，确保所有任务遵循一致的日志、重试和错误处理程序。
- **资源:**
  - [Template Method Pattern](https://refactoring.guru/design-patterns/template-method): Refactoring Guru 关于带有可插拔步骤的算法骨架定义。
  - [Template Method Design Pattern](https://sourcemaking.com/design_patterns/template_method): SourceMaking 对“好莱坞原则”的分析。

</details>

<details>
<summary><strong>Visitor (访问者模式):</strong> 表示要在一组对象结构元素上执行的操作，允许在不改变元素类的前提下定义新操作。</summary>

用于在不修改现有对象的前提下为结构添加新功能的模式。访问者对象遍历结构并对每个元素执行操作。这对审计、数据导出或执行复杂验证非常有效。

- **示例:**
  - [home-assistant/core](https://github.com/home-assistant/core): 采用访问者模式遍历设备配置注册表以执行系统校验并生成行政报告。
  - [grafana/grafana](https://github.com/grafana/grafana): 在仪表板和警报处理组件中遍历复杂的 JSON 配置树进行验证。
- **资源:**
  - [Visitor Pattern](https://refactoring.guru/design-patterns/visitor): Refactoring Guru 关于如何为现有层级添加新操作的指南。
  - [Visitor Design Pattern](https://sourcemaking.com/design_patterns/visitor): SourceMaking 关于双重分派和结构遍历的分解。

</details>

<details>
<summary><strong>Interpreter (解释器模式):</strong> 为语言定义其文法表示及一个使用该表示来评估句子的解释器。</summary>

用于为特定语言文法或表达式定义类层次结构的模式。解释器遍历该层次结构以评估表达式。常用于执行自定义查询或解析数学公式。

- **示例:**
  - [metabase/metabase](https://github.com/metabase/metabase): 使用解释器将其内部 JSON 格式的 MBQL 翻译为各数据库所需的特定 SQL 方言。
  - [grafana/grafana](https://github.com/grafana/grafana): 实现解释器以在前端和后端评估用户定义的警报条件。
- **资源:**
  - [Interpreter Design Pattern](https://sourcemaking.com/design_patterns/interpreter): SourceMaking 关于文法表示与评估的概述。
  - [Interpreter](https://en.wikipedia.org/wiki/Interpreter_pattern): 维基百科上关于该模式在领域特定语言中作用的概述。

</details>

<details>
<summary><strong>Null Object Pattern (空对象模式):</strong> 使用实现预期接口的默认、中性对象来替代空引用，从而避免全代码库的判空检查和异常。</summary>

用一个不做任何事但实现了所需接口的具体对象来替换 `null` 的模式。通过将缺失的依赖项视为有效的“无操作”对象来简化代码。

- **示例:**
  - [discourse/discourse](https://github.com/discourse/discourse): 当设置或用户关系缺失时使用空对象，允许 UI 逻辑无需显式判空即可继续。
  - [spree/spree](https://github.com/spree/spree): 为促销计算器和税收处理器使用空对象，确保在无特定规则时结算流保持一致。
- **资源:**
  - [Null Object Pattern](https://sourcemaking.com/design_patterns/null_object): SourceMaking 关于通过消除判空来简化代码的指南。
  - [Null Object](https://en.wikipedia.org/wiki/Null_object_pattern): 维基百科关于该模式对软件鲁棒性益处的概述。

</details>


### 并发模式 (Concurrency Patterns)

*处理多线程范式和并行处理的模式*

<details>
<summary><strong>Active Object (活动对象模式):</strong> 将方法执行与方法调用解耦，以增强并发性并简化对拥有独立控制线程的对象进行同步访问。</summary>

允许对象在自己的线程（而非调用者线程）中执行方法的模式。将同步方法调用转化为异步消息，允许调用者立即继续。

- **示例:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): 在后台作业管理中实现，确保重度加密和数据库写入不阻塞 UI 主线程。
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): 使用活动对象结构处理异步 worker，防止阻塞入站网络请求。
- **资源:**
  - [Active Object](https://en.wikipedia.org/wiki/Active_object): 包含代理、调度器、仆人等组件的模式概述。
  - [Active Object Design Pattern](https://www.dre.vanderbilt.edu/~schmidt/PDF/Active-Object.pdf) (Douglas C. Schmidt): 详述调用与执行解耦的原始研究论文。

</details>

<details>
<summary><strong>Monitor Object (监视器对象模式):</strong> 同步并发方法执行，确保同一时间只有一个方法在对象内运行，安全地封装互斥操作。</summary>

保护对象内部状态免受多线程并发访问的模式。确保任一时刻只有一个线程在执行对象的同步方法，其他线程需排队等待进入锁。

- **示例:**
  - [metabase/metabase](https://github.com/metabase/metabase): 使用监视器对象管理对共享数据库连接池和全局配置的同步访问，防止竞态条件。
  - [discourse/discourse](https://github.com/discourse/discourse): 在其 Ruby 环境中使用监视器和互斥量 (mutex) 来同步对共享内存结构的访问。
- **资源:**
  - [Monitor Object Design Pattern](https://www.dre.vanderbilt.edu/~schmidt/PDF/Monitor.pdf) (Douglas C. Schmidt): 封装面向对象软件互斥操作的指南。
  - [Monitor](https://en.wikipedia.org/wiki/Monitor_(synchronization)): 对高级同步原语的技术分解。

</details>

<details>
<summary><strong>Half-Sync/Half-Async (半同步/半异步模式):</strong> 将并发系统中的异步和同步处理服务解耦，旨在不降低性能的前提下简化编程。</summary>

用于桥接低层级异步事件处理（为了 I/O 效率）与高层级同步处理（为了编程逻辑简单）的模式。使用队列将数据在异步层与同步 worker 池之间传递。

- **示例:**
  - [zulip/zulip](https://github.com/zulip/zulip): 使用异步事件循环处理 Socket 连接，并将其业务逻辑和数据库操作委托给同步 worker 线程处理。
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): 依靠该架构管理高速网络 I/O 与顺序执行持久化逻辑间的切换。
- **资源:**
  - [Half-Sync/Half-Async Design Pattern](https://www.dre.vanderbilt.edu/~schmidt/PDF/HSHA.pdf) (Douglas C. Schmidt): 同步与异步关注点分离的技术分析。
  - [Pattern-Oriented Software Architecture (POSA)](https://en.wikipedia.org/wiki/Pattern-Oriented_Software_Architecture): 并发与网络模式汇总。

</details>

<details>
<summary><strong>Thread Pool (线程池模式):</strong> 管理一组工作线程，代表应用高效地执行异步回调。</summary>

避免频繁创建/销毁线程的高开销。维护预先初始化的线程，任务到达后分配给可用线程，完成后返回池中复用。

- **示例:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): 在 Sidekiq 引擎中使用线程池管理成千上万个并发任务，而不会压垮系统资源。
  - [metabase/metabase](https://github.com/metabase/metabase): 在其 Jetty Web 服务器配置中采用线程池处理并发 HTTP 请求。
- **资源:**
  - [Thread Pool Pattern](https://sourcemaking.com/design_patterns/thread_pool): SourceMaking 关于管理工作线程生命周期的指南。
  - [Thread Pool](https://en.wikipedia.org/wiki/Thread_pool): 维基百科上关于任务队列和资源管理的概述。

</details>

<details>
<summary><strong>Read-Write Lock (读写锁模式):</strong> 允许多个并发读访问，但写操作需要排他性访问，通过优化读多写少的负载提升性能。</summary>

在数据读取频率远高于修改频率的系统中提升性能。允许多个“读者”同时访问，但“写者”必须等待所有读者结束后才能获得独占权修改数据。

- **示例:**
  - [grafana/grafana](https://github.com/grafana/grafana): 为其内部数据源缓存使用读写锁，支持数千个并发读取同时保护配置更新。
  - [home-assistant/core](https://github.com/home-assistant/core): 在状态注册表中使用读写锁，允许各组件并发查询状态同时保护关键写入。
- **资源:**
  - [Read-Write Lock Pattern](https://en.wikipedia.org/wiki/Readers%E2%80%93writer_lock): 关于管理并发读与独占写优先级的技术细节。
  - [Read-Write Lock](https://sourcemaking.com/design_patterns/read_write_lock): SourceMaking 对优化读密集型并发负载的分析。

</details>

<details>
<summary><strong>Double-Checked Locking (双重检查锁定):</strong> 通过首先在无同步的情况下测试锁定条件，仅在通过后才获取锁，以此减少获取锁的开销。</summary>

优化多线程环境下的延迟初始化。首先无锁检查是否已初始化；若未初始化再进入同步块二次检查，确保只有一个线程创建实例。

- **示例:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): 经常用于数据库工厂和加密配置管理器的延迟初始化，以最小开销实现线程安全。
  - [wordpress-mobile/WordPress-Android](https://github.com/wordpress-mobile/WordPress-Android): 在初始化共享服务时采用双检锁模式，确保线程安全且不牺牲启动速度。
- **资源:**
  - [Double-Checked Locking Pattern](https://sourcemaking.com/design_patterns/double_checked_locking): SourceMaking 提供的优化同步机制指南。
  - [The Double-Checked Locking is Broken Declaration](http://www.cs.umd.edu/~pugh/java/memoryModel/DoubleCheckedLocking.html): 对早期 Java 版本中内存模型问题的批判性历史分析。

</details>


### 函数式模式 (Functional Patterns)

*源于函数式编程范式、适用于现代软件设计的模式*

<details>
<summary><strong>Monad (单子):</strong> 一种将计算描述为一系列步骤、并以纯函数方式处理副作用（Side Effects）、状态或 I/O 的模式。</summary>

将值包装在上下文中并提供将函数应用于该包装值的机制。允许将复杂操作顺序链接，同时抽象掉判空、状态传递或异步执行等样本代码。

- **示例:**
  - [lemmynet/lemmy](https://github.com/lemmynet/lemmy): 使用 Rust 编写，其后端广泛使用原生的 `Option` 和 `Result` 单子来安全处理缺失值和 I/O 副作用。
  - [standardnotes/app](https://github.com/standardnotes/app): 在其 TypeScript 代码中依靠 Promise（异步单子结构）来链接复杂的加密操作和数据库写入。
- **资源:**
  - [Monad (functional programming)](https://en.wikipedia.org/wiki/Monad_(functional_programming)): 维基百科上关于单子结构及其数学起源的概述。
  - [Functors, Applicatives, and Monads in Pictures](https://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html) (Aditya Bhargava): 非常易懂的函数式上下文视觉指南。

</details>

<details>
<summary><strong>Functor (函子):</strong> 一种映射模式，允许将函数应用于包装在上下文中的值，同时保留该上下文的结构。</summary>

代表了任何实现了映射 (mapping) 函数的类型。它对容器（如数组、列表或可选类型）内的内容进行转换，返回结构完全相同的新容器，而不变更原包装。

- **示例:**
  - [plausible/analytics](https://github.com/plausible/analytics): 基于 Elixir 的分析平台，大量依靠函子式的映射操作来高效处理遥测数据。
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): 频繁在集合上进行映射操作，为展示层应用数据转换函数。
- **资源:**
  - [Functor (functional programming)](https://en.wikipedia.org/wiki/Functor_(functional_programming)): 维基百科上关于对数据类型进行映射的技术细节。
  - [Category Theory for Programmers: Functors](https://bartoszmilewski.com/2015/01/20/functors/) (Bartosz Milewski): 对函子的理论与实践应用的深入研究。

</details>

<details>
<summary><strong>Immutable Object (不可变对象):</strong> 状态在创建后无法修改的对象。消除意外副作用并使并发编程天然安全。</summary>

一种严格的数据管理模式。对对象的更新不是修改其属性，而是创建包含新值的副本。这保证了线程安全，防止了竞态条件。

- **示例:**
  - [zulip/zulip-mobile](https://github.com/zulip/zulip-mobile): 使用 Redux 来对整个应用状态树强制执行严格的不可变性。每条新消息都会生成新状态，而非原地修改。
  - [ornicar/lila](https://github.com/ornicar/lila): Lichess 服务器将对局记录、棋盘布局表示为严格不可变的数据结构，从而实现高速并发处理。
- **资源:**
  - [Immutable Object](https://en.wikipedia.org/wiki/Immutable_object): 维基百科关于实现策略和性能特性的概述。
  - [ValueObject](https://martinfowler.com/bliki/ValueObject.html) (Martin Fowler): 关于基于属性而非标识区分对象的指南。

</details>

<details>
<summary><strong>Result Pattern / Railway Oriented Programming (结果模式 / 铁路面向编程):</strong> 将操作结果（成功或失败）封装在特定的类型中，允许顺序链接操作，而无需使用异常。</summary>

替代传统的 try-catch 异常处理。函数返回代表成功或错误的对象。在链式调用中，一旦某个环节失败，系统会转入“错误轨道”，跳过后续逻辑。

- **示例:**
  - [lemmynet/lemmy](https://github.com/lemmynet/lemmy): 弃用传统的异常抛出，几乎所有数据库和网络请求均返回 Rust 的 `Result` 枚举。
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): 使用 Kotlin 原生的 `Result` 类型来安全包装可能由于坏密钥或损坏网络载荷而失败的加密处理链。
- **资源:**
  - [Railway Oriented Programming](https://fsharpforfunandprofit.com/rop/) (Scott Wlaschin): 关于通过铁路类比进行错误处理的权威指南。
  - [Error Handling in Rust](https://doc.rust-lang.org/book/ch09-00-error-handling.html): 用于弹性软件设计的 `Result` 枚举官方文档。

</details>

<details>
<summary><strong>Dependency Rejection (依赖排斥):</strong> 依赖注入的函数式替代方案。将所有副作用和外部依赖推到应用的最外缘，保持核心领域逻辑的纯净。</summary>

将逻辑与行动分离的架构模式。纯领域模型不再注入数据库服务，而是直接接收原始数据并返回原始数据。应用外壳负责实际读写操作。

- **示例:**
  - [metabase/metabase](https://github.com/metabase/metabase): 将复杂的查询生成和转换逻辑隔离为 Clojure 纯函数，脱离副作用沉重的数据库执行壳。
  - [grafana/grafana](https://github.com/grafana/grafana): 将仪表板数据转换提取为纯函数，将网络请求和写入推送到最外层的 HTTP 处理程序中。
- **资源:**
  - [Dependency Rejection](https://blog.ploeh.dk/2017/01/27/dependency-rejection/) (Mark Seemann): 关于用纯函数替换依赖注入的核心文章。
  - [Functional Core, Imperative Shell](https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell) (Gary Bernhardt): 关于将状态变更推送到架构边界的技术探索。

</details>


<br>

[![回到顶部](https://img.shields.io/badge/-回到顶部-6f42c1?style=for-the-badge&logoColor=white)](#目录)

## 横切架构关注点

这些是触及软件系统各个部分的模式和工具。与孤立的功能不同，这些关注点（如安全性、可观测性和数据备份）影响许多组件，需要一致的设置来保持整个系统的正常运行。此类别侧重于平台的基石，包括安全标准、链路追踪和自动化部署。

### 安全架构模式

在所有系统边界内维持系统安全、安全访问控制、数据机密性以及整体合规性的模式和机制。

<details>
<summary><strong>Zero Trust Architecture (零信任架构):</strong> 一种假设网络始终处于敌对状态的架构；它要求对每个请求（无论来源如何）进行严格的身份和设备验证。</summary>

取代了传统的“堡垒加护城河”安全模型。零信任不再信任企业防火墙内的任何东西，而是要求每个用户、设备和应用程序在获得任何资源访问权限之前，都必须经过持续的身份验证和授权，并在微观层面上执行最小权限原则。

- **标准工具:**
  - [cloudflare/cloudflared](https://github.com/cloudflare/cloudflared): Cloudflare Tunnel 客户端，通过安全地将本地服务暴露给外部网络而不打开入站端口，成为构建零信任网络访问的核心组件。
  - [pomerium/pomerium](https://github.com/pomerium/pomerium): 一个开源的身份感知访问代理，充当内部应用程序的网关，在边缘执行零信任策略。
- **资源:**
  - [Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final): NIST 特别出版物 (800-207)，定义了零信任的核心原则和部署模型。
  - [BeyondCorp](https://www.beyondcorp.com/): 谷歌的企业安全模型，率先推动了行业商向零信任网络的转变。

</details>

<details>
<summary><strong>Role-Based Access Control (RBAC, 基于角色的访问控制):</strong> 根据组织内单个用户预定义的角色和权限限制系统访问。</summary>

一种安全范式，访问权限按角色名称（如“管理员”、“编辑”、“查看者”）分组，而不是单独分配给用户。然后为用户分配一个或多个角色，极大地简化了大型组织中的权限管理。

- **标准工具:**
  - [kubernetes/kubernetes](https://github.com/kubernetes/kubernetes): Kubernetes 容器编排系统大量使用 RBAC，根据人类用户和服务账户的角色来调节对其 API 资源的访问。
  - [casbin/casbin](https://github.com/casbin/casbin): 一个强大且高效的开源访问控制库，支持基于各种访问控制模型（主要是 RBAC）执行授权。
- **资源:**
  - [Role-Based Access Control](https://csrc.nist.gov/projects/role-based-access-control): NIST 核心标准，确立了 RBAC 的经济和安全效益。
  - [RBAC Authorization](https://kubernetes.io/docs/reference/access-authn-authz/rbac/): Kubernetes 官方文档，详细介绍了如何架构角色绑定和集群角色。

</details>

<details>
<summary><strong>Attribute-Based Access Control (ABAC, 基于属性的访问控制):</strong> 通过评估结合了用户、资源和环境属性的策略来授予访问权限。</summary>

一种高度细粒度的授权模型，超越了静态角色。它通过评估属性组合（如用户部门、文档敏感级别、一天中的时间和当前 IP 地址）在运行时做出访问决策，从而支持高度复杂的安全策略。

- **标准工具:**
  - [open-policy-agent/opa](https://github.com/open-policy-agent/opa): 一个通用的策略引擎，将策略决策与应用逻辑解耦，广泛用于使用 Rego 语言在云原生堆栈中实现 ABAC。
  - [permitio/permit-node](https://github.com/permitio/permit-node): 一个全栈授权框架，提供通过 API 驱动的界面实现复杂 ABAC 和 RBAC 策略的工具。
- **资源:**
  - [Attribute-Based Access Control](https://csrc.nist.gov/publications/detail/sp/800-162/final): NIST 特特别出版物 (800-162)，定义了企业 ABAC 的组成部分和考虑因素。
  - [OPA Documentation](https://www.openpolicyagent.org/docs/latest/): Open Policy Agent 关于编写用于属性评估的声明式策略的官方指南。

</details>

<details>
<summary><strong>Mutual TLS (mTLS, 双向 TLS):</strong> 通过要求客户端和服务器相互验证对方的加密证书，来验证流量在双向上都是安全且可信的。</summary>

标准 TLS (HTTPS) 仅向客户端验证服务器身份。mTLS 强制客户端也向服务器出示有效证书。这验证了流量已加密，并且只有经过严格授权的微服务或设备才能彼此通信，形成了服务网格安全的主干。

- **标准工具:**
  - [istio/istio](https://github.com/istio/istio): 一个流行的开源服务网格，在 Kubernetes 集群内的所有内部服务间通信中无缝分层 mTLS 加密和身份验证。
  - [linkerd/linkerd2](https://github.com/linkerd/linkerd2): 一个针对 Kubernetes 的极轻量级、安全优先的服务网格，在所有网格化的 Pod 之间提供自动、透明的 mTLS。
- **资源:**
  - [Mutual TLS](https://www.cloudflare.com/learning/access-management/what-is-mutual-tls/): Cloudflare 提供的 mTLS 概念及其在零信任环境中的作用概述。
  - [Istio Security Concept](https://istio.io/latest/docs/concepts/security/): 关于 Istio 如何生成和分发 mTLS 证书的技术文档。

</details>

<details>
<summary><strong>Identity Federation / Single Sign-On (SSO, 身份联邦 / 单点登录):</strong> 将用户身份验证委托给受信任的中央身份提供商，允许用户使用一套凭据访问多个独立系统。</summary>

一种集中身份管理的模式。应用不再管理各自的用户数据库和密码哈希，而是通过 SAML 或 OpenID Connect 等协议将用户重定向到中央身份提供商 (IdP)。IdP 对用户进行身份验证并返回安全令牌，从而减少密码疲劳并集中安全审计。

- **标准工具:**
  - [keycloak/keycloak](https://github.com/keycloak/keycloak): 由 Red Hat 支持的开源身份和访问管理系统，提供 SSO、身份代理和用户联邦。
  - [dexidp/dex](https://github.com/dexidp/dex): 一个联邦 OpenID Connect 提供商，作为连接外部身份提供商（如 LDAP、SAML 或 GitHub）到 Kubernetes 集群和其他应用的门户。
- **资源:**
  - [Federated Identity](https://en.wikipedia.org/wiki/Federated_identity): 维基百科上关于身份联邦模式及其常用协议的概述。
  - [OpenID Connect](https://openid.net/connect/): 构建在 OAuth 2.0 协议之上的身份层的官方规范。

</details>


### 数据架构模式

定义组织内静态和动态数据资产的结构、管理和治理的策略。

<details>
<summary><strong>Data Lake (数据湖):</strong> 一个集中的、高度可扩展的存储库，以原生格式存储大量原始、非结构化和结构化数据。</summary>

它允许组织在不对数据进行预先结构化的情况下存储数据，用于多样化的分析、机器学习和大数据处理流水线。

- **标准工具:**
  - [delta-io/delta](https://github.com/delta-io/delta): Delta Lake 是一个开源存储框架，支持使用 Spark、PrestoDB、Flink 和 Trino 等计算引擎构建湖仓一体 (Lakehouse) 架构。
  - [apache/hudi](https://github.com/apache/hudi): Apache Hudi 为大数据带来流式处理，在提供新鲜数据的同时，比传统的数据湖批处理效率高出一个数量级。
- **资源:**
  - [什么是数据湖?](https://aws.amazon.com/cn/big-data/datalakes-and-analytics/what-is-a-data-lake/): AWS 关于数据湖架构、效益和组成部分的指南。
  - [Data Lake](https://martinfowler.com/bliki/DataLake.html) (Martin Fowler): 关于数据湖模式及其陷阱的概念性概述。

</details>

<details>
<summary><strong>Data Warehouse (数据仓库):</strong> 一个存储高度结构化、集成化数据的中央存储库，数据从多个不同来源过滤而来，严格针对查询和分析报告进行了优化。</summary>

它使用预定义的架构（写时模式）来维持数据质量，并为商业智能工具提供快速的查询性能。

- **标准工具:**
  - [clickhouse/clickhouse](https://github.com/clickhouse/clickhouse): 一个开源、列式存储的数据库管理系统，允许实时生成分析数据报告，充当高性能数据仓库。
  - [apache/druid](https://github.com/apache/druid): 一个用于对流式和批量数据进行亚秒级查询的高性能实时分析数据库。
- **资源:**
  - [Data Warehouse](https://en.wikipedia.org/wiki/Data_warehouse): 维基百科上关于数据仓库原则的概述。
  - [什么是数据仓库?](https://cloud.google.com/learn/what-is-a-data-warehouse?hl=zh-cn): 谷歌云关于现代分析数据库结构和功能的指南。

</details>

<details>
<summary><strong>Data Mesh (数据网格):</strong> 一种去中心化的架构，告别集中的数据湖，转而将数据视为产品，由去中心化的领域团队拥有并分发自己的数据。</summary>

它将领域驱动设计原则应用于数据管理，依靠自服务的分布式数据基础设施和联邦计算治理。

- **标准工具:**
  - [trinodb/trino](https://github.com/trinodb/trino): 一个用于大数据分析的高速分布式 SQL 查询引擎，通过跨异构源在数据所在地进行查询，帮助实现数据网格。
  - [amundsen-io/amundsen](https://github.com/amundsen-io/amundsen): 一个数据发现和元数据引擎，供领域团队发布和发现数据产品。
- **资源:**
  - [How to Move Beyond a Monolithic Data Lake to a Distributed Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html) (Zhamak Dehghani): 定义数据网格范式的原创文章。
  - [Data Mesh Principles and Logical Architecture](https://martinfowler.com/articles/data-mesh-principles.html) (Zhamak Dehghani): 深入探讨该架构的四个核心原则。

</details>

<details>
<summary><strong>Data Fabric (数据织网):</strong> 一种定义了跨混合云和多云环境的统一、自动化且智能的数据集成层的架构。</summary>

它利用激活的元数据、知识图谱和机器学习来自动化数据发现、治理和消费，无论数据存储在哪里都能将其连接起来。

- **标准工具:**
  - [linkedin/datahub](https://github.com/linkedin/datahub): 一个可扩展的元数据平台，支持数据发现、可观测性和联邦治理，充当数据织网的智能核心。
  - [apache/atlas](https://github.com/apache/atlas): 为组织提供开放的元数据管理和治理能力，以构建其数据资产目录。
- **资源:**
  - [什么是数据织网?](https://www.ibm.com/cn-zh/topics/data-fabric): IBM 关于自动化集成和元数据层的技术概述。
  - [Data Fabric](https://www.sap.com/resources/what-is-data-fabric): SAP 关于自动化数据管理设计模式的定义和市场视角。

</details>


### 部署架构模式

用于配置、交付、管理和扩展物理或云端计算资源的策略和拓扑。

<details>
<summary><strong>Blue-Green Deployment (蓝绿部署):</strong> 通过运行两个相同的生产环境（蓝色和绿色），并在新部署验证通过后将流量完全从一个路由到另一个，从而减少停机时间。</summary>

一种最小化风险的部署方法。在将新版本部署到空闲环境时，保持应用程序的旧版本在线。一旦新环境通过健康检查，网络路由器或负载均衡器立即将流量切换到新版本，如果发生故障则允许快速回滚。

- **标准工具:**
  - [argoproj/argo-rollouts](https://github.com/argoproj/argo-rollouts): 一个提供高级部署能力的 Kubernetes 控制器，自动管理蓝绿和金丝雀网络路由。
  - [kubernetes/kubernetes](https://github.com/kubernetes/kubernetes): 可以通过操作 Service 标签选择器，原生执行蓝绿部署，在不同的部署 Pod 之间立即重定向流量。
- **资源:**
  - [BlueGreenDeployment](https://martinfowler.com/bliki/BlueGreenDeployment.html) (Martin Fowler): 关于双环境路由策略的核心解释。
  - [AWS 上的蓝绿部署](https://docs.aws.amazon.com/whitepapers/latest/blue-green-deployments/introduction.html): 使用云原生负载均衡器和 DNS 路由实现此模式的最佳实践。

</details>

<details>
<summary><strong>Canary Release (金丝雀发布):</strong> 通过在向全体用户开放更新前，缓慢地将更改推送给极少数受控用户子集，以此降低风险。</summary>

一种渐进式交付模式，新代码与稳定版本并行部署。一小部分实时流量（如 5%）被路由到“金丝雀”实例。重度监控遥测数据的错误情况；如果金丝雀运行健康，则逐渐增加流量比例，直到新版本替换旧版本。

- **标准工具:**
  - [fluxcd/flagger](https://github.com/fluxcd/flagger): 一个渐进式交付工具，根据路由指标和自动化 Webhook 测试来自动提升金丝雀部署。
  - [istio/istio](https://github.com/istio/istio): 一个服务网格，提供执行精确的按百分比金丝雀发布所需的细粒度流量拆分能力。
- **资源:**
  - [CanaryRelease](https://martinfowler.com/bliki/CanaryRelease.html) (Martin Fowler): 通过渐进曝光捕捉生产缺陷的概述。
  - [部署策略](https://cloud.google.com/architecture/application-deployment-and-testing-strategies?hl=zh-cn): 谷歌云关于金丝雀与其他发布方式对比的架构分解。

</details>

<details>
<summary><strong>Rolling Update (滚动更新):</strong> 在集群中递增地用新版本的实例替换旧版本的实例，实现零停机时间。</summary>

一种依次（或分小批次）更新服务器或容器集群的部署策略。编排器关掉少量旧实例，启动新实例，等待它们变健康，然后移至下一批次，确保应用程序在过渡期间始终有足够的容量为用户提供服务。

- **标准工具:**
  - [kubernetes/kubernetes](https://github.com/kubernetes/kubernetes): Kubernetes 中的默认部署策略，原生管理 Pod 的增量替换，同时维持指定的最小可用性阈值。
  - [hashicorp/nomad](https://github.com/hashicorp/nomad): 一个灵活的工作负载编排器，提供用于管理容器化和非容器化应用的内置滚动更新策略。
- **资源:**
  - [执行滚动更新](https://kubernetes.io/zh-cn/docs/tutorials/kubernetes-basics/update/update-intro/): 关于管理渐进式实例替换的官方文档。
  - [AWS 上的滚动部署](https://docs.aws.amazon.com/whitepapers/latest/overview-deployment-options/rolling-deployments.html): 详细介绍增量集群更新机制和风险缓解策略的技术白皮书。

</details>

<details>
<summary><strong>Immutable Server / Infrastructure (不可变服务器 / 基础设施):</strong> 一种在部署后从不就地修改服务器或容器的模式；任何更改都需要构建并部署一个新实例。</summary>

一种消除配置漂移的操作范式。不再登录到运行中的服务器安装更新或调整设置，而是由部署流水线通过印模获得一个全新的、完全配置好的机器镜像。旧服务器被销毁并替换，从而保证环境完全可重现。

- **标准工具:**
  - [hashicorp/packer](https://github.com/hashicorp/packer): 一个用于从单一源配置为多个平台创建相同机器镜像的开源工具，构成了不可变虚拟机的基础。
  - [moby/moby](https://github.com/moby/moby): Docker 背后的开源项目，通过将应用及其依赖项打包到只读容器镜像中来强制执行不可变性。
- **资源:**
  - [ImmutableServer](https://martinfowler.com/bliki/ImmutableServer.html) (Martin Fowler): 关于销毁服务器而非更新服务器的概念指南。
  - [什么是不可变基础设施?](https://www.hashicorp.com/resources/what-is-mutable-vs-immutable-infrastructure): HashiCorp 关于静态配置的安全和操作效益的分解。

</details>

<details>
<summary><strong>Sidecar Pattern (边车模式):</strong> 将辅助基础设施组件（如日志记录、同步或代理）部署到与主应用容器并行运行的独立且附加的容器中。</summary>

容器化环境中广泛使用的一种架构模式。它将非业务逻辑（如指标收集、mTLS 加密或机密管理）从主应用代码中抽象出来。边车与主应用共享相同的生命周期、网络和磁盘空间，作为一个集成的支撑进程运行。

- **标准工具:**
  - [envoyproxy/envoy](https://github.com/envoyproxy/envoy): 一个高性能的 C++ 分布式代理，用作单个服务和应用，作为现代服务网格中通用的数据平面边车运行。
  - [fluent/fluent-bit](https://github.com/fluent/fluent-bit): 一个轻量级的日志处理器和转发器，经常部署为边车以收集和传输应用日志，而无需修改核心应用代码。
- **资源:**
  - [Sidecar pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/sidecar): 微软 Azure 架构中心关于隔离助手组件的指南。
  - [多容器 Pod](https://kubernetes.io/zh-cn/docs/concepts/workloads/pods/#how-pods-manage-multiple-containers): Kubernetes 文档解释了边车执行和生命周期管理的技术机制。

</details>


### 可观测性架构模式

提供对系统健康状况、性能和复杂内部状态的深度外部可见性的遥测机制。

<details>
<summary><strong>Distributed Tracing (分布式追踪):</strong> 通过在整个调用链中传递唯一的、关联的追踪 ID，跨多个分布式微服务跟踪单个请求的流程。</summary>

微服务调试的关键模式。允许工程师通过分析跨度 (Span) 和追踪 (Trace)，准确地在复杂的内部 API 调用网络中可视化延迟或错误发生的位置。

- **标准工具:**
  - [jaegertracing/jaeger](https://github.com/jaegertracing/jaeger): 一个开源的端到端分布式追踪系统，最初由 Uber 构建，用于监控和排除复杂微服务架构的故障。
  - [openzipkin/zipkin](https://github.com/openzipkin/zipkin): 一个分布式追踪系统，有助于收集排查服务架构中延迟问题所需的定时数据。
- **资源:**
  - [OpenTelemetry](https://opentelemetry.io/): CNCF 关于生成、收集和导出遥测数据（指标、日志和追踪）的标准。
  - [W3C Trace Context](https://www.w3.org/TR/trace-context/): W3C 关于标准化分布式追踪上下文标头的官方建议。

</details>

<details>
<summary><strong>Log Aggregation (日志聚合):</strong> 将来自多个不同服务和实例的本地日志文件集中并解析到一个单一的、可搜索的存储库中（如 ELK 堆栈）。</summary>

这防止了登录单个服务器读取文本文件的运维噩梦，实现了跨服务的查询、可视化以及整个集群的基于日志的告警。

- **标准工具:**
  - [fluent/fluentd](https://github.com/fluent/fluentd): 一个用于统一日志层的开源数据收集器，支持数据收集和消费的统一。
  - [grafana/loki](https://github.com/grafana/loki): 一个受 Prometheus 启发、水平可扩展、高可用、多租户的日志聚合系统。
- **资源:**
  - [The Twelve-Factor App: Logs](https://12factor.net/logs): 将日志视为事件流的核心方法论。
  - [日志架构](https://kubernetes.io/zh-cn/docs/concepts/cluster-administration/logging/): Kubernetes 官方关于集群级日志架构的文档。

</details>

<details>
<summary><strong>Metrics Collection (Time-Series) (指标收集 / 时序数据):</strong> 随时间收集结构化的数值数据，以监控系统健康基准并在突破阈值时触发自动告警。</summary>

与日志不同，指标是经过数学聚合且高度压缩的，允许系统每秒摄取数百万个数据点，用以跟踪长期的 CPU 使用率、内存限制和 HTTP 错误率。

- **标准工具:**
  - [prometheus/prometheus](https://github.com/prometheus/prometheus): 行业标准的系统和服务监控系统，具有多维数据模型和强大的查询语言 (PromQL)。
  - [influxdata/telegraf](https://github.com/influxdata/telegraf): 一个插件驱动的服务器代理，用于收集和报告指标，常用作数据收集守护进程。
- **资源:**
  - [监控分布式系统](https://sre.google/sre-book/monitoring-distributed-systems/): 谷歌 SRE 著作中的权威指南。
  - [Prometheus Concepts](https://prometheus.io/docs/concepts/data_model/): 关于序数据结构和指标类型的技术文档。

</details>

<details>
<summary><strong>Synthetic Monitoring (合成监控):</strong> 使用自动化脚本不断模拟典型的用户交互，以便主动从外部检测应用程序的性能下降或可用性问题。</summary>

通常被称为黑盒监控。它从用户角度确认关键的用户路径（如登录或完成结账）是否正在活跃运行，而不管内部服务器指标报告了什么。

- **标准工具:**
  - [prometheus/blackbox_exporter](https://github.com/prometheus/blackbox_exporter): 允许通过 HTTP、HTTPS、DNS、TCP 和 ICMP 对端点进行黑盒探测，以生成合成的正常运行时间指标。
  - [checkly/checkly-cli](https://github.com/checkly/checkly-cli): 一个开源 CLI，用于使用 Playwright 编码合成监控检查，以模拟复杂的浏览器交互。
- **资源:**
  - [Synthetic Monitoring Overview](https://en.wikipedia.org/wiki/Synthetic_monitoring): 维基百科上关于主动监控概念的分解。
  - [实用告警](https://sre.google/sre-book/practical-alerting/): 谷歌 SRE 著作中讨论白盒与黑盒监控平衡的章节。

</details>


### DevOps 架构模式

通过重度自动化、持续交付流水线和程序化基础设施管理，架起软件开发与 IT 运维桥梁的范式。

<details>
<summary><strong>GitOps:</strong> 一种以 Git 仓库作为单一事实来源，通过拉取请求 (Pull Request) 自动管理基础设施配置和软件部署的范式。</summary>

它维持集群或基础设施的状态与存储在 Git 中的声明式配置相匹配。如果发生漂移，GitOps 管理器会自动将系统协调回 Git 状态。

- **标准工具:**
  - [argoproj/argo-cd](https://github.com/argoproj/argo-cd): 一个声明式的、适用于 Kubernetes 的 GitOps 持续交付工具，可自动使应用状态与 Git 仓库中定义的期望状态同步。
  - [fluxcd/flux2](https://github.com/fluxcd/flux2): 一套开放且可扩展的 Kubernetes 持续和渐进式交付解决方案，充当 GitOps 工具包的核心实现。
- **资源:**
  - [什么是 GitOps?](https://about.gitlab.com/topics/gitops/): GitLab 提供的关于 Git 驱动运维原则、工作流和效益的指南。
  - [GitOps Principles](https://opengitops.dev/): 由 CNCF 内的 OpenGitOps 工作组维护的供应商中立标准和原则。

</details>

<details>
<summary><strong>Infrastructure as Code (IaC, 基础设施即代码):</strong> 通过版本控制、机器可读的定义文件而非手动配置来管理和提供完整的计算环境。</summary>

这种方法将软件工程实践（如测试、代码审查和版本控制）引入到基础设施管理中，消除了服务器环境中的“在我的机器上能运行”的问题。

- **标准工具:**
  - [hashicorp/terraform](https://github.com/hashicorp/terraform): 一个开源的基础设施即代码软件工具，提供一致的 CLI 工作流来声明式地管理数百个云服务。
  - [pulumi/pulumi](https://github.com/pulumi/pulumi): 一个现代的 IaC 平台，允许工程师使用熟悉的编程语言（如 TypeScript、Python 和 Go）而非域特定语言来定义云基础设施。
- **资源:**
  - [Infrastructure as Code](https://martinfowler.com/bliki/InfrastructureAsCode.html) (Martin Fowler): 关于像处理软件一样处理服务器的概念分解。
  - [什么是基础设施即代码?](https://docs.aws.amazon.com/whitepapers/latest/introduction-devops-aws/infrastructure-as-code.html): AWS 文档详细说明了代码化基础设施的操作效益和生命周期。

</details>

<details>
<summary><strong>Continuous Integration / Continuous Deployment (CI/CD, 持续集成 / 持续部署):</strong> 一种自动化的流水线模式，它合并开发人员的代码、运行自动化测试，并将最终生成的构建直接推送到生产环境。</summary>

持续集成确保代码更改被频繁地合并和验证，而持续部署则在无需人工干预的情况下，自动将每一个通过测试的构建发布给用户。

- **标准工具:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): 提供行业标准、完全集成的 CI/CD 流水线引擎，管理从代码提交到部署的整个软件生命周期。
  - [tektoncd/pipeline](https://github.com/tektoncd/pipeline): 一个用于创建持续集成和交付系统的云原生框架，直接在 Kubernetes 集群内实现流水线执行的标准化。
- **资源:**
  - [Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html) (Martin Fowler): 频繁代码集成实践及其效益指南。
  - [CI/CD Concepts](https://www.redhat.com/en/topics/devops/what-is-ci-cd): Red Hat 的技术概述，解释了持续集成、持续交付和持续部署之间的界限。

</details>


### FinOps 架构模式

严格针对云财务管理进行了优化的架构设计和工程实践，使多变的云基础设施成本变得高度可见、可预测，并与业务价值直接挂钩。

<details>
<summary><strong>Resource Tagging / Labeling Strategy (资源标记 / 标签策略):</strong> 在所有云资源上强制执行严格且一致的元数据架构，以准确地将基础设施成本映射到具体的团队、环境或业务领域。</summary>

一项 FinOps 核心实践，要求每一个配置的云资产都必须附带键值元数据（如 `CostCenter: Marketing` 或 `Environment: Production`）。这能将难以解读的大量集中式云账单转化为精准的、可按业务单元分析的分类财务数据。

- **标准工具:**
  - [cloud-custodian/cloud-custodian](https://github.com/cloud-custodian/cloud-custodian): 一个适用于云环境的无状态规则引擎，可以自动强制标签合规、对违例进行告警，并终止未标记资源以防止未跟踪的支出。
  - [infracost/infracost](https://github.com/infracost/infracost): 显示基础设施即代码项目的云成本估算，在资源配置前就直接在 CI/CD 流水线中依靠资源标签映射潜在的未来费用。
- **资源:**
  - [资源标记策略最佳实践](https://docs.aws.amazon.com/whitepapers/latest/tagging-best-practices/tagging-best-practices.html): AWS 关于设计、实现和治理有效资源标签的白皮书。
  - [Google Cloud Tagging Overview](https://cloud.google.com/resource-manager/docs/tags/tags-overview): 谷歌云关于为成本分配和访问控制构建和治理资源标签的文档。

</details>

<details>
<summary><strong>Showback / Chargeback (成本分摊 / 费用回扣):</strong> 能够将中央 IT 和云运维成本分配回具体消耗它们的业务单元的架构能力，或是为了可见性（showback），或是为了内部计费（chargeback）。</summary>

将云支出从集中的 IT 开销支出转变为去中心化的问责模式。Showback 向各个工程团队报告精确成本以驱动财务意识，而 Chargeback 则与会计软件集成，从部门预算中正式扣除这些基础设施费用。

- **标准工具:**
  - [opencost/opencost](https://github.com/opencost/opencost): 一个为 Kubernetes 打造的开源成本监控工具，允许组织衡量并将共享集群成本分配回各个命名空间、部署或标签。
  - [kubecost/cost-analyzer-helm-chart](https://github.com/kubecost/cost-analyzer-helm-chart): Kubecost 的 Helm 配置，该平台基于 OpenCost 构建，为云原生环境提供颗粒化的成本可见性、费用报告和优化建议。
- **资源:**
  - [AWS 云财务管理](https://aws.amazon.com/cn/aws-cost-management/): AWS 关于成本分配、分摊和财务问责的工具与策略概述。
  - [什么是 FinOps?](https://www.ibm.com/cn-zh/topics/finops): IBM 关于云财务管理的技术概述，侧重于成本分配和组织层面的费用回扣模型。

</details>


### 联邦架构模式

去中心化的系统模型，支持多个自治实体或节点在不依赖单一中央管理机构的情况下，利用共享标准实现安全互操作。

<details>
<summary><strong>Data Federation (数据联邦):</strong> 在不需要物理移动或复制数据的情况下，定义一个跨多个自治数据存储的统一实时查询接口。</summary>

一种创建虚拟数据库的模式，抽象了底层存储的复杂性，允许用户像对单一位置查询一样来查询数据。这减少了对昂贵的抽取、转换和加载 (ETL) 流水线的需求，使得查询始终能直接从源系统返回最新数据。

- **标准工具:**
  - [prestodb/presto](https://github.com/prestodb/presto): 一个开源分布式 SQL 查询引擎，用于对各种规模的数据源运行交互式分析查询，原生支持跨异构数据库的联邦查询。
  - [apache/drill](https://github.com/apache/drill): 一个适用于 Hadoop、NoSQL 和云存储的无架构 SQL 查询引擎，允许用户就地查询复杂格式的数据，而无需定义集中式架构。
- **资源:**
  - [Federated Database System](https://en.wikipedia.org/wiki/Federated_database_system): 维基百科上关于虚拟数据库集成架构和历史的概述。
  - [联邦查询简介](https://cloud.google.com/bigquery/docs/federated-queries-intro?hl=zh-cn): 谷歌云文档，详情说明了在不移动数据的情况下查询外部数据源的机制和架构效益。

</details>

<details>
<summary><strong>GraphQL Federation (GraphQL 联邦):</strong> 一种 API 网关模式，它将多个独立的 GraphQL API（子图）组合成一个统一的、面向客户端的架构（超图）。</summary>

一种允许不同领域的团队独立开发、部署和扩展各自 API 部分的模式。它为前端客户端提供单一端点，通过一次请求即可获取所有相关数据，抽象了底层微服务架构的复杂性和路由逻辑。

- **标准工具:**
  - [apollographql/federation](https://github.com/apollographql/federation): 官方声明式架构和开源工具，用于从多个子图构建、管理和扩展统一的超图。
  - [wundergraph/cosmo](https://github.com/wundergraph/cosmo): 一个用于 GraphQL 联邦的开源工具链和路由器，用于跨分布式团队构建、管理和监测统一的 API。
- **资源:**
  - [Introduction to Apollo Federation](https://www.apollographql.com/docs/federation/): 关于子图架构和超图生成的详细技术文档。
  - [GraphQL Mesh Federation](https://the-guild.dev/graphql/mesh/docs): 关于使用 GraphQL Mesh 将多个异构 API 统一为单一联邦 GraphQL 架构的技术文档。

</details>

<br>

[![回到顶部](https://img.shields.io/badge/-回到顶部-6f42c1?style=for-the-badge&logoColor=white)](#目录)

## 企业架构框架

这些是管理大型公司如何将其业务和 IT 战略联系起来的方法。它们在狭义上不是软件架构；相反，它们定义了业务流程、数据和技术工具如何协同工作。这些框架有助于将业务目标与技术工作结合起来，以支持长期增长和技术变革。

<details>
<summary><strong>Business Architecture (业务架构):</strong> 定义业务战略、治理、组织和关键业务流程。</summary>

企业业务模型和企业战略与企业业务功能之间的桥梁。它展示了组织如何创造价值，并将所有后续 IT 架构直接与公司目标对齐。

- **标准工具:**
  - [leanix/leanix](https://www.leanix.net/): 一个现代的企业架构管理 (EAM) 平台，广泛用于将业务能力与 IT 景观对齐，并管理投资组合转型。
  - [signavio/process-manager](https://www.signavio.com/): 企业级业务流程建模和挖掘工具（现为 SAP 的一部分），用于绘制复杂的业务架构和工作流。
- **资源:**
  - [Business Architecture Basics](https://bizzdesign.com/blog/what-is-business-architecture/): Bizzdesign 提供的该学科价值、结构和核心映射技术的概述。
  - [Business Architecture](https://en.wikipedia.org/wiki/Business_architecture): 维基百科上关于该学科、其历史以及与其他企业框架关系的概述。

</details>

<details>
<summary><strong>Information Architecture / Data Architecture (信息架构 / 数据架构):</strong> 描述组织逻辑和物理数据资产以及数据管理资源的结构。</summary>

侧重于数据如何在整个企业范围内收集、存储、集成和使用。它将数据视为极具价值的、受治理的公司资产，而不仅仅是单个应用的产物。

- **标准工具:**
  - [schemaspy/schemaspy](https://github.com/schemaspy/schemaspy): 一个开源工具，通过分析数据库元数据生成复杂物理数据架构的可视化表示。
  - [collibra/data-intelligence](https://www.collibra.com/): 企业数据治理、隐私和编目的平台，对于执行企业范围内信息架构战略至关重要。
- **资源:**
  - [DAMA-DMBOK](https://www.dama.org/cpages/body-of-knowledge): 数据管理知识体系，数据架构和治理的标准框架。
  - [什么是数据架构?](https://www.ibm.com/cn-zh/topics/data-architecture): IBM 关于构建和管理企业数据资产的技术概述。

</details>

<details>
<summary><strong>Application Architecture (应用架构):</strong> 定义要部署的单个应用的蓝图、它们之间的交互以及它们与核心业务流程的关系。</summary>

绘制公司的整个软件投资组合，识别冗余，管理技术债务，并验证软件解决方案是否直接支持记录在案的业务能力。

- **标准工具:**
  - [archimatetool/archi](https://github.com/archimatetool/archi): 一个用于创建 ArchiMate 模型的开源建模工具包，广泛用于绘制复杂的应用架构及其相互依赖关系。
  - [bizzdesign/horizzon](https://bizzdesign.com/): 一个擅长将应用组合与业务目标及基础技术层联系起来的企业架构平台。
- **资源:**
  - [ArchiMate](https://en.wikipedia.org/wiki/ArchiMate): 维基百科上关于开放且独立的企业架构建模语言的概述。
  - [AWS Architecture Center](https://aws.amazon.com/cn/architecture/): 来自亚马逊云科技的参考应用架构、最佳实践和投资组合现代化模式的官方库。

</details>

<details>
<summary><strong>Technology Architecture (技术架构):</strong> 描述支持业务、数据和应用服务所需的逻辑软件和硬件能力（如 IT 基础设施、中间件、网络）。</summary>

详情说明托管企业应用和数据的物理和虚拟化硬件、云计算环境及网络拓扑的核心层。

- **标准工具:**
  - [structurizr/structurizr](https://github.com/structurizr): 基于 C4 模型构建的软件架构可视化工具，非常有助于弥合应用设计与底层技术架构之间的鸿沟。
  - [drawio/drawio](https://github.com/jgraph/drawio): 一个开源绘图工具，在行业内广泛用于起草标准化的基础设施、网络和技术架构布局。
- **资源:**
  - [The C4 Model](https://c4model.com/): 一种“抽象优先”的架构图绘制方法，从系统上下文一直到物理技术层。
  - [ITIL Service Management](https://www.axelos.com/certifications/itil-service-management): 使物理 IT 基础设施和技术服务与业务需求保持对齐的全球标准框架。

</details>

<details>
<summary><strong>Security Architecture (安全架构):</strong> 保护企业信息和 IT 资产的过程和控制措施。</summary>

超越了简单的防火墙，定义了整合在所有其他架构领域的企业范围风险管理、身份治理、合规执行和威胁缓解设计。

- **标准工具:**
  - [owasp/threat-dragon](https://github.com/OWASP/threat-dragon): 一个开源威胁建模工具，用于设计安全架构并在企业生命周期早期识别结构性漏洞。
  - [osquery/osquery](https://github.com/osquery/osquery): 一个操作系统分析框架，将基础设施暴露为高性能关系数据库，以实现深度的安全可见性和合规性审计。
- **资源:**
  - [SABSA Framework](https://sabsa.org/): 业务驱动的企业安全架构领先方法论（Sherwood Applied Business Security Architecture）。
  - [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework): 美国政府用于维护企业 IT 架构安全和管理结构性风险的标准。

</details>

<details>
<summary><strong>Geospatial Architecture (地理空间架构):</strong> 将位置数据和服务整合到企业架构中。</summary>

对物流、农业和政府部门至关重要的专业领域，侧重于空间数据（地图、坐标、地形）如何在企业范围内捕获、处理、标准化和交付。

- **标准工具:**
  - [postgis/postgis](https://github.com/postgis/postgis): PostgreSQL 的空间数据库扩展，是许多企业级地理空间系统的核心数据架构。
  - [geoserver/geoserver](https://github.com/geoserver/geoserver): 一个用于共享、处理和编辑完全基于开放标准构建的复杂地理空间数据的开源服务器。
- **资源:**
  - [OGC Reference Model](https://www.ogc.org/standards/orm): 开放地理空间联盟 (OGC) 的框架，详细说明了空间数据集成的标准接口和协议。
  - [Location Intelligence](https://en.wikipedia.org/wiki/Location_intelligence): 维基百科上关于利用空间数据进行业务架构和运维智能的概述。

</details>

<details>
<summary><strong>Social Architecture (社会架构):</strong> 模拟企业通过社交媒体和其他渠道与个人及社区的互动。</summary>

一个新兴领域，绘制组织如何从结构上促进内部协作、知识共享和外部社区参与，有意地使人类网络与 IT 系统保持对齐。

- **标准工具:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): 一个开源、自托管的即时通讯平台，用于为大型组织构建安全的内部社交和协作架构。
  - [discourse/discourse](https://github.com/discourse/discourse): 开源讨论平台的现代标准，用于构建弹性的外部社区架构和支持网络。
- **资源:**
  - [Social Architecture](https://en.wikipedia.org/wiki/Social_architecture): 关于设计人群交互和数字社区构建系统的理论概述。
  - [Digital Ecosystem](https://en.wikipedia.org/wiki/Digital_ecosystem): 关于企业如何与外部参与者构建分布式、自适应且协作的网络的分散。

</details>

<br>

[![回到顶部](https://img.shields.io/badge/-回到顶部-6f42c1?style=for-the-badge&logoColor=white)](#目录)
