
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
Como ya se menciono en la practica la implementación de los mapas con una lista hash tiene un buen rendimiento, sin embargo ninguna de las implementaciones previamente mencionadas puede mantener el orden si el tipo de dato de la llave tiene alguna forma de ordenarse.

