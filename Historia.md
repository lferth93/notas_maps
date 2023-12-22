
# Mapas
Los mapas también conocidos como diccionarios, arreglo asociativo o tabla de símbolos son una estructura de datos abstracta que nos permite almacenar pares ordenados (llave, valor), de tal manera que solo se permite a lo mas una aparición para cada llave posible.

Esta estructura permite las tres operaciones siguientes:
- Insertar o Agregar: Inserta una pareja (llave, valor) dada en el mapa.
- Eliminar o Borrar: Elimina una pareja (llave, valor) del mapa dada la llave que la identifica.
- Buscar o Consultar : Busca una pareja (llave, valor) dada una llave, y en caso de que se encuentre en el mapa se devuelve el valor asociado a la llave.

Los mapas son útiles ya que nos permiten tener mas flexibilidad que los arreglos ya que estos solo permiten un valor numérico entero para las llaves, mientras los mapas permiten un tipo de dato arbitrario para las llaves.

## Implementaciones
### Lista ligada
Una implementación muy simple para esta estructura es mediante una lista ligada simple donde cada nodo de la lista almacena una pareja (llave, valor), es fácil notar que las complejidades tanto espacial como temporal de esta implementación son las mismas que las de la lista ligada simple. Las complejidad temporal de la inserción es O(1) lo cual es muy bueno ya que nos permite insertar muchas parejas de una forma muy eficiente, el problema es cuando realizamos búsquedas o eliminaciones, ya que la complejidad temporal es O(n), esto significa que realizar una sola consulta puede llegar a ser muy costosa si la lista es muy grande.

## Tabla hash
Una tabla hash consiste en un arreglo de tamaño fijo donde cada elemento es una lista ligada. Para poder realizar cualquier operación es esta implementación es necesario que tener una función "hash" h que dada una llave devuelva un numero natural, después es necesaria una función que tome el resultado de h y lo lleve a un valor entre 0 y el tamaño de nuestro arreglo, esto determinara en que posición del  arreglo se almacenara nuestra pareja.

Dado que el tamaño de nuestro arreglo puede ser menor que la cantidad de llaves diferentes que se pueden almacenar es posible que existan colisiones, con esto nos referimos a que dos llaves diferentes se almacenen en la misma posición del arreglo, por esta razón tenemos listas ligadas en cada posición. Si sucede una colisión la pareja que se inserto después se inserta al final de la lista ligada correspondiente.

La complejidad temporal se ve afectada por la capacidad de nuestra función hash de producir valores diferentes para las llaves y del tamaño de nuestro arreglo, el caso ideal es que todas las parejas se almacenen en posiciones diferentes, en este caso las 3 operaciones tienen una complejidad temporal O(1). Por el contrario el peor de los casos es que todas las parejas estén almacenadas en la misma posición, en este caso las complejidades de la búsqueda y eliminación se ven afectadas y quedarían como O(n).

En la practica la complejidad promedio de la búsqueda y eliminación es theta(1) lo cual es muy bueno, también se pueden aplicar estrategias en las que se re dimensiona nuestro arreglo para evitar las colisiones, pero esto tiene el costo de que la complejidad de la inserción en el peor de los casos de vuelve O(n).

## Árbol de búsqueda balanceado
Como ya se menciono, en la practica la implementación de los mapas con una tabla hash tiene un buen rendimiento, sin embargo ninguna de las implementaciones previamente mencionadas puede mantener el orden si el tipo de dato de la llave tiene alguna forma de ordenarse.

Una solución al problema de ordenamiento en los mapas es hacer una implementación usando arboles de búsqueda balanceados, dentro de estos arboles de usa la llave como criterio de búsqueda. Los arboles mas usados para este propósito son los arboles AVL y los arboles rojo-negro.

### Arboles AVL
Los arboles AVL son un tipo de árbol binario de búsqueda, la particularidad de estos es su capacidad de auto balancearse cada vez que se inserta un nuevo elemento.

Dado que después de cada operación de inserción el árbol esta balanceado, esto significa que si el árbol tiene n elementos la altura del árbol sera log(n)+1, esto nos garantiza que las operaciones de consulta tienen una complejidad temporal O(log n). Para mantener el orden la complejidad temporal de la inserción y eliminación es O(log n).

Debido al balance estricto que tienen los arboles AVL en la práctica el desempeño no es muy bueno cuando se requieren hacer muchas operaciones de inserción.

### Arboles rojo-negro
Un árbol rojo-negro es un árbol binario de búsqueda, al igual que los arboles AVL los arboles rojo-negro pueden auto balancearse, solo que el balance de estos es menos estricto. Esto causa que en la mayoría de las inserciones no se requiere hacer ajustes de balanceo.

Una de las principales características de estos arboles es que para todos los nodos del árbol no se permite que la altura de uno de sus subarboles supere el doble de la altura del otro subarbol.

En la practica las operaciones de inserción y eliminación son mas eficientes que en un árbol AVL, sin embargo las operaciones de consulta serán mas eficientes en un árbol AVL.

La preferencia de un tipo de árbol sobre el otro se vera afectada por el tipo de operaciones que mas se efectúen para cada caso en particular.

Si la operación predominante es consulta entonces es mas conveniente usar arboles AVL, si por el contrario la operación predominante es inserción y eliminación es preferible usar arboles rojo-negro.

## Mapas en Java
En Java la librería estándar del lenguaje cuenta con las clases HashMap y TreeMap del paquete java.util, estas son las respectivas implementaciones usando tablas hash y arboles binarios de búsqueda respectivamente.

En particular la clase TreeMap esta implementada usando un árbol rojo-negro.

### Complejidad
La complejidad espacial tanto para la clase HashMap como para TreeMap es O(n), solo hay que tener en cuenta que se debe de reservar un nuevo arreglo para la tabla hash de HashMap cuando ocurre un re dimensionamiento.

En cuanto a la complejidad temporal para la clase HashMap se tiene:
- Insertar: O(n) theta(1)
- Eliminar: O(n) theta(1)
- Buscar: O(n) theta(1)

Para TreeMap:
- Insertar: O(log n) theta(log n)
- Eliminar: O(log n) theta(log n)
- Buscar: O(log n) theta(log n)

## Ejemplos de uso de mapas

# Conjuntos
En ciencias de la computación un conjunto (Set) es una estructura de datos que no permite almacenar valores duplicados.

Las operaciones permitidas por esta estructura de datos son:
- Insertar o agregar: Inserta un valor al conjunto en caso de que este valor no se encuentre previamente.
- Eliminar o borrar: Elimina un valor del conjunto.
- Buscar o consultar: Busca si un valor determinado se encuentra dentro del conjunto.

## Implementaciones
Esta estructura de datos puede ser vista como un caso particular de los mapas donde solo nos importa la llave, por esta razón toda la teoría previamente mencionada es aplicable a los conjuntos.

## Conjuntos en Java
En Java se cuenta con las clases HashSet y TreeSet del paquete util.

Debido a que estas estructuras son casos particulares de sus mapas correspondientes, en Java las implementaciones esta codificadas haciendo uso de mapas estableciendo el tipo para los valores como nulo.

La clase HashSet es implementada haciendo uso de la clase HashMap, de forma similar la clase TreeSet es implementada usando la clase TreeMap.


