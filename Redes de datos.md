# Modelo OSI

### Capa Física
- Topologías
- Medio físico
- Señalización

### Capa de enlace de datos
- Direccionamiento físico
- Control de acceso al medio
- Detección de errores

### Capa de red
- Direccionamiento lógico
- Selección de ruta para la comunicación

### Capa de transporte
- Elige protocolo de transporte TCP / UDP
- Crea los paquetes de datos a mandar

### Capa de sesión
- Mantiene la conexión activa entre dos dispositivos

### Capa de presentación
- Traduce información
- Encripta / Desencripta

### Capa de aplicación
- Define el protocolo de transmisión que se va a usar

----
# Capa
## Lazo 20mA

Forma de transmisión digital

|Señal|Corriente|
|---|---|
|0|No hay|
|1|Hay|


## Lazo 4-20mA

Forma de transmisión analógica

|Señal|Corriente (mA)|
|---|---|
|0%|4|
|100%|20|
|Error|< 4|

## RS-232
Se utiliza un único cable, y la tensión de salida se mide entre este y tierra. Es barato pero admite distancias muy cortas. Ej: mouse

## RS-485
Se utilizan dos cables, y la tensión de salida se mide entre estos. Es más inmune al ruido por lo que admite distancias largas pero es más costoso.

----
# Acceso al Medio (MAC)

## Determinísticos

### Pasaje de token
  Los nodos se van pasando una trama que contiene un token que indica el nodo destino y los datos. Cuando el token llega al nodo destino, lo copia, lo marca y lo pasa. Cuando vuelve al emisor, este lo retira, dejando el token libre para quien lo necesite.

### Maestro-Esclavo
  El maestro es el que controla el medio, decide con cuál esclavo se va a comunicar y cuanto tiempo le da.

### Token Híbrido
  Utiliza el método de pasaje de token entre maestros para ver quien tiene control del bus.
  La comunicación a sus esclavos se hace mediante el bus, que podría ser un profibus.

### Productor-Consumidor
  Los nodos tienen un tiempo para poner su dato en el bus dado por un árbitro, el dato se lee por los demás esclavos y se identifica según su contenido.

## No Determinísticos

### CSMA
Escucha el medio y si no hay nadie transimitiendo tranmite (CS), todos los dispositivos tienen la misma posibilidad de transmitir (MA)

- **CD:** Detecta colisiones, si dos empiezan a hablar en el mismo instante, el que detecta la colisión envía un mensaje de JAM y esperan un tiempo aleatorio para volver a transmitir. En el caso de ser binary backoff, el tiempo de espera se va duplicando por cada colisión

- **CA:** Evita colisiones,  el nodo que quiere transmitir envía RTS, el receptor responde con CTS a todos los nodos para evitar que el resto mande, una vez terminada el receptor responde con ACK a todos los nodos para informar que terminó la transmisión.

- **BA:** es una especie de CA, si dos nodos quieren transmitir, se frenan y transmite el de mayor prioridad, el otro transite en el próximo ciclo.


---

# HART

High Adressable Remote Trasducer. Se emplea para la configuración remota. No es un bus de campo ya que conecta los instrumentos a un controlador de E/S. Utiliza Lazo 4-20mA.

---
# Buses de campo

Son buses utilizados en la industria para conectar PLCs con sensores y actuadores. Se caracterizan por ser de instalación simple y costos bajos ya que se comparte un bus entre varios dispositivos. Es de comunicación bidireccional.

Antiguamente se conectaban los sensores a un CPU mediante lazo 4-20mA y este procesaba las entradas y envíaba la información a los actuadores.

Se pueden clasificar en 3 grupos:


|Grupo|Inteligencia|Velocidad|Tipo de dato|Función|
|---|---|---|
|De campo|Alta|Baja|Paquete|Conectan PLCs (Programable Logic Controller)|
|De dispositivos|Baja|Baja| Bit/Byte|Conectan dispositivos|
|De sensores|Nula|Alta|Bit|Transforman magnitudes físicas en señales digitales|



### Profinet
Protocolo de estandarización que adapta el hardware de Ethernet a las necesidades de la industria. Implementa las siguientes tácticas:

- **Fast fowarding:** el codigo que identifica al nodo destino se mueve adelante de la trama para que la verificicación se haga lo antes posible

- **Dyanmic Frame Packaging:** el tamaño de los paquetes depende del tamaño del dato, esto evita los bits de relleno

### Profibus
La familia de profibus es una arquitectura abierta que permite la interconexión de dispositivos de distintos fabricantes.

Existen 3 protocolos:

##### Profibus-DP
Es un bus de dispositivos y el más usado. Implementa las capas 1 y 2 del modelo OSI + una interfaz con el usuario.
En la capa 1 puede usar RS-485 o fibra óptica y en la 2 Maestro-Esclavo o pasaje de Token.

##### Profibus-PA
Es parecido al DP pero está pensado para trabajar en zonas no seguras, como por ejemplo con riesgo de explosión. Permite que la alimentación de los dispositivos sea a través del bus.

##### Profibus-FMS
Pertenece a los buses de campo, tiene mayor funcionalidad respecto a DP y AP. Se utiliza para conectar PLCs y tiene lógica a nivel de control. Implementa además la capa 7 del modelo OSI.

### LonWorks
Usado para la automatización de hogares, transporte, electricidad o industria. No está sujeto a buses físicos unicamente. Se pueden pueden conectar una enorme cantidad de dispositivos. El protocolo se encarga de las comunicaciones entre los dispositivos.

### Foundation Field
Usado en la comunicación entre los dispositivos de campo y los sistemas de supervisación de plata. Entraría en el grupo de los buses de campo. Ofrece control distribuído.

Tiene 2 implementaciones:
- **H1:** De baja velocidad pero provee alimentación por el bus
- **HSE:** High Speed Ethernet. Alta velocidad pero no provee alimentación por cable.


### CANbus
Usado en la industria automotriz, utiliza dos buses para un mayor protección contra fallos (la señal se envía por ambos buses). Utiliza Productor-Consumidor. Permite resolver colisiones por prioridad.


### Sensor AS-I
No buscar ser un bus de campo para la automatización unviersal. Se centra en conectar sensores y actuadores con el menor costo y complejidad posible. Es de alta velocidad y utiliza Maestro-Esclavo.


---
# Ethernet
Es el estándar de red más conocido. Trabaja a altas velocidades y bajo costo. Utiliza CSMA/CD con binary backoff como controlo de acceso al medio. La adquisisión del canal se da cuando un nodo logra transmitir 512 bits a partir del preámbulo sin colisiones. Se maneja con el método de mejor esfuerzo, esto significa que manda los datos pero no asegura que sea infalible (por ejemplo si una trama colisiona 16 veces se descartaría). Son los protocolos de alto nivel los que se encargan de enmendar estos errores.


**Round Trip Timing:** Es el tiempo que tarda en volver una señal que fue enviada.

**Frame brusting:** Es un técnica que implementa Gigabit ethernet cuando tiene que mandar datos pequeños. Permite mandar mas de un dato en un mismo tiempo de transmisión. El primer dato se manda normal en caso de ocurrir una colisión. Una vez que se adquirió el canal más datos pueden mandarse como ráfaga antes dentro del mismo tiempo de transmisión.

## Trama
- Comienzo
  - Preambulo
- Direcciones
  - Destino
  - Origen
- Datos
  - Tipo
  - Dato
- Errores
  - CRC
- Fin
  - Espacio

---

# Redes inalámbricas 802.11
Estas se caracterizan por tener un Bit Error Rate alto, bajos niveles de señal, baja posibilidad de detección de errores y no son seguras. Utiliza CSMA/CA como método de acceso al medio y reconocimiento positivo en el envío de tramas, que consiste en responder con ACK por cada trama recibida.

El censado del medio puede ser **Físico** (como en Ethernet) o **Virtual** (las tramas contienen un campo que determina el tiempo que va a estar ocupado el medio)

Diferentes implementaciones pueden utilizar **FHSS** o **DSSS**

## Tipos de red

|Tipo|Caracteística|
|---|---|
|Infrastructure BSS | Nodos conectados por un Acces Point|
|Independent BSS | Nodos conectados entre sí (sin AP)|
| ESS | Grupo de BSSs|



# Bluetooth
Es una tecnología inalámbrica de corto alcance. Se caracteriza por ser seguro, de bajo costo y consumo.

Se clasifican 3 clases de BT según su distancia en metros:

1. **100m**
2. **10m**
3. **1m**


Utiliza **AFH** (Adaptive Frecuency Hopping) que permite detectar transimisiones en la banda y utilizar otras frecuencias no usadas.

Un grupo de 8 (máx) dispositivos (1 maestro y 7 eslcavos) se denomina **Piconet**. El maestro transmite en los invervalos pares de tiempo y los esclavos en los intervalos impares, esto hace que la comunicación sea **full-duplex**.

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
