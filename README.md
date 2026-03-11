<div align="center">

<h1>Awesome Architecture Patterns</h1>
Choose a language

[![English](https://img.shields.io/badge/-English-blue.svg)](README.md) [![Español](https://img.shields.io/badge/-Español-red.svg)](README.es.md) [![中文](https://img.shields.io/badge/-中文-lightgrey.svg)](README.zh.md)

</div>

A multi-level taxonomy of software architecture and design patterns. This repository attempts to categorize the structural building blocks of software engineering, scaling from macro-level cloud topologies down to micro-level object interactions, while also covering cross-cutting concerns and high-level enterprise frameworks.

My goal is to build a centralized index of resources, documentation, and implementation examples for every architectural pattern and variant available.

## References

This compilation synthesizes and organizes concepts from several foundational software engineering works and industry standards:
* **Pattern-Oriented Software Architecture (POSA)** by Frank Buschmann, Regine Meunier, Hans Rohnert, Peter Sommerlad, and Michael Stal.
* **The C4 Model** for visualizing software architecture by Simon Brown.
* **Enterprise Integration Patterns** by Gregor Hohpe and Bobby Woolf.
* **Design Patterns: Elements of Reusable Object-Oriented Software (Gang of Four)** by Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides.
* **Domain-Driven Design (DDD)** by Eric Evans.
* **Clean Architecture** by Robert C. Martin.

## Table of Contents

* [Layer 1: System Architecture Patterns](#layer-1-system-architecture-patterns)
* [Layer 2: Enterprise Integration Patterns](#layer-2-enterprise-integration-patterns)
* [Layer 3: Application Architecture Patterns](#layer-3-application-architecture-patterns)
* [Layer 4: Software Design Patterns](#layer-4-software-design-patterns)
* [Cross-Cutting Architectural Concerns](#cross-cutting-architectural-concerns)
* [Enterprise Architecture Frameworks](#enterprise-architecture-frameworks)

<details>
<summary><h2>Layer 1: System Architecture Patterns</h2></summary>

<details>
<summary><h3>Core Application Deployment Topologies</h3></summary>

Broad structural paradigms defining how the primary functional units of an application are packaged, scaled, and deployed over underlying infrastructure.

<details>
<summary><strong>Monolithic Architecture:</strong> A unified model where the entire application is built, packaged, and deployed as a single unit.</summary>

Historically, the monolith was simply how software was built before distributed cloud computing became accessible. Every component, from UI rendering to database access, shares the same memory space and deployment pipeline. While heavily criticized during the microservices boom for becoming tangled "big balls of mud," the pattern has seen a massive resurgence (often dubbed the "Majestic Monolith") as companies realize that single-process architectures drastically reduce operational complexity, network latency, and infrastructure costs for all but the largest engineering teams.

- **Examples:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): The core GitLab monolithic application built heavily on Ruby on Rails.
  - [discourse/discourse](https://github.com/discourse/discourse): The widely used open-source discussion platform monolith.
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): The primary server application for the decentralized social network.
- **Resources:**
  - [MonolithFirst](https://martinfowler.com/bliki/MonolithFirst.html) by Martin Fowler: An essay on why starting with a monolith is often the best approach.
  - [The Majestic Monolith](https://m.signalvnoise.com/the-majestic-monolith/) by DHH: An argument for the benefits of monolithic architectures by the creator of Ruby on Rails.

</details>

<details>
<summary><strong>Modular Monolith Architecture:</strong> A monolith internally structured into modules based on business capabilities, allowing for potential extraction into microservices later.</summary>

This pattern gained massive traction as a pragmatic reaction to the operational nightmares of distributed microservices. It applies the strict boundary contexts of Domain-Driven Design (DDD) to a single deployment unit. Teams can work independently on their isolated modules, bypassing the management of network failures, eventual consistency, or complex Kubernetes clusters. It became highly popularized by tech giants like Shopify, who proved that with strict static analysis tooling, a monolithic codebase can scale to thousands of developers without degrading into a tightly coupled mess.

- **Examples:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): A full TypeScript reference application implementing a modular monolith for an e-commerce domain.
  - [danilofes/modular-monolith-architecture](https://github.com/danilofes/modular-monolith-architecture): A Java/Spring Boot reference application demonstrating a modular monolith for an online store.
  - [kgrzybek/modular-monolith-with-ddd](https://github.com/kgrzybek/modular-monolith-with-ddd): A comprehensive .NET reference application using strict Domain-Driven Design boundaries.
- **Resources:**
  - [Deconstructing the Monolith](https://shopify.engineering/deconstructing-monolith-designing-software-that-grows) by Shopify Engineering: A detailed case study on Shopify's transition to a modular monolith.
  - "Modular Monoliths" by Simon Brown: Structural guidelines for maintaining clean boundaries in a single deployment unit.

</details>

<details>
<summary><strong>Microservices Architecture:</strong> An application decomposed into small, loosely coupled, independently deployable services, each with its own database.</summary>

Emerging in the early 2010s from hyper-growth companies like Netflix and Amazon, microservices became the defining architecture of the cloud-native era. The primary driver was organizational scaling. By breaking the system into isolated services, independent teams could deploy code without coordinating with a central release manager. While it solves organizational bottlenecks, it introduces immense technical complexity regarding distributed data transactions, network reliability, and observability, making it a double-edged sword for smaller engineering organizations.

- **Examples:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Google's 11-tier polyglot reference application (Online Boutique) for Kubernetes and gRPC.
  - [dotnet/eShop](https://github.com/dotnet/eShop): Microsoft's official cross-platform .NET reference application for microservices and containers.
  - [microservices-demo/microservices-demo](https://github.com/microservices-demo/microservices-demo): The "Sock Shop" reference application designed to teach polyglot microservice deployments.
- **Resources:**
  - "Building Microservices: Designing Fine-Grained Systems" by Sam Newman: The foundational book on designing, deploying, and maintaining microservices.
  - [Microservices Resource Guide](https://martinfowler.com/microservices/) by Martin Fowler: A comprehensive collection of articles and definitions.

</details>

<details>
<summary><strong>Service-Oriented Architecture (SOA):</strong> Coarse-grained, reusable services provide business functionality via a communications protocol, often mediated by an Enterprise Service Bus (ESB).</summary>

Dominating the enterprise landscape in the early 2000s, SOA was the precursor to microservices. SOA focused on integrating massive, monolithic enterprise applications (like ERPs and CRMs) across a company using standardized protocols (typically SOAP and XML). It heavily relied on "smart pipes": centralized Enterprise Service Buses (ESBs) that handled routing, transformation, and security. Ultimately, SOA's reputation suffered due to the heavy vendor lock-in, bloated middleware, and complex governance required to maintain it, paving the way for the "dumb pipes, smart endpoints" philosophy of modern distributed systems.

- **Examples:**
  - [apereo/cas](https://github.com/apereo/cas): The Central Authentication Service, a standalone enterprise application providing single sign-on services, acting as a core node in a broader Service-Oriented Architecture.
- **Resources:**
  - "SOA in Practice: The Art of Distributed System Design" by Nicolai M. Josuttis: A practical guide to implementing SOA in enterprise environments.
  - [Service-Oriented Architecture](https://www.ibm.com/topics/soa) by IBM: An architectural overview and history of SOA patterns.

</details>

<details>
<summary><strong>Serverless Architecture (Function-as-a-Service / FaaS):</strong> Applications are divided into ephemeral, event-triggered functions where the cloud provider dynamically manages the allocation and provisioning of servers.</summary>

Popularized by the launch of AWS Lambda in 2014, serverless represents the ultimate shift of operational responsibility to the cloud provider. Developers write isolated functions that execute only in response to specific events (HTTP requests, database triggers, message queues) and scale to zero when idle. While it radically reduces infrastructure management and baseline costs, it introduces new challenges like cold start latency, vendor lock-in, and complex debugging across highly distributed, ephemeral execution environments.

- **Examples:**
  - [serverless/examples](https://github.com/serverless/examples): A vast collection of real-world examples using the Serverless Framework across AWS, Azure, and GCP.
  - [aws-samples/aws-serverless-workshops](https://github.com/aws-samples/aws-serverless-workshops): AWS's official repository for serverless training, patterns, and reference architectures.
  - [Azure-Samples/functions-quickstart](https://github.com/Azure-Samples/functions-quickstart): Microsoft's official template and sample repository for Azure Functions.
- **Resources:**
  - [Serverless Architectures](https://martinfowler.com/articles/serverless.html) by Mike Roberts: A deep dive into the traits and benefits of serverless computing.
  - "Serverless Architectures on AWS" by Peter Sbarski: A comprehensive guide to building serverless applications.

</details>

<details>
<summary><strong>Cell-Based Architecture:</strong> The system is divided into isolated, self-contained "cells" to limit failure blast radius and enable massive scale.</summary>

Originally pioneered by cloud providers like AWS to manage global infrastructure scale (using Availability Zones and deployment "stamps"), cell-based architecture was formalized as a composable software pattern by organizations like WSO2. The system is divided into functional "cells": independent, deployable units containing their own API gateway, logic, and data. If a cell fails or is overwhelmed by traffic, the blast radius is strictly contained to that specific cell or routing partition, ensuring the broader system remains online. It is the architecture of choice for systems requiring hyper-resilience and massive multi-tenancy.

- **Examples:**
  - *Note on Examples:* Cell-Based Architecture is a macro-level cloud infrastructure deployment paradigm used by massive organizations to manage global traffic and blast radiuses. Because it relies on orchestrating physical infrastructure zones and routing layers rather than a specific codebase structure, there are no single, deployable open-source application repositories that represent it.
- **Resources:**
  - [Cell-Based Architecture Reference](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) by Asanka Abeysinghe: The original whitepaper defining the pattern.
  - [Workload Isolation Using Shuffle Sharding](https://aws.amazon.com/builders-library/workload-isolation-using-shuffle-sharding/) by AWS Architecture Blog: Amazon's documentation on limiting blast radius using cell-based concepts.

</details>

</details>


<details>
<summary><h3>Network & Node Distribution Topologies</h3></summary>

High-level models describing how processing tasks, physical resources, and network traffic are partitioned across distinct logical nodes.

<details>
<summary><strong>Client-Server Architecture:</strong> A distributed model partitioning tasks between resource providers (servers) and service requesters (clients).</summary>

The foundational model of the modern web. In this architecture, centralized resource providers (servers) handle data storage, processing, and business logic, while service requesters (clients) consume those resources. It simplifies data management and security by keeping sensitive operations centralized. As systems scale, the server becomes the primary bottleneck, requiring load balancing and horizontal scaling to maintain performance under heavy client traffic.

- **Examples:**
  - [owncloud/core](https://github.com/owncloud/core): The core server for the OwnCloud platform, demonstrating a server providing resources to distributed clients.
  - [metabase/metabase](https://github.com/metabase/metabase): An open-source business intelligence server that serves dashboards and data to web clients.
- **Resources:**
  - [Client-Server Overview](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Client-Server_overview) by MDN Web Docs: A breakdown of how client-server web architectures function.
  - "Client/Server Survival Guide" by Robert Orfali: A textbook on designing distributed client-server systems.

</details>

<details>
<summary><strong>N-Tier Architecture:</strong> A client-server model where presentation, application, and data tiers are physically separated onto different machines.</summary>

A physical and logical extension of the client-server model. The system is physically separated into distinct tiers, most commonly presentation, application logic, and data storage. Each tier runs on its own infrastructure and only communicates with the tier immediately adjacent to it. This isolation allows teams to scale the database independently from the web servers and provides an extra layer of security, as the presentation layer cannot directly access the data layer.

- **Examples:**
  - [nopSolutions/nopCommerce](https://github.com/nopSolutions/nopCommerce): An open-source e-commerce cart structured as a multi-tier ASP.NET application.
  - [spring-projects/spring-petclinic](https://github.com/spring-projects/spring-petclinic): The reference application demonstrating a 3-tier architecture using the Spring framework.
- **Resources:**
  - [N-tier architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/n-tier) by Microsoft Azure Architecture Center: A guide on structuring and deploying N-tier applications in the cloud.
  - "Patterns of Enterprise Application Architecture" by Martin Fowler: Covers the layering patterns that form the basis of N-tier systems.

</details>

<details>
<summary><strong>Peer-to-Peer (P2P) Architecture:</strong> A decentralized network where all nodes have equal privilege and share resources directly without a central server.</summary>

A decentralized network topology where every node (peer) acts simultaneously as both a client and a server. Nodes share resources like bandwidth, storage, or processing power directly with one another, bypassing a centralized authority. It is highly resilient to single points of failure and scales organically, as every new user adds capacity to the network. It requires complex routing algorithms to locate data across distributed nodes.

- **Examples:**
  - [ipfs/kubo](https://github.com/ipfs/kubo): The reference implementation of the InterPlanetary File System (IPFS), a decentralized P2P storage network.
  - [bitcoin/bitcoin](https://github.com/bitcoin/bitcoin): The reference implementation of the decentralized P2P digital currency network.
  - [webtorrent/webtorrent](https://github.com/webtorrent/webtorrent): A streaming torrent client that brings P2P networking directly to web browsers via WebRTC.
- **Resources:**
  - [How IPFS Works](https://docs.ipfs.tech/concepts/how-ipfs-works/): Official documentation detailing content addressing and P2P routing mechanisms.
  - "Peer-to-Peer: Harnessing the Power of Disruptive Technologies" by Andy Oram: A book exploring the design and impact of decentralized networks.

</details>

<details>
<summary><strong>Hub and Spoke Architecture:</strong> A centralized network or messaging topology where a central hub acts as the single point of transit routing traffic and data to distributed nodes (spokes).</summary>

A centralized routing topology designed to simplify network connections. All nodes (spokes) connect directly to a single central router or message broker (the hub). The hub handles all message routing, filtering, and delivery. It drastically reduces the number of connections required in a large system but makes the hub a critical bottleneck that must be highly available.

- **Examples:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): A central collaboration server that acts as a hub, routing messages, webhooks, and integrations between various third-party application spokes.
  - [signalapp/Signal-Server](https://github.com/signalapp/Signal-Server): The server repository for Signal, functioning as a hub that securely routes encrypted messages between mobile client spokes.
- **Resources:**
  - [Hub-and-spoke network topology](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/hybrid-networking/hub-spoke) by Microsoft Azure: A guide to applying this topology for enterprise cloud networking.
  - [Message Broker Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageBroker.html) by Gregor Hohpe: The architectural theory behind using a central hub for application integration.

</details>

<details>
<summary><strong>Edge Computing Architecture:</strong> Processes data near the source (on edge nodes) to reduce latency and bandwidth use.</summary>

A distributed computing paradigm that brings computation and data storage closer to the physical location where it is needed. Processing happens on local edge nodes like routers, base stations, or local servers. It drastically reduces latency, conserves backhaul bandwidth, and enables real-time processing for applications requiring immediate feedback.

- **Examples:**
  - [home-assistant/core](https://github.com/home-assistant/core): A local home automation platform that processes data entirely on the edge node (a local server) to ensure zero latency and offline functionality.
  - [pi-hole/pi-hole](https://github.com/pi-hole/pi-hole): A network-level application deployed on local edge hardware to process and filter DNS requests before they leave the local network.
- **Resources:**
  - [What is Edge Computing?](https://www.cloudflare.com/learning/serverless/glossary/what-is-edge-computing/) by Cloudflare: An explanation of edge architectures and their benefits over centralized cloud processing.
  - "Edge Computing: Fundamentals, Advances and Applications" by K. Anitha Kumari: A look at edge computing models.

</details>

<details>
<summary><strong>IoT Gateway Architecture:</strong> Uses a local gateway to aggregate, filter, and route data from devices to the cloud.</summary>

A specialized topology for managing arrays of constrained hardware devices. A local gateway device sits physically close to the sensors and actuators, acting as an intermediary between the local device network and the wider internet or cloud. The gateway aggregates raw telemetry, filters out noise, handles local protocol translation, and executes offline control logic when the internet connection drops.

- **Examples:**
  - [edgexfoundry/edgex-go](https://github.com/edgexfoundry/edgex-go): The core implementation of EdgeX Foundry, an open-source IoT edge gateway framework.
  - [ThingsBoard/thingsboard-gateway](https://github.com/ThingsBoard/thingsboard-gateway): An open-source IoT gateway that integrates devices into the central ThingsBoard platform.
- **Resources:**
  - [AWS IoT Greengrass Architecture](https://docs.aws.amazon.com/greengrass/v2/developerguide/what-is-iot-greengrass.html): AWS documentation explaining how IoT gateways bring cloud-level processing to local devices.
  - "Building the Internet of Things" by Maciej Kranz: Covers the architecture and deployment of IoT systems, including gateway patterns.

</details>

</details>


<details>
<summary><h3>Component Interaction & Layering Topologies</h3></summary>

Structural organizations that define how internal modules, execution tiers, or processing steps are arranged and invoke one another.

<details>
<summary><strong>Layered Architecture:</strong> Organizes code into horizontal tiers (presentation, business logic, data access) where each layer communicates only with the layer directly below it.</summary>

The standard for traditional business applications. It enforces a strict separation of concerns by stacking logical tiers. Typically divided into presentation, business logic, and data access layers. Each layer relies exclusively on the layer immediately below it, creating a unidirectional flow of dependencies. It simplifies initial development and testing, though it can lead to "sinkhole anti-patterns" where requests simply pass through layers without any real processing.

- **Examples:**
  - [spring-projects/spring-petclinic](https://github.com/spring-projects/spring-petclinic): The standard Spring reference application, demonstrating a classic 3-tier layered architecture (Web, Service, Repository).
  - [nopSolutions/nopCommerce](https://github.com/nopSolutions/nopCommerce): An open-source e-commerce platform structured as a layered ASP.NET application.
- **Resources:**
  - "Software Architecture Patterns" by Mark Richards: The chapter on Layered Architecture provides a breakdown of isolated vs. open layers.
  - [Software Architecture Patterns: Layered Architecture](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch01.html) by O'Reilly Media: An explanation of the Layered Architecture pattern and its constraints.

</details>

<details>
<summary><strong>Microkernel Architecture (Plug-in Architecture):</strong> A minimal core system with fundamental logic, surrounded by independent plug-in modules that provide extensible features.</summary>

Designed for extreme extensibility. It relies on a minimal core system that handles fundamental operations and lifecycle management. All extended features, custom logic, and integrations are pushed into independent, isolated plug-in modules. This allows third-party developers to add massive amounts of functionality without modifying the core codebase. It is the dominant architecture for IDEs, web browsers, and task orchestration tools.

- **Examples:**
  - [microsoft/vscode](https://github.com/microsoft/vscode): A core editor engine extended almost entirely by its massive ecosystem of independent plugins.
  - [eclipse-jdt/eclipse.jdt.core](https://github.com/eclipse-jdt/eclipse.jdt.core): The core Java tooling for Eclipse, built heavily on the OSGi microkernel pattern.
- **Resources:**
  - "Software Architecture Patterns" by Mark Richards: Detailed breakdown of the Microkernel pattern and its use cases.
  - [Pattern: Microkernel Architecture](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch03.html) by O'Reilly Media: An explanation of core systems versus plug-in components.

</details>

<details>
<summary><strong>Pipe-and-Filter Architecture:</strong> Processes data streams through independent processing steps (filters) connected by channels (pipes).</summary>

The classic data processing pipeline. It breaks complex data transformations into a series of independent, single-purpose components called filters. These filters are strung together via communication channels called pipes. Data flows continuously from one filter to the next, with each component modifying or analyzing the stream before passing it along. It is highly prevalent in command-line environments, compiler design, and enterprise integration tools.

- **Examples:**
  - [FFmpeg/FFmpeg](https://github.com/FFmpeg/FFmpeg): The ultimate example of a pipe-and-filter application, where distinct processing filters (decoders, scalers, encoders) are chained together via channels to process video and audio streams.
  - [elastic/logstash](https://github.com/elastic/logstash): A server-side data processing pipeline that ingests data from multiple sources, transforms it, and sends it to a "stash."
- **Resources:**
  - [Pipes and Filters pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/pipes-and-filters) by Microsoft Azure: A guide to applying this pattern for cloud-based data processing.
  - "Pattern-Oriented Software Architecture, Volume 1" (POSA): The foundational textbook detailing the Pipe and Filter architectural style.

</details>

<details>
<summary><strong>Main Program and Subroutine Architecture:</strong> The classic procedural decomposition where a main program controls and calls subroutines.</summary>

The foundation of structured programming. It relies on a central control module that dictates the execution flow by invoking a hierarchy of specialized subroutines. Data is passed downwards as parameters and results are returned upwards. While largely superseded by object-oriented and component-based paradigms for high-level application design, it remains highly effective and widely used in systems programming, embedded systems, and performance-critical core engines written in languages like C.

- **Examples:**
  - [curl/curl](https://github.com/curl/curl): A widely used command-line tool and library written in C, relying heavily on a main control flow calling specialized subroutines.
  - [redis/redis](https://github.com/redis/redis): The core Redis database engine, written in C, utilizing procedural architecture for high-performance memory management and network I/O.
- **Resources:**
  - "Software Architecture: Perspectives on an Emerging Discipline" by Mary Shaw and David Garlan: Discusses classical procedural and language-based architectural styles.
  - [Procedural Programming](https://en.wikipedia.org/wiki/Procedural_programming): Core concepts of breaking down systems into routines and subroutines.

</details>

<details>
<summary><strong>Object-Oriented Architecture:</strong> Components are objects that encapsulate data and behavior, communicating through method calls.</summary>

Models the system as a collection of interacting entities. Components are defined as objects that encapsulate both state (data) and behavior (methods). Objects communicate with each other exclusively through defined method calls, enforcing information hiding and clear interfaces. It forms the structural basis of massive enterprise applications built in Java, C#, and C++, emphasizing reusability through patterns like inheritance and polymorphism.

- **Examples:**
  - [jfree/jfreechart](https://github.com/jfree/jfreechart): A massive, classic Java charting application that serves as a textbook example of deep object-oriented class hierarchies, encapsulation, and polymorphism.
  - [iluwatar/java-design-patterns](https://github.com/iluwatar/java-design-patterns): A repository explicitly dedicated to demonstrating object-oriented design patterns.
- **Resources:**
  - "Design Patterns: Elements of Reusable Object-Oriented Software" by the Gang of Four: The standard text on object-oriented software design.
  - "Object-Oriented Software Engineering" by Ivar Jacobson: A use-case driven approach to object-oriented architectures.

</details>

<details>
<summary><strong>C2 Style:</strong> A component-and-connector style where components communicate asynchronously via connectors, used for highly decoupled, GUI-based systems.</summary>

Finding a mainstream, production-grade open-source application explicitly built and labeled as a "C2 Architecture" is nearly impossible today. C2 (Component-and-Connector) was primarily an academic architectural style developed at UC Irvine in the mid-1990s by Richard N. Taylor and his team. It was created as a research model to figure out how to build highly decoupled, event-driven Graphical User Interfaces (GUIs). Because it was an academic model, the industry absorbed its principles (strict decoupling, asynchronous message passing, event buses) but didn't adopt "C2" as a mainstream marketing term the way they did with "Microservices" or "MVC."

- **Examples:**
  - [isr-uci-edu/ArchStudio5](https://github.com/isr-uci-edu/ArchStudio5): The official architecture research environment developed by UC Irvine (the creators of C2), built heavily upon C2 principles and xADL to model and run component-and-connector systems.
  - While strict C2 remains primarily an academic model, modern event-driven UI frameworks like [facebook/react](https://github.com/facebook/react) share its conceptual DNA of asynchronous, decoupled component communication through state/props boundaries.
- **Resources:**
  - [A Component- and Message-Based Architectural Style for GUI Software](https://ics.uci.edu/~taylor/documents/1995-C2-TSE.pdf) by Richard N. Taylor: The original academic paper defining the C2 architectural style.
  - [C2 Architectural Style Overview](https://isr.uci.edu/architecture/c2StyleRules.html) by UC Irvine: The original project page and documentation for the C2 style.

</details>

<details>
<summary><strong>Interpreter Architecture:</strong> A virtual machine that executes instructions in a custom language (e.g., JVM, scripting engines).</summary>

Built to execute custom instructions or domain-specific languages. It functions as a virtual machine that reads, parses, and executes code at runtime rather than compiling it down to native machine code beforehand. It provides massive cross-platform portability and enables dynamic language features, functioning as the core engine behind scripting languages like Python, Ruby, and JavaScript.

- **Examples:**
  - [python/cpython](https://github.com/python/cpython): The reference implementation of the Python programming language, containing the compiler and the execution loop (interpreter).
  - [ruby/ruby](https://github.com/ruby/ruby): The core interpreter for the Ruby programming language.
- **Resources:**
  - "Crafting Interpreters" by Robert Nystrom: A practical guide to building an interpreter architecture from scratch.
  - "Engineering a Compiler" by Keith Cooper and Linda Torczon: The standard textbook covering the design of parsers, virtual machines, and interpreters.

</details>

</details>


<details>
<summary><h3>Data-Centric & Big Data Processing Topologies</h3></summary>

Macro-architectures built specifically to ingest, store, route, and process massive volumes of information across distributed clusters or unified planes.

<details>
<summary><strong>Lambda Architecture:</strong> Designed for big data processing, combining batch processing for comprehensive views and stream processing for real-time views.</summary>

An approach to big data processing that provides a robust, fault-tolerant system against hardware failures and human mistakes. It processes massive quantities of data by providing both batch-processing and stream-processing methods simultaneously. The batch layer manages the historical archive and computes accurate views, while the speed layer handles recent data for low-latency queries. The serving layer indexes the output for fast querying.

- **Examples:**
  - *Note on Examples:* Lambda is a macro-pipeline design pattern used in enterprise big data systems. It is built by wiring together separate infrastructure engines (like Hadoop for batch and Storm for speed). Therefore, there is no single "Lambda Architecture" open-source application repository; it is a deployment strategy used by data engineering teams across varied infrastructure.
- **Resources:**
  - [How to beat the CAP theorem](http://nathanmarz.com/blog/how-to-beat-the-cap-theorem.html) by Nathan Marz: The original blog post introducing the Lambda Architecture.
  - "Big Data: Principles and best practices of scalable realtime data systems" by Nathan Marz and James Warren: The comprehensive book on building Lambda architectures.

</details>

<details>
<summary><strong>Kappa Architecture:</strong> A simplification of Lambda, using a single stream processing engine for both real-time and batch data.</summary>

A data processing architecture designed to simplify the complexities of large-scale data systems. It uses a single technology stack for both real-time and batch processing, treating everything as a continuous stream of events. Historical data is re-processed by replaying the event stream through the same processing engine used for real-time data, maintaining a unified pipeline for all computations.

- **Examples:**
  - *Note on Examples:* Kappa is an enterprise data pipeline philosophy that treats all data as a continuous stream. It is constructed by deploying and configuring streaming engines (like Kafka and Flink). Since it is a conceptual infrastructure pipeline rather than a single application codebase, there are no standalone application examples available in open-source repositories.
- **Resources:**
  - [Questioning the Lambda Architecture](https://www.oreilly.com/radar/questioning-the-lambda-architecture/) by Jay Kreps: The original article proposing the Kappa Architecture as an alternative to Lambda.
  - [Kappa Architecture Introduction](https://hazelcast.com/glossary/kappa-architecture/) by Hazelcast: A clear breakdown of the Kappa architecture principles.

</details>

<details>
<summary><strong>MapReduce Architecture:</strong> A programming model for processing large datasets in parallel across a distributed cluster.</summary>

A processing technique and program model for distributed computing. The algorithm contains two distinct phases: Map and Reduce. The Map phase takes a set of data and converts it into another set of data, breaking individual elements into tuples (key/value pairs). The Reduce phase takes the output from the map phase as input and combines those data tuples into a condensed set of results.

- **Examples:**
  - [apache/hadoop](https://github.com/apache/hadoop): The original open-source framework that implemented the MapReduce programming model for distributed storage and processing.
  - [apache/couchdb](https://github.com/apache/couchdb): A document-oriented NoSQL database that uses MapReduce as its primary mechanism for building views and querying data.
- **Resources:**
  - [MapReduce: Simplified Data Processing on Large Clusters](https://research.google/pubs/pub62/) by Jeffrey Dean and Sanjay Ghemawat: The foundational Google research paper that introduced MapReduce to the world.
  - [Hadoop MapReduce Tutorial](https://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html) by Apache Software Foundation: Official documentation and guides for implementing MapReduce jobs.

</details>

<details>
<summary><strong>Batch Sequential Architecture:</strong> Programs run independently in a predefined order, passing data as files; used in traditional data processing.</summary>

A classic data processing pattern where separate, independent programs execute in a strict sequence. Each program runs to completion, reads an input file, processes the data, and writes an output file that becomes the input for the exact next program in the sequence. It is highly effective for scheduled, high-volume data transformations like end-of-day financial reconciliation or payroll processing.

- **Examples:**
  - *Note on Examples:* Batch Sequential is a traditional enterprise workflow where discrete, standalone scripts execute sequentially, passing files between them. Because it relies on the orchestration of many separate business scripts (like end-of-day payroll or banking reconciliation pipelines), there are no unified, open-source repositories that represent a full Batch Sequential business application.
- **Resources:**
  - [Batch Processing Documentation](https://docs.spring.io/spring-batch/reference/) by Spring: Comprehensive guidelines on structuring and managing batch sequential jobs.
  - [Enterprise Integration Patterns: Process Manager](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ProcessManager.html) by Gregor Hohpe: Architectural patterns related to routing and sequential processing of large workloads.

</details>

<details>
<summary><strong>Database Systems Architecture:</strong> Centralized data store accessed by multiple, independent computations (classic 3-tier applications).</summary>

An architecture where a robust, centralized database management system acts as the core of the application. Multiple separate application instances or services connect to this shared database to read, write, and manipulate data. The database itself handles concurrency, transaction integrity, and data security, acting as the single source of truth for the entire distributed system.

- **Examples:**
  - [postgres/postgres](https://github.com/postgres/postgres): The core repository for PostgreSQL, representing the gold standard for centralized, relational database systems.
  - [mysql/mysql-server](https://github.com/mysql/mysql-server): The core repository for MySQL, widely used as the centralized data store in traditional web architectures.
- **Resources:**
  - "Database System Concepts" by Abraham Silberschatz, Henry F. Korth, and S. Sudarshan: The definitive academic textbook detailing the architecture of database management systems.
  - [Architecture of a Database System](https://dsf.berkeley.edu/papers/fntdb07-architecture.pdf) by Joseph M. Hellerstein, Michael Stonebraker, and James Hamilton: An in-depth paper on how relational database engines are constructed.

</details>

<details>
<summary><strong>Data Mesh:</strong> A decentralized sociotechnical architecture that treats data as a product, with domain teams owning and serving their data.</summary>

A decentralized approach to data architecture that distributes responsibility directly to the specific business domains that generate the data. Each domain team owns its data pipelines and serves its data as a fully functional "product" to the rest of the organization. A federated governance structure ensures these distinct data products remain interoperable and secure across the broader enterprise.

- **Examples:**
  - *Note on Examples:* Data Mesh is a decentralized, sociotechnical organizational paradigm, not a software application. It dictates how different domain teams within a massive enterprise govern and share their data. Because it is a corporate restructuring of data ownership heavily reliant on internal governance and disparate tools, there is no open-source application codebase that represents a Data Mesh.
- **Resources:**
  - [How to Move Beyond a Monolithic Data Lake to a Distributed Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html) by Zhamak Dehghani: The original article introducing the Data Mesh paradigm.
  - "Data Mesh: Delivering Data-Driven Value at Scale" by Zhamak Dehghani: The comprehensive book detailing the implementation and organizational shifts required for a data mesh.

</details>

<details>
<summary><strong>Data Fabric:</strong> An architecture that provides a unified data plane across hybrid and multi-cloud environments.</summary>

An architecture that uses machine learning and metadata to automatically discover, connect, and secure data across disparate systems and cloud providers. It creates a unified, virtualized data layer, allowing users and applications to access information seamlessly across all physical locations and storage formats.

- **Examples:**
  - *Note on Examples:* Data Fabric is a conceptual, enterprise-wide integration strategy that uses AI and metadata to stitch together data across multiple private and public clouds. It is achieved by buying or deploying dozens of interconnected governance, cataloging, and virtualization platforms. As a macro-level IT strategy, there are no single open-source applications that embody a Data Fabric.
- **Resources:**
  - [What is a Data Fabric?](https://www.ibm.com/topics/data-fabric) by IBM: A clear definition and overview of the components that make up a data fabric.
  - [What is a Data Fabric?](https://www.sap.com/insights/what-is-a-data-fabric.html) by SAP: A detailed breakdown of data fabric concepts, core components, and how it unifies data management across environments.

</details>

</details>


<details>
<summary><h3>Event, Messaging & Communication Topologies</h3></summary>

Distributed models dictating how disparate services exchange information, react to state changes, and manage request routing dynamically.

<details>
<summary><strong>Event-Driven Architecture (Macro):</strong> A distributed system where components react to state changes (events) broadcast across the network, rather than relying on direct request/response.</summary>

A highly decoupled topology built around the production, detection, and consumption of state changes. Services publish events to a central broker or event bus. Subscribed services listen for these events and trigger their own isolated business logic asynchronously. It is essential for building highly responsive, scalable systems where unpredictable spikes in traffic are absorbed by queues to protect downstream databases.

- **Examples:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): The reference application for the "Microservices Patterns" book, built entirely on an event-driven architecture using sagas and transactional outboxes.
  - [aws-samples/aws-serverless-airline-booking](https://github.com/aws-samples/aws-serverless-airline-booking): A complete serverless application built on AWS utilizing an event-driven architecture to coordinate distinct booking services via EventBridge.
- **Resources:**
  - [What is an Event-Driven Architecture?](https://aws.amazon.com/event-driven-architecture/) by AWS: A guide to the components and benefits of event-driven systems.
  - "Designing Event-Driven Systems" by Ben Stopford: A comprehensive book on building event-centric architectures.

</details>

<details>
<summary><strong>Process Communication (Communicating Processes) Architecture:</strong> Independent processes communicate through channels like sockets, message queues, or shared memory.</summary>

A foundational concurrency model where an application is divided into isolated, concurrently executing processes that pass messages to one another to coordinate work. By ensuring processes share only explicitly passed messages through strictly defined channels, the system prevents race conditions and complex locking mechanisms. It is the architectural basis for highly concurrent systems like telecom switches, chat servers, and distributed databases.

- **Examples:**
  - [rabbitmq/rabbitmq-server](https://github.com/rabbitmq/rabbitmq-server): While used as a message broker by others, its internal architecture is a prime example of the Erlang Actor model, utilizing thousands of isolated, communicating processes to handle massive concurrency.
  - [syncthing/syncthing](https://github.com/syncthing/syncthing): A continuous file synchronization program written in Go, architected internally around Communicating Sequential Processes (CSP) using goroutines and channels to pass messages safely between syncing operations.
- **Resources:**
  - [Communicating Sequential Processes](http://www.usingcsp.com/cspbook.pdf) by C.A.R. Hoare: The foundational computer science paper defining the CSP architectural style.
  - [The Actor Model](https://doc.akka.io/docs/akka/current/typed/guide/actors-intro.html) by Akka: Documentation explaining how concurrent processes communicate via message passing.

</details>

<details>
<summary><strong>Service Mesh Architecture:</strong> A dedicated infrastructure layer for managing service-to-service communications in microservices architectures, typically using a sidecar proxy to handle routing, security, and observability without altering application code.</summary>

An operational topology that abstracts the network layer away from the application code. Network capabilities like retry logic, mutual TLS encryption, and distributed tracing are handled by a sidecar proxy deployed alongside every service instance. The interconnected web of these proxies forms the mesh, controlled by a central control plane. It is crucial for maintaining security, observability, and traffic control in massive Kubernetes deployments.

- **Examples:**
  - [istio/istio/tree/master/samples/bookinfo](https://github.com/istio/istio/tree/master/samples/bookinfo): The official polyglot reference application specifically engineered to demonstrate Service Mesh traffic routing, fault injection, and metrics across different language backends.
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Google's 11-tier application (Online Boutique) explicitly architected to be deployed onto a service mesh to handle service-to-service communication.
- **Resources:**
  - [What is a Service Mesh?](https://www.redhat.com/en/topics/microservices/what-is-a-service-mesh) by Red Hat: A clear breakdown of the data plane, control plane, and sidecar proxy concepts.
  - "Istio up and Running" by Lee Calcote and Zack Butcher: A practical guide to implementing a service mesh architecture.

</details>

<details>
<summary><strong>API Gateway / Backends for Frontends (BFF) Architecture:</strong> A single entry point (gateway) or multiple client-specific backends (BFF) that handle routing, composition, and cross-cutting concerns for APIs.</summary>

A structural pattern used to abstract the complexity of backend microservices. An API Gateway acts as a reverse proxy, aggregating multiple microservice calls into a single response, handling authentication, rate limiting, and request routing. The Backends for Frontends (BFF) variant takes this further by creating dedicated, separate gateways tailored specifically for different UI clients (e.g., one API for mobile, a different one for desktop web). This ensures clients receive the exact data they require, formatted perfectly for their specific interface.

- **Examples:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Microsoft's reference microservices application which explicitly implements the Backends for Frontends (BFF) pattern, featuring entirely separate gateway routing configurations for its Web UI and Mobile clients.
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Features a dedicated `frontend` service acting as the single API Gateway that orchestrates calls to the various backend services (cart, product catalog, currency, etc.) to render the final web views.
- **Resources:**
  - [Pattern: Backends For Frontends](https://samnewman.io/patterns/architectural/bff/) by Sam Newman: The original definition and deep dive into the BFF architectural pattern.
  - [API Gateway Pattern](https://microservices.io/patterns/apigateway.html) by Chris Richardson: A comprehensive look at the benefits and drawbacks of using a unified API gateway.

</details>

</details>


<details>
<summary><h3>Concurrency, State & Transactional Topologies</h3></summary>

Paradigms designed to handle complex state management, high-throughput parallelism, and distributed transactions without traditional locking bottlenecks.

<details>
<summary><strong>Actor Model Architecture:</strong> A conceptual model for concurrent computation where "actors" are the universal primitives, modifying their own state and communicating exclusively through asynchronous message passing (e.g., Erlang, Akka).</summary>

A highly concurrent topology where the system is composed of thousands or millions of independent, lightweight entities called "actors." Each actor strictly encapsulates its own private state and thread of execution. Because actors never share memory and only interact by sending asynchronous messages to each other's mailboxes, the system completely eliminates the need for traditional thread locking and mutexes. It is the architecture of choice for massively concurrent, fault-tolerant systems like multiplayer game servers and telecommunication switches.

- **Examples:**
  - [ornicar/lila](https://github.com/ornicar/lila): The core backend application for Lichess.org. It is built using Scala and the Akka actor framework to handle millions of concurrent chess matches, player states, and real-time websocket connections without locking bottlenecks.
  - [rabbitmq/rabbitmq-server](https://github.com/rabbitmq/rabbitmq-server): The widely used message broker, built natively in Erlang. Its internal architecture is a textbook implementation of the Actor model, where millions of lightweight actor processes handle queuing, routing, and state management concurrently.
- **Resources:**
  - [The Actor Model in 10 Minutes](https://www.brianstorti.com/the-actor-model/) by Brian Storti: An accessible breakdown of how actors manage state, concurrency, and message mailboxes.
  - "Reactive Messaging Patterns with the Actor Model" by Vaughn Vernon: A deep dive into building enterprise systems using actor-based concurrency.

</details>

<details>
<summary><strong>Space-Based Architecture (Tuple Space):</strong> Uses distributed shared memory to avoid database bottlenecks, scaling horizontally for high-volume, variable traffic.</summary>

An architecture designed to completely eliminate the database as a performance bottleneck. Instead of applications querying a central database over a network, data is partitioned and held in memory across a grid of active processing units. The application logic and the data it operates on are co-located in RAM (the "space"). It scales horizontally by spinning up more processing units, making it highly effective for systems dealing with extreme, unpredictable spikes in traffic, such as high-frequency trading platforms, ticketing systems, and real-time bidding engines.

- **Examples:**
  - *Note on Examples:* Space-Based Architecture is an enterprise deployment topology rather than a standalone application design. It is implemented by deploying business logic directly into distributed In-Memory Data Grid (IMDG) middleware. Because it relies heavily on orchestrating these specialized grid engines (like Apache Ignite or Hazelcast) across a cluster, there are no single, deployable open-source business application repositories that fully represent the topology natively.
- **Resources:**
  - [Space-Based Architecture Pattern](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch04.html) by Mark Richards: The definitive architectural explanation of processing units, virtualized middleware, and data grids.
  - [Tuple Space](https://en.wikipedia.org/wiki/Tuple_space): An overview of the foundational distributed computing concept that evolved into modern space-based architectures.

</details>

<details>
<summary><strong>Saga Architecture:</strong> Manages distributed transactions across microservices using a sequence of local transactions with compensating actions.</summary>

A distributed transactional pattern that solves the problem of maintaining data consistency across multiple, independent databases. Because loosely coupled microservices cannot share a single ACID database transaction, a Saga breaks a large business transaction into a series of smaller, local steps. If one downstream step fails, the system executes a series of "compensating transactions" (rollbacks) to undo the preceding steps. It ensures eventual consistency without relying on synchronous, distributed locking protocols like Two-Phase Commit (2PC).

- **Examples:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): The definitive reference application for microservices, specifically engineered to demonstrate Saga choreography and orchestration for a complex "Food to Go" order management system.
  - [berndruecker/trip-booking-saga-java](https://github.com/berndruecker/trip-booking-saga-java): A pure business application demonstrating a travel booking saga (booking a flight, hotel, and car sequentially), highlighting the execution of compensating actions when a remote booking fails.
- **Resources:**
  - [Pattern: Saga](https://microservices.io/patterns/data/saga.html) by Chris Richardson: The industry-standard definition and breakdown of orchestration versus choreography in Sagas.
  - [Saga distributed transactions](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/saga/saga) by Microsoft Azure: A practical guide on implementing the Saga pattern for cloud-based microservices.

</details>

</details>


<details>
<summary><h3>Knowledge, AI & Control Systems Architectures</h3></summary>

Specialized macro-structures designed for autonomous reasoning, inference, pattern recognition, and physical hardware management.

<details>
<summary><strong>Agentic Architecture (Multi-Agent Systems):</strong> An emerging AI-driven topology where autonomous systems (agents) use large language models to reason, plan, and execute actions, often collaborating to achieve complex goals.</summary>

A dynamic topology heavily relying on Large Language Models (LLMs) as central reasoning engines. Instead of following deterministic, hardcoded paths, the system defines high-level goals and equips "agents" with tools (calculators, web search, API access). These agents autonomously plan their execution steps, reflect on intermediate results, and communicate with other specialized agents to solve complex, open-ended problems. It represents a massive shift from imperative programming to goal-oriented, autonomous orchestration.

- **Examples:**
  - [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT): A highly popular open-source application that acts as an autonomous agent, chaining together LLM thoughts to independently achieve user-defined goals.
  - [OpenBMB/ChatDev](https://github.com/OpenBMB/ChatDev): A virtual software company application where multiple distinct AI agents (acting as a CEO, programmer, and reviewer) collaborate autonomously to build software based on a single prompt.
- **Resources:**
  - [LLM Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/) by Lilian Weng: The definitive technical breakdown of agent planning, memory, and tool use.
  - [AutoGPT Documentation](https://docs.agpt.co/): Practical implementation guides for autonomous agent loops.

</details>

<details>
<summary><strong>Blackboard Architecture:</strong> Multiple specialized subsystems collaborate on a shared data structure (blackboard), common in AI and pattern recognition.</summary>

An early AI pattern designed for complex, non-deterministic problems like speech recognition or structural protein modeling. It features a central global memory space (the blackboard) and a collection of independent, specialized knowledge sources (the "experts"). There is no central control flow dictating the sequence of operations. Each expert constantly monitors the blackboard. When an expert sees data it can process, it updates the blackboard with a partial solution, which triggers other experts to contribute until a final solution emerges.

- **Examples:**
  - [stanfordnlp/CoreNLP](https://github.com/stanfordnlp/CoreNLP): The core Stanford NLP application uses a pipeline heavily inspired by the Blackboard pattern. A shared `Annotation` object (the blackboard) is passed around and modified by independent annotators (experts in Part-of-Speech tagging, Named Entity Recognition, parsing) to build a complete linguistic analysis.
- **Resources:**
  - [Blackboard System](https://en.wikipedia.org/wiki/Blackboard_system): An overview of the control shell, blackboard, and knowledge sources.
  - "Pattern-Oriented Software Architecture, Volume 1" (POSA): Contains the definitive formalization of the Blackboard pattern.

</details>

<details>
<summary><strong>Rule-Based System Architecture:</strong> An inference engine applies a set of rules to a knowledge base to derive conclusions; used in expert systems.</summary>

A foundational pattern of classical symbolic AI, often referred to as an "Expert System." It strictly separates the business logic (the rules) from the execution control (the inference engine). Human domain experts define a massive knowledge base of "IF-THEN" facts and conditions. The inference engine then dynamically evaluates incoming data against these rules, firing applicable rules to deduce new facts or trigger actions. It is highly effective for complex compliance, medical diagnosis, and automated underwriting systems where decision logic must be strictly auditable.

- **Examples:**
  - [eslint/eslint](https://github.com/eslint/eslint): A pure rule-based application where a core engine evaluates an Abstract Syntax Tree (AST) against hundreds of independent, pluggable rules to infer code quality and trigger warnings.
  - [Yelp/elastalert](https://github.com/Yelp/elastalert): An application that alerts on anomalies from Elasticsearch by continuously evaluating data against a massive dictionary of user-defined rules.
- **Resources:**
  - [Rule-Based System](https://en.wikipedia.org/wiki/Rule-based_system): An overview of inference engines and expert systems.
  - "Expert Systems: Principles and Programming" by Joseph C. Giarratano and Gary D. Riley: The classic textbook on designing rule-based architectures.

</details>

<details>
<summary><strong>Closed-Loop Control Architecture (Process Control):</strong> Manages physical processes through sensors and actuators (thermostat, cruise control, embedded systems).</summary>

An architecture fundamentally bound to the physical world, operating in a continuous, infinite loop to maintain a desired physical state. It relies on a sensor to read the current state of a system, compares that reading to a desired setpoint to calculate an error value, and immediately sends a corrective command to a physical actuator. The system relies entirely on this continuous feedback loop to adapt to external physical disturbances. It is the dominant software architecture for industrial robotics, autonomous vehicles, and HVAC systems.

- **Examples:**
  - [ArduPilot/ardupilot](https://github.com/ArduPilot/ardupilot): The highly popular open-source autopilot software suite, built precisely around high-frequency closed-loop PID controllers to maintain aircraft stability.
  - [commaai/openpilot](https://github.com/commaai/openpilot): An open-source autonomous driving application that uses closed-loop control architectures to continuously adjust a vehicle's steering and acceleration based on real-time camera and radar feedback.
- **Resources:**
  - [Control Theory](https://en.wikipedia.org/wiki/Control_theory): The foundational mathematics and concepts of feedback loops.
  - "Feedback Control of Dynamic Systems" by Gene F. Franklin: The standard engineering text detailing the design of closed-loop software and hardware.

</details>

<details>
<summary><strong>Real-Time Architecture:</strong> Systems where response time is critical and must be guaranteed (e.g., avionics, medical devices).</summary>

An architecture defined by strict deterministic timing constraints rather than pure throughput. In a real-time architecture, calculating the correct answer too late is considered a complete system failure. To guarantee execution within microsecond deadlines, these systems use specialized Real-Time Operating Systems (RTOS), avoid unpredictable garbage collection pauses, and strictly partition memory. They are essential for safety-critical hardware like pacemakers, anti-lock braking systems, and orbital satellites.

- **Examples:**
  - [PX4/PX4-Autopilot](https://github.com/PX4/PX4-Autopilot): An open-source flight control application that specifically targets real-time operating systems (like NuttX) to guarantee strict deterministic timing for drone motor control.
  - [nasa/cFS](https://github.com/nasa/cFS): The Core Flight System developed by NASA, a real-time software framework and application suite used in actual spaceflight missions where missing a processing deadline can result in mission failure.
- **Resources:**
  - [Real-Time Computing](https://en.wikipedia.org/wiki/Real-time_computing): An overview of hard, firm, and soft real-time constraints.
  - "Real-Time Systems Design and Analysis" by Phillip A. Laplante: A comprehensive guide on structuring determinism into software architectures.

</details>

</details>


<details>
<summary><h3>System Migration & Hybrid Topologies</h3></summary>

Transitional or composite architectural models used to bridge distinct computing environments or gracefully phase out legacy monolithic systems.

<details>
<summary><strong>Strangler Fig Architecture:</strong> Incrementally replaces a legacy system by building a new system around it and gradually routing functionality to it.</summary>

A migration pattern used to safely modernize massive, monolithic legacy systems. A routing facade is placed in front of the legacy application. As development teams build new, modernized services, the facade intercepts requests and redirects them to the new services while routing the remaining unmigrated traffic to the legacy system. Over time, the new system grows around the old one, completely replacing its functionality until the legacy system can be safely decommissioned.

- **Examples:**
  - *Note on Examples:* Strangler Fig is a transient migration strategy applied to existing, usually proprietary, enterprise codebases rather than a standalone architectural end-state. Because it describes the active process of rewriting and routing traffic away from a specific legacy system, there are no open-source application repositories built natively as "Strangler Fig" applications.
- **Resources:**
  - [StranglerFigApplication](https://martinfowler.com/bliki/StranglerFigApplication.html) by Martin Fowler: The original article coining the term and outlining the migration strategy.
  - [Strangler Fig pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/strangler-fig) by Microsoft Azure: A practical guide to implementing the facade and routing necessary for the migration.

</details>

<details>
<summary><strong>Hybrid Architecture / Multi-Cloud Architecture:</strong> Combines multiple architectural styles or deployment across multiple cloud providers.</summary>

A macro-level deployment topology that spans physical on-premises data centers and one or more public cloud environments. It provides organizations with extreme flexibility, allowing them to keep highly sensitive data on local hardware for regulatory compliance while bursting variable workloads into the public cloud to use infinite horizontal scaling. It relies heavily on container orchestration platforms to maintain consistent application behavior across completely different physical environments.

- **Examples:**
  - *Note on Examples:* Hybrid and Multi-Cloud architectures are infrastructure deployment strategies managed by networking and orchestration layers (like Google Anthos, Azure Arc, or Kubernetes Federation). A business application deployed in a hybrid setup is just a standard application (often microservices) mapped across different servers. Therefore, there is no single open-source codebase that embodies "Hybrid Architecture."
- **Resources:**
  - [What is a Hybrid Cloud?](https://www.redhat.com/en/topics/cloud-computing/what-is-hybrid-cloud) by Red Hat: A clear breakdown of how on-premises and cloud resources are integrated.
  - [Multi-cloud architecture patterns](https://cloud.google.com/architecture/multi-cloud-architecture) by Google Cloud: Industry-standard deployment models for distributing workloads across different providers.

</details>

</details>


<details>
<summary><h3>Information & Resource Linking Topologies</h3></summary>

Architectures fundamentally based on centralizing shared data access or connecting distributed documents via associative references.

<details>
<summary><strong>Hypertext System Architecture:</strong> Documents (nodes) interconnected by links; the foundation of the World Wide Web.</summary>

A non-linear architectural paradigm where discrete blocks of information (nodes) are connected via associative references (hyperlinks). It completely decouples the storage of information from its structural presentation, allowing users to navigate dynamically based on context rather than a strict hierarchy. This is the foundational architecture of the World Wide Web, modern documentation platforms, and associative note-taking applications.

- **Examples:**
  - [wikimedia/mediawiki](https://github.com/wikimedia/mediawiki): The core application powering Wikipedia, acting as a massive, dynamic hypertext system where millions of nodes are interconnected via associative links.
  - [logseq/logseq](https://github.com/logseq/logseq): A local-first, non-linear outliner application built entirely on a hypertext architecture, using bidirectional links to connect and traverse thought nodes autonomously.
- **Resources:**
  - [As We May Think](https://www.theatlantic.com/magazine/archive/1945/07/as-we-may-think/303881/) by Vannevar Bush: The foundational 1945 essay that conceptualized the Memex, the precursor to hypertext architectures.
  - [Information Management: A Proposal](https://www.w3.org/History/1989/proposal.html) by Tim Berners-Lee: The original architectural proposal for the World Wide Web, defining the structural use of nodes and hypertext links.

</details>

<details>
<summary><strong>Repository Architecture:</strong> Centralized data store accessed by multiple independent components (e.g., database-centric systems).</summary>

A data-centric topology where a single, central repository holds the shared state of the system, and a collection of independent software components operate on that centralized data. The components interact almost exclusively through the repository rather than communicating directly with one another. It is highly effective for systems dealing with complex, shared data structures where different, decoupled tools need to read, analyze, and modify the same source of truth simultaneously.

- **Examples:**
  - [git/git](https://github.com/git/git): The core version control application operates natively as a repository architecture. Independent command components (`commit`, `status`, `log`) do not communicate with each other; they all execute their logic by reading and writing to the central `.git` object database.
  - [WordPress/WordPress](https://github.com/WordPress/WordPress): An example of a web-based repository architecture. The central database holds all state, and independent components (the core rendering engine, diverse plugins, and themes) independently interact with this central data store without requiring direct component-to-component messaging.
- **Resources:**
  - "Software Architecture: Perspectives on an Emerging Discipline" by Mary Shaw and David Garlan: Provides a deep academic breakdown of the shared-data and repository architectural styles.
  - "Software Architecture in Practice" by Len Bass, Paul Clements, and Rick Kazman: Discusses the operational benefits and scalability constraints of centralizing application state within a single repository layer.

</details>

</details>

</details>

<details>
<summary><h2>Layer 2: Enterprise Integration Patterns</h2></summary>

<br>

*Communication and data flow between major components or services*

<details>
<summary><h3>Message Channel Patterns</h3></summary>

<br>

Foundational structures defining the virtual pathways through which applications inject and consume decoupled information.

<details>
<summary><strong>Point-to-Point Channel:</strong> Ensures that only one receiver consumes any given message. Once read, the message is removed from the channel.</summary>

A messaging topology designed for distributing discrete units of work. A sender places a message onto a specific channel (usually a queue). While multiple concurrent receivers (workers) can listen to the same channel, the channel guarantees that only a single receiver will successfully consume and process any given message. It is the foundational pattern for load-balancing background tasks and ensuring idempotent execution of commands.

- **Examples:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Relies heavily on Point-to-Point channels (via Sidekiq and Redis) to distribute asynchronous, heavy-lifting background jobs, like federating posts or processing image uploads, to single, available worker instances.
  - [getsentry/sentry](https://github.com/getsentry/sentry): The core Sentry application uses point-to-point task queues (via Celery) to route millions of incoming crash reports to available processors without duplicating work.
- **Resources:**
  - [Point-to-Point Channel](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PointToPointChannel.html) by Gregor Hohpe: The original Enterprise Integration Patterns definition.
  - [AWS SQS (Simple Queue Service)](https://aws.amazon.com/sqs/): Amazon's core documentation on how standard point-to-point queues operate.

</details>

<details>
<summary><strong>Publish-Subscribe Channel:</strong> Broadcasts a single event to multiple active subscribers simultaneously.</summary>

A messaging topology designed for event notification rather than task distribution. A sender (publisher) broadcasts a message to a specific topic or channel. A copy of that message is instantly delivered to every single receiver (subscriber) currently actively listening to that channel. It allows for massive decoupling, as the publisher has no knowledge of how many subscribers exist or what they do with the data.

- **Examples:**
  - [discourse/discourse](https://github.com/discourse/discourse): Uses a highly active Publish-Subscribe channel (via its custom Ruby `MessageBus`) to broadcast live UI updates, such as new replies or user notifications, to all concurrently connected web clients simultaneously.
  - [RocketChat/Rocket.Chat](https://github.com/RocketChat/Rocket.Chat): An open-source communication platform that heavily relies on pub/sub architectures to instantly broadcast chat messages across multiple distributed node instances and user screens.
- **Resources:**
  - [Publish-Subscribe Channel](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html) by Gregor Hohpe: The foundational pattern definition.
  - [Pub/Sub Messaging](https://cloud.google.com/pubsub/docs/overview) by Google Cloud: Architectural overviews of massive-scale event broadcasting.

</details>

<details>
<summary><strong>Dead Letter Channel:</strong> A dedicated channel where the messaging system routes messages that cannot be successfully delivered or processed.</summary>

An error-handling topology for asynchronous systems. When a message encounters a terminal error, such as maxing out its delivery retry attempts, exceeding its Time-To-Live (TTL), or failing schema validation, the message broker automatically removes it from the active processing queue and routes it to a specific Dead Letter Channel. This prevents "poison pill" messages from endlessly clogging up the primary queue while preserving the failed data for manual inspection or automated logging.

- **Examples:**
  - *Note on Examples:* The Dead Letter Channel is a granular error-routing configuration implemented *within* message broker infrastructure (like RabbitMQ, Kafka, or AWS SQS). Because it is a specific queue configuration state rather than a standalone software architecture, there are no open-source business application repositories that represent it natively.
- **Resources:**
  - [Dead Letter Channel](https://www.enterpriseintegrationpatterns.com/patterns/messaging/DeadLetterChannel.html) by Gregor Hohpe: The core logic behind isolating failed messages.
  - [Understanding Amazon SQS dead-letter queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues.html): Practical implementations of DLCs in cloud architecture.

</details>

<details>
<summary><strong>Guaranteed Delivery:</strong> Uses persistent, built-in storage mechanisms to ensure a message is not lost even if the system or network crashes before delivery.</summary>

A Quality of Service (QoS) topology designed to prevent data loss in highly volatile environments. When a sender dispatches a message, the messaging infrastructure forces that message to be written to non-volatile physical disk storage before returning a success acknowledgement to the sender. If the broker crashes, the message survives in storage and is delivered as soon as the system comes back online.

- **Examples:**
  - *Note on Examples:* Guaranteed Delivery is a Quality of Service (QoS) property and a data-durability protocol, not a software application codebase. It is achieved by configuring deployment infrastructure engines (forcing tools like Apache ActiveMQ or Kafka to commit to disk). Therefore, no standalone business application repository can be linked as an example.
- **Resources:**
  - [Guaranteed Delivery](https://www.enterpriseintegrationpatterns.com/patterns/messaging/GuaranteedMessaging.html) by Gregor Hohpe: The architectural trade-offs between delivery safety and system performance.
  - [RabbitMQ Reliability Guide](https://www.rabbitmq.com/docs/reliability): Technical documentation on implementing publisher confirms and disk persistence to guarantee message delivery.

</details>

</details>

<details>
<summary><h3>Message Routing Patterns</h3></summary>

<br>

Mechanisms that determine the specific path a message should take to reach its final destination based on context, rules, or content.

<details>
<summary><strong>Content-Based Router:</strong> Examines a message's content and routes it to a specific destination channel based on that data.</summary>

A logical switchboard for messaging topologies. Instead of requiring a sender to know exactly which downstream queue should handle a task, the sender publishes to a single, central router. The router parses the incoming message's payload or headers (e.g., checking a "customer_tier" or "region" field) and dynamically redirects the message to the appropriate specialized channel. This drastically simplifies the sender's logic and decouples producers from consumers.

- **Examples:**
  - [home-assistant/core](https://github.com/home-assistant/core): Heavily uses content-based routing within its event bus. The core engine constantly evaluates the payload of incoming state-change events from physical sensors and routes them to specific automation channels based on the exact data (e.g., if temperature > 70).
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): An open-source Git service that uses content-based routing to examine incoming webhook payloads and dispatch them to different runner queues based on the event type (push, pull request, release).
- **Resources:**
  - [Content-Based Router](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ContentBasedRouter.html) by Gregor Hohpe: The foundational concept of data-driven message routing.
  - [AWS EventBridge Content Filtering](https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-event-patterns.html): Practical documentation on routing events based on JSON payload contents.

</details>

<details>
<summary><strong>Message Filter:</strong> Evaluates a message against specific criteria and drops it from the channel if it does not meet the requirements.</summary>

A protective routing mechanism designed to prevent downstream components from being overwhelmed by irrelevant data. The filter sits on a channel and inspects every passing message. If the message matches the filter's criteria, it is passed through seamlessly to the output channel. If it fails, the message is quietly discarded. It is heavily used in logging aggregation and security monitoring.

- **Examples:**
  - [fail2ban/fail2ban](https://github.com/fail2ban/fail2ban): A security application that acts as an aggressive message filter. It continuously parses massive streams of server log files, silently dropping normal traffic and only passing through (and acting upon) log lines that indicate malicious authentication failures.
  - [pi-hole/pi-hole](https://github.com/pi-hole/pi-hole): A network-level application that functions purely as a message filter for DNS requests, silently dropping queries that match known ad-serving domains while passing legitimate web requests through.
- **Resources:**
  - [Message Filter](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Filter.html) by Gregor Hohpe: The pattern definition for eliminating unwanted messages from a stream.

</details>

<details>
<summary><strong>Recipient List:</strong> Inspects an incoming message and forwards it to a dynamically determined list of recipients.</summary>

An intelligent broadcasting pattern. Unlike a standard Publish-Subscribe channel (which blindly broadcasts to everyone listening), a Recipient List dynamically calculates *who* should receive the message at runtime based on the message content or external state. It acts as a targeted scatter-gather mechanism, commonly used in notification systems and complex approval workflows.

- **Examples:**
  - [novuhq/novu](https://github.com/novuhq/novu): An open-source notification infrastructure application. It implements the Recipient List pattern natively by taking a single incoming trigger (like "password reset") and dynamically calculating the correct delivery channels (email, SMS, push) based on user preference tables.
- **Resources:**
  - [Recipient List](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RecipientList.html) by Gregor Hohpe: The architectural theory behind dynamic, selective broadcasting.

</details>

<details>
<summary><strong>Splitter:</strong> Breaks a single, composite message into multiple individual messages so they can be processed independently.</summary>

A structural pattern used to parallelize work and handle massive data payloads. When a system receives a massive batch file or an order with dozens of line items, passing the entire block to a single worker is inefficient. The Splitter intercepts the composite message, breaks it down into discrete, atomic units, and publishes each unit as a separate message onto a processing queue, allowing a fleet of concurrent workers to process the parts simultaneously.

- **Examples:**
  - [airbytehq/airbyte](https://github.com/airbytehq/airbyte): An open-source data integration platform that uses splitting mechanisms to take massive bulk API responses (like an entire CRM database pull) and break them into individual JSON record messages for independent downstream processing and normalization.
- **Resources:**
  - [Splitter Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Sequencer.html) by Gregor Hohpe: The core logic for breaking down composite payloads.

</details>

<details>
<summary><strong>Aggregator:</strong> Collects and combines multiple related, smaller messages into a single, comprehensive message.</summary>

The functional inverse of the Splitter. It is a highly stateful routing pattern that buffers incoming messages until a specific completion condition is met (e.g., waiting for all 5 line items of an order to arrive, or waiting for a 10-second time window to close). Once the condition is triggered, it compiles the buffered messages into a single, unified payload and sends it downstream. It is essential for batching database writes and compiling disparate API responses.

- **Examples:**
  - [prometheus/prometheus](https://github.com/prometheus/prometheus): The time-series monitoring application inherently relies on aggregation architectures to ingest thousands of individual telemetry metrics per second, buffering and compressing them into highly efficient blocks before writing them to disk.
  - [getsentry/sentry](https://github.com/getsentry/sentry): Sentry relies on complex aggregation logic to group thousands of identical, individual error messages firing from a broken client application into a single, coherent "Issue" on the user's dashboard.
- **Resources:**
  - [Aggregator Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Aggregator.html) by Gregor Hohpe: Managing state and correlation IDs to reconstruct messages.

</details>

<details>
<summary><strong>Resequencer:</strong> Buffers out-of-sequence messages and publishes them downstream in the correct, original order.</summary>

A stateful buffer used to correct temporal issues in distributed systems. Because network latency and concurrent processing queues often result in messages arriving at their destination out of chronological order, a Resequencer temporarily holds incoming messages in memory. It inspects a sequence ID or timestamp on the payloads and releases them to the final destination strictly in their intended chronological sequence.

- **Examples:**
  - [jitsi/jitsi-videobridge](https://github.com/jitsi/jitsi-videobridge): A WebRTC compatible video router. Its internal architecture relies heavily on real-time resequencing buffers to catch incoming, highly fragmented UDP video packets and put them back in the correct sequential order before rendering the video frame to the end user.
- **Resources:**
  - [Resequencer Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Resequencer.html) by Gregor Hohpe: The theory of managing sequence gaps and temporal buffering.

</details>

<details>
<summary><strong>Routing Slip:</strong> Attaches a sequence of routing instructions directly to the message payload so it knows where to go next.</summary>

A distributed orchestration pattern where the itinerary travels *with* the data. Instead of a central controller orchestrating a complex workflow, the initial sender attaches a list of required processing steps (the "slip") to the message itself. When a worker finishes its task, it inspects the slip on the message, determines the next destination, and forwards it directly. This removes the need for a central orchestrator bottleneck.

- **Examples:**
  - [Netflix/conductor](https://github.com/Netflix/conductor): While serving as an orchestrator, its worker execution model mimics the Routing Slip paradigm, where state and sequential routing context are passed alongside tasks so distributed workers know exactly where a workflow stands without querying a massive monolithic database.
- **Resources:**
  - [Routing Slip Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RoutingTable.html) by Gregor Hohpe: Decoupling workflow orchestration from the central hub.

</details>

<details>
<summary><strong>Throttler:</strong> Restricts the rate at which messages are passed to a receiver to prevent the destination from being overloaded.</summary>

A traffic-control mechanism designed to enforce Service Level Agreements (SLAs) and protect fragile downstream legacy systems. If messages arrive in a massive burst, the Throttler buffers them and leaks them to the destination at a strict, controlled, predetermined rate (e.g., 50 messages per second). 

- **Examples:**
  - [discourse/discourse](https://github.com/discourse/discourse): Implements application-level throttlers and rate limiters natively to restrict how fast users can publish messages or hit endpoints, intentionally buffering or rejecting traffic to protect the core Postgres database from localized DoS spikes.
- **Resources:**
  - [Throttling pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/throttling) by Microsoft Azure: Cloud-native guidelines for implementing rate limiting and message throttling.

</details>

<details>
<summary><strong>Load Balancer:</strong> Distributes incoming messages across multiple receiver instances to optimize resource utilization and throughput.</summary>

The fundamental mechanism for horizontal scaling. It acts as a reverse proxy, intercepting all incoming traffic and algorithmically dividing it (e.g., Round Robin, Least Connections) across a pool of identical backend workers or servers. If a worker dies, the load balancer stops routing traffic to it, ensuring high availability.

- **Examples:**
  - *Note on Examples:* A Load Balancer is entirely an infrastructure component (like HAProxy, Nginx, or AWS ALB) rather than a business application codebase. Applications are deployed *behind* load balancers. Therefore, there are no end-user open-source applications that natively represent this macro-routing pattern. 
- **Resources:**
  - [What is Load Balancing?](https://www.cloudflare.com/learning/performance/what-is-load-balancing/) by Cloudflare: A comprehensive breakdown of Layer 4 vs. Layer 7 balancing algorithms.

</details>

</details>

<details>
<summary><h3>Message Transformation Patterns</h3></summary>

<br>

Intermediary steps that alter, enrich, or standardize the payload of a message to decouple the sender's data format from the receiver's expectations.

<details>
<summary><strong>Envelope Wrapper:</strong> Wraps existing data inside a compliant, standardized message envelope without altering the original payload.</summary>

A pattern used to encapsulate raw data within a standardized metadata structure (the envelope) required by the messaging infrastructure (like headers, correlation IDs, or routing instructions) without modifying the original payload itself. It ensures that the transport layer can successfully route and track the message without needing to parse, understand, or alter the core business data inside.

- **Examples:**
  - [matrix-org/synapse](https://github.com/matrix-org/synapse): The core reference server for the Matrix communication protocol. It explicitly relies on envelope wrappers to encapsulate end-to-end encrypted chat payloads inside standardized JSON federation envelopes, allowing servers to route messages to the correct destinations without ever being able to read the internal payload.
  - [letsencrypt/boulder](https://github.com/letsencrypt/boulder): The core application running Let's Encrypt. It wraps raw certificate signing requests (CSRs) and validation payloads inside standardized JWS (JSON Web Signature) envelopes for secure transport and cryptographic verification.
- **Resources:**
  - [Envelope Wrapper](https://www.enterpriseintegrationpatterns.com/patterns/messaging/EnvelopeWrapper.html) by Gregor Hohpe: The original pattern definition for encapsulating data.

</details>

<details>
<summary><strong>Content Enricher:</strong> Intercepts a message and accesses an external data source to append missing, required information before sending it onward.</summary>

A pattern used when a source system produces a message that lacks all the necessary data required by the target system. An intermediary component intercepts the message, queries an external database or API to retrieve the missing context (e.g., taking a generic `user_id` from the payload and fetching the full user profile), appends it to the message, and forwards the enriched payload to the destination.

- **Examples:**
  - [getsentry/sentry](https://github.com/getsentry/sentry): Intercepts raw crash logs (which often contain just a user ID or an IP address) and passes them through an internal enrichment pipeline that queries databases to append full user context, geographic location, and release deployment data before saving the event to the dashboard.
  - [matomo-org/matomo](https://github.com/matomo-org/matomo): The open-source web analytics platform receives raw HTTP hit data and dynamically enriches it by querying IP geolocation databases and device-fingerprint dictionaries to append location and browser details before saving the analytic record.
- **Resources:**
  - [Content Enricher](https://www.enterpriseintegrationpatterns.com/patterns/messaging/DataEnricher.html) by Gregor Hohpe: The architectural theory behind intercepting and appending data.

</details>

<details>
<summary><strong>Content Filter:</strong> Removes unneeded or sensitive data from a message to simplify it or enhance security before delivery.</summary>

The structural inverse of the Content Enricher. Instead of adding data, the Content Filter actively strips specific data fields from a message payload before routing it to the final destination. It is heavily used for data minimization, stripping out massive unneeded fields to save network bandwidth, or sanitizing sensitive Personally Identifiable Information (PII) before sending data to a third-party service.

- **Examples:**
  - [getsentry/sentry](https://github.com/getsentry/sentry): Employs advanced content filtering (called Data Scrubbing) to automatically parse JSON payloads and strip out credit card numbers, passwords, and custom PII from incoming error messages before they are routed to the database or notification channels.
  - [nextcloud/server](https://github.com/nextcloud/server): Uses strict content filtering when generating external share links or API responses, explicitly stripping internal database IDs, absolute server file paths, and system ownership metadata from the JSON payloads before serving them to unauthorized external clients.
- **Resources:**
  - [Content Filter](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ContentFilter.html) by Gregor Hohpe: The pattern definition for simplifying and securing payloads.

</details>

<details>
<summary><strong>Claim Check:</strong> Stores large, heavy message payloads in a persistent database and passes only a lightweight reference identifier (the claim check) through the messaging bus.</summary>

A pattern designed to prevent message brokers from being choked by massive payloads (like video files, hi-res images, or multi-megabyte documents). Instead of pushing the heavy data directly through the queue, the sender uploads the payload to a separate, persistent data store (like AWS S3 or a local database), receives a lightweight unique ID (the claim check), and sends *only* that ID through the messaging channel. The receiver reads the ID and uses it to download the heavy payload directly from the persistent store.

- **Examples:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Implements the Claim Check pattern for media processing. When a user uploads a video, the massive file is saved to cloud storage, and only the lightweight media ID (the claim check) is passed into the Redis background queues for video transcoding workers to pick up and process.
- **Resources:**
  - [Claim Check Pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/claim-check) by Microsoft Azure: Cloud-native guidelines for avoiding message bus throttling using external storage.
  - [Claim Check](https://www.enterpriseintegrationpatterns.com/patterns/messaging/StoreInLibrary.html) by Gregor Hohpe: The original Enterprise Integration Pattern definition.

</details>

<details>
<summary><strong>Normalizer:</strong> Routes messages of disparate formats through custom translators so they all arrive at their destination in a single, unified format.</summary>

A pattern essential for integrating multiple diverse systems that speak different languages. When a single destination application needs to consume data from various legacy systems, APIs, or third-party vendors (each using wildly different XML, JSON, or CSV structures), a Normalizer sits in front of the destination. It identifies the incoming format and routes the message through a specific translator, ensuring the destination application only ever has to process one single, standardized canonical data model.

- **Examples:**
  - [airbytehq/airbyte](https://github.com/airbytehq/airbyte): An open-source data integration platform that functions essentially as a massive normalization engine. It connects to hundreds of different external APIs and databases, pulls their wildly differing schema structures, and normalizes all of them into a single, standardized JSON format for the destination data warehouse.
  - [huginn/huginn](https://github.com/huginn/huginn): An automated task agent that scrapes data from hundreds of different websites, APIs, and RSS feeds (all with different HTML/XML structures) and uses normalization agents to map them into a single, standard internal event JSON format so other agents can easily trigger actions based on them.
- **Resources:**
  - [Normalizer](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Normalizer.html) by Gregor Hohpe: The architectural theory for converting disparate data into canonical formats.

</details>

</details>

<details>
<summary><h3>Messaging Endpoint Patterns</h3></summary>

<br>

Architectural interfaces connecting an application's internal code to the external messaging system, dictating how messages are sent and received.

<details>
<summary><strong>Polling Consumer:</strong> Proactively checks for and pulls messages from a channel at specific intervals.</summary>

A client that proactively checks a channel at scheduled intervals to retrieve messages, rather than waiting for the broker to push them. It gives the consumer total control over its own ingestion rate, preventing it from being overwhelmed, but introduces latency and wasted CPU cycles if the queue is frequently empty.

- **Examples:**
  - [discourse/discourse](https://github.com/discourse/discourse): Relies heavily on Polling Consumers (via the Sidekiq background job framework) to continuously poll Redis queues for asynchronous tasks like sending digest emails or processing user badges.
- **Resources:**
  - [Polling Consumer Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PollingConsumer.html) by Gregor Hohpe: The architectural trade-offs between polling and event-driven consumption.

</details>

<details>
<summary><strong>Event-Driven Consumer:</strong> Operates on a push model, reacting automatically the moment a message is delivered to it.</summary>

A push-based client that sits idle until the messaging infrastructure actively delivers a message to it. It provides near real-time processing and is highly efficient on CPU resources since it doesn't constantly poll empty queues. However, it requires the consumer to be capable of handling unpredictable bursts of traffic without crashing.

- **Examples:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Its webhook ingest architecture acts as an Event-Driven Consumer. The server's HTTP endpoints sit idle and react instantly when an external system (like GitHub or Jira) pushes an event payload to them.
- **Resources:**
  - [Event-Driven Consumer](https://www.enterpriseintegrationpatterns.com/patterns/messaging/EventDrivenConsumer.html) by Gregor Hohpe: The foundational theory behind reactive message endpoints.

</details>

<details>
<summary><strong>Competing Consumers:</strong> Uses multiple consumers pulling from a single point-to-point channel to enable concurrent processing and scale out workloads.</summary>

Multiple identical consumer instances explicitly configured to listen to the exact same point-to-point channel. The channel guarantees that each message is delivered to only one of the consumers. This is the primary architectural pattern for horizontally scaling background processing workloads to handle massive, concurrent throughput.

- **Examples:**
  - [getsentry/sentry](https://github.com/getsentry/sentry): Deploys fleets of identical Celery worker nodes that act as Competing Consumers. They all pull from the same central Redis/RabbitMQ crash-report queues to process thousands of incoming errors in parallel without duplicating work.
- **Resources:**
  - [Competing Consumers Pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/competing-consumers) by Microsoft Azure: Cloud-native guidelines for implementing scalable worker pools.

</details>

<details>
<summary><strong>Message Dispatcher:</strong> A central component that consumes messages from a channel and actively distributes them to various worker threads or endpoints.</summary>

A central coordinator that consumes messages from a channel and delegates them to a pool of distinct worker threads or internal endpoints based on load, priority, or message type. It keeps the channel-reading logic centralized while distributing the actual processing execution.

- **Examples:**
  - [gitlabhq/gitlab-runner](https://github.com/gitlabhq/gitlab-runner): The core GitLab Runner application acts as a Message Dispatcher. It connects to the central GitLab instance, pulls pending CI/CD pipeline jobs, and dispatches them to specific, localized executors (like Docker, Shell, or Kubernetes) to run the actual builds.
- **Resources:**
  - [Message Dispatcher](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageDispatcher.html) by Gregor Hohpe: The logic of decoupling message ingestion from message processing.

</details>

<details>
<summary><strong>Selective Consumer:</strong> Applies a filter directly at the consumer level so it ignores messages on the channel that do not match its specific criteria.</summary>

A consumer that connects to a shared broadcast channel but explicitly configures a filter (often using SQL-like message selectors) so that the broker only delivers messages matching specific criteria. It prevents the consumer from wasting CPU and network bandwidth discarding irrelevant messages on the client side.

- **Examples:**
  - [home-assistant/core](https://github.com/home-assistant/core): Its internal automation engine operates as a collection of Selective Consumers. Dozens of automation scripts connect to the central Home Assistant event bus, but they register selective triggers so they only wake up and consume events originating from specific device IDs or states.
- **Resources:**
  - [Selective Consumer](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageSelector.html) by Gregor Hohpe: Using message selectors to filter data at the endpoint level.

</details>

<details>
<summary><strong>Durable Subscriber:</strong> Ensures a subscriber receives all messages sent to a topic, safely buffering them even if the subscriber is temporarily disconnected.</summary>

A specialized Publish-Subscribe client endpoint. When a standard subscriber disconnects, it misses any messages broadcast during its downtime. A Durable Subscriber registers its identity with the broker, forcing the broker to safely buffer all missed messages and deliver them the moment the subscriber reconnects.

- **Examples:**
  - *Note on Examples:* A Durable Subscriber is a protocol-level connection state (like an MQTT persistent session or a Kafka consumer group offset) maintained by the message broker infrastructure, rather than a standalone software application. Therefore, there are no open-source business application repositories that "are" a Durable Subscriber; they simply configure their client libraries to use the feature.
- **Resources:**
  - [Durable Subscriber](https://www.enterpriseintegrationpatterns.com/patterns/messaging/DurableSubscription.html) by Gregor Hohpe: Managing persistent sessions in pub/sub architectures.

</details>

<details>
<summary><strong>Idempotent Receiver:</strong> Safely handles duplicate messages by ensuring that processing the same message multiple times yields the exact same state as processing it once.</summary>

A highly robust consumer designed to handle the "At-Least-Once" delivery guarantees of modern distributed systems, where network retries often cause the exact same message to be delivered twice. The receiver tracks unique message IDs (or hashes payloads) to ensure that processing a duplicate message has absolutely no unintended side effects on the application's state.

- **Examples:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): Explicitly implements Idempotent Receivers in its saga participants to ensure that if a payment or kitchen-ticket message is delivered twice due to a network timeout, the customer is not double-charged.
- **Resources:**
  - [Idempotent Receiver](https://www.enterpriseintegrationpatterns.com/patterns/messaging/IdempotentReceiver.html) by Gregor Hohpe: The architectural necessity of idempotency in distributed architectures.

</details>

<details>
<summary><strong>Transactional Client:</strong> Groups multiple message sends and receives into a single atomic transaction that either fully succeeds or entirely rolls back.</summary>

A client endpoint that groups database updates and message publishing into a single atomic operation. If the application crashes immediately after writing to the database but before publishing the message to the queue, the entire transaction rolls back. This prevents system inconsistencies where a database records a state change that the rest of the distributed system is never notified about.

- **Examples:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): A textbook implementation of the Transactional Outbox pattern, ensuring that saving an order to the MySQL database and publishing the "OrderCreated" event to the message broker are executed as a single, atomic transactional client operation.
- **Resources:**
  - [Transactional Client](https://www.enterpriseintegrationpatterns.com/patterns/messaging/TransactionalClient.html) by Gregor Hohpe: Managing atomicity between persistent data stores and message brokers.

</details>

</details>

<details>
<summary><h3>API Gateway Patterns</h3></summary>

<br>

Front-facing aggregation and routing layers managing how external clients interface with internal, distributed microservices.

<details>
<summary><strong>API Gateway:</strong> Provides a single, unified entry point that handles request routing, composition, and security for internal microservices.</summary>

An architectural pattern where all external clients call a single, centralized endpoint instead of calling dozens of internal microservices directly. The gateway acts as a reverse proxy, handling cross-cutting concerns like authentication, SSL termination, rate limiting, and request routing. It hides the internal partitioning of the system from the outside world, drastically simplifying the client code.

- **Examples:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Google's 11-tier reference application uses a dedicated `frontend` service that acts as the singular API Gateway, shielding the user's browser from needing to know the IP addresses of the internal cart, currency, or checkout microservices.
- **Resources:**
  - [API Gateway Pattern](https://microservices.io/patterns/apigateway.html) by Chris Richardson: The comprehensive definition of the gateway's role in a distributed architecture.

</details>

<details>
<summary><strong>Backends for Frontends (BFF):</strong> Creates separate, custom-tailored API gateways for different types of clients (e.g., one for mobile, one for web) rather than forcing a one-size-fits-all API.</summary>

A variation of the API Gateway pattern where instead of a single, monolithic gateway for all clients, the system provisions multiple, smaller gateways tailored exactly to the needs of a specific UI or client type. A mobile app gets a Mobile BFF that returns compact JSON to save bandwidth, while a desktop web app gets a Web BFF that returns highly detailed, aggregated data. It prevents a primary gateway from becoming a bloated, unmaintainable bottleneck.

- **Examples:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Microsoft's official microservices reference application is the absolute textbook example of this pattern. It explicitly implements separate `Web.BFF.Shopping` and `Mobile.BFF.Shopping` gateway services to serve vastly different payload structures to its distinct client apps.
- **Resources:**
  - [Pattern: Backends For Frontends](https://samnewman.io/patterns/architectural/bff/) by Sam Newman: The original article coining the term and outlining the architectural split.

</details>

<details>
<summary><strong>Gateway Aggregation:</strong> Uses the gateway to fan out a single client request to multiple downstream microservices and aggregates their responses into a single payload for the client.</summary>

A pattern designed to reduce "chattiness" and network latency between a client and a distributed backend. Instead of a mobile app making five separate HTTP calls over a slow cellular network to fetch user details, order history, inventory, and shipping status, it makes one single call to the Gateway. The Gateway concurrently calls the five downstream microservices over the fast internal network, stitches their JSON responses together into a single, unified payload, and returns it to the client.

- **Examples:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): The API Gateway in this reference application explicitly implements an `OrderDetailsAggregator`. When the frontend requests an order summary, the aggregator concurrently fetches data from the separate Order, Kitchen, and Accounting microservices and compiles it into one response.
  - [dotnet/eShop](https://github.com/dotnet/eShop): Features a dedicated `Web.Shopping.HttpAggregator` service that compiles catalog items, basket status, and user pricing into a single frontend HTTP response.
- **Resources:**
  - [Gateway Aggregation pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/gateway-aggregation) by Microsoft Azure: Cloud-native guidelines for implementing scatter-gather aggregation at the edge.

</details>

<details>
<summary><strong>Gateway Routing:</strong> Maps external request paths or headers to specific, internal backend services invisibly to the caller.</summary>

The most fundamental feature of an API gateway, acting as an intelligent Layer 7 (application layer) reverse proxy. External clients make requests to a generic URL path (like `/api/users` or `/api/orders`), and the Gateway Routing mechanism inspects the URL path, HTTP method, or headers to silently forward the request to the correct internal microservice's IP address and port, often rewriting the URL in the process so the internal network structure remains completely hidden.

- **Examples:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): The `frontend` service uses strict HTTP routing rules to intercept incoming browser requests, passing `/cart` requests down to the Cart Service and `/product/*` requests down to the Product Catalog Service without the browser ever knowing those are distinct applications.
- **Resources:**
  - [Gateway Routing pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/gateway-routing) by Microsoft Azure: The architectural theory behind mapping external endpoints to internal service topologies.

</details>

</details>

<details>
<summary><h3>Resilience Patterns</h3></summary>

<br>

Defensive engineering tactics designed to protect systems from cascading failures, network unreliability, and resource exhaustion.

<details>
<summary><strong>Circuit Breaker:</strong> Prevents an application from repeatedly trying to execute an operation that is failing, "tripping" to return immediate errors and giving the failing service time to recover.</summary>

An automated electrical switch for software calls. When an external service or database starts failing or timing out, the circuit breaker counts the failures. Once a specific threshold is reached, the breaker "trips" (opens). For a set period, any further calls to that service instantly return an error or a fallback response without even attempting the network request. This prevents the caller's threads from hanging and gives the struggling downstream system breathing room to recover instead of being hammered with traffic.

- **Examples:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Microsoft's reference shopping application natively uses the Polly library to wrap all of its internal microservice HTTP calls in strict Circuit Breakers. If the Catalog service goes down, the Web UI instantly trips the circuit rather than freezing up while waiting for timeouts.
- **Resources:**
  - [CircuitBreaker](https://martinfowler.com/bliki/CircuitBreaker.html) by Martin Fowler: The definitive explanation of the closed, open, and half-open states of the pattern.
  - [Circuit Breaker pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/circuit-breaker) by Microsoft Azure: Cloud-native guidelines for implementation.

</details>

<details>
<summary><strong>Bulkhead:</strong> Partitions system resources (like connection pools or memory) so that a failure or spike in one component does not cascade and bring down the entire system.</summary>

Named after the partitioned watertight sections of a ship's hull. It isolates critical resources dedicated to different operational components. By assigning strict limits to connection pools, memory allocations, or CPU threads for specific tasks, a system ensures that an aggressive spike in traffic to Feature A cannot consume 100% of the server's resources, ensuring Feature B remains fully operational.

- **Examples:**
  - [elastic/elasticsearch](https://github.com/elastic/elasticsearch): The core database engine is a textbook example of internal bulkheading. It maintains strictly separated thread pools for different operations (e.g., one pool for `search`, a separate pool for `index`, another for `bulk` operations). This ensures that a massive spike in data ingestion cannot consume the threads required to serve user search queries.
- **Resources:**
  - [Bulkhead pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/bulkhead) by Microsoft Azure: The architectural theory behind resource isolation.
  - "Release It! Design and Deploy Production-Ready Software" by Michael Nygard: The book that popularized the Bulkhead pattern in software engineering.

</details>

<details>
<summary><strong>Retry with Exponential Backoff:</strong> Automatically retries a transiently failed operation, waiting progressively longer between each attempt to avoid overwhelming a struggling resource.</summary>

A self-healing mechanism designed for the inherent unreliability of distributed networks. Instead of failing immediately after one dropped packet, or retrying in a tight loop (which effectively acts as a self-inflicted DDoS attack against a recovering server), the system retries the operation with progressively longer wait times (e.g., 1s, 2s, 4s, 8s, 16s). It often incorporates "jitter" (randomized delays) to prevent thousands of clients from retrying at the exact same millisecond.

- **Examples:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): The social network inherently relies on this pattern for its federation model. If a remote server is temporarily offline when Mastodon tries to deliver a post, the background worker automatically schedules retries using an exponential backoff curve, eventually giving up and dropping the message into a dead letter queue if days pass without success.
- **Resources:**
  - [Exponential Backoff And Jitter](https://aws.amazon.com/blogs/architecture/exponential-backoff-and-jitter/) by AWS Architecture Blog: The mathematical breakdown of why jitter is necessary to prevent retry storms.

</details>

<details>
<summary><strong>Rate Limiting / Throttling:</strong> Restricts the total number of requests a client can make within a specific timeframe to protect overall service availability.</summary>

A defensive perimeter pattern. It tracks the volume of inbound traffic from distinct clients, IP addresses, or user accounts. If a client exceeds a predefined quota (e.g., 100 requests per minute), the system actively rejects subsequent requests (usually returning an HTTP 429 Too Many Requests status code) until the time window resets. This is critical for preventing resource exhaustion, mitigating brute-force attacks, and enforcing API billing tiers.

- **Examples:**
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): The open-source Git forge includes native rate-limiting middleware that tracks client IPs to prevent automated bots from spamming the server with clone requests or API queries, protecting the underlying database.
  - [discourse/discourse](https://github.com/discourse/discourse): Uses the `Rack::Attack` library as an application-level throttle to aggressively rate-limit password attempts and account creation endpoints.
- **Resources:**
  - [Rate Limiting pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/rate-limiting) by Microsoft Azure: Cloud-native design for distributed counters.

</details>

<details>
<summary><strong>Timeout Management:</strong> Sets strict time limits for operations to complete, proactively aborting them to prevent resources from being tied up indefinitely.</summary>

The most fundamental safeguard in distributed systems. Because a remote server might accept a connection but never return a response (a "hanging" connection), the calling application must define a hard maximum duration it is willing to wait. Once that clock expires, the client forcefully severs the connection, frees up its own thread, and throws an exception, preventing silent cascading failures across the network.

- **Examples:**
  - [prometheus/prometheus](https://github.com/prometheus/prometheus): The time-series monitoring system relies entirely on strict `scrape_timeout` configurations. Because it pings thousands of external targets continuously, it forcefully aborts any HTTP pull that takes too long, guaranteeing that a few frozen external servers cannot stall the global metric collection loop.
- **Resources:**
  - [Understanding API Timeouts](https://cloud.google.com/blog/products/api-management/understanding-api-timeouts) by Google Cloud: Guidelines on configuring connection, read, and write timeouts.

</details>

<details>
<summary><strong>Graceful Degradation:</strong> Allows a system to continue functioning with reduced features, older cached data, or lower performance rather than failing completely when a dependency goes down.</summary>

A design philosophy that prioritizes partial availability over total system failure. Instead of throwing a massive 500 Internal Server Error when a non-critical downstream dependency fails, the system catches the error and serves a fallback experience. This ensures the primary user journey (like reading an article or checking out a cart) remains operational, even if auxiliary features are temporarily missing.

- **Examples:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): The frontend application is explicitly engineered for graceful degradation. If the underlying `recommendation-service` crashes, the UI catches the timeout and seamlessly displays a hardcoded list of default products, allowing the user to continue shopping without ever knowing a backend component failed.
- **Resources:**
  - [Graceful Degradation](https://en.wikipedia.org/wiki/Fault_tolerance#Graceful_degradation): The overarching engineering principles of fault tolerance.
  - "Building Microservices" by Sam Newman: Covers strategies for implementing fallbacks and default behaviors in UI composition.

</details>

<details>
<summary><strong>Health Check Endpoint:</strong> Exposes a dedicated API route that monitoring tools ping to verify the operational status and database connectivity of a service.</summary>

An observability pattern mandated by modern container orchestration. The application exposes a standardized HTTP route (commonly `/healthz` or `/ready`). Infrastructure managers (like Kubernetes or AWS Load Balancers) continuously ping this endpoint. The endpoint executes internal checks (e.g., "Can I reach my database? Am I out of memory?") and returns a 200 OK. If the endpoint returns an error or times out, the orchestrator automatically stops routing traffic to the instance and eventually restarts it.

- **Examples:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Every microservice in the repository implements the ASP.NET Core Health Checks routing (`/hc` and `/liveness`). These endpoints are continuously polled by the Kubernetes cluster to manage pod lifecycles and traffic routing.
- **Resources:**
  - [Health Endpoint Monitoring pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/health-endpoint-monitoring) by Microsoft Azure: Guidelines for separating liveness probes from readiness probes.
  - [Kubernetes Liveness, Readiness and Startup Probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/): The definitive operational guide to consuming health endpoints.

</details>

</details>

<details>
<summary><h3>Saga Patterns</h3></summary>

<br>

Strategies for managing long-lived, distributed business transactions across independent services without relying on two-phase commits.

<details>
<summary><strong>Choreographed Saga:</strong> A decentralized transaction model where each local service publishes domain events that trigger local transactions in other services, with no central controller.</summary>

This pattern operates like a relay race or a highly decoupled dance. When the first service completes its local transaction, it publishes an event to a message broker. Other services are actively subscribed to that broker; they hear the event, execute their own local database transactions, and publish their own subsequent events. If any service fails to complete its task, it publishes a failure event, which triggers the preceding services to execute compensating transactions (rollbacks) to undo their work. It requires very little central logic but can become difficult to trace or debug as the workflow grows increasingly complex.

- **Examples:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Microsoft's reference application heavily uses choreographed sagas for its checkout process. When a user places an order, the Order service publishes an `OrderStartedIntegrationEvent`. The Basket service, Catalog service, and Payment service independently listen to this event, update their local databases, and fire back their own events to complete the chain without a central manager.
- **Resources:**
  - [Pattern: Saga Choreography](https://microservices.io/patterns/data/saga.html#example-choreography-based-saga) by Chris Richardson: The definitive breakdown of event-driven distributed transactions.
  - [Choreography pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/choreography) by Microsoft Azure: Cloud-native guidelines for decentralizing workflow logic.

</details>

<details>
<summary><strong>Orchestrated Saga:</strong> A centralized transaction model where a dedicated coordinator (orchestrator) tells participating services exactly what local transactions or compensating rollbacks to execute.</summary>

This pattern operates like a conductor leading an orchestra. A single, centralized "Saga Orchestrator" object or service maintains the entire state machine of the business transaction. It sequentially sends command messages to downstream services, waits for their explicit reply messages, and decides the next step based on those replies. If a downstream service reports a failure, the orchestrator takes over and actively fires command messages to the previous services, instructing them to execute their specific compensating rollbacks. It provides excellent, unified visibility into the state of the transaction but introduces a point of centralized logic and coupling.

- **Examples:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): The reference application for the "Microservices Patterns" book features a textbook `CreateOrderSaga` orchestrator. This specific class acts as the central brain, actively sending creation commands to the Kitchen, Consumer, and Accounting microservices and managing their replies to ensure the entire distributed transaction either completes or rolls back cleanly.
  - [berndruecker/trip-booking-saga-java](https://github.com/berndruecker/trip-booking-saga-java): A pure business application demonstrating a complex travel booking scenario (booking a flight, hotel, and rental car across different services). It uses an orchestration engine (Camunda) to centrally manage the state and execute rollbacks if the hotel booking succeeds but the flight booking fails.
- **Resources:**
  - [Pattern: Saga Orchestration](https://microservices.io/patterns/data/saga.html#example-orchestration-based-saga) by Chris Richardson: The architectural theory behind centralizing distributed transaction state.
  - [Orchestrator pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/orchestrator) by Microsoft Azure: Building stateful, centralized workflow coordinators.

</details>

</details>

<details>
<summary><h3>Streaming Patterns</h3></summary>

<br>

High-throughput paradigms for handling unbounded, continuous flows of data and database state changes in real-time.

<details>
<summary><strong>Change Data Capture (CDC):</strong> Automatically captures database inserts, updates, and deletes, delivering them as real-time event streams to downstream systems.</summary>

An architectural approach that turns a static database into a dynamic event source. Instead of downstream systems polling the database for changes (which is slow and resource-heavy), CDC watches the database and immediately broadcasts every row-level change as a message. This ensures that caches, search indexes, and data warehouses stay perfectly synchronized with the primary database in near real-time.

- **Examples:**
  - [airbytehq/airbyte](https://github.com/airbytehq/airbyte): An open-source data integration platform that inherently relies on CDC patterns to sync data between different sources. It uses specialized connectors to capture incremental changes from production databases and stream them into data lakes or warehouses.
  - [sysown/proxysql](https://github.com/sysown/proxysql): A high-performance MySQL proxy that uses CDC-like patterns to track database state and configuration changes, ensuring that its internal routing tables are updated instantly across distributed nodes.
- **Resources:**
  - [What is Change Data Capture?](https://www.redhat.com/en/topics/integration/what-is-change-data-capture) by Red Hat: A clear overview of the benefits of event-driven data synchronization.
  - [Change Data Capture pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/change-data-capture) by Microsoft Azure: Architectural guidelines for implementing CDC in cloud environments.

</details>

<details>
<summary><strong>Event Streaming Platform:</strong> Uses a distributed, append-only commit log to durably store and process massive streams of records in real-time.</summary>

A macro-architecture where the "log" is the primary source of truth. Unlike traditional message brokers that delete messages once they are consumed, an Event Streaming Platform persists events in an ordered, immutable log. This allows multiple different applications to "replay" the stream from any point in time, enabling complex real-time analytics, event sourcing, and the creation of materialized views.

- **Examples:**
  - *Note on Examples:* An Event Streaming Platform is a foundational piece of infrastructure (like Apache Kafka, Redpanda, or Apache Pulsar) rather than an individual business application. Business applications are "stream processors" that run *on* these platforms. Therefore, there is no single open-source business application repository that represents the platform itself.
- **Resources:**
  - [What is Event Streaming?](https://www.confluent.io/learn/event-streaming/) by Confluent: A deep dive into the "log-centric" mindset of modern data architecture.
  - [Introduction to Event Streaming](https://kafka.apache.org/documentation/#intro) by Apache Kafka: The foundational concepts of topics, partitions, and immutable logs.

</details>

<details>
<summary><strong>Log-Based CDC:</strong> A specific, highly efficient type of CDC that reads directly from the database's internal transaction log to capture changes without impacting query performance.</summary>

The "gold standard" for Change Data Capture. While some CDC methods use database triggers or polling (which can slow down the production database), Log-Based CDC reads the database's internal transaction log (like MySQL's binlog or Postgres's WAL) directly from the disk. This allows the system to capture every single change, including deletes and schema updates, with zero overhead on the database's execution engine.

- **Examples:**
  - [debezium/debezium](https://github.com/debezium/debezium): Although often used as a tool, Debezium is the industry-standard implementation of Log-Based CDC. It consists of a set of source connectors that "tail" the transaction logs of databases like MySQL, MongoDB, and Postgres to turn them into event streams.
  - [meroxa/conduit](https://github.com/meroxa/conduit): An open-source data integration tool written in Go that implements log-based CDC to move data between various infrastructure components with extremely low latency.
- **Resources:**
  - [Log-Based Change Data Capture](https://www.qlik.com/us/change-data-capture/log-based-cdc) by Qlik: A technical comparison between log-based, trigger-based, and query-based CDC.
  - [Debezium Architecture](https://debezium.io/documentation/reference/stable/architecture.html): A detailed look at how log-based connectors interface with database internals.

</details>

</details>

<details>
<summary><h3>System Management Patterns</h3></summary>

<br>

Administrative and diagnostic tools injected into the messaging architecture to monitor, audit, and debug asynchronous communication flows.

<details>
<summary><strong>Wire Tap:</strong> Silently duplicates messages from a channel and routes them to a secondary channel for inspection or logging without affecting the primary message flow.</summary>

An observability pattern designed for "non-intrusive" monitoring. It functions like a physical phone tap; a component is inserted into the message path that intercepts an incoming message, makes an exact replica, and sends the replica to a separate diagnostic or logging channel while allowing the original message to continue to its destination instantly. This allows developers to debug live traffic in production without adding latency or risk to the primary business transaction.

- **Examples:**
  - *Note on Examples:* A Wire Tap is an operational routing configuration implemented at the infrastructure level (e.g., using a service mesh sidecar like Istio, an Nginx mirror, or a RabbitMQ exchange to duplicate traffic). Because it is a method of orchestrating existing services rather than a standalone software application, there are no open-source business application repositories that represent it natively.
- **Resources:**
  - [Wire Tap](https://www.enterpriseintegrationpatterns.com/patterns/messaging/WireTap.html) by Gregor Hohpe: The original pattern definition for non-intrusive message inspection.
  - [Istio Traffic Mirroring](https://istio.io/latest/docs/tasks/traffic-management/mirroring/): Practical implementation documentation for wire-tapping traffic in a service mesh.

</details>

<details>
<summary><strong>Message History:</strong> Appends a running list of all components a message has passed through directly to the message header for debugging and tracing.</summary>

A distributed tracing pattern that turns a message into its own travel log. As a message moves through various routers, filters, and processors, each component "stamps" its identity and a timestamp into a specific metadata array in the message header. This provides an immutable audit trail that allows developers to reconstruct the exact path a message took through a complex, decoupled system to identify exactly where a delay or logic error occurred.

- **Examples:**
  - [jaegertracing/jaeger](https://github.com/jaegertracing/jaeger): While Jaeger is a tool, the applications that integrate with it (like [mastodon/mastodon](https://github.com/mastodon/mastodon)) explicitly implement the Message History pattern by propagating "Trace Context" headers across every microservice and background worker to track a request's lifecycle.
- **Resources:**
  - [Message History](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageHistory.html) by Gregor Hohpe: The architectural theory behind self-documenting message paths.
  - [W3C Trace Context Specification](https://www.w3.org/TR/trace-context/): The industry standard for how "history" metadata should be formatted in message headers.

</details>

<details>
<summary><strong>Message Log:</strong> Records the complete, immutable details of every message passing through a system to enable deep auditing and historical replay capabilities.</summary>

A persistence pattern for system accountability. Unlike standard application logging (which records *what* the application did), a Message Log captures the *entire* raw message, including headers and payload, exactly as it appeared on the wire. This creates a high-fidelity audit trail essential for financial systems, compliance, and "Time Travel" debugging, where a faulty message can be retrieved months later to see exactly what triggered a specific system state.

- **Examples:**
  - [tryghost/ghost](https://github.com/tryghost/ghost): The open-source publishing platform maintains a robust internal "Activity Log" that functions as a message log, capturing the full metadata and state of every internal API request and integration hook for administrative auditing.
  - [discourse/discourse](https://github.com/discourse/discourse): Implements a comprehensive "Staff Action Log" and "WebHook Log" that records the full payload of incoming and outgoing events to ensure all system-level communications are auditable and replayable for troubleshooting.
- **Resources:**
  - [Message Store](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageStore.html) by Gregor Hohpe: Discusses the architectural implications of persisting every message in a distributed system.

</details>

</details>

<details>
<summary><h3>Database & Domain Integration Patterns</h3></summary>

<br>

Bridging techniques that safely synchronize strict database transactions with eventual consistency messaging and legacy domain boundaries.

<details>
<summary><strong>Transactional Outbox Pattern:</strong> A crucial pattern for microservices that resolves the dual-write problem by saving state changes and queued events within the same local database transaction before a separate relay process publishes them to a message broker.</summary>

In distributed systems, updating a database and publishing a message to a broker (the "dual-write") is not atomic; one can succeed while the other fails, leading to data inconsistency. This pattern solves the issue by creating an "Outbox" table in the same database as the business entities. Every time a business record is updated, a corresponding event record is inserted into the Outbox table within the same ACID transaction. A separate relay process (like a polling thread or a CDC tool) then reads the Outbox table and reliably publishes the messages to the broker.

- **Examples:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): The primary reference application for Chris Richardson’s "Microservices Patterns," which explicitly implements the Transactional Outbox using a specialized `MessagePublishingWatcher` to relay events from a MySQL outbox table.
  - [dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers): A comprehensive .NET reference application that uses an Integration Event Log (acting as a Transactional Outbox) to ensure that catalog updates and order placements are reliably broadcast to other microservices.
- **Resources:**
  - [Pattern: Transactional outbox](https://microservices.io/patterns/data/transactional-outbox.html) by Chris Richardson: The industry-standard definition and implementation guide.
  - [The Outbox Pattern](https://event-driven.io/en/outbox_pattern_done_right/): A technical deep dive into common implementation pitfalls and performance considerations.

</details>

<details>
<summary><strong>Anti-Corruption Layer (ACL):</strong> A strategic Domain-Driven Design integration pattern that places a translation layer between different subsystems to prevent a legacy or external system's domain model from polluting a new system's model.</summary>

When a modern application must interface with a legacy system or a third-party API that uses a messy or incompatible data model, developers use an ACL to protect the "integrity" of the new system. The ACL acts as a bidirectional translator: it converts requests from the new system's clean domain model into the legacy system's format, and translates the legacy responses back into the new domain's language. This ensures that the legacy system's technical debt or poor design does not leak into the new codebase.

- **Examples:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): This TypeScript reference application uses strict infrastructure adapters that function as Anti-Corruption Layers, isolating the core business domain from external APIs and database schemas.
  - [kgrzybek/modular-monolith-with-ddd](https://github.com/kgrzybek/modular-monolith-with-ddd): Implements specialized "Integration" modules between bounded contexts that act as ACLs, ensuring that the internal logic of one module remains decoupled from the implementation details of another.
- **Resources:**
  - [Anti-corruption Layer pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/anti-corruption-layer) by Microsoft Azure: Practical guidelines for implementing translation layers in cloud-native migrations.
  - [Domain-Driven Design: Anti-Corruption Layer](https://ddd-practitioners.com/home/glossary/anti-corruption-layer/): An overview of the strategic importance of ACLs in complex domain modeling.

</details>

</details>

</details>

<details>
<summary><h2>Layer 3: Application Architecture Patterns</h2></summary>

<br>

*Internal structure of a single application or service*

<details>
<summary><h3>Presentation / UI Architecture Patterns</h3></summary>

<br>

Patterns that dictate how user interfaces are structured and how they communicate with underlying business logic.

<details>
<summary><strong>Model-View-Controller (MVC):</strong> Separates user interface into Model (data), View (presentation), and Controller (logic).</summary>

The classic pattern for decoupling data representation from user interaction. The Model manages the data and business rules, the View displays the information, and the Controller intercepts user input to update the Model. It is the architectural foundation of modern web development, allowing for independent evolution of the user interface and core business logic.

- **Examples:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): A primary implementation of the MVC pattern using Ruby on Rails for a massive, real-world server-side rendered application.
  - [moodle/moodle](https://github.com/moodle/moodle): An open-source learning platform utilizing a strict MVC architecture to manage complex student data and course presentation.
- **Resources:**
  - [GUI Architectures](https://martinfowler.com/eaaDev/uiArchs.html) by Martin Fowler: A deep dive into the evolution of MVC and its variants.

</details>

<details>
<summary><strong>Model-View-Presenter (MVP):</strong> Presenter handles all UI logic, making the View passive.</summary>

A derivation of MVC where the Presenter acts as a middleman. In MVP, the View is "passive"; it does not listen to the Model directly. Instead, the Presenter retrieves data from the Model, formats it, and instructs the View exactly what to display. This enhances the testability of UI logic by removing direct dependencies on UI frameworks.

- **Examples:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Historically used MVP for many core Android activities to ensure encryption logic remained isolated from OS-level UI code.
- **Resources:**
  - [Model-View-Presenter](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter): An overview of the Supervising Controller and Passive View variations.

</details>

<details>
<summary><strong>Model-View-ViewModel (MVVM):</strong> Supports two-way data binding between View and ViewModel.</summary>

A pattern designed to leverage data-binding technologies. The ViewModel provides a specialized data model for the View, containing "view state" such as input validation or button status. Through two-way binding, changes in the UI update the ViewModel, and changes in the ViewModel refresh the UI without manual DOM or widget manipulation.

- **Examples:**
  - [kiwix/kiwix-android](https://github.com/kiwix/kiwix-android): An open-source offline reader that implements MVVM using Android Architecture Components to bind library state to the UI.
  - [Anki-Android/Anki-Android](https://github.com/ankidroid/Anki-Android): A popular flashcard application using MVVM to manage complex states of card reviews and deck management.
- **Resources:**
  - [WPF Apps With The MVVM Design Pattern](https://learn.microsoft.com/en-us/archive/msdn-magazine/2009/february/patterns-wpf-apps-with-the-mvvm-design-pattern) by Microsoft: The foundational article that popularized MVVM.

</details>

<details>
<summary><strong>Flux / Redux Architecture:</strong> Unidirectional data flow for client-side applications.</summary>

A pattern designed to manage complex state in single-page applications (SPAs). It enforces a strict one-way data loop: Actions are sent to a central Dispatcher, which updates a Store. The Store then notifies the View to re-render. This explicit and sequential state management enables predictable debugging and state tracking.

- **Examples:**
  - [zulip/zulip-mobile](https://github.com/zulip/zulip-mobile): Uses Redux to manage a single source of truth for all chat messages and user presence state in its mobile client.
  - [wordpress-mobile/WordPress-Android](https://github.com/wordpress-mobile/WordPress-Android): Employs a Flux-based architecture (FluxC) to manage content synchronization across the mobile application.
- **Resources:**
  - [Flux Concepts](https://facebookarchive.github.io/flux/docs/in-depth-overview/): The original documentation defining the unidirectional data flow.

</details>

<details>
<summary><strong>Micro Frontends Architecture:</strong> Decomposes a web application into independent frontend modules.</summary>

An organizational and technical pattern that extends microservices to the frontend. A large application is decomposed into independent, feature-based modules developed and deployed by different teams. These modules are integrated at runtime to present a seamless experience to the user.

- **Examples:**
  - [openmrs/openmrs-esm-core](https://github.com/openmrs/openmrs-esm-core): The frontend for the Open Medical Record System, built on micro-frontend architecture to allow modular hospital customisation.
- **Resources:**
  - [Micro Frontends](https://martinfowler.com/articles/micro-frontends.html) by Cam Jackson: A technical guide to composition and integration strategies.

</details>

</details>

<details>
<summary><h3>Domain-Centric / Layering Architectures</h3></summary>

<br>

Patterns defining the macro-structure of internal layers to isolate the core business domain from infrastructure.

<details>
<summary><strong>Hexagonal Architecture (Ports and Adapters):</strong> Isolates core domain logic via ports and adapters.</summary>

An architectural style that treats business logic as the core of the application, isolated from external concerns. Communication occurs through "Ports" (interfaces), which are implemented by "Adapters" to connect to specific technologies such as databases or APIs. This ensures high testability and allows for technology swaps without impacting core business logic.

- **Examples:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): A TypeScript reference application demonstrating strict domain isolation and business logic protection.
- **Resources:**
  - [Hexagonal architecture](https://alistair.cockburn.us/hexagonal-architecture/) by Alistair Cockburn: The original article defining the ports and adapters terminology.

</details>

<details>
<summary><strong>Clean Architecture:</strong> Concentric rings enforcing the Dependency Rule.</summary>

A refinement of layering patterns that organizes code into concentric circles where dependencies point strictly inward. The innermost circle contains stable business rules (Entities), while the outermost layers handle frameworks and drivers. This ensures that changes in external tools never force a change in the core business rules.

- **Examples:**
  - [android10/Android-CleanArchitecture](https://github.com/android10/Android-CleanArchitecture): A classic reference application implementing Clean Architecture principles for mobile development.
  - [ivanpaulovich/clean-architecture-manga](https://github.com/ivanpaulovich/clean-architecture-manga): A .NET implementation that follows strict Clean Architecture rules to manage a library system.
- **Resources:**
  - [The Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) by Robert C. Martin: The definitive post outlining the layers and the Dependency Rule.

</details>

<details>
<summary><strong>Onion Architecture:</strong> Domain model at the core with inward-pointing dependencies.</summary>

This architecture places the Domain Model at the center, surrounded by Domain Services, Application Services, and Infrastructure. It relies on Dependency Inversion: the core defines the interfaces, and the outer layers implement them, ensuring the application is built around the business domain rather than technology stacks.

- **Examples:**
  - [jasontaylordev/CleanArchitecture](https://github.com/jasontaylordev/CleanArchitecture): An industry-standard .NET template for Onion-style layering with a central domain core.
- **Resources:**
  - [The Onion Architecture](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/) by Jeffrey Palermo: The original series defining the architecture and its tiers.

</details>

</details>

<details>
<summary><h3>Data Source & Object-Relational Patterns</h3></summary>

<br>

Patterns managing how in-memory application objects interact with the underlying database or persistence layer.

<details>
<summary><strong>Repository Pattern:</strong> Mediates between domain and data mapping layers.</summary>

An abstraction layer acting as a gatekeeper between business logic and the database. It provides a collection-like interface (e.g., `Add`, `Find`) for accessing domain objects, hiding the details of data retrieval. This facilitates persistence ignorance in business logic and simplifies unit testing via in-memory implementation.

- **Examples:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): Every domain aggregate has a corresponding Repository interface implemented in the infrastructure layer to isolate the domain from the database.
  - [android10/Android-CleanArchitecture](https://github.com/android10/Android-CleanArchitecture): Coordinates data retrieval from local caches and remote network sources using the Repository pattern.
- **Resources:**
  - [The Repository Pattern](https://martinfowler.com/eaaCatalog/repository.html) by Martin Fowler: The definitive definition of the pattern.

</details>

<details>
<summary><strong>Active Record:</strong> An object that wraps a database row, encapsulating both data and behavior.</summary>

A pattern where the data model object contains the logic to manage its own persistence (save, update, delete). Each instance corresponds directly to a database row. It is optimized for rapid development and CRUD-heavy applications.

- **Examples:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): A Ruby on Rails application where core entities (Users, Statuses) contain both business data and persistence logic.
  - [discourse/discourse](https://github.com/discourse/discourse): Uses Active Record to manage its forum state and user interactions.
- **Resources:**
  - [Active Record](https://martinfowler.com/eaaCatalog/activeRecord.html) by Martin Fowler: An overview of the pattern's structure and trade-offs.

</details>

</details>

<details>
<summary><h3>State Management & Data Flow Patterns</h3></summary>

<br>

Patterns defining how application state is mutated, stored, and propagated.

<details>
<summary><strong>CQRS (Command Query Responsibility Segregation):</strong> Separates data modification from data retrieval.</summary>

An architecture that splits the traditional CRUD model into Commands (mutating state) and Queries (returning data). This allows the read and write sides of an application to be optimized and scaled independently, which is effective in complex domains where write logic and read requirements differ.

- **Examples:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): The Ordering microservice strictly separates incoming REST commands from database queries using the MediatR library.
  - [kgrzybek/modular-monolith-with-ddd](https://github.com/kgrzybek/modular-monolith-with-ddd): Enforces CQRS across business modules, separating write-model entities from read-model DTOs.
- **Resources:**
  - [CQRS](https://martinfowler.com/bliki/CQRS.html) by Martin Fowler: The foundational article defining the pattern.

</details>

<details>
<summary><strong>Event Sourcing:</strong> Stores state as an immutable sequence of events.</summary>

Instead of storing current state, Event Sourcing records every state-mutating action as an immutable historical event. Current state is derived by replaying the event log. This provides a reliable audit trail and enables point-in-time state reconstruction.

- **Examples:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): The Accounting Service stores financial transactions as a sequence of events rather than overwriting database rows.
  - [ornicar/lila](https://github.com/ornicar/lila): The Lichess server derives board state from the sequential, immutable log of player moves.
- **Resources:**
  - [Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html) by Martin Fowler: Breakdown of replaying application state.

</details>

</details>

<details>
<summary><h3>Concurrency & Performance Patterns</h3></summary>

<br>

Patterns focused on high-throughput and low-latency execution.

<details>
<summary><strong>LMAX Disruptor Pattern:</strong> High-performance inter-thread communication via ring buffer.</summary>

Designed to overcome performance bottlenecks of traditional concurrent queues by using a pre-allocated ring buffer and sequence-tracking. This aligns with modern CPU hardware behavior (mechanical sympathy) to achieve massive throughput and predictable latency.

- **Examples:**
  - *Note on Examples:* The Disruptor is an infrastructure-level framework. Production applications typically consume it through high-performance tools such as logging frameworks (Log4j2) or query engines (Trino) rather than implementing it in business logic.
- **Resources:**
  - [The LMAX Disruptor](https://lmax-exchange.github.io/disruptor/): Official technical documentation on the ring buffer architecture.

</details>

<details>
<summary><strong>Software Transactional Memory (STM):</strong> Concurrency control analogous to database transactions.</summary>

Allows developers to group multiple changes to shared memory into atomic transactions. If conflicts occur, transactions are automatically retried. This eliminates deadlocks and provides a safer alternative to manual lock management.

- **Examples:**
  - [metabase/metabase](https://github.com/metabase/metabase): Relies on Clojure's native STM to safely manage global application configuration across concurrent user sessions.
- **Resources:**
  - [Software Transactional Memory](https://en.wikipedia.org/wiki/Software_transactional_memory): Technical overview of memory transactions.

</details>

</details>

<details>
<summary><h3>System Connectivity Patterns</h3></summary>

<br>

Patterns dictating how applications handle network reliance and synchronization.

<details>
<summary><strong>Offline-First Architecture:</strong> Application operates primarily against a local database.</summary>

A design paradigm where the app reads and writes to local storage by default, ensuring instant responsiveness. Background synchronization reconciles local data with the remote server when connectivity is available, handling conflict resolution as required.

- **Examples:**
  - [standardnotes/app](https://github.com/standardnotes/app): A notes application that writes to local storage for seamless offline use, syncing encrypted payloads to the server in the background.
  - [logseq/logseq](https://github.com/logseq/logseq): Functions entirely offline on local files, using background sync processes to coordinate with remote repositories.
- **Resources:**
  - [Offline First](https://offlinefirst.org/): Community principles for building apps for disconnected environments.

</details>

<details>
<summary><strong>Optimistic UI:</strong> Updates interface immediately assuming network success.</summary>

A frontend pattern that masks latency by updating the UI instantly when a user acts, before the server responds. If the background request fails, the local state is rolled back and the user is notified.

- **Examples:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Updates the UI instantly when a user "favorites" a status, incrementing counters locally before the server confirmation.
  - [zulip/zulip-mobile](https://github.com/zulip/zulip-mobile): Displays sent chat messages immediately in the feed, showing a pending state until acknowledged by the server.
- **Resources:**
  - [True Lies Of Optimistic User Interfaces](https://www.smashingmagazine.com/2016/11/true-lies-of-optimistic-user-interfaces/): Psychology and technical rollback mechanisms of the pattern.

</details>

</details>

<details>
<summary><h3>Mobile Architecture Patterns</h3></summary>

<br>

Frameworks and methodologies designed for mobile lifecycle and routing constraints.

<details>
<summary><strong>VIPER:</strong> Isolates logic, UI, and routing into separate components.</summary>

A modular architecture for iOS that removes business logic and routing from the view controller. Navigation is isolated in the Router and business rules in the Interactor, allowing for unit testing without UI components.

- **Examples:**
  - *Note on Examples:* VIPER is primarily used in large-scale proprietary enterprise applications. Reference implementations are typically observed in architectural templates rather than open-source consumer codebases.
- **Resources:**
  - [Architecting iOS Apps with VIPER](https://www.objc.io/issues/13-architecture/viper/): The article that introduced the pattern to the iOS community.

</details>

<details>
<summary><strong>RIBs:</strong> Business logic tree driven by routing state.</summary>

An architecture where business logic (Interactors) functions independently of the view hierarchy. A business process can exist and route data regardless of whether a View is currently attached, designed for large engineering teams and complex state management.

- **Examples:**
  - *Note on Examples:* RIBs is a specialized architecture used in large-scale applications such as Uber. The open-source `uber/RIBs` repository provides the framework and documentation rather than a consumer implementation.
- **Resources:**
  - [RIBs - Uber's cross-platform architecture](https://github.com/uber/RIBs): Technical documentation on separating View and Logic trees.

</details>

</details>

<details>
<summary><h3>Test Double Patterns</h3></summary>

<br>

Specialized objects used in automated testing to isolate code by simulating dependencies.

<details>
<summary><strong>Stub:</strong> Provides hardcoded answers to calls during a test.</summary>

Stubs provide consistent data to the system under test, such as hardcoding a specific service response to isolate the test from external API variability.

- **Examples:**
  - [discourse/discourse](https://github.com/discourse/discourse): Hardcodes successful responses from external providers to verify application logic without network calls.
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Simulates Git repository states to test UI logic without actual disk-heavy operations.
- **Resources:**
  - [Mocks Aren't Stubs](https://martinfowler.com/articles/mocksArentStubs.html) by Martin Fowler: Deep dive into state-based vs. interaction-based testing.

</details>

<details>
<summary><strong>Fake:</strong> Working implementation unsuitable for production.</summary>

Fakes are lightweight versions of real systems, such as in-memory databases, that behave like production systems during test cycles but offer significantly faster execution.

- **Examples:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Uses an InMemory database provider for integration tests to avoid SQL Server overhead.
  - [metabase/metabase](https://github.com/metabase/metabase): Employs in-memory H2 databases to simulate data warehouse environments during testing.
- **Resources:**
  - [Testing with Fakes](https://github.com/google/googletest/blob/main/docs/gmock_cook_book.md#fakes): Documentation on using simplified implementations for efficiency.

</details>

</details>

</details>

<details>
<summary><h2>Layer 4: Software Design Patterns</h2></summary>

<br>

*Micro-level solutions for object-oriented design problems*

<details>
<summary><h3>Creational Patterns</h3></summary>

<br>

*Patterns that abstract the instantiation process, making a system independent of how its objects are created, composed, and represented*

<details>
<summary><strong>Singleton:</strong> Ensures a class has only one instance and provides a global point of access to it.</summary>

A pattern used to coordinate state across an entire application by restricting a class to a single instance. It is commonly used for global configurations, database connection pools, or hardware managers. While powerful for centralized control, it creates a global state that can make unit testing more difficult if not managed via dependency injection.

- **Examples:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Uses Singletons for core system managers, such as the `DatabaseFactory` and `ApplicationContext` providers, ensuring centralized access to critical encrypted storage.
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Employs Singletons to manage global system settings and feature flags, providing a single source of truth for application behavior across concurrent web requests.
- **Resources:**
  - [Singleton Pattern](https://refactoring.guru/design-patterns/singleton): A technical breakdown of implementation strategies and common pitfalls by Refactoring Guru.
  - [Singleton Design Pattern](https://sourcemaking.com/design_patterns/singleton): A comprehensive look at the pattern's structure and thread safety considerations by SourceMaking.

</details>

<details>
<summary><strong>Factory Method:</strong> Defines an interface for creating an object but lets subclasses alter the type of objects created.</summary>

A pattern that provides a way to delegate the instantiation logic to child classes. Instead of the main application code calling "new" on a specific class, it calls a factory method. This allows the system to remain decoupled from the specific concrete types it needs to create, facilitating easier extension when new types are added.

- **Examples:**
  - [moodle/moodle](https://github.com/moodle/moodle): Uses factory methods to instantiate various plugin types and activity modules, allowing the core engine to manage diverse content types without knowing their specific implementations.
  - [metabase/metabase](https://github.com/metabase/metabase): Employs factory methods to create specific database driver instances (e.g., Postgres vs. MySQL) based on the user's connection configuration.
- **Resources:**
  - [Factory Method](https://refactoring.guru/design-patterns/factory-method): Visual guides on decoupling creators from products by Refactoring Guru.
  - [Factory Method Pattern](https://sourcemaking.com/design_patterns/factory_method): Structural UML diagrams and implementation checklists by SourceMaking.

</details>

<details>
<summary><strong>Abstract Factory:</strong> Provides an interface for creating families of related objects without specifying concrete classes.</summary>

An extension of the Factory pattern that groups related factories together. It allows a system to be independent of how its products are created, composed, and represented. It is especially useful when a system must be configured with one of multiple families of products, such as different UI themes or different storage backends.

- **Examples:**
  - [tryghost/ghost](https://github.com/tryghost/ghost): Implements an abstract factory for its storage layer, providing related objects for local file storage, S3 storage, or other cloud providers depending on the environment configuration.
  - [home-assistant/core](https://github.com/home-assistant/core): Uses abstract factories to generate families of entities (sensors, lights, switches) for specific hardware integrations, ensuring all components from a single vendor share consistent internal logic.
- **Resources:**
  - [Abstract Factory](https://refactoring.guru/design-patterns/abstract-factory): Detailed explanation of product families and factory interfaces by Refactoring Guru.
  - [Abstract Factory Design Pattern](https://sourcemaking.com/design_patterns/abstract_factory): A deep dive into the pattern's intent and applicability by SourceMaking.

</details>

<details>
<summary><strong>Builder:</strong> Separates the construction of a complex object from its representation.</summary>

A pattern designed to handle objects that require many steps or many parameters to initialize. Instead of a "telescoping constructor" with dozens of arguments, the Builder allows you to set only the specific values you need in a readable, step-by-step manner before finally producing the finished object.

- **Examples:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Relies on the Builder pattern for constructing complex objects like `Notification` records or `Message` payloads, where many optional fields must be set before transmission.
  - [getsentry/sentry](https://github.com/getsentry/sentry): Uses builders within its event processing pipeline to assemble complex crash report events from disparate pieces of telemetry data before they are saved to the database.
- **Resources:**
  - [Builder Pattern](https://refactoring.guru/design-patterns/builder): Practical examples of step-by-step object construction by Refactoring Guru.
  - [Builder Design Pattern](https://sourcemaking.com/design_patterns/builder): An overview of how to parse complex representations by SourceMaking.

</details>

<details>
<summary><strong>Prototype:</strong> Creates new objects by copying an existing object.</summary>

A pattern used when the cost of creating a new object from scratch is expensive or complex. Instead of performing a full initialization, the system takes an existing "prototype" instance and clones it. This is often used in systems with many similar objects that only differ by a few attributes.

- **Examples:**
  - [moodle/moodle](https://github.com/moodle/moodle): Implements prototype cloning when duplicating courses or activity templates, allowing a teacher to create a new course based on a complex existing structure without re-executing all setup logic.
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Uses prototype patterns for internal object cloning during repository mirroring, ensuring that new repository metadata objects are created efficiently from existing templates.
- **Resources:**
  - [Prototype Pattern](https://refactoring.guru/design-patterns/prototype): Explanation of deep vs. shallow cloning by Refactoring Guru.
  - [Prototype Design Pattern](https://sourcemaking.com/design_patterns/prototype): A look at the performance benefits of prototype registries by SourceMaking.

</details>

<details>
<summary><strong>Object Pool Pattern:</strong> Maintains a set of initialized, reusable objects to optimize performance.</summary>

A performance optimization pattern used when creating an object is significantly expensive (such as database connections or network sockets). Instead of destroying objects after use, they are returned to a "pool" to be reused by the next requester. This reduces the overhead of frequent allocation and garbage collection.

- **Examples:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Manages highly efficient pools of database connections and worker threads to handle thousands of concurrent chat messages without the latency of repeated object instantiation.
  - [discourse/discourse](https://github.com/discourse/discourse): Uses internal pools for its background processing tasks and database connections, ensuring that the high-traffic forum application maintains stable resource usage.
- **Resources:**
  - [Object Pool Pattern](https://sourcemaking.com/design_patterns/object_pool): Theory and implementation of resource management via pooling by SourceMaking.
  - [Object Pool](https://en.wikipedia.org/wiki/Object_pool_pattern): A comprehensive overview of lifecycle management and pool sizing on Wikipedia.

</details>

</details>

<details>
<summary><h3>Structural Patterns</h3></summary>

<br>

*Patterns that deal with how classes and objects are composed to form larger structures*

<details>
<summary><strong>Adapter:</strong> Allows incompatible interfaces to work together by wrapping an otherwise incompatible object in an adapter.</summary>

A pattern that acts as a translator between two different interfaces. It allows a system to consume external libraries or legacy components without forcing the core application code to change its internal expectations. This is essential for maintaining a clean domain model while interacting with third-party APIs.

- **Examples:**
  - [home-assistant/core](https://github.com/home-assistant/core): Uses adapters to make thousands of distinct smart home hardware protocols conform to a standardized internal entity model for lights, switches, and sensors.
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Relies on storage adapters to translate generic file attachment commands into the specific API requests required by various cloud providers like AWS S3, Google Cloud Storage, or OpenStack Swift.
- **Resources:**
  - [Adapter Pattern](https://refactoring.guru/design-patterns/adapter): A technical overview of class and object adapters by Refactoring Guru.
  - [Adapter Design Pattern](https://sourcemaking.com/design_patterns/adapter): A guide to the implementation and intent of the pattern by SourceMaking.

</details>

<details>
<summary><strong>Bridge:</strong> Decouples an abstraction from its implementation so the two can vary independently.</summary>

A pattern designed to avoid a massive hierarchy of classes when a component has multiple independent dimensions of variation. Instead of creating a subclass for every combination of features, the Bridge extracts one dimension into a separate object hierarchy, allowing both to be extended without affecting the other.

- **Examples:**
  - [metabase/metabase](https://github.com/metabase/metabase): Separates the abstract representation of a data query from the specific implementations required to execute that query across dozens of different SQL and NoSQL database engines.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Separates the abstract concept of a "File Backend" from the specific implementations required to read and write to local disk, AWS S3, or MinIO. This allows the core messaging logic to handle file attachments independently of the storage technology.
- **Resources:**
  - [Bridge Pattern](https://refactoring.guru/design-patterns/bridge): An explanation of how to split large classes into separate hierarchies by Refactoring Guru.
  - [Bridge Design Pattern](https://sourcemaking.com/design_patterns/bridge): A breakdown of the structural composition of the pattern by SourceMaking.

</details>

<details>
<summary><strong>Composite:</strong> Composes objects into tree structures to represent part-whole hierarchies, letting clients treat individual objects and compositions uniformly.</summary>

A pattern that allows a collection of objects to be treated as if it were a single instance of that object. It is used to build hierarchical structures, such as file systems or UI component trees, where a group of items can respond to the same commands as a single item.

- **Examples:**
  - [moodle/moodle](https://github.com/moodle/moodle): Represents complex course structures, including categories, sub-categories, and individual modules, as a composite tree that can be navigated and rendered uniformly.
  - [standardnotes/app](https://github.com/standardnotes/app): Manages hierarchical note organizations and folder structures where a parent container and an individual note respond uniformly to synchronization and metadata operations.
- **Resources:**
  - [Composite Pattern](https://refactoring.guru/design-patterns/composite): Visual guides on building recursive object structures by Refactoring Guru.
  - [Composite](https://en.wikipedia.org/wiki/Composite_pattern): A comprehensive overview of the pattern's role in tree-based data structures on Wikipedia.

</details>

<details>
<summary><strong>Decorator:</strong> Attaches additional responsibilities to an object dynamically, providing a flexible alternative to subclassing for extending functionality.</summary>

A pattern that allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class. It wraps the original object in a "decorator" class that maintains the original interface while adding new logic before or after the original method calls.

- **Examples:**
  - [discourse/discourse](https://github.com/discourse/discourse): Frequently uses decorators to dynamically add features to core user or post models based on active plugins without modifying the base Ruby classes.
  - [spree/spree](https://github.com/spree/spree): Relies on decorators to allow developers to extend the business logic of core e-commerce entities, such as orders or shipments, without altering the underlying framework code.
- **Resources:**
  - [Decorator Pattern](https://refactoring.guru/design-patterns/decorator): How to attach new behaviors to objects at runtime by Refactoring Guru.
  - [Decorator Design Pattern](https://sourcemaking.com/design_patterns/decorator): An analysis of wrapper-based extension by SourceMaking.

</details>

<details>
<summary><strong>Facade:</strong> Provides a unified, simplified interface to a set of interfaces in a subsystem, making it easier to use.</summary>

A pattern that defines a higher-level interface that makes a subsystem easier to use by hiding its complexity. It provides a single entry point to a complex group of classes, reducing the learning curve for developers and minimizing the dependencies between the subsystem and the rest of the application.

- **Examples:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Implements facade services to wrap complex Git operations and internal RPC calls, providing the web application with a simple API for repository management.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Provides a facade for its notification subsystem, allowing the application to trigger alerts without managing the specific protocols for mobile push, email, and desktop notifications.
- **Resources:**
  - [Facade Pattern](https://refactoring.guru/design-patterns/facade): Shielding clients from complex library dependencies by Refactoring Guru.
  - [Facade](https://en.wikipedia.org/wiki/Facade_pattern): An overview of simplified interface design on Wikipedia.

</details>

<details>
<summary><strong>Flyweight:</strong> Uses sharing to support large numbers of fine-grained objects efficiently, minimizing memory usage.</summary>

A memory-saving pattern that focuses on sharing as much data as possible with similar objects. It extracts "intrinsic" state (data that is the same for all objects) into a shared flyweight object, while "extrinsic" state (unique data) is stored separately, allowing thousands of objects to occupy very little RAM.

- **Examples:**
  - [ornicar/lila](https://github.com/ornicar/lila): Shares immutable chess board configurations and piece representations across millions of active game sessions on Lichess to minimize server memory consumption.
  - [plausible/analytics](https://github.com/plausible/analytics): Uses shared metadata strings for common browser and operating system types across high-volume analytics event streams to reduce redundant data in memory.
- **Resources:**
  - [Flyweight Pattern](https://refactoring.guru/design-patterns/flyweight): Techniques for memory management in high-volume object systems by Refactoring Guru.
  - [Flyweight Design Pattern](https://sourcemaking.com/design_patterns/flyweight): A guide to efficient state sharing by SourceMaking.

</details>

<details>
<summary><strong>Proxy:</strong> Provides a surrogate or placeholder for another object to control access to it.</summary>

A pattern where a proxy object acts as an intermediary for another object. It can be used for lazy initialization to delay expensive object creation, for access control to verify permissions before a call is forwarded, or for logging and caching requests to the original object.

- **Examples:**
  - [tryghost/ghost](https://github.com/tryghost/ghost): Employs proxy objects to intercept database requests, providing a layer for query validation and internal caching before the request reaches the underlying data store.
  - [nextcloud/server](https://github.com/nextcloud/server): Uses proxies to represent files on external storage mounts, only initiating expensive network authentication and connection processes when the file is explicitly accessed.
- **Resources:**
  - [Proxy Pattern](https://refactoring.guru/design-patterns/proxy): Controlling access to original objects via surrogates by Refactoring Guru.
  - [Proxy Design Pattern](https://sourcemaking.com/design_patterns/proxy): Implementation strategies for surrogate and placeholder objects by SourceMaking.

</details>

</details>

<details>
<summary><h3>Behavioral Patterns</h3></summary>

<br>

*Patterns concerned with algorithms and the assignment of responsibilities between objects*

<details>
<summary><strong>Strategy:</strong> Defines a family of algorithms, encapsulates each one, and makes them interchangeable at runtime.</summary>

A pattern used when an application needs to choose between different ways of doing the same thing at runtime. Instead of hard-coding a specific algorithm, the application uses a strategy object. This allows the system to swap, for example, a local storage strategy for a cloud storage strategy without changing the code that uses the storage.

- **Examples:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Uses different delivery strategies for its federation engine, choosing between background push or immediate delivery based on the priority of the post and the network state.
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Employs the strategy pattern to handle multiple authentication methods, allowing users to log in via local password, LDAP, OAuth2, or SSH keys interchangeably.
- **Resources:**
  - [Strategy Pattern](https://refactoring.guru/design-patterns/strategy): Techniques for swapping algorithms at runtime by Refactoring Guru.
  - [Strategy Design Pattern](https://sourcemaking.com/design_patterns/strategy): A guide to encapsulating families of algorithms by SourceMaking.

</details>

<details>
<summary><strong>State:</strong> Allows an object to alter its behavior when its internal state changes, appearing as if it changed its class.</summary>

A pattern that encapsulates state-specific behaviors into separate classes. Instead of a single class containing massive conditional blocks to handle different states, the object delegates the work to a state object. When the state changes, the object swaps its internal state object, completely changing its behavior.

- **Examples:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Manages the complex transitions of Merge Requests (e.g., Draft, Open, Merged, Closed) by using state objects to enforce specific rules and available actions for each status.
  - [spree/spree](https://github.com/spree/spree): Relies on state patterns to manage the checkout lifecycle of an order, ensuring that payment, shipping, and completion steps happen in the correct sequence.
- **Resources:**
  - [State Pattern](https://refactoring.guru/design-patterns/state): How to implement finite state machines as objects by Refactoring Guru.
  - [State Design Pattern](https://sourcemaking.com/design_patterns/state): An analysis of state-driven behavior transitions by SourceMaking.

</details>

<details>
<summary><strong>Observer:</strong> Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.</summary>

A pattern used to create a subscription mechanism. An object (the subject) maintains a list of interested parties (observers). When the subject state changes, it automatically notifies every observer on its list. This is the foundational pattern for reactive user interfaces and event-driven systems.

- **Examples:**
  - [home-assistant/core](https://github.com/home-assistant/core): Built entirely on the observer pattern, where the central event bus notifies various automation components and UI dashboards the moment a physical sensor reports a state change.
  - [discourse/discourse](https://github.com/discourse/discourse): Uses the observer pattern to trigger notifications, emails, and UI updates whenever a new post is created or a user is mentioned in a topic.
- **Resources:**
  - [Observer Pattern](https://refactoring.guru/design-patterns/observer): A guide to implementing subscription-based event notification by Refactoring Guru.
  - [Observer Design Pattern](https://sourcemaking.com/design_patterns/observer): A breakdown of the subject and observer relationship by SourceMaking.

</details>

<details>
<summary><strong>Chain of Responsibility:</strong> Passes a request along a chain of handlers, where each handler decides either to process the request or pass it to the next handler.</summary>

A pattern used to decouple the sender of a request from its receivers. It allows multiple objects a chance to handle the request without the sender needing to know which specific object will eventually process it. This is frequently used for request processing pipelines, middleware, and plugin systems.

- **Examples:**
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Uses a chain of middleware handlers for incoming HTTP requests to manage authentication, logging, and CSRF protection sequentially before reaching the core logic.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Implements a chain of responsibility for its plugin hook system, where various active plugins can intercept and modify messages before they are persisted to the database.
- **Resources:**
  - [Chain of Responsibility](https://refactoring.guru/design-patterns/chain-of-responsibility): A technical overview of handler-based request processing by Refactoring Guru.
  - [Chain of Responsibility Design Pattern](https://sourcemaking.com/design_patterns/chain_of_responsibility): A breakdown of the pattern's intent and structural participants by SourceMaking.

</details>

<details>
<summary><strong>Command:</strong> Encapsulates a request as an object, thereby allowing parameterization of clients with queues, requests, and operations.</summary>

A pattern that turns a specific request or action into a standalone object containing all the information necessary to execute that action. This allows the application to delay execution, store the action in a queue, or keep a history of actions to support undo or redo functionality.

- **Examples:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Encapsulates background tasks as command objects to ensure that heavy operations like repository archiving are queued and executed independently of the main web thread.
  - [zulip/zulip](https://github.com/zulip/zulip): Relies on command objects to process incoming chat messages and events, allowing the system to handle complex message delivery logic in an isolated and testable manner.
- **Resources:**
  - [Command Pattern](https://refactoring.guru/design-patterns/command): A guide to encapsulating actions and supporting undo/redo by Refactoring Guru.
  - [Command Design Pattern](https://sourcemaking.com/design_patterns/command): A technical analysis of the invoker and receiver relationship by SourceMaking.

</details>

<details>
<summary><strong>Iterator:</strong> Provides a way to access the elements of an aggregate object sequentially without exposing its underlying representation.</summary>

A pattern that extracts the traversal logic of a collection into a separate object called an iterator. This allows the client to step through elements of a list, tree, or graph without needing to know if the data is stored in an array, a linked list, or a remote database.

- **Examples:**
  - [moodle/moodle](https://github.com/moodle/moodle): Uses iterators to traverse course items and student records, allowing the core engine to process large datasets without loading the entire collection into memory at once.
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Implements iterators for navigating through Git commit histories and file trees, providing a uniform way to access repository data regardless of the underlying Git backend.
- **Resources:**
  - [Iterator Pattern](https://refactoring.guru/design-patterns/iterator): Visual guides on traversing complex collections by Refactoring Guru.
  - [Iterator Design Pattern](https://sourcemaking.com/design_patterns/iterator): A guide to decoupling collection traversal from collection implementation by SourceMaking.

</details>

<details>
<summary><strong>Mediator:</strong> Defines an object that encapsulates how a set of objects interact, promoting loose coupling by keeping objects from referring to each other explicitly.</summary>

A pattern that centralizes the communication between different components of an application. Instead of objects talking directly to each other, they all talk to a central mediator. The mediator then coordinates the interactions, making it easier to change the communication logic in one place.

- **Examples:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Uses a central mediator to coordinate UI updates between different fragments and activities when the underlying database state changes.
  - [zulip/zulip](https://github.com/zulip/zulip): Employs a mediator pattern to coordinate the delivery of real-time events between the server logic and the various connected web and mobile clients.
- **Resources:**
  - [Mediator Pattern](https://refactoring.guru/design-patterns/mediator): How to reduce chaotic dependencies between classes by Refactoring Guru.
  - [Mediator Design Pattern](https://sourcemaking.com/design_patterns/mediator): An analysis of centralized vs. distributed communication by SourceMaking.

</details>

<details>
<summary><strong>Memento:</strong> Captures and externalizes an object's internal state without violating encapsulation, allowing the object to be restored to this state later.</summary>

A pattern used to implement checkpoints for an object state. It allows an application to save the current state of an object into a memento and restore it later, which is essential for implementing undo/redo features or session recovery without exposing internal details.

- **Examples:**
  - [standardnotes/app](https://github.com/standardnotes/app): Implements memento concepts to snapshot note content and metadata, allowing users to view and restore previous versions of their encrypted notes.
  - [logseq/logseq](https://github.com/logseq/logseq): Uses memento-style state management to handle undo and redo operations for its internal graph structure, ensuring that complex edits can be reversed safely.
- **Resources:**
  - [Memento Pattern](https://refactoring.guru/design-patterns/memento): Techniques for saving and restoring object snapshots by Refactoring Guru.
  - [Memento Design Pattern](https://sourcemaking.com/design_patterns/memento): A guide to capturing internal state for restoration by SourceMaking.

</details>

<details>
<summary><strong>Template Method:</strong> Defines the skeleton of an algorithm in an operation, deferring some steps to subclasses without changing the algorithm's structure.</summary>

A pattern that defines the standard steps of a process in a base class but leaves the implementation of certain steps to child classes. This ensures that the overall workflow is always followed correctly while allowing specific parts of the process to be customized by different modules.

- **Examples:**
  - [moodle/moodle](https://github.com/moodle/moodle): Provides base classes for its various activity modules that define the standard lifecycle for grading and submission, while allowing each module to implement its own specific grading logic.
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Uses template methods in its background worker base classes to ensure that all tasks follow consistent logging, retry, and error-handling procedures while executing their unique business logic.
- **Resources:**
  - [Template Method Pattern](https://refactoring.guru/design-patterns/template-method): How to define algorithmic skeletons with swappable steps by Refactoring Guru.
  - [Template Method Design Pattern](https://sourcemaking.com/design_patterns/template_method): An analysis of the Hollywood Principle (Don't call us, we'll call you) by SourceMaking.

</details>

<details>
<summary><strong>Visitor:</strong> Represents an operation to be performed on the elements of an object structure, letting you define a new operation without changing the classes of the elements on which it operates.</summary>

A pattern used to add new features to an existing object structure without modifying the objects themselves. A visitor object walks through the structure and performs its operation on each element it encounters. This is highly effective for operations like auditing, exporting data, or performing complex validations.

- **Examples:**
  - [home-assistant/core](https://github.com/home-assistant/core): Employs visitors to walk through its registry of device configurations to perform system-wide validations and generate administrative reports without altering the individual device classes.
  - [grafana/grafana](https://github.com/grafana/grafana): Uses the visitor pattern within its dashboard and alert processing components to traverse complex JSON-based configuration trees for validation and data transformation.
- **Resources:**
  - [Visitor Pattern](https://refactoring.guru/design-patterns/visitor): How to add new operations to existing object hierarchies by Refactoring Guru.
  - [Visitor Design Pattern](https://sourcemaking.com/design_patterns/visitor): A breakdown of double-dispatch and structural traversal by SourceMaking.

</details>

<details>
<summary><strong>Interpreter:</strong> Given a language, defines a representation for its grammar along with an interpreter that uses the representation to evaluate sentences in the language.</summary>

A pattern used to define a class hierarchy for representing the grammar of a specific language or expression format. An interpreter then walks through this hierarchy to evaluate the expression. It is commonly used in applications that parse and execute custom queries or mathematical formulas.

- **Examples:**
  - [metabase/metabase](https://github.com/metabase/metabase): Uses an interpreter to translate its internal JSON-based MBQL into the specific SQL dialects required by different database engines.
  - [grafana/grafana](https://github.com/grafana/grafana): Implements interpreter patterns in its frontend and backend to parse and evaluate user-defined alert conditions and data transformation expressions.
- **Resources:**
  - [Interpreter Design Pattern](https://sourcemaking.com/design_patterns/interpreter): An overview of grammar representation and evaluation by SourceMaking.
  - [Interpreter](https://en.wikipedia.org/wiki/Interpreter_pattern): A comprehensive overview of the pattern's role in domain-specific languages on Wikipedia.

</details>

<details>
<summary><strong>Null Object Pattern:</strong> Uses a default, neutral object implementing an expected interface to do nothing, thereby avoiding null reference checks and exceptions throughout the codebase.</summary>

A pattern that replaces null checks with a specialized object that implements the required interface but performs no action. This simplifies client code by allowing it to treat the absence of a dependency as a valid, functional object that simply does nothing when called.

- **Examples:**
  - [discourse/discourse](https://github.com/discourse/discourse): Uses the Null Object pattern to handle cases where settings or user relationships are missing, allowing the UI and business logic to proceed without explicit null checks.
  - [spree/spree](https://github.com/spree/spree): Employs Null Objects for promotional calculators and tax handlers when no specific rules apply to an order, ensuring the checkout flow remains consistent.
- **Resources:**
  - [Null Object Pattern](https://sourcemaking.com/design_patterns/null_object): A guide to simplifying code by eliminating null checks by SourceMaking.
  - [Null Object](https://en.wikipedia.org/wiki/Null_object_pattern): An overview of the pattern's benefits for software robustness on Wikipedia.

</details>

</details>

<details>
<summary><h3>Concurrency Patterns</h3></summary>

<br>

*Patterns that handle multi-threading paradigms and parallel processing*

<details>
<summary><strong>Active Object:</strong> Decouples method execution from method invocation to enhance concurrency and simplify synchronized access to objects that reside in their own threads of control.</summary>

A pattern that allows an object to execute its methods in its own thread rather than the thread of the caller. This transforms synchronous method calls into asynchronous messages stored in a queue, allowing the caller to continue execution immediately while the active object processes the request in the background.

- **Examples:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Implements active object principles in its background job management to ensure that intensive cryptographic operations and database writes do not block the main user interface thread.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Uses active object structures for its asynchronous worker processing, allowing the server to queue and execute complex background tasks without stalling incoming network requests.
- **Resources:**
  - [Active Object](https://en.wikipedia.org/wiki/Active_object): An overview of the pattern components including proxy, scheduler, and servant.
  - [Active Object Design Pattern](https://www.dre.vanderbilt.edu/~schmidt/PDF/Active-Object.pdf) by Douglas C. Schmidt: The original research paper detailing the decoupling of invocation and execution.

</details>

<details>
<summary><strong>Monitor Object:</strong> Synchronizes concurrent method execution to ensure only one method at a time runs within an object, safely encapsulating mutual exclusion.</summary>

A pattern that protects the internal state of an object from concurrent access by multiple threads. It ensures that only one thread at a time can execute a synchronized method on the object, while other threads must wait until the current thread releases the lock.

- **Examples:**
  - [metabase/metabase](https://github.com/metabase/metabase): Uses monitor objects to manage synchronized access to shared database connection pools and global configuration states, preventing race conditions during concurrent user queries.
  - [discourse/discourse](https://github.com/discourse/discourse): Employs monitor and mutex objects within its Ruby environment to synchronize access to shared memory structures and ensure thread-safe execution of background processing logic.
- **Resources:**
  - [Monitor Object Design Pattern](https://www.dre.vanderbilt.edu/~schmidt/PDF/Monitor.pdf) by Douglas C. Schmidt: A guide to encapsulating mutual exclusion within object-oriented software.
  - [Monitor](https://en.wikipedia.org/wiki/Monitor_(synchronization)): A technical breakdown of high-level synchronization primitives.

</details>

<details>
<summary><strong>Half-Sync/Half-Async:</strong> Decouples asynchronous and synchronous service processing in concurrent systems, simplifying programming without degrading performance.</summary>

A pattern used to bridge the gap between low-level asynchronous event handling (for I/O efficiency) and high-level synchronous processing (for simpler programming logic). It uses a queue to pass data from an asynchronous layer to a pool of synchronous worker threads.

- **Examples:**
  - [zulip/zulip](https://github.com/zulip/zulip): Implements this pattern by using an asynchronous event loop to handle incoming socket connections while delegating heavy business logic and database operations to synchronous worker threads.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Relies on half-sync/half-async architectures to manage the transition between high-speed network I/O and the sequential execution of message persistence and notification logic.
- **Resources:**
  - [Half-Sync/Half-Async Design Pattern](https://www.dre.vanderbilt.edu/~schmidt/PDF/HSHA.pdf) by Douglas C. Schmidt: A technical analysis of separating sync and async concerns.
  - [Pattern-Oriented Software Architecture (POSA)](https://en.wikipedia.org/wiki/Pattern-Oriented_Software_Architecture): A summary of the architectural patterns for concurrent and networked objects.

</details>

<details>
<summary><strong>Thread Pool:</strong> Manages a collection of worker threads that efficiently execute asynchronous callbacks on behalf of the application.</summary>

A pattern that avoids the high cost of frequently creating and destroying threads. It maintains a set of pre-initialized threads in a pool. When a task arrives, it is assigned to an available thread; once the task is complete, the thread returns to the pool for reuse.

- **Examples:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Uses thread pools within its Sidekiq background processing engine to manage the concurrent execution of thousands of repository tasks without overwhelming system resources.
  - [metabase/metabase](https://github.com/metabase/metabase): Employs thread pools in its Jetty web server configuration to efficiently handle concurrent HTTP requests and database query execution.
- **Resources:**
  - [Thread Pool Pattern](https://sourcemaking.com/design_patterns/thread_pool): A guide to managing worker thread lifecycles by SourceMaking.
  - [Thread Pool](https://en.wikipedia.org/wiki/Thread_pool): An overview of task queuing and resource management on Wikipedia.

</details>

<details>
<summary><strong>Read-Write Lock:</strong> Allows concurrent read access to an object but requires exclusive access for write operations, optimizing read-heavy workloads.</summary>

A pattern that improves performance in systems where data is read much more often than it is modified. It allows multiple "reader" threads to access data simultaneously, but requires a "writer" thread to wait until all readers are finished before it can gain exclusive access to modify the data.

- **Examples:**
  - [grafana/grafana](https://github.com/grafana/grafana): Uses read-write locks for its internal data source caches and session managers, allowing thousands of simultaneous reads while ensuring consistency during configuration updates.
  - [home-assistant/core](https://github.com/home-assistant/core): Employs read-write locking mechanisms in its state registry to allow multiple components to query the current state of devices concurrently while protecting against corruption during state writes.
- **Resources:**
  - [Read-Write Lock Pattern](https://en.wikipedia.org/wiki/Readers%E2%80%93writer_lock): Technical details on managing concurrent read vs. exclusive write priority.
  - [Read-Write Lock](https://sourcemaking.com/design_patterns/read_write_lock): An analysis of optimizing read-heavy concurrency by SourceMaking.

</details>

<details>
<summary><strong>Double-Checked Locking:</strong> Reduces the overhead of acquiring a lock by first testing the locking criterion without synchronization, only acquiring the lock if the criterion passes.</summary>

A pattern used to optimize lazy initialization in multi-threaded environments. It checks if an object is already initialized without a lock; if not, it enters a synchronized block and checks again before performing the initialization, ensuring that only one thread creates the instance while avoiding lock overhead for subsequent calls.

- **Examples:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Frequently uses double-checked locking for the lazy initialization of its database factory and encrypted preference managers to ensure thread-safe singletons with minimal performance impact.
  - [wordpress-mobile/WordPress-Android](https://github.com/wordpress-mobile/WordPress-Android): Employs double-checked locking patterns to initialize its shared services and configuration handlers only when first accessed, ensuring thread safety without sacrificing startup speed.
- **Resources:**
  - [Double-Checked Locking Pattern](https://sourcemaking.com/design_patterns/double_checked_locking): A guide to optimizing synchronization by SourceMaking.
  - [The Double-Checked Locking is Broken Declaration](http://www.cs.umd.edu/~pugh/java/memoryModel/DoubleCheckedLocking.html): A critical historical analysis of memory model issues with this pattern in early Java versions.

</details>

</details>

<details>
<summary><h3>Functional Patterns</h3></summary>

<br>

*Patterns derived from functional programming paradigms adapted for modern software design*

<details>
<summary><strong>Monad:</strong> A design pattern used to describe computations as a series of steps, handling side effects, state, or I/O in a purely functional way.</summary>

A structural pattern that wraps a value in a context and provides a mechanism to apply functions to that wrapped value. It allows developers to chain complex operations together sequentially while abstracting away boilerplate code for things like null checking, state passing, or asynchronous execution. 

- **Examples:**
  - [lemmynet/lemmy](https://github.com/lemmynet/lemmy): The federated link aggregator is written in Rust, utilizing the language's native `Option` and `Result` types (which are monads) pervasively across its backend to handle absent values and I/O side effects securely.
  - [standardnotes/app](https://github.com/standardnotes/app): Relies heavily on Promises (a monadic structure) in its TypeScript codebase to chain complex, asynchronous cryptographic operations and database writes without deeply nested callbacks.
- **Resources:**
  - [Monad (functional programming)](https://en.wikipedia.org/wiki/Monad_(functional_programming)): A comprehensive overview of monadic structures and their mathematical origins on Wikipedia.
  - [Functors, Applicatives, and Monads in Pictures](https://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html) by Aditya Bhargava: A highly accessible visual guide to understanding functional contexts.

</details>

<details>
<summary><strong>Functor:</strong> A mapping pattern that allows a function to be applied to values wrapped in a context, preserving the structure of that context.</summary>

A pattern representing any type that implements a mapping function. It applies a data transformation to the contents inside a container (like an array, a list, or an option type) and returns a new container of the exact same structure without mutating the original wrapper.

- **Examples:**
  - [plausible/analytics](https://github.com/plausible/analytics): The Elixir-based analytics platform relies extensively on functor-like mapping over collections and streams to process large volumes of web telemetry data efficiently.
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Frequently maps over collections, applying transformation functions to arrays of statuses or user profiles while preserving the underlying data structures for the presentation layer.
- **Resources:**
  - [Functor (functional programming)](https://en.wikipedia.org/wiki/Functor_(functional_programming)): Technical details on mapping over data types on Wikipedia.
  - [Category Theory for Programmers: Functors](https://bartoszmilewski.com/2015/01/20/functors/) by Bartosz Milewski: A deep dive into the theoretical and practical applications of functors.

</details>

<details>
<summary><strong>Immutable Object:</strong> An object whose state cannot be modified after it is created, eliminating unintended side effects and making concurrent programming inherently safe.</summary>

A strict data management pattern. Instead of changing the properties of an existing object, any update creates a completely new copy of the object containing the new values. This guarantees thread safety, prevents race conditions, and provides a predictable, trackable history of application state.

- **Examples:**
  - [zulip/zulip-mobile](https://github.com/zulip/zulip-mobile): Uses Redux to enforce strict immutability for the entire application state tree. Every chat message received results in a new state object being generated rather than mutating the existing data in memory.
  - [ornicar/lila](https://github.com/ornicar/lila): The Lichess server represents chess games, board layouts, and player moves as strictly immutable data structures, allowing thousands of concurrent games to be processed rapidly without complex memory locks.
- **Resources:**
  - [Immutable Object](https://en.wikipedia.org/wiki/Immutable_object): An overview of implementation strategies and performance characteristics on Wikipedia.
  - [ValueObject](https://martinfowler.com/bliki/ValueObject.html) by Martin Fowler: A guide to distinguishing objects based on their properties rather than their identity.

</details>

<details>
<summary><strong>Result Pattern / Railway Oriented Programming:</strong> Encapsulates the result of an operation (success or failure) in a specialized type, allowing sequential composition of operations that might fail without using exceptions.</summary>

A pattern that replaces traditional try-catch exception handling. Functions return a specialized object representing either a success or an error. When chained together, if one function fails, the system switches to the "error track," safely bypassing all subsequent success logic and delivering the error cleanly to the end of the chain.

- **Examples:**
  - [lemmynet/lemmy](https://github.com/lemmynet/lemmy): Completely eschews traditional exception throwing, instead returning Rust's `Result` enum from almost every database query and network request to enforce explicit error handling at compile time.
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Uses Kotlin's native `Result` types to safely wrap and chain complex cryptographic decryption processes that might fail due to bad keys or corrupted network payloads.
- **Resources:**
  - [Railway Oriented Programming](https://fsharpforfunandprofit.com/rop/) by Scott Wlaschin: The definitive guide to error handling in functional languages via the Railway analogy.
  - [Error Handling in Rust](https://doc.rust-lang.org/book/ch09-00-error-handling.html): Official documentation on using the Result enum for robust software design.

</details>

<details>
<summary><strong>Dependency Rejection:</strong> A functional programming alternative to Dependency Injection that pushes all side effects and external dependencies to the outermost edges of the application, keeping the core domain logic completely pure.</summary>

An architectural pattern that separates logic from action. Instead of injecting a database service into a domain model, the pure domain model takes raw data as arguments and returns raw data. The outer imperative shell of the application reads from the database, passes the pure data into the core, and then writes the pure result back to the system.

- **Examples:**
  - [metabase/metabase](https://github.com/metabase/metabase): Isolates its complex query generation and data transformation logic as pure functions in Clojure, completely decoupled from the side-effect-heavy database execution shell.
  - [grafana/grafana](https://github.com/grafana/grafana): Extracts complex dashboard data transformations and alerting rule evaluations into pure functions that simply take inputs and return outputs, pushing the actual network fetching and database writes to the outermost HTTP handlers.
- **Resources:**
  - [Dependency Rejection](https://blog.ploeh.dk/2017/01/27/dependency-rejection/) by Mark Seemann: The foundational article explaining how to replace Dependency Injection with pure functions.
  - [Functional Core, Imperative Shell](https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell) by Gary Bernhardt: A technical exploration of pushing state mutation and I/O to the architectural boundaries.

</details>

</details>

</details>

# Cross-Cutting Architectural Concerns

*Patterns that permeate all layers and boundaries of a system*

## **Security Architecture Patterns**

Patterns and mechanisms maintaining system safety, robust access control, data confidentiality, and overall regulatory compliance across all systemic boundaries.

- **Zero Trust Architecture:** A conceptual architecture that assumes the network is always hostile; it requires strict identity and device verification for every single request, regardless of origin.
- **Role-Based Access Control (RBAC):** Restricts system access based on the predefined roles and permissions of individual users within an organization.
- **Attribute-Based Access Control (ABAC):** Grants access rights through the dynamic evaluation of policies that combine user, resource, and environmental attributes.
- **Mutual TLS (mTLS):** Ensures that traffic is secure and trusted in both directions by requiring both the client and the server to authenticate each other's cryptographic certificates.
- **Identity Federation / Single Sign-On (SSO):** Delegates user authentication to a trusted central identity provider, allowing a user to access multiple independent systems with one set of credentials.

## **Data Architecture Patterns**

Holistic strategies defining the structure, management, and governance of an organization's data assets at rest and in motion.

- **Data Lake:** A centralized, highly scalable repository that stores massive volumes of raw, unstructured, and structured data in its native format.
- **Data Warehouse:** A central repository of highly structured, integrated data filtered from multiple disparate sources, optimized strictly for querying and analytical reporting.
- **Data Mesh:** A decentralized sociotechnical architecture that moves away from central data lakes, instead treating data as a product with decentralized domain teams owning and serving their own data.
- **Data Fabric:** An architecture that provides a unified, automated, and intelligent data integration layer across hybrid and multi-cloud environments.

## **Deployment Architecture Patterns**

Comprehensive strategies and topologies for provisioning, delivering, managing, and scaling physical or cloud-based computational resources.

- **Blue-Green Deployment:** Reduces downtime by running two identical production environments (Blue and Green) and routing traffic entirely from one to the other once a new deployment is verified.
- **Canary Release:** Mitigates risk by slowly rolling out changes to a very small, controlled subset of users before making the update available to the entire user base.
- **Rolling Update:** Incrementally replaces instances of a previous application version with instances of the new version across a cluster to ensure zero downtime.
- **Immutable Server / Infrastructure:** A pattern where servers or containers are never modified in-place after deployment; any change requires building and deploying a completely new instance.
- **Sidecar Pattern:** Deploys supporting infrastructure components (like logging, syncing, or proxies) into a separate, attached container running alongside the primary application container.

## **Observability Architecture Patterns**

Telemetry mechanisms designed to provide deep external visibility into system health, performance, and complex internal states.

- **Distributed Tracing:** Tracks the flow of a single request across multiple distributed microservices by passing a unique, correlated trace ID along the entire call chain.
- **Log Aggregation:** Centralizes and parses localized log files from multiple disparate services and instances into a single, searchable repository (e.g., the ELK stack).
- **Metrics Collection (Time-Series):** Gathers structured, numeric data over time to monitor system health baselines and trigger automated alerts when thresholds are breached.
- **Synthetic Monitoring:** Uses automated scripts to constantly simulate typical user interactions with an application to proactively detect performance drops or availability issues from the outside in.

## **DevOps Architecture Patterns**

Paradigms bridging software development and IT operations through heavy automation, continuous delivery pipelines, and programmatic infrastructure management.

- **GitOps:** A paradigm that uses Git repositories as the single source of truth to automatically manage infrastructure provisioning and software deployments via pull requests.
- **Infrastructure as Code (IaC):** Manages and provisions complete computing environments through version-controlled, machine-readable definition files rather than manual configuration.
- **Continuous Integration / Continuous Deployment (CI/CD):** An automated pipeline pattern that merges developer code, runs automated tests, and securely pushes the finalized build directly to production environments.

## **FinOps Architecture Patterns**

Architectural design and engineering practices strictly optimized for cloud financial management, making variable infrastructure costs highly visible, predictable, and directly correlated to business value.

- **Resource Tagging / Labeling Strategy:** Enforces a strict, consistent metadata schema across all cloud resources to accurately map infrastructure costs to specific teams, environments, or business domains.
- **Showback / Chargeback:** The architectural capability to allocate central IT and cloud operational costs back to the specific business units that consumed them, either for visibility (showback) or internal billing (chargeback).

## **Federated Architecture Patterns**

Decentralized system models enabling multiple autonomous entities or nodes to securely interoperate using shared standards without relying on a single central governing authority.

- **Data Federation:** Provides a unified, real-time query interface across multiple autonomous data stores without requiring the data to be physically moved or duplicated.
- **GraphQL Federation:** An API gateway pattern that seamlessly combines multiple independent GraphQL APIs (subgraphs) into a single, unified schema (supergraph) for the client.

---

## **Enterprise Architecture Frameworks**

*Holistic frameworks for managing the entire enterprise's architecture; these are not software architectures per se but define categories of architecture from a business and IT strategy perspective*

- **Business Architecture:** Defines business strategy, governance, organization, and key business processes.
- **Information Architecture (Data Architecture):** Describes the structure of an organization's logical and physical data assets and data management resources.
- **Application Architecture:** Provides a blueprint for the individual applications to be deployed, their interactions, and their relationships to core business processes.
- **Technology Architecture:** Describes the logical software and hardware capabilities required to support business, data, and application services (e.g., IT infrastructure, middleware, networks).
- **Security Architecture:** Processes and controls to protect the enterprise's information and IT assets.
- **Geospatial Architecture:** Incorporates location-based data and services into the enterprise architecture.
- **Social Architecture:** Models the enterprise's interactions with individuals and communities through social media and other channels.
