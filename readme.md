

# What is Software Architecture



monolithic architectures
* layered architecture
* micro-kernel architecture
* pipeline architecture

distributed architectures
* event-driven architecture
* space-based architecture
* microservices architecture
* service-oriented architecture
* service-base architecture




# Understanding Microservices Architecture

Es una arquitectura muy popular, gracias al éxito de compañías como Netflix, Amazon, etc. Esta arquitectura tiene beneficios en términos de escalabilidad y agilidad que otras arquitecturas no tienen.

![](img/microservices-architecture.png)

## Características

### Distributed

* Cada uno de los servicios corren en sus propios procesos y tipicamente son desplegados individualmente
* Cada uno de sus componentes hablan unos a otros de una forma distribuida usando: 
    * Comunicación síncrona con protocolos como HTTP, REST o SOAP
    * Comunicación asíncrona usando **event queues**
* Interoperabilidad heterogénea consciente del protocolo
    * El consumidor necesita saber del protocolo de la cosa de la cual está consumiendo. Otras arquitectura remueven esta restricción usando middlewares. En la arquitectura de microservicios no hay middlewares.
    * Necesito saber si el endpoint que estoy llamado es REST, message queue u otro tipo de protocolo.
    * Heterogéneo implica que sistemas distintos construidos con distintos lenguajes se pueden comunicar
    * Interoperabilidad implica que una cosa pueda llamar a otra cosa

![](img/protocol-aware-heterogeneous-interoperability.png)

### Separately deployed

* Cada pieza (service component) puede ser desplegada de forma independiente
* El despliegue puede ser completamente automatizado
* La adopción de una arquitectura de microservicios implica el conocimiento de una serie de prácticas técnicas
* Una de las ventajas poderosa de esta arquitectura es el extremo despliegue desacoplado

![](img/practicas-tecnicas.png)

### Service component 

* Los componente tienden a ser pequeños, por eso el nombre de microservices
* Tipos de service components
    * functional services: 
    * infraestructure services: monitoring, logging, authentication, authorization, etc. 
    * messaging services: 
* La comunicación es siempre point-to-point
* En esta arquitectura si no monitoreas un componente, no lo ves
![](img/service-components.png)


Services templates
* Es la base sobre la que construyes un servicio
* Contiene infraestructura predefinida, cosas que queremos de manera consistente a través de toda la arquitectura
    * logging
    * monitoring
    * A&A: Authentication and Authorization
* El equipo extiende el service template y construye su funcionalidad dentro de él.
* Herramientas
    * Spring Boot
    * Dropwizard


Una de las ideas importante de la arquitectura de microservicios es: el acoplamiento es malo
La **duplicación** es preferible al acoplamiento
Los Services templates son los ideales para compartir código en cada servicio

¿Qué pasa si implementas A&A como microservicio?
* latencia en cada request: muchas peticiones al servicio de A&A. Esto es un candidato para colocarlo en un service template


### Bounded context

* Es la idea más fuerte detrás de este estilo arquitectónico
* Cualquier cosa de importancia en esta arquitectura debe ser encapsulada en un **bounded context**. Incluye data y persistencia
* Cada uno de los componentes actúa como LEGOs
* problema: data replication

### Data domains

* ?

### API Layer

* Fachada que expones endpoints al exterior
* endpoint proxy
    * apache
    * IIS
    * Nginx
    * Proxy server
    * ziproxy
* load balancer
    * Barracuda
    * neustar
    * f5
    * Citrix NetScaler
* gateway (integration hub)
    * apache camel
    * muleESB
    * 

### Event driven

* lo común es la comunicación asíncrona
* hacer rollbacks distribuidos es muy difícil





## ¿Cuál es le tamaño correcto para un microservicio?

Para determinar el tamaño, debemos considerar lo siguiente: 

* Cuál es el propósito de este microservicio
* transactions
* choreography

El término microservicio fue popularizado por un post de Martin Fowler y James Lewis

Microservice is a "label" not a "description"


Los componentes de un arquitectura microservicios incluyen la base de datos


## Service orchestration

* No existe un mediador
* ¿como se manejan las coordinaciones complejas entre servicios?
* Patrones
    * Front ochestrator: ponenmos algo de la responsabilidad de la mediación en el primer servicio que llamos en la serie
        * es optimista ¿que pasa si algo falla?
        * implica comunicación síncrona
    * event queues
        * fire-and-forget version
        * 




## Links
* https://learning.oreilly.com/library/view/microservices-vs-service-oriented/9781491975657/ch04.html