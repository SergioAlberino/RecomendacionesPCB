********
Hardware
********

.. contents:: Contenido
   :depth: 2
   :local:


Características Generales
=========================

El robot cuenta con:

-  1 Micro-controlador `LPC1769 NXP`_  con un core `ARM Cortex-M3`_
-  2 motores de CC controlados por medio de puente H (L298)
-  4 Sensores de ultrasonido HC-SR04
-  4 Sensores de línea Infrarrojos
-  1 Módulo de Comunicación Wireless Xbee
-  4 Leds de propósito general
-  1 Pulsador de propósito general
-  1 Batería de Li-Po 11,1V

.. _LPC1769 NXP: https://www.nxp.com/products/processors-and-microcontrollers/arm-microcontrollers/general-purpose-mcus/lpc1700-cortex-m3/512kb-flash-64kb-sram-ethernet-usb-lqfp100-package:LPC1769FBD100

.. _ARM Cortex-M3: https://developer.arm.com/ip-products/processors/cortex-m/cortex-m3

---------------------------------------------------------------------------------------------------

Sensores
========

El robot cuenta con los siguientes sensores:

-  Sensores de línea.
-  Sensores de ultrasonido
-  Encoder de posición absoluta

Sensores Infrarrojos
--------------------

El sensor IR utilizado es el TCRT5000. Es un sensor óptico reflexivo que consta de un emisor de luz infrarroja y un fototransistor. El fototransistor detecta la luz que es reflejada cuando un objeto pasa enfrente del sensor.

.. image:: ../media/img/sensor_infrarojo.jpeg
   :align: left
   :scale: 50 %
.. image:: ../media/img/diagram_sensor_infrarojo.png
   :scale: 40%
.. image:: ../media/img/schm_sensor_infrarojo.png
   :align: right
   :scale: 70%

Se diseñaron las placas en pares para facilitar el montaje en la base del robot manteniendo la distribución de pines en el conector permitiendo así es uso de un mismo cable.

Mecanizado y vista de componentes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ../media/img/pcb_sensor_infrarojo.png
   :align: center
   :scale: 100%

.. image:: ../media/img/mechanics_sensor_infrarojo.png
   :align: center
   :scale: 100%

.. note:: Medidas en mm

Sensores de Ultrasonido
-----------------------

.. image:: ../media/img/HR-SR04.jpg
   :align: center
   :scale: 50%

El HC-SR04 es un sensor de distancias por ultrasonidos capaz de detectar objetos y calcular la distancia a la que se encuentra en un
rango de 2 a 450 cm. Funciona por ultrasonidos y contiene toda la electrónica encargada de hacer la medición.

Para su utilización es necesario enviar un pulso de arranque y medir la anchura del pulso de retorno.

Características

-  Dimensiones del circuito: 43 x 20 x 17 mm
-  Tensión de alimentación: 5 Vcc
-  Frecuencia de trabajo: 40 KHz
-  Rango máximo: 4.5 m
-  Rango mínimo: 1.7 cm
-  Duración mínima del pulso de disparo (nivel TTL): 10 μS.
-  Duración del pulso eco de salida (nivel TTL): 100-25000 μS.
-  Tiempo mínimo de espera entre una medida y el inicio de otra 20 mS.
-  Pines de conexión:

    -  VCC
    -  Trig (*Disparo del ultrasonido*)
    -  Echo (*Recepción del ultrasonido*)
    -  GND

La equción para calcular la distancia es:

.. math:: d = \frac{t_{echo} \cdot v_{sound}}{2}

donde :math:`t_{echo}` es el tiempo de duración del eco y :math:`v_{sound}` es la velocidad del sonido en :math:`\left[\frac{m}{s}\right]`


Encoder magnético
-----------------

.. image:: ../media/img/AS5045.png
   :align: right
   :scale: 50%

El circuito Integrado AS5045 corresponde a un encoder o codificador magnético sin contacto, para medición de giro angular de 360°.

Permite obtener mediciones absolutas instantáneas de posición magnética angular con una resolución de 0.0879° = 4096 (posiciones por revolución).

La medición se transmite como secuencia serie de datos digitales, modulados a través de una señal PWM.


PCB
^^^

Se desarrolló una placa de pequeñas dimensiones para la conexión e fijación mecánica del AS5045 sobre el eje del motor a utilizar.

.. image:: ../media/img/pcb_as5045.png
   :align: center
   :scale: 50%

Modo de uso
^^^^^^^^^^^

La disposición *Daisy Chain mode* permite conectar varios sensores AS5045 en serie, manteniendo una única línea de comunicación para la comunicación con el microcontrolador.

.. image:: ../media/img/as5045_time_diagram.png
   :align: center
   :scale: 80%


Esquema de Conexión
^^^^^^^^^^^^^^^^^^^

.. image:: ../media/img/schm_sensor_as5045.png
   :align: center
   :scale: 80%


+----------+----------------+----------------------------------+-------------+
| Nombre   | Cable          | Descripción                      | PIN µC      |
+==========+================+==================================+=============+
| CLK      | NARANJA o GRIS | Señal de clock                   | P1.20       |
+----------+----------------+----------------------------------+-------------+
| CSN      | VERDE          | SS/Select                        | P1.21 (SS1) |
+----------+----------------+----------------------------------+-------------+
| VDD      | ROJO           | Alimentación                     | 3.3V        |
+----------+----------------+----------------------------------+-------------+
| PROG\_DI | AMARILLO       | MOSI (Master Output Slave Input) |             |
+----------+----------------+----------------------------------+-------------+
| GND      | NEGRO          | Alimentación                     | GND         |
+----------+----------------+----------------------------------+-------------+
| DO       | AZUL           | MISO (Master Input Slave Output) | P1.23       |
+----------+----------------+----------------------------------+-------------+

.. note:: JP2 permite usar La disposición “Daisy Chain mode” para un solo encoder


Motores
=======

.. image:: ../media/img/image29.png
   :align: center
   :scale: 50%


Se utilizan dos motores de C.C. con reducción mecánica para el posicionamiento diferencial del robot. Los motores seleccionados corresponden al modelo SP4L de la línea de motorreductores de la empresa AP&S.


Características
---------------

.. image:: ../media/img/image30.png
   :align: center
   :scale: 50%


Dimensiones
-----------

.. image:: ../media/img/image31.png
   :align: center
   :scale: 50%



Curvas de funcionamiento
------------------------

.. image:: ../media/img/image32.png
   :align: center
   :scale: 50%



LEDs
====

La placa cuenta con 4 LEDs superficiales, para señalización según programa. Están asociados a los Pines 0, 1, 4 y 8 del puerto 1. Se diferencian por su posición y color.

+------------+-----------+-------------+
|            | **Color** | **Port1.N** |
+============+===========+=============+
| **LED\_1** | Rojo      | 0           |
+------------+-----------+-------------+
| **LED\_2** | Amarillo  | 1           |
+------------+-----------+-------------+
| **LED\_3** | Azul      | 4           |
+------------+-----------+-------------+
| **LED\_4** | Verde     | 8           |
+------------+-----------+-------------+


Pulsador
--------

+------------+--------------+
|            | **Puerto 1** |
+============+==============+
| **SWT\_1** |              |
+------------+--------------+




Batería
=======

Se utiliza una Batería de Polímero de Litio (LiPo) marca DUALSKY XPOWER
LIPO BATTERY PACK ECO-S 1300 MAH / 11,1 VOLT 3S

|DUALSKY XPOWER LIPO BATTERY PACK ECO-S 1300 MAH / 11,1 VOLT 3S|

Características

- Capacidad 1300 mAh
- Tensión 11,1 V
- Peso 109 g
- Constante de descarga 25C
- Domensiones [en mm] 66/34/23
- Conector tipo EC-3
- Form 3S


Distribución de pines del microcontrolador
==========================================

+--------+---------------------------+---------------------+-------------------+
|        | **P0**                    | **P1**              | **P2**            |
+========+===========================+=====================+===================+
| **0**  | Propósito General         | **LED\_1**          | **PWM\_M1**       |
+--------+---------------------------+---------------------+-------------------+
| **1**  | Propósito General         | **LED\_2**          | **PWM\_M2**       |
+--------+---------------------------+---------------------+-------------------+
| **2**  | **UART: TXD0**            |                     | Propósito General |
+--------+---------------------------+---------------------+-------------------+
| **3**  | **UART: RXD0**            |                     | Propósito General |
+--------+---------------------------+---------------------+-------------------+
| **4**  | Propósito General         | **LED\_3**          | Propósito General |
+--------+---------------------------+---------------------+-------------------+
| **5**  | Propósito General         |                     | Propósito General |
+--------+---------------------------+---------------------+-------------------+
| **6**  | Propósito General         |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **7**  | Propósito General         |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **8**  | Propósito General         | **LED\_4**          |                   |
+--------+---------------------------+---------------------+-------------------+
| **9**  | Propósito General         | **Pulsador\_1**     |                   |
+--------+---------------------------+---------------------+-------------------+
| **10** | Propósito General         |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **11** | Propósito General         |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **12** |                           |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **13** |                           |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **14** |                           | **TRIGGER US\_1**   |                   |
+--------+---------------------------+---------------------+-------------------+
| **15** | **TXD1**                  | **TRIGGER US\_2**   |                   |
|        | va directo al RX del Xbee |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **16** | **RXD1**                  | **TRIGGER US\_3**   |                   |
|        | va directo al TX del Xbee |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **17** | **CTS**                   | **TRIGGER US\_4**   |                   |
|        | va directo a CTS del Xbee |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **18** |                           | **ECHO US\_1**      |                   |
+--------+---------------------------+---------------------+-------------------+
| **19** |                           | **ECHO US\_2**      |                   |
+--------+---------------------------+---------------------+-------------------+
| **20** |                           | **Encoders: SCK0**  |                   |
+--------+---------------------------+---------------------+-------------------+
| **21** |                           | **Encoders: SSEL0** |                   |
+--------+---------------------------+---------------------+-------------------+
| **22** | **RTS1**                  | **ENABLE Motor\_1** |                   |
|        | va directo a RTS del Xbee |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **23** | **Sensor de Linea\_1**    | **Encoders: MISO0** |                   |
+--------+---------------------------+---------------------+-------------------+
| **24** | **Sensor de Linea\_2**    | **Encoders: MOSI0** |                   |
+--------+---------------------------+---------------------+-------------------+
| **25** | **Sensor de Linea\_3**    | **ENABLE Motor\_2** |                   |
+--------+---------------------------+---------------------+-------------------+
| **26** | **Sensor de Linea\_4**    | **ECHO US\_3**      |                   |
+--------+---------------------------+---------------------+-------------------+
| **27** |                           | **ECHO US\_4**      |                   |
+--------+---------------------------+---------------------+-------------------+
| **28** |                           |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **29** |                           |                     |                   |
+--------+---------------------------+---------------------+-------------------+
| **30** |                           |                     |                   |
+--------+---------------------------+---------------------+-------------------+


Conectores
==========

Conectores de placa Robot
-------------------------

Sensores IR: Conectores J3, J4, J5 y J6
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

    Conecta con las placas de sensores de línea por medio de cables que

+--------------------+---------------------------+---------------+
| **Sensor Línea 2** |                           |               |
+====================+===========================+===============+
| **J\ :sub:`3`**    | **TCRT5000**              | **Puerto µC** |
+--------------------+---------------------------+---------------+
| **1**              | E\ :sub:`1`               | P0.23         |
+--------------------+---------------------------+---------------+
| **2**              | A\ :sub:`1` y C\ :sub:`1` | Vcc 5V        |
+--------------------+---------------------------+---------------+
| **3**              | K\ :sub:`2`               | GND           |
+--------------------+---------------------------+---------------+

+--------------------+---------------------------+---------------+
| **Sensor Línea 1** |                           |               |
+====================+===========================+===============+
| **J\ :sub:`4`**    | **TCRT5000**              | **Puerto µC** |
+--------------------+---------------------------+---------------+
| **1**              | E\ :sub:`1`               | P0.24         |
+--------------------+---------------------------+---------------+
| **2**              | A\ :sub:`1` y C\ :sub:`1` | Vcc 5V        |
+--------------------+---------------------------+---------------+
| **3**              | K\ :sub:`2`               | GND           |
+--------------------+---------------------------+---------------+

+--------------------+---------------------------+---------------+
| **Sensor Línea 3** |                           |               |
+====================+===========================+===============+
| **J\ :sub:`5`**    | **TCRT5000**              | **Puerto µC** |
+--------------------+---------------------------+---------------+
| **1**              | K\ :sub:`2`               | GND           |
+--------------------+---------------------------+---------------+
| **2**              | A\ :sub:`1` y C\ :sub:`1` | Vcc 5V        |
+--------------------+---------------------------+---------------+
| **3**              | E\ :sub:`1`               | P0.25         |
+--------------------+---------------------------+---------------+

+--------------------+---------------------------+---------------+
| **Sensor Línea 4** |                           |               |
+====================+===========================+===============+
| **J\ :sub:`6`**    | **TCRT5000**              | **Puerto µC** |
+--------------------+---------------------------+---------------+
| **1**              | K\ :sub:`2`               | GND           |
+--------------------+---------------------------+---------------+
| **2**              | A\ :sub:`1` y C\ :sub:`1` | Vcc 5V        |
+--------------------+---------------------------+---------------+
| **3**              | E\ :sub:`1`               | P0.26         |
+--------------------+---------------------------+---------------+

**Ojo: el orden de los pines no es el mismo en todos los conectores.
Deben utilizarse cables específicos para cada conector (error de diseño
que se corregirá a futuro).**

|image33|

Motores / Encoders
^^^^^^^^^^^^^^^^^^

|image34|

+-----------------------+--------------+---------------+
| **Motor / Encoder 2** |              |               |
+=======================+==============+===============+
| **E\ :sub:`1`**       | **Línea**    | **Puerto µC** |
+-----------------------+--------------+---------------+
| **1**                 | Motor -      |               |
+-----------------------+--------------+---------------+
| **2**                 | Motor +      |               |
+-----------------------+--------------+---------------+
| **3**                 | Sin conexión |               |
+-----------------------+--------------+---------------+
| **4**                 | CLK          | P1.20         |
+-----------------------+--------------+---------------+
| **5**                 | CSN          | P1.21         |
+-----------------------+--------------+---------------+
| **6**                 | Vcc 3.3V     |               |
+-----------------------+--------------+---------------+
| **7**                 | Prog\_DI     |               |
+-----------------------+--------------+---------------+
| **8**                 | GND          |               |
+-----------------------+--------------+---------------+
| **9**                 | D0           |               |
+-----------------------+--------------+---------------+

|image35|

+-----------------------+--------------+---------------+
| **Motor / Encoder 1** |              |               |
+=======================+==============+===============+
| **E\ :sub:`2`**       | **Línea**    | **Puerto µC** |
+-----------------------+--------------+---------------+
| **1**                 | Motor -      |               |
+-----------------------+--------------+---------------+
| **2**                 | Motor +      |               |
+-----------------------+--------------+---------------+
| **3**                 | Sin conexión |               |
+-----------------------+--------------+---------------+
| **4**                 | CLK          | P1.20         |
+-----------------------+--------------+---------------+
| **5**                 | CSN          | P1.21         |
+-----------------------+--------------+---------------+
| **6**                 | Vcc 3.3V     |               |
+-----------------------+--------------+---------------+
| **7**                 | Prog\_DI     |               |
+-----------------------+--------------+---------------+
| **8**                 | GND          |               |
+-----------------------+--------------+---------------+
| **9**                 | D0           | P1.23         |
+-----------------------+--------------+---------------+


Sensores de Ultrasonido J7, J8, J9 y J10
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+--------------------------+-------------+---------------+
| **Sensor Ultrasonido 1** |             |               |
+==========================+=============+===============+
| **J\ :sub:`7`**          | **Función** | **Puerto µC** |
+--------------------------+-------------+---------------+
| **1**                    | Vcc 5V      |               |
+--------------------------+-------------+---------------+
| **2**                    | Trigger\_1  | P1.14         |
+--------------------------+-------------+---------------+
| **3**                    | Echo\_1     | P1.18         |
+--------------------------+-------------+---------------+
| **4**                    | GND         |               |
+--------------------------+-------------+---------------+

+--------------------------+-------------+---------------+
| **Sensor Ultrasonido 2** |             |               |
+==========================+=============+===============+
| **J\ :sub:`8`**          | **Función** | **Puerto µC** |
+--------------------------+-------------+---------------+
| **1**                    | Vcc 5V      |               |
+--------------------------+-------------+---------------+
| **2**                    | Trigger\_2  | P1.15         |
+--------------------------+-------------+---------------+
| **3**                    | Echo\_2     | P1.19         |
+--------------------------+-------------+---------------+
| **4**                    | GND         |               |
+--------------------------+-------------+---------------+

+--------------------------+-------------+---------------+
| **Sensor Ultrasonido 3** |             |               |
+==========================+=============+===============+
| **J\ :sub:`9`**          | **Función** | **Puerto µC** |
+--------------------------+-------------+---------------+
| **1**                    | Vcc 5V      |               |
+--------------------------+-------------+---------------+
| **2**                    | Trigger\_3  | P1.16         |
+--------------------------+-------------+---------------+
| **3**                    | Echo\_3     | P1.26         |
+--------------------------+-------------+---------------+
| **4**                    | GND         |               |
+--------------------------+-------------+---------------+

+--------------------------+-------------+---------------+
| **Sensor Ultrasonido 4** |             |               |
+==========================+=============+===============+
| **J\ :sub:`9`**          | **Función** | **Puerto µC** |
+--------------------------+-------------+---------------+
| **1**                    | Vcc 5V      |               |
+--------------------------+-------------+---------------+
| **2**                    | Trigger\_4  | P1.17         |
+--------------------------+-------------+---------------+
| **3**                    | Echo\_4     | P1.27         |
+--------------------------+-------------+---------------+
| **4**                    | GND         |               |
+--------------------------+-------------+---------------+

|image36|

|image38|


Conectores de la Placa microcontrolador
---------------------------------------

Conector CN1: Programación y Debug
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+--------------------------+----------------+------------+------------+
| **Programación y Debug** |                |            |            |
+==========================+================+============+============+
| **CN\ :sub:`1`**         | **Función**    | **PIN µC** | **ULINK2** |
|                          | **JTAG / SWD** |            |            |
+--------------------------+----------------+------------+------------+
| **1**                    | Vcc 3,3V       |            | 1          |
+--------------------------+----------------+------------+------------+
| **2**                    | TMS/SWDIO      | 3          | 7          |
+--------------------------+----------------+------------+------------+
| **3**                    | TCK/SWDCLK     | 5          | 9          |
+--------------------------+----------------+------------+------------+
| **4**                    | TDO/SWO        | 1          | 13         |
+--------------------------+----------------+------------+------------+
| **5**                    | TDI            | 2          | 5          |
+--------------------------+----------------+------------+------------+
| **6**                    | RST            | 17         | 15         |
+--------------------------+----------------+------------+------------+
| **7**                    | NC             |            | NC         |
+--------------------------+----------------+------------+------------+
| **8**                    | GND            |            | 20         |
+--------------------------+----------------+------------+------------+

|image39|

|Imagen relacionada|

**JTAG:** *Joint Test Action Group*

Interfaz utilizada para testear PCBs, según Norma IEEE 1149.1 (*Standard Test Access PortandBoundary-Scan Architecture* para test access ports).

JTAG es una interfaz especial de cuatro o cinco pines agregadas a un chip, diseñada de forma que varios chips en una tarjeta puedan tener sus líneas JTAG conectadas en *daisychain*, de manera tal que una sonda de testeo JTAG necesita conectarse a un solo "puerto JTAG" para acceder a todos los chips en un circuito impreso. Los pines del conector son:

- TDI Entrada de Datos de Testeo
- TDO Salida de Datos de Testeo
- TCK Reloj de Testeo
- TMS Selector de Modo de Testeo
- TRST Reset de Testeo (opcional)

Cuando se utiliza como herramienta de depuración, permite al programador acceder al módulo de depuración que se encuentra integrado en la CPU.

**SWD:** *Serial WireDebugging*

Es una interfaz de dos pines alternativa al tradicional JTAG. Provee la funcionalidad de debug&trace. Desarrollada por ARM para ser utilizada en conjunción con su arquitectura CoreSight, es especialmente adecuada para dispositivos con escaso número de pines

Conector Serie: J3
^^^^^^^^^^^^^^^^^^

|image41|

Conector XBee
^^^^^^^^^^^^^




.. |image0| image:: ../media/img/image1.jpeg
   :width: 2.34028in
   :height: 2.00000in
.. |image1| image:: ../media/img/image2.png
   :width: 3.79583in
   :height: 1.64583in
.. |image2| image:: ../media/img/image3.png
   :width: 3.28740in
   :height: 3.24359in
.. |image3| image:: ../media/img/image4.png
   :width: 4.67756in
   :height: 3.97672in
.. |Explosion miniPI.jpg| image:: ../media/img/image5.jpeg
   :width: 4.83368in
   :height: 6.59851in
.. |image5| image:: ../media/img/image6.png
   :width: 3.07431in
   :height: 2.90417in
.. |image6| image:: ../media/img/image7.png
   :width: 2.92847in
   :height: 2.90486in
.. |image7| image:: ../media/img/image8.png
   :width: 5.99444in
   :height: 2.84306in
.. |placamicro1.PNG| image:: ../media/img/image9.png
   :width: 4.98550in
   :height: 8.55315in
.. |image9| image:: ../media/img/image10.png
   :width: 6.13750in
   :height: 1.79477in
.. |image10| image:: ../media/img/image11.png
   :width: 1.71621in
   :height: 2.09639in
.. |image11| image:: ../media/img/image12.png
   :width: 6.00000in
   :height: 3.90625in
.. |image12| image:: ../media/img/image13.png
   :width: 5.99654in
   :height: 2.18072in
.. |image13| image:: ../media/img/image14.png
   :width: 3.10833in
   :height: 2.75486in
.. |image14| image:: ../media/img/image15.png
   :width: 3.07639in
   :height: 2.75556in
.. |image15| image:: ../media/img/image16.png
   :width: 5.73472in
   :height: 2.65139in
.. |Placadistribuidora.PNG| image:: ../media/img/image17.png
   :width: 4.92169in
   :height: 8.16681in
.. |Placadistribuidora2.PNG| image:: ../media/img/image18.png
   :width: 5.32254in
   :height: 8.35344in
.. |image18| image:: ../media/img/image19.jpeg
   :width: 1.30417in
   :height: 1.18056in
.. |image19| image:: ../media/img/image20.png
   :width: 3.02736in
   :height: 2.16867in
.. |image20| image:: ../media/img/image21.png
   :width: 2.96795in
   :height: 2.19168in
.. |image22| image:: ../media/img/image23.png
   :width: 6.13542in
   :height: 2.15625in
.. |image23| image:: ../media/img/image24.jpeg
   :width: 2.42708in
   :height: 1.51875in
.. |image24| image:: ../media/img/image25.png
   :width: 1.29167in
   :height: 1.24028in
.. |DUALSKY XPOWER LIPO BATTERY PACK ECO-S 1300 MAH / 11,1 VOLT 3S| image:: ../media/img/image33.jpeg
   :width: 2.63462in
   :height: 2.63462in
.. |image33| image:: ../media/img/image35.png
   :width: 2.06944in
   :height: 2.40347in
.. |image34| image:: ../media/img/image36.png
   :width: 2.75417in
   :height: 2.63403in
.. |image35| image:: ../media/img/image37.png
   :width: 2.77361in
   :height: 2.05069in
.. |image36| image:: ../media/img/image38.png
   :width: 1.80278in
   :height: 2.18590in
.. |image38| image:: ../media/img/image39.png
   :width: 4.49726in
   :height: 2.75854in
.. |image39| image:: ../media/img/image40.png
   :width: 3.98056in
   :height: 3.32083in
.. |Imagen relacionada| image:: ../media/img/image41.jpeg
   :width: 4.99324in
   :height: 1.93375in
.. |image41| image:: ../media/img/image42.png
   :width: 3.57326in
   :height: 1.99292in
.. |image42| image:: ../media/img/image43.png
.. |image43| image:: ../media/img/image44.png
   :width: 6.13750in
   :height: 2.17292in