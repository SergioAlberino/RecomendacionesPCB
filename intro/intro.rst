

Tips Esquemático
---------

-	Cada componente debe tener su símbolo y éste debe ser lo más descriptivo posible.
-	Los símbolos deben estar incluidos en una librería propia del proyecto y cada proyecto debe tener su propia librería. Esto mejora la portabilidad, es decir si el proyecto es controlado por varias personas todas poseen la misma librería dado que está incluida en el proyecto.


.. image:: ../media/img/simbolo1.png
   :align: left
   :scale: 100 %  
  
  
  




Rlalata
-----------

-   Generar un footprint por cada tipo de encapsulado y repetirlo en los
    distintos símbolos esquemáticos. Es decir crear un footprint TO-92 y
    utilizarlo para el BC548, BC337, etc.

-   Cada footprint debe contener idealmente como mínimo las siguientes capas:

    1.  Top y Bottom layer: Capas para la ubicación de Pads y ruteado de pistas.

    2.  Top y Bottom Overlay: Capas para serigrafía. Cada footprint debe tener
        una serigrafía clara y representativa del componente y su forma,
        tratando de respetar las dimensiones físicas.

    3.  Top y Bottom Drawing: Estas capas se utilizan para delimitar el tamaño
        total ocupado por el componente. Se utilizan para visualizar una posible
        colisión de componentes.

        ![](media/65ab89d77758b5f97698abd3a92574fa.png)

    4.  Capa 3d: Asignar alguna capa mecánica al modelo 3d del Componente y
        respetarla para todos.




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


Con este nombre denominamos a un conjunto de archivos que conforman un nivel de abstracción que permite acceder a micros de diferentes fabricantes de una forma común. ARM provee los archivos necesarios para acceder al NVIC y para poder utilizar las características distintivas del micro con diversos compiladores. Así, existen funciones intrínsecas que son mapeadas mediante macros al compilador utilizado, de modo que el usuario pueda también cambiar de compilador cuando lo desee. De momento Keil, IAR y GNU son los entornos soportados.

Además, cada fabricante provee un set de archivos que permite acceder a los periféricos del micro de modo uniforme

Mediante estructuras en C.