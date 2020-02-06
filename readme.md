

# What is Software Architecture

La arquitectura de software implica:
* Estructura
    * Patrones de arquitectura
    * Abarca las "ilities"
* Decisiones de arquitectura
    * only the business and services layers can access the persistence layer
    * all shared objects use by business objects in the business layer should reside in the shared service layer
* Principios de diseño
    * inter-service communications should leverage async messaging whenever possible to increse performance

# Understanding the expectations of an architect

Dentro del rol del arquitecto de software, lo que se espera que un arquitecto haga es:

1. Definir la arquitectura y los los principios de diseño para guiar las decisiones tecnológicas para la empresa.
2. Definir la viabilidad de una arquitectura a corto, mediano y largo plazo
3. Analyze technology and industry trends and keep current with the latest trends
4. Asegurar el cumplimiento de la arquitectura
5. Have exposure to multiple and diverse technologies, platforms and environments
6. Have a certain level of business domain expertise. Usa el lenguaje que usa el negocio
7. Possess exceptional interpersonal skills, including teamwork, facilitation and negotiation
8. Understand the political climate of the enterprise and be able to navigate the politics

# Thinking like an architect

Si pensamos en todo el conocimiento del universo, lo podemos dividir en tres grandes bloques:

* cosas que conoces
* cosas que sabes que no conoces
* cosas que no sabes que no conoces

Como arquitecto, tu foco está en las "cosas que sabes que no conoces"

La forma de convertirse en arquitcto es mostrando expertise en una variedad de diversas áreas técnicas.

![](img/stuff-you-know.png)

## ¿Cuál es la línea divisioria entre diseño y arquitectura?

En realidad, no existe. 

El arquitecto:

* Identificar las caraterísticas arquitecturales (ilities)
* Identificar los patrones de arquitectura más adecuados para la aplicación (microservices, micro-kernel,...)
* Identificar los bloques principales de la arquitectura

El desarrollador:
* Diseñar los componentes que el arquitecto identificó
* Diseñar la experiencia de usuario
* Codificar

Tiene que haber una comunicación bidireccional entre arquitectos y desarrolladores.

Para que un arquitecto esté involucrado con el código fuente debe:
* Hacer experimentos (spikes)
* Hacer Pair Programming
* Code reviews

> El pair programming sería una buena práctica para mejorar la calidad del código y para formar a nuevos miembros del equipo.



# Identifying Architecture Characteristics

Tanto el desarrollador como el arquitecto están pendientes de la funcionalidad de una aplicación. Sin embargo, el arquitecto tiene responsabilidades adicionales, las cuales son las otras características arquitecturales de la aplicación:
* reliability
* scalability
* functionality
* performance
* availability

Los atributos de calidad no vienen de requerimientos, historias de usuario, etc. sino vienen del negocio. **Es un proceso de escuchar y traducir a requerimientos no funcionales**.

¿Cómo se relaciona la identificación de los atributos de calidad con los patrones arquitecturales?
Hay cierto patrones que promueven niveles altos de testability, deployability, performance y scalability. Por lo tanto, elegir el patrón equivocado no nos permitirá lograr los objetivos.

Entre los diferentes patrones tenemos:
* monolithic architectures
    * layered architecture
    * micro-kernel architecture
    * pipeline architecture
* distributed architectures
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

### API Layer

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

### Event driven

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



<hr />

# MODULE II: FOUNDATIONS

## Chapter 2. Architectural Thinking

A diferencia de un developer, un arquitecto debe desarrollar un "pensamiento arquitectónico". El pensamiento arquitectónico implica:
* Entender la diferencia entre arquitectura y diseño
* Tener una amplia gama de conocimientos técnicos y al mismo tiempo mantener un cierto nivel de profundidad técnica
* Entender, analizar y reconciliar trade-offs entre varias soluciones y tecnologías
* Entender los requisitos de negocio y traducirlos a características arquitectónicas

### Arquitectura vs Diseño

* La visión tradicional de arquitectura y diseño es la siguiente:
![](img/responsabilidades-arq-dev.png)
* Entender la diferencia entre arquitectura y diseño y ver cómo ambos se integran
* Para que la arquitectura funcione, los arquitectos y desarrolladores deben trabajar juntos (estar en el mismo equipo). El arquitecto debe proporcionar tutoría y entrenamiento a los desarrolladores del equipo.
* ¿Cuál es la línea que divide la arquitecta y el diseño? No existe. Ambos están integrados y deben mantenerse sincronizados 

![](img/arquitectura-vs-diseno.png)

### Amplitud técnica
Mienras que un desarrollador debe tener una profundidad técnica para realizar su trabajo, un arquitecto debe tener una amplitud técnica para pensar desde un punto de vista de la arquitectura.

Cualquier individuo puede dividir todos sus conocimientos en tres secciones: cosas que sabe, cosas que sabe que no sabe y cosas que no sabe que no sabe.

![](img/piramide-conocimiento.png)

Sin embargo, la naturaleza del conocimiento cambia a medida que los desarrolladores hacen la transición al papel de arquitecto. Una gran parte del valor de un arquitecto es una amplia comprensión de la tecnología y de cómo utilizarla para resolver problemas concretos. Por ejemplo, como arquitecto, es más beneficioso saber que existen cinco soluciones para un problema particular que tener conocimientos singulares en una sola.

![](img/amplitud-profundidad-tecnica.png)

Equilibrar su cartera de conocimientos en cuanto a profundidad y amplitud es algo que todo desarrollador debería considerar a lo largo de su carrera.


### Analyzing Trade-Offs

Pensar como arquitecto implica en evaluar los trade-offs de cada alternativa para elegir la mejor solución.

```
La arquitectura es lo que no puedes buscar en Google
```

Todo en la arquitectura es un trade-off, por lo que la famosa respuesta a cada pregunta de arquitectura es "depende". No se puede buscar en Google si los microservicios es el estilo de arquitectura correcto, porque depende del entorno de implementación, de los drivers de negocio, de la cultura de la empresa, del presupuesto, de los plazos, del conjunto de habilidades del desarrollador y muchos otros factores más.

El entorno, la situación y el problema de cda uno es diferente, de ahí que la arquitectura sea tan difícil.

```
Los programadores conocen los beneficios de todo y los trade-offs de nada. Los arquitectos necesitan entender ambas cosas.
```

Pensar arquitectónicamente implica observar los beneficios de una solución dada, pero también analizar los aspectos negativos.

Todo en la arquitectura tiene un trade-off: una ventaja y una desventaja. Pensar como arquitecto es pensar en estos trade-off y luego preguntarse "¿Qué es más importante: la extensibilidad o la seguridad?". La decisión entre las diferentes soluciones siempre dependerá de los drivers de negocio, el entorno y otra serie de factores más.

### Understanding Business Drivers

Pensar como arquitecto requiere entender los requerimientos de negocio para luego traducirlos en características de la arquitectura (escalabilidad, rendimiento, disponibilidad, etc.). Es una tarea compleja porque requiere conocimiento del negocio y buenas relaciones con los principales stakeholders de la empresa.

### Balancing Architecture and Hands-On Coding

Todo arquitecto debe codificar y tener un cierto nivel de profundidad técnica. Algunas formas de que un arquitecto practique la codificación son:
* Hacer pruebas de concepto (POCs): Esto permite validar una decisión de arquitectura teniendo en cuenta los detalles de la implementación.
* Abordar los casos de deuda técnica o de arquitectura.
* Automatizar tareas repetitivas. El equipo de desarrollo agradecerá la automatización.
* Hacer code reviews frecuentemente.


<hr />

# MODULE III: ARCHITECTURE STYLES

## Chapter 9. Foundations

URL: https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch09.html#ch-architecture-styles

Los estilos arquitectónicos (algunas veces llamados patrones de arquitectura) describen una relación nombrada de componentes que cubren una variedad de características de la arquitectura.

Los arquitectos deben estar familiarizados con los nombres básicos de los estilos arquitectónicos genéricos fundamentales.

### Fundamental Patterns

#### Big Ball of Mud

Se refiere a la ausencia de cualquier estructura arquitectónica.

![](img/big-ball-mud.png)

#### Unitary Architecture

La arquitectura unitaria se refiere a un sistema específico que funciona en un hardware específico. 

Investigar: "embedded systems"
https://www.guru99.com/embedded-systems-tutorial.html


#### Client/Server

Con el tiempo, cuando las redes de computadoras se hicieron común, surgió la necesidad de separar en partes un sistema (sistema distribuido).

La arquitectura Cliente/Servidor consiste en separar la funcionalidad técnica entre el frontend y backend. A este estilo arquitectónico también se lo conocomo como **two-tier**.

Algunos sabores de estilo arquitectónico son:
* DESKTOP + DATABASE SERVER
* BROWSER + WEB SERVER
* THREE-TIER

### Monolithic Versus Distributed Architectures

Los estilos de arquitectura pueden clasificarse en dos tipos principales: monolíticos (una sola unidad de despliegue de todo el código) y distribuidos (múltiples unidades de despliegue conectadas a través de protocolos de acceso remoto.

Monolithic
* Layered architecture
* Pipeline architecture
* Microkernel architecture

Distributed
* Service-based architecture
* Event-driven architecture
* Space-based architecture
* Service-oriented architecture
* Microservices architecture

Los estilos de arquitectura distribuida, aunque son mucho más poderosos en términos de rendimiento, escalabilidad y disponibilidad que los estilos de arquitectura monolítica, tienen importantes trade-offs por este poder.

El primer grupo de problemas a los que se enfrentan todas las arquitecturas distribuidas se describen en las "falacias de la informática distribuida"
* Falacia #1: La red es confiable
* Falacia #2: La latencia es cero
* Falacia #3: El ancho de banda es infinito
* Falacia #4: La red es segura
* Falacia #5: La topología nunca cambia
* Falacia #7: El costo de transporte es cero
* Falacia #8: La red es homogénea

Otras consideraciones distribuidas
* DISTRIBUTED LOGGING
* DISTRIBUTED TRANSACTIONS
* CONTRACT MAINTENANCE AND VERSIONING

