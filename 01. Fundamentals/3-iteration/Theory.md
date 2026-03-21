# Iteración

## ¿Qué es la iteración?

La iteración es el proceso de repetir un conjunto de instrucciones múltiples veces, generalmente hasta que se cumple una condición de parada. Es una de las bases de la programación y permite trabajar con colecciones de datos sin escribir código repetitivo.

En lugar de ejecutar manualmente una operación varias veces, usamos estructuras como `for`, `while` o `do-while` para automatizar ese comportamiento.

## ¿Por qué es importante?

La iteración está directamente relacionada con la complejidad algorítmica: la cantidad de veces que se repite un bloque de código afecta el rendimiento del algoritmo.

## Tipos de iteración

- **Iteración controlada por contador (`for`)**: se usa cuando sabemos cuántas veces se repetirá el ciclo.
- **Iteración controlada por condición (`while`)**: se repite mientras una condición sea verdadera.
- **Iteración post-condición (`do-while`)**: garantiza al menos una ejecución antes de evaluar la condición.

## Elementos clave de un ciclo

1. **Inicialización**: define el punto de partida.
2. **Condición**: determina si el ciclo continúa o termina.
3. **Actualización**: modifica el estado para evitar ciclos infinitos.

## Errores comunes

- Ciclos infinitos por no actualizar la condición.
- Off-by-one (iterar una vez de más o de menos).
- Modificar la colección mientras se itera sin control.

---

### Ejemplos

### Suma de elementos de un arreglo

```markdown
# Problema

Dado un arreglo de números enteros, calcula la suma de todos sus elementos.

## Ejemplo

Entrada: [1, 2, 3, 4]  
Salida: 10

Entrada: [5, -2, 7]  
Salida: 10

## Pistas

1. Inicializa una variable acumuladora en 0.
2. Recorre el arreglo elemento por elemento.
3. Ve sumando cada valor al acumulador.
```

**Una posible solución es:**

1- Recibe un arreglo de números

2- Inicializa una variable suma en 0

3- Recorre el arreglo desde el primer elemento hasta el último

4- En cada iteración, agrega el valor actual a suma

5- Al finalizar el recorrido, devuelve suma

## Analisis de complejidad

### Tiempo

- **Recorre todos los elementos una vez** → O(n)

### Espacio

Solo usa una variable adicional → O(1)

### Resultado final

- **Complejidad temporal:** O(n)
- **Complejidad espacial:** O(1)

## Pseudo codigo

```
ALGORITMO suma_arreglo(arreglo)

    suma = 0

    PARA i = 0 HASTA longitud(arreglo) - 1 HACER {
        suma = suma + arreglo[i]
    }

    RETURN suma

FIN ALGORITMO
```
