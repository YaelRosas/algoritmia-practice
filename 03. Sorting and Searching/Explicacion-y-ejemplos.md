# Algoritmos de Búsqueda y Ordenamiento: Una explicación narrativa

Los algoritmos de búsqueda y ordenamiento son las operaciones fundamentales que transforman datos brutos en información estructurada y localizable. Mientras que el ordenamiento organiza los elementos bajo un criterio específico (numérico o alfabético), la búsqueda se encarga de encontrar la ubicación de un dato dentro de un conjunto.

## La importancia del orden previo

La eficiencia de una búsqueda depende directamente de si los datos están ordenados o no. Buscar una palabra en un diccionario físico es rápido porque está ordenado; buscar una herramienta en un garaje desordenado requiere revisar cada rincón. En computación, invertimos tiempo en ordenar para ahorrar tiempo en buscar.

## Algoritmos de Búsqueda

Existen dos enfoques principales dependiendo de la estructura de los datos:

* **Búsqueda Lineal (O(n))**: Es el método de fuerza bruta. Revisa cada elemento uno por uno hasta encontrar el objetivo o terminar la lista. Se usa en listas desordenadas.
* **Búsqueda Binaria (O(log n))**: Es extremadamente eficiente pero requiere que la lista esté **ordenada**. Funciona dividiendo el conjunto a la mitad en cada paso, descartando la mitad donde el valor no puede estar.

---

## Algoritmos de Ordenamiento

Se clasifican según su estrategia y su eficiencia computacional.

### Algoritmos Simples (Cuadráticos)

Son fáciles de implementar pero ineficientes para grandes volúmenes de datos (**O(n²)**):

* **Bubble Sort (Burbuja)**: Compara elementos adyacentes y los intercambia si están en el orden incorrecto. Los valores más grandes "flotan" hacia el final.
* **Insertion Sort (Inserción)**: Similar a cómo ordenamos cartas en la mano; toma un elemento y lo inserta en su posición correcta respecto a los anteriores.
* **Selection Sort (Selección)**: Busca el elemento más pequeño y lo coloca al principio, repitiendo el proceso para el resto.

### Algoritmos Eficientes (Linealítmicos)

Utilizan la estrategia de "Divide y Vencerás" para lograr una complejidad de **O(n log n)**:

* **Merge Sort (Mezcla)**: Divide la lista en mitades hasta tener elementos individuales y luego los combina de forma ordenada. Es estable y predecible.
* **Quick Sort (Rápido)**: Elige un "pivote" y coloca los menores a un lado y los mayores al otro. Es muy veloz en la práctica, aunque su peor caso es **O(n²)** si el pivote se elige mal.

---

## Comparativa de Complejidad

| Algoritmo | Mejor Caso | Promedio | Peor Caso |
| --- | --- | --- | --- |
| Búsqueda Lineal | O(1) | O(n) | O(n) |
| Búsqueda Binaria | O(1) | O(log n) | O(log n) |
| Quick Sort | O(n log n) | O(n log n) | O(n²) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) |
| Bubble Sort | O(n) | O(n²) | O(n²) |

---

## Ejemplos de implementación

```python
# Búsqueda Binaria - O(log n)
def busqueda_binaria(lista, objetivo):
    bajo = 0
    alto = len(lista) - 1
    while bajo <= alto:
        medio = (bajo + alto) // 2
        if lista[medio] == objetivo:
            return medio
        elif lista[medio] < objetivo:
            bajo = medio + 1
        else:
            alto = medio - 1
    return -1

# Ordenamiento por Mezcla (Merge Sort) - O(n log n)
def merge_sort(lista):
    if len(lista) > 1:
        medio = len(lista) // 2
        izquierda = lista[:medio]
        derecha = lista[medio:]

        merge_sort(izquierda)
        merge_sort(derecha)

        i = j = k = 0
        while i < len(izquierda) and j < len(derecha):
            if izquierda[i] < derecha[j]:
                lista[k] = izquierda[i]
                i += 1
            else:
                lista[k] = derecha[j]
                j += 1
            k += 1

```