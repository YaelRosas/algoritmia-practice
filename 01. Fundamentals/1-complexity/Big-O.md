# 01 - Fundamentos

## Introducción

Los fundamentos son la base de todo algoritmo. Antes de resolver problemas complejos, es necesario entender cómo medir la eficiencia de una solución, cuándo usar recursión vs iteración, y dominar las técnicas básicas con arreglos y cadenas.

---

## 1. Complejidad Algorítmica (Big O)

### ¿Por qué nos importa la tendencia?

Porque los algoritmos que funcionan bien con pocos datos pueden volverse inútiles cuando la escala aumenta. Un método que tarda 0.1 segundos con 100 elementos podría tardar 10 segundos con 10.000 si su complejidad es cuadrática. Big O nos ayuda a anticipar esos cuellos de botella sin necesidad de ejecutar el código.

### crecimiento asintótico

Cuando analizamos un algoritmo, contamos operaciones básicas (comparaciones, asignaciones, etc.) en función del tamaño de la entrada, al que llamamos `n`.

**El crecimiento asintótico** describe el comportamiento de una función o algoritmo cuando el tamaño de la entrada **(n)** tiende al infinito, enfocándose en su tasa de crecimiento y no en valores pequeños.

Luego expresamos ese conteo de forma simplificada, conservando únicamente el término que crece más rápido y desechando constantes multiplicativas. Por ejemplo:

- Si un algoritmo hace `3n² + 5n + 2` operaciones, decimos que es **O(n²)**.
- Si hace `10n + 100`, es **O(n)**.
- Si siempre da igual el tamaño, hace `7` operaciones, es **O(1)**.

Esta simplificación se justifica porque cuando `n` es grande, los términos de menor orden y las constantes pierden relevancia frente al término dominante.

### Complejidad temporal y espacial

Big O se aplica tanto al **tiempo** (número de operaciones) como a la **memoria** (espacio adicional utilizado). Hablamos de _complejidad temporal_ y _complejidad espacial_. Por ejemplo, un algoritmo que ordena una lista puede necesitar un arreglo auxiliar del mismo tamaño —eso sería **O(n)** en espacio.

### Clases comunes de complejidad

| Notación   | Nombre       | Característica                                                                   |
| ---------- | ------------ | -------------------------------------------------------------------------------- |
| O(1)       | Constante    | El algoritmo siempre tarda lo mismo, sin importar `n`                            |
| O(log n)   | Logarítmica  | Crece muy lentamente. Aparece en algoritmos que dividen el problema en cada paso |
| O(n)       | Lineal       | El tiempo crece proporcionalmente a `n`                                          |
| O(n log n) | Linealítmica | Típico de algoritmos de ordenamiento eficientes                                  |
| O(n²)      | Cuadrática   | Común en bucles anidados que recorren toda la entrada                            |
| O(2ⁿ)      | Exponencial  | Crece explosivamente. Fuerza bruta para problemas combinatorios                  |
| O(n!)      | Factorial    | Peor aún. Solo útil para `n` muy pequeños (menos de 10-12)                       |

### Reglas prácticas para calcular Big O

1. **Ignora constantes**: `O(2n)` es `O(n)`, `O(100)` es `O(1)`.
2. **Suma de complejidades**: si haces A (`O(n)`) y luego B (`O(n)`), el total es `O(n)`. Si uno es dominante, ese prevalece.
3. **Bucles anidados**: un bucle que itera `n` veces y dentro otro que también itera `n` veces da `O(n²)`. Si el interno itera sobre una fracción de `n`, igual se simplifica a `O(n²)` porque la constante no importa.
4. **Divide y vencerás**: algoritmos que parten el problema en mitades y procesan cada parte suelen dar `O(n log n)`.

### Formato de cada ejercicio

Cada ejercicio tendrá la siguiente estructura:

```markdown
# Problema

[Descripción del problema]

## Ejemplo

Entrada: ...
Salida: ...

## Pistas

1. Pista 1
2. Pista 2
```

### Ejemplos

### Palindromo

```markdown
# Problema

Dada una cadena, determina si es un palíndromo.

Un palíndromo es una cadena que se lee igual de izquierda a derecha que de derecha a izquierda.  
Ignora espacios, mayúsculas/minúsculas y caracteres no alfanuméricos.

## Ejemplo

Entrada: "Anita lava la tina"  
Salida: verdadero

Entrada: "Hola mundo"  
Salida: falso

## Pistas

1. Normaliza la cadena (minúsculas y sin caracteres innecesarios).
2. Usa dos punteros: uno al inicio y otro al final.
3. Compara los caracteres y avanza hacia el centro.
```

Una posible solucion es

1- Recibe una cadena

2- Normaliza para eliminar diferencias de formato (acentos, mayusculas/minusculas, espacios, etc.)

3- Coloca dos indices en los extremos opuestos de la cadena para comparar los caracteres entre sí mientras se desplazan hacia el centro

4- Comparar los caracteres señalados por los indices

5- Si los caracteres señalados por los indices son distintos, el algoritmo determina que no es un palíndromo

6- Recorre los indices hacia el centro y regresa al paso 4 hasta que el primer indice sea estrictamente mayor al segundo

7- si el bucle termina todo el recorrido confirma que la cadena es un palíndromo

## Analisis de complejidad

### Tiempo

- **Normalización (paso 2):** recorre toda la cadena → **O(n)**
- **Comparación con dos índices (pasos 3–7):** en el peor caso recorre la mitad de la cadena → **O(n)**

**Total:**

- **O(n) + O(n) = O(n)**

### Espacio

Depende de cómo se implemente la normalización:

- Si creas una nueva cadena limpia → **O(n)**
- Si normalizas en el mismo espacio (in-place o ignorando caracteres sobre la marcha) → **O(1)**

---

### Resultado final

- **Complejidad temporal:** O(n)
- **Complejidad espacial:** O(n) o O(1)

## Pseudo codigo

```
ALGORITMO es_palindromo(cadena)

    cadena_limpia = limpiar_cadena(cadena)
    izquierda = 0
    derecha = longitud(cadena_limpia) - 1

    WHILE (izquierda < derecha) DO {
        IF cadena_limpia[izquierda] != cadena_limpia[derecha] THEN {
            RETURN falso
        }

        izquierda = izquierda + 1
        derecha = derecha - 1
    }

    RETURN verdadero

FIN ALGORITMO
```
