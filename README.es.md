<div align="center">

<h1>Awesome Architecture Patterns</h1>

[![Awesome](https://img.shields.io/badge/Awesome-lista-green?style=for-the-badge&logo=awesome-lists&logoColor=white)](https://github.com/kbtale/awesome-architecture-patterns)
[![Licencia](https://img.shields.io/badge/Licencia-MIT-blue?style=for-the-badge&logo=open-source-initiative&logoColor=white)](LICENSE)
[![PRs bienvenidos](https://img.shields.io/badge/PRs-Bienvenidos-brightgreen?style=for-the-badge&logo=github&logoColor=white)](CONTRIBUTING.es.md)

<br>

[![English](https://img.shields.io/badge/-English-blue?style=for-the-badge&logoColor=white)](README.md)
[![Español](https://img.shields.io/badge/-Español-red?style=for-the-badge&logoColor=white)](README.es.md)
[![中文](https://img.shields.io/badge/-中文-orange?style=for-the-badge&logoColor=white)](README.zh.md)

</div>

> [!TIP]
> Utiliza el menú del **Índice (Table of Contents)** en la parte superior derecha de este README para navegar rápidamente entre las capas y patrones arquitectónicos.

Una taxonomía multinivel de patrones de diseño y arquitectura de software. Este repositorio intenta categorizar los bloques estructurales de la ingeniería de software, escalando desde topologías de nube a nivel macro hasta interacciones de objetos a nivel micro, cubriendo también preocupaciones transversales y marcos de trabajo empresariales de alto nivel.

Mi objetivo es construir un índice centralizado de recursos, documentación y ejemplos de implementación para cada patrón arquitectónico y variante disponible.

## Referencias

Esta compilación sintetiza y organiza conceptos de varias obras fundamentales de la ingeniería de software y estándares de la industria:
* **Pattern-Oriented Software Architecture (POSA)** por Frank Buschmann, Regine Meunier, Hans Rohnert, Peter Sommerlad y Michael Stal.
* **The C4 Model** para la visualización de arquitectura de software por Simon Brown.
* **Enterprise Integration Patterns** por Gregor Hohpe y Bobby Woolf.
* **Design Patterns: Elements of Reusable Object-Oriented Software (Gang of Four)** por Erich Gamma, Richard Helm, Ralph Johnson y John Vlissides.
* **Domain-Driven Design (DDD)** por Eric Evans.
* **Clean Architecture** por Robert C. Martin.

## Índice

* [Capa 1: Patrones de Arquitectura de Sistemas](#capa-1-patrones-de-arquitectura-de-sistemas)
* [Capa 2: Patrones de Integración Empresarial](#capa-2-patrones-de-integración-empresarial)
* [Capa 3: Patrones de Arquitectura de Aplicaciones](#capa-3-patrones-de-arquitectura-de-aplicaciones)
* [Capa 4: Patrones de Diseño de Software](#capa-4-patrones-de-diseño-de-software)
* [Temas Transversales de Arquitectura](#temas-transversales-de-arquitectura)
* [Marcos de Trabajo de Arquitectura Empresarial](#marcos-de-trabajo-de-arquitectura-empresarial)

## Capa 1: Patrones de Arquitectura de Sistemas

Esta capa trata sobre la estructura de alto nivel y cómo se despliega un sistema. Cubre cómo dividir una aplicación en piezas y distribuirlas a través de una red. Ya sea usando un monolito o microservicios, estos patrones gestionan el escalado, fallos regionales y el procesamiento de datos a gran escala.

### Topologías de Despliegue de Aplicaciones Principales

Paradigmas estructurales amplios que definen cómo se empaquetan, escalan y despliegan las unidades funcionales primarias de una aplicación sobre la infraestructura subyacente.

<details>
<summary><strong>Monolithic Architecture:</strong> Un modelo unificado donde toda la aplicación se construye, empaqueta y despliega como una sola unidad.</summary>

Históricamente, el monolito era simplemente cómo se construía el software antes de que la computación distribuida en la nube fuera accesible. Cada componente, desde el renderizado de la interfaz de usuario hasta el acceso a la base de datos, comparte el mismo espacio de memoria y flujo de despliegue. Aunque fue muy criticado durante el auge de los microservicios por convertirse en "grandes bolas de lodo" enredadas, el patrón ha visto un resurgimiento (a menudo llamado el "Monolito Majestuoso"), ya que las empresas se dan cuenta de que las arquitecturas de un solo proceso reducen drásticamente la complejidad operativa, la latencia de red y los costes de infraestructura para todos excepto los equipos de ingeniería más grandes.

- **Ejemplos:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): La aplicación monolítica principal de GitLab, construida en gran medida sobre Ruby on Rails.
  - [discourse/discourse](https://github.com/discourse/discourse): El monolito de la plataforma de discusión de código abierto ampliamente utilizado.
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): La aplicación de servidor principal para la red social descentralizada.
- **Recursos:**
  - [MonolithFirst](https://martinfowler.com/bliki/MonolithFirst.html) por Martin Fowler: Un ensayo sobre por qué comenzar con un monolito suele ser el mejor enfoque.
  - [The Majestic Monolith](https://m.signalvnoise.com/the-majestic-monolith/) por DHH: Un argumento a favor de los beneficios de las arquitecturas monolíticas por el creador de Ruby on Rails.

</details>

<details>
<summary><strong>Modular Monolith Architecture:</strong> Un monolito estructurado internamente en módulos basados en capacidades de negocio, lo que permite una potencial extracción a microservicios más adelante.</summary>

Este patrón ganó tracción como una reacción pragmática a las pesadillas operativas de los microservicios distribuidos. Aplica los contextos de límites estrictos del Diseño Dirigido por el Dominio (DDD) a una sola unidad de despliegue. Los equipos pueden trabajar de forma independiente en sus módulos aislados, evitando la gestión de fallos de red, la consistencia eventual o los complejos clústeres de Kubernetes. Se popularizó por gigantes tecnológicos como Shopify, quienes demostraron que, con herramientas de análisis estático estrictas, una base de código monolítica puede escalar a miles de desarrolladores sin degradarse en un desorden estrechamente acoplado.

- **Ejemplos:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): Una aplicación de referencia completa en TypeScript que implementa un monolito modular para un dominio de comercio electrónico.
  - [danilofes/modular-monolith-architecture](https://github.com/danilofes/modular-monolith-architecture): Una aplicación de referencia en Java/Spring Boot que demuestra un monolito modular para una tienda en línea.
  - [kgrzybek/modular-monolith-with-ddd](https://github.com/kgrzybek/modular-monolith-with-ddd): Una aplicación de referencia detallada en .NET que utiliza límites estrictos de Diseño Dirigido por el Dominio.
- **Recursos:**
  - [Deconstructing the Monolith](https://shopify.engineering/deconstructing-monolith-designing-software-that-grows) por Shopify Engineering: Un estudio de caso detallado sobre la transición de Shopify a un monolito modular.
  - "Modular Monoliths" por Simon Brown: Directrices estructurales para mantener límites limpios en una sola unidad de despliegue.

</details>

<details>
<summary><strong>Microservices Architecture:</strong> Una aplicación descompuesta en servicios pequeños, poco acoplados y desplegables de forma independiente, cada uno con su propia base de datos.</summary>

Surgidos a principios de la década de 2010 de empresas con un crecimiento exponencial como Netflix y Amazon, los microservicios se convirtieron en la arquitectura definitiva de la era nativa de la nube. El motor principal fue el escalado organizacional. Al dividir el sistema en servicios aislados, los equipos independientes podían desplegar código sin coordinarse con un gestor de lanzamientos central. Aunque resuelve los cuellos de botella organizativos, introduce una inmensa complejidad técnica con respecto a las transacciones de datos distribuidos, la fiabilidad de la red y la observabilidad, lo que lo convierte en un arma de doble filo para las organizaciones de ingeniería más pequeñas.

- **Ejemplos:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): La aplicación de referencia políglota de 11 niveles de Google (Online Boutique) para Kubernetes y gRPC.
  - [dotnet/eShop](https://github.com/dotnet/eShop): La aplicación de referencia oficial multiplataforma de .NET de Microsoft para microservicios y contenedores.
  - [microservices-demo/microservices-demo](https://github.com/microservices-demo/microservices-demo): La aplicación de referencia "Sock Shop" que enseña despliegues de microservicios políglotas.
- **Recursos:**
  - "Building Microservices: Designing Fine-Grained Systems" por Sam Newman: La obra fundamental sobre el diseño, despliegue y mantenimiento de microservicios.
  - [Microservices Resource Guide](https://martinfowler.com/microservices/) por Martin Fowler: Una colección detallada de artículos y definiciones.

</details>

<details>
<summary><strong>Service-Oriented Architecture (SOA):</strong> Servicios de grano grueso y reutilizables proporcionan funcionalidad de negocio a través de un protocolo de comunicación, a menudo mediados por un Bus de Servicios Empresariales (ESB).</summary>

Dominando el panorama empresarial a principios de la década de 2000, SOA fue el precursor de los microservicios. SOA se centró en integrar aplicaciones empresariales monolíticas (como ERPs y CRMs) en toda una empresa utilizando protocolos estandarizados (normalmente SOAP y XML). Dependía en gran medida de "tuberías inteligentes": Buses de Servicios Empresariales (ESB) centralizados que gestionaban el enrutamiento, la transformación y la seguridad. Al final, la reputación de SOA sufrió debido al fuerte bloqueo por parte de los proveedores, el middleware sobrecargado y la compleja gobernanza necesaria para mantenerlo, allanando el camino para la filosofía de "tuberías tontas, puntos finales inteligentes" de los sistemas distribuidos modernos.

- **Ejemplos:**
  - [apereo/cas](https://github.com/apereo/cas): El Servicio de Autenticación Central, una aplicación empresarial independiente que proporciona servicios de inicio de sesión único, actuando como un nodo central en una arquitectura orientada a servicios más amplia.
- **Recursos:**
  - "SOA in Practice: The Art of Distributed System Design" por Nicolai M. Josuttis: Una guía práctica para implementar SOA en entornos empresariales.
  - [Service-Oriented Architecture](https://www.ibm.com/topics/soa) por IBM: Una visión general arquitectónica e historia de los patrones SOA.

</details>

<details>
<summary><strong>Serverless Architecture (Function-as-a-Service / FaaS):</strong> Las aplicaciones se dividen en funciones efímeras activadas por eventos donde el proveedor de la nube gestiona dinámicamente la asignación y el aprovisionamiento de servidores.</summary>

Popularizado por el lanzamiento de AWS Lambda en 2014, el serverless representa el cambio definitivo de la responsabilidad operativa hacia el proveedor de la nube. Los desarrolladores escriben funciones aisladas que se ejecutan solo en respuesta a eventos específicos (solicitudes HTTP, activadores de bases de datos, colas de mensajes) y se escalan a cero cuando están inactivas. Aunque reduce radicalmente la gestión de infraestructura y los costes base, introduce nuevos retos como la latencia de arranque en frío (cold start), el bloqueo por parte del proveedor y la depuración compleja en entornos de ejecución altamente distribuidos y efímeros.

- **Ejemplos:**
  - [serverless/examples](https://github.com/serverless/examples): Una vasta colección de ejemplos del mundo real utilizando el Serverless Framework en AWS, Azure y GCP.
  - [aws-samples/aws-serverless-workshops](https://github.com/aws-samples/aws-serverless-workshops): Repositorio oficial de AWS para formación, patrones y arquitecturas de referencia serverless.
  - [Azure-Samples/functions-quickstart](https://github.com/Azure-Samples/functions-quickstart): Repositorio oficial de Microsoft de plantillas y ejemplos para Azure Functions.
- **Recursos:**
  - [Serverless Architectures](https://martinfowler.com/articles/serverless.html) por Mike Roberts: Una inmersión profunda en los rasgos y beneficios de la computación serverless.
  - "Serverless Architectures on AWS" por Peter Sbarski: Una guía detallada para construir aplicaciones serverless.

</details>

<details>
<summary><strong>Cell-Based Architecture:</strong> El sistema se divide en "células" aisladas y autónomas para limitar el radio de impacto de fallos y permitir una gran escala.</summary>

Originalmente pionero en proveedores de nube como AWS para gestionar la escala de infraestructura global (utilizando Zonas de Disponibilidad y "sellos" de despliegue), la arquitectura basada en células fue formalizada como un patrón de software componible por organizaciones como WSO2. El sistema se divide en "células" funcionales: unidades independientes y desplegables que contienen su propio gateway de API, lógica y datos. Si una célula falla o se ve saturada por el tráfico, el radio de impacto se limita estrictamente a esa célula específica o partición de enrutamiento, manteniendo el sistema más amplio en línea. Es la arquitectura de elección para sistemas que requieren resiliencia y alta multi-tenencia.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* La arquitectura basada en células es un paradigma de despliegue de infraestructura de nube a nivel macro utilizado por grandes organizaciones para gestionar el tráfico global y los radios de impacto. Debido a que depende de orquestar zonas de infraestructura física y capas de enrutamiento más que de una estructura de código específica, no hay repositorios de aplicaciones de código abierto individuales y desplegables que lo representen. Sin embargo, los siguientes ejemplos ilustran detalles de implementación:
    - [GoogleCloudPlatform/cloud-foundation-fabric](https://github.com/GoogleCloudPlatform/cloud-foundation-fabric/tree/master/blueprints/networking/cell-based-architecture): Un modelo de referencia para implementar redes basadas en células en GCP.
- **Recursos:**
  - [Cell-Based Architecture Reference](https://github.com/wso2/reference-architecture/blob/master/reference-architecture-cell-based.md) por Asanka Abeysinghe: El libro blanco original que define el patrón.
  - [Workload Isolation Using Shuffle Sharding](https://aws.amazon.com/builders-library/workload-isolation-using-shuffle-sharding/) por el Blog de Arquitectura de AWS: Documentación de Amazon sobre la limitación del radio de impacto utilizando conceptos basados en células.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

### Topologías de Red y Distribución de Nodos

Modelos de alto nivel que describen cómo se reparten las tareas de procesamiento, los recursos físicos y el tráfico de red en distintos nodos lógicos.

<details>
<summary><strong>Client-Server Architecture:</strong> Un modelo distribuido que reparte las tareas entre los proveedores de recursos (servidores) y los solicitantes de servicios (clientes).</summary>

El modelo central de la web moderna. En esta arquitectura, los proveedores de recursos centralizados (servidores) gestionan el almacenamiento de datos, el procesamiento y la lógica de negocio, mientras que los solicitantes de servicios (clientes) consumen esos recursos. Simplifica la gestión de datos y la seguridad al mantener las operaciones sensibles centralizadas. A medida que los sistemas escalan, el servidor se convierte en el principal cuello de botella, lo que requiere equilibrio de carga y escalado horizontal para mantener el rendimiento bajo un tráfico de clientes denso.

- **Ejemplos:**
  - [owncloud/core](https://github.com/owncloud/core): El servidor principal para la plataforma OwnCloud, demostrando un servidor que proporciona recursos a clientes distribuidos.
  - [metabase/metabase](https://github.com/metabase/metabase): Un servidor de inteligencia de negocio de código abierto que sirve cuadros de mando y datos a clientes web.
- **Recursos:**
  - [Client-Server Overview](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Client-Server_overview) por MDN Web Docs: Un desglose de cómo funcionan las arquitecturas web cliente-servidor.
  - "Client/Server Survival Guide" por Robert Orfali: Un libro de texto sobre el diseño de sistemas cliente-servidor distribuidos.

</details>

<details>
<summary><strong>N-Tier Architecture:</strong> Un modelo cliente-servidor donde los niveles de presentación, aplicación y datos están físicamente separados en máquinas diferentes.</summary>

Una extensión física y lógica del modelo cliente-servidor. El sistema se separa físicamente en distintos niveles, más comúnmente presentación, lógica de aplicación y almacenamiento de datos. Cada nivel se ejecuta en su propia infraestructura y solo se comunica con el nivel inmediatamente adyacente a él. Este aislamiento permite a los equipos escalar la base de datos de forma independiente de los servidores web y añade una capa extra de seguridad, ya que la capa de presentación no puede acceder directamente a la capa de datos.

- **Ejemplos:**
  - [nopSolutions/nopCommerce](https://github.com/nopSolutions/nopCommerce): Un carrito de comercio electrónico de código abierto estructurado como una aplicación ASP.NET multinivel.
  - [spring-projects/spring-petclinic](https://github.com/spring-projects/spring-petclinic): La aplicación de referencia que demuestra una arquitectura de 3 niveles utilizando el framework Spring.
- **Recursos:**
  - [N-tier architecture style](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/n-tier) por Microsoft Azure Architecture Center: Una guía sobre la estructuración y el despliegue de aplicaciones de N niveles en la nube.
  - "Patterns of Enterprise Application Architecture" por Martin Fowler: Cubre los patrones de niveles que forman la base de los sistemas de N niveles.

</details>

<details>
<summary><strong>Peer-to-Peer (P2P) Architecture:</strong> Una red descentralizada donde todos los nodos tienen los mismos privilegios y comparten recursos directamente sin un servidor central.</summary>

Una topología de red descentralizada donde cada nodo (par o "peer") actúa simultáneamente como cliente y como servidor. Los nodos comparten recursos como ancho de banda, almacenamiento o potencia de procesamiento directamente entre sí, evitando una autoridad centralizada. Es muy resistente a los puntos únicos de fallo y escala orgánicamente, ya que cada nuevo usuario añade capacidad a la red. Requiere algoritmos de enrutamiento complejos para localizar datos en nodos distribuidos.

- **Ejemplos:**
  - [ipfs/kubo](https://github.com/ipfs/kubo): La implementación de referencia del InterPlanetary File System (IPFS), una red de almacenamiento P2P descentralizada.
  - [bitcoin/bitcoin](https://github.com/bitcoin/bitcoin): La implementación de referencia de la red de moneda digital P2P descentralizada.
  - [webtorrent/webtorrent](https://github.com/webtorrent/webtorrent): Un cliente de torrent en streaming que lleva las redes P2P directamente a los navegadores web mediante WebRTC.
- **Recursos:**
  - [How IPFS Works](https://docs.ipfs.tech/concepts/how-ipfs-works/): Documentación oficial que detalla el direccionamiento de contenido y los mecanismos de enrutamiento P2P.
  - "Peer-to-Peer: Harnessing the Power of Disruptive Technologies" por Andy Oram: Un libro que explora el diseño y el impacto de las redes descentralizadas.

</details>

<details>
<summary><strong>Hub and Spoke Architecture:</strong> Una topología de red o mensajería centralizada donde un hub central es el único punto de tránsito que enruta el tráfico y los datos hacia nodos distribuidos (radios o "spokes").</summary>

Una topología de enrutamiento centralizada que simplifica las conexiones de red. Todos los nodos (radios) se conectan directamente a un único router central o broker de mensajes (el hub). El hub gestiona todo el enrutamiento, filtrado y entrega de mensajes. Reduce el número de conexiones necesarias en un sistema grande, pero convierte al hub en un cuello de botella crítico que debe ser altamente disponible.

- **Ejemplos:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Un servidor de colaboración central que actúa como hub, enrutando mensajes, webhooks e integraciones entre varios radios de aplicaciones de terceros.
  - [signalapp/Signal-Server](https://github.com/signalapp/Signal-Server): El repositorio de servidor de Signal, como un hub que enruta de forma segura mensajes cifrados entre los radios de los clientes móviles.
- **Recursos:**
  - [Hub-and-spoke network topology](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/hybrid-networking/hub-spoke) por Microsoft Azure: Una guía para aplicar esta topología en redes de nube empresariales.
  - [Message Broker Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageBroker.html) por Gregor Hohpe: La teoría arquitectónica detrás del uso de un hub central para la integración de aplicaciones.

</details>

<details>
<summary><strong>Edge Computing Architecture:</strong> Procesa los datos cerca de la fuente (en nodos de borde o "edge nodes") para reducir la latencia y el uso del ancho de banda.</summary>

Un paradigma de computación distribuida que acerca la computación y el almacenamiento de datos a la ubicación física donde se necesitan. El procesamiento ocurre en nodos de borde locales como routers, estaciones base o servidores locales. Reduce la latencia, conserva el ancho de banda de retorno y permite el procesamiento en tiempo real para aplicaciones que requieren feedback inmediato.

- **Ejemplos:**
  - [home-assistant/core](https://github.com/home-assistant/core): Una plataforma de automatización del hogar local que procesa datos íntegramente en el nodo de borde (un servidor local) para una latencia cero y funcionalidad fuera de línea.
  - [pi-hole/pi-hole](https://github.com/pi-hole/pi-hole): Una aplicación a nivel de red desplegada en hardware de borde local para procesar y filtrar solicitudes DNS antes de que salgan de la red local.
- **Recursos:**
  - [What is Edge Computing?](https://www.cloudflare.com/learning/serverless/glossary/what-is-edge-computing/) por Cloudflare: Una explicación de las arquitecturas de borde y sus beneficios frente al procesamiento en la nube centralizado.
  - "Edge Computing: Fundamentals, Advances and Applications" por K. Anitha Kumari: Una mirada a los modelos de computación de borde.

</details>

<details>
<summary><strong>IoT Gateway Architecture:</strong> Utiliza un gateway local para agregar, filtrar y enrutar los datos de los dispositivos hacia la nube.</summary>

Una topología especializada para gestionar conjuntos de dispositivos de hardware limitados. Un dispositivo gateway local se sitúa físicamente cerca de los sensores y actuadores, actuando como intermediario entre la red local de dispositivos e internet o la nube. El gateway agrega telemetría bruta, filtra el ruido, gestiona la traducción de protocolos locales y ejecuta lógica de control fuera de línea cuando se cae la conexión a internet.

- **Ejemplos:**
  - [edgexfoundry/edgex-go](https://github.com/edgexfoundry/edgex-go): La implementación principal de EdgeX Foundry, un framework de gateway IoT de borde de código abierto.
  - [ThingsBoard/thingsboard-gateway](https://github.com/ThingsBoard/thingsboard-gateway): Un gateway IoT de código abierto que integra dispositivos en la plataforma central ThingsBoard.
- **Recursos:**
  - [AWS IoT Greengrass Architecture](https://docs.aws.amazon.com/greengrass/v2/developerguide/what-is-iot-greengrass.html): Documentación de AWS que explica cómo los gateways IoT llevan el procesamiento a nivel de nube a los dispositivos locales.
  - "Building the Internet of Things" por Maciej Kranz: Cubre la arquitectura y el despliegue de sistemas IoT, incluidos los patrones de gateway.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

### Topologías de Interacción y Capas de Componentes

Organizaciones estructurales que definen cómo se organizan e invocan entre sí los módulos internos, los niveles de ejecución o los pasos de procesamiento.

<details>
<summary><strong>Layered Architecture:</strong> Organiza el código en niveles horizontales (presentación, lógica de negocio, acceso a datos) donde cada capa se comunica solo con la capa situada directamente debajo de ella.</summary>

El estándar para las aplicaciones de negocio tradicionales. Aplica una separación estricta de preocupaciones mediante el apilamiento de niveles lógicos. Normalmente se divide en capas de presentación, lógica de negocio y acceso a datos. Cada capa depende exclusivamente de la capa inmediatamente inferior, creando un flujo de dependencias unidireccional. Simplifica el desarrollo inicial y las pruebas, aunque puede llevar a "anti-patrones de sumidero" donde las solicitudes simplemente pasan a través de las capas sin ningún procesamiento real.

- **Ejemplos:**
  - [spring-projects/spring-petclinic](https://github.com/spring-projects/spring-petclinic): La aplicación de referencia estandarizada de Spring, que demuestra una arquitectura clásica de capas de 3 niveles (Web, Servicio, Repositorio).
  - [nopSolutions/nopCommerce](https://github.com/nopSolutions/nopCommerce): Una plataforma de comercio electrónico de código abierto estructurada como una aplicación ASP.NET por capas.
- **Recursos:**
  - "Software Architecture Patterns" por Mark Richards: El capítulo sobre Arquitectura por Capas proporciona un desglose de capas aisladas frente a capas abiertas.
  - [Software Architecture Patterns: Layered Architecture](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch01.html) por O'Reilly Media: Una explicación del patrón de Arquitectura por Capas y sus restricciones.

</details>

<details>
<summary><strong>Microkernel Architecture (Plug-in Architecture):</strong> Un sistema central mínimo con lógica fundamental, rodeado por módulos de extensión ("plug-ins") independientes que proporcionan características extensibles.</summary>

Construido para la extensibilidad. Se basa en un sistema central mínimo que gestiona las operaciones fundamentales y el ciclo de vida. Todas las funciones extendidas, la lógica personalizada y las integraciones se trasladan a módulos de plug-in aislados e independientes. Esto permite a terceros añadir una gran funcionalidad sin modificar la base de código central. Es la arquitectura dominante para IDEs, navegadores web y herramientas de orquestación de tareas.

- **Ejemplos:**
  - [microsoft/vscode](https://github.com/microsoft/vscode): Un motor de editor central extendido casi en su totalidad por su ecosistema de plug-ins independientes.
  - [eclipse-jdt/eclipse.jdt.core](https://github.com/eclipse-jdt/eclipse.jdt.core): Las herramientas centrales de Java para Eclipse, construidas en gran medida sobre el patrón de microkernel OSGi.
- **Recursos:**
  - "Software Architecture Patterns" por Mark Richards: Desglose detallado del patrón Microkernel y sus casos de uso.
  - [Pattern: Microkernel Architecture](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch03.html) por O'Reilly Media: Una explicación de los sistemas centrales frente a los componentes de plug-in.

</details>

<details>
<summary><strong>Pipe-and-Filter Architecture:</strong> Procesa flujos de datos a través de pasos de procesamiento independientes (filtros) conectados por canales (tuberías o "pipes").</summary>

El flujo de procesamiento de datos clásico. Divide las transformaciones de datos complejas en una serie de componentes independientes de un solo propósito llamados filtros. Estos filtros se encadenan mediante canales de comunicación llamados tuberías. Los datos fluyen continuamente de un filtro al siguiente, y cada componente modifica o analiza el flujo antes de pasarlo. Es muy común en entornos de línea de comandos, diseño de compiladores y herramientas de integración empresarial.

- **Ejemplos:**
  - [FFmpeg/FFmpeg](https://github.com/FFmpeg/FFmpeg): El ejemplo definitivo de una aplicación de tuberías y filtros, donde distintos filtros de procesamiento (decodificadores, escaladores, codificadores) se encadenan mediante canales para procesar flujos de vídeo y audio.
  - [elastic/logstash](https://github.com/elastic/logstash): Un flujo de procesamiento de datos en el lado del servidor que ingiere datos de múltiples fuentes, los transforma y los envía a un "stash".
- **Recursos:**
  - [Pipes and Filters pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/pipes-and-filters) por Microsoft Azure: Una guía para aplicar este patrón en el procesamiento de datos basado en la nube.
  - "Pattern-Oriented Software Architecture, Volume 1" (POSA): El libro de texto principal que detalla el estilo arquitectónico de Tuberías y Filtros.

</details>

<details>
<summary><strong>Main Program and Subroutine Architecture:</strong> La descomposición procedimental clásica en la que un programa principal controla y llama a subrutinas.</summary>

El núcleo de la programación estructurada. Se basa en un módulo de control central que dicta el flujo de ejecución invocando una jerarquía de subrutinas especializadas. Los datos se pasan hacia abajo como parámetros y los resultados se devuelven hacia arriba. Aunque ha sido superado en gran medida por los paradigmas orientados a objetos y basados en componentes para el diseño de aplicaciones de alto nivel, sigue siendo muy eficaz y se utiliza ampliamente en la programación de sistemas, sistemas embebidos y motores de alto rendimiento escritos en lenguajes como C.

- **Ejemplos:**
  - [curl/curl](https://github.com/curl/curl): Una herramienta de línea de comandos y biblioteca ampliamente utilizada escrita en C, que se apoya fuertemente en un flujo de control principal que llama a subrutinas especializadas.
  - [redis/redis](https://github.com/redis/redis): El motor de base de datos central de Redis, escrito en C, que utiliza una arquitectura procedimental para la gestión de memoria de alto rendimiento y E/S de red.
- **Recursos:**
  - "Software Architecture: Perspectives on an Emerging Discipline" por Mary Shaw y David Garlan: Analiza los estilos clásicos procedimentales y basados en el lenguaje.
  - [Procedural Programming](https://en.wikipedia.org/wiki/Procedural_programming): Conceptos básicos de la división de sistemas en rutinas y subrutinas.

</details>

<details>
<summary><strong>Object-Oriented Architecture:</strong> Los componentes son objetos que encapsulan datos y comportamiento, comunicándose a través de llamadas a métodos.</summary>

Modela el sistema como una colección de entidades que interactúan. Los componentes se definen como objetos que encapsulan tanto el estado (datos) como el comportamiento (métodos). Los objetos se comunican entre sí exclusivamente a través de llamadas a métodos definidas, forzando la ocultación de información e interfaces claras. Forma la base estructural de las aplicaciones empresariales construidas en Java, C# y C++, enfatizando la reutilización mediante patrones como la herencia y el polimorfismo.

- **Ejemplos:**
  - [jfree/jfreechart](https://github.com/jfree/jfreechart): Una aplicación de gráficos Java clásica de gran tamaño que sirve como ejemplo de libro de texto de jerarquías de clases orientadas a objetos profundas, encapsulación y polimorfismo.
  - [iluwatar/java-design-patterns](https://github.com/iluwatar/java-design-patterns): Un repositorio dedicado explícitamente a demostrar patrones de diseño orientados a objetos.
- **Recursos:**
  - "Design Patterns: Elements of Reusable Object-Oriented Software" por el Gang of Four (GoF): El texto estándar sobre el diseño de software orientado a objetos.
  - "Object-Oriented Software Engineering" por Ivar Jacobson: Un enfoque de arquitecturas orientadas a objetos impulsado por casos de uso.

</details>

<details>
<summary><strong>C2 Style:</strong> Un estilo de componente y conector en el que los componentes se comunican de forma asíncrona a través de conectores, utilizado en sistemas basados en GUI altamente desacoplados.</summary>

Encontrar una aplicación de código abierto de producción convencional construida y etiquetada explícitamente como "Arquitectura C2" es casi imposible hoy en día. C2 (Component-and-Connector) fue principalmente un estilo arquitectónico académico desarrollado en la UC Irvine a mediados de la década de 1990 por Richard N. Taylor y su equipo. Fue creado como un modelo de investigación para descubrir cómo construir interfaces gráficas de usuario (GUIs) altamente desacopladas y basadas en eventos. Debido a que era un modelo académico, la industria absorbió sus principios (desacoplamiento estricto, paso de mensajes asíncronos, buses de eventos), pero no adoptó "C2" como un término de marketing convencional como hizo con "Microservicios" o "MVC".

- **Ejemplos:**
  - [isr-uci-edu/ArchStudio5](https://github.com/isr-uci-edu/ArchStudio5): El entorno de investigación de arquitectura oficial desarrollado por la UC Irvine (los creadores de C2), construido sobre los principios de C2 y xADL para modelar y ejecutar sistemas de componentes y conectores.
  - Aunque el C2 estricto sigue siendo principalmente un modelo académico, los frameworks de interfaz de usuario modernos basados en eventos como [facebook/react](https://github.com/facebook/react) comparten su ADN conceptual de comunicación asíncrona y desacoplada de componentes a través de estados y propiedades.
- **Recursos:**
  - [A Component- and Message-Based Architectural Style for GUI Software](https://ics.uci.edu/~taylor/documents/1995-C2-TSE.pdf) por Richard N. Taylor: El artículo académico original que define el estilo arquitectónico C2.
  - [C2 Architectural Style Overview](https://isr.uci.edu/architecture/c2StyleRules.html) por la UC Irvine: La página original del proyecto y documentación para el estilo C2.

</details>

<details>
<summary><strong>Interpreter Architecture:</strong> Una máquina virtual que ejecuta instrucciones en un lenguaje personalizado (por ejemplo, JVM, motores de scripting).</summary>

Construida para ejecutar instrucciones personalizadas o lenguajes específicos de dominio. Funciona como una máquina virtual que lee, analiza y ejecuta el código en tiempo de ejecución en lugar de compilarlo en código máquina nativo previamente. Hace posible la portabilidad multiplataforma y permite características de lenguaje dinámico, como el motor principal detrás de lenguajes de scripting como Python, Ruby y JavaScript.

- **Ejemplos:**
  - [python/cpython](https://github.com/python/cpython): La implementación de referencia del lenguaje de programación Python, que contiene el compilador y el bucle de ejecución (intérprete).
  - [ruby/ruby](https://github.com/ruby/ruby): El intérprete central para el lenguaje de programación Ruby.
- **Recursos:**
  - "Crafting Interpreters" por Robert Nystrom: Una guía práctica para construir una arquitectura de intérprete desde cero.
  - "Engineering a Compiler" por Keith Cooper y Linda Torczon: El libro de texto estándar que cubre el diseño de analizadores, máquinas virtuales e intérpretes.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

### Topologías de Procesamiento de Datos a Gran Escala y Centradas en Datos

Macroarquitecturas construidas específicamente para ingerir, almacenar, enrutar y procesar grandes volúmenes de información en clústeres distribuidos o planos unificados.

<details>
<summary><strong>Lambda Architecture:</strong> Construida para el procesamiento de big data, combinando el procesamiento por lotes para vistas detalladas y el procesamiento por flujos ("stream processing") para vistas en tiempo real.</summary>

Un enfoque para el procesamiento de big data que ofrece un sistema fiable y tolerante a fallos contra errores de hardware y humanos. Procesa grandes cantidades de datos ejecutando simultáneamente métodos de procesamiento por lotes y de procesamiento por flujos. El nivel de lote gestiona el archivo histórico y computa vistas precisas, mientras que el nivel de velocidad gestiona los datos recientes para consultas de baja latencia. El nivel de servicio indexa la salida para una consulta rápida.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* Lambda es un patrón de diseño de macro-tuberías utilizado en sistemas de big data empresariales. Se construye uniendo motores de infraestructura separados (como Hadoop para el lote y Storm para la velocidad). Por lo tanto, no hay un repositorio único de aplicación de "Arquitectura Lambda" de código abierto; es una estrategia de despliegue utilizada por equipos de ingeniería de datos en diversas infraestructuras. Sin embargo, los siguientes ejemplos ilustran detalles de implementación:
    - [terraform-aws-modules/terraform-aws-lambda](https://github.com/terraform-aws-modules/terraform-aws-lambda): El módulo Terraform estándar de la industria para gestionar despliegues de lambda serverless en una arquitectura por niveles.
- **Recursos:**
  - [How to beat the CAP theorem](http://nathanmarz.com/blog/how-to-beat-the-cap-theorem.html) por Nathan Marz: La entrada de blog original que introduce la Arquitectura Lambda.
  - "Big Data: Principles and best practices of scalable realtime data systems" por Nathan Marz y James Warren: El libro detallado sobre la construcción de arquitecturas Lambda.

</details>

<details>
<summary><strong>Kappa Architecture:</strong> Una simplificación de Lambda, que utiliza un único motor de procesamiento por flujos tanto para los datos en tiempo real como para los datos por lotes.</summary>

Una arquitectura de procesamiento de datos que simplifica los sistemas de datos a gran escala. Utiliza una única tecnología tanto para el procesamiento en tiempo real como por lotes, tratando todo como un flujo continuo de eventos. Los datos históricos se vuelven a procesar reproduciendo el flujo de eventos a través del mismo motor de procesamiento utilizado para los datos en tiempo real, manteniendo una tubería unificada para todos los cálculos.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* Kappa es una filosofía de flujo de datos empresarial que trata todos los datos como un flujo continuo. Se construye desplegando y configurando motores de streaming (como Kafka y Flink). Dado que es un flujo de infraestructura conceptual y no una única base de código de aplicación, no hay ejemplos de aplicaciones independientes disponibles en repositorios de código abierto. Sin embargo, los siguientes ejemplos ilustran detalles de implementación:
    - [confluentinc/cp-demo](https://github.com/confluentinc/cp-demo): Una completa demostración de la Plataforma Confluent, que muestra el streaming de eventos en tiempo real y el reprocesamiento (conceptos Kappa).
- **Recursos:**
  - [Questioning the Lambda Architecture](https://www.oreilly.com/radar/questioning-the-lambda-architecture/) por Jay Kreps: El artículo original que propone la Arquitectura Kappa como alternativa a Lambda.
  - [Kappa Architecture Introduction](https://hazelcast.com/glossary/kappa-architecture/) por Hazelcast: Un desglose claro de los principios de la arquitectura Kappa.

</details>

<details>
<summary><strong>MapReduce Architecture:</strong> Un modelo de programación para procesar grandes conjuntos de datos en paralelo en un clúster distribuido.</summary>

Una técnica de procesamiento y modelo de programa para la computación distribuida. El algoritmo contiene dos fases distintas: Map (Mapear) y Reduce (Reducir). La fase Map toma un conjunto de datos y lo convierte en otro conjunto de datos, descomponiendo elementos individuales en tuplas (pares clave/valor). La fase Reduce toma la salida de la fase map como entrada y combina esas tuplas de datos en un conjunto condensado de resultados.

- **Ejemplos:**
  - [apache/hadoop](https://github.com/apache/hadoop): El framework de código abierto original que implementó el modelo de programación MapReduce para el almacenamiento y procesamiento distribuidos.
  - [apache/couchdb](https://github.com/apache/couchdb): Una base de datos NoSQL orientada a documentos que utiliza MapReduce como su mecanismo principal para construir vistas y consultar datos.
- **Recursos:**
  - [MapReduce: Simplified Data Processing on Large Clusters](https://research.google/pubs/pub62/) por Jeffrey Dean y Sanjay Ghemawat: El artículo de investigación central de Google que introdujo MapReduce al mundo.
  - [Hadoop MapReduce Tutorial](https://hadoop.apache.org/docs/current/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html) por la Apache Software Foundation: Documentación y guías oficiales para implementar trabajos de MapReduce.

</details>

<details>
<summary><strong>Batch Sequential Architecture:</strong> Los programas se ejecutan de forma independiente en un orden predefinido, pasando los datos como archivos; utilizado en el procesamiento de datos tradicional.</summary>

Un patrón de procesamiento de datos clásico donde programas separados e independientes se ejecutan en una secuencia estricta. Cada programa se ejecuta hasta su finalización, lee un archivo de entrada, procesa los datos y escribe un archivo de salida que se convierte en la entrada para el siguiente programa exacto en la secuencia. Es muy eficaz para transformaciones de datos programadas de gran volumen, como la conciliación financiera al final del día o el procesamiento de nóminas.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* El procesamiento por lotes secuencial (Batch Sequential) es un flujo de trabajo empresarial tradicional en el que se ejecutan secuencialmente scripts discretos e independientes, pasando archivos entre ellos. Debido a que depende de la orquestación de muchos scripts de negocio separados (como las tuberías de conciliación bancaria o de nóminas al final del día), no hay repositorios unificados de código abierto que representen una aplicación de negocio completa de este tipo. Sin embargo, los siguientes ejemplos ilustran detalles de implementación:
    - [spring-projects/spring-batch](https://github.com/spring-projects/spring-batch/tree/main/spring-batch-samples): Ejemplos mantenidos oficialmente para el framework Spring Batch, que demuestran la ejecución de trabajos secuenciales y el procesamiento basado en archivos.
- **Recursos:**
  - [Batch Processing Documentation](https://docs.spring.io/spring-batch/reference/) por Spring: Directrices detalladas sobre la estructuración y gestión de trabajos secuenciales por lotes.
  - [Enterprise Integration Patterns: Process Manager](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ProcessManager.html) por Gregor Hohpe: Patrones arquitectónicos relacionados con el enrutamiento y el procesamiento secuencial de grandes cargas de trabajo.

</details>

<details>
<summary><strong>Database Systems Architecture:</strong> Almacén de datos centralizado al que acceden múltiples computaciones independientes (aplicaciones clásicas de 3 niveles).</summary>

Una arquitectura donde un sistema de gestión de bases de datos centralizado y fiable es el núcleo de la aplicación. Múltiples instancias de aplicaciones o servicios integrales se conectan a esta base de datos compartida para leer, escribir y manipular datos. La propia base de datos gestiona la concurrencia, la integridad de las transacciones y la seguridad de los datos, como la única fuente de verdad para todo el sistema distribuido.

- **Ejemplos:**
  - [postgres/postgres](https://github.com/postgres/postgres): El repositorio principal de PostgreSQL, que representa el estándar de oro para los sistemas de bases de datos relacionales centralizados.
  - [mysql/mysql-server](https://github.com/mysql/mysql-server): El repositorio principal de MySQL, ampliamente utilizado como almacén de datos centralizado en las arquitecturas web tradicionales.
- **Recursos:**
  - "Database System Concepts" por Abraham Silberschatz, Henry F. Korth y S. Sudarshan: El libro de texto académico definitivo que detalla la arquitectura de los sistemas de gestión de bases de datos.
  - [Architecture of a Database System](https://dsf.berkeley.edu/papers/fntdb07-architecture.pdf) por Joseph M. Hellerstein, Michael Stonebraker y James Hamilton: Un artículo detallado sobre cómo se construyen los motores de bases de datos relacionales.

</details>

<details>
<summary><strong>Data Mesh:</strong> Una arquitectura sociotécnica descentralizada que trata los datos como un producto, con equipos de dominio que poseen y sirven sus propios datos.</summary>

Un enfoque descentralizado de la arquitectura de datos que distribuye la responsabilidad directamente a los dominios de negocio específicos que generan los datos. Cada equipo de dominio posee sus propias tuberías de datos y sirve sus datos como un "producto" totalmente funcional al resto de la organización. Una estructura de gobernanza federada mantiene que estos distintos productos de datos sigan siendo interoperables y seguros en toda la empresa.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* Data Mesh es un paradigma organizacional sociotécnico descentralizado, no una aplicación de software. Dicta cómo los diferentes equipos de dominio dentro de una empresa gobiernan y comparten sus datos. Debido a que es una reestructuración corporativa de la propiedad de los datos que depende en gran medida de la gobernanza interna y de diversas herramientas, no existe una base de código de aplicación de código abierto que represente un Data Mesh. Sin embargo, los siguientes ejemplos ilustran detalles de implementación:
    - [Data-Mesh-Manager/data-mesh-architecture-examples](https://github.com/Data-Mesh-Manager/data-mesh-architecture-examples): Una colección de modelos arquitectónicos y ejemplos de infraestructura para implementar productos de datos descentralizados.
- **Recursos:**
  - [How to Move Beyond a Monolithic Data Lake to a Distributed Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html) por Zhamak Dehghani: El artículo original que introduce el paradigma Data Mesh.
  - "Data Mesh: Delivering Data-Driven Value at Scale" por Zhamak Dehghani: El libro detallado que describe la implementación y los cambios organizativos necesarios para un data mesh.

</details>

<details>
<summary><strong>Data Fabric:</strong> Una arquitectura que proporciona un plano de datos unificado en entornos híbridos y de múltiples nubes.</summary>

Una arquitectura que utiliza el aprendizaje automático y los metadatos para descubrir, conectar y asegurar automáticamente los datos en sistemas y proveedores de nube dispares. Crea una capa de datos unificada y virtualizada, permitiendo que los usuarios y las aplicaciones accedan a la información directamente a través de todas las ubicaciones físicas y formatos de almacenamiento.

- **Ejemplos:**
  - *Note sobre Ejemplos:* Data Fabric es una estrategia de integración conceptual a nivel empresarial que utiliza IA y metadatos para unir datos de múltiples nubes privadas y públicas. Se logra adquiriendo o desplegando docenas de plataformas interconectadas de gobernanza, catalogación y virtualización. Al ser una estrategia de TI a nivel macro, no existen aplicaciones de código abierto individuales que encarnen un Data Fabric. Sin embargo, los siguientes ejemplos ilustran detalles de implementación:
    - [GoogleCloudPlatform/dataplex-blueprints](https://github.com/GoogleCloudPlatform/dataplex-blueprints): Infraestructura como código y ejemplos de configuración para construir un tejido de datos inteligente utilizando Google Cloud Dataplex.
- **Recursos:**
  - [What is a Data Fabric?](https://www.ibm.com/topics/data-fabric) por IBM: Una definición clara y una visión general de los componentes que forman un tejido de datos.
  - [What is a Data Fabric?](https://www.sap.com/insights/what-is-a-data-fabric.html) por SAP: Un desglose detallado de los conceptos de tejido de datos, componentes principales y cómo unifica la gestión de datos entre entornos.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

### Topologías de Eventos, Mensajería y Comunicación

Modelos distribuidos que dictan cómo los servicios dispares intercambian información, reaccionan a los cambios de estado y gestionan el enrutamiento de solicitudes de forma dinámica.

<details>
<summary><strong>Event-Driven Architecture (Macro):</strong> Un sistema distribuido donde los componentes reaccionan a los cambios de estado (eventos) difundidos a través de la red, en lugar de depender de una respuesta/solicitud directa.</summary>

Una topología altamente desacoplada construida en torno a la producción, detección y consumo de cambios de estado. Los servicios publican eventos en un broker central o bus de eventos. Los servicios suscritos escuchan estos eventos y activan su propia lógica de negocio aislada de forma asíncrona. Se utiliza para construir sistemas responsivos y escalables donde los picos impredecibles de tráfico son absorbidos por colas para evitar dañar las bases de datos posteriores.

- **Ejemplos:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): La aplicación de referencia para el libro "Microservices Patterns", construida íntegramente sobre una arquitectura dirigida por eventos utilizando sagas y buzones de salida transaccionales (transactional outboxes).
  - [aws-samples/aws-serverless-airline-booking](https://github.com/aws-samples/aws-serverless-airline-booking): Una aplicación serverless completa construida en AWS utilizando una arquitectura dirigida por eventos para coordinar distintos servicios de reserva a través de EventBridge.
- **Recursos:**
  - [What is an Event-Driven Architecture?](https://aws.amazon.com/event-driven-architecture/) por AWS: Una guía de los componentes y beneficios de los sistemas dirigidos por eventos.
  - "Designing Event-Driven Systems" por Ben Stopford: Un libro detallado sobre la construcción de arquitecturas centradas en eventos.

</details>

<details>
<summary><strong>Process Communication (Communicating Processes) Architecture:</strong> Procesos independientes que se comunican a través de canales como sockets, colas de mensajes o memoria compartida.</summary>

Un modelo de concurrencia central donde una aplicación se divide en procesos aislados que se ejecutan simultáneamente y se pasan mensajes entre sí para coordinar el trabajo. Al garantizar que los procesos solo compartan mensajes pasados explícitamente a través de canales estrictamente definidos, el sistema evita condiciones de carrera y complejos mecanismos de bloqueo. Es la base arquitectónica de los sistemas altamente concurrentes, como los conmutadores de telecomunicaciones, los servidores de chat y las bases de datos distribuidas.

- **Ejemplos:**
  - [rabbitmq/rabbitmq-server](https://github.com/rabbitmq/rabbitmq-server): Aunque utilizado como broker de mensajes por otros, su arquitectura interna es un ejemplo perfecto del modelo de Actor de Erlang, utilizando miles de procesos aislados comunicados para gestionar una alta concurrencia.
  - [syncthing/syncthing](https://github.com/syncthing/syncthing): Un programa de sincronización continua de archivos escrito en Go, estructurado internamente en torno a Procesos Secuenciales Comunicantes (CSP) utilizando gorrutinas (goroutines) y canales para pasar mensajes de forma segura entre las operaciones de sincronización.
- **Recursos:**
  - [Communicating Sequential Processes](http://www.usingcsp.com/cspbook.pdf) por C.A.R. Hoare: El artículo fundamental de la informática que define el estilo arquitectónico CSP.
  - [The Actor Model](https://doc.akka.io/docs/akka/current/typed/guide/actors-intro.html) por Akka: Documentación que explica cómo los procesos concurrentes se comunican mediante el paso de mensajes.

</details>

<details>
<summary><strong>Service Mesh Architecture:</strong> Una capa de infraestructura dedicada para gestionar las comunicaciones de servicio a servicio en arquitecturas de microservicios, utilizando normalmente un proxy sidecar para gestionar el enrutamiento, la seguridad y la observabilidad sin alterar el código de la aplicación.</summary>

Una topología operativa que abstrae la capa de red del código de la aplicación. Las capacidades de red, como la lógica de reintento, el cifrado mutuo TLS y el rastreo distribuido, se gestionan mediante un proxy sidecar desplegado junto a cada instancia de servicio. La red interconectada de estos proxies forma la malla (mesh), controlada por un nivel de control central. Es crucial para mantener la seguridad, la observabilidad y el control del tráfico en grandes despliegues de Kubernetes.

- **Ejemplos:**
  - [istio/istio/tree/master/samples/bookinfo](https://github.com/istio/istio/tree/master/samples/bookinfo): La aplicación de referencia políglota oficial diseñada específicamente para demostrar el enrutamiento de tráfico de Service Mesh, la inyección de fallos y las métricas a través de diferentes backends de lenguaje.
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): La aplicación de 11 niveles de Google (Online Boutique) estructurada explícitamente para ser desplegada en una malla de servicios para gestionar la comunicación de servicio a servicio.
- **Recursos:**
  - [What is a Service Mesh?](https://www.redhat.com/en/topics/microservices/what-is-a-service-mesh) por Red Hat: Un desglose claro de los conceptos de plano de datos, plano de control y proxy sidecar.
  - "Istio Up and Running" por Lee Calcote y Zack Butcher: Una guía práctica para implementar una arquitectura de malla de servicios.

</details>

<details>
<summary><strong>API Gateway / Backends for Frontends (BFF) Architecture:</strong> Un único punto de entrada (gateway) o múltiples backends específicos para el cliente (BFF) que gestionan el enrutamiento, la composición y las preocupaciones transversales de las APIs.</summary>

Un patrón estructural utilizado para abstraer la complejidad de los microservicios de backend. Un API Gateway es un proxy inverso que añade múltiples llamadas a microservicios en una sola respuesta, gestionando la autenticación, la limitación de velocidad y el enrutamiento de solicitudes. La variante Backends for Frontends (BFF) va más allá al crear gateways dedicados y separados adaptados específicamente para diferentes clientes de interfaz de usuario (por ejemplo, una API para móviles y otra diferente para la web de escritorio). Esto gestiona que los clientes reciban los datos exactos que necesitan, formateados perfectamente para su interfaz específica.

- **Ejemplos:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Aplicación de microservicios de referencia de Microsoft que implementa el patrón Backends for Frontends (BFF), con configuraciones de enrutamiento de gateway totalmente separadas para sus clientes Web y Móvil.
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Presenta un servicio `frontend` dedicado como el único API Gateway que orquesta las llamadas a los diversos servicios de backend (carrito, catálogo de productos, moneda, etc.) para renderizar las vistas web finales.
- **Recursos:**
  - [Pattern: Backends For Frontends](https://samnewman.io/patterns/architectural/bff/) por Sam Newman: La definición original y la inmersión profunda en el patrón arquitectónico BFF.
  - [API Gateway Pattern](https://microservices.io/patterns/apigateway.html) por Chris Richardson: Una mirada detallada a los beneficios e inconvenientes de utilizar un gateway de API unificado.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

### Topologías de Concurrencia, Estado y Transacciones

Paradigmas que facilitan la gestión de estados complejos, el paralelismo de alto rendimiento y las transacciones distribuidas sin los cuellos de botella de los bloqueos tradicionales.

<details>
<summary><strong>Actor Model Architecture:</strong> Un modelo conceptual para la computación concurrente donde los "actores" son las primitivas universales, modificando su propio estado y comunicándose exclusivamente mediante el paso asíncrono de mensajes (por ejemplo, Erlang, Akka).</summary>

Una topología altamente concurrente donde el sistema se compone de miles o millones de entidades independientes y ligeras llamadas "actores". Cada actor encapsula estrictamente su propio estado privado y flujo de ejecución. Debido a que los actores nunca comparten memoria y solo interactúan enviando mensajes asíncronos a los buzones de los demás, el sistema elimina la necesidad de bloqueos de hilos (locks) y semáforos (mutexes) tradicionales. Es la arquitectura de elección para sistemas altamente concurrentes y tolerantes a fallos, como los servidores de juegos multijugador y los conmutadores de telecomunicaciones.

- **Ejemplos:**
  - [ornicar/lila](https://github.com/ornicar/lila): La aplicación de backend principal de Lichess.org. Está construida usando Scala y el framework de actores Akka para gestionar millones de partidas de ajedrez simultáneas, estados de jugadores y conexiones websocket en tiempo real sin cuellos de botella por bloqueos.
  - [rabbitmq/rabbitmq-server](https://github.com/rabbitmq/rabbitmq-server): El broker de mensajes ampliamente utilizado, construido de forma nativa en Erlang. Su arquitectura interna es una implementación de libro del modelo de Actor, donde millones de procesos de actor ligeros gestionan las colas, el enrutamiento y la gestión del estado de forma concurrente.
- **Recursos:**
  - [The Actor Model in 10 Minutes](https://www.brianstorti.com/the-actor-model/) por Brian Storti: Una explicación accesible de cómo los actores gestionan el estado, la concurrencia y los buzones de mensajes.
  - "Reactive Messaging Patterns with the Actor Model" por Vaughn Vernon: Una inmersión profunda en la construcción de sistemas empresariales utilizando la concurrencia basada en actores.

</details>

<details>
<summary><strong>Space-Based Architecture (Tuple Space):</strong> Utiliza memoria compartida distribuida para evitar los cuellos de botella de la base de datos, escalando horizontalmente para un tráfico de gran volumen y variable.</summary>

Una arquitectura que elimina la base de datos como cuello de botella del rendimiento. En lugar de que las aplicaciones consulten una base de datos central a través de una red, los datos se particionan y se mantienen en memoria a través de una red (grid) de unidades de procesamiento activas. La lógica de la aplicación y los datos sobre los que opera se encuentran en la misma memoria RAM (el "espacio" o space). Escala horizontalmente activando más unidades de procesamiento, lo que la hace altamente eficaz para sistemas que se enfrentan a picos impredecibles de tráfico, como las plataformas de trading de alta frecuencia, los sistemas de venta de entradas y los motores de pujas en tiempo real.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* La Arquitectura Basada en el Espacio (Space-Based Architecture) es una topología de despliegue empresarial más que un diseño de aplicación independiente. Se implementa desplegando la lógica de negocio directamente en el middleware de Cuadrículas de Datos en Memoria (IMDG) distribuidas. Debido a que depende en gran medida de la orquestación de estos motores de cuadrícula especializados (como Apache Ignite o Hazelcast) a través de un clúster, no hay repositorios únicos de aplicación de negocio de código abierto desplegables que representen plenamente esta topología de forma nativa.
- **Recursos:**
  - [Space-Based Architecture Pattern](https://www.oreilly.com/library/view/software-architecture-patterns/9781491971437/ch04.html) por Mark Richards: La explicación arquitectónica definitiva de las unidades de procesamiento, el middleware virtualizado y las cuadrículas de datos.
  - [Tuple Space](https://en.wikipedia.org/wiki/Tuple_space): Una visión general del concepto central de computación distribuida que evolucionó hacia las arquitecturas modernas basadas en el espacio.

</details>

<details>
<summary><strong>Saga Architecture:</strong> Gestiona transacciones distribuidas en microservicios mediante una secuencia de transacciones locales con acciones de compensación.</summary>

Un patrón transaccional distribuido que resuelve el problema de mantener la consistencia de los datos en múltiples bases de datos independientes. Dado que los microservicios poco acoplados no pueden compartir una única transacción de base de datos ACID, una Saga divide una gran transacción de negocio en una serie de pasos locales más pequeños. Si un paso posterior falla, el sistema ejecuta una serie de "transacciones de compensación" (rollbacks) para deshacer los pasos anteriores. El resultado es una consistencia eventual sin depender de protocolos de bloqueo síncronos y distribuidos como la Confirmación en Dos Fases (2PC).

- **Ejemplos:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): La aplicación de referencia definitiva para microservicios, diseñada para demostrar la coreografía y orquestación de Sagas para un complejo sistema de gestión de pedidos de comida para llevar ("Food to Go").
  - [berndruecker/trip-booking-saga-java](https://github.com/berndruecker/trip-booking-saga-java): Una aplicación de negocio pura que demuestra una saga de reserva de viajes (reserva de un vuelo, hotel y coche de forma secuencial), destacando la ejecución de acciones compensatorias cuando falla una reserva remota.
- **Recursos:**
  - [Pattern: Saga](https://microservices.io/patterns/data/saga.html) por Chris Richardson: El estándar de la industria para la definición y el desglose de orquestación frente a coreografía en las Sagas.
  - [Saga distributed transactions](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/saga/saga) por Microsoft Azure: Una guía práctica sobre la implementación del patrón Saga para microservicios basados en la nube.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

### Arquitecturas de Sistemas de Control, IA y Conocimiento

Macroestructuras especializadas para el razonamiento autónomo, la inferencia, el reconocimiento de patrones y el manejo del hardware físico.

<details>
<summary><strong>Agentic Architecture (Multi-Agent Systems):</strong> Una topología emergente impulsada por la IA en la que sistemas autónomos (agentes) utilizan modelos de lenguaje de gran tamaño (LLM) para razonar, planificar y ejecutar acciones, colaborando a menudo para lograr objetivos complejos.</summary>

Una topología dinámica que se apoya fuertemente en los Modelos de Lenguaje de Gran Tamaño (LLMs) como motores de razonamiento central. En lugar de seguir caminos deterministas y preconfigurados, el sistema define objetivos de alto nivel y equipa a los "agentes" con herramientas (calculadoras, búsqueda web, acceso a APIs). Estos agentes planifican sus pasos de ejecución de forma autónoma, reflexionan sobre los resultados intermedios y se comunican con otros agentes especializados para resolver problemas complejos y abiertos. Representa un cambio de la programación imperativa a la orquestación autónoma orientada a objetivos.

- **Ejemplos:**
  - [Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT): Una aplicación de código abierto muy popular que actúa como un agente autónomo, encadenando pensamientos de LLM para lograr de forma independiente los objetivos definidos por el usuario.
  - [OpenBMB/ChatDev](https://github.com/OpenBMB/ChatDev): Una aplicación de compañía de software virtual donde múltiples agentes de IA distintos (como un CEO, un programador y un revisor) colaboran de forma autónoma para construir software basado en una única indicación (prompt).
- **Recursos:**
  - [LLM Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/) por Lilian Weng: El desglose técnico definitivo de la planificación de agentes, la memoria y el uso de herramientas.
  - [AutoGPT Documentation](https://docs.agpt.co/): Guías prácticas de implementación para bucles de agentes autónomos.

</details>

<details>
<summary><strong>Blackboard Architecture:</strong> Múltiples subsistemas especializados colaboran en una estructura de datos compartida (pizarra o "blackboard"), común en la IA y el reconocimiento de patrones.</summary>

Un patrón de IA temprano para problemas complejos y no deterministas como el reconocimiento de voz o el modelado estructural de proteínas. Cuenta con un espacio de memoria global central (la pizarra) y una colección de fuentes de conocimiento independientes y especializadas (los "expertos"). No hay un flujo de control central que dicte la secuencia de operaciones. Cada experto supervisa constantemente la pizarra. Cuando un experto ve datos que puede procesar, actualiza la pizarra con una solución parcial, lo que activa a otros expertos para que contribuyan hasta que surja una solución final.

- **Ejemplos:**
  - [stanfordnlp/CoreNLP](https://github.com/stanfordnlp/CoreNLP): La aplicación central de procesamiento de lenguaje natural (NLP) de Stanford utiliza una tubería inspirada en gran medida en el patrón Blackboard. Un objeto `Annotation` compartido (la pizarra) se pasa y es modificado por anotadores independientes (expertos en etiquetado de categorías gramaticales, reconocimiento de entidades, análisis sintáctico) para construir un análisis lingüístico completo.
- **Recursos:**
  - [Blackboard System](https://en.wikipedia.org/wiki/Blackboard_system): Una visión general del shell de control, la pizarra y las fuentes de conocimiento.
  - "Pattern-Oriented Software Architecture, Volume 1" (POSA): Contiene la formalización definitiva del patrón Blackboard.

</details>

<details>
<summary><strong>Rule-Based System Architecture:</strong> Un motor de inferencia aplica un conjunto de reglas a una base de conocimientos para derivar conclusiones; utilizado en sistemas expertos.</summary>

Un patrón central de la IA simbólica clásica, a menudo denominado "Sistema Experto". Separa estrictamente la lógica de negocio (las reglas) del control de ejecución (el motor de inferencia). Los expertos en el dominio humano definen una amplia base de conocimientos de hechos y condiciones "SI-ENTONCES" (IF-THEN). A continuación, el motor de inferencia evalúa dinámicamente los datos entrantes frente a estas reglas, disparando las reglas aplicables para deducir nuevos hechos o activar acciones. Es muy eficaz para sistemas complejos de cumplimiento, diagnóstico médico y suscripción automatizada, donde la lógica de decisión debe ser estrictamente auditable.

- **Ejemplos:**
  - [eslint/eslint](https://github.com/eslint/eslint): Una aplicación pura basada en reglas donde un motor central evalúa un Árbol de Sintaxis Abstracta (AST) frente a cientos de reglas independientes y conectables para inferir la calidad del código y activar advertencias.
  - [Yelp/elastalert](https://github.com/Yelp/elastalert): Una aplicación que alerta sobre anomalías de Elasticsearch evaluando continuamente los datos frente a un amplio diccionario de reglas definidas por el usuario.
- **Recursos:**
  - [Rule-Based System](https://en.wikipedia.org/wiki/Rule-based_system): Una visión general de los motores de inferencia y los sistemas expertos.
  - "Expert Systems: Principles and Programming" por Joseph C. Giarratano y Gary D. Riley: El libro de texto clásico sobre el diseño de arquitecturas basadas en reglas.

</details>

<details>
<summary><strong>Closed-Loop Control Architecture (Process Control):</strong> Gestiona procesos físicos a través de sensores y actuadores (termostato, control de crucero, sistemas embebidos).</summary>

Una arquitectura vinculada al mundo físico, que opera en un bucle continuo e infinito para mantener un estado físico deseado. Se basa en un sensor para leer el estado actual de un sistema, compara esa lectura con el punto de ajuste deseado para calcular un valor de error y envía inmediatamente una orden correctiva a un actuador físico. El sistema depende íntegramente de este bucle de retroalimentación continua para adaptarse a las perturbaciones físicas externas. Es la arquitectura de software dominante para la robótica industrial, los vehículos autónomos y los sistemas de climatización (HVAC).

- **Ejemplos:**
  - [ArduPilot/ardupilot](https://github.com/ArduPilot/ardupilot): La popular suite de software de piloto automático de código abierto, construida precisamente en torno a controladores PID de bucle cerrado de alta frecuencia para mantener la estabilidad de la aeronave.
  - [commaai/openpilot](https://github.com/commaai/openpilot): Una aplicación de conducción autónoma de código abierto que utiliza arquitecturas de control de bucle cerrado para ajustar continuamente la dirección y la aceleración de un vehículo basándose en el feedback de la cámara y el radar en tiempo real.
- **Recursos:**
  - [Control Theory](https://en.wikipedia.org/wiki/Control_theory): Los conceptos y las matemáticas básicas de los bucles de retroalimentación (feedback loops).
  - "Feedback Control of Dynamic Systems" por Gene F. Franklin: El texto de ingeniería estándar que detalla el diseño de software y hardware de bucle cerrado.

</details>

<details>
<summary><strong>Real-Time Architecture:</strong> Sistemas en los que el tiempo de respuesta es crítico y debe estar garantizado (por ejemplo, aviónica, dispositivos médicos).</summary>

Una arquitectura definida por restricciones temporales deterministas estrictas más que por el rendimiento puro. En una arquitectura de tiempo real, calcular la respuesta correcta demasiado tarde se considera un fallo total del sistema. Para cumplir con los estrictos plazos de tiempo de respuesta, estos sistemas utilizan Sistemas Operativos de Tiempo Real (RTOS) especializados, evitan las pausas imprevisibles de la recolección de basura (garbage collection) y particionan estrictamente la memoria. Son esenciales para el hardware crítico para la seguridad como marcapasos, sistemas de frenado antibloqueo y satélites orbitales.

- **Ejemplos:**
  - [PX4/PX4-Autopilot](https://github.com/PX4/PX4-Autopilot): Una aplicación de control de vuelo de código abierto que se dirige específicamente a sistemas operativos de tiempo real (como NuttX) para garantizar una sincronización determinista estricta para el control de los motores de los drones.
  - [nasa/cFS](https://github.com/nasa/cFS): El Core Flight System desarrollado por la NASA, un framework de software de tiempo real y una suite de aplicaciones utilizada en misiones reales de vuelo espacial donde el incumplimiento de un plazo de procesamiento puede dar lugar al fracaso de la misión.
- **Recursos:**
  - [Real-Time Computing](https://en.wikipedia.org/wiki/Real-time_computing): Una visión general de las restricciones de tiempo real duras (hard), firmes (firm) y suaves (soft).
  - "Real-Time Systems Design and Analysis" por Phillip A. Laplante: Una guía sobre la estructuración del determinismo en las arquitecturas de software.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

### Migración de Sistemas y Topologías Híbridas

Modelos arquitectónicos de transición o compuestos utilizados para unir distintos entornos de computación o para eliminar gradualmente los sistemas monolíticos heredados.

<details>
<summary><strong>Strangler Fig Architecture:</strong> Reemplaza gradualmente un sistema heredado construyendo un nuevo sistema a su alrededor y redirigiendo gradualmente la funcionalidad hacia él.</summary>

Un patrón de migración utilizado para modernizar de forma segura los sistemas heredados monolíticos (legacy). Se coloca una fachada de enrutamiento delante de la aplicación heredada. A medida que los equipos de desarrollo construyen servicios nuevos y modernizados, la fachada intercepta las solicitudes y las redirige a los nuevos servicios, mientras enruta el tráfico restante no migrado al sistema heredado. Con el tiempo, el nuevo sistema crece alrededor del antiguo, sustituyendo su funcionalidad hasta que el sistema heredado puede ser retirado con seguridad.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* Strangler Fig es una estrategia de migración transitoria aplicada a bases de código empresariales propietarias existentes en lugar de un estado final arquitectónico independiente. Debido a que describe el proceso activo de reescribir y enrutar el tráfico fuera de un sistema legado específico, no hay repositorios de aplicaciones de código abierto construidos nativamente como aplicaciones "Strangler Fig". Sin embargo, los siguientes ejemplos ilustran detalles de implementación:
    - [aws-samples/strangler-fig-pattern-using-amazon-api-gateway](https://github.com/aws-samples/strangler-fig-pattern-using-amazon-api-gateway): Una implementación práctica que demuestra cómo utilizar API Gateway para enrutar el tráfico de forma incremental entre servicios heredados y modernos.
- **Recursos:**
  - [StranglerFigApplication](https://martinfowler.com/bliki/StranglerFigApplication.html) por Martin Fowler: El artículo original que acuñó el término y describió la estrategia de migración.
  - [Strangler Fig pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/strangler-fig) por Microsoft Azure: Una guía práctica para implementar la fachada y el enrutamiento necesarios para la migración.

</details>

<details>
<summary><strong>Hybrid Architecture / Multi-Cloud Architecture:</strong> Combina múltiples estilos arquitectónicos o despliegue a través de múltiples proveedores de nube.</summary>

Una topología de despliegue a nivel macro que abarca centros de datos físicos locales (on-premises) y uno o más entornos de nube pública. Proporciona flexibilidad a las organizaciones, permitiéndoles mantener los datos altamente sensibles en hardware local para el cumplimiento normativo mientras escalan las cargas de trabajo variables en la nube pública para aprovechar el escalado horizontal. Se apoya fuertemente en plataformas de orquestación de contenedores para mantener un comportamiento consistente de las aplicaciones en diferentes entornos físicos.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* Las arquitecturas híbridas y multi-nube son estrategias de despliegue de infraestructura gestionadas por capas de red y orquestación (como Google Anthos, Azure Arc o Kubernetes Federation). Una aplicación de negocio desplegada en una configuración híbrida es simplemente una aplicación estándar (a menudo microservicios) distribuida en diferentes servidores. Por lo tanto, no existe una base de código única de código abierto que encarne la "Arquitectura Híbrida".
- **Recursos:**
  - [What is a Hybrid Cloud?](https://www.redhat.com/en/topics/cloud-computing/what-is-hybrid-cloud) por Red Hat: Un desglose claro de cómo se integran los recursos locales y de la nube.
  - [Multi-cloud architecture patterns](https://cloud.google.com/architecture/multi-cloud-architecture) por Google Cloud: Modelos de despliegue estándar de la industria para distribuir cargas de trabajo entre diferentes proveedores.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

### Topologías de Enlace de Recursos e Información

Arquitecturas basadas fundamentalmente en la centralización del acceso a datos compartidos o en la conexión de documentos distribuidos mediante referencias asociativas.

<details>
<summary><strong>Hypertext System Architecture:</strong> Documentos (nodos) interconectados mediante enlaces; la base de la World Wide Web.</summary>

Un modelo no lineal en el que bloques discretos de información (nodos) se conectan mediante referencias asociativas (hipervínculos). Desacopla el almacenamiento de la información de su presentación estructural, permitiendo que los usuarios naveguen de forma dinámica basándose en el contexto más que en una jerarquía estricta. Es la arquitectura central de la World Wide Web, de las plataformas de documentación modernas y de las aplicaciones de toma de notas asociativas.

- **Ejemplos:**
  - [wikimedia/mediawiki](https://github.com/wikimedia/mediawiki): La aplicación principal que impulsa Wikipedia, actuando como un sistema de hipertexto dinámico de gran tamaño donde millones de nodos están interconectados mediante enlaces asociativos.
  - [logseq/logseq](https://github.com/logseq/logseq): Una aplicación de esquematización (outliner) local-first y no lineal construida íntegramente sobre una arquitectura de hipertexto, que utiliza enlaces bidireccionales para conectar y recorrer nodos de pensamiento de forma autónoma.
- **Recursos:**
  - [As We May Think](https://www.theatlantic.com/magazine/archive/1945/07/as-we-may-think/303881/) por Vannevar Bush: El ensayo central de 1945 que conceptualizó el Memex, el precursor de las arquitecturas de hipertexto.
  - [Information Management: A Proposal](https://www.w3.org/History/1989/proposal.html) por Tim Berners-Lee: La propuesta arquitectónica original para la World Wide Web, que define el uso estructural de los nodos y los enlaces de hipertexto.

</details>

<details>
<summary><strong>Repository Architecture:</strong> Almacén de datos centralizado al que acceden múltiples componentes independientes (por ejemplo, sistemas centrados en bases de datos).</summary>

Una topología centrada en los datos en la que un único repositorio central mantiene el estado compartido del sistema, y una colección de componentes de software independientes operan sobre esos datos centralizados. Los componentes interactúan casi exclusivamente a través del repositorio en lugar de comunicarse directamente entre sí. Es muy eficaz para sistemas que manejan estructuras de datos compartidas complejas en las que diferentes herramientas desacopladas necesitan leer, analizar y modificar la misma fuente de verdad simultáneamente.

- **Ejemplos:**
  - [git/git](https://github.com/git/git): La aplicación de control de versiones central funciona de forma nativa como una arquitectura de repositorio. Los componentes de comandos independientes (`commit`, `status`, `log`) no se comunican entre sí; todos ejecutan su lógica leyendo y escribiendo en la base de datos central de objetos `.git`.
  - [WordPress/WordPress](https://github.com/WordPress/WordPress): Un ejemplo de arquitectura de repositorio basada en la web. La base de datos central mantiene todo el estado, y los componentes independientes (el motor de renderizado central, diversos plug-ins y temas) interactúan de forma independiente con este almacén de datos central sin requerir mensajería directa entre componentes.
- **Recursos:**
  - "Software Architecture: Perspectives on an Emerging Discipline" por Mary Shaw y David Garlan: Proporciona un profundo desglose académico de los estilos arquitectónicos de datos compartidos y repositorios.
  - "Software Architecture in Practice" por Len Bass, Paul Clements y Rick Kazman: Analiza los beneficios operativos y las restricciones de escalabilidad de centralizar el estado de la aplicación dentro de una única capa de repositorio.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

## Capa 2: Patrones de Integración Empresarial

La integración es el "pegamento" que permite que diferentes servicios y sistemas antiguos se comuniquen entre sí. En lugar de centrarse en la lógica interna, esta capa gestiona el movimiento, la conversión y la sincronización de datos entre servicios. Proporciona patrones para mensajería, gateways y tareas distribuidas (Sagas) para que los retrasos de red o los fallos parciales no detengan toda la empresa.

### Patrones de Canales de Mensajería

Estructuras centrales que definen las vías virtuales a través de las cuales las aplicaciones inyectan y consumen información desacoplada.

<details>
<summary><strong>Point-to-Point Channel:</strong> Distribuye mensajes de modo que solo un receptor consuma un mensaje determinado. Una vez leído, el mensaje se elimina del canal.</summary>

Una topología de mensajería para distribuir unidades de trabajo discretas. Un remitente coloca un mensaje en un canal específico (normalmente una cola). Aunque varios receptores concurrentes (workers) pueden escuchar el mismo canal, el canal garantiza que solo un único receptor consumirá y procesará con éxito un mensaje determinado. Es el patrón central para el equilibrio de carga de tareas en segundo plano y para la ejecución idempotente de comandos.

- **Ejemplos:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Depende en gran medida de los canales punto a punto (vía Sidekiq y Redis) para distribuir trabajos asíncronos pesados en segundo plano, como la federación de publicaciones o el procesamiento de imágenes, a instancias de trabajadores individuales disponibles.
  - [getsentry/sentry](https://github.com/getsentry/sentry): La aplicación principal de Sentry utiliza colas de tareas punto a punto (vía Celery) para enrutar millones de informes de fallos entrantes a procesadores disponibles sin duplicar el trabajo.
- **Recursos:**
  - [Point-to-Point Channel](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PointToPointChannel.html) por Gregor Hohpe: La definición original de Patrones de Integración Empresarial.
  - [AWS SQS (Simple Queue Service)](https://aws.amazon.com/sqs/): Documentación central de Amazon sobre cómo operan las colas punto a punto estándar.

</details>

<details>
<summary><strong>Publish-Subscribe Channel:</strong> Difunde un único evento a múltiples suscriptores activos simultáneamente.</summary>

Una topología de mensajería para la notificación de eventos en lugar de la distribución de tareas. Un remitente (publicador) difunde un mensaje a un tema o canal específico. Una copia de ese mensaje se entrega instantáneamente a cada uno de los receptores (suscriptores) que estén escuchando activamente ese canal en ese momento. Permite el desacoplamiento, ya que el publicador no tiene conocimiento de cuántos suscriptores existen ni de qué hacen con los datos.

- **Ejemplos:**
  - [discourse/discourse](https://github.com/discourse/discourse): Utiliza un canal de publicación-suscripción muy activo (vía su Ruby `MessageBus` personalizado) para difundir actualizaciones de la interfaz de usuario en vivo, como nuevas respuestas o notificaciones de usuario, a todos los clientes web conectados simultáneamente.
  - [RocketChat/Rocket.Chat](https://github.com/RocketChat/Rocket.Chat): Una plataforma de comunicación de código abierto que se apoya fuertemente en arquitecturas pub/sub para difundir instantáneamente mensajes de chat a través de múltiples instancias de nodos distribuidos y pantallas de usuario.
- **Recursos:**
  - [Publish-Subscribe Channel](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html) por Gregor Hohpe: La definición central del patrón.
  - [Pub/Sub Messaging](https://cloud.google.com/pubsub/docs/overview) por Google Cloud: Visiones generales arquitectónicas de la difusión de eventos a gran escala.

</details>

<details>
<summary><strong>Dead Letter Channel:</strong> Un canal dedicado donde el sistema de mensajería enruta los mensajes que no pueden ser entregados o procesados con éxito.</summary>

Una topología de gestión de errores para sistemas asíncronos. Cuando un mensaje encuentra un error terminal, como agotar sus intentos de reintento de entrega, exceder su tiempo de vida (TTL) o fallar la validación del esquema, el broker de mensajes lo elimina automáticamente de la cola de procesamiento activa y lo enruta a un Canal de Mensajes Fallidos específico. Esto evita que los mensajes "píldora venenosa" obstruyan la cola principal mientras se preservan los datos fallidos para inspección manual o registro automatizado.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* El Dead Letter Channel es una configuración granular de enrutamiento de errores implementada *dentro* de la infraestructura del broker de mensajes (como RabbitMQ, Kafka o AWS SQS). Dado que es un estado de configuración de cola específico e independiente de una aplicación, no hay repositorios de aplicaciones empresariales independientes que lo representen nativamente.
- **Recursos:**
  - [Dead Letter Channel](https://www.enterpriseintegrationpatterns.com/patterns/messaging/DeadLetterChannel.html) por Gregor Hohpe: La lógica central detrás del aislamiento de mensajes fallidos.
  - [Understanding Amazon SQS dead-letter queues](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues.html): Implementaciones prácticas de DLCs en la arquitectura de nube.

</details>

<details>
<summary><strong>Guaranteed Delivery:</strong> Utiliza mecanismos de almacenamiento persistentes para que un mensaje no se pierda incluso si el sistema o la red fallan antes de la entrega.</summary>

Una topología de Calidad de Servicio (QoS) que evita la pérdida de datos en entornos volátiles. Cuando un remitente despacha un mensaje, la infraestructura de mensajería obliga a que ese mensaje se escriba en un almacenamiento físico no volátil antes de devolver un acuse de recibo de éxito. Si el broker falla, el mensaje sobrevive en el almacenamiento y se entrega tan pronto como el sistema vuelve a estar en línea.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* La Entrega Garantizada es una propiedad de Calidad de Servicio (QoS) impulsada por motores de infraestructura (como Apache ActiveMQ o Kafka). Por lo tanto, no se puede vincular ningún repositorio de aplicación empresarial independiente como ejemplo de esta característica de infraestructura.
- **Recursos:**
  - [Guaranteed Delivery](https://www.enterpriseintegrationpatterns.com/patterns/messaging/GuaranteedMessaging.html) por Gregor Hohpe: Los compromisos arquitectónicos entre la seguridad de la entrega y el rendimiento del sistema.
  - [RabbitMQ Reliability Guide](https://www.rabbitmq.com/docs/reliability): Documentación técnica sobre la implementación de confirmaciones de publicador y persistencia en disco.

</details>


### Patrones de Enrutamiento de Mensajes

Mecanismos que determinan la ruta específica que debe tomar un mensaje basándose en el contexto, reglas o contenido.

<details>
<summary><strong>Content-Based Router:</strong> Examina el contenido de un mensaje y lo enruta a un canal de destino específico basándose en esos datos.</summary>

Un cuadro de conmutación lógico para topologías de mensajería. En lugar de requerir que un remitente sepa exactamente qué cola de bajada debe gestionar una tarea, el remitente publica en un único enrutador central. El enrutador analiza la carga útil o los encabezados del mensaje y redirige dinámicamente el mensaje al canal adecuado. Esto simplifica la lógica del remitente y desacopla a los productores de los consumidores.

- **Ejemplos:**
  - [home-assistant/core](https://github.com/home-assistant/core): Utiliza el enrutamiento basado en contenido dentro de su bus de eventos. El motor central evalúa la carga útil de los eventos entrantes y los enruta a canales de automatización específicos basados en los datos (por ejemplo, si temperatura > 70).
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Examina las cargas útiles de los webhooks entrantes y los despacha a diferentes colas de ejecución basadas en el tipo de evento (push, pull request, release).
- **Recursos:**
  - [Content-Based Router](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ContentBasedRouter.html) por Gregor Hohpe: El concepto central de enrutamiento de mensajes basado en datos.

</details>

<details>
<summary><strong>Message Filter:</strong> Evalúa un mensaje basándose en criterios específicos y lo elimina del canal si no cumple con los requisitos.</summary>

Un mecanismo de enrutamiento protector que evita que los componentes aguas abajo se vean abrumados por datos irrelevantes. El filtro inspecciona cada mensaje; si coincide con los criterios, pasa al canal de salida. Si no, se descarta silenciosamente. Se utiliza mucho en la agregación de logs y sistemas de seguridad.

- **Ejemplos:**
  - [fail2ban/fail2ban](https://github.com/fail2ban/fail2ban): Analiza flujos de archivos de registro del servidor, descartando el tráfico normal y actuando solo sobre las líneas que indican fallos de autenticación maliciosos.
  - [pi-hole/pi-hole](https://github.com/pi-hole/pi-hole): Funciona como un filtro de mensajes para solicitudes DNS, descartando las consultas que coinciden con dominios de publicidad conocidos.
- **Recursos:**
  - [Message Filter](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Filter.html) por Gregor Hohpe: Definición del patrón para eliminar mensajes no deseados de un flujo.

</details>

<details>
<summary><strong>Recipient List:</strong> Inspecciona un mensaje entrante y lo reenvía a una lista de destinatarios determinada dinámicamente.</summary>

Un patrón de difusión inteligente. A diferencia de un canal pub/sub estándar, una Lista de Destinatarios calcula dinámicamente quién debe recibir el mensaje en tiempo de ejecución basándose en el contenido o el estado externo. Es un mecanismo de dispersión-reunión (scatter-gather) dirigido, utilizado en sistemas de notificación complejos.

- **Ejemplos:**
  - [novuhq/novu](https://github.com/novuhq/novu): Implementa el patrón de Lista de Destinatarios tomando un único disparador (como "restablecer contraseña") y calculando los canales de entrega correctos (email, SMS, push) según las preferencias del usuario.
- **Recursos:**
  - [Recipient List](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RecipientList.html) por Gregor Hohpe: Teoría arquitectónica detrás de la difusión dinámica y selectiva.

</details>

<details>
<summary><strong>Splitter:</strong> Divide un único mensaje compuesto en múltiples mensajes individuales para que puedan procesarse de forma independiente.</summary>

Un patrón estructural utilizado para paralelizar el trabajo. Cuando un sistema recibe una carga útil grande (como un pedido con docenas de artículos), el Divisor la descompone en unidades atómicas y publica cada una como un mensaje separado, permitiendo que múltiples trabajadores procesen las partes simultáneamente.

- **Ejemplos:**
  - [airbytehq/airbyte](https://github.com/airbytehq/airbyte): Toma respuestas de API voluminosas y las divide en mensajes individuales para su procesamiento y normalización independiente.
- **Recursos:**
  - [Splitter Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Sequencer.html) por Gregor Hohpe: Lógica central para descomponer cargas útiles compuestas.

</details>

<details>
<summary><strong>Aggregator:</strong> Recopila y combina múltiples mensajes relacionados más pequeños en un único mensaje detallado.</summary>

El inverso funcional del Divisor. Es un patrón con estado que almacena mensajes hasta que se cumple una condición (como recibir todos los artículos de un pedido). Una vez activada, compila los mensajes en una única carga útil unificada. Se utiliza para agrupar escrituras en base de datos o compilar respuestas de múltiples APIs.

- **Ejemplos:**
  - [prometheus/prometheus](https://github.com/prometheus/prometheus): Ingiere miles de métricas individuales, almacenándolas y comprimiéndolas en bloques eficientes antes de escribirlas en disco.
  - [getsentry/sentry](https://github.com/getsentry/sentry): Agrupa miles de mensajes de error idénticos en un único "Asunto" coherente en el panel del usuario.
- **Recursos:**
  - [Aggregator Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Aggregator.html) por Gregor Hohpe: Gestión del estado e IDs de correlación.

</details>

<details>
<summary><strong>Resequencer:</strong> Almacena mensajes desordenados y los publica aguas abajo en el orden original correcto.</summary>

Un búfer con estado utilizado para corregir problemas temporales en sistemas distribuidos. Retiene temporalmente los mensajes que llegan fuera de secuencia, inspecciona un ID o marca de tiempo y los libera hacia el destino estrictamente en su secuencia cronológica prevista.

- **Ejemplos:**
  - [jitsi/jitsi-videobridge](https://github.com/jitsi/jitsi-videobridge): Utiliza búferes de reordenación para capturar paquetes de vídeo UDP fragmentados y volver a ponerlos en el orden correcto antes de renderizar el vídeo.
- **Recursos:**
  - [Resequencer Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Resequencer.html) por Gregor Hohpe: Teoría de la gestión de brechas de secuencia y almacenamiento en búfer.

</details>

<details>
<summary><strong>Routing Slip:</strong> Adjunta instrucciones de enrutamiento directamente al mensaje para que sepa a dónde ir a continuación sin un orquestador central.</summary>

Un patrón de orquestación distribuida donde el itinerario viaja con los datos. El remitente adjunta una lista de pasos necesarios (la "hoja"). Al terminar una tarea, el trabajador inspecciona la hoja, determina el siguiente destino y lo reenvía directamente, eliminando el cuello de botella de un orquestador central.

- **Ejemplos:**
  - [Netflix/conductor](https://github.com/Netflix/conductor): Su modelo de ejecución imita el paradigma de la Hoja de Enrutamiento, donde el estado de enrutamiento secuencial se pasa con las tareas para que los trabajadores sepan su posición en el flujo.
- **Recursos:**
  - [Routing Slip Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RoutingTable.html) por Gregor Hohpe: Desacoplamiento de la orquestación del flujo de trabajo.

</details>

<details>
<summary><strong>Throttler:</strong> Restringe la tasa a la que los mensajes pasan a un receptor para evitar que se sobrecargue.</summary>

Un mecanismo de control de tráfico que impone Acuerdos de Nivel de Servicio (SLAs). Si los mensajes llegan en ráfagas, el Limitador los almacena y los libera a una tasa controlada (por ejemplo, 50 mensajes por segundo) para proteger sistemas frágiles.

- **Ejemplos:**
  - [discourse/discourse](https://github.com/discourse/discourse): Implementa limitadores de tasa nativos para restringir la rapidez de publicación de mensajes, protegiendo la base de datos Postgres de picos de tráfico.
- **Recursos:**
  - [Throttling pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/throttling) por Microsoft Azure: Directrices para implementar limitación de tasa y estrangulamiento.

</details>

<details>
<summary><strong>Load Balancer:</strong> Distribuye los mensajes entrantes entre múltiples instancias de receptor para optimizar recursos y rendimiento.</summary>

Mecanismo central para el escalado horizontal. Intercepta el tráfico y lo divide algorítmicamente (ej. Round Robin) entre un grupo de trabajadores idénticos. Si uno falla, el balanceador deja de enrutar tráfico hacia él, manteniendo la alta disponibilidad.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* Un Balanceador de Carga es un componente de infraestructura (como HAProxy o Nginx). Las aplicaciones se despliegan detrás de ellos.
    - [terraform-google-modules/terraform-google-lb](https://github.com/terraform-google-modules/terraform-google-lb): Módulo oficial de Terraform para configurar Balanceadores de Carga en Google Cloud.
- **Recursos:**
  - [What is Load Balancing?](https://www.cloudflare.com/learning/performance/what-is-load-balancing/) por Cloudflare: Desglose de algoritmos de equilibrio en las capas 4 y 7.

</details>


### Patrones de Transformación de Mensajes

Pasos intermediarios que alteran o estandarizan la carga útil para desacoplar el formato del remitente de las expectativas del receptor.

<details>
<summary><strong>Envelope Wrapper:</strong> Envuelve los datos dentro de un sobre estandarizado sin alterar la carga útil original.</summary>

Encapsula datos brutos dentro de una estructura de metadatos (el sobre) requerida por la infraestructura (como encabezados o IDs de correlación). Permite que la capa de transporte enrute el mensaje sin necesidad de comprender o alterar los datos de negocio internos.

- **Ejemplos:**
  - [matrix-org/synapse](https://github.com/matrix-org/synapse): Utiliza sobres para encapsular cargas útiles de chat cifradas de extremo a extremo dentro de estructuras JSON de federación estandarizadas.
  - [letsencrypt/boulder](https://github.com/letsencrypt/boulder): Envuelve solicitudes de firma de certificados dentro de sobres JWS (JSON Web Signature) para transporte seguro y verificación.
- **Recursos:**
  - [Envelope Wrapper](https://www.enterpriseintegrationpatterns.com/patterns/messaging/EnvelopeWrapper.html) por Gregor Hohpe: Definición del patrón para encapsular datos.

</details>

<details>
<summary><strong>Content Enricher:</strong> Accede a fuentes externas para añadir información faltante a un mensaje antes de enviarlo.</summary>

Se utiliza cuando un sistema de origen produce datos incompletos. Un componente intermediario consulta una base de datos o API externa para recuperar el contexto faltante (ej. obtener el perfil completo desde un `user_id`), lo adjunta al mensaje y lo reenvía al destino.

- **Ejemplos:**
  - [getsentry/sentry](https://github.com/getsentry/sentry): Intercepta registros de fallos brutos y les adjunta el contexto del usuario, ubicación geográfica y versión del despliegue consultando bases de datos internas.
  - [matomo-org/matomo](https://github.com/matomo-org/matomo): Enriquece los datos de visitas HTTP consultando bases de datos de geolocalización de IPs antes de guardar el registro analítico.
- **Recursos:**
  - [Content Enricher](https://www.enterpriseintegrationpatterns.com/patterns/messaging/DataEnricher.html) por Gregor Hohpe: Teoría arquitectónica de la interceptación y el adjunto de datos.

</details>

<details>
<summary><strong>Content Filter:</strong> Elimina datos innecesarios o sensibles de un mensaje para simplificarlo o mejorar la seguridad.</summary>

El inverso del Enriquecedor. Elimina campos de datos específicos antes de enrutar el mensaje. Se utiliza para minimizar datos (ahorro de ancho de banda) o sanear información sensible (PII) antes de enviar datos a servicios externos.

- **Ejemplos:**
  - [getsentry/sentry](https://github.com/getsentry/sentry): Emplea "Data Scrubbing" para eliminar números de tarjetas y contraseñas de los mensajes de error entrantes.
  - [nextcloud/server](https://github.com/nextcloud/server): Elimina IDs internos y rutas de servidor absolutas de las respuestas de API antes de servirlas a clientes externos.
- **Recursos:**
  - [Content Filter](https://www.enterpriseintegrationpatterns.com/patterns/messaging/ContentFilter.html) por Gregor Hohpe: Simplificación y aseguramiento de cargas útiles.

</details>

<details>
<summary><strong>Claim Check:</strong> Almacena cargas útiles grandes en una base de datos y pasa solo un identificador ligero a través del bus de mensajería.</summary>

Evita que los brokers de mensajes se saturen con archivos grandes (vídeos, imágenes). El remitente carga el archivo pesado en un almacén (ej. AWS S3) y envía solo un ID único (el claim check) por la cola. El receptor usa ese ID para descargar la carga útil directamente.

- **Ejemplos:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Cuando un usuario sube un vídeo, se guarda en la nube y solo el ID ligero pasa a las colas de Redis para que los trabajadores de transcodificación lo procesen.
- **Recursos:**
  - [Claim Check Pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/claim-check) por Microsoft Azure: Directrices para evitar el estrangulamiento del bus de mensajes.

</details>

<details>
<summary><strong>Normalizer:</strong> Convierte mensajes de formatos dispares en un único formato unificado para el destino.</summary>

Esencial para integrar sistemas que hablan diferentes lenguajes. Un Normalizador identifica el formato entrante (XML, JSON, CSV) y lo traduce a un modelo de datos canónico estandarizado que la aplicación de destino pueda procesar.

- **Ejemplos:**
  - [airbytehq/airbyte](https://github.com/airbytehq/airbyte): Se conecta a cientos de APIs y normaliza sus esquemas dispares en un formato JSON estandarizado para almacenes de datos.
  - [huginn/huginn](https://github.com/huginn/huginn): Extrae datos de sitios web y APIs, mapeándolos a un formato de evento interno estándar.
- **Recursos:**
  - [Normalizer](https://www.enterpriseintegrationpatterns.com/patterns/messaging/Normalizer.html) por Gregor Hohpe: Conversión de datos dispares en formatos canónicos.

</details>


### Patrones de Puntos de Conexión de Mensajería

Interfaces que conectan el código interno con el sistema de mensajería externo, dictando cómo se envían y reciben los datos.

<details>
<summary><strong>Polling Consumer:</strong> Verifica activamente un canal a intervalos específicos para extraer mensajes.</summary>

El cliente verifica proactivamente el canal para recuperar mensajes. Da al consumidor control total sobre su tasa de ingestión, evitando que se vea abrumado, aunque introduce latencia y gasta ciclos de CPU si la cola está vacía.

- **Ejemplos:**
  - [discourse/discourse](https://github.com/discourse/discourse): Utiliza el framework Sidekiq para sondear colas de Redis en busca de tareas asíncronas como el envío de correos o procesamiento de medallas.
- **Recursos:**
  - [Polling Consumer Pattern](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PollingConsumer.html) por Gregor Hohpe: Compromisos entre sondeo y consumo dirigido por eventos.

</details>

<details>
<summary><strong>Event-Driven Consumer:</strong> Reacciona automáticamente en el momento en que se le entrega un mensaje (modelo push).</summary>

Un cliente basado en empuje que permanece inactivo hasta que el broker le entrega un mensaje. Permite procesamiento en tiempo real y es eficiente en recursos, pero requiere que el consumidor soporte ráfagas impredecibles de tráfico.

- **Ejemplos:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Sus endpoints reaccionan instantáneamente cuando un sistema externo (como GitHub) les empuja una carga útil de evento vía webhook.
- **Recursos:**
  - [Event-Driven Consumer](https://www.enterpriseintegrationpatterns.com/patterns/messaging/EventDrivenConsumer.html) por Gregor Hohpe: Teoría central de los puntos de conexión reactivos.

</details>

<details>
<summary><strong>Competing Consumers:</strong> Múltiples consumidores extraen de un único canal para permitir el procesamiento concurrente y escalado.</summary>

Múltiples instancias idénticas escuchan el mismo canal punto a punto. El canal garantiza que cada mensaje se entregue a solo un consumidor. Es el patrón principal para escalar horizontalmente las cargas de trabajo en segundo plano.

- **Ejemplos:**
  - [getsentry/sentry](https://github.com/getsentry/sentry): Despliega flotas de trabajadores Celery que extraen de las mismas colas centralizadas para procesar miles de errores en paralelo sin duplicar trabajo.
- **Recursos:**
  - [Competing Consumers Pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/competing-consumers) por Microsoft Azure: Implementación de grupos de trabajadores escalables.

</details>

<details>
<summary><strong>Message Dispatcher:</strong> Consume mensajes de un canal y los distribuye a varios hilos de trabajo o puntos de conexión.</summary>

Un coordinador que consume de un canal y delega a hilos de trabajo internos según la carga o prioridad. Mantiene centralizada la lógica de lectura mientras distribuye la ejecución de los procesos.

- **Ejemplos:**
  - [gitlabhq/gitlab-runner](https://github.com/gitlabhq/gitlab-runner): Consume trabajos de tubería (pipeline) de CI/CD pendientes de la instancia central y los distribuye a ejecutores localizados específicos (Docker, Kubernetes).
- **Recursos:**
  - [Message Dispatcher](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageDispatcher.html) por Gregor Hohpe: Desacoplamiento de la ingestión del procesamiento.

</details>

<details>
<summary><strong>Selective Consumer:</strong> El propio consumidor elige ignorar los mensajes del canal que no cumplen sus criterios específicos.</summary>

Un consumidor que se conecta a un canal compartido pero configura un filtro (ej. selectores SQL) para que el broker solo le entregue mensajes que coincidan, evitando desperdiciar recursos del cliente con datos irrelevantes.

- **Ejemplos:**
  - [home-assistant/core](https://github.com/home-assistant/core): Los scripts de automatización se registran en el bus de eventos central pero solo se activan ante cambios de estado de dispositivos específicos.
- **Recursos:**
  - [Selective Consumer](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageSelector.html) por Gregor Hohpe: Uso de selectores para filtar a nivel de punto de conexión.

</details>

<details>
<summary><strong>Durable Subscriber:</strong> Garantiza que un suscriptor reciba todos los mensajes, guardándolos incluso si este se desconecta temporalmente.</summary>

Cuando un suscriptor estándar se desconecta, pierde mensajes nuevos. Un Suscriptor Duradero registra su identidad ante el broker, que almacena los mensajes durante la inactividad y los entrega al momento de la reconexión.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* Es una característica de infraestructura (sesiones persistentes MQTT o Kafka).
    - [mqttjs/MQTT.js](https://github.com/mqttjs/MQTT.js): Demuestra cómo configurar sesiones persistentes en las opciones de conexión.
- **Resources:**
  - [Durable Subscriber](https://www.enterpriseintegrationpatterns.com/patterns/messaging/DurableSubscription.html) por Gregor Hohpe: Gestión de sesiones en arquitecturas pub/sub.

</details>

<details>
<summary><strong>Idempotent Receiver:</strong> Maneja de forma segura mensajes duplicados garantizando que procesarlos múltiples veces produzca el mismo resultado que una sola vez.</summary>

Gestiona las entregas "Al Menos Una Vez" donde los reintentos pueden duplicar mensajes. El receptor rastrea IDs únicos para evitar efectos secundarios no deseados en el estado de la aplicación.

- **Ejemplos:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): Implementa idempotencia en sus participantes de saga para evitar cobros dobles si un mensaje de pago llega dos veces por fallos de red.
- **Recursos:**
  - [Idempotent Receiver](https://www.enterpriseintegrationpatterns.com/patterns/messaging/IdempotentReceiver.html) por Gregor Hohpe: Necesidad de la idempotencia en arquitecturas distribuidas.

</details>

<details>
<summary><strong>Transactional Client:</strong> Agrupa múltiples envíos y recepciones en una única transacción atómica (todo o nada).</summary>

Un punto de conexión que agrupa actualizaciones de base de datos y publicación de mensajes. Si falla uno, se revierte todo, evitando inconsistencias donde se guarda un cambio pero el sistema distribuido no es notificado.

- **Ejemplos:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): Implementa el patrón Transactional Outbox, asegurando que guardar un pedido y publicar el evento "OrderCreated" sea una única operación atómica.
- **Recursos:**
  - [Transactional Client](https://www.enterpriseintegrationpatterns.com/patterns/messaging/TransactionalClient.html) por Gregor Hohpe: Atomicidad entre almacenes de datos y brokers.

</details>


### Patrones de API Gateway

Capas que gestionan cómo los clientes externos interactúan con microservicios internos.

<details>
<summary><strong>API Gateway:</strong> Punto de entrada unificado que gestiona enrutamiento, composición y seguridad para servicios internos.</summary>

Los clientes llaman a un endpoint central en lugar de a docenas de microservicios. El gateway maneja autenticación, limitación de tasa y oculta la estructura interna, simplificando el código del cliente.

- **Ejemplos:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Utiliza un servicio `frontend` como API Gateway unificado, protegiendo al navegador de necesitar conocer las IPs de los servicios internos de pago o carrito.
- **Recursos:**
  - [API Gateway Pattern](https://microservices.io/patterns/apigateway.html) por Chris Richardson: Papel del gateway en arquitecturas distribuidas.

</details>

<details>
<summary><strong>Backends for Frontends (BFF):</strong> Gateways personalizados para diferentes tipos de clientes (ej. uno para móvil, otro para web).</summary>

Variación donde, en lugar de un gateway monolítico, se usan gateways a medida. El BFF Móvil devuelve JSON optimizado para bajo ancho de banda, mientras que el BFF Web devuelve datos detallados, evitando cuellos de botella.

- **Ejemplos:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Implementa servicios por separado como `Web.BFF.Shopping` y `Mobile.BFF.Shopping` para servir a sus distintas aplicaciones.
- **Recursos:**
  - [Pattern: Backends For Frontends](https://samnewman.io/patterns/architectural/bff/) por Sam Newman: Artículo original sobre la división arquitectónica.

</details>

<details>
<summary><strong>Gateway Aggregation:</strong> El gateway dispersa una solicitud a múltiples servicios internos y combina sus respuestas para el cliente.</summary>

Reduce la latencia entre cliente y backend. En lugar de realizar múltiples llamadas HTTP lentas, el cliente hace una al Gateway. Este llama a los microservicios aguas abajo en paralelo, une las respuestas y devuelve una carga útil agregada.

- **Ejemplos:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): Su gateway implementa un `OrderDetailsAggregator` que obtiene datos de Pedido, Cocina y Contabilidad de forma concurrente.
  - [dotnet/eShop](https://github.com/dotnet/eShop): Usa un `HttpAggregator` que compila el estado de la cesta, inventario y precios en una sola respuesta.
- **Recursos:**
  - [Gateway Aggregation pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/gateway-aggregation) por Microsoft Azure: Agregación scatter-gather en el borde.

</details>

<details>
<summary><strong>Gateway Routing:</strong> Mapea rutas de solicitud externa a servicios de backend específicos de forma invisible para el llamador.</summary>

Funciona como un proxy inverso inteligente. El cliente pide una dirección genérica (ej. `/api/pedidos`) y el Gateway inspecciona la ruta y el método para reenviar la solicitud al puerto y servicio interno correcto, ocultando la topología de red.

- **Ejemplos:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): El servicio `frontend` intercepta rutas como `/cart` y las pasa al Servicio de Carrito sin que el navegador sepa que son aplicaciones distintas.
- **Recursos:**
  - [Gateway Routing pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/gateway-routing) por Microsoft Azure: Mapeo de endpoints externos a servicios internos.

</details>


### Patrones de Resiliencia

Tácticas defensivas que protegen los sistemas de fallos en cascada y agotamiento de recursos.

<details>
<summary><strong>Circuit Breaker:</strong> Evita reintentar operaciones fallidas "disparándose" (abriendo el circuito) para dar tiempo al servicio a recuperarse.</summary>

Cuando un servicio empieza a fallar, el disyuntor abre el circuito tras un umbral de errores. Durante un periodo, cualquier llamada devuelve un error instantáneo de reserva sin intentar la red, evitando bloquear hilos y permitiendo la recuperación del destino.

- **Ejemplos:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Utiliza la biblioteca Polly para envolver llamadas HTTP en Disyuntores. Si el servicio de Catálogo cae, el frontal dispara el circuito en lugar de congelarse esperando el tiempo de espera.
- **Recursos:**
  - [CircuitBreaker](https://martinfowler.com/bliki/CircuitBreaker.html) por Martin Fowler: Estados cerrado, abierto y semi-abierto.

</details>

<details>
<summary><strong>Bulkhead:</strong> Particiona recursos (como hilos o memoria) para que un fallo en un componente no consuma todo el sistema.</summary>

Divide recursos críticos dedicados a componentes específicos. Al asignar límites estrictos a grupos de conexiones o hilos por tarea, el sistema mantiene la función B incluso si la función A sufre un pico de tráfico o falla.

- **Ejemplos:**
  - [elastic/elasticsearch](https://github.com/elastic/elasticsearch): Mantiene grupos de hilos separados para búsquedas e indexación, garantizando que un pico de ingestión no detenga las consultas de los usuarios.
- **Recursos:**
  - [Bulkhead pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/bulkhead) por Microsoft Azure: Aislamiento de recursos.

</details>

<details>
<summary><strong>Retry with Exponential Backoff:</strong> Reintenta automáticamente fallos transitorios esperando progresivamente más tiempo entre intentos.</summary>

Mecanismo de auto-curación para redes distribuidas. En lugar de reintentar en bucle (DoS auto-infligido), espera tiempos crecientes (ej. 1s, 2s, 4s). Suele incluir "jitter" (retrasos aleatorios) para evitar tormentas de reintentos masivos.

- **Ejemplos:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Su modelo de federación reintenta la entrega de publicaciones con retroceso exponencial si un servidor remoto está desconectado.
- **Recursos:**
  - [Exponential Backoff And Jitter](https://aws.amazon.com/blogs/architecture/exponential-backoff-and-jitter/) por AWS: Por qué el jitter es necesario.

</details>

<details>
<summary><strong>Rate Limiting / Throttling:</strong> Restringe el número de solicitudes por cliente para proteger la disponibilidad del servicio.</summary>

Rastrea el volumen de tráfico de IPs o cuentas. Si se excede la cuota, rechaza solicitudes (error 429) hasta el siguiente ciclo. Crítico para evitar agotamiento de recursos y mitigar ataques de fuerza bruta.

- **Ejemplos:**
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Incluye middleware nativo de limitación para evitar que bots saturen el servidor con solicitudes de clonación.
- **Recursos:**
  - [Rate Limiting pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/rate-limiting) por Microsoft Azure.

</details>

<details>
<summary><strong>Timeout Management:</strong> Establece límites de tiempo estrictos abortando operaciones que tardan demasiado para liberar recursos.</summary>

Debido a que un servidor podría nunca responder, el cliente debe definir un tiempo máximo de espera. Al expirar, corta la conexión y libera su hilo, evitando fallos en cascada por hilos bloqueados infinitamente.

- **Ejemplos:**
  - [prometheus/prometheus](https://github.com/prometheus/prometheus): Aborta extracciones HTTP que tardan demasiado, garantizando que servidores congelados no detengan el ciclo de recolección global.
- **Recursos:**
  - [Understanding API Timeouts](https://cloud.google.com/blog/products/api-management/understanding-api-timeouts) por Google Cloud.

</details>

<details>
<summary><strong>Graceful Degradation:</strong> Permite que un sistema funcione con menos funciones o datos antiguos en lugar de fallar totalmente si cae una dependencia.</summary>

Prioriza la disponibilidad parcial. Si falla una dependencia no crítica, sirve una respuesta de reserva (ej. datos cacheados). Esto mantiene el flujo principal del usuario incluso si faltan funciones auxiliares.

- **Ejemplos:**
  - [GoogleCloudPlatform/microservices-demo](https://github.com/GoogleCloudPlatform/microservices-demo): Si falla el servicio de recomendaciones, el frontal muestra una lista por defecto, permitiendo al usuario seguir comprando.
- **Recursos:**
  - [Graceful Degradation](https://en.wikipedia.org/wiki/Fault_tolerance#Graceful_degradation).

</details>

<details>
<summary><strong>Health Check Endpoint:</strong> Expone una ruta (ej. /healthz) para que monitores verifiquen el estado y la conectividad de un servicio.</summary>

Los orquestadores (Kubernetes) consultan esta ruta. El endpoint verifica conexiones a bases de datos y memoria, respondiendo 200 OK si todo es correcto. Si falla, el tráfico se redirige fuera de esa instancia.

- **Ejemplos:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Implementa rutas de verificación en cada servicio para que el clúster de Kubernetes gestione sus ciclos de vida.
- **Recursos:**
  - [Health Endpoint Monitoring pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/health-endpoint-monitoring) por Microsoft Azure.

</details>


### Patrones de Saga

Estrategias para gestionar transacciones distribuidas sin confirmaciones en dos fases.

<details>
<summary><strong>Choreographed Saga:</strong> Modelo descentralizado donde cada servicio publica eventos que disparan transacciones en otros, sin controlador central.</summary>

Funciona como una carrera de relevos. Al terminar una tarea, el servicio publica un evento. Otros suscritos lo escuchan y actúan. Si uno falla, publica un evento de retroceso que indica a los anteriores que ejecuten rollbacks (compensa la transacción anterior).

- **Ejemplos:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Usa sagas coreografiadas para el pago; servicios de Cesta, Catálogo y Pagos escuchan eventos e interactúan sin gestor central.
- **Recursos:**
  - [Pattern: Saga Choreography](https://microservices.io/patterns/data/saga.html#example-choreography-based-saga) por Chris Richardson.

</details>

<details>
<summary><strong>Orchestrated Saga:</strong> Modelo centralizado donde un coordinador indica a los servicios qué transacciones o rollbacks ejecutar.</summary>

Un "Orquestador de Saga" central mantiene la máquina de estados. Envía comandos y decide el siguiente paso según las respuestas. Si hay fallos, dispara los rollbacks en los servicios previos de forma explícita. Ofrece mejor visibilidad pero centraliza la lógica.

- **Ejemplos:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): Implementa un orquestador que coordina microservicios de Cocina y Contabilidad para crear pedidos.
  - [berndruecker/trip-booking-saga-java](https://github.com/berndruecker/trip-booking-saga-java): Demuestra reservas de viaje complejas usando un motor (Camunda) para gestionar el estado.
- **Recursos:**
  - [Pattern: Saga Orchestration](https://microservices.io/patterns/data/saga.html#example-orchestration-based-saga) por Chris Richardson.

</details>


### Patrones de Streaming

Manejo de flujos de datos continuos y cambios de base de datos en tiempo real.

<details>
<summary><strong>Change Data Capture (CDC):</strong> Captura automáticamente cambios en bases de datos (insert, update) y los entrega como flujos de eventos.</summary>

Convierte una base de datos estática en una fuente de eventos. En lugar de sondeo, CDC difunde cada cambio de fila de inmediato, manteniendo sincronizados cachés e índices de búsqueda en tiempo casi real.

- **Ejemplos:**
  - [airbytehq/airbyte](https://github.com/airbytehq/airbyte): Depende de CDC para sincronizar datos capturando cambios incrementales desde bases de datos de producción a almacenes de datos.
- **Recursos:**
  - [What is Change Data Capture?](https://www.redhat.com/en/topics/integration/what-is-change-data-capture) por Red Hat.

</details>

<details>
<summary><strong>Event Streaming Platform:</strong> Usa un registro de solo anexión para almacenar y procesar grandes flujos de registros de forma duradera.</summary>

Arquitectura centrada en el log inmutable. A diferencia de los brokers clásicos, persiste los eventos, permitiendo que múltiples aplicaciones los "reproduzcan" desde cualquier punto, habilitando analíticas históricas y abastecimiento de eventos.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* Se basa en infraestructura como Apache Kafka o Redpanda.
    - [redpanda-data/redpanda-examples](https://github.com/redpanda-data/redpanda-examples).
- **Recursos:**
  - [What is Event Streaming?](https://www.confluent.io/learn/event-streaming/) por Confluent.

</details>

<details>
<summary><strong>Log-Based CDC:</strong> CDC eficiente que lee directamente del registro de transacciones de la base de datos sin afectar su rendimiento.</summary>

Lee del disco el log interno (binlog o WAL). Permite capturar cambios con sobrecarga nula en el motor de ejecución, incluyendo actualizaciones de esquema y eliminaciones.

- **Ejemplos:**
  - [debezium/debezium](https://github.com/debezium/debezium): El estándar para Log-Based CDC que "sigue" logs de MySQL, Postgres y MongoDB.
- **Recursos:**
  - [Log-Based Change Data Capture](https://www.qlik.com/us/change-data-capture/log-based-cdc) por Qlik.

</details>


### Patrones de Gestión del Sistema

Herramientas para monitorear, auditar y depurar flujos asíncronos.

<details>
<summary><strong>Wire Tap:</strong> Duplica silenciosamente los mensajes a un canal secundario para inspección sin afectar el flujo principal.</summary>

Un patrón de observabilidad no intrusivo. Intercepta el mensaje, crea una réplica y la envía a un canal de diagnóstico mientras el original sigue su curso instantáneamente hacia el destino, permitiendo depurar en vivo sin añadir latencia.

- **Ejemplos:**
  - *Nota sobre Ejemplos:* Configuración de infraestructura (malla de servicios o Nginx).
    - [istio/istio](https://github.com/istio/istio/tree/master/samples/httpbin): Demuestra el espejado de tráfico (Wire Tap) en una malla de servicios.
- **Recursos:**
  - [Wire Tap](https://www.enterpriseintegrationpatterns.com/patterns/messaging/WireTap.html) por Gregor Hohpe.

</details>

<details>
<summary><strong>Message History:</strong> Adjunta una lista de los componentes por los que ha pasado un mensaje a sus encabezados para rastreo.</summary>

Convierte al mensaje en su propio registro. Cada componente "sella" su identidad al paso del mensaje, permitiendo reconstruir la ruta exacta en sistemas complejos para identificar dónde ocurrió un fallo.

- **Ejemplos:**
  - [jaegertracing/jaeger](https://github.com/jaegertracing/jaeger): Implementa rastreo distribuido propagando encabezados de contexto a través de microservicios.
- **Recursos:**
  - [Message History](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageHistory.html) por Gregor Hohpe.

</details>

<details>
<summary><strong>Message Log:</strong> Registra los detalles inmutables de cada mensaje para auditorías profundas y reproducción histórica.</summary>

Captura el mensaje bruto completo (encabezados y carga útil). Esencial en sistemas financieros y cumplimiento normativo, donde se necesita ver qué disparó un estado específico meses después.

- **Ejemplos:**
  - [tryghost/ghost](https://github.com/tryghost/ghost): Mantiene un "Activity Log" que captura los metadatos de cada solicitud de API para auditoría.
- **Recursos:**
  - [Message Store](https://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageStore.html) por Gregor Hohpe.

</details>


### Patrones de Integración de Bases de Datos y Dominios

Sincronizan transacciones de base de datos con mensajería y límites de dominio.

<details>
<summary><strong>Transactional Outbox Pattern:</strong> Resuelve la doble escritura guardando cambios y eventos en una misma transacción ACID antes de publicarlos.</summary>

Actualizar base de datos y broker no es atómico. Este patrón crea una tabla "Outbox" en la propia base de datos de negocio. Se guarda el cambio y el evento en la misma transacción; un proceso externo lee luego la tabla y publica el mensaje de forma fiable.

- **Ejemplos:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): Implementa Transactional Outbox usando un relevo para enviar eventos desde MySQL.
- **Recursos:**
  - [Pattern: Transactional outbox](https://microservices.io/patterns/data/transactional-outbox.html) por Chris Richardson.

</details>

<details>
<summary><strong>Anti-Corruption Layer (ACL):</strong> Coloca una capa de traducción entre sistemas para evitar que modelos heredados contaminen el nuevo dominio.</summary>

Protege la integridad del sistema moderno al interactuar con APIs o sistemas legados. El ACL traduce bidireccionalmente: convierte solicitudes del modelo limpio al formato heredado y viceversa, evitando que la deuda técnica se filtre en la nueva base de código.

- **Ejemplos:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): Usa adaptadores que actúan como ACLs aislando el dominio de APIs externas.
- **Recursos:**
  - [Anti-corruption Layer pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/anti-corruption-layer) por Microsoft Azure.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

## Capa 3: Patrones de Arquitectura de Aplicaciones

Esta capa trata sobre cómo se organiza internamente una única aplicación o servicio. El objetivo principal es mantener la lógica de negocio separada de los frameworks, bases de datos e interfaces de usuario. Patrones como la Arquitectura Limpia o Hexagonal mantienen el código central fácil de probar y hacen posible cambiar una base de datos sin cambiar el funcionamiento de la aplicación.

### Patrones de Arquitectura de Presentación / UI

Dictan cómo se estructuran las interfaces de usuario y su comunicación con la lógica de negocio.

<details>
<summary><strong>Model-View-Controller (MVC):</strong> Separa la interfaz en Modelo (datos), Vista (presentación) y Controlador (lógica).</summary>

Desacopla la representación de datos de la interacción del usuario. El Modelo gestiona reglas de negocio, la Vista muestra la información y el Controlador intercepta la entrada del usuario para actualizar el Modelo.

- **Ejemplos:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Implementación primaria de MVC usando Ruby on Rails.
  - [moodle/moodle](https://github.com/moodle/moodle): Gestiona datos complejos de cursos mediante arquitectura MVC.
- **Recursos:**
  - [GUI Architectures](https://martinfowler.com/eaaDev/uiArchs.html) por Martin Fowler.

</details>

<details>
<summary><strong>Model-View-Presenter (MVP):</strong> El Presentador maneja toda la lógica de la UI, dejando a la Vista como pasiva.</summary>

Derivación de MVC donde el Presentador es el intermediario total; la Vista no escucha al Modelo. Mejora la testabilidad al aislar la lógica de UI de los frameworks gráficos.

- **Ejemplos:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Usó MVP para aislar lógica de cifrado del código de UI del sistema operativo.
- **Recursos:**
  - [Model-View-Presenter](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93presenter).

</details>

<details>
<summary><strong>Model-View-ViewModel (MVVM):</strong> Admite el enlace de datos bidireccional (two-way binding) entre Vista y Modelo de Vista.</summary>

El Modelo de Vista provee un modelo especializado para la Vista. Mediante el enlace bidireccional, los cambios en UI actualizan el Modelo de Vista automáticamente sin manipulación manual del DOM o widgets.

- **Ejemplos:**
  - [kiwix/kiwix-android](https://github.com/kiwix/kiwix-android): Implementa MVVM para enlazar el estado de la biblioteca a la interfaz.
- **Recursos:**
  - [WPF Apps With The MVVM Design Pattern](https://learn.microsoft.com/en-us/archive/msdn-magazine/2009/february/patterns-wpf-apps-with-the-mvvm-design-pattern).

</details>

<details>
<summary><strong>Flux / Redux Architecture:</strong> Flujo de datos unidireccional y centralizado para aplicaciones cliente.</summary>

Patrón para gestionar el estado en SPAs. Impone un bucle: las Acciones van a un Despachador que actualiza un Almacén (Store), notificando después a la Vista. Permite una depuración predecible.

- **Ejemplos:**
  - [zulip/zulip-mobile](https://github.com/zulip/zulip-mobile): Usa Redux para gestionar la verdad única de mensajes y presencia de usuarios.
- **Recursos:**
  - [Flux Concepts](https://facebookarchive.github.io/flux/docs/in-depth-overview/).

</details>

<details>
<summary><strong>Micro Frontends Architecture:</strong> Descompone una aplicación web en módulos independientes por característica.</summary>

Extiende microservicios al frontend. Una aplicación grande se divide en módulos independientes desarrollados por diferentes equipos e integrados en tiempo de ejecución para una experiencia fluida.

- **Ejemplos:**
  - [openmrs/openmrs-esm-core](https://github.com/openmrs/openmrs-esm-core): Sistema de registros médicos modular basado en micro-frontends.
- **Recursos:**
  - [Micro Frontends](https://martinfowler.com/articles/micro-frontends.html) por Cam Jackson.

</details>


### Patrones de Arquitecturas Centradas en el Dominio / Capas

Definen la macroestructura interna para aislar el dominio central de la infraestructura.

<details>
<summary><strong>Hexagonal Architecture (Ports and Adapters):</strong> Aísla la lógica del dominio central mediante puertos e interfaces.</summary>

Trata la lógica de negocio como el núcleo. La comunicación ocurre por "Puertos" (interfaces) implementados por "Adaptadores" para conectar con bases de datos o APIs, permitiendo cambios técnicos sin tocar el núcleo.

- **Ejemplos:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): Demuestra un aislamiento de dominio estricto en TypeScript.
- **Recursos:**
  - [Hexagonal architecture](https://alistair.cockburn.us/hexagonal-architecture/) por Alistair Cockburn.

</details>

<details>
<summary><strong>Arquitectura de Micro-Frontends:</strong> Descompone una aplicación web en módulos frontend independientes.</summary>

Un patrón organizacional y técnico que extiende los microservicios al frontend. Una aplicación grande se descompone en módulos independientes basados en características, desarrollados y desplegados por diferentes equipos. Estos módulos se integran en tiempo de ejecución para ofrecer una experiencia fluida al usuario.

- **Ejemplos:**
  - [openmrs/openmrs-esm-core](https://github.com/openmrs/openmrs-esm-core): El frontend para el Open Medical Record System (OpenMRS), construido sobre una arquitectura de micro-frontends para permitir una personalización hospitalaria modular.
- **Recursos:**
  - [Micro Frontends](https://martinfowler.com/articles/micro-frontends.html) por Cam Jackson: Una guía técnica sobre estrategias de composición e integración.

</details>

<details>
<summary><strong>Clean Architecture:</strong> Anillos concéntricos donde las dependencias apuntan estrictamente hacia adentro.</summary>

Organiza el código en círculos donde el más interno contiene las Entidades estables y los externos manejan controladores y herramientas, evitando que cambios externos afecten las reglas de negocio.

- **Ejemplos:**
  - [android10/Android-CleanArchitecture](https://github.com/android10/Android-CleanArchitecture): Aplicación de referencia clásica para principios de Arquitectura Limpia en móvil.
  - [ivanpaulovich/clean-architecture-manga](https://github.com/ivanpaulovich/clean-architecture-manga): Una implementación en .NET que sigue reglas estrictas de Arquitectura Limpia para gestionar un sistema de biblioteca.
- **Recursos:**
  - [The Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html) por Robert C. Martin.

</details>

<details>
<summary><strong>Onion Architecture:</strong> Modelo de dominio en el centro apoyado en la Inversión de Dependencia.</summary>

Coloca el Modelo de Dominio en el centro rodeado por servicios de aplicación e infraestructura. El núcleo define las interfaces y las capas externas las implementan, reflejando el negocio más que la tecnología.

- **Ejemplos:**
  - [jasontaylordev/CleanArchitecture](https://github.com/jasontaylordev/CleanArchitecture): Plantilla .NET estándar para estratificado estilo Onion.
- **Recursos:**
  - [The Onion Architecture](https://jeffreypalermo.com/2008/07/the-onion-architecture-part-1/) por Jeffrey Palermo.

</details>


### Patrones de Fuentes de Datos y Objetos-Relacionales

Gestionan la interacción de objetos en memoria con la capa de persistencia.

<details>
<summary><strong>Repository Pattern:</strong> Intermediario que actúa como guardián entre la lógica de dominio y la persistencia.</summary>

Abstracción que simula una colección (Add, Find) para acceder a objetos, ocultando los detalles de recuperación. Facilita la ignorancia de persistencia y simplifica tests unitarios con dobles en memoria.

- **Ejemplos:**
  - [Sairyss/domain-driven-hexagon](https://github.com/Sairyss/domain-driven-hexagon): Cada agregado tiene su Repositorio implementado en infraestructura aislada del dominio.
- **Recursos:**
  - [The Repository Pattern](https://martinfowler.com/eaaCatalog/repository.html) por Martin Fowler.

</details>

<details>
<summary><strong>Active Record:</strong> Objeto que envuelve una fila de base de datos encapsulando datos y persistencia.</summary>

El propio objeto de modelo contiene la lógica para guardarse o actualizarse. Cada instancia corresponde a una fila física, optimizando el desarrollo rápido en aplicaciones CRUD.

- **Ejemplos:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Entidades centrales contienen tanto datos de negocio como lógica de persistencia en Ruby on Rails.
- **Recursos:**
  - [Active Record](https://martinfowler.com/eaaCatalog/activeRecord.html) por Martin Fowler.

</details>


### Patrones de Gestión de Estado y Flujo de Datos

Definen cómo se muta, almacena y propaga el estado de la aplicación.

<details>
<summary><strong>CQRS:</strong> Separa las operaciones de escritura (Commands) de las de lectura (Queries).</summary>

Divide el modelo CRUD. Permite optimizar y escalar los lados de lectura y escritura de forma independiente, esencial en dominios donde la lógica de escritura y los requisitos de lectura difieren.

- **Ejemplos:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): El microservicio de Pedidos separa comandos REST de consultas usando la biblioteca MediatR.
- **Recursos:**
  - [CQRS](https://martinfowler.com/bliki/CQRS.html) por Martin Fowler.

</details>

<details>
<summary><strong>Event Sourcing:</strong> Almacena el estado como una secuencia inmutable de eventos históricos.</summary>

En lugar de guardar el estado actual, registra cada acción. El estado actual se deriva reproduciendo el historial, creando un registro de auditoría fiable y permitiendo reconstrucción temporal del estado.

- **Ejemplos:**
  - [microservices-patterns/ftgo-application](https://github.com/microservices-patterns/ftgo-application): Contabilidad almacena transacciones como secuencia de eventos en lugar de sobrescribir filas.
- **Recursos:**
  - [Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html) por Martin Fowler.

</details>


### Patrones de Concurrencia y Rendimiento

Enfocados en la ejecución de alta velocidad y baja latencia.

<details>
<summary><strong>LMAX Disruptor:</strong> Mensajería entre hilos de alto rendimiento basada en un búfer circular compartido.</summary>

Optimiza el rendimiento extremo mediante estructuras de memoria compartida sin bloqueos pesados de hilos.

- **Ejemplos:**
  - [LMAX-Exchange/disruptor](https://github.com/LMAX-Exchange/disruptor): Repositorio central de la biblioteca Disruptor.
  - [apache/logging-log4j2](https://github.com/apache/logging-log4j2): Usa el Disruptor internamente para registro asíncrono masivo.
- **Recursos:**
  - [The LMAX Disruptor](https://lmax-exchange.github.io/disruptor/).

</details>

<details>
<summary><strong>Software Transactional Memory (STM):</strong> Control de concurrencia basado en transacciones de memoria atómicas.</summary>

Agrupa cambios en memoria compartida. Si hay conflictos, se reintentan automáticamente, eliminando deadlocks y ofreciendo seguridad frente a la gestión manual de bloqueos.

- **Ejemplos:**
  - [metabase/metabase](https://github.com/metabase/metabase): Usa STM nativa para gestionar configuraciones globales seguras entre sesiones concurrentes.
- **Recursos:**
  - [Software Transactional Memory](https://en.wikipedia.org/wiki/Software_transactional_memory).

</details>


### Patrones de Conectividad del Sistema

Manejan la dependencia de la red y la sincronización de datos.

<details>
<summary><strong>Offline-First:</strong> La aplicación opera principalmente contra una base de datos local para respuesta instantánea.</summary>

Escribe en almacenamiento local por defecto. La sincronización en segundo plano concilia datos con el servidor según disponibilidad, manejando resolución de conflictos automáticamente.

- **Ejemplos:**
  - [standardnotes/app](https://github.com/standardnotes/app): Escribe localmente para uso offline fluido y sincroniza cifrado en segundo plano.
- **Recursos:**
  - [Offline First](https://offlinefirst.org/).

</details>

<details>
<summary><strong>Optimistic UI:</strong> Actualiza la interfaz sospechando éxito inmediato antes de la confirmación del servidor.</summary>

Enmascara latencia actualizando la UI al instante. Si la red falla, el estado local se revierte y se notifica al usuario.

- **Ejemplos:**
  - [zulip/zulip-mobile](https://github.com/zulip/zulip-mobile): Muestra mensajes enviados inmediatamente con estado pendiente hasta la confirmación.
- **Recursos:**
  - [True Lies Of Optimistic User Interfaces](https://www.smashingmagazine.com/2016/11/true-lies-of-optimistic-user-interfaces/).

</details>


### Patrones de Arquitectura Móvil

Metodologías para ciclo de vida y enrutamiento en dispositivos móviles.

<details>
<summary><strong>VIPER:</strong> Aísla lógica, UI y enrutamiento en componentes modulares separados.</summary>

Elimina lógica del controlador de vista. La navegación se aísla en el Enrutador y reglas en el Interactor, permitiendo tests unitarios sin interfaz gráfica.

- **Recursos:**
  - [Architecting iOS Apps with VIPER](https://www.objc.io/issues/13-architecture/viper/).

</details>

<details>
<summary><strong>RIBs:</strong> Árbol de lógica de negocio impulsado por estados de navegación independientes de la vista.</summary>

La lógica de negocio funciona de forma autónoma. Un proceso puede existir y enrutar datos incluso si no hay una vista adjunta, ideal para grandes equipos.

- **Recursos:**
  - [RIBs - Uber's cross-platform architecture](https://github.com/uber/RIBs).

</details>


### Patrones de Dobles de Prueba

Objetos para aislar código simulando dependencias en tests automatizados.

<details>
<summary><strong>Stub:</strong> Predefine respuestas fijas a llamadas durante la ejecución de un test.</summary>

Ofrece datos consistentes aislando la prueba de variaciones en APIs externas.

- **Ejemplos:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Simula estados de git para probar UI con operaciones reales de disco.
- **Recursos:**
  - [Mocks Aren't Stubs](https://martinfowler.com/articles/mocksArentStubs.html) por Martin Fowler.

</details>

<details>
<summary><strong>Fake:</strong> Versión funcional pero simplificada (como bases de datos en memoria) para ejecución rápida.</summary>

Se comportan como sistemas reales en tests pero no son aptos para producción por su falta de persistencia real o rendimiento.

- **Ejemplos:**
  - [dotnet/eShop](https://github.com/dotnet/eShop): Usa InMemory database para tests de integración evitando sobrecarga de SQL Server.
- **Recursos:**
  - [Testing with Fakes](https://github.com/google/googletest/blob/main/docs/gmock_cook_book.md#fakes).

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

## Capa 4: Patrones de Diseño de Software

<br>

Son las piezas fundamentales del código: soluciones simples para problemas de programación comunes. Mientras que la arquitectura maneja el diseño de todo el sistema, los patrones de diseño gestionan cómo se construyen y conectan las piezas individuales. Esto cubre configuraciones clásicas de orientación a objetos, programación funcional y patrones para multi-tarea segura.

### Patrones Creacionales

<br>

*Patrones que abstraen el proceso de instanciación, haciendo que un sistema sea independiente de cómo se crean, componen y representan sus objetos*

<details>
<summary><strong>Singleton:</strong> Limita una clase a una sola instancia y ofrece un punto de acceso global a ella.</summary>

Se utiliza para coordinar el estado en toda la aplicación restringiendo una clase a una única instancia. Comúnmente usado para configuraciones globales, grupos de conexiones a bases de datos o gestores de hardware. Aunque es potente para el control centralizado, crea un estado global que puede dificultar las pruebas unitarias si no se gestiona mediante inyección de dependencias.

- **Ejemplos:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Utiliza Singletons para gestores centrales del sistema, como `DatabaseFactory`, proporcionando acceso centralizado al almacenamiento cifrado crítico.
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Emplea Singletons para gestionar configuraciones globales del sistema, ofreciendo una única fuente de verdad para el comportamiento de la aplicación.
- **Recursos:**
  - [Singleton Pattern](https://refactoring.guru/design-patterns/singleton): Análisis técnico de estrategias de implementación por Refactoring Guru.
  - [Singleton Design Pattern](https://sourcemaking.com/design_patterns/singleton): Un análisis de la estructura del patrón y consideraciones de seguridad de hilos por SourceMaking.

</details>

<details>
<summary><strong>Factory Method:</strong> Define una interfaz para crear un objeto, pero deja que las subclases alteren el tipo de objetos creados.</summary>

Proporciona una forma de delegar la lógica de instanciación a clases secundarias. En lugar de que el código principal llame a "new" en una clase específica, llama a un método de fábrica. Esto permite que el sistema permanezca desacoplado de los tipos concretos, facilitando la extensión cuando se añaden nuevos tipos.

- **Ejemplos:**
  - [moodle/moodle](https://github.com/moodle/moodle): Usa métodos de fábrica para instanciar diversos tipos de plugins, permitiendo al motor central gestionar contenido diverso sin conocer sus detalles.
  - [metabase/metabase](https://github.com/metabase/metabase): Emplea métodos de fábrica para crear instancias de controladores de base de datos específicos según la configuración del usuario.
- **Recursos:**
  - [Factory Method](https://refactoring.guru/design-patterns/factory-method): Guía visual sobre el desacoplamiento de creadores y productos por Refactoring Guru.
  - [Factory Method Pattern](https://sourcemaking.com/design_patterns/factory_method): Diagramas UML estructurales y listas de verificación de implementación por SourceMaking.

</details>

<details>
<summary><strong>Abstract Factory:</strong> Define una interfaz para crear familias de objetos relacionados sin especificar sus clases concretas.</summary>

Extensión del patrón Factory que agrupa fábricas relacionadas. Permite que un sistema sea independiente de cómo se crean sus productos. Es especialmente útil cuando un sistema debe configurarse con una de varias familias de productos, como diferentes temas de UI o motores de almacenamiento.

- **Ejemplos:**
  - [tryghost/ghost](https://github.com/tryghost/ghost): Implementa una fábrica abstracta para su capa de almacenamiento, proporcionando objetos para almacenamiento local, S3 u otros proveedores según el entorno.
  - [home-assistant/core](https://github.com/home-assistant/core): Utiliza fábricas abstractas para generar familias de entidades (sensores, luces) para integraciones de hardware específicas.
- **Recursos:**
  - [Abstract Factory](https://refactoring.guru/design-patterns/abstract-factory): Explicación detallada de familias de productos por Refactoring Guru.
  - [Abstract Factory Design Pattern](https://sourcemaking.com/design_patterns/abstract_factory): Una inmersión profunda en la intención y aplicabilidad del patrón por SourceMaking.

</details>

<details>
<summary><strong>Builder:</strong> Separa la construcción de un objeto complejo de su representación.</summary>

Patrón para objetos que requieren muchos pasos o parámetros para inicializarse. En lugar de un constructor con docenas de argumentos, el Builder permite establecer solo los valores necesarios de forma legible y paso a paso antes de producir el objeto final.

- **Ejemplos:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Se basa en el patrón Builder para construir objetos complejos como registros de `Notification` o cargas de `Message`.
  - [getsentry/sentry](https://github.com/getsentry/sentry): Usa builders en su flujo de procesamiento de eventos para ensamblar informes de error complejos a partir de datos de telemetría dispersos.
- **Recursos:**
  - [Builder Pattern](https://refactoring.guru/design-patterns/builder): Ejemplos prácticos de construcción paso a paso por Refactoring Guru.
  - [Builder Design Pattern](https://sourcemaking.com/design_patterns/builder): Una visión general de cómo analizar representaciones complejas por SourceMaking.

</details>

<details>
<summary><strong>Prototype:</strong> Crea nuevos objetos copiando un objeto existente.</summary>

Se utiliza cuando el coste de crear un objeto desde cero es alto o complejo. En lugar de una inicialización completa, el sistema toma una instancia "prototipo" existente y la clona. Común en sistemas con muchos objetos similares que solo difieren en pocos atributos.

- **Ejemplos:**
  - [moodle/moodle](https://github.com/moodle/moodle): Implementa la clonación de prototipos al duplicar cursos o plantillas de actividad, permitiendo crear nuevas estructuras complejas sin repetir toda la lógica de configuración.
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Utiliza patrones de prototipo para la clonación interna de objetos durante el espejado de repositorios.
- **Recursos:**
  - [Prototype Pattern](https://refactoring.guru/design-patterns/prototype): Explicación de clonación profunda y superficial por Refactoring Guru.
  - [Prototype Design Pattern](https://sourcemaking.com/design_patterns/prototype): Una mirada a los beneficios de rendimiento de los registros de prototipos por SourceMaking.

</details>

<details>
<summary><strong>Object Pool Pattern:</strong> Mantiene un conjunto de objetos inicializados y reutilizables para optimizar el rendimiento.</summary>

Patrón de optimización cuando la creación de objetos es costosa (como conexiones a bases de datos). En lugar de destruir los objetos tras su uso, se devuelven a un "pool" para ser reutilizados por la siguiente petición, reduciendo la sobrecarga de asignación frecuente y recolección de basura.

- **Ejemplos:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Gestiona pools eficientes de conexiones a bases de datos para manejar miles de mensajes concurrentes sin la latencia de instanciación repetida.
  - [discourse/discourse](https://github.com/discourse/discourse): Utiliza pools internos para tareas en segundo plano y conexiones de datos, manteniendo un uso de recursos estable.
- **Recursos:**
  - [Object Pool Pattern](https://sourcemaking.com/design_patterns/object_pool): Teoría y ejecución de gestión de recursos mediante pooling.
  - [Object Pool](https://en.wikipedia.org/wiki/Object_pool_pattern): Una visión general de la gestión del ciclo de vida y el tamaño del pool en Wikipedia.

</details>


### Patrones Estructurales

<br>

*Patrones que tratan sobre cómo se componen las clases y objetos para formar estructuras más grandes*

<details>
<summary><strong>Adapter:</strong> Permite que interfaces incompatibles trabajen juntas envolviendo un objeto en un adaptador.</summary>

Funciona como un traductor entre dos interfaces diferentes. Permite que un sistema consuma bibliotecas externas o componentes antiguos sin forzar cambios en el código principal de la aplicación. Evita la contaminación del modelo de dominio al interactuar con APIs de terceros.

- **Ejemplos:**
  - [home-assistant/core](https://github.com/home-assistant/core): Usa adaptadores para que miles de protocolos de hardware distintos se ajusten a un modelo interno estándar de luces, interruptores y sensores.
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Traduce comandos genéricos de archivos adjuntos a las peticiones de API específicas requeridas por proveedores de la nube como S3 o Google Cloud Storage.
- **Recursos:**
  - [Adapter Pattern](https://refactoring.guru/design-patterns/adapter): Resumen técnico de adaptadores de clases y objetos por Refactoring Guru.
  - [Adapter Design Pattern](https://sourcemaking.com/design_patterns/adapter): Una guía para la implementación e intención del patrón por SourceMaking.

</details>

<details>
<summary><strong>Bridge:</strong> Desacopla una abstracción de su implementación para que ambas puedan variar de forma independiente.</summary>

Evita jerarquías de clases gigantescas cuando un componente tiene múltiples dimensiones de variación. En lugar de crear una subclase para cada combinación de características, Bridge extrae una dimensión a una jerarquía separada, permitiendo extender ambas sin afectarse entre sí.

- **Ejemplos:**
  - [metabase/metabase](https://github.com/metabase/metabase): Separa la representación abstracta de una consulta de datos de las implementaciones específicas necesarias para ejecutarla en docenas de motores SQL y NoSQL.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Separa el concepto de "Backend de archivos" de las implementaciones para disco local, S3 o MinIO, permitiendo que la lógica de mensajería sea independiente de la tecnología de almacenamiento.
- **Recursos:**
  - [Bridge Pattern](https://refactoring.guru/design-patterns/bridge): Cómo dividir clases grandes en jerarquías separadas por Refactoring Guru.
  - [Bridge Design Pattern](https://sourcemaking.com/design_patterns/bridge): Un desglose de la composición estructural del patrón por SourceMaking.

</details>

<details>
<summary><strong>Composite:</strong> Compone objetos en estructuras de árbol para representar jerarquías parte-todo, permitiendo tratar objetos individuales y composiciones de forma uniforme.</summary>

Permite que una colección de objetos sea tratada como si fuera una sola instancia. Se usa para construir estructuras jerárquicas, como sistemas de archivos o árboles de componentes de UI, donde un grupo de elementos responde a los mismos comandos que un elemento individual.

- **Ejemplos:**
  - [moodle/moodle](https://github.com/moodle/moodle): Representa estructuras de cursos complejas, incluyendo categorías y módulos, como un árbol compuesto que se puede navegar de forma uniforme.
  - [standardnotes/app](https://github.com/standardnotes/app): Gestiona organizaciones jerárquicas de notas donde carpetas y notas responden uniformemente a operaciones de sincronización.
- **Recursos:**
  - [Composite Pattern](https://refactoring.guru/design-patterns/composite): Guía visual sobre construcción de estructuras de objetos recursivos por Refactoring Guru.
  - [Composite](https://en.wikipedia.org/wiki/Composite_pattern): Una visión general del papel del patrón en las estructuras de datos basadas en árboles en Wikipedia.

</details>

<details>
<summary><strong>Decorator:</strong> Añade responsabilidades adicionales a un objeto de forma dinámica, ofreciendo una alternativa flexible a la herencia.</summary>

Permite añadir comportamientos a un objeto individual sin afectar a otros de la misma clase. Envuelve el objeto original en una clase "decoradora" que mantiene la interfaz original pero añade lógica nueva antes o después de las llamadas a los métodos.

- **Ejemplos:**
  - [discourse/discourse](https://github.com/discourse/discourse): Usa decoradores para añadir funciones dinámicamente a los modelos de usuario o publicaciones basados en plugins activos sin modificar las clases base.
  - [spree/spree](https://github.com/spree/spree): Se apoya en decoradores para permitir a los desarrolladores extender la lógica de negocio de pedidos o envíos sin alterar el código del framework.
- **Recursos:**
  - [Decorator Pattern](https://refactoring.guru/design-patterns/decorator): Cómo adjuntar comportamientos a objetos en tiempo de ejecución por Refactoring Guru.
  - [Decorator Design Pattern](https://sourcemaking.com/design_patterns/decorator): Un análisis de la extensión basada en envoltorios por SourceMaking.

</details>

<details>
<summary><strong>Facade:</strong> Define una interfaz unificada y simplificada para un conjunto de interfaces en un subsistema, facilitando su uso.</summary>

Interfaz que oculta la complejidad de un subsistema. Define un único punto de entrada a un grupo complejo de clases, reduciendo la curva de aprendizaje para los desarrolladores y minimizando las dependencias entre el subsistema y el resto de la aplicación.

- **Ejemplos:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Implementa servicios facade para envolver operaciones complejas de Git y llamadas RPC internas, ofreciendo una API simple para la gestión de repositorios.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Proporciona una fachada para su subsistema de notificaciones, permitiendo disparar alertas sin gestionar protocolos específicos de móvil, email o escritorio.
- **Recursos:**
  - [Facade Pattern](https://refactoring.guru/design-patterns/facade): Protegiendo a los clientes de dependencias complejas por Refactoring Guru.
  - [Facade](https://en.wikipedia.org/wiki/Facade_pattern): Una visión general del diseño de interfaces simplificadas en Wikipedia.

</details>

<details>
<summary><strong>Flyweight:</strong> Utiliza el uso compartido para manejar grandes cantidades de objetos de grano fino de forma eficiente, minimizando el uso de memoria.</summary>

Patrón de ahorro de memoria que comparte la mayor cantidad de datos posible entre objetos similares. Extrae el estado "intrínseco" (datos comunes) a un objeto compartido, mientras que el estado "extrínseco" (datos únicos) se almacena por separado, permitiendo que miles de objetos ocupen muy poca RAM.

- **Ejemplos:**
  - [ornicar/lila](https://github.com/ornicar/lila): Comparte configuraciones de tableros de ajedrez y representaciones de piezas inmutables entre millones de sesiones para minimizar el consumo de memoria del servidor.
  - [plausible/analytics](https://github.com/plausible/analytics): Utiliza metadatos compartidos para tipos de navegadores y sistemas operativos comunes en flujos de eventos de alta densidad.
- **Recursos:**
  - [Flyweight Pattern](https://refactoring.guru/design-patterns/flyweight): Técnicas para gestión de memoria en sistemas de alto volumen por Refactoring Guru.
  - [Flyweight Design Pattern](https://sourcemaking.com/design_patterns/flyweight): Una guía para el intercambio de estado eficiente por SourceMaking.

</details>

<details>
<summary><strong>Proxy:</strong> Define un sustituto o marcador de posición para otro objeto para controlar el acceso a él.</summary>

Patrón donde un objeto proxy actúa como intermediario. Puede usarse para inicialización retardada (lazy loading), control de acceso para verificar permisos antes de una llamada, o para registro y caché de peticiones al objeto original.

- **Ejemplos:**
  - [tryghost/ghost](https://github.com/tryghost/ghost): Emplea objetos proxy para interceptar peticiones a la base de datos, proporcionando una capa de validación y caché interna.
  - [nextcloud/server](https://github.com/nextcloud/server): Usa proxies para representar archivos en almacenamientos externos, iniciando la conexión de red solo cuando se accede explícitamente al archivo.
- **Recursos:**
  - [Proxy Pattern](https://refactoring.guru/design-patterns/proxy): Control de acceso a objetos originales mediante sustitutos por Refactoring Guru.
  - [Proxy Design Pattern](https://sourcemaking.com/design_patterns/proxy): Estrategias de implementación para objetos sustitutos y marcadores de posición por SourceMaking.

</details>


### Patrones de Comportamiento

<br>

*Patrones relacionados con algoritmos y la asignación de responsabilidades entre objetos*

<details>
<summary><strong>Strategy:</strong> Define una familia de algoritmos, encapsula cada uno y los hace intercambiables en tiempo de ejecución.</summary>

Permite elegir entre diferentes formas de realizar la misma tarea sin cambiar el código que la utiliza. Por ejemplo, intercambiar una estrategia de almacenamiento local por una en la nube de forma transparente para el resto de la aplicación.

- **Ejemplos:**
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Utiliza diferentes estrategias para su motor de federación, eligiendo entre envío inmediato o en segundo plano según la prioridad.
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Emplea el patrón estrategia para manejar múltiples métodos de autenticación (contraseña, LDAP, OAuth2, SSH) de forma intercambiable.
- **Recursos:**
  - [Strategy Pattern](https://refactoring.guru/design-patterns/strategy): Técnicas para intercambiar algoritmos en tiempo de ejecución por Refactoring Guru.
  - [Strategy Design Pattern](https://sourcemaking.com/design_patterns/strategy): Una guía para encapsular familias de algoritmos por SourceMaking.

</details>

<details>
<summary><strong>State:</strong> Permite que un objeto altere su comportamiento cuando cambia su estado interno, pareciendo que cambia de clase.</summary>

Encapsula comportamientos específicos de cada estado en clases separadas. En lugar de una clase con grandes bloques condicionales, el objeto delega el trabajo a un objeto de estado. Al cambiar el estado, se intercambia el objeto interno, modificando el comportamiento.

- **Ejemplos:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Gestiona transiciones de peticiones de fusión (Borrador, Abierta, Fusionada, Cerrada) mediante objetos de estado que imponen reglas específicas.
  - [spree/spree](https://github.com/spree/spree): Se apoya en patrones de estado para gestionar el ciclo de vida de un pedido (pago, envío, completado) en la secuencia correcta.
- **Recursos:**
  - [State Pattern](https://refactoring.guru/design-patterns/state): Cómo implementar máquinas de estados de forma orientada a objetos por Refactoring Guru.
  - [State Design Pattern](https://sourcemaking.com/design_patterns/state): Un análisis de las transiciones de comportamiento impulsadas por el estado por SourceMaking.

</details>

<details>
<summary><strong>Observer:</strong> Define una dependencia uno-a-muchos entre objetos para que, cuando uno cambie, todos sus dependientes sean notificados automáticamente.</summary>

Crea un mecanismo de suscripción. Un objeto (el sujeto) mantiene una lista de interesados (observadores). Cuando el estado cambia, notifica automáticamente a todos los observadores. Es el núcleo de las interfaces reactivas y sistemas guiados por eventos.

- **Ejemplos:**
  - [home-assistant/core](https://github.com/home-assistant/core): Construido íntegramente sobre el patrón observador; el bus de eventos notifica a componentes y paneles en el momento en que un sensor físico reporta cambios.
  - [discourse/discourse](https://github.com/discourse/discourse): Usa el patrón observador para disparar notificaciones y correos cuando se crea un post o se menciona a un usuario.
- **Recursos:**
  - [Observer Pattern](https://refactoring.guru/design-patterns/observer): Guía para implementar notificaciones por suscripción por Refactoring Guru.
  - [Observer Design Pattern](https://sourcemaking.com/design_patterns/observer): Un desglose de la relación entre sujeto y observador por SourceMaking.

</details>

<details>
<summary><strong>Chain of Responsibility:</strong> Pasa una petición a lo largo de una cadena de manejadores, donde cada uno decide si procesarla o pasarla al siguiente.</summary>

Desacopla al emisor de una petición de sus receptores. Permite que múltiples objetos tengan la oportunidad de manejar la petición sin que el emisor necesite saber quién lo hará. Común en flujos de procesamiento de peticiones, middleware y sistemas de plugins.

- **Ejemplos:**
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Usa una cadena de manejadores de middleware para peticiones HTTP (autenticación, registro, CSRF) antes de llegar a la lógica central.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Implementa una cadena de responsabilidad para su sistema de plugins, donde varios plugins interceptan y modifican mensajes.
- **Recursos:**
  - [Chain of Responsibility](https://refactoring.guru/design-patterns/chain-of-responsibility): Resumen de procesamiento por manejadores por Refactoring Guru.
  - [Chain of Responsibility Design Pattern](https://sourcemaking.com/design_patterns/chain_of_responsibility): Un desglose de la intención del patrón y los participantes estructurales por SourceMaking.

</details>

<details>
<summary><strong>Command:</strong> Encapsula una petición como un objeto, permitiendo parametrizar clientes con colas, peticiones y operaciones.</summary>

Convierte una acción en un objeto independiente que contiene toda la información para ejecutarla. Esto permite retrasar la ejecución, guardar la acción en una cola o mantener un historial para soportar funciones de deshacer y rehacer.

- **Ejemplos:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Encapsula tareas en segundo plano como objetos comando para operaciones pesadas como archivado de repositorios.
  - [zulip/zulip](https://github.com/zulip/zulip): Se apoya en comandos para procesar mensajes entrantes, permitiendo manejar lógica compleja de entrega de forma aislada.
- **Recursos:**
  - [Command Pattern](https://refactoring.guru/design-patterns/command): Guía para encapsular acciones y soportar deshacer/rehacer por Refactoring Guru.
  - [Command Design Pattern](https://sourcemaking.com/design_patterns/command): Un análisis técnico de la relación entre invocador y receptor por SourceMaking.

</details>

<details>
<summary><strong>Iterator:</strong> Define una forma de acceder a los elementos de un objeto agregado secuencialmente sin exponer su representación interna.</summary>

Extrae la lógica de recorrido de una colección a un objeto separado. Esto permite recorrer listas, árboles o grafos sin saber si los datos están en un array, lista vinculada o base de datos remota.

- **Ejemplos:**
  - [moodle/moodle](https://github.com/moodle/moodle): Usa iteradores para recorrer ítems de cursos sin cargar toda la colección en memoria a la vez.
  - [go-gitea/gitea](https://github.com/go-gitea/gitea): Implementa iteradores para navegar por el historial de commits o árboles de archivos de forma uniforme.
- **Recursos:**
  - [Iterator Pattern](https://refactoring.guru/design-patterns/iterator): Guía visual de recorrido de colecciones complejas por Refactoring Guru.
  - [Iterator Design Pattern](https://sourcemaking.com/design_patterns/iterator): Una guía para desacoplar el recorrido de la colección de su implementación por SourceMaking.

</details>

<details>
<summary><strong>Mediator:</strong> Define un objeto que encapsula cómo interactúa un conjunto de objetos, promoviendo el acoplamiento débil.</summary>

Centraliza la comunicación entre componentes. En lugar de que los objetos hablen directamente entre sí, todos se comunican con un mediador central que coordina las interacciones, facilitando cambios en la lógica de comunicación en un solo lugar.

- **Ejemplos:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Usa un mediador central para coordinar actualizaciones de UI entre fragmentos cuando cambia el estado de la base de datos.
  - [zulip/zulip](https://github.com/zulip/zulip): Emplea un mediador para coordinar la entrega de eventos en tiempo real entre el servidor y los clientes conectados.
- **Recursos:**
  - [Mediator Pattern](https://refactoring.guru/design-patterns/mediator): Cómo reducir dependencias caóticas entre clases por Refactoring Guru.
  - [Mediator Design Pattern](https://sourcemaking.com/design_patterns/mediator): Un análisis de la comunicación centralizada frente a la distribuida por SourceMaking.

</details>

<details>
<summary><strong>Memento:</strong> Captura y externaliza el estado interno de un objeto sin violar su encapsulamiento, permitiendo restaurarlo más tarde.</summary>

Implementa puntos de control para el estado de un objeto. Permite guardar el estado actual en un "memento" y restaurarlo después, algo esencial para funciones de deshacer/rehacer o recuperación de sesiones.

- **Ejemplos:**
  - [standardnotes/app](https://github.com/standardnotes/app): Implementa conceptos de memento para fotografiar contenido de notas, permitiendo ver y restaurar versiones anteriores.
  - [logseq/logseq](https://github.com/logseq/logseq): Usa gestión de estado tipo memento para operaciones de deshacer y rehacer en su estructura interna de grafo.
- **Recursos:**
  - [Memento Pattern](https://refactoring.guru/design-patterns/memento): Técnicas para guardar snapshots de objetos por Refactoring Guru.
  - [Memento Design Pattern](https://sourcemaking.com/design_patterns/memento): Una guía para capturar el estado interno para su restauración por SourceMaking.

</details>

<details>
<summary><strong>Template Method:</strong> Define el esqueleto de un algoritmo en una operación, delegando algunos pasos a las subclases sin cambiar la estructura del mismo.</summary>

Define pasos estándar en una clase base pero deja la ejecución de ciertos pasos a clases secundarias. Asegura que el flujo general se siga correctamente mientras permite personalizar partes específicas en diferentes módulos.

- **Ejemplos:**
  - [moodle/moodle](https://github.com/moodle/moodle): Proporciona clases base para módulos de actividad que definen el ciclo estándar de calificación, dejando que cada módulo implemente su lógica específica.
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Usa métodos de plantilla en sus workers en segundo plano para procesos consistentes de registro, reintento y errores.
- **Recursos:**
  - [Template Method Pattern](https://refactoring.guru/design-patterns/template-method): Algoritmos con pasos intercambiables por Refactoring Guru.
  - [Template Method Design Pattern](https://sourcemaking.com/design_patterns/template_method): Un análisis del Principio de Hollywood ("No nos llames, nosotros te llamaremos") por SourceMaking.

</details>

<details>
<summary><strong>Visitor:</strong> Representa una operación a realizar sobre los elementos de una estructura de objetos, permitiendo definir una nueva operación sin cambiar sus clases.</summary>

Añade funciones a una estructura de objetos existente sin modificarlos. Un objeto visitante recorre la estructura y realiza su operación en cada elemento. Muy eficaz para auditorías, exportación de datos o validaciones complejas.

- **Ejemplos:**
  - [home-assistant/core](https://github.com/home-assistant/core): Emplea visitantes para recorrer registros de dispositivos y realizar validaciones globales sin alterar las clases individuales de dispositivos.
  - [grafana/grafana](https://github.com/grafana/grafana): Usa el patrón visitante para recorrer árboles de configuración JSON complejos para su transformación y validación.
- **Recursos:**
  - [Visitor Pattern](https://refactoring.guru/design-patterns/visitor): Añadiendo operaciones a jerarquías de objetos existentes por Refactoring Guru.
  - [Visitor Design Pattern](https://sourcemaking.com/design_patterns/visitor): Un desglose del doble despacho y el recorrido estructural por SourceMaking.

</details>

<details>
<summary><strong>Interpreter:</strong> Dada un lenguaje, define una representación de su gramática junto con un intérprete que la utiliza para evaluar sentencias.</summary>

Define una jerarquía de clases para representar la gramática de un lenguaje o formato de expresión. Un intérprete recorre esta jerarquía para evaluar la expresión. Común en aplicaciones que analizan consultas personalizadas o fórmulas matemáticas.

- **Ejemplos:**
  - [metabase/metabase](https://github.com/metabase/metabase): Usa un intérprete para traducir su MBQL interno (basado en JSON) a dialectos SQL específicos de bases de datos.
  - [grafana/grafana](https://github.com/grafana/grafana): Implementa patrones de intérprete para analizar condiciones de alerta definidas por usuario y expresiones de transformación.
- **Recursos:**
  - [Interpreter Design Pattern](https://sourcemaking.com/design_patterns/interpreter): Resumen de representación y evaluación de gramáticas.
  - [Interpreter](https://en.wikipedia.org/wiki/Interpreter_pattern): Una visión general del papel del patrón en los lenguajes específicos de dominio en Wikipedia.

</details>

<details>
<summary><strong>Null Object Pattern:</strong> Utiliza un objeto neutro por defecto que implementa una interfaz esperada para no hacer nada, evitando comprobaciones de nulos.</summary>

Sustituye comprobaciones de nulos por un objeto especializado que implementa la interfaz requerida pero no realiza acción alguna. Simplifica el código al tratar la ausencia de una dependencia como un objeto válido y funcional.

- **Ejemplos:**
  - [discourse/discourse](https://github.com/discourse/discourse): Usa Null Object para manejar casos donde faltan ajustes o relaciones, evitando comprobaciones explícitas en la lógica de negocio.
  - [spree/spree](https://github.com/spree/spree): Emplea Null Objects para calculadoras promocionales y gestores de impuestos cuando no aplican reglas específicas.
- **Recursos:**
  - [Null Object Pattern](https://sourcemaking.com/design_patterns/null_object): Guía para simplificar código eliminando comprobaciones de nulos.
  - [Null Object](https://en.wikipedia.org/wiki/Null_object_pattern): Una visión general de los beneficios del patrón para la resiliencia del software en Wikipedia.

</details>


### Patrones de Concurrencia

<br>

*Patrones que manejan paradigmas de multi-hilo y procesamiento paralelo*

<details>
<summary><strong>Active Object:</strong> Desacopla la ejecución del método de su invocación para mejorar la concurrencia y simplificar el acceso sincronizado.</summary>

Permite que un objeto ejecute sus métodos en su propio hilo en lugar del hilo del emisor. Transforma llamadas síncronas en mensajes asíncronos en una cola, permitiendo que el emisor continúe inmediatamente mientras el objeto activo procesa la petición en segundo plano.

- **Ejemplos:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Implementa principios de objeto activo en la gestión de trabajos para que operaciones criptográficas intensas no bloqueen la interfaz de usuario.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Utiliza hilos de trabajo asíncronos para ejecutar tareas pesadas sin detener las peticiones de red entrantes.
- **Recursos:**
  - [Active Object](https://en.wikipedia.org/wiki/Active_object): Resumen de componentes: proxy, planificador y servidor.
  - [Active Object Design Pattern](https://www.dre.vanderbilt.edu/~schmidt/PDF/Active-Object.pdf) por Douglas C. Schmidt: El artículo de investigación original que detalla el desacoplamiento de la invocación y la ejecución.

</details>

<details>
<summary><strong>Monitor Object:</strong> Sincroniza la ejecución de métodos concurrentes para que solo un método a la vez se ejecute dentro de un objeto.</summary>

Protege el estado interno de un objeto del acceso concurrente de múltiples hilos. Garantiza que solo un hilo pueda ejecutar un método sincronizado en el objeto, mientras otros esperan a que se libere el bloqueo.

- **Ejemplos:**
  - [metabase/metabase](https://github.com/metabase/metabase): Usa objetos monitor para gestionar el acceso sincronizado a pools de conexiones compartidas, evitando condiciones de carrera.
  - [discourse/discourse](https://github.com/discourse/discourse): Emplea mutex y monitores en Ruby para sincronizar el acceso a memoria compartida en la ejecución de lógica en segundo plano.
- **Recursos:**
  - [Monitor Object Design Pattern](https://www.dre.vanderbilt.edu/~schmidt/PDF/Monitor.pdf): Guía para encapsular exclusión mutua en software orientado a objetos.
  - [Monitor](https://en.wikipedia.org/wiki/Monitor_(synchronization)): Un desglose técnico de las primitivas de sincronización de alto nivel en Wikipedia.

</details>

<details>
<summary><strong>Half-Sync/Half-Async:</strong> Desacopla el procesamiento de servicios asíncronos y síncronos en sistemas concurrentes.</summary>

Salva la distancia entre el manejo de eventos asíncronos de bajo nivel (eficiencia de E/S) y el procesamiento síncrono de alto nivel (lógica de programación simple). Usa una cola para pasar datos de una capa asíncrona a un pool de hilos síncronos.

- **Ejemplos:**
  - [zulip/zulip](https://github.com/zulip/zulip): Implementa este patrón usando un bucle de eventos asíncrono para conexiones mientras delega la lógica pesada de negocio a hilos síncronos.
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Se apoya en arquitecturas half-sync/half-async para gestionar la transición entre E/S de red rápida y la persistencia de mensajes secuencial.
- **Recursos:**
  - [Half-Sync/Half-Async Design Pattern](https://www.dre.vanderbilt.edu/~schmidt/PDF/HSHA.pdf): Análisis técnico sobre la separación de preocupaciones síncronas y asíncronas.
  - [Pattern-Oriented Software Architecture (POSA)](https://en.wikipedia.org/wiki/Pattern-Oriented_Software_Architecture): Un resumen de los patrones arquitectónicos para objetos concurrentes y en red.

</details>

<details>
<summary><strong>Thread Pool:</strong> Gestiona una colección de hilos de trabajo que ejecutan callbacks asíncronos de forma eficiente.</summary>

Evita el alto coste de crear y destruir hilos frecuentemente. Mantiene un conjunto de hilos pre-inicializados en un "pool". Al llegar una tarea, se asigna a un hilo disponible; una vez terminada, el hilo vuelve al pool para ser reutilizado.

- **Ejemplos:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Usa pools de hilos en Sidekiq para gestionar la ejecución concurrente de miles de tareas de repositorio sin saturar los recursos del sistema.
  - [metabase/metabase](https://github.com/metabase/metabase): Emplea pools de hilos en su servidor web Jetty para manejar eficientemente peticiones HTTP y consultas de datos concurrentes.
- **Recursos:**
  - [Thread Pool Pattern](https://sourcemaking.com/design_patterns/thread_pool): Guía para gestionar el ciclo de vida de hilos de trabajo.
  - [Thread Pool](https://en.wikipedia.org/wiki/Thread_pool): Una visión general del encolado de tareas y la gestión de recursos en Wikipedia.

</details>

<details>
<summary><strong>Read-Write Lock:</strong> Permite acceso de lectura concurrente pero requiere acceso exclusivo para operaciones de escritura.</summary>

Mejora el rendimiento en sistemas donde los datos se leen mucho más de lo que se modifican. Permite que múltiples hilos lectores accedan simultáneamente, pero obliga a un hilo escritor a esperar hasta que terminen las lecturas para ganar acceso exclusivo.

- **Ejemplos:**
  - [grafana/grafana](https://github.com/grafana/grafana): Usa cerrojos de lectura-escritura para sus cachés de fuentes de datos, permitiendo miles de lecturas mientras garantiza consistencia en las actualizaciones.
  - [home-assistant/core](https://github.com/home-assistant/core): Emplea mecanismos de bloqueo de lectura-escritura en su registro de estado para permitir consultas concurrentes mientras protege contra corrupción durante las escrituras.
- **Recursos:**
  - [Read-Write Lock Pattern](https://en.wikipedia.org/wiki/Readers%E2%80%93writer_lock): Detalles técnicos sobre prioridades de lectura concurrente frente a escritura exclusiva.
  - [Read-Write Lock](https://sourcemaking.com/design_patterns/read_write_lock): Un análisis de la optimización de la concurrencia de lectura intensiva por SourceMaking.

</details>

<details>
<summary><strong>Double-Checked Locking:</strong> Reduce la sobrecarga de adquirir un bloqueo comprobando primero el criterio sin sincronización.</summary>

Optimiza la inicialización retardada en entornos multi-hilo. Comprueba si un objeto ya está inicializado sin un bloqueo; si no lo está, entra en un bloque sincronizado y vuelve a comprobarlo antes de crearlo, garantizando que solo un hilo cree la instancia sin sacrificar rendimiento.

- **Ejemplos:**
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Usado frecuentemente para la inicialización retardada de su `DatabaseFactory` y gestores de preferencias de forma segura y eficiente.
  - [wordpress-mobile/WordPress-Android](https://github.com/wordpress-mobile/WordPress-Android): Emplea este patrón para inicializar servicios compartidos solo cuando se acceden por primera vez.
- **Recursos:**
  - [Double-Checked Locking Pattern](https://sourcemaking.com/design_patterns/double_checked_locking): Guía para optimizar la sincronización.
  - [The Double-Checked Locking is Broken Declaration](http://www.cs.umd.edu/~pugh/java/memoryModel/DoubleCheckedLocking.html): Un análisis histórico crítico de los problemas del modelo de memoria con este patrón.

</details>


### Patrones Funcionales

<br>

*Patrones derivados de paradigmas de programación funcional adaptados al diseño de software moderno*

<details>
<summary><strong>Monad:</strong> Patrón para describir computaciones como una serie de pasos, manejando efectos secundarios o estado de forma puramente funcional.</summary>

Patrón estructural que envuelve un valor en un contexto y proporciona un mecanismo para aplicar funciones a ese valor envuelto. Permite encadenar operaciones complejas abstrayendo código repetitivo para comprobación de nulos o ejecución asíncrona.

- **Ejemplos:**
  - [lemmynet/lemmy](https://github.com/lemmynet/lemmy): Escrito en Rust, usa los tipos nativos `Option` y `Result` (mónadas) de forma generalizada para manejar valores ausentes y efectos secundarios de red con seguridad.
  - [standardnotes/app](https://github.com/standardnotes/app): Se apoya en Promesas (estructura monádica) en TypeScript para encadenar operaciones criptográficas asíncronas complejas sin rellamadas (callbacks) anidadas.
- **Recursos:**
  - [Monad (functional programming)](https://en.wikipedia.org/wiki/Monad_(functional_programming)): Origen matemático y estructuras monádicas.
  - [Functors, Applicatives, and Monads in Pictures](https://adit.io/posts/2013-04-17-functors,_applicatives,_and_monads_in_pictures.html) por Aditya Bhargava: Una guía visual altamente accesible para entender los contextos funcionales.

</details>

<details>
<summary><strong>Functor:</strong> Patrón de mapeo que permite aplicar una función a valores envueltos en un contexto, preservando su estructura.</summary>

Representa cualquier tipo que implemente una función de mapeo. Aplica una transformación de datos al contenido de un contenedor (como una lista o un tipo "opción") y devuelve un nuevo contenedor con la misma estructura sin mutar el original.

- **Ejemplos:**
  - [plausible/analytics](https://github.com/plausible/analytics): La plataforma en Elixir confía en mapeos tipo functor sobre colecciones para procesar grandes volúmenes de telemetría web eficientemente.
  - [mastodon/mastodon](https://github.com/mastodon/mastodon): Mapea frecuentemente sobre colecciones de perfiles o estados para aplicar transformaciones preservando las estructuras de datos para la capa de presentación.
- **Recursos:**
  - [Category Theory for Programmers: Functors](https://bartoszmilewski.com/2015/01/20/functors/): Profundización teórica y práctica en aplicaciones de functores.
  - [Functor (functional programming)](https://en.wikipedia.org/wiki/Functor_(functional_programming)): Detalles técnicos sobre el mapeo sobre tipos de datos en Wikipedia.

</details>

<details>
<summary><strong>Immutable Object:</strong> Objeto cuyo estado no puede modificarse tras su creación, eliminando efectos secundarios y haciendo segura la programación concurrente.</summary>

Patrón estricto de gestión de datos. En lugar de cambiar propiedades de un objeto existente, cualquier actualización crea una nueva copia con los nuevos valores. Garantiza seguridad de hilos, evita condiciones de carrera y ofrece un historial predecible del estado.

- **Ejemplos:**
  - [zulip/zulip-mobile](https://github.com/zulip/zulip-mobile): Usa Redux para imponer inmutabilidad estricta. Cada mensaje recibido genera un nuevo objeto de estado en lugar de mutar los datos en memoria.
  - [ornicar/lila](https://github.com/ornicar/lila): Representa partidas de ajedrez y movimientos como estructuras inmutables, permitiendo procesar miles de partidas sin bloqueos complejos de memoria.
- **Recursos:**
  - [ValueObject](https://martinfowler.com/bliki/ValueObject.html) por Martin Fowler.
  - [Immutable Object](https://en.wikipedia.org/wiki/Immutable_object): Una visión general de las estrategias de implementación y características de rendimiento en Wikipedia.

</details>

<details>
<summary><strong>Result Pattern / Railway Oriented Programming:</strong> Envuelve el resultado de una operación (éxito o fallo) en un tipo especializado, permitiendo composición secuencial sin excepciones.</summary>

Sustituye el manejo tradicional con `try-catch`. Las funciones devuelven un objeto que representa éxito o error. Si una función falla en una cadena, el sistema cambia a la "vía de error", saltando la lógica de éxito posterior y entregando el fallo limpiamente al final.

- **Ejemplos:**
  - [lemmynet/lemmy](https://github.com/lemmynet/lemmy): Evita lanzar excepciones tradicionales, devolviendo el enumerado `Result` de Rust en casi cada consulta o petición de red.
  - [signalapp/Signal-Android](https://github.com/signalapp/Signal-Android): Usa tipos `Result` nativos de Kotlin para encadenar procesos de descifrado criptográfico que podrían fallar por claves incorrectas o datos corruptos.
- **Recursos:**
  - [Railway Oriented Programming](https://fsharpforfunandprofit.com/rop/): Guía definitiva de manejo de errores mediante la analogía de vías de tren.
  - [Error Handling in Rust](https://doc.rust-lang.org/book/ch09-00-error-handling.html): Documentación oficial sobre el uso del enumerado Result para un diseño de software resiliente.

</details>

<details>
<summary><strong>Dependency Rejection:</strong> Alternativa funcional a la Inyección de Dependencias que empuja efectos secundarios a los bordes de la aplicación.</summary>

Separa la lógica de la acción. En lugar de inyectar servicios en un modelo de dominio, el modelo puro recibe datos planos y devuelve resultados planos. El núcleo "imperativo" de la aplicación lee de la red, pasa datos al núcleo puro y escribe el resultado final.

- **Ejemplos:**
  - [metabase/metabase](https://github.com/metabase/metabase): Aísla su generación compleja de consultas y lógica de transformación como funciones puras en Clojure, desacopladas de la ejecución real en base de datos.
  - [grafana/grafana](https://github.com/grafana/grafana): Extrae transformaciones de datos de paneles a funciones puras que solo toman entradas y devuelven salidas, dejando las peticiones de red para los manejadores externos.
- **Recursos:**
  - [Functional Core, Imperative Shell](https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell) por Gary Bernhardt.
  - [Dependency Rejection](https://blog.ploeh.dk/2017/01/27/dependency-rejection/) por Mark Seemann: El artículo central que explica cómo reemplazar la Inyección de Dependencias con funciones puras.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

## Temas Transversales de Arquitectura

<br>

Son patrones y herramientas que afectan a todas las partes de un sistema de software. A diferencia de las funciones aisladas, estos temas —como la seguridad, la observabilidad y el respaldo de datos— impactan en múltiples componentes y requieren una configuración coherente para que todo el sistema funcione correctamente. Esta categoría se centra en los cimientos de una plataforma, incluyendo estándares de seguridad, trazabilidad y despliegues automatizados.

### Patrones de Arquitectura de Seguridad

<br>

*Mecanismos para mantener la seguridad del sistema, control de acceso, confidencialidad de datos y cumplimiento normativo en todas las fronteras sistémicas*

<details>
<summary><strong>Zero Trust Architecture:</strong> Arquitectura que asume que la red es siempre hostil; requiere verificación estricta de identidad y dispositivo para cada petición.</summary>

Sustituye el modelo tradicional de "castillo y foso". En lugar de confiar en todo lo que está dentro del cortafuegos corporativo, obliga a que cada usuario, dispositivo y aplicación sea autenticado continuamente, aplicando el principio de mínimo privilegio.

- **Herramientas Estándar:**
  - [cloudflare/cloudflared](https://github.com/cloudflare/cloudflared): Cliente de Cloudflare Tunnel para exponer servicios locales de forma segura sin abrir puertos entrantes.
  - [pomerium/pomerium](https://github.com/pomerium/pomerium): Proxy de acceso abierto basado en identidad que actúa como puerta de enlace, aplicando políticas Zero Trust en el borde.
- **Recursos:**
  - [Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final): Publicación oficial NIST (800-207) sobre principios y modelos de despliegue.

</details>

<details>
<summary><strong>Role-Based Access Control (RBAC):</strong> Restringe el acceso al sistema basándose en roles y permisos predefinidos para los usuarios.</summary>

Paradigma donde los derechos de acceso se agrupan por nombre de rol (ej. "Administrador", "Editor", "Visor") en lugar de asignarse individualmente. Los usuarios reciben uno o más roles, simplificando la gestión de permisos en grandes organizaciones.

- **Herramientas Estándar:**
  - [kubernetes/kubernetes](https://github.com/kubernetes/kubernetes): Utiliza intensamente RBAC para regular el acceso a sus recursos de API basándose en roles de usuarios y cuentas de servicio.
  - [casbin/casbin](https://github.com/casbin/casbin): Biblioteca potente de control de acceso que soporta la aplicación de autorización basada en modelos RBAC.
- **Recursos:**
  - [Role-Based Access Control](https://csrc.nist.gov/projects/role-based-access-control): Estándar NIST sobre los beneficios económicos y de seguridad de RBAC.

</details>

<details>
<summary><strong>Attribute-Based Access Control (ABAC):</strong> Otorga derechos de acceso mediante la evaluación de políticas que combinan atributos de usuario, recurso y entorno.</summary>

Modelo de autorización granular que va más allá de los roles estáticos. Toma decisiones en tiempo de ejecución evaluando combinaciones de atributos (departamento, sensibilidad del documento, hora del día, IP actual), permitiendo políticas de seguridad muy complejas.

- **Herramientas Estándar:**
  - [open-policy-agent/opa](https://github.com/open-policy-agent/opa): Motor de políticas de propósito general que desacopla la decisión de políticas de la lógica de aplicación, usado para implementar ABAC en nubes nativas.
  - [permitio/permit-node](https://github.com/permitio/permit-node): Framework de autorización que ofrece herramientas para políticas complejas ABAC y RBAC mediante API.
- **Recursos:**
  - [Attribute-Based Access Control](https://csrc.nist.gov/publications/detail/sp/800-162/final): Publicación NIST (800-162) sobre componentes y consideraciones de ABAC empresarial.

</details>

<details>
<summary><strong>Mutual TLS (mTLS):</strong> Valida que el tráfico sea seguro y confiable en ambas direcciones exigiendo que cliente y servidor se autentiquen mutuamente.</summary>

Mientras que el TLS estándar solo verifica la identidad del servidor, mTLS obliga al cliente a presentar un certificado válido. Garantiza que el tráfico esté cifrado y que solo microservicios o dispositivos autorizados puedan comunicarse, siendo el núcleo de la seguridad en mallas de servicios (service mesh).

- **Herramientas Estándar:**
  - [istio/istio](https://github.com/istio/istio): Malla de servicios que añade cifrado mTLS y verificación de identidad de forma transparente en todas las comunicaciones internas de un clúster.
  - [linkerd/linkerd2](https://github.com/linkerd/linkerd2): Malla de servicios ligera para Kubernetes que proporciona mTLS automático y transparente entre pods.
- **Recursos:**
  - [Mutual TLS](https://www.cloudflare.com/learning/access-management/what-is-mutual-tls/): Resumen de conceptos de mTLS por Cloudflare.

</details>

<details>
<summary><strong>Identity Federation / Single Sign-On (SSO):</strong> Delega la autenticación a un proveedor central de identidad, permitiendo acceder a múltiples sistemas con una sola credencial.</summary>

Centraliza la gestión de identidad. En lugar de que cada aplicación gestione su base de datos de usuarios, redirigen al usuario a un Proveedor de Identidad (IdP) central (vía SAML u OpenID Connect). Esto reduce la fatiga de contraseñas y centraliza las auditorías de seguridad.

- **Herramientas Estándar:**
  - [keycloak/keycloak](https://github.com/keycloak/keycloak): Sistema de gestión de identidad y acceso de código abierto, proporcionando SSO, federación de usuarios y mediación de identidad.
  - [dexidp/dex](https://github.com/dexidp/dex): Proveedor federado de OpenID Connect que sirve de portal para conectar IdPs externos (LDAP, SAML, GitHub) a clústeres de Kubernetes.
- **Recursos:**
  - [OpenID Connect](https://openid.net/connect/): Especificaciones oficiales para la capa de identidad construida sobre OAuth 2.0.

</details>


### Patrones de Arquitectura de Datos

<br>

*Estrategias que definen la estructura, gestión y gobernanza de los activos de datos de una organización, tanto en reposo como en movimiento*

<details>
<summary><strong>Data Lake:</strong> Repositorio centralizado y escalable que almacena grandes volúmenes de datos en bruto, tanto estructurados como no estructurados.</summary>

Permite almacenar datos sin estructurarlos previamente para su uso en análisis diversos, aprendizaje automático y procesamiento de grandes volúmenes de datos (Big Data).

- **Herramientas Estándar:**
  - [delta-io/delta](https://github.com/delta-io/delta): Framework de almacenamiento que permite construir arquitecturas Lakehouse con motores como Spark, Flink o Trino.
  - [apache/hudi](https://github.com/apache/hudi): Aporta procesamiento de flujos a Big Data, ofreciendo mayor eficiencia que el procesamiento por lotes tradicional en lagos de datos.
- **Recursos:**
  - [¿Qué es un Data Lake?](https://aws.amazon.com/es/big-data/datalakes-and-analytics/what-is-a-data-lake/): Guía de AWS sobre arquitectura, beneficios y componentes.

</details>

<details>
<summary><strong>Data Warehouse:</strong> Repositorio central de datos altamente estructurados e integrados, optimizado estrictamente para consultas y generación de informes analíticos.</summary>

Utiliza esquemas definidos previamente (esquema en escritura) para mantener la calidad de los datos y un rendimiento de consulta rápido para herramientas de inteligencia de negocio.

- **Herramientas Estándar:**
  - [clickhouse/clickhouse](https://github.com/clickhouse/clickhouse): Sistema de gestión de base de datos orientado a columnas que permite generar informes analíticos en tiempo real con alto rendimiento.
  - [apache/druid](https://github.com/apache/druid): Base de datos de análisis en tiempo real de alto rendimiento para consultas de sub-segundo.
- **Recursos:**
  - [Data Warehouse](https://en.wikipedia.org/wiki/Data_warehouse): Principios de almacenamiento de datos en Wikipedia.

</details>

<details>
<summary><strong>Data Mesh:</strong> Arquitectura descentralizada que trata los datos como un producto, donde equipos de dominio son dueños y sirven sus propios datos.</summary>

Aplica principios de Diseño Guiado por el Dominio (DDD) a la gestión de datos, apoyándose en una infraestructura de autoservicio y gobernanza computacional federada.

- **Herramientas Estándar:**
  - [trinodb/trino](https://github.com/trinodb/trino): Motor de consultas SQL distribuidas rápidas que ayuda a materializar un data mesh consultando datos allí donde residen.
  - [amundsen-io/amundsen](https://github.com/amundsen-io/amundsen): Motor de descubrimiento de datos y metadatos para que los equipos publiquen y descubran productos de datos.
- **Recursos:**
  - [How to Move Beyond a Monolithic Data Lake to a Distributed Data Mesh](https://martinfowler.com/articles/data-monolith-to-mesh.html) por Zhamak Dehghani: Artículo original que define el paradigma.

</details>

<details>
<summary><strong>Data Fabric:</strong> Arquitectura que define una capa de integración de datos unificada, automatizada e inteligente en entornos híbridos y multi-nube.</summary>

Utiliza metadatos activos, grafos de conocimiento y aprendizaje automático para automatizar el descubrimiento, gobernanza y consumo de datos, conectándolos independientemente de su ubicación.

- **Herramientas Estándar:**
  - [linkedin/datahub](https://github.com/linkedin/datahub): Plataforma de metadatos extensible para descubrimiento y observabilidad, actuando como el núcleo de un data fabric.
  - [apache/atlas](https://github.com/apache/atlas): Proporciona capacidades de gestión de metadatos y gobernanza para construir un catálogo de activos de datos.
- **Recursos:**
  - [¿Qué es un Data Fabric?](https://www.ibm.com/es-es/topics/data-fabric): Visión técnica de IBM sobre capas de integración automatizada.

</details>


### Patrones de Arquitectura de Despliegue

<br>

*Estrategias y topologías para la provisión, entrega, gestión y escalado de recursos computacionales físicos o en la nube*

<details>
<summary><strong>Blue-Green Deployment:</strong> Reduce el tiempo de inactividad ejecutando dos entornos de producción idénticos (Azul y Verde) y desviando el tráfico por completo de uno a otro.</summary>

Metodología que minimiza riesgos manteniendo la versión anterior en vivo mientras se despliega la nueva en un entorno inactivo. Una vez verificada, el balanceador desvía el tráfico al instante, permitiendo reversiones rápidas si hay fallos.

- **Herramientas Estándar:**
  - [argoproj/argo-rollouts](https://github.com/argoproj/argo-rollouts): Controlador de Kubernetes que automatiza y gestiona el enrutamiento Blue-Green y Canary.
  - [kubernetes/kubernetes](https://github.com/kubernetes/kubernetes): Ejecuta despliegues Blue-Green de forma nativa manipulando selectores de etiquetas de Servicios para redirigir el tráfico.
- **Recursos:**
  - [BlueGreenDeployment](https://martinfowler.com/bliki/BlueGreenDeployment.html) por Martin Fowler: Explicación de la estrategia de enrutamiento dual.

</details>

<details>
<summary><strong>Canary Release:</strong> Mitiga riesgos desplegando cambios lentamente a un subconjunto pequeño y controlado de usuarios antes de lanzarlos a toda la base.</summary>

Patrón de entrega progresiva donde el nuevo código reside junto al estable. Se desvía un pequeño porcentaje de tráfico (ej. 5%) a las instancias "canario" y se monitoriza. Si todo va bien, el porcentaje aumenta gradualmente hasta reemplazar la versión antigua.

- **Herramientas Estándar:**
  - [fluxcd/flagger](https://github.com/fluxcd/flagger): Herramienta de entrega progresiva que automatiza la promoción basándose en métricas y tests automáticos.
  - [istio/istio](https://github.com/istio/istio): Malla de servicios que ofrece división de tráfico granular necesaria para ejecuciones canario precisas.
- **Recursos:**
  - [CanaryRelease](https://martinfowler.com/bliki/CanaryRelease.html) por Martin Fowler: Exposición progresiva para detectar fallos antes del despliegue masivo.

</details>

<details>
<summary><strong>Rolling Update:</strong> Reemplaza incrementalmente instancias de la versión anterior con instancias de la nueva para un tiempo de inactividad cero.</summary>

Estrategia que actualiza una flota de servidores uno a uno (o en pequeños lotes). El orquestador retira un pequeño número de instancias antiguas, levanta nuevas, espera a que sean saludables y pasa al siguiente lote, asegurando capacidad constante durante la transición.

- **Herramientas Estándar:**
  - [kubernetes/kubernetes](https://github.com/kubernetes/kubernetes): Estrategia por defecto en Kubernetes, gestionando el reemplazo incremental de Pods manteniendo un umbral mínimo de disponibilidad.
  - [hashicorp/nomad](https://github.com/hashicorp/nomad): Orquestador flexible que proporciona estrategias de actualización progresiva integradas.
- **Recursos:**
  - [Performing a Rolling Update](https://kubernetes.io/docs/tutorials/kubernetes-basics/update/update-intro/): Documentación oficial sobre gestión de reemplazo incremental.

</details>

<details>
<summary><strong>Immutable Server / Infrastructure:</strong> Patrón donde los servidores o contenedores nunca se modifican una vez desplegados; cualquier cambio requiere crear una instancia nueva.</summary>

Paradigma operativo que elimina la deriva de configuración. En lugar de entrar en un servidor para actualizarlo, el flujo de despliegue genera una imagen de máquina nueva y totalmente configurada. El servidor antiguo se destruye, garantizando entornos perfectamente reproducibles.

- **Herramientas Estándar:**
  - [hashicorp/packer](https://github.com/hashicorp/packer): Herramienta para crear imágenes de máquina idénticas para múltiples plataformas desde una única fuente.
  - [moby/moby](https://github.com/moby/moby): Proyecto detrás de Docker, que impone inmutabilidad empaquetando aplicaciones en imágenes de solo lectura.
- **Recursos:**
  - [ImmutableServer](https://martinfowler.com/bliki/ImmutableServer.html) por Martin Fowler: Guía sobre la destrucción de servidores frente a su actualización.

</details>

<details>
<summary><strong>Sidecar Pattern:</strong> Despliega componentes de infraestructura de apoyo (logging, proxies) en un contenedor separado adjunto que corre junto a la aplicación principal.</summary>

Abstrae la lógica ajena al negocio (recolección de métricas, cifrado mTLS, gestión de secretos) del código de la aplicación. El sidecar comparte el mismo ciclo de vida, red y espacio de disco que la aplicación principal como un proceso de apoyo integrado.

- **Herramientas Estándar:**
  - [envoyproxy/envoy](https://github.com/envoyproxy/envoy): Proxy distribuido de alto rendimiento que funciona como sidecar universal en el plano de datos de mallas de servicios.
  - [fluent/fluent-bit](https://github.com/fluent/fluent-bit): Procesador de logs ligero desplegado frecuentemente como sidecar para recolectar y enviar logs sin modificar la aplicación principal.
- **Recursos:**
  - [Sidecar pattern](https://learn.microsoft.com/es-es/azure/architecture/patterns/sidecar): Guía de Microsoft Azure sobre el aislamiento de componentes auxiliares.

</details>


### Patrones de Arquitectura de Observabilidad

<br>

*Mecanismos de telemetría que ofrecen una visibilidad externa profunda de la salud del sistema, el rendimiento y los estados internos complejos*

<details>
<summary><strong>Distributed Tracing:</strong> Rastrea el flujo de una petición a través de múltiples microservicios pasando un ID de traza único a lo largo de toda la cadena de llamadas.</summary>

Patrón crítico para depurar microservicios, permitiendo visualizar exactamente dónde ocurre la latencia o los errores en una red compleja de llamadas a APIs internas analizando tramos (spans) y trazas.

- **Herramientas Estándar:**
  - [jaegertracing/jaeger](https://github.com/jaegertracing/jaeger): Sistema de trazabilidad distribuida de código abierto para monitorizar y depurar arquitecturas complejas de microservicios.
  - [openzipkin/zipkin](https://github.com/openzipkin/zipkin): Ayuda a recopilar datos de tiempo necesarios para solucionar problemas de latencia en arquitecturas de servicios.
- **Recursos:**
  - [OpenTelemetry](https://opentelemetry.io/): Estándar CNCF para generar, recolectar y exportar datos de telemetría (métricas, logs y trazas).

</details>

<details>
<summary><strong>Log Aggregation:</strong> Centraliza y analiza archivos de registro localizados desde múltiples servicios e instancias en un único repositorio consultable.</summary>

Evita la pesadilla operativa de entrar en servidores individuales para leer archivos de texto, permitiendo consultas cruzadas entre servicios, visualización y alertas basadas en logs en toda la flota.

- **Herramientas Estándar:**
  - [fluent/fluentd](https://github.com/fluent/fluentd): Colector de datos para capas de registro unificadas.
  - [grafana/loki](https://github.com/grafana/loki): Sistema de agregación de logs escalable, altamente disponible y multi-inquilino inspirado en Prometheus.
- **Recursos:**
  - [The Twelve-Factor App: Logs](https://12factor.net/es/logs): Metodología para tratar logs como flujos de eventos.

</details>

<details>
<summary><strong>Metrics Collection (Time-Series):</strong> Reúne datos numéricos estructurados a lo largo del tiempo para monitorizar líneas base de salud y disparar alertas automatizadas.</summary>

A diferencia de los logs, las métricas se agregan matemáticamente y se comprimen mucho, permitiendo ingerir millones de puntos de datos por segundo para rastrear uso de CPU, límites de memoria y tasas de error HTTP.

- **Herramientas Estándar:**
  - [prometheus/prometheus](https://github.com/prometheus/prometheus): Estándar de la industria para monitorización de sistemas, con un modelo de datos multidimensional y lenguaje de consulta potente (PromQL).
  - [influxdata/telegraf](https://github.com/influxdata/telegraf): Agente impulsado por plugins para recolectar y reportar métricas.
- **Recursos:**
  - [Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/): Guía definitiva del libro SRE de Google.

</details>

<details>
<summary><strong>Synthetic Monitoring:</strong> Utiliza scripts automáticos para simular interacciones típicas de usuario con una aplicación para detectar proactivamente caídas de rendimiento.</summary>

A menudo llamado monitoreo de caja negra (black-box), confirma que las rutas críticas de usuario (como inicio de sesión o completar una compra) funcionan activamente desde la perspectiva del usuario, independientemente de las métricas internas del servidor.
- **Herramientas Estándar:**
  - [prometheus/blackbox_exporter](https://github.com/prometheus/blackbox_exporter): Permite sondeo de caja negra de endpoints sobre HTTP, HTTPS, DNS, TCP e ICMP.
  - [checkly/checkly-cli](https://github.com/checkly/checkly-cli): CLI para programar comprobaciones sintéticas usando Playwright para simular interacciones de navegador.
- **Recursos:**
  - [Practical Alerting](https://sre.google/sre-book/practical-alerting/): Capítulo del libro SRE de Google sobre el equilibrio entre monitoreo de caja blanca y caja negra.

</details>


### Patrones de Arquitectura DevOps

Paradigmas que unen el desarrollo de software y las operaciones de TI mediante automatización intensiva, flujos de entrega continua y gestión programática de infraestructura.

<details>
<summary><strong>GitOps:</strong> Paradigma que utiliza repositorios Git como única fuente de verdad para gestionar automáticamente la provisión de infraestructura y despliegues.</summary>

Mantiene el estado del clúster o infraestructura sincronizado con la configuración declarativa guardada en Git. Si ocurre una desviación, el controlador GitOps reconcilia automáticamente el sistema al estado definido en Git.
- **Herramientas Estándar:**
  - [argoproj/argo-cd](https://github.com/argoproj/argo-cd): Herramienta de entrega continua declarativa para Kubernetes que sincroniza el estado de la aplicación con Git.
  - [fluxcd/flux2](https://github.com/fluxcd/flux2): Soluciones de entrega continua y progresiva para Kubernetes, base del toolkit de GitOps.
- **Recursos:**
  - [GitOps Principles](https://opengitops.dev/): Estándares y principios neutrales mantenidos por el grupo OpenGitOps dentro de la CNCF.

</details>

<details>
<summary><strong>Infrastructure as Code (IaC):</strong> Gestiona y provisiona entornos de computación completos mediante archivos de definición legibles por máquina en lugar de configuraciones manuales.</summary>

Este enfoque lleva las prácticas de ingeniería de software (pruebas, revisión de código, versionado) a la gestión de infraestructura, eliminando problemas de consistencia entre entornos.
- **Herramientas Estándar:**
  - [hashicorp/terraform](https://github.com/hashicorp/terraform): Herramienta de infraestructura como código que permite gestionar servicios de nube de forma declarativa.
  - [pulumi/pulumi](https://github.com/pulumi/pulumi): Plataforma de IaC moderna que permite definir infraestructura en lenguajes familiares como TypeScript, Python o Go.
- **Recursos:**
  - [Infrastructure as Code](https://martinfowler.com/bliki/InfrastructureAsCode.html) por Martin Fowler.

</details>

<details>
<summary><strong>Continuous Integration / Continuous Deployment (CI/CD):</strong> Patrón de flujos automatizados que integran código, ejecutan tests y despliegan la construcción final a producción.</summary>

La Integración Continua asegura que los cambios se unifiquen y validen frecuentemente, mientras que el Despliegue Continuo lanza automáticamente cada construcción que pasa los tests sin intervención manual.
- **Herramientas Estándar:**
  - [gitlabhq/gitlabhq](https://github.com/gitlabhq/gitlabhq): Proporciona un motor de flujos CI/CD integrado que gestiona todo el ciclo de vida del software.
  - [tektoncd/pipeline](https://github.com/tektoncd/pipeline): Framework nativo de nube para crear sistemas de integración y entrega continua en Kubernetes.
- **Recursos:**
  - [Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html) por Martin Fowler.

</details>


### Patrones de Arquitectura FinOps

Prácticas de diseño e ingeniería optimizadas para la gestión financiera en la nube, haciendo que los costes variables sean visibles, predecibles y correlacionados con el valor de negocio.

<details>
<summary><strong>Estrategia de Etiquetado de Recursos:</strong> Impone un esquema estricto de metadatos en todos los recursos de nube para mapear costes a equipos, entornos o dominios.</summary>

Práctica central de FinOps que exige que cada activo en la nube tenga metadatos adjuntos (ej. `CentroDeCoste: Marketing`). Esto transforma una factura compleja en datos financieros categorizables que pueden ser analizados por unidad de negocio.
- **Herramientas Estándar:**
  - [cloud-custodian/cloud-custodian](https://github.com/cloud-custodian/cloud-custodian): Motor de reglas para nubes que automatiza el cumplimiento de etiquetas y alerta sobre violaciones.
  - [infracost/infracost](https://github.com/infracost/infracost): Muestra estimaciones de coste para proyectos de infraestructura como código directamente en el flujo CI/CD.
- **Recursos:**
  - [Tagging Strategy Best Practices](https://docs.aws.amazon.com/whitepapers/latest/tagging-best-practices/tagging-best-practices.html): Guía de AWS sobre diseño e implementación de etiquetas efectivas.

</details>

<details>
<summary><strong>Showback / Chargeback:</strong> Capacidad arquitectónica para asignar costes operativos de nube a las unidades de negocio que los consumieron.</summary>

Mueve el gasto en la nube de un gasto general de TI a un modelo de responsabilidad descentralizada. El Showback reporta los costes precisos a los equipos para concienciación, mientras que el Chargeback deduce esos costes de los presupuestos departamentales.
- **Herramientas Estándar:**
  - [opencost/opencost](https://github.com/opencost/opencost): Herramienta de monitoreo de costes de código abierto para Kubernetes para asignar costes de clústeres compartidos.
  - [kubecost/cost-analyzer-helm-chart](https://github.com/kubecost/cost-analyzer-helm-chart): Plataforma que ofrece visibilidad granular de costes y recomendaciones de optimización para entornos nativos de nube.
- **Recursos:**
  - [¿Qué es FinOps?](https://www.ibm.com/es-es/topics/finops): Visión técnica de gestión financiera en la nube y modelos de responsabilidad.

</details>


### Patrones de Arquitectura Federada

Modelos de sistemas descentralizados que permiten que múltiples entidades autónomas interoperen de forma segura usando estándares compartidos sin una autoridad central fija.

<details>
<summary><strong>Federación de Datos:</strong> Define una interfaz de consulta unificada en tiempo real a través de múltiples almacenes de datos autónomos sin duplicidad física.</summary>

Crea una base de datos virtual, abstrayendo la complejidad del almacenamiento y permitiendo consultar datos como si estuvieran en un solo lugar, reduciendo la necesidad de flujos ETL costosos.
- **Herramientas Estándar:**
  - [prestodb/presto](https://github.com/prestodb/presto): Motor de consultas SQL distribuidas para ejecutar análisis interactivos contra fuentes de datos de cualquier tamaño.
  - [apache/drill](https://github.com/apache/drill): Motor de consultas SQL sin esquema para Hadoop y NoSQL, permitiendo consultar formatos complejos en su sitio original.
- **Recursos:**
  - [Federated Database System](https://en.wikipedia.org/wiki/Federated_database_system): Resumen de arquitectura e historia de integraciones virtuales en Wikipedia.

</details>

<details>
<summary><strong>GraphQL Federation:</strong> Patrón de puerta de enlace (gateway) que combina múltiples APIs GraphQL independientes en un único esquema unificado para el cliente.</summary>

Permite que diferentes equipos de dominio desarrollen y escalen sus propias partes de una API de forma independiente, ofreciendo al cliente un único endpoint para obtener todos los datos relacionados en una petición.
- **Herramientas Estándar:**
  - [apollographql/federation](https://github.com/apollographql/federation): Arquitectura declarativa y herramientas para construir y gestionar un supergrafo unificado a partir de subgrafos.
  - [wundergraph/cosmo](https://github.com/wundergraph/cosmo): Router y herramientas de código abierto para gestionar APIs federadas en equipos distribuidos.
- **Recursos:**
  - [Introduction to Apollo Federation](https://www.apollographql.com/docs/federation/): Documentación técnica sobre arquitectura de subgrafos.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)

## Marcos de Trabajo de Arquitectura Empresarial

<br>

Son formas de gestionar cómo una gran empresa vincula su estrategia de negocio con su tecnología. No son arquitecturas de software en sentido estricto; definen cómo trabajan juntos los procesos de negocio, los datos y las herramientas técnicas. Estos marcos ayudan a alinear los objetivos corporativos con el trabajo técnico para apoyar el crecimiento a largo plazo.

<details>
<summary><strong>Arquitectura de Negocio:</strong> Define la estrategia, gobernanza, organización y procesos clave de negocio.</summary>

Es el puente entre el modelo de negocio y la estrategia corporativa por un lado, y la funcionalidad técnica por el otro. Visualiza cómo la organización crea valor y alinea todas las arquitecturas posteriores directamente con los objetivos de la empresa.

- **Herramientas Estándar:**
  - [leanix/leanix](https://www.leanix.net/): Plataforma de gestión de Arquitectura Empresarial (EAM) usada para alinear capacidades con el paisaje de TI.
  - [signavio/process-manager](https://www.signavio.com/): Herramienta de modelado de procesos de negocio a escala empresarial (parte de SAP).
- **Recursos:**
  - [Business Architecture Basics](https://bizzdesign.com/blog/what-is-business-architecture/): Resumen de valor, estructura y técnicas de mapeo de la disciplina.

</details>

<details>
<summary><strong>Arquitectura de Información (Arquitectura de Datos):</strong> Describe la estructura de los activos de datos lógicos y físicos de una organización.</summary>

Se centra en cómo se recopilan, almacenan, integran y utilizan los datos en toda la empresa. Trata los datos como un activo corporativo valioso y gobernado más que como un subproducto de las aplicaciones individuales.

- **Herramientas Estándar:**
  - [schemaspy/schemaspy](https://github.com/schemaspy/schemaspy): Herramienta de código abierto que analiza metadatos de bases de datos para generar representaciones visuales.
  - [collibra/data-intelligence](https://www.collibra.com/): Plataforma para gobernanza de datos empresarial, privacidad y catalogación.
- **Recursos:**
  - [DAMA-DMBOK](https://www.dama.org/cpages/body-of-knowledge): El cuerpo de conocimiento de gestión de datos, el marco estándar para arquitectura y gobernanza.

</details>

<details>
<summary><strong>Arquitectura de Aplicaciones:</strong> Define un plano para las aplicaciones individuales a desplegar, sus interacciones y su relación con los procesos de negocio.</summary>

Mapea toda la cartera de software de una empresa, identificando redundancias, gestionando la deuda técnica y verificando que las soluciones de software apoyen las capacidades de negocio.

- **Herramientas Estándar:**
  - [archimatetool/archi](https://github.com/archimatetool/archi): Toolkit de modelado de código abierto para crear modelos ArchiMate.
  - [bizzdesign/horizzon](https://bizzdesign.com/): Plataforma de arquitectura empresarial que vincula carteras de aplicaciones con objetivos.
- **Recursos:**
  - [ArchiMate](https://en.wikipedia.org/wiki/ArchiMate): Lenguaje de modelado de arquitectura empresarial abierto e independiente.

</details>

<details>
<summary><strong>Arquitectura Tecnológica:</strong> Describe las capacidades lógicas de software y hardware necesarias para soportar los servicios de aplicaciones y datos.</summary>

La capa central que detalla el hardware físico y virtualizado, entornos de computación en la nube y topologías de red que alojan las aplicaciones y datos de la empresa de forma segura.

- **Herramientas Estándar:**
  - [structurizr/structurizr](https://github.com/structurizr): Herramienta basada en el modelo C4 para visualizar arquitectura de software y tecnología.
  - [drawio/drawio](https://github.com/jgraph/drawio): Herramienta de diagramación ampliamente usada para diseñar infraestructuras y redes.
- **Recursos:**
  - [The C4 Model](https://c4model.com/): Enfoque de "abstracción primero" para diagramar arquitectura desde el contexto del sistema hasta la capa tecnológica.

</details>

<details>
<summary><strong>Arquitectura de Seguridad:</strong> Procesos y controles para proteger la información y los activos de TI de la empresa.</summary>

Va más allá de los cortafuegos simples para definir el diseño de gestión de riesgos, gobernanza de identidad y mitigación de amenazas integrado en todos los dominios arquitectónicos.

- **Herramientas Estándar:**
  - [owasp/threat-dragon](https://github.com/OWASP/threat-dragon): Herramienta de modelado de amenazas para diseñar arquitecturas seguras e identificar vulnerabilidades estructurales.
  - [osquery/osquery](https://github.com/osquery/osquery): Framework de instrumentación de sistemas operativos para visibilidad profunda de seguridad y auditoría de cumplimiento.
- **Recursos:**
  - [SABSA Framework](https://sabsa.org/): Metodología líder para arquitectura de seguridad empresarial guiada por el negocio.

</details>

<details>
<summary><strong>Arquitectura Geoespacial:</strong> Incorpora datos y servicios basados en la ubicación en la arquitectura empresarial.</summary>

Dominio especializado crítico para logística, agricultura y administración pública, centrado en cómo se capturan, procesan y sirven los datos espaciales (mapas, coordenadas).

- **Herramientas Estándar:**
  - [postgis/postgis](https://github.com/postgis/postgis): Extensión espacial para PostgreSQL, núcleo de muchos sistemas geoespaciales empresariales.
  - [geoserver/geoserver](https://github.com/geoserver/geoserver): Servidor de código abierto para compartir y editar datos geoespaciales basados en estándares abiertos.
- **Recursos:**
  - [OGC Reference Model](https://www.ogc.org/standards/orm): Marco de estándares para protocolos e interfaces de integración de datos espaciales.

</details>

<details>
<summary><strong>Arquitectura Social:</strong> Modela las interacciones de la empresa con individuos y comunidades a través de diversos canales.</summary>

Dominio emergente que mapea cómo una organización facilita la colaboración interna, el intercambio de conocimiento y el compromiso con comunidades externas, alineando redes humanas con sistemas de TI.

- **Herramientas Estándar:**
  - [mattermost/mattermost-server](https://github.com/mattermost/mattermost-server): Plataforma de mensajería de código abierto para construir arquitecturas colaborativas seguras.
  - [discourse/discourse](https://github.com/discourse/discourse): Estándar para plataformas de discusión, usado para construir arquitecturas de comunidades externas resilientes.
- **Recursos:**
  - [Social Architecture](https://en.wikipedia.org/wiki/Social_architecture): Resumen teórico sobre el diseño de sistemas para la interacción humana.
  - [Digital Ecosystem](https://en.wikipedia.org/wiki/Digital_ecosystem): Exploración de las redes interconectadas de humanos y sistemas de TI.

</details>

<br>

[![Volver arriba](https://img.shields.io/badge/-Volver_arriba-6f42c1?style=for-the-badge&logoColor=white)](#índice)


