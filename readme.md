
## Tabla de contenido
- [MODULE I: FOUNDATIONS](#)
    - [Chapter 2. Architectural Thinking](#chapter-2-architectural-thinking)
    - [Chapter 3. Modularity](#chapter-3-modularity)
    - [Chapter 4. Architecture Characteristics Defined](#chapter-4-architecture-characteristics-defined)
    - [Chapter 5. Identifying Architectural Characteristics](#chapter-5-identifying-architectural-characteristics)
    - [Chapter 6. Measuring and Governing Architecture Characteristics](#chapter-6-measuring-and-governing-architecture-characteristics)
    - [Chapter 7. Scope of Architecture Characteristics](#chapter-7-scope-of-architecture-characteristics)
    - [Chapter 8. Component-Based Thinking](#chapter-8-component-based-thinking)
- [MODULE II: ARCHITECTURE STYLES](#)
    - [Chapter 9. Foundations](#chapter-9-foundations)
    - [Chapter 10. Layered Architecture Style](#chapter-10-layered-architecture-style)
    - [Chapter 11. Pipeline Architecture Style](#)
    - [Chapter 12. Microkernel Architecture Style](#)
    - [Chapter 13. Service-Based Architecture Style](#)
    - [Chapter 14. Event-Driven Architecture Style](#)
    - [Chapter 15. Space-Based Architecture Style](#)
    - [Chapter 16. Orchestration-Driven Service-Oriented Architecture](#)
    - [Chapter 17. Microservices Architecture](#)
    - [Chapter 18. Choosing the Appropriate Architecture Style](#)

## MODULE I FOUNDATIONS

Para comprender los importantes trade-offs en la arquitectura, los desarrolladores deben entender algunos conceptos y terminología básicos relativos a los componentes, la modularidad, el acoplamiento y la connascence.

### Chapter 2. Architectural Thinking

URL: https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch02.html

A diferencia de un developer, un arquitecto debe desarrollar un "pensamiento arquitectónico". El pensamiento arquitectónico implica:
* Entender la diferencia entre arquitectura y diseño
* Tener una amplia gama de conocimientos técnicos y al mismo tiempo mantener un cierto nivel de profundidad técnica
* Entender, analizar y reconciliar trade-offs entre varias soluciones y tecnologías
* Entender los requisitos de negocio y traducirlos a características arquitectónicas

#### Arquitectura vs Diseño

* La visión tradicional de arquitectura y diseño es la siguiente:
![](img/responsabilidades-arq-dev.png)
* Entender la diferencia entre arquitectura y diseño y ver cómo ambos se integran
* Para que la arquitectura funcione, los arquitectos y desarrolladores deben trabajar juntos (estar en el mismo equipo). El arquitecto debe proporcionar tutoría y entrenamiento a los desarrolladores del equipo.
* ¿Cuál es la línea que divide la arquitecta y el diseño? No existe. Ambos están integrados y deben mantenerse sincronizados 

![](img/arquitectura-vs-diseno.png)

#### Amplitud técnica
Mienras que un desarrollador debe tener una profundidad técnica para realizar su trabajo, un arquitecto debe tener una amplitud técnica para pensar desde un punto de vista de la arquitectura.

Cualquier individuo puede dividir todos sus conocimientos en tres secciones: cosas que sabe, cosas que sabe que no sabe y cosas que no sabe que no sabe.

![](img/piramide-conocimiento.png)

Sin embargo, la naturaleza del conocimiento cambia a medida que los desarrolladores hacen la transición al papel de arquitecto. Una gran parte del valor de un arquitecto es una amplia comprensión de la tecnología y de cómo utilizarla para resolver problemas concretos. Por ejemplo, como arquitecto, es más beneficioso saber que existen cinco soluciones para un problema particular que tener conocimientos singulares en una sola.

![](img/amplitud-profundidad-tecnica.png)

Equilibrar su cartera de conocimientos en cuanto a profundidad y amplitud es algo que todo desarrollador debería considerar a lo largo de su carrera.


#### Analyzing Trade-Offs

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

#### Understanding Business Drivers

Pensar como arquitecto requiere entender los requerimientos de negocio para luego traducirlos en características de la arquitectura (escalabilidad, rendimiento, disponibilidad, etc.). Es una tarea compleja porque requiere conocimiento del negocio y buenas relaciones con los principales stakeholders de la empresa.

#### Balancing Architecture and Hands-On Coding

Todo arquitecto debe codificar y tener un cierto nivel de profundidad técnica. Algunas formas de que un arquitecto practique la codificación son:
* Hacer pruebas de concepto (POCs): Esto permite validar una decisión de arquitectura teniendo en cuenta los detalles de la implementación.
* Abordar los casos de deuda técnica o de arquitectura.
* Automatizar tareas repetitivas. El equipo de desarrollo agradecerá la automatización.
* Hacer code reviews frecuentemente.

<div align="right"><small><a href="#tabla-de-contenido">volver al inicio</a></small></div>

### Chapter 3. Modularity

URL: https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch03.html

Algunas ideas generales:
* La modularidad es un principio organizador. 
* Muchas de las herramientas para analizar la arquitectura (metrics, fitness functions y visualizations) se basan en el concepto de modularidad.
* Si un arquitecto diseña un sistema sin prestar atención a cómo se conectan las piezas, terminan creando un sistema que presenta innumerables dificultades.
* Para usar una analogía física, los sistema de software modelan sistemas complejos que tienden a la entropía (desorden). La energía debes ser añadida a un sistema físico para preservar el orden. Lo mismo ocurre con los sistemas de software: los arquitectos deben gastar constantemente energía para asegurar una buena solidez estructural, lo que no ocurriría por accidente.

### Definition

Utilizamos la modularidad para describir una *agrupación lógica de código relacionado*, que podría ser un grupo de clases en un lenguaje OO o funciones en un lenguaje estructura o funcional.

La mayoría de lenguajes proporcionan mecanismos de modularidad:
* Paquete en Java
* Espacio de nombres en .NET
* ...

Los desarrolladores típicamente usan módulos como una forma de agrupar código relacionado. Por ejemplo, el paquete com.mycompany.customer en Java debería contener cosas relacionadas con los clientes.

Para las discusiones sobre arquitectura, usamos la modularidad como un término general para denotar una agrupación de código relacionado: clases, funciones, o cualquier otra agrupación. **Esto no implica una separación física, sino simplemente lógica**; la diferencia es a veces importante. 

### Measuring Modularity

Dada la importancia de la modularidad para los arquitectos, necesitan herramientas para entenderla. Afortunadamente, los investigadores crearon una variedad de métricas agnósticas del lenguaje para ayudar a los arquitectos a entender la modularidad. Nos centramos en tres conceptos clave: 
* Cohesión
* Acoplamiento
* Connascence

#### Cohesión

Es una medida de cuán relacionadas están las partes entre sí. Idealmente, un **módulo cohesivo** es aquel en el que todas las partes deben estar empaquetadas juntas, porque para romperlas en piezas más pequeñas sería necesario acoplar las partes entre sí mediante llamadas entre módulos para lograr resultados útiles.

```
El intento de dividir un módulo cohesivo sólo daría como resultado un mayor acoplamiento y una menor legibilidad.
Larry Constantine
```

Los científicos de la computación han definido una gama de medidas de cohesión, enumeradas aquí de mejor a peor:
* Functional cohesion
* Sequential cohesion
* Communicational cohesion
* Procedural cohesion
* Temporal cohesion
* Logical cohesion
* Coincidental cohesion

A pesar de tener siete variantes enumeradas, la cohesión es una métrica menos precisa que el acoplamiento. A menudo, el grado de cohesión de un módulo concreto queda a discreción de un arquitecto particular. 

Sorprendentemente, dada la subjetividad de la cohesión, los informáticos han desarrollado una buena métrica estructural para determinar la cohesión (o, más concretamente, la falta de cohesión). Un conjunto de métricas muy conocido, denominado conjunto de métricas orientadas a objetos de Chidamber y Kemerer, fue desarrollado por los autores homónimos para medir aspectos particulares de los sistemas de software orientados a objetos. 

La métrica **Chidamber and Kemerer Lack of Cohesion in Methods (LCOM)** mide la cohesión estructural de un módulo, típicamente un componente.


#### Acoplamiento

En 1979, Edward Yourdon y Larry Constantine publicaron *Structured Design: Fundamentals of a Discipline of Computer Program and Systems Design (Prentice-Hall)*, definiendo muchos conceptos centrales, incluyendo las métricas de acoplamiento aferente y eferente.

El acoplamiento aferente mide el número de conexiones entrantes a un artefacto de código (componente, clase, función, etc.). El acoplamiento eferente mide las conexiones salientes con otros artefactos de código. 

El libro anteriormente mencionado es anterior a la popularidad de los lenguajes orientados a objetos, centrándose en cambio en las construcciones de programación estructurada, como las funciones (no los métodos). También definió otros tipos de acoplamiento que no cubrimos aquí porque han sido suplantados por la conascencia.

¿Para qué sirve entender el acoplamiento?  Para ayudar a reestructurar, migrar o comprender una base de código.

#### Connascence

En 1996, Meilir Page-Jones publicó *What Every Programmer Should Know About Object-Oriented Design (Dorset House)* donde refinó las métricas de acoplamiento aferente y eferente reformulándolas para los lenguajes OO con un concepto que denominó **Connascence**. 

Dos componentes son **connascents** cuando deben cambiar de manera conjunta para que el sistema siga siendo válido: Si A cambia, entonces B debe cambiar.

TIPOS DE CONNASCENCE
* Static Connascence: acoplamiento a nivel de código fuente.
    * Connascence of Name (CoN)
    * Connascence of Type (CoT)
    * Connascence of Meaning (CoM) or Connascence of Convention (CoC)
    * Connascence of Position (CoP)
    * Connascence of Algorithm (CoA)
* Dynamic Connascence: Acoplamiento en tiempo de ejecución.
    * Connascence of Execution (CoE)
    * Connascence of Timing (CoT)
    * Connascence of Values (CoV)
    * Connascence of Identity (CoI)

CONNASCENCE PROPERTIES

Connascence es una herramienta de análisis para el arquitecto y los desarrolladores, y algunas propiedades de connascence ayudan a los desarrolladores a usarla sabiamente. La siguiente es una descripción de cada una de estas connascence properties:
* Strength
* Locality
* Degree

#### Unificando las métricas de acoplamiento y de Connascence

Hasta ahora, hemos discutido tanto el acoplamiento como la connascence, medidas de diferentes épocas y con diferentes objetivos. Sin embargo, desde el punto de vista de un arquitecto, estos dos puntos de vista se superponen. 

![](img/coupling-connascence.png)


### From Modules to Components

Los módulos son una colección de código relacionado. Sin embargo, **los arquitectos suelen pensar en términos de componentes, la manifestación física de un módulo**.

<div align="right"><small><a href="#tabla-de-contenido">volver al inicio</a></small></div>

### Chapter 4. Architecture Characteristics Defined

Además de los requisitos funcionales necesarios para desarrollar un sistema de software el arquitecto debe considerar otros factores para diseñar una solución de software. Una solución de software consiste de requerimientos funcionales y características arquitectónicas.

![](img/architecture-characteristics.png)

El arquitecto tiene la esponsabilidad clave de definir, descubrir y analizar de otro modo todas las cosas que el software debe hacer y que no están directamente relacionadas con la funcionalidad del dominio: las **características arquitectónicas**, las cuales describen los aspectos críticos para el éxito de la arquitectura, y por lo tanto del sistema en su conjunto.

Otros términos para referirse a las caractísticas arquitectónicas del software:
* Requerimientos no funcioanles
* Atributos de calidad

### Architectural Characteristics (Partially) Listed

Las característias de la arquitectura se pueden clasificar en las siguientes categorías:

* Operational Architecture Characteristics
    * Availability
    * Continuity
    * Performance
    * Recoverability
    * Reliability/safety
    * Robustness
    * Scalability
* Structural Architecture Characteristics: Relacionado a la estructura del código
    * Configurability
    * Extensibility
    * Installability
    * Leverageability/reuse
    * Localization
    * Maintainability
    * Portability
    * Supportability
    * Upgradeability
* Cross-Cutting Architecture Characteristics
    * Accessibility
    * Archivability
    * Authentication
    * Authorization
    * Legal
    * Privacy
    * Security
    * Supportability
    * Usability/achievability

![](img/development-operations-teams.jpeg)


### Trade-Offs and Least Worst Architecture

Las aplicaciones sólo pueden soportar algunas de las características de la arquitectura que hemos enumerado por una variedad de razones. 
* Cada una de las características soportadas requiere un esfuerzo de diseño
* El mayor problema radica en el hecho de que cada característica de la arquitectura a menudo tiene un impacto en otras.

```
Tip:
Nunca se busca la mejor arquitectura, sino la menos mala.
```

### Chapter 5. Identifying Architectural Characteristics

URL: https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch05.html

```
Identificar las características arquitectónicas es el primer paso para crear una arquitectura o determinar la validez de una arquitetura existente.
```

Para identificar las características arquitectónicas correctas para un determinado problema o aplicación el arquitecto debe:
* Comprender el dominio del problema
* Trabajar con los stakeholders para establecer lo que es verdaderamente importante desde la perspectiva del dominio.

Tres formas de descubrir las características arquitectónicas:
* extracting from domain concerns
* extracting from requirements
* extracting from implicit domain knowledge

### Extracting Architecture Characteristics from Domain Concerns

Un arquitecto debe ser capaz de identificar las características arquitectónicas correctas. Por ejemplo, ¿es la escalabilidad la preocupación más importante, o es la tolerancia a los fallos, la seguridad o el rendimiento? Tal vez el sistema requiere las cuatro características combinadas.

La comprensión de los objetivos clave del dominio y de la situación del dominio permite al arquitecto traducir esas preocupaciones del dominio en "-ilities", lo que luego constituye la base de decisiones arquitectónicas correctas y justificables.

Un antipatrón común en la arquitectura implica tratar de diseñar una arquitectura genérica, una que soporte todas las características de la arquitectura. El hecho de soportar demasiadas características arquitectónicas conduce a una complejidad cada vez mayor. No se obsesione con el número de características arquitectónicas, sino con la motivación para mantener el diseño simple.

En vez de tener un lista completa de características arquitectónicas para satisfacer, lo que se debe hacer es que lo stakeholders seleccionen las 3 características más importantes de la lista final. Esto no sólo hace mucho más fácil de lograr el consenso, sino que también fomenta los debates sobre lo que es más importante y ayuda al arquitecto a analizar los trade-offs cuando toma decisiones vitales en materia de arquitectura.

La mayoría de las características arquietctónicas se obtienen escuchando a los stakeholders y colaborando con ellos para determinar qué es importantes desde la perspectiva del negocio. 

Aunque esto puede parecer una actividad sencilla, el problema es que los arquitectos y los stakeholders del negocio hablan idiomas diferentes. Los arquitectos hablan de escalabilidad, interoperabilidad, tolerancia a los fallos, capacidad de aprendizaje y disponibilidad. Los stakeholders del negocio hablan de fusiones y adquisiciones, satisfacción del usuario, time to market y ventaja competitiva. 

Lo que sucede es un problema de "lost in translation" en el que el arquitecto y el stakeholder del negocio no se entienden entre sí. Los arquitectos no tienen ni idea de cómo crear una arquitectura que apoye la satisfacción del usuario, y los stakeholders del negocio no entienden por qué hay tanta atención y hablan de disponibilidad, interoperabilidad, capacidad de aprendizaje y tolerancia a los fallos en la aplicación. Afortunadamente, suele haber una traducción de las preocupaciones del dominio a las características de la arquitectura. 

![](img/domain-concerns-to-architecture-characteristics.png)

Recordar que normalmente un "Domain concern" implica satisfacer la combinación varias características arquitectónicas y hay que tener cuidado de no caer en la trampa de concentrarnos en uno sólo de ellos.

Qué significa "Lost in translation"
* http://spanishstudies.blogspot.com/2006/03/lost-in-translation.html
* https://www.bbc.com/mundo/noticias-48279142


### Extracting Architecture Characteristics from Requirements

Algunas características de la arquitectura provienen de declaraciones explícitas en los documentos de requisitos.

Otras provienen del conocimiento inherente del dominio por parte de los arquitectos, una de las muchas razones por las que el conocimiento del dominio es siempre beneficioso para los arquitectos.

![](img/7-product-dimensions.png)

### Architecture Katas
* https://www.youtube.com/watch?v=w_jSI5Xs1Ag
* https://blog.adrianbolboaca.ro/2013/01/architectural-kata/
* https://www.youtube.com/watch?v=quLrc3PbuIw&list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX
* http://nealford.com/katas/
* https://stevenschwenke.de/myFirstArchitecturalKata
* https://simplicable.com/new/system-architecture

<div align="right"><small><a href="#tabla-de-contenido">volver al inicio</a></small></div>

### Chapter 6. Measuring and Governing Architecture Characteristics

URL: https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch06.html

Vamos a aprender como expresar de manera concreta las características arquitectónicas más comunes, además de mecanismos de governanza.

En las organizaciones, hay tres problemas alrededor de las características arquitectónicas:
* No son físicas: Muchas características arquitectónicas tienen significados vagos.
* Tienen definiciones muy variadas: 
* Demasiada compuestos: Los desarrolladores pueden descomponer la agilidad en modularity, deployability y testability.

La necesidad de expresar de manera concreta las características arquitectónicas resuelven los problemas anteriores, es cuestión de ponerse de acuedo dentro de la organización.

### Measuring Architecture Characteristics

* Operational Measures
    * La performance y la scalability tienen mediciones directas que ofrecen interpretaciones variadas dependiendo de los objetivos del equipo.
    * Los equipos de alto nivel basan sus definiciones en el análisis estadístico.
    * Por ejemplo, digamos que un servicio de transmisión de video quiere monitorear la escalabilidad. En lugar de establecer un número arbitrario como objetivo, los ingenieros miden la escala a lo largo del tiempo y construyen modelos estadísticos, y luego dan la alarma si las métricas en tiempo real quedan fuera de los modelos de predicción.
* Structural Measures
    * Para medir la complejidad del código usamos la métrica **complejidad ciclomática**
    * Si los equipos no se fijan en la creciente complejidad gradual, esa complejidad dominará la base de código.
* Process Measures
    * ?

### Governance and Fitness Functions

Una vez que los arquitectos han establecido las características arquitectónicas y las han priorizado, ¿cómo pueden asegurarse de que los desarrolladores respetarán esas prioridades? 

#### Governing Architecture Characteristics
La gobernanza es una importante responsabilidad del rol del arquitecto

Garantizar la calidad del software dentro de una organización entra en el ámbito de la gobernanza de la arquitectura porque entra en el ámbito de la arquitectura, y la negligencia puede dar lugar a problemas de calidad desastrosos.

Soluciones para la gobernanza
* DevOps
* El libro Building Evolutionary Architectures (O'Reilly) describe una familia de técnicas, llamadas **fitness functions**, utilizadas para automatizar muchos aspectos del gobierno de la arquitectura.

#### Fitness Functions

Una fitness function (función de aptitud) se utiliza para evaluar lo cerca que está el resultado de alcanzar el objetivo.

Las prácticas de la arquitectura evolutiva toman prestado el concepto de fitness function de la computación evolutiva para crear una **architecture fitness function**

>**Architecture fitness function:** Cualquier mecanismo que proporcione una evaluación objetiva de la integridad de alguna característica de la arquitectura o combinación de características de la arquitectura

![](img/mechanisms-fitness-functions.png)

Se pueden utilizar muchas herramientas diferentes para implementar las fitness functions, dependiendo de las características arquitectónicas.
* CYCLIC DEPENDENCIES
    * Patrón dañino que los arquitectos deben evitar
    * Perjudica la modularidad porque un desarrollador no puede reutilizar un solo componente sin traer también los otros
    * La solución a este problema es escribir una fitness function para detectar los ciclos.
    * Colocar las pruebas en el continuous build
* DISTANCE FROM THE MAIN SEQUENCE FITNESS FUNCTION

<div align="right"><small><a href="#tabla-de-contenido">volver al inicio</a></small></div>

### Chapter 7. Scope of Architecture Characteristics





```
¿Qué es un quantum?

El origen del término proviene de los estudios de Max Planck cuando investigaba la forma en que dos sistemas, uno, el “horno que calentaba” y el otro, el “cuerpo calentado”, intercambiaban energía entre sí. Él descubrió que llegado cierto punto de la interacción, el intercambio se producía por unidades indivisibles a las que llamó quantum.

Quantum es la mínima cantidad de energía que un sistema puede intercambiar con otro. Por ejemplo, en el sistema monetario, el quantum del Euro sería 1 céntimo de Euro, que es la mínima cantidad indivisible que se puede intercambiar.
```



<div align="right"><small><a href="#tabla-de-contenido">volver al inicio</a></small></div>

### Chapter 8. Component-Based Thinking

Los arquitectos suelen pensar en términos de componentes, la manifestación física de un módulo.

#### Component Scope

Algunas formas de los componentes:
* Library: Envoltorio de código relacionado (clases o funciones)
* Layer or subsystem
* Event processor
* Distributed service: Se comunican a través de protocolos de red: TCPI/IP, REST

![](img/variedades-componentes.png)

Nada requiere que un arquitecto utilice componentes; sólo sucede que a menudo es útil tener un nivel más alto de modularidad que el nivel más bajo que ofrece el lenguaje

Los componentes forman el bloque de construcción modular fundamental en la arquitectura, lo que los convierte en una consideración crítica para los arquitectos. De hecho, una de las principales decisiones que un arquitecto debe tomar se refiere a la división de alto nivel de los componentes en la arquitectura.

#### Architect Role

Los arquitectos crean el diseño inicial del software, incorporando las características arquitectónicas.

Por lo general, el componente es el nivel más bajo del sistema de software con el que un arquitecto interactúa directamente.

Los componentes consisten en clases o funciones (dependiendo de la plataforma de implementación), cuyo diseño es responsabilidad de los líderes técnicos o los desarrolladores

```
Un arquitecto debe identificar los componentes como una de las primeras tareas de un nuevo proyecto. Pero antes de que un arquitecto pueda identificar los componentes, debe saber cómo dividir la arquitectura.
```

#### Particionar la arquitectura (partición de nivel superior)

La Primera Ley de Arquitectura de Software establece que todo en el software es un trade-off, incluyendo la forma en que los arquitectos crean componentes en una arquitectura. Debido a que los componentes representan un mecanismo de contención general, un arquitecto puede construir cualquier tipo de partición que desee. Existen varios estilos comunes, con diferentes conjuntos de trade-offs. Discutimos los estilos de arquitectura en profundidad en la Parte II. Aquí discutimos un aspecto importante de los estilos, la partición de nivel superior en una arquitectura.

![Two types of top-level architecture partitioning: layered and modular](img/layered-modular.png)

Particionamientos de alto nivel en arquitectura:
* Layered monolith
    * división técnica de alto nivel
    * MVC coincide con esta forma de particionamiento
* Modular monolith 
    * división en torno a los dominios o flujos de trabajo
    * Inspirado en el libro de Eric Evans (técnica de modelado para descomponer sistemas complejos). 
    * La arquitectura de microservicios se basa en esto

![Two types of top-level partitioning in architecture](img/technical-donmain-partitioning.png)

Una de las distinciones fundamentales entre los diferentes patrones de arquitectura es **qué tipo de partición de nivel superior** soporta cada uno. También tiene un gran impacto en la forma en que un arquitecto decide cómo identificar inicialmente los componentes: ¿el arquitecto quiere hacer una partición técnica o por dominio?


### Developer Role

Los desarrolladores suelen tomar componentes, diseñados conjuntamente con el arquitecto, y los subdividen en clases, funciones o subcomponentes. En general, el diseño de clases y funciones es responsabilidad compartida de los arquitectos, los líderes técnicos y los desarrolladores, y la mayor parte de las funciones de los desarrolladores. 

Los desarrolladores nunca deben tomar los componentes diseñados por los arquitectos como la última palabra; todo el diseño de software se beneficia de la iteración. Más bien, ese diseño inicial debe considerarse como un primer borrador, en el que la implementación revelará más detalles y refinamientos.

#### Component Identification Flow

La identificación de los componentes funciona mejor como un proceso iterativo, produciendo candidatos y refinamientos a través de la retroalimentación, ilustrado en la Figura:

![Component identification cycle](img/component-identification-cycle.png)

#### Component Granularity

#### Component Design

#### Case Study: Going, Going, Gone: Discovering Components

#### Architecture Quantum Redux: Choosing Between Monolithic Versus Distributed Architectures

<div align="right"><small><a href="#tabla-de-contenido">volver al inicio</a></small></div>

## MODULE II ARCHITECTURE STYLES

### Chapter 9. Foundations

URL: https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch09.html

Los estilos arquitectónicos (algunas veces llamados patrones de arquitectura) describen una relación nombrada de componentes que cubren una variedad de características de la arquitectura.

Los arquitectos deben estar familiarizados con los nombres básicos de los estilos arquitectónicos genéricos fundamentales.

#### Fundamental Patterns

Big Ball of Mud

Se refiere a la ausencia de cualquier estructura arquitectónica.

![](img/big-ball-mud.png)

Unitary Architecture

La arquitectura unitaria se refiere a un sistema específico que funciona en un hardware específico. 

Investigar: "embedded systems"
https://www.guru99.com/embedded-systems-tutorial.html


Client/Server

Con el tiempo, cuando las redes de computadoras se hicieron común, surgió la necesidad de separar en partes un sistema (sistema distribuido).

La arquitectura Cliente/Servidor consiste en separar la funcionalidad técnica entre el frontend y backend. A este estilo arquitectónico también se lo conocomo como **two-tier**.

Algunos sabores de estilo arquitectónico son:
* DESKTOP + DATABASE SERVER
* BROWSER + WEB SERVER
* THREE-TIER

Monolithic Versus Distributed Architectures

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

Otros problemas que enfrentan las arquitecturas distribuidas son:
* DISTRIBUTED LOGGING: 
* DISTRIBUTED TRANSACTIONS: Este es uno de los trade-offs de la arquitectura distribuida: alta escalabilidad, rendimiento y disponibilidad a costa de la consistencia y la integraidad de datos.
* CONTRACT MAINTENANCE AND VERSIONING: 

<div align="right"><small><a href="#tabla-de-contenido">volver al inicio</a></small></div>

### Chapter 10. Layered Architecture Style

La arquitectura en capas es uno de los estilos arquitectónicos más comunes. Este estilo de arquitectura es el estándar de facto para la mayoría de las aplicaciones, principalmente por su simplicidad, familiaridad y bajo costo.

También es una forma muy natural de desarrollar aplicaciones debido a la ley de Conway, que establece que las organizaciones que diseñan sistemas están obligadas a producir diseños que son copias de las estructuras de comunicación de estas organizaciones. En la mayoría de las organizaciones hay desarrolladores de interfaces de usuario (UI), desarrolladores de backend, desarrolladores de reglas y expertos en bases de datos (DBA). Estas capas organizativas encajan muy bien en los niveles de una arquitectura tradicional de capas, lo que la convierte en una opción natural para muchas aplicaciones comerciales. 

El estilo de la arquitectura en capas también cae en varios anti-patrones arquitectónicos:
* architecture by implication
* accidental architecture

Siendo de naturaleza monolítica, las arquitecturas en capas no tienen las complejidades asociadas con los estilos de arquitectura distribuida, son simples y fáciles de entender, y tienen un costo relativamente bajo de construcción y mantenimiento

#### Topology

Los componentes del estilo de arquitectura en capas se organizan en **capas horizontales lógicas**, y cada capa desempeña una función específica dentro de la aplicación (como la lógica de presentación o la lógica de negocio). 

La mayoría de las arquitecturas en capas consisten en cuatro capas estándar: presentación, negocio, persistencia y base de datos, como se ilustra en la sigiuente figura:

![](img/arquitectura-en-capas.png)

También existen diversas variantes de topología desde la perspectiva de la estratificación física (despliegue). 

![](img/physical-topology-deployment.png)

El concepto de **separación de responsabilidades** dentro del estilo de la arquitectura en capas hace fácil la construcción de roles efectivos y modelos de responsabilidad dentro de la arquitectura. 

Los componentes dentro de una capa específica están limitados en su alcance, tratando sólo con la lógica que pertenece a esa capa. Por ejemplo, los componentes de la capa de presentación sólo se ocupan de la lógica de presentación, mientras que los componentes que residen en la capa de negocio sólo se ocupan de la lógica de negocio. 

Esto permite a los desarrolladores aprovechar sus conocimientos técnicos particulares para centrarse en los aspectos técnicos del dominio (como la lógica de presentación o la lógica de persistencia). Sin embargo, la contrapartida de este beneficio es la falta de agilidad general (la capacidad de responder rápidamente a los cambios).

#### Layers of Isolation

Cada capa en el estilo de arquitectura de capas puede ser cerrada o abierta. Una capa cerrada significa que a medida que una solicitud se mueve de arriba a abajo de una capa a otra, la solicitud no puede saltarse ninguna capa, sino que debe atravesar la capa inmediatamente inferior para llegar a la siguiente. Por ejemplo, en una arquitectura de capas cerradas, una solicitud originada en la capa de presentación debe pasar primero por la capa de negocios y luego por la capa de persistencia antes de llegar finalmente a la capa de la base de datos.

![](img/closed-layers.png)

Sería mucho más rápido y fácil para la capa de presentación acceder directamente a la base de datos para solicitudes de recuperación simples, pasando por alto cualquier capa innecesaria (lo que solía conocerse a principios de la década de 2000 como el patrón de lectura rápida). Para que esto ocurriera, las capas de negocio y de persistencia tendrían que estar abiertas, permitiendo que las solicitudes pasen por alto otras capas. ¿Qué es mejor: capas abiertas o capas cerradas? La respuesta a esta pregunta se encuentra en un concepto clave conocido como **aislamineto de capas**.

El concepto **aislamiento de capas** significa que los cambios realizados en una capa de la arquitectura generalmente no impactan o afectan a los componentes de las otras capas, siempre que los contratos entre esas capas permanezcan inalterados. Cada capa es independiente de las otras capas, por lo que se tiene poco o ningún conocimiento del funcionamiento interno de las otras capas de la arquitectura. Sin embargo, para soportar el aislamiento de capas, las capas involucradas con el flujo principal de la solicitud necesariamente tienen que ser cerradas. Si la capa de presentación puede acceder directamente a la capa de persistencia, entonces los cambios realizados en la capa de persistencia impactarían tanto en la capa de negocio como en la capa de presentación, produciendo una aplicación muy estrechamente acoplada con interdependencias de capas entre componentes. Este tipo de arquitectura se vuelve entonces muy frágil, así como difícil y costoso de cambiar.

El concepto **aislamiento de capas** también permite sustituir cualquier capa de la arquitectura sin afectar a ninguna otra capa (una vez más, suponiendo que los contratos estén bien definidos y que se utilice el business delegate pattern). Por ejemplo, puede aprovechar el concepto de aislamiento de capas dentro del estilo de arquitectura en capas para sustituir su antigua capa de presentación de JavaServer Faces (JSF) por React.js sin afectar a ninguna otra capa de la aplicación.

#### Adding Layers

Mientras que las capas cerradas facilitan el aislamiento de capas y por lo tanto ayudan a aislar el cambio dentro de la arquitectura, hay momentos en los que tiene sentido que ciertas capas estén abiertas. 

Aprovechar el concepto de capas abiertas y cerradas ayuda a definir la relación entre las capas de la arquitectura y los flujos de solicitud. También proporciona a los desarrolladores la información y la orientación necesarias para comprender las diversas restricciones de acceso a las capas dentro de la arquitectura. 

El fracaso en documentar o comunicar adecuadamente qué capas de la arquitectura están abiertas y cerradas (y por qué) suele dar lugar a arquitecturas estrechamente acopladas y quebradizas que son muy difíciles de probar, mantener y desplegar.

#### Other Considerations

La arquitectura en capas es un buen punto de partida para la mayoría de las aplicaciones cuando no se sabe aún exactamente qué estilo de arquitectura se utilizará finalmente. 

Una cosa a tener en cuenta con la arquitectura de capas es el anti-patrón **architecture sinkhole**. Este anti-patrón se produce cuando las solicitudes se mueven de una capa a otra como un simple pasamano sin que se realice una lógica de negocio dentro de cada capa. Esto da como resultado una instanciación y procesamiento innecesarios de los objetos, lo que afecta tanto al consumo de memoria como al rendimiento. Analizar el porcentaje de solicitudes que caen en esta categoría. Es aceptable que sólo el 20% de las solicitudes que estén dentro de este anti-patrón.

#### Why Use This Architecture Style

El estilo de arquitectura en capas es una buena opción para aplicaciones o sitios web pequeños y simples. 

También es una buena elección de arquitectura, particularmente como punto de partida, para situaciones con un presupuesto muy ajustado y limitaciones de tiempo. 

Debido a la simplicidad y familiaridad entre los desarrolladores y arquitectos, la arquitectura en capas es quizás uno de los estilos de arquitectura de más bajo costo, promoviendo la facilidad de desarrollo para aplicaciones más pequeñas. 

El estilo de arquitectura en capas también es una buena opción cuando un arquitecto todavía está analizando las necesidades y requerimientos del negocio y no está seguro de qué estilo de arquitectura sería el mejor.


A medida que crecen las aplicaciones que utilizan el estilo de arquitectura en capas, características como la mantenibilidad, la agilidad, la comprobabilidad y la capacidad de despliegue se ven afectadas negativamente. Por esta razón, las grandes aplicaciones y sistemas que utilizan la arquitectura en capas podrían ser más adecuadas para otros estilos de arquitectura más modulares.

#### Architecture Characteristics Ratings

![](img/layered-architecture-characteristics-ratings.png)
