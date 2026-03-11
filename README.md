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

# **Layer 1: System Architecture Patterns**

## **Core Application Deployment Topologies**

Broad structural paradigms defining how the primary functional units of an application are packaged, scaled, and deployed over underlying infrastructure.

- **Monolithic Architecture:** A unified model where the entire application is built, packaged, and deployed as a single unit.
  Historically, the monolith was simply how software was built before distributed cloud computing became accessible. Every component, from UI rendering to database access, shares the same memory space and deployment pipeline. While heavily criticized during the microservices boom for becoming tangled "big balls of mud," the pattern has seen a massive resurgence (often dubbed the "Majestic Monolith") as companies realize that single-process architectures drastically reduce operational complexity, network latency, and infrastructure costs for all but the largest engineering teams.
  - **Examples:**
    - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): The core GitLab monolithic application built heavily on Ruby on Rails.
    - [discourse/discourse](https://github.com/discourse/discourse): The widely used open-source discussion platform monolith.
    - [mastodon/mastodon](https://github.com/mastodon/mastodon): The primary server application for the decentralized social network.
  - **Resources:**
    - [MonolithFirst](https://martinfowler.com/bliki/MonolithFirst.html) by Martin Fowler: An essay on why starting with a monolith is often the best approach.
    - [The Majestic Monolith](https://m.signalvnoise.com/the-majestic-monolith/) by DHH: An argument for the benefits of monolithic architectures by the creator of Ruby on Rails.

- **Modular Monolith Architecture:** A monolith internally structured into modules based on business capabilities, allowing for potential extraction into microservices later.
  This pattern gained massive traction as a pragmatic reaction to the operational nightmares of distributed microservices. It applies the strict boundary contexts of Domain-Driven Design (DDD) to a single deployment unit. Teams can work independently on their isolated modules, bypassing the management of network failures, eventual consistency, or complex Kubernetes clusters. It became highly popularized by tech giants like Shopify, who proved that with strict static analysis tooling, a monolithic codebase can scale to thousands of developers without degrading into a tightly coupled mess.
  - **Examples:**
    - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): A full TypeScript reference application implementing a modular monolith for an e-commerce domain.
    - [danilofes/modular-monolith-architecture](https://github.com/danilofes/modular-monolith-architecture): A Java/Spring Boot reference application demonstrating a modular monolith for an online store.
    - [kgrzybek/modular-monolith-with-ddd](https://github.com/kgrzybek/modular-monolith-with-ddd): A comprehensive .NET reference application using strict Domain-Driven Design boundaries.
  - **Resources:**
    - [Deconstructing the Monolith](https://shopify.engineering/deconstructing-monolith-designing-software-that-grows) by Shopify Engineering: A detailed case study on Shopify's transition to a modular monolith.
    - "Modular Monoliths" by Simon Brown: Structural guidelines for maintaining clean boundaries in a single deployment unit.

- **Microservices Architecture:** An application decomposed into small, loosely coupled, independently deployable services, each with its own database.
  Emerging in the early 2010s from hyper-growth companies like Netflix and Amazon, microservices became the defining architecture of the cloud-native era. The primary driver was organizational scaling. By breaking the system into isolated services, independent teams could deploy code without coordinating with a central release manager. While it solves organizational bottlenecks, it introduces immense technical complexity regarding distributed data transactions, network reliability, and observability, making it a double-edged sword for smaller engineering organizations.
  - **Examples:**
    - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Google's 11-tier polyglot reference application (Online Boutique) for Kubernetes and gRPC.
    - [dotnet/eShop](https://github.com/dotnet/eShop): Microsoft's official cross-platform .NET reference application for microservices and containers.
    - [microservices-demo/microservices-demo](https://github.com/microservices-demo/microservices-demo): The "Sock Shop" reference application designed to teach polyglot microservice deployments.
  - **Resources:**
    - "Building Microservices: Designing Fine-Grained Systems" by Sam Newman: The foundational book on designing, deploying, and maintaining microservices.
    - [Microservices Resource Guide](https://martinfowler.com/microservices/) by Martin Fowler: A comprehensive collection of articles and definitions.

- **Service-Oriented Architecture (SOA):** Coarse-grained, reusable services provide business functionality via a communications protocol, often mediated by an Enterprise Service Bus (ESB).
  Dominating the enterprise landscape in the early 2000s, SOA was the precursor to microservices. SOA focused on integrating massive, monolithic enterprise applications (like ERPs and CRMs) across a company using standardized protocols (typically SOAP and XML). It heavily relied on "smart pipes": centralized Enterprise Service Buses (ESBs) that handled routing, transformation, and security. Ultimately, SOA's reputation suffered due to the heavy vendor lock-in, bloated middleware, and complex governance required to maintain it, paving the way for the "dumb pipes, smart endpoints" philosophy of modern distributed systems.
  - **Examples:**
    - [apereo/cas](https://github.com/apereo/cas): The Central Authentication Service, a standalone enterprise application providing single sign-on services, acting as a core node in a broader Service-Oriented Architecture.
  - **Resources:**
    - "SOA in Practice: The Art of Distributed System Design" by Nicolai M. Josuttis: A practical guide to implementing SOA in enterprise environments.
    - [Service-Oriented Architecture](https://www.ibm.com/topics/soa) by IBM: An architectural overview and history of SOA patterns.

- **Serverless Architecture (Function-as-a-Service / FaaS):** Applications are divided into ephemeral, event-triggered functions where the cloud provider dynamically manages the allocation and provisioning of servers.
  Popularized by the launch of AWS Lambda in 2014, serverless represents the ultimate shift of operational responsibility to the cloud provider. Developers write isolated functions that execute only in response to specific events (HTTP requests, database triggers, message queues) and scale to zero when idle. While it radically reduces infrastructure management and baseline costs, it introduces new challenges like cold start latency, vendor lock-in, and complex debugging across highly distributed, ephemeral execution environments.
  - **Examples:**
    - [serverless/examples](https://github.com/serverless/examples): A vast collection of real-world examples using the Serverless Framework across AWS, Azure, and GCP.
    - [aws-samples/aws-serverless-workshops](https://github.com/aws-samples/aws-serverless-workshops): AWS's official repository for serverless training, patterns, and reference architectures.
    - [Azure-Samples/functions-quickstart](https://github.com/Azure-Samples/functions-quickstart): Microsoft's official template and sample repository for Azure Functions.
  - **Resources:**
    - [Serverless Architectures](https://martinfowler.com/articles/serverless.html) by Mike Roberts: A deep dive into the traits and benefits of serverless computing.
    - "Serverless Architectures on AWS" by Peter Sbarski: A comprehensive guide to building serverless applications.

- **Cell-Based Architecture:** The system is divided into isolated, self-contained "cells" to limit failure blast radius and enable massive scale.
  Originally pioneered by cloud providers like AWS to manage global infrastructure scale (using Availability Zones and deployment "stamps"), cell-based architecture was formalized as a composable software pattern by organizations like WSO2. The system is divided into functional "cells": independent, deployable units containing their own API gateway, logic, and data. If a cell fails or is overwhelmed by traffic, the blast radius is strictly contained to that specific cell or routing partition, ensuring the broader system remains online. It is the architecture of choice for systems requiring hyper-resilience and massive multi-tenancy.
  - **Examples:**
    - *Note on Examples:* Cell-Based Architecture is a macro-level cloud infrastructure deployment paradigm used by massive organizations to manage global traffic and blast radiuses. Because it relies on orchestrating physical infrastructure zones and routing layers rather than a specific codebase structure, there are no single, deployable open-source application repositories that represent it.
  - **Resources:**
    - [Cell-Based Architecture Reference](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) by Asanka Abeysinghe: The original whitepaper defining the pattern.
    - [Workload Isolation Using Shuffle Sharding](https://aws.amazon.com/builders-library/workload-isolation-using-shuffle-sharding/) by AWS Architecture Blog: Amazon's documentation on limiting blast radius using cell-based concepts.

## **Network & Node Distribution Topologies**

High-level models describing how processing tasks, physical resources, and network traffic are partitioned across distinct logical nodes.

- **Client-Server Architecture:** A distributed model partitioning tasks between resource providers (servers) and service requesters (clients).
  The foundational model of the modern web. In this architecture, centralized resource providers (servers) handle data storage, processing, and business logic, while service requesters (clients) consume those resources. It simplifies data management and security by keeping sensitive operations centralized. As systems scale, the server becomes the primary bottleneck, requiring load balancing and horizontal scaling to maintain performance under heavy client traffic.
  - **Examples:**
    - [owncloud/core](https://github.com/owncloud/core): The core server for the OwnCloud platform, demonstrating a server providing resources to distributed clients.
    - [metabase/metabase](https://github.com/metabase/metabase): An open-source business intelligence server that serves dashboards and data to web clients.
  - **Resources:**
    - [Client-Server Overview](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Client-Server_overview) by MDN Web Docs: A breakdown of how client-server web architectures function.
    - "Client/Server Survival Guide" by Robert Orfali: A textbook on designing distributed client-server systems.

- **N-Tier Architecture:** A client-server model where presentation, application, and data tiers are physically separated onto different machines.
  A physical and logical extension of the client-server model. The system is physically separated into distinct tiers, most commonly presentation, application logic, and data storage. Each tier runs on its own infrastructure and only communicates with the tier immediately adjacent to it. This isolation allows teams to scale the database independently from the web servers and provides an extra layer of security, as the presentation layer cannot directly access the data layer.
  - **Examples:**
    - [nopSolutions/nopCommerce](https://github.com/nopSolutions/nopCommerce): An open-source e-commerce cart structured as a multi-tier ASP.NET application.
    - [spring-projects/spring-petclinic](https://github.com/spring-projects/spring-petclinic): The reference application demonstrating a 3-tier architecture using the Spring framework.
  - **Resources:**
    - [N-tier architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/n-tier) by Microsoft Azure Architecture Center: A guide on structuring and deploying N-tier applications in the cloud.
    - "Patterns of Enterprise Application Architecture" by Martin Fowler: Covers the layering patterns that form the basis of N-tier systems.

- **Peer-to-Peer (P2P) Architecture:** A decentralized network where all nodes have equal privilege and share resources directly without a central server.
  A decentralized network topology where every node (peer) acts simultaneously as both a client and a server. Nodes share resources like bandwidth, storage, or processing power directly with one another, bypassing a centralized authority. It is highly resilient to single points of failure and scales organically, as every new user adds capacity to the network. It requires complex routing algorithms to locate data across distributed nodes.
  - **Examples:**
    - [ipfs/kubo](https://github.com/ipfs/kubo): The reference implementation of the InterPlanetary File System (IPFS), a decentralized P2P storage network.
    - [bitcoin/bitcoin](https://github.com/bitcoin/bitcoin): The reference implementation of the decentralized P2P digital currency network.
    - [webtorrent/webtorrent](https://github.com/webtorrent/webtorrent): A streaming torrent client that brings P2P networking directly to web browsers via WebRTC.
  - **Resources:**
    - [How IPFS Works](https://docs.ipfs.tech/concepts/how-ipfs-works/): Official documentation detailing content addressing and P2P routing mechanisms.
    - "Peer-to-Peer: Harnessing the Power of Disruptive Technologies" by Andy Oram: A book exploring the design and impact of decentralized networks.

- **Hub and Spoke Architecture:** A centralized network or messaging topology where a central hub acts as the single point of transit routing traffic and data to distributed nodes (spokes).
  A centralized routing topology designed to simplify network connections. All nodes (spokes) connect directly to a single central router or message broker (the hub). The hub handles all message routing, filtering, and delivery. It drastically reduces the number of connections required in a large system but makes the hub a critical bottleneck that must be highly available.
  - **Examples:**
    - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): A central collaboration server that acts as a hub, routing messages, webhooks, and integrations between various third-party application spokes.
    - [signalapp/Signal-Server](https://github.com/signalapp/Signal-Server): The server repository for Signal, functioning as a hub that securely routes encrypted messages between mobile client spokes.
  - **Resources:**
    - [Hub-and-spoke network topology](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/hybrid-networking/hub-spoke) by Microsoft Azure: A guide to applying this topology for enterprise cloud networking.
    - [Message Broker Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageBroker.html) by Gregor Hohpe: The architectural theory behind using a central hub for application integration.

- **Edge Computing Architecture:** Processes data near the source (on edge nodes) to reduce latency and bandwidth use.
  A distributed computing paradigm that brings computation and data storage closer to the physical location where it is needed. Processing happens on local edge nodes like routers, base stations, or local servers. It drastically reduces latency, conserves backhaul bandwidth, and enables real-time processing for applications requiring immediate feedback.
  - **Examples:**
    - [home-assistant/core](https://github.com/home-assistant/core): A local home automation platform that processes data entirely on the edge node (a local server) to ensure zero latency and offline functionality.
    - [pi-hole/pi-hole](https://github.com/pi-hole/pi-hole): A network-level application deployed on local edge hardware to process and filter DNS requests before they leave the local network.
  - **Resources:**
    - [What is Edge Computing?](https://www.cloudflare.com/learning/serverless/glossary/what-is-edge-computing/) by Cloudflare: An explanation of edge architectures and their benefits over centralized cloud processing.
    - "Edge Computing: Fundamentals, Advances and Applications" by K. Anitha Kumari: A look at edge computing models.

- **IoT Gateway Architecture:** Uses a local gateway to aggregate, filter, and route data from devices to the cloud.
  A specialized topology for managing arrays of constrained hardware devices. A local gateway device sits physically close to the sensors and actuators, acting as an intermediary between the local device network and the wider internet or cloud. The gateway aggregates raw telemetry, filters out noise, handles local protocol translation, and executes offline control logic when the internet connection drops.
  - **Examples:**
    - [edgexfoundry/edgex-go](https://github.com/edgexfoundry/edgex-go): The core implementation of EdgeX Foundry, an open-source IoT edge gateway framework.
    - [ThingsBoard/thingsboard-gateway](https://github.com/ThingsBoard/thingsboard-gateway): An open-source IoT gateway that integrates devices into the central ThingsBoard platform.
  - **Resources:**
    - [AWS IoT Greengrass Architecture](https://docs.aws.amazon.com/greengrass/v2/developerguide/what-is-iot-greengrass.html): AWS documentation explaining how IoT gateways bring cloud-level processing to local devices.
    - "Building the Internet of Things" by Maciej Kranz: Covers the architecture and deployment of IoT systems, including gateway patterns.

## **Component Interaction & Layering Topologies**

Structural organizations that define how internal modules, execution tiers, or processing steps are arranged and invoke one another.

- **Layered Architecture:** Organizes code into horizontal tiers (presentation, business logic, data access) where each layer communicates only with the layer directly below it.
  The standard for traditional business applications. It enforces a strict separation of concerns by stacking logical tiers. Typically divided into presentation, business logic, and data access layers. Each layer relies exclusively on the layer immediately below it, creating a unidirectional flow of dependencies. It simplifies initial development and testing, though it can lead to "sinkhole anti-patterns" where requests simply pass through layers without any real processing.
  - **Examples:**
    - [spring-projects/spring-petclinic](https://github.com/spring-projects/spring-petclinic): The standard Spring reference application, demonstrating a classic 3-tier layered architecture (Web, Service, Repository).
    - [nopSolutions/nopCommerce](https://github.com/nopSolutions/nopCommerce): An open-source e-commerce platform structured as a layered ASP.NET application.
  - **Resources:**
    - "Software Architecture Patterns" by Mark Richards: The chapter on Layered Architecture provides a breakdown of isolated vs. open layers.
    - [Software Architecture Patterns: Layered Architecture](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch01.html) by O'Reilly Media: An explanation of the Layered Architecture pattern and its constraints.

- **Microkernel Architecture (Plug-in Architecture):** A minimal core system with fundamental logic, surrounded by independent plug-in modules that provide extensible features.
  Designed for extreme extensibility. It relies on a minimal core system that handles fundamental operations and lifecycle management. All extended features, custom logic, and integrations are pushed into independent, isolated plug-in modules. This allows third-party developers to add massive amounts of functionality without modifying the core codebase. It is the dominant architecture for IDEs, web browsers, and task orchestration tools.
  - **Examples:**
    - [microsoft/vscode](https://github.com/microsoft/vscode): A core editor engine extended almost entirely by its massive ecosystem of independent plugins.
    - [eclipse-jdt/eclipse.jdt.core](https://github.com/eclipse-jdt/eclipse.jdt.core): The core Java tooling for Eclipse, built heavily on the OSGi microkernel pattern.
  - **Resources:**
    - "Software Architecture Patterns" by Mark Richards: Detailed breakdown of the Microkernel pattern and its use cases.
    - [Pattern: Microkernel Architecture](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch03.html) by O'Reilly Media: An explanation of core systems versus plug-in components.

- **Pipe-and-Filter Architecture:** Processes data streams through independent processing steps (filters) connected by channels (pipes).
  The classic data processing pipeline. It breaks complex data transformations into a series of independent, single-purpose components called filters. These filters are strung together via communication channels called pipes. Data flows continuously from one filter to the next, with each component modifying or analyzing the stream before passing it along. It is highly prevalent in command-line environments, compiler design, and enterprise integration tools.
  - **Examples:**
    - [FFmpeg/FFmpeg](https://github.com/FFmpeg/FFmpeg): The ultimate example of a pipe-and-filter application, where distinct processing filters (decoders, scalers, encoders) are chained together via channels to process video and audio streams.
    - [elastic/logstash](https://github.com/elastic/logstash): A server-side data processing pipeline that ingests data from multiple sources, transforms it, and sends it to a "stash."
  - **Resources:**
    - [Pipes and Filters pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/pipes-and-filters) by Microsoft Azure: A guide to applying this pattern for cloud-based data processing.
    - "Pattern-Oriented Software Architecture, Volume 1" (POSA): The foundational textbook detailing the Pipe and Filter architectural style.

- **Main Program and Subroutine Architecture:** The classic procedural decomposition where a main program controls and calls subroutines.
  The foundation of structured programming. It relies on a central control module that dictates the execution flow by invoking a hierarchy of specialized subroutines. Data is passed downwards as parameters and results are returned upwards. While largely superseded by object-oriented and component-based paradigms for high-level application design, it remains highly effective and widely used in systems programming, embedded systems, and performance-critical core engines written in languages like C.
  - **Examples:**
    - [curl/curl](https://github.com/curl/curl): A widely used command-line tool and library written in C, relying heavily on a main control flow calling specialized subroutines.
    - [redis/redis](https://github.com/redis/redis): The core Redis database engine, written in C, utilizing procedural architecture for high-performance memory management and network I/O.
  - **Resources:**
    - "Software Architecture: Perspectives on an Emerging Discipline" by Mary Shaw and David Garlan: Discusses classical procedural and language-based architectural styles.
    - [Procedural Programming](https://en.wikipedia.org/wiki/Procedural_programming): Core concepts of breaking down systems into routines and subroutines.

- **Object-Oriented Architecture:** Components are objects that encapsulate data and behavior, communicating through method calls.
  Models the system as a collection of interacting entities. Components are defined as objects that encapsulate both state (data) and behavior (methods). Objects communicate with each other exclusively through defined method calls, enforcing information hiding and clear interfaces. It forms the structural basis of massive enterprise applications built in Java, C#, and C++, emphasizing reusability through patterns like inheritance and polymorphism.
  - **Examples:**
    - [jfree/jfreechart](https://github.com/jfree/jfreechart): A massive, classic Java charting application that serves as a textbook example of deep object-oriented class hierarchies, encapsulation, and polymorphism.
    - [iluwatar/java-design-patterns](https://github.com/iluwatar/java-design-patterns): A repository explicitly dedicated to demonstrating object-oriented design patterns.
  - **Resources:**
    - "Design Patterns: Elements of Reusable Object-Oriented Software" by the Gang of Four: The standard text on object-oriented software design.
    - "Object-Oriented Software Engineering" by Ivar Jacobson: A use-case driven approach to object-oriented architectures.

- **C2 Style:** A component-and-connector style where components communicate asynchronously via connectors, used for highly decoupled, GUI-based systems.
  Finding a mainstream, production-grade open-source application explicitly built and labeled as a "C2 Architecture" is nearly impossible today. C2 (Component-and-Connector) was primarily an academic architectural style developed at UC Irvine in the mid-1990s by Richard N. Taylor and his team. It was created as a research model to figure out how to build highly decoupled, event-driven Graphical User Interfaces (GUIs). Because it was an academic model, the industry absorbed its principles (strict decoupling, asynchronous message passing, event buses) but didn't adopt "C2" as a mainstream marketing term the way they did with "Microservices" or "MVC."
  - **Examples:**
    - [isr-uci-edu/ArchStudio5](https://github.com/isr-uci-edu/ArchStudio5): The official architecture research environment developed by UC Irvine (the creators of C2), built heavily upon C2 principles and xADL to model and run component-and-connector systems.
    - While strict C2 remains primarily an academic model, modern event-driven UI frameworks like [facebook/react](https://github.com/facebook/react) share its conceptual DNA of asynchronous, decoupled component communication through state/props boundaries.
  - **Resources:**
    - [A Component- and Message-Based Architectural Style for GUI Software](https://ics.uci.edu/~taylor/documents/1995-C2-TSE.pdf) by Richard N. Taylor: The original academic paper defining the C2 architectural style.
    - [C2 Architectural Style Overview](https://isr.uci.edu/architecture/c2StyleRules.html) by UC Irvine: The original project page and documentation for the C2 style.

- **Interpreter Architecture:** A virtual machine that executes instructions in a custom language (e.g., JVM, scripting engines).
  Built to execute custom instructions or domain-specific languages. It functions as a virtual machine that reads, parses, and executes code at runtime rather than compiling it down to native machine code beforehand. It provides massive cross-platform portability and enables dynamic language features, functioning as the core engine behind scripting languages like Python, Ruby, and JavaScript.
  - **Examples:**
    - [python/cpython](https://github.com/python/cpython): The reference implementation of the Python programming language, containing the compiler and the execution loop (interpreter).
    - [ruby/ruby](https://github.com/ruby/ruby): The core interpreter for the Ruby programming language.
  - **Resources:**
    - "Crafting Interpreters" by Robert Nystrom: A practical guide to building an interpreter architecture from scratch.
    - "Engineering a Compiler" by Keith Cooper and Linda Torczon: The standard textbook covering the design of parsers, virtual machines, and interpreters.

## **Data-Centric & Big Data Processing Topologies**

Macro-architectures built specifically to ingest, store, route, and process massive volumes of information across distributed clusters or unified planes.

- **Lambda Architecture:** Designed for big data processing, combining batch processing for comprehensive views and stream processing for real-time views.
  An approach to big data processing that provides a robust, fault-tolerant system against hardware failures and human mistakes. It processes massive quantities of data by providing both batch-processing and stream-processing methods simultaneously. The batch layer manages the historical archive and computes accurate views, while the speed layer handles recent data for low-latency queries. The serving layer indexes the output for fast querying.
  - **Examples:**
    - *Note on Examples:* Lambda is a macro-pipeline design pattern used in enterprise big data systems. It is built by wiring together separate infrastructure engines (like Hadoop for batch and Storm for speed). Therefore, there is no single "Lambda Architecture" open-source application repository; it is a deployment strategy used by data engineering teams across varied infrastructure.
  - **Resources:**
    - [How to beat the CAP theorem](http://nathanmarz.com/blog/how-to-beat-the-cap-theorem.html) by Nathan Marz: The original blog post introducing the Lambda Architecture.
    - "Big Data: Principles and best practices of scalable realtime data systems" by Nathan Marz and James Warren: The comprehensive book on building Lambda architectures.

- **Kappa Architecture:** A simplification of Lambda, using a single stream processing engine for both real-time and batch data.
  A data processing architecture designed to simplify the complexities of large-scale data systems. It uses a single technology stack for both real-time and batch processing, treating everything as a continuous stream of events. Historical data is re-processed by replaying the event stream through the same processing engine used for real-time data, maintaining a unified pipeline for all computations.
  - **Examples:**
    - *Note on Examples:* Kappa is an enterprise data pipeline philosophy that treats all data as a continuous stream. It is constructed by deploying and configuring streaming engines (like Kafka and Flink). Since it is a conceptual infrastructure pipeline rather than a single application codebase, there are no standalone application examples available in open-source repositories.
  - **Resources:**
    - [Questioning the Lambda Architecture](https://www.oreilly.com/radar/questioning-the-lambda-architecture/) by Jay Kreps: The original article proposing the Kappa Architecture as an alternative to Lambda.
    - [Kappa Architecture Introduction](https://hazelcast.com/glossary/kappa-architecture/) by Hazelcast: A clear breakdown of the Kappa architecture principles.

- **MapReduce Architecture:** A programming model for processing large datasets in parallel across a distributed cluster.
  A processing technique and program model for distributed computing. The algorithm contains two distinct phases: Map and Reduce. The Map phase takes a set of data and converts it into another set of data, breaking individual elements into tuples (key/value pairs). The Reduce phase takes the output from the map phase as input and combines those data tuples into a condensed set of results.
  - **Examples:**
    - [apache/hadoop](https://github.com/apache/hadoop): The original open-source framework that implemented the MapReduce programming model for distributed storage and processing.
    - [apache/couchdb](https://github.com/apache/couchdb): A document-oriented NoSQL database that uses MapReduce as its primary mechanism for building views and querying data.
  - **Resources:**
    - [MapReduce: Simplified Data Processing on Large Clusters](https://research.google/pubs/pub62/) by Jeffrey Dean and Sanjay Ghemawat: The foundational Google research paper that introduced MapReduce to the world.
    - [Hadoop MapReduce Tutorial](https://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html) by Apache Software Foundation: Official documentation and guides for implementing MapReduce jobs.

- **Batch Sequential Architecture:** Programs run independently in a predefined order, passing data as files; used in traditional data processing.
  A classic data processing pattern where separate, independent programs execute in a strict sequence. Each program runs to completion, reads an input file, processes the data, and writes an output file that becomes the input for the exact next program in the sequence. It is highly effective for scheduled, high-volume data transformations like end-of-day financial reconciliation or payroll processing.
  - **Examples:**
    - *Note on Examples:* Batch Sequential is a traditional enterprise workflow where discrete, standalone scripts execute sequentially, passing files between them. Because it relies on the orchestration of many separate business scripts (like end-of-day payroll or banking reconciliation pipelines), there are no unified, open-source repositories that represent a full Batch Sequential business application.
  - **Resources:**
    - [Batch Processing Documentation](https://docs.spring.io/spring-batch/reference/) by Spring: Comprehensive guidelines on structuring and managing batch sequential jobs.
    - [Enterprise Integration Patterns: Process Manager](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ProcessManager.html) by Gregor Hohpe: Architectural patterns related to routing and sequential processing of large workloads.

- **Database Systems Architecture:** Centralized data store accessed by multiple, independent computations (classic 3-tier applications).
  An architecture where a robust, centralized database management system acts as the core of the application. Multiple separate application instances or services connect to this shared database to read, write, and manipulate data. The database itself handles concurrency, transaction integrity, and data security, acting as the single source of truth for the entire distributed system.
  - **Examples:**
    - [postgres/postgres](https://github.com/postgres/postgres): The core repository for PostgreSQL, representing the gold standard for centralized, relational database systems.
    - [mysql/mysql-server](https://github.com/mysql/mysql-server): The core repository for MySQL, widely used as the centralized data store in traditional web architectures.
  - **Resources:**
    - "Database System Concepts" by Abraham Silberschatz, Henry F. Korth, and S. Sudarshan: The definitive academic textbook detailing the architecture of database management systems.
    - [Architecture of a Database System](https://dsf.berkeley.edu/papers/fntdb07-architecture.pdf) by Joseph M. Hellerstein, Michael Stonebraker, and James Hamilton: An in-depth paper on how relational database engines are constructed.

- **Data Mesh:** A decentralized sociotechnical architecture that treats data as a product, with domain teams owning and serving their data.
  A decentralized approach to data architecture that distributes responsibility directly to the specific business domains that generate the data. Each domain team owns its data pipelines and serves its data as a fully functional "product" to the rest of the organization. A federated governance structure ensures these distinct data products remain interoperable and secure across the broader enterprise.
  - **Examples:**
    - *Note on Examples:* Data Mesh is a decentralized, sociotechnical organizational paradigm, not a software application. It dictates how different domain teams within a massive enterprise govern and share their data. Because it is a corporate restructuring of data ownership heavily reliant on internal governance and disparate tools, there is no open-source application codebase that represents a Data Mesh.
  - **Resources:**
    - [How to Move Beyond a Monolithic Data Lake to a Distributed Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html) by Zhamak Dehghani: The original article introducing the Data Mesh paradigm.
    - "Data Mesh: Delivering Data-Driven Value at Scale" by Zhamak Dehghani: The comprehensive book detailing the implementation and organizational shifts required for a data mesh.

- **Data Fabric:** An architecture that provides a unified data plane across hybrid and multi-cloud environments.
  An architecture that utilizes machine learning and metadata to automatically discover, connect, and secure data across disparate systems and cloud providers. It creates a unified, virtualized data layer, allowing users and applications to access information seamlessly across all physical locations and storage formats.
  - **Examples:**
    - *Note on Examples:* Data Fabric is a conceptual, enterprise-wide integration strategy that uses AI and metadata to stitch together data across multiple private and public clouds. It is achieved by buying or deploying dozens of interconnected governance, cataloging, and virtualization platforms. As a macro-level IT strategy, there are no single open-source applications that embody a Data Fabric.
  - **Resources:**
    - [What is a Data Fabric?](https://www.ibm.com/topics/data-fabric) by IBM: A clear definition and overview of the components that make up a data fabric.
    - [What is a Data Fabric?](https://www.sap.com/insights/what-is-a-data-fabric.html) by SAP: A detailed breakdown of data fabric concepts, core components, and how it unifies data management across environments.

## **Event, Messaging & Communication Topologies**

Distributed models dictating how disparate services exchange information, react to state changes, and manage request routing dynamically.

- **Event-Driven Architecture (Macro):** A distributed system where components react to state changes (events) broadcast across the network, rather than relying on direct request/response.
  A highly decoupled topology built around the production, detection, and consumption of state changes. Services publish events to a central broker or event bus. Subscribed services listen for these events and trigger their own isolated business logic asynchronously. It is essential for building highly responsive, scalable systems where unpredictable spikes in traffic are absorbed by queues to protect downstream databases.
  - **Examples:**
    - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): The reference application for the "Microservices Patterns" book, built entirely on an event-driven architecture using sagas and transactional outboxes.
    - [aws-samples/aws-serverless-airline-booking](https://github.com/aws-samples/aws-serverless-airline-booking): A complete serverless application built on AWS utilizing an event-driven architecture to coordinate distinct booking services via EventBridge.
  - **Resources:**
    - [What is an Event-Driven Architecture?](https://aws.amazon.com/event-driven-architecture/) by AWS: A guide to the components and benefits of event-driven systems.
    - "Designing Event-Driven Systems" by Ben Stopford: A comprehensive book on building event-centric architectures.

- **Process Communication (Communicating Processes) Architecture:** Independent processes communicate through channels like sockets, message queues, or shared memory.
  A foundational concurrency model where an application is divided into isolated, concurrently executing processes that pass messages to one another to coordinate work. By ensuring processes share only explicitly passed messages through strictly defined channels, the system prevents race conditions and complex locking mechanisms. It is the architectural basis for highly concurrent systems like telecom switches, chat servers, and distributed databases.
  - **Examples:**
    - [rabbitmq/rabbitmq-server](https://github.com/rabbitmq/rabbitmq-server): While used as a message broker by others, its internal architecture is a prime example of the Erlang Actor model, utilizing thousands of isolated, communicating processes to handle massive concurrency.
    - [syncthing/syncthing](https://github.com/syncthing/syncthing): A continuous file synchronization program written in Go, architected internally around Communicating Sequential Processes (CSP) using goroutines and channels to pass messages safely between syncing operations.
  - **Resources:**
    - [Communicating Sequential Processes](http://www.usingcsp.com/cspbook.pdf) by C.A.R. Hoare: The foundational computer science paper defining the CSP architectural style.
    - [The Actor Model](https://doc.akka.io/docs/akka/current/typed/guide/actors-intro.html) by Akka: Documentation explaining how concurrent processes communicate via message passing.

- **Service Mesh Architecture:** A dedicated infrastructure layer for managing service-to-service communications in microservices architectures, typically using a sidecar proxy to handle routing, security, and observability without altering application code.
  An operational topology that abstracts the network layer away from the application code. Network capabilities like retry logic, mutual TLS encryption, and distributed tracing are handled by a sidecar proxy deployed alongside every service instance. The interconnected web of these proxies forms the mesh, controlled by a central control plane. It is crucial for maintaining security, observability, and traffic control in massive Kubernetes deployments.
  - **Examples:**
    - [istio/istio/tree/master/samples/bookinfo](https://github.com/istio/istio/tree/master/samples/bookinfo): The official polyglot reference application specifically engineered to demonstrate Service Mesh traffic routing, fault injection, and metrics across different language backends.
    - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Google's 11-tier application (Online Boutique) explicitly architected to be deployed onto a service mesh to handle service-to-service communication.
  - **Resources:**
    - [What is a Service Mesh?](https://www.redhat.com/en/topics/microservices/what-is-a-service-mesh) by Red Hat: A clear breakdown of the data plane, control plane, and sidecar proxy concepts.
    - "Istio up and Running" by Lee Calcote and Zack Butcher: A practical guide to implementing a service mesh architecture.

- **API Gateway / Backends for Frontends (BFF) Architecture:** A single entry point (gateway) or multiple client-specific backends (BFF) that handle routing, composition, and cross-cutting concerns for APIs.
  A structural pattern used to abstract the complexity of backend microservices. An API Gateway acts as a reverse proxy, aggregating multiple microservice calls into a single response, handling authentication, rate limiting, and request routing. The Backends for Frontends (BFF) variant takes this further by creating dedicated, separate gateways tailored specifically for different UI clients (e.g., one API for mobile, a different one for desktop web). This ensures clients receive the exact data they require, formatted perfectly for their specific interface.
  - **Examples:**
    - [dotnet/eShop](https://github.com/dotnet/eShop): Microsoft's reference microservices application which explicitly implements the Backends for Frontends (BFF) pattern, featuring entirely separate gateway routing configurations for its Web UI and Mobile clients.
    - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Features a dedicated `frontend` service acting as the single API Gateway that orchestrates calls to the various backend services (cart, product catalog, currency, etc.) to render the final web views.
  - **Resources:**
    - [Pattern: Backends For Frontends](https://samnewman.io/patterns/architectural/bff/) by Sam Newman: The original definition and deep dive into the BFF architectural pattern.
    - [API Gateway Pattern](https://microservices.io/patterns/apigateway.html) by Chris Richardson: A comprehensive look at the benefits and drawbacks of using a unified API gateway.

## **Concurrency, State & Transactional Topologies**

Paradigms designed to handle complex state management, high-throughput parallelism, and distributed transactions without traditional locking bottlenecks.

- **Actor Model Architecture:** A conceptual model for concurrent computation where "actors" are the universal primitives, modifying their own state and communicating exclusively through asynchronous message passing (e.g., Erlang, Akka).
  A highly concurrent topology where the system is composed of thousands or millions of independent, lightweight entities called "actors." Each actor strictly encapsulates its own private state and thread of execution. Because actors never share memory and only interact by sending asynchronous messages to each other's mailboxes, the system completely eliminates the need for traditional thread locking and mutexes. It is the architecture of choice for massively concurrent, fault-tolerant systems like multiplayer game servers and telecommunication switches. 
  - **Examples:**
    - [ornicar/lila](https://github.com/ornicar/lila): The core backend application for Lichess.org. It is built using Scala and the Akka actor framework to handle millions of concurrent chess matches, player states, and real-time websocket connections without locking bottlenecks.
    - [rabbitmq/rabbitmq-server](https://github.com/rabbitmq/rabbitmq-server): The widely used message broker, built natively in Erlang. Its internal architecture is a textbook implementation of the Actor model, where millions of lightweight actor processes handle queuing, routing, and state management concurrently.
  - **Resources:**
    - [The Actor Model in 10 Minutes](https://www.brianstorti.com/the-actor-model/) by Brian Storti: An accessible breakdown of how actors manage state, concurrency, and message mailboxes.
    - "Reactive Messaging Patterns with the Actor Model" by Vaughn Vernon: A deep dive into building enterprise systems using actor-based concurrency.

- **Space-Based Architecture (Tuple Space):** Uses distributed shared memory to avoid database bottlenecks, scaling horizontally for high-volume, variable traffic.
  An architecture designed to completely eliminate the database as a performance bottleneck. Instead of applications querying a central database over a network, data is partitioned and held in memory across a grid of active processing units. The application logic and the data it operates on are co-located in RAM (the "space"). It scales horizontally by spinning up more processing units, making it highly effective for systems dealing with extreme, unpredictable spikes in traffic, such as high-frequency trading platforms, ticketing systems, and real-time bidding engines. 
  - **Examples:**
    - *Note on Examples:* Space-Based Architecture is an enterprise deployment topology rather than a standalone application design. It is implemented by deploying business logic directly into distributed In-Memory Data Grid (IMDG) middleware. Because it relies heavily on orchestrating these specialized grid engines (like Apache Ignite or Hazelcast) across a cluster, there are no single, deployable open-source business application repositories that fully represent the topology natively.
  - **Resources:**
    - [Space-Based Architecture Pattern](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch04.html) by Mark Richards: The definitive architectural explanation of processing units, virtualized middleware, and data grids.
    - [Tuple Space](https://en.wikipedia.org/wiki/Tuple_space): An overview of the foundational distributed computing concept that evolved into modern space-based architectures.

- **Saga Architecture:** Manages distributed transactions across microservices using a sequence of local transactions with compensating actions.
  A distributed transactional pattern that solves the problem of maintaining data consistency across multiple, independent databases. Because loosely coupled microservices cannot share a single ACID database transaction, a Saga breaks a large business transaction into a series of smaller, local steps. If one downstream step fails, the system executes a series of "compensating transactions" (rollbacks) to undo the preceding steps. It ensures eventual consistency without relying on synchronous, distributed locking protocols like Two-Phase Commit (2PC). 
  - **Examples:**
    - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): The definitive reference application for microservices, specifically engineered to demonstrate Saga choreography and orchestration for a complex "Food to Go" order management system.
    - [berndruecker/trip-booking-saga-java](https://github.com/berndruecker/trip-booking-saga-java): A pure business application demonstrating a travel booking saga (booking a flight, hotel, and car sequentially), highlighting the execution of compensating actions when a remote booking fails.
  - **Resources:**
    - [Pattern: Saga](https://microservices.io/patterns/data/saga.html) by Chris Richardson: The industry-standard definition and breakdown of orchestration versus choreography in Sagas.
    - [Saga distributed transactions](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/saga/saga) by Microsoft Azure: A practical guide on implementing the Saga pattern for cloud-based microservices.

## **Knowledge, AI & Control Systems Architectures**

Specialized macro-structures designed for autonomous reasoning, inference, pattern recognition, and physical hardware management.

- **Agentic Architecture (Multi-Agent Systems):** An emerging AI-driven topology where autonomous systems (agents) utilize large language models to reason, plan, and execute actions, often collaborating to achieve complex goals.
  A dynamic topology heavily relying on Large Language Models (LLMs) as central reasoning engines. Instead of following deterministic, hardcoded paths, the system defines high-level goals and equips "agents" with tools (calculators, web search, API access). These agents autonomously plan their execution steps, reflect on intermediate results, and communicate with other specialized agents to solve complex, open-ended problems. It represents a massive shift from imperative programming to goal-oriented, autonomous orchestration. 
  - **Examples:**
    - [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT): A highly popular open-source application that acts as an autonomous agent, chaining together LLM thoughts to independently achieve user-defined goals.
    - [OpenBMB/ChatDev](https://github.com/OpenBMB/ChatDev): A virtual software company application where multiple distinct AI agents (acting as a CEO, programmer, and reviewer) collaborate autonomously to build software based on a single prompt.
  - **Resources:**
    - [LLM Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/) by Lilian Weng: The definitive technical breakdown of agent planning, memory, and tool use.
    - [AutoGPT Documentation](https://docs.agpt.co/): Practical implementation guides for autonomous agent loops.

- **Blackboard Architecture:** Multiple specialized subsystems collaborate on a shared data structure (blackboard), common in AI and pattern recognition.
  An early AI pattern designed for complex, non-deterministic problems like speech recognition or structural protein modeling. It features a central global memory space (the blackboard) and a collection of independent, specialized knowledge sources (the "experts"). There is no central control flow dictating the sequence of operations. Each expert constantly monitors the blackboard. When an expert sees data it can process, it updates the blackboard with a partial solution, which triggers other experts to contribute until a final solution emerges. 
  - **Examples:**
    - [stanfordnlp/CoreNLP](https://github.com/stanfordnlp/CoreNLP): The core Stanford NLP application utilizes a pipeline heavily inspired by the Blackboard pattern. A shared `Annotation` object (the blackboard) is passed around and modified by independent annotators (experts in Part-of-Speech tagging, Named Entity Recognition, parsing) to build a complete linguistic analysis.
  - **Resources:**
    - [Blackboard System](https://en.wikipedia.org/wiki/Blackboard_system): An overview of the control shell, blackboard, and knowledge sources.
    - "Pattern-Oriented Software Architecture, Volume 1" (POSA): Contains the definitive formalization of the Blackboard pattern.

- **Rule-Based System Architecture:** An inference engine applies a set of rules to a knowledge base to derive conclusions; used in expert systems.
  A foundational pattern of classical symbolic AI, often referred to as an "Expert System." It strictly separates the business logic (the rules) from the execution control (the inference engine). Human domain experts define a massive knowledge base of "IF-THEN" facts and conditions. The inference engine then dynamically evaluates incoming data against these rules, firing applicable rules to deduce new facts or trigger actions. It is highly effective for complex compliance, medical diagnosis, and automated underwriting systems where decision logic must be strictly auditable. 
  - **Examples:**
    - [eslint/eslint](https://github.com/eslint/eslint): A pure rule-based application where a core engine evaluates an Abstract Syntax Tree (AST) against hundreds of independent, pluggable rules to infer code quality and trigger warnings.
    - [Yelp/elastalert](https://github.com/Yelp/elastalert): An application that alerts on anomalies from Elasticsearch by continuously evaluating data against a massive dictionary of user-defined rules.
  - **Resources:**
    - [Rule-Based System](https://en.wikipedia.org/wiki/Rule-based_system): An overview of inference engines and expert systems.
    - "Expert Systems: Principles and Programming" by Joseph C. Giarratano and Gary D. Riley: The classic textbook on designing rule-based architectures.

- **Closed-Loop Control Architecture (Process Control):** Manages physical processes through sensors and actuators (thermostat, cruise control, embedded systems).
  An architecture fundamentally bound to the physical world, operating in a continuous, infinite loop to maintain a desired physical state. It relies on a sensor to read the current state of a system, compares that reading to a desired setpoint to calculate an error value, and immediately sends a corrective command to a physical actuator. The system relies entirely on this continuous feedback loop to adapt to external physical disturbances. It is the dominant software architecture for industrial robotics, autonomous vehicles, and HVAC systems. 
  - **Examples:**
    - [ArduPilot/ardupilot](https://github.com/ArduPilot/ardupilot): The highly popular open-source autopilot software suite, built precisely around high-frequency closed-loop PID controllers to maintain aircraft stability.
    - [commaai/openpilot](https://github.com/commaai/openpilot): An open-source autonomous driving application that uses closed-loop control architectures to continuously adjust a vehicle's steering and acceleration based on real-time camera and radar feedback.
  - **Resources:**
    - [Control Theory](https://en.wikipedia.org/wiki/Control_theory): The foundational mathematics and concepts of feedback loops.
    - "Feedback Control of Dynamic Systems" by Gene F. Franklin: The standard engineering text detailing the design of closed-loop software and hardware.

- **Real-Time Architecture:** Systems where response time is critical and must be guaranteed (e.g., avionics, medical devices).
  An architecture defined by strict deterministic timing constraints rather than pure throughput. In a real-time architecture, calculating the correct answer too late is considered a complete system failure. To guarantee execution within microsecond deadlines, these systems utilize specialized Real-Time Operating Systems (RTOS), avoid unpredictable garbage collection pauses, and strictly partition memory. They are essential for safety-critical hardware like pacemakers, anti-lock braking systems, and orbital satellites. 
  - **Examples:**
    - [PX4/PX4-Autopilot](https://github.com/PX4/PX4-Autopilot): An open-source flight control application that specifically targets real-time operating systems (like NuttX) to guarantee strict deterministic timing for drone motor control.
    - [nasa/cFS](https://github.com/nasa/cFS): The Core Flight System developed by NASA, a real-time software framework and application suite used in actual spaceflight missions where missing a processing deadline can result in mission failure.
  - **Resources:**
    - [Real-Time Computing](https://en.wikipedia.org/wiki/Real-time_computing): An overview of hard, firm, and soft real-time constraints.
    - "Real-Time Systems Design and Analysis" by Phillip A. Laplante: A comprehensive guide on structuring determinism into software architectures.

## **System Migration & Hybrid Topologies**

Transitional or composite architectural models used to bridge distinct computing environments or gracefully phase out legacy monolithic systems.

- **Strangler Fig Architecture:** Incrementally replaces a legacy system by building a new system around it and gradually routing functionality to it.
  A migration pattern used to safely modernize massive, monolithic legacy systems. A routing facade is placed in front of the legacy application. As development teams build new, modernized services, the facade intercepts requests and redirects them to the new services while routing the remaining unmigrated traffic to the legacy system. Over time, the new system grows around the old one, completely replacing its functionality until the legacy system can be safely decommissioned.
  - **Examples:**
    - *Note on Examples:* Strangler Fig is a transient migration strategy applied to existing, usually proprietary, enterprise codebases rather than a standalone architectural end-state. Because it describes the active process of rewriting and routing traffic away from a specific legacy system, there are no open-source application repositories built natively as "Strangler Fig" applications.
  - **Resources:**
    - [StranglerFigApplication](https://martinfowler.com/bliki/StranglerFigApplication.html) by Martin Fowler: The original article coining the term and outlining the migration strategy.
    - [Strangler Fig pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/strangler-fig) by Microsoft Azure: A practical guide to implementing the facade and routing necessary for the migration.

- **Hybrid Architecture / Multi-Cloud Architecture:** Combines multiple architectural styles or deployment across multiple cloud providers.
  A macro-level deployment topology that spans physical on-premises data centers and one or more public cloud environments. It provides organizations with extreme flexibility, allowing them to keep highly sensitive data on local hardware for regulatory compliance while bursting variable workloads into the public cloud to utilize infinite horizontal scaling. It relies heavily on container orchestration platforms to maintain consistent application behavior across completely different physical environments.
  - **Examples:**
    - *Note on Examples:* Hybrid and Multi-Cloud architectures are infrastructure deployment strategies managed by networking and orchestration layers (like Google Anthos, Azure Arc, or Kubernetes Federation). A business application deployed in a hybrid setup is just a standard application (often microservices) mapped across different servers. Therefore, there is no single open-source codebase that embodies "Hybrid Architecture."
  - **Resources:**
    - [What is a Hybrid Cloud?](https://www.redhat.com/en/topics/cloud-computing/what-is-hybrid-cloud) by Red Hat: A clear breakdown of how on-premises and cloud resources are integrated.
    - [Multi-cloud architecture patterns](https://cloud.google.com/architecture/multi-cloud-architecture) by Google Cloud: Industry-standard deployment models for distributing workloads across different providers.

## **Information & Resource Linking Topologies**

Architectures fundamentally based on centralizing shared data access or connecting distributed documents via associative references.

- **Hypertext System Architecture:** Documents (nodes) interconnected by links; the foundation of the World Wide Web.
  A non-linear architectural paradigm where discrete blocks of information (nodes) are connected via associative references (hyperlinks). It completely decouples the storage of information from its structural presentation, allowing users to navigate dynamically based on context rather than a strict hierarchy. This is the foundational architecture of the World Wide Web, modern documentation platforms, and associative note-taking applications.
  - **Examples:**
    - [wikimedia/mediawiki](https://github.com/wikimedia/mediawiki): The core application powering Wikipedia, acting as a massive, dynamic hypertext system where millions of nodes are interconnected via associative links.
    - [logseq/logseq](https://github.com/logseq/logseq): A local-first, non-linear outliner application built entirely on a hypertext architecture, using bidirectional links to connect and traverse thought nodes autonomously.
  - **Resources:**
    - [As We May Think](https://www.theatlantic.com/magazine/archive/1945/07/as-we-may-think/303881/) by Vannevar Bush: The foundational 1945 essay that conceptualized the Memex, the precursor to hypertext architectures.
    - [Information Management: A Proposal](https://www.w3.org/History/1989/proposal.html) by Tim Berners-Lee: The original architectural proposal for the World Wide Web, defining the structural use of nodes and hypertext links.

- **Repository Architecture:** Centralized data store accessed by multiple independent components (e.g., database-centric systems).
  A data-centric topology where a single, central repository holds the shared state of the system, and a collection of independent software components operate on that centralized data. The components interact almost exclusively through the repository rather than communicating directly with one another. It is highly effective for systems dealing with complex, shared data structures where different, decoupled tools need to read, analyze, and modify the same source of truth simultaneously.
  - **Examples:**
    - [git/git](https://github.com/git/git): The core version control application operates natively as a repository architecture. Independent command components (`commit`, `status`, `log`) do not communicate with each other; they all execute their logic by reading and writing to the central `.git` object database.
    - [WordPress/WordPress](https://github.com/WordPress/WordPress): An example of a web-based repository architecture. The central database holds all state, and independent components (the core rendering engine, diverse plugins, and themes) independently interact with this central data store without requiring direct component-to-component messaging.
  - **Resources:**
    - "Software Architecture: Perspectives on an Emerging Discipline" by Mary Shaw and David Garlan: Provides a deep academic breakdown of the shared-data and repository architectural styles.
    - "Software Architecture in Practice" by Len Bass, Paul Clements, and Rick Kazman: Discusses the operational benefits and scalability constraints of centralizing application state within a single repository layer.

---

# **Layer 2: Enterprise Integration Patterns**

*Communication and data flow between major components or services*

## **Message Channel Patterns**

Foundational structures defining the virtual pathways through which applications inject and consume decoupled information.

- **Point-to-Point Channel:** Ensures that only one receiver consumes any given message. Once read, the message is removed from the channel.
- **Publish-Subscribe Channel:** Broadcasts a single event to multiple active subscribers simultaneously.
- **Dead Letter Channel:** A dedicated channel where the messaging system routes messages that cannot be successfully delivered or processed.
- **Guaranteed Delivery:** Utilizes persistent, built-in storage mechanisms to ensure a message is not lost even if the system or network crashes before delivery.

## **Message Routing Patterns**

Mechanisms that determine the specific path a message should take to reach its final destination based on context, rules, or content.

- **Content-Based Router:** Examines a message's content and routes it to a specific destination channel based on that data.
- **Message Filter:** Evaluates a message against specific criteria and drops it from the channel if it does not meet the requirements.
- **Recipient List:** Inspects an incoming message and forwards it to a dynamically determined list of recipients.
- **Splitter:** Breaks a single, composite message into multiple individual messages so they can be processed independently.
- **Aggregator:** Collects and combines multiple related, smaller messages into a single, comprehensive message.
- **Resequencer:** Buffers out-of-sequence messages and publishes them downstream in the correct, original order.
- **Routing Slip:** Attaches a sequence of routing instructions directly to the message payload so it knows where to go next.
- **Throttler:** Restricts the rate at which messages are passed to a receiver to prevent the destination from being overloaded.
- **Load Balancer:** Distributes incoming messages across multiple receiver instances to optimize resource utilization and throughput.

## **Message Transformation Patterns**

Intermediary steps that alter, enrich, or standardize the payload of a message to decouple the sender's data format from the receiver's expectations.

- **Envelope Wrapper:** Wraps existing data inside a compliant, standardized message envelope without altering the original payload.
- **Content Enricher:** Intercepts a message and accesses an external data source to append missing, required information before sending it onward.
- **Content Filter:** Removes unneeded or sensitive data from a message to simplify it or enhance security before delivery.
- **Claim Check:** Stores large, heavy message payloads in a persistent database and passes only a lightweight reference identifier (the claim check) through the messaging bus.
- **Normalizer:** Routes messages of disparate formats through custom translators so they all arrive at their destination in a single, unified format.

## **Messaging Endpoint Patterns**

Architectural interfaces connecting an application's internal code to the external messaging system, dictating how messages are sent and received.

- **Polling Consumer:** Proactively checks for and pulls messages from a channel at specific intervals.
- **Event-Driven Consumer:** Operates on a push model, reacting automatically the moment a message is delivered to it.
- **Competing Consumers:** Uses multiple consumers pulling from a single point-to-point channel to enable concurrent processing and scale out workloads.
- **Message Dispatcher:** A central component that consumes messages from a channel and actively distributes them to various worker threads or endpoints.
- **Selective Consumer:** Applies a filter directly at the consumer level so it ignores messages on the channel that do not match its specific criteria.
- **Durable Subscriber:** Ensures a subscriber receives all messages sent to a topic, safely buffering them even if the subscriber is temporarily disconnected.
- **Idempotent Receiver:** Safely handles duplicate messages by ensuring that processing the same message multiple times yields the exact same state as processing it once.
- **Transactional Client:** Groups multiple message sends and receives into a single atomic transaction that either fully succeeds or entirely rolls back.

## **API Gateway Patterns**

Front-facing aggregation and routing layers managing how external clients interface with internal, distributed microservices.

- **API Gateway:** Provides a single, unified entry point that handles request routing, composition, and security for internal microservices.
- **Backends for Frontends (BFF):** Creates separate, custom-tailored API gateways for different types of clients (e.g., one for mobile, one for web) rather than forcing a one-size-fits-all API.
- **Gateway Aggregation:** Uses the gateway to fan out a single client request to multiple downstream microservices and aggregates their responses into a single payload for the client.
- **Gateway Routing:** Maps external request paths or headers to specific, internal backend services invisibly to the caller.

## **Resilience Patterns**

Defensive engineering tactics designed to protect systems from cascading failures, network unreliability, and resource exhaustion.

- **Circuit Breaker:** Prevents an application from repeatedly trying to execute an operation that is failing, "tripping" to return immediate errors and giving the failing service time to recover.
- **Bulkhead:** Partitions system resources (like connection pools or memory) so that a failure or spike in one component does not cascade and bring down the entire system.
- **Retry with Exponential Backoff:** Automatically retries a transiently failed operation, waiting progressively longer between each attempt to avoid overwhelming a struggling resource.
- **Rate Limiting / Throttling:** Restricts the total number of requests a client can make within a specific timeframe to protect overall service availability.
- **Timeout Management:** Sets strict time limits for operations to complete, proactively aborting them to prevent resources from being tied up indefinitely.
- **Graceful Degradation:** Allows a system to continue functioning with reduced features, older cached data, or lower performance rather than failing completely when a dependency goes down.
- **Health Check Endpoint:** Exposes a dedicated API route that monitoring tools ping to verify the operational status and database connectivity of a service.

## **Saga Patterns**

Strategies for managing long-lived, distributed business transactions across independent services without relying on two-phase commits.

- **Choreographed Saga:** A decentralized transaction model where each local service publishes domain events that trigger local transactions in other services, with no central controller.
- **Orchestrated Saga:** A centralized transaction model where a dedicated coordinator (orchestrator) tells participating services exactly what local transactions or compensating rollbacks to execute.

## **Streaming Patterns**

High-throughput paradigms for handling unbounded, continuous flows of data and database state changes in real-time.

- **Change Data Capture (CDC):** Automatically captures database inserts, updates, and deletes, delivering them as real-time event streams to downstream systems.
- **Event Streaming Platform:** Utilizes a distributed, append-only commit log to durably store and process massive streams of records in real-time.
- **Log-Based CDC:** A specific, highly efficient type of CDC that reads directly from the database's internal transaction log to capture changes without impacting query performance.

## **System Management Patterns**

Administrative and diagnostic tools injected into the messaging architecture to monitor, audit, and debug asynchronous communication flows.

- **Wire Tap:** Silently duplicates messages from a channel and routes them to a secondary channel for inspection or logging without affecting the primary message flow.
- **Message History:** Appends a running list of all components a message has passed through directly to the message header for debugging and tracing.
- **Message Log:** Records the complete, immutable details of every message passing through a system to enable deep auditing and historical replay capabilities.

## **Database & Domain Integration Patterns**

Bridging techniques that safely synchronize strict database transactions with eventual consistency messaging and legacy domain boundaries.

- **Transactional Outbox Pattern:** A crucial pattern for microservices that resolves the dual-write problem by saving state changes and queued events within the same local database transaction before a separate relay process publishes them to a message broker.
- **Anti-Corruption Layer (ACL):** A strategic Domain-Driven Design integration pattern that places a translation layer between different subsystems to prevent a legacy or external system's domain model from polluting a new system's model.

---

# **Layer 3: Application Architecture Patterns**

*Internal structure of a single application or service*

## **Presentation / UI Architecture Patterns**

Patterns that dictate how user interfaces are structured and how they communicate with underlying business logic.

- **Model-View-Controller (MVC):** Separates user interface into Model (data), View (presentation), and Controller (logic).
- **Model-View-Presenter (MVP):** Presenter handles all UI logic, making the View passive.
- **Model-View-ViewModel (MVVM):** Supports two-way data binding between View and ViewModel.
- **Presentation-Abstraction-Control (PAC):** Hierarchical structure for multi-agent interactive systems; each agent has presentation, abstraction, and control components.
- **Flux / Redux Architecture:** Unidirectional data flow (Action -> Dispatcher -> Store -> View) for client-side applications.
- **Micro Frontends Architecture:** Decomposes a web application into independent, feature-based frontend modules.

## **Domain-Centric / Layering Architectures**

Patterns defining the macro-structure of internal layers to isolate the core business domain from infrastructure.

- **Hexagonal Architecture (Ports and Adapters):** Isolates core domain logic from external concerns (UI, database, APIs) via ports and adapters.
- **Clean Architecture:** Concentric rings (Entities, Use Cases, Interface Adapters, Frameworks) enforcing the Dependency Rule.
- **Onion Architecture:** Similar to Clean, with domain model at the core and dependencies inward.

## **Data Source & Object-Relational Patterns**

Patterns managing how in-memory application objects interact with the underlying database or persistence layer.

- **Repository Pattern:** Mediates between domain and data mapping layers, acting like an in-memory collection.
- **Active Record:** An object that wraps a database row, encapsulating both data and behavior.
- **Data Mapper:** Separates in-memory objects from the database, transferring data between them independently.
- **Unit of Work:** Maintains a list of objects affected by a transaction and coordinates writes and concurrency.
- **Lazy Loading:** Delays loading of an object until needed to improve performance.
- **Identity Map:** Ensures each object is loaded only once per transaction by maintaining a map.

## **Domain-Driven Design (DDD) Patterns**

Concepts that help model complex business rules and boundaries.

- **Bounded Context:** A DDD pattern delineating explicit boundaries within which a domain model applies.
- **Aggregate:** A cluster of domain objects treated as a unit for data changes, with a root entity ensuring consistency.
- **Domain Event:** An event that domain experts care about, triggered within the application logic.

## **State Management & Data Flow Patterns**

Patterns defining how application state is mutated, stored, and propagated.

- **CQRS (Command Query Responsibility Segregation):** Separates data modification (commands) from data retrieval (queries).
- **Event Sourcing:** Stores state as a sequence of events; current state derived by replaying the event log.
- **Materialized View:** Generates and stores pre-calculated read models from complex queries or event streams to dramatically optimize read performance.
- **State Machine (Finite State Machine):** Manages complex entity lifecycles by explicitly defining allowed states and the specific events that trigger transitions between them.
- **Reactive Architecture (Reactive Streams):** Models data as asynchronous, observable streams, allowing application components to react to data changes dynamically and non-blockingly.

## **Concurrency & Performance Patterns**

Patterns focused on high-throughput and low-latency execution.

- **LMAX Disruptor Pattern:** A high-performance inter-thread communication architecture utilizing a mechanical sympathy approach and a ring buffer to achieve ultra-low latency without traditional locks.
- **Software Transactional Memory (STM):** Provides a concurrency control mechanism analogous to database transactions, isolating shared memory modifications to prevent race conditions without manual lock management.
- **Reactor Pattern:** An event handling pattern that synchronously demultiplexes and dispatches service requests delivered concurrently to an application by one or more clients.
- **Proactor Pattern:** An asynchronous variant of the Reactor pattern where the operating system handles the I/O operations and notifies the application architecture only when the operation is fully complete.

## **System Connectivity Patterns**

Patterns dictating how applications handle network reliance and synchronization.

- **Offline-First Architecture:** A design paradigm where the application's core functionality is built to operate primarily against a local database, asynchronously syncing with a remote server only when network connectivity is available.
- **Optimistic UI:** Updates the user interface immediately upon user action, assuming the asynchronous network request will succeed, and silently rolling back the local state only if a network failure occurs.
- **Store-and-Forward:** Temporarily saves outbound application data or requests locally when destination systems are unavailable, automatically forwarding them in the background once connectivity is restored.

## **Structural & Wiring Patterns**

Patterns handling the lifecycle and assembly of application components.

- **Dependency Injection:** Externally supplies dependencies to an object, enabling testability and loose coupling.
- **Service Locator:** Utilizes a central registry object that components can query to retrieve their necessary dependencies at runtime, serving as a pull-based alternative to push-based injection.

## **Mobile Architecture Patterns**

Frameworks and structural methodologies specifically designed to manage the unique constraints, lifecycle events, and complex UI routing of native mobile applications.

- **VIPER (View, Interactor, Presenter, Entity, Router):** A strict, modular architecture for iOS applications that isolates business logic, UI manipulation, and routing into separate components to maximize testability.
- **Clean Swift (VIP):** An architecture heavily inspired by Clean Architecture, utilizing a unidirectional data flow cycle specifically between a View, an Interactor, and a Presenter to decoupled iOS application logic.
- **RIBs (Router, Interactor, Builder):** Uber's cross-platform mobile architecture framework that utilizes a tree of business logic components (Interactors) driven by routing state rather than being driven by the view hierarchy.

## **Test Double Patterns**

Specialized structural objects used in automated testing to isolate the code under test by simulating the behavior of real, complex dependencies.

- **Dummy Object:** Objects that are passed around to satisfy API requirements but are never actually used or called within the execution of the test.
- **Stub:** An object that provides canned, hardcoded answers to calls made during a test, usually not responding at all to anything outside what is programmed for the test.
- **Spy:** A stub that internally records information about how it was called, such as keeping track of the number of times a specific method was invoked or the arguments that were passed to it.
- **Mock:** An object pre-programmed with specific expectations that form a specification of the calls it is expected to receive. The test will automatically fail if the mock is not interacted with exactly as expected.
- **Fake:** An object that contains an actual, working implementation but takes a deliberate shortcut making it unsuitable for production (for example, using a fast, local in-memory database instead of a real SQL database).

---

# **Layer 4: Software Design Patterns**

*Micro-level solutions for object-oriented design problems*

## **Creational Patterns**

*Patterns that abstract the instantiation process, making a system independent of how its objects are created, composed, and represented*

- **Singleton:** Ensures a class has only one instance and provides a global point of access to it.
- **Factory Method:** Defines an interface for creating an object but lets subclasses alter the type of objects that will be created.
- **Abstract Factory:** Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
- **Builder:** Separates the construction of a complex object from its representation, allowing the same construction process to create various representations.
- **Prototype:** Creates new objects by copying an existing object, known as the prototype.
- **Object Pool Pattern:** Maintains a set of initialized, reusable objects ready for use to optimize performance in systems where instantiation is expensive.

## **Structural Patterns**

*Patterns that deal with how classes and objects are composed to form larger structures*

- **Adapter:** Allows incompatible interfaces to work together by wrapping an otherwise incompatible object in an adapter.
- **Bridge:** Decouples an abstraction from its implementation so the two can vary independently.
- **Composite:** Composes objects into tree structures to represent part-whole hierarchies, letting clients treat individual objects and compositions uniformly.
- **Decorator:** Attaches additional responsibilities to an object dynamically, providing a flexible alternative to subclassing for extending functionality.
- **Facade:** Provides a unified, simplified interface to a set of interfaces in a subsystem, making it easier to use.
- **Flyweight:** Uses sharing to support large numbers of fine-grained objects efficiently, minimizing memory usage.
- **Proxy:** Provides a surrogate or placeholder for another object to control access to it.

## **Behavioral Patterns**

*Patterns concerned with algorithms and the assignment of responsibilities between objects*

- **Strategy:** Defines a family of algorithms, encapsulates each one, and makes them interchangeable at runtime.
- **State:** Allows an object to alter its behavior when its internal state changes, appearing as if it changed its class.
- **Observer:** Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
- **Chain of Responsibility:** Passes a request along a chain of handlers, where each handler decides either to process the request or pass it to the next handler.
- **Command:** Encapsulates a request as an object, thereby allowing parameterization of clients with queues, requests, and operations.
- **Iterator:** Provides a way to access the elements of an aggregate object sequentially without exposing its underlying representation.
- **Mediator:** Defines an object that encapsulates how a set of objects interact, promoting loose coupling by keeping objects from referring to each other explicitly.
- **Memento:** Captures and externalizes an object's internal state without violating encapsulation, allowing the object to be restored to this state later.
- **Template Method:** Defines the skeleton of an algorithm in an operation, deferring some steps to subclasses without changing the algorithm's structure.
- **Visitor:** Represents an operation to be performed on the elements of an object structure, letting you define a new operation without changing the classes of the elements on which it operates.
- **Interpreter:** Given a language, defines a representation for its grammar along with an interpreter that uses the representation to evaluate sentences in the language.
- **Null Object Pattern:** Uses a default, neutral object implementing an expected interface to do nothing, thereby avoiding null reference checks and exceptions throughout the codebase.

## **Concurrency Patterns**

*Patterns that handle multi-threading paradigms and parallel processing*

- **Active Object:** Decouples method execution from method invocation to enhance concurrency and simplify synchronized access to objects that reside in their own threads of control.
- **Monitor Object:** Synchronizes concurrent method execution to ensure only one method at a time runs within an object, safely encapsulating mutual exclusion.
- **Half-Sync/Half-Async:** Decouples asynchronous and synchronous service processing in concurrent systems, simplifying programming without degrading performance.
- **Thread Pool:** Manages a collection of worker threads that efficiently execute asynchronous callbacks on behalf of the application.
- **Read-Write Lock:** Allows concurrent read access to an object but requires exclusive access for write operations, optimizing read-heavy workloads.
- **Double-Checked Locking:** Reduces the overhead of acquiring a lock by first testing the locking criterion without synchronization, only acquiring the lock if the criterion passes.

## **Functional Patterns**

*Patterns derived from functional programming paradigms adapted for modern software design*

- **Monad:** A design pattern used to describe computations as a series of steps, handling side effects, state, or I/O in a purely functional way.
- **Functor:** A mapping pattern that allows a function to be applied to values wrapped in a context, preserving the structure of that context.
- **Immutable Object:** An object whose state cannot be modified after it is created, eliminating unintended side effects and making concurrent programming inherently safe.
- **Result Pattern / Railway Oriented Programming:** Encapsulates the result of an operation (success or failure) in a specialized type, allowing sequential composition of operations that might fail without using exceptions.
- **Dependency Rejection:** A functional programming alternative to Dependency Injection that pushes all side effects and external dependencies to the outermost edges of the application, keeping the core domain logic completely pure.

---

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
