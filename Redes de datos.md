# Modelo OSI

##### Capa Física
- Topologías
- Medio físico
- Señalización

###### Capa de enlace de datos
- Direccionamiento físico
- Control de acceso al medio
- Detección de errores

###### Capa de red
- Direccionamiento lógico
- Selección de ruta para la comunicación
###### Capa de transporte
- Elige protocolo de transporte TCP / UDP
- Crea los paquetes de datos a mandar

###### Capa de sesión
- Mantiene la conexión activa entre dos dispositivos
###### Capa de presentación
- Traduce información
- Encripta / Desencripta
###### Capa de aplicación
- Define el protocolo de transmisión que se va a usar

----
# Capa Física
## Medio de transmisión
  - #### Guiados
    - **Cable coaxil**
    - **Cable UTP**
    - **Fibra óptica:** envía pulsos de luz.
      - Múltimodo: barato, distancias cortas. La luz viaja por más de un camino.

      - Mónomodo: caro, distancias largas. La luz viaja por un único camino.

  - #### No Guiados
    - Ondas de radio
    - Microondas
    - Luz

## Codificación
  - #### Lazo 20mA
   - 0 => no hay corriente
   - 1 => hay
  - #### Lazo 4-20mA
    - 0% => 4mA
    - 100% => 20mA
    - error => <4mA
  - #### RS-232
    Único cable, V= V+ - tierra, distancias cortas, barato. Ej: mouse
  - #### RS-485
    Dos cables, V = V+ - V-, distancias largas, costoso.
----
# Acceso al Medio (MAC)

## Determinísticos

- #### Pasaje de token
  Los nodos se van pasando un token, el que tiene el token puede transmitir por un tiempo determinado
- #### Maestro-Esclavo
  El maestro es el que controla el medio, decide con cuál esclavo se va a comunicar y cuanto tiempo le da.
- #### Token Híbrido
  El token pasa por los maestros que están conectados a sus esclavos a través de un profibus.
- #### Productor-Consumidor
  Los nodos tienen un tiempo para poner su dato en el bus dado por un árbitro, el dato se lee por los demás esclavos y se identifica según su contenido.

## No Determinísticos

- #### CSMA
  Escucha el medio y si no hay nadie transimitiendo tranmite (CS), todos los dispositivos tienen la misma posibilidad de transmitir (MA)
  - **CD:** Detecta colisiones, si dos empiezan a hablar en el mismo instante, el que detecta la colisión envía un mensaje de JAM y esperan un tiempo aleatorio para volver a transmitir.
  - **CA:** Evita colisiones,  el nodo que quiere transmitir envía RTS, el receptor responde con CTS a todos los nodos para evitar que el resto mande, una vez terminada el receptor responde con ACK a todos los nodos para informar que terminó la transmisión.
----
# Buses
- #### Sensor
  BIT
- #### Device
  BYTE
- #### Field
  PAQUETE


## Profibus
Bus de campo estándar para tecnologías de automatización.
Usan las capas 1, 2 y 7 del modelo OSI.

- #### Profibus-DP
  Alta velocidad y bajo costo
- #### Profibus-PA
  Unica linea de datos y alimentación, baja velocidad
- #### Profibus-FMS
  Se está reemplzando por Ethernet por ser de uso p2p.

## ProfiNET
Adatpa el protocolo de Ethernet a las neceisdades de la industria de la automatización.

#Ethernet

## Trama
  - Preambulo
  - Destino
  - Origen
  - Tipo
  - Datos
  - CRC
  - Espacio

## MAC
  - CSMA/CD con binary backoff

# 802.11

- BSS = grupo de nodos
- ESS = grupo de BSS

## Movilidad
 - #### Sin transición
 Un nodo no cambia de BSS
 - #### Trans BSS
 Un nodo cambia de BSS pero no de ESS
 - #### Trans ESS
 No posible


## MAC
  - CSMA/CA


# Bluetooth
- Alta seguridad
- Corto alcance
- Bajo consumo
- Bajo costo
- Full duplex

##### AFH
Permite detectar transimisiones en la banda y utilizar otras frecuencias no usadas

##### Piconet
Un grupo de 8 dispositivos (1 maestro y 7 eslcavos)

## BT v3 +HS
Alta velocidad, configura por Bluetooth pero transmite por wifi

## BT MAC/PHY
Se utiliza Bluetooth salvo cuando se deben pasar muchos datos, ahi se utiliza wifi

## BT v4
Incluye al Bluetooth clasico, al de alta velocidad y uno nuevo de bajo consumo

# ZigBee
Está pensado para automatización de hogares.

- Bajo costo
- Bajo consumo
- Baja transferencia
- Usa CSMA/CA.
- Conexión en estrella o P2P
