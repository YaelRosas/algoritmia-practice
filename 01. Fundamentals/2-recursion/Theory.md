# Recursión

## ¿Qué es la recursión?

La recursión es una técnica donde una función **se llama a sí misma** para resolver un problema dividiéndolo en subproblemas más pequeños y similares.

Una función recursiva necesita dos partes esenciales:

1. **Caso base**: La condición que detiene la recursión
2. **Caso recursivo**: La llamada a sí misma con un problema más pequeño

## Analogía

Imagina que estás en un cine y quieres saber en qué fila estás sentado. Le preguntas a la persona de adelante: "¿En qué fila estás?". Ella le pregunta a la de adelante, y así sucesivamente hasta llegar a la primera fila. La primera fila responde "fila 1", y la respuesta va volviendo hacia atrás sumando 1 cada vez.

## Ejemplo básico: Factorial

El factorial de un número n (n!) es:

- 5! = 5 × 4 × 3 × 2 × 1 = 120
- 0! = 1 (por definición)

```javascript
function factorial(n) {
  // Caso base
  if (n === 0 || n === 1) {
    return 1;
  }

  // Caso recursivo
  return n * factorial(n - 1);
}

// factorial(5) = 5 * factorial(4)
// factorial(4) = 4 * factorial(3)
// factorial(3) = 3 * factorial(2)
// factorial(2) = 2 * factorial(1)
// factorial(1) = 1  ← caso base
// Resultado: 120
```

Ejemplo: Fibonacci
La secuencia de Fibonacci: 0, 1, 1, 2, 3, 5, 8, 13...
Cada número es la suma de los dos anteriores.

```
function fibonacci(n) {
  // Casos base
  if (n === 0) return 0
  if (n === 1) return 1

  // Caso recursivo
  return fibonacci(n - 1) + fibonacci(n - 2)
}

// fibonacci(4) = fibonacci(3) + fibonacci(2)
// fibonacci(3) = fibonacci(2) + fibonacci(1)
// fibonacci(2) = fibonacci(1) + fibonacci(0)
```

¿Cómo funciona? El call stack
Cada llamada recursiva se apila en la memoria:

```
factorial(3)
  → factorial(3) llama a factorial(2)
    → factorial(2) llama a factorial(1)
      → factorial(1) devuelve 1 (caso base)
    → factorial(2) recibe 1 y devuelve 2 × 1 = 2
  → factorial(3) recibe 2 y devuelve 3 × 2 = 6
Resultado: 6

```

Ventajas y desventajas
Ventajas Desventajas
Código más limpio y legible Puede ser más lento que la iteración
Ideal para problemas con estructura recursiva natural (árboles, grafos) Riesgo de desbordamiento de pila (stack overflow) si hay muchas llamadas
Divide problemas complejos en subproblemas simples Mayor consumo de memoria por el call stack
Cuándo usar recursión
Estructuras de datos jerárquicas: Árboles, grafos

Problemas de backtracking: Laberintos, sudoku, permutaciones

Algoritmos de divide y vencerás: Merge sort, quick sort

Problemas definidos recursivamente: Fibonacci, factorial, Torres de Hanoi

Recursión vs Iteración

```
// Recursivo
function sumRecursive(n) {
  if (n === 0) return 0
  return n + sumRecursive(n - 1)
}

// Iterativo
function sumIterative(n) {
  let sum = 0
  for (let i = 1; i <= n; i++) {
    sum += i
  }
  return sum
}
```

Regla práctica: Usa recursión cuando el problema sea naturalmente recursivo. Usa iteración cuando:

La profundidad de recursión pueda ser muy grande

La versión recursiva sea más difícil de entender

Necesites mejor rendimiento

Problemas comunes de recursión

1. Backtracking básico

```
function generatePermutations(arr, current = [], result = []) {
  if (current.length === arr.length) {
    result.push([...current])
    return result
  }

  for (let i = 0; i < arr.length; i++) {
    if (!current.includes(arr[i])) {
      current.push(arr[i])
      generatePermutations(arr, current, result)
      current.pop() // backtracking
    }
  }

  return result
}

// generatePermutations([1, 2, 3])
// [[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], [3,2,1]]
```

2. Recursión en árboles

```
function traverseTree(node) {
  if (!node) return

  console.log(node.value)        // Pre-order
  traverseTree(node.left)
  traverseTree(node.right)
}

Errores comunes
Olvidar el caso base: La función nunca se detiene → stack overflow

No reducir el problema: Llamar con el mismo argumento → recursión infinita

Usar recursión cuando no es necesario: La versión iterativa sería más clara

Ejercicios para practicar
Calcular la potencia de un número (xⁿ)

Invertir una cadena de texto

Contar dígitos de un número

Verificar si una palabra es palíndromo

Sumar todos los elementos de un array

Recorrer un árbol binario (in-order, pre-order, post-order)

```
