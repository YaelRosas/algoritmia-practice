# Estructuras de Datos

Una estructura de datos es una forma especializada de organizar, gestionar y almacenar datos en la memoria de una computadora para que puedan ser utilizados de manera eficiente. Si los algoritmos son las instrucciones, las estructuras de datos son los contenedores; la elección de uno afecta directamente la velocidad y el consumo de recursos de cualquier sistema.

## ¿Por qué importa la estructura?

Porque no existe una solución universal. Cada estructura de datos tiene fortalezas y debilidades dependiendo de la operación que se realice: buscar, insertar, eliminar o acceder a un elemento. Una elección incorrecta puede transformar un proceso instantáneo en uno extremadamente lento a medida que el volumen de información crece.

## La idea central: Organización y Acceso

El diseño de una estructura de datos define cómo se relacionan los elementos entre sí y qué reglas rigen su manipulación. Se dividen principalmente en dos categorías:

- **Lineales**: Los elementos se organizan en una secuencia lógica (uno tras otro).
- **No lineales**: Los elementos se organizan de forma jerárquica o interconectada, como árboles o grafos.

La eficiencia de estas estructuras se mide generalmente bajo el análisis de la notación Big O, evaluando el costo de sus operaciones fundamentales.

## Estructuras de Datos Comunes

A continuación, se presentan las estructuras más habituales y sus características principales:

- **Arreglos (Arrays)** Colecciones de elementos almacenados en posiciones de memoria contiguas. Su gran ventaja es el acceso directo mediante un índice (**O(1)**), pero insertar o eliminar elementos en medio es costoso (**O(n)**).
- **Listas Enlazadas (Linked Lists)** Conjuntos de nodos donde cada uno apunta al siguiente. A diferencia de los arreglos, son dinámicas y eficientes para insertar o eliminar (**O(1)** si se tiene el puntero), pero el acceso a un elemento específico requiere recorrer la lista (**O(n)**).
- **Pilas (Stacks)** Siguen el principio LIFO (_Last In, First Out_). El último elemento en entrar es el primero en salir. Ideales para deshacer acciones o gestionar llamadas a funciones.
- **Colas (Queues)** Siguen el principio FIFO (_First In, First Out_). El primer elemento en entrar es el primero en salir. Se utilizan en sistemas de impresión o procesamiento de tareas por turno.
- **Tablas Hash (Hash Tables)** Almacenan pares clave-valor. Utilizan una función hash para transformar una clave en un índice. Permiten búsquedas, inserciones y eliminaciones extremadamente rápidas, generalmente en tiempo constante promedio (**O(1)**).
- **Árboles Binarios de Búsqueda (BST)** Estructuras jerárquicas donde cada nodo tiene máximo dos hijos. Si están balanceados, permiten buscar, insertar y eliminar en tiempo logarítmico (**O(log n)**).
- **Grafos** Conjuntos de nodos (vértices) conectados por aristas. Son fundamentales para representar redes sociales, rutas de mapas o interconexiones complejas.

## Criterios para elegir una estructura

1. **Tipo de operación frecuente**: Si necesitas acceder por índice frecuentemente, usa un arreglo. Si necesitas insertar y eliminar constantemente en los extremos, usa una lista o una cola.
2. **Gestión de memoria**: Los arreglos tienen un tamaño fijo o requieren redimensionamiento; las listas enlazadas crecen dinámicamente pero usan más memoria por los punteros.
3. **Orden de los datos**: Si el orden de llegada es crítico, usa colas; si la jerarquía es lo importante, usa árboles.

## Ejemplos conceptuales

```python
# Uso de una Pila (Stack) - LIFO
historial = []
historial.append("página_1") # push
historial.append("página_2")
ultimo = historial.pop()      # pop -> devuelve "página_2"

# Uso de un Diccionario (Hash Table) - O(1)
precios = {
    "manzana": 1.5,
    "banana": 0.8
}
precio_manzana = precios["manzana"]

# Uso de una Lista Enlazada (Representación simple de Nodo)
class Nodo:
    def __init__(self, valor):
        self.valor = valor
        self.siguiente = None

```
