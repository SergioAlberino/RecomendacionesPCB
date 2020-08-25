********
S�mbolos
********


Simbolos
---------


-	Cada componente debe tener su s�mbolo y �ste debe ser lo m�s descriptivo posible.
-	Los s�mbolos deben estar incluidos en una librer�a propia del proyecto y cada proyecto debe tener su propia librer�a. Esto mejora la portabilidad, es decir si el proyecto es controlado por varias personas todas poseen la misma librer�a dado que est� incluida en el proyecto.


.. image:: ../media/img/simbolo1.png
   :align: left
   :scale: 100 %






-   Agregar al componente toda la informaci�n adicional que sea posible y que
    sea de utilidad a la hora de fabricar la placa (Valor, footprint,
    fabricante, n�mero de parte, distribuidor, etc).
	
	
	

	
	
	



.. image:: ../media/img/simbolo2.png
   :align: left
   :scale: 100 %







-   Crear un s�mbolo por cada tipo de componente, valor y encapsulado , es decir
    crear un s�mbolo para un resistor de 1k 1/8W, otro para un resistor de 1k
    1/4W, etc. Esto si bien genera una librer�a m�s grande dado que se tiene un
    s�mbolo por cada componente, cada valor y cada footprint, ahorra tiempo a la
    hora de generar la BOM (Bill Of Materials - Lista de materiales). Generar
    una BOM clara y ajustada a los est�ndares de los fabricantes puede llegar a
    ser un proceso engorroso y demandante en caso de tener un �nico s�mbolo para
    todas las resistencias y todos los valores por ejemplo.







.. image:: ../media/img/simbolo3.png
   :align: left
   :scale: 150 %







-   Para los Circuitos integrados no hace falta respetar la disposici�n de pines
    de la hoja de datos, si no que es m�s eficiente ubicar los pines de manera
    que genere un esquem�tico m�s organizado y sencillo a la vista. En lo
    posible tratar de mantener las entradas del lado izquierdo y las salidas del
    lado derecho.






.. image:: ../media/img/simbolo4.png
   :align: center
   :scale: 100 %
   
  
   
.. image:: ../media/img/simbolo5.png
   :align: left
   :scale: 100 %





*Disposici�n de pines de la hoja de datos                  Disposici�n de Pines
Ordenado*


FootPrints
-----------

-   Generar un footprint por cada tipo de encapsulado y repetirlo en los
    distintos s�mbolos esquem�ticos. Es decir crear un footprint TO-92 y
    utilizarlo para el BC548, BC337, etc.

-   Cada footprint debe contener idealmente como m�nimo las siguientes capas:

    1.  Top y Bottom layer: Capas para la ubicaci�n de Pads y ruteado de pistas.

    2.  Top y Bottom Overlay: Capas para serigraf�a. Cada footprint debe tener
        una serigraf�a clara y representativa del componente y su forma,
        tratando de respetar las dimensiones f�sicas.

    3.  Top y Bottom Drawing: Estas capas se utilizan para delimitar el tama�o
        total ocupado por el componente. Se utilizan para visualizar una posible
        colisi�n de componentes.

        ![](media/65ab89d77758b5f97698abd3a92574fa.png)

    4.  Capa 3d: Asignar alguna capa mec�nica al modelo 3d del Componente y
        respetarla para todos.

        ![](media/191dc6e9802b8b414b1e77b109e6d126.png)

        ![](media/cff1dfef8f7af40b65a3e20ffb4c7e15.png)
