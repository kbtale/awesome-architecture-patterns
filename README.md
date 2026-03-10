# **Level 1: System Architecture Patterns (Macro-Level Topology)**

## **Core Application Deployment Topologies**

Broad structural paradigms defining how the primary functional units of an application are packaged, scaled, and deployed over underlying infrastructure.

- **Monolithic Architecture:** A unified model where the entire application is built, packaged, and deployed as a single unit.
- **Modular Monolith Architecture:** A monolith internally structured into modules based on business capabilities, allowing for potential extraction into microservices later.
- **Microservices Architecture:** An application decomposed into small, loosely coupled, independently deployable services, each with its own database.
- **Service-Oriented Architecture (SOA):** Coarse-grained, reusable services provide business functionality via a communications protocol, often mediated by an Enterprise Service Bus (ESB).
- **Serverless Architecture (Function-as-a-Service / FaaS):** Applications are divided into ephemeral, event-triggered functions where the cloud provider dynamically manages the allocation and provisioning of servers.
- **Cell-Based Architecture:** The system is divided into isolated, self-contained "cells" to limit failure blast radius and enable massive scale.

## **Network & Node Distribution Topologies**

High-level models describing how processing tasks, physical resources, and network traffic are partitioned across distinct logical nodes.

- **Client-Server Architecture:** A distributed model partitioning tasks between resource providers (servers) and service requesters (clients).
- **N-Tier Architecture:** A client-server model where presentation, application, and data tiers are physically separated onto different machines.
- **Peer-to-Peer (P2P) Architecture:** A decentralized network where all nodes have equal privilege and share resources directly without a central server.
- **Hub and Spoke Architecture:** A centralized network or messaging topology where a central hub acts as the single point of transit routing traffic and data to distributed nodes (spokes).
- **Edge Computing Architecture:** Processes data near the source (on edge nodes) to reduce latency and bandwidth use.
- **IoT Gateway Architecture:** Uses a local gateway to aggregate, filter, and route data from devices to the cloud.

## **Component Interaction & Layering Topologies**

Structural organizations that define how internal modules, execution tiers, or processing steps are arranged and invoke one another.

- **Layered Architecture:** Organizes code into horizontal tiers (presentation, business logic, data access) where each layer communicates only with the layer directly below it.
- **Microkernel Architecture (Plug-in Architecture):** A minimal core system with fundamental logic, surrounded by independent plug-in modules that provide extensible features.
- **Pipe-and-Filter Architecture:** Processes data streams through independent processing steps (filters) connected by channels (pipes).
- **Main Program and Subroutine Architecture:** The classic procedural decomposition where a main program controls and calls subroutines.
- **Object-Oriented Architecture:** Components are objects that encapsulate data and behavior, communicating through method calls.
- **C2 Style:** A component-and-connector style where components communicate asynchronously via connectors, used for highly decoupled, GUI-based systems.
- **Interpreter Architecture:** A virtual machine that executes instructions in a custom language (e.g., JVM, scripting engines).

## **Data-Centric & Big Data Processing Topologies**

Macro-architectures built specifically to ingest, store, route, and process massive volumes of information across distributed clusters or unified planes.

- **Lambda Architecture:** Designed for big data processing, combining batch processing for comprehensive views and stream processing for real-time views.
- **Kappa Architecture:** A simplification of Lambda, using a single stream processing engine for both real-time and batch data.
- **MapReduce Architecture:** A programming model for processing large datasets in parallel across a distributed cluster.
- **Batch Sequential Architecture:** Programs run independently in a predefined order, passing data as files; used in traditional data processing.
- **Database Systems Architecture:** Centralized data store accessed by multiple, independent computations (classic 3-tier applications).
- **Data Mesh:** A decentralized sociotechnical architecture that treats data as a product, with domain teams owning and serving their data.
- **Data Fabric:** An architecture that provides a unified, intelligent data plane across hybrid and multi-cloud environments.

## **Event, Messaging & Communication Topologies**

Distributed models dictating how disparate services exchange information, react to state changes, and manage request routing dynamically.

- **Event-Driven Architecture (Macro):** A distributed system where components react to state changes (events) broadcast across the network, rather than relying on direct request/response.
- **Process Communication (Communicating Processes) Architecture:** Independent processes communicate through channels like sockets, message queues, or shared memory.
- **Service Mesh Architecture:** A dedicated infrastructure layer for managing service-to-service communications in microservices architectures, typically using a sidecar proxy to handle routing, security, and observability without altering application code.
- **API Gateway / Backends for Frontends (BFF) Architecture:** A single entry point (gateway) or multiple client-specific backends (BFF) that handle routing, composition, and cross-cutting concerns for APIs.

## **Concurrency, State & Transactional Topologies**

Paradigms designed to handle complex state management, high-throughput parallelism, and distributed transactions without traditional locking bottlenecks.

- **Actor Model Architecture:** A conceptual model for concurrent computation where "actors" are the universal primitives, modifying their own state and communicating exclusively through asynchronous message passing (e.g., Erlang, Akka).
- **Space-Based Architecture (Tuple Space):** Uses distributed shared memory to avoid database bottlenecks, scaling horizontally for high-volume, variable traffic.
- **Saga Architecture:** Manages distributed transactions across microservices using a sequence of local transactions with compensating actions.

## **Knowledge, AI & Control Systems Architectures**

Specialized macro-structures designed for autonomous reasoning, inference, pattern recognition, and physical hardware management.

- **Agentic Architecture (Multi-Agent Systems):** An emerging AI-driven topology where autonomous systems (agents) utilize large language models to reason, plan, and execute actions, often collaborating to achieve complex goals.
- **Blackboard Architecture:** Multiple specialized subsystems collaborate on a shared data structure (blackboard), common in AI and pattern recognition.
- **Rule-Based System Architecture:** An inference engine applies a set of rules to a knowledge base to derive conclusions; used in expert systems.
- **Closed-Loop Control Architecture (Process Control):** Manages physical processes through sensors and actuators (thermostat, cruise control, embedded systems).
- **Real-Time Architecture:** Systems where response time is critical and must be guaranteed (e.g., avionics, medical devices).

## **System Migration & Hybrid Topologies**

Transitional or composite architectural models used to bridge distinct computing environments or gracefully phase out legacy monolithic systems.

- **Strangler Fig Architecture:** Incrementally replaces a legacy system by building a new system around it and gradually routing functionality to it.
- **Hybrid Architecture / Multi-Cloud Architecture:** Combines multiple architectural styles or deployment across multiple cloud providers.

## **Information & Resource Linking Topologies**

Architectures fundamentally based on centralizing shared data access or connecting distributed documents via associative references.

- **Hypertext System Architecture:** Documents (nodes) interconnected by links; the foundation of the World Wide Web.
- **Repository Architecture:** Centralized data store accessed by multiple independent components (e.g., database-centric systems).

---

# **Level 2: Enterprise Integration Patterns**

*(Communication and data flow between major components or services)*

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

# **Level 3: Application Architecture Patterns**

*(Internal structure of a single application or service)*

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

# **Level 4: Software Design Patterns (Gang of Four & Modern)**

*(Micro-level solutions for object-oriented design problems)*

## **Creational Patterns**

(Patterns that abstract the instantiation process, making a system independent of how its objects are created, composed, and represented)

- **Singleton:** Ensures a class has only one instance and provides a global point of access to it.
- **Factory Method:** Defines an interface for creating an object but lets subclasses alter the type of objects that will be created.
- **Abstract Factory:** Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
- **Builder:** Separates the construction of a complex object from its representation, allowing the same construction process to create various representations.
- **Prototype:** Creates new objects by copying an existing object, known as the prototype.
- **Object Pool Pattern:** Maintains a set of initialized, reusable objects ready for use to optimize performance in systems where instantiation is expensive.

## **Structural Patterns**

(Patterns that deal with how classes and objects are composed to form larger structures)

- **Adapter:** Allows incompatible interfaces to work together by wrapping an otherwise incompatible object in an adapter.
- **Bridge:** Decouples an abstraction from its implementation so the two can vary independently.
- **Composite:** Composes objects into tree structures to represent part-whole hierarchies, letting clients treat individual objects and compositions uniformly.
- **Decorator:** Attaches additional responsibilities to an object dynamically, providing a flexible alternative to subclassing for extending functionality.
- **Facade:** Provides a unified, simplified interface to a set of interfaces in a subsystem, making it easier to use.
- **Flyweight:** Uses sharing to support large numbers of fine-grained objects efficiently, minimizing memory usage.
- **Proxy:** Provides a surrogate or placeholder for another object to control access to it.

## **Behavioral Patterns**

(Patterns concerned with algorithms and the assignment of responsibilities between objects)

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

(Patterns that handle multi-threading paradigms and parallel processing)

- **Active Object:** Decouples method execution from method invocation to enhance concurrency and simplify synchronized access to objects that reside in their own threads of control.
- **Monitor Object:** Synchronizes concurrent method execution to ensure only one method at a time runs within an object, safely encapsulating mutual exclusion.
- **Half-Sync/Half-Async:** Decouples asynchronous and synchronous service processing in concurrent systems, simplifying programming without degrading performance.
- **Thread Pool:** Manages a collection of worker threads that efficiently execute asynchronous callbacks on behalf of the application.
- **Read-Write Lock:** Allows concurrent read access to an object but requires exclusive access for write operations, optimizing read-heavy workloads.
- **Double-Checked Locking:** Reduces the overhead of acquiring a lock by first testing the locking criterion without synchronization, only acquiring the lock if the criterion passes.

## **Functional Patterns**

(Patterns derived from functional programming paradigms adapted for modern software design)

- **Monad:** A design pattern used to describe computations as a series of steps, handling side effects, state, or I/O in a purely functional way.
- **Functor:** A mapping pattern that allows a function to be applied to values wrapped in a context, preserving the structure of that context.
- **Immutable Object:** An object whose state cannot be modified after it is created, eliminating unintended side effects and making concurrent programming inherently safe.
- **Result Pattern / Railway Oriented Programming:** Encapsulates the result of an operation (success or failure) in a specialized type, allowing sequential composition of operations that might fail without using exceptions.
- **Dependency Rejection:** A functional programming alternative to Dependency Injection that pushes all side effects and external dependencies to the outermost edges of the application, keeping the core domain logic completely pure.

---

# Cross-Cutting Architectural Concerns

(Patterns that permeate all layers and boundaries of a system)

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

*(Holistic frameworks for managing the entire enterprise's architecture; these are not software architectures per se but define categories of architecture from a business and IT strategy perspective)*

- **Business Architecture:** Defines business strategy, governance, organization, and key business processes.
- **Information Architecture (Data Architecture):** Describes the structure of an organization's logical and physical data assets and data management resources.
- **Application Architecture:** Provides a blueprint for the individual applications to be deployed, their interactions, and their relationships to core business processes.
- **Technology Architecture:** Describes the logical software and hardware capabilities required to support business, data, and application services (e.g., IT infrastructure, middleware, networks).
- **Security Architecture:** Processes and controls to protect the enterprise's information and IT assets.
- **Geospatial Architecture:** Incorporates location-based data and services into the enterprise architecture.
- **Social Architecture:** Models the enterprise's interactions with individuals and communities through social media and other channels.
