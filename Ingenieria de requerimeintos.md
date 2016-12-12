

**Ingeniería de los requerimientos**
=======

## Viavilidad ##
Determina si el sistema se puede implementar según la tecnología, costo y tiempo; o si soluciona el problema del cliente.
## Obtención y análisis (Elicitación) ##
Para poder extraer los requerimientos hay que interactuar con los stakeholders. Esto se conoce como **elicitación**.
#### Dificultades

- **Por parte del cliente**
    - No sabes expersar sus necesidades
    - No está al tanto del alcance de la tecnología y lo que esta puede hacer por él
    - Puede dar por sentado ciertos requisitos
    - No sabe lo que necesita para resolver su problema
- **Por parte del desarrollador**
    - Dificíl entender o explicar las cuestiones técnicas por la diferencia de tecnicidad en los lenguajes
    - A priori parte con una visión distinta de la del cliente por la que puede malinterpretar un requisito
    - Puede asumir requesitos que el cliente no especifica pensando que quizás este los omitió.

### Determinar los puntos de vista
Los stakeholders se pueden clasificar según punto de vista
- **Directo:** Aquellas personas que interactúan directamente con el sistema (ej: los usuarios)
- **Indirecto:** Aquellas personas que no interactúan directamente con el sistema pero si influyen en él o viceversa (ej: el cliente, quizás).
- **Del dominio:** No hace referencia a un stakeholder. Son las características o restricciones dadas por el contexto del sistema (ej : el acceso web)

### Técnicas de elicitación

- **Muestreo de documentación**
Revisión de documentos que describan el funcionamiento del negocio, o a partir de sistemas anteriores que necesiten ser mejorados o remplazados.

- **Investigación**
Investigar sobre soluciones ya implementadas

- **Observación del ambiente de trabajo**
El analista observa las tareas que realizará el sistema de forma más tangible

- **Cuestionarios**
Útiles para obtener información masivamente (ej: preferencias de los usuarios o de
los empleados, también usuarios)
    - Abiertos: Respuestas desarrolladas
    - Cerrados: SI/NO, Multiple choice

- **Entrevistas**
Es la interacción cara a cara, da una mayor calidad de información respecto a los cuestionarios.
    -   Estructuradas: mantienen un formato en cuanto al tipo de preguntas
        - Pirámide: Cerradas - Abiertas
        - Embudo: Abiertas - Cerradas
        - Diamánte: Abiertas - Cerradas - Abiertas
    - No Estructuradas

- **JRP**
Significa planeación conjunta de requerimientos. Consta de reuniones que involucran a el responsable del proyecto, los usuarios, los desarrolladores, y personal que se encarga de dirigir y registrar la sesión.

### Clasificación de los requerimientos

- #### Funcional/No funcional
    - **Funcional**: describe qué tiene que hacer el sistema (ej: registro de usuarios).
    - **No funcional:** restricciones de cómo lo tiene que hacer el sistema (ej: encriptar la información de los usuarios)
        - Del producto: Como debe comportarse el producto (ej: menu violeta para admin)
        - Organizacionales: Como debe operar el equipo de desarrollo (ej: tiempo de entrega)
        - Externos: Legales, estándares

        **Dentro de estos se encuentran**
        - Rendimiento
        - Fiabilidad
        - Seguridad
        - Disponibilidad
        - Mantenibilidad
        - Portabilidad

- #### Usuario/Sistema
    - **Del usuario:** Se declaran en lenguaje natural, hacen referencia a las exigencias del usuario.
    - **Del sistema:** Hacen referencia a las restricciones del sistema.

## Especifiación

Una especifiación de requerimientos debe detallar
- **Funcionalidad:** Qué debe hacer el software (ej: registrar usuarios)
- **Interfaces Externas:** Cómo va a interactuar el usuario (ej: web)
- **Rendimiento:** Velocidad, disponibilidad (ej: los workers de heroku)
- **Atributos:** Seguridad, mantenibilidad, portabilidad (ej: info encriptada)
- **Restricciones de diseño:** Estándares, recursos, lenguajes (ej: usar rails)

### Técnicas de especificación de requerimientos
-   #### Estáticas: A través de entidades y relaciones

    ### 1. Referencia indirecta
    Se define **qué** se hace y no **cómo**.

    EJ: resolver ecuación de *k* incognitas y *n* ecuaciones

    ### 2. Relaciones de recurrencia

    ### 3. Definición axiomática
    Se define a través de axiomas (observaciones evidentes)

    ### 4. Expresiones regulares

    ### 5. Abstracciones de datos

-   #### Dinámicas: A través de estados y estímulos

    ### 1. Tablas de decisión
      Condiciones --> Reglas (2 x condición) --> Acciones

    ### 2. Diagramas de estados finitos

    ### 3. Redes de petri
    Utilizadas para especificar sistemas de tiempo real en los que son necesarios representar aspectos de concurrencia.

    ### 4. Casos de uso
    - Diagramas
      - Actores --> Persona
      - Casos --> Circulo
      - Relaciones --> Extensión, uso, dependencia
    - Escensarios

    ### 5. Historias de usuario
    Utilizadas en las metodologías de desarrollo ágil
    Son independientes, pequeñas, estimables y rapidas de implementar pero es dificil usarlas como base de un contrato.

    Como (rol) quiero (algo) para poder (beneficio)

    ### 6. Diagrama de Flujo de Datos (DFD)

    - Procesos  --> Circulo
    - Flujos    --> Flechas
    - Almacenamientos --> Rectangulo sin costados
    - Entidades --> Rectangulo
## Validación
Antes de empezar a desarrollar hay que estar seguro de que se va a satisfacer lo pedido. Deben ser **correctos, consistentes, completos y realizables**.

## Gestión de los requerimientos
Se identifican los requerimientos para poder generar las políticas de rastreo que definen las relaciones entre estos.
Se pueden detectar dos tipos de requerimientos
- **Duraderos**
- **Volatiles**

### Gestión del cambio
- ##### Análisis del cambio
    Se analiza cuáles son los requerimientos en conflicto ante el cambio solicitado.
- ##### Cálculo de costo
    Se calcula el costo de efectuar el cambio y se informa al cliente
- ##### Implementación
    Si el cliente a prueba el presupuesto se lleva a cabo la implementación
