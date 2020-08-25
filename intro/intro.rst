Grupo de Inteligencia Artificial y Robótica

**Robot miniPi**

Manual de Usuario

**Integrantes**

    Alejandro Gastón Alvarez

    `*alegasalv@gmail.com* <mailto:alegasalv@gmail.com>`__

    Juan Manuel Gabis Gomez

    `*jgabis14@gmail.com* <mailto:jgabis14@gmail.com>`__

    JoaquinToranzo Calderón

    `*toranzocalderonjs@gmail.com* <mailto:toranzocalderonjs@gmail.com>`__

    Juan Ignacio Basile

    `*juaanii.b@hotmail.com* <mailto:juaanii.b@hotmail.com>`__

    Nicolás Brunella

    `*nicolasbrunella@gmail.com* <mailto:nicolasbrunella@gmail.com>`__

    Micaela Viegas Domina

    `*micaviegasdomina@hotmail.com* <mailto:micaviegasdomina@hotmail.com>`__

**Directores del Proyecto**

    Sergio Alberino

    `*alberino@gmail.com* <mailto:alberino@gmail.com>`__

    Pablo Folino

    `*pfolino@gmail.com* <mailto:pfolino@gmail.com>`__

**Directores del Grupo**

    Claudio Verrastro

    `*cverra@cae.cnea.gov.ar* <mailto:cverra@cae.cnea.gov.ar>`__

    Juan Carlos Gómez

    `*juanca@inti.gob.ar* <mailto:juanca@inti.gob.ar>`__



Principales características de la plataforma Robot
--------------------------------------------------

+-------------------------------+--------+
| **Características físicas**   |        |
+===============================+========+
| Ancho                         | 9,7 cm |
+-------------------------------+--------+
| Largo                         | 9,7 cm |
+-------------------------------+--------+
| Alto                          | 10 cm  |
+-------------------------------+--------+
| Peso Aproximado (sin batería) | xx g   |
+-------------------------------+--------+
| Peso Aproximado (con batería) | xx g   |
+-------------------------------+--------+

+---------------------+-------------------+
| **Alimentación**    |                   |
+=====================+===================+
| Batería Li-Po       | 11,1V – xx Ah     |
+---------------------+-------------------+
| Tiempo de autonomía | xx horas (Aprox.) |
+---------------------+-------------------+
| Tiempo de recarga   | xx horas (Aprox.) |
+---------------------+-------------------+

+--------------------------------+---------------------------+
| **Desplazamiento**             |                           |
+================================+===========================+
| Motores Con reducción mecánica | AP&S 12V. Reducción xx:xx |
+--------------------------------+---------------------------+
| Ruedas Diámetro                | 6 cm                      |
+--------------------------------+---------------------------+

+----------------------------+--------------------------------------+
| **Procesador**\ LPC1769    |                                      |
+============================+======================================+
| Core                       | ARM Cortex-M3 de NXP                 |
+----------------------------+--------------------------------------+
| Memoria RAM                | 64kB                                 |
+----------------------------+--------------------------------------+
| Memoria Flash ROM          | 512kB (on-chip)                      |
+----------------------------+--------------------------------------+
| Clock                      | 120MHz                               |
+----------------------------+--------------------------------------+
| In-SystemProgramming (ISP) | Si                                   |
+----------------------------+--------------------------------------+
| USB                        | USB 2.0 full-speed Device controller |
+----------------------------+--------------------------------------+
| UARTs                      | 4                                    |
+----------------------------+--------------------------------------+
| I2C serial interfaces      | 3                                    |
+----------------------------+--------------------------------------+
| SPI/SSP serial interfaces  | 3                                    |
+----------------------------+--------------------------------------+
| ADC                        | ADC de 12-bit con 8 canales          |
+----------------------------+--------------------------------------+
| Timer/Counter/PWM          | 4 x 32-bit Timer                     |
+----------------------------+--------------------------------------+
| PWM                        | Standard PWM Timer block             |
+----------------------------+--------------------------------------+
| JTAG and Serial Wire Debug | Si                                   |
+----------------------------+--------------------------------------+

+-----------------------------+------------------------------------+
| **Sensores**                |                                    |
+=============================+====================================+
| Infrarrojos (TCRT5000) x 4. | Rango xx – xx cm                   |
+-----------------------------+------------------------------------+
| Ultrasonido (HCSR04) x 4    | Rango xx – xx cm                   |
+-----------------------------+------------------------------------+
| Encoders (AS5045) x 2       | Medición de 4096 pulsos por vuelta |
+-----------------------------+------------------------------------+

+------------------------------+-------+
| **Comunicación inalámbrica** |       |
+==============================+=======+
| Modulo Xbee                  |       |
+------------------------------+-------+
| Alcance                      | xx m  |
+------------------------------+-------+
| Frecuencia de operación      | xx Hz |
+------------------------------+-------+


Diseño Mecánico
===============

.. |image1| image:: media/image2.png
   :width: 3.79583in
   :height: 1.64583in

Pieza Base – Dimensiones
------------------------

.. |image3| image:: media/image4.png
   :width: 4.67756in
   :height: 3.97672in

Vista explosionada
------------------

|Explosion miniPI.jpg|



ANEXOS
======

**Anexo A: Programación con MdE **

.. |image42| image:: media/image43.png


La primera columna corresponde al ESTADO de la MdE

    Las columnas siguientes corresponden a los valores que pueden tomar
    las distintas entradas.

.. |image43| image:: media/image44.png
   :width: 6.13750in
   :height: 2.17292in


Las Columnas M1 y M2, corresponden a las salidas.

    Columna Estado+1, contiene el valor del Estado al que debe pasar la
    Máquina de Estados.


**Material que puede ser aprovechado**

**CMSIS**

Con este nombre denominamos a un conjunto de archivos que conforman un nivel de abstracción que permite acceder a micros de diferentes fabricantes de una forma común. ARM provee los archivos necesarios para acceder al NVIC y para poder utilizar las características distintivas del micro con diversos compiladores. Así, existen funciones intrínsecas que son mapeadas mediante macros al compilador utilizado, de modo que el usuario pueda también cambiar de compilador cuando lo desee. De momento Keil, IAR y GNU son los entornos soportados.

Además, cada fabricante provee un set de archivos que permite acceder a los periféricos del micro de modo uniforme

Mediante estructuras en C.