# Conceptos de diseños

## Abstracción
 Permite tener una visión general del sistema sin tener que preocuparse por detalles

## Refinamiento
 Se va iterando sobre las funcionalidades obteniendo mayor nivel de detalle

## Modularidad
  Se divide el diseño en módulos con propósitos bien definidos

## Ocultamiento de información
  Solo se intercambia la información necesaria entre módulos


# Diseño arquitectónico
Propósito de identificar a los subsistemas y establecer el marco de control

Afecta directamente a los requisitos **no funcionales**

## Organización del sistema

Puede ser
- ### Modelo de repositorio
  Los datos se almacenan en un subsistema y están presentes al resto.
  - ++ Facil comunicación entre subsistemas
  - ++ La protección de los datos está centralizada
  - ++ Separa la lógica de los datos
  - --- Dificil de agregar funcionalidades
  - --- El modelo de datos lleva a los subsistemas a implementarse de cierta manera

- ### Modelo cliente-servidor
  Se basa en un subsistema que sirve y otro que utiliza
  - +++ Permite concurrencia
  - +++ El servidor no conoce al cliente

- #### Modelo de capas
  El sistema se organiza en capas (ej: Modelo OSI, DBP)
  - +++ Las capas pueden cambiar su implementación
  - +++ Fácil implementación de la seguridad
  - --- Puede que ser repitan los servicios

## Descomposición modular

  - ### Orientada a objetos
    - +++ Ocultamiento de información e implementación
    - +++ Débil acoplamiento

  - ### Orientada a funciones
    - +++ Mayor reusabilidad de código
    - --- Menor ocultamiento de información


## Modelos de control

  - ### Centralizado
    El programa principal se encarga de utilizar a los subsitemas

    - LLamada retorno
    - Gestor

  - ### Basado en eventos
  Los subsitemas se utilizan a medida que surgen los eventos
    - Broadcasts
    - Interrupciones

# Arquitectura de los diseños distribuidos
