# Notación Big O: Una explicación narrativa

La notación Big O es una herramienta matemática que utilizamos en computación para describir cómo se comporta el tiempo de ejecución (o el uso de memoria) de un algoritmo a medida que crece el tamaño de la entrada. En lugar de medir segundos o megabytes —que dependen de la máquina, el lenguaje y hasta la fase de la luna—, nos interesa la **tendencia**: qué pasa cuando la entrada se hace muy grande.

## ¿Por qué nos importa la tendencia?

Porque los algoritmos que funcionan bien con pocos datos pueden volverse inútiles cuando la escala aumenta. Un método que tarda 0.1 segundos con 100 elementos podría tardar 10 segundos con 10.000 si su complejidad es cuadrática. Big O nos ayuda a anticipar esos cuellos de botella sin necesidad de ejecutar el código.

## La idea central: crecimiento asintótico

Cuando analizamos un algoritmo, contamos operaciones básicas (comparaciones, asignaciones, etc.) en función del tamaño de la entrada, al que llamamos `n`. Luego expresamos ese conteo de forma simplificada, conservando únicamente el término que crece más rápido y desechando constantes multiplicativas. Por ejemplo:

- Si un algoritmo hace `3n² + 5n + 2` operaciones, decimos que es **O(n²)**.
- Si hace `10n + 100`, es **O(n)**.
- Si siempre da igual el tamaño, hace `7` operaciones, es **O(1)**.

Esta simplificación se justifica porque cuando `n` es grande, los términos de menor orden y las constantes pierden relevancia frente al término dominante.

## Complejidad temporal y espacial

Big O se aplica tanto al **tiempo** (número de operaciones) como a la **memoria** (espacio adicional utilizado). Hablamos de _complejidad temporal_ y _complejidad espacial_. Por ejemplo, un algoritmo que ordena una lista puede necesitar un arreglo auxiliar del mismo tamaño —eso sería **O(n)** en espacio.

## Clases comunes de complejidad

Veamos las más habituales, ordenadas de mejor a peor escalabilidad:

- **O(1) – Tiempo constante**  
  El algoritmo siempre tarda lo mismo, sin importar `n`. Ejemplo: acceder a un elemento de un arreglo por su índice.

- **O(log n) – Tiempo logarítmico**  
  Crece muy lentamente. Aparece en algoritmos que dividen el problema en cada paso, como la búsqueda binaria.

- **O(n) – Tiempo lineal**  
  El tiempo crece proporcionalmente a `n`. Ejemplo: recorrer un arreglo una vez.

- **O(n log n) – Tiempo linealítmico**  
  Típico de algoritmos de ordenamiento eficientes (Merge Sort, Heap Sort). Es un poco peor que lineal, pero aceptable para muchos propósitos.

- **O(n²) – Tiempo cuadrático**  
  Común en bucles anidados que recorren toda la entrada. Ejemplo: comparar cada elemento con todos los demás. Con `n=10.000` se vuelve impracticable.

- **O(2ⁿ) – Tiempo exponencial**  
  Crece explosivamente. Suele aparecer en algoritmos de fuerza bruta para problemas combinatorios. Útil solo para `n` muy pequeños.

- **O(n!) – Tiempo factorial**  
  Peor aún. Resolver el problema del viajante por fuerza bruta es un ejemplo. Para `n` mayor que 10 o 12, olvídate.

## Reglas prácticas para calcular Big O

1. **Ignora constantes**: `O(2n)` es `O(n)`, `O(100)` es `O(1)`.
2. **Suma de complejidades**: si haces A (O(n)) y luego B (O(n)), el total es O(n) (no O(2n) → O(n)). Si uno es dominante, ese prevalece.
3. **Bucles anidados**: un bucle que itera `n` veces y dentro otro que también itera `n` veces da O(n²). Si el interno itera sobre una fracción de `n` (por ejemplo, la mitad), igual se simplifica a O(n²) porque la constante no importa.
4. **Divide y vencerás**: algoritmos que parten el problema en mitades y procesan cada parte suelen dar O(n log n).

## Ejemplos concretos

```python
# O(1)
def obtener_primero(lista):
    return lista[0] if lista else None

# O(n)
def suma_elementos(lista):
    total = 0
    for x in lista:
        total += x
    return total

# O(n²)
def pares_repetidos(lista):
    for i in range(len(lista)):
        for j in range(len(lista)):
            if i != j and lista[i] == lista[j]:
                return True
    return False

```
