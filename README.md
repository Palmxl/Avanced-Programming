# Avanced-Programming
**Objetivo del Taller**:

El objetivo de este taller es utilizar un programa en C++ para analizar dos conjuntos de datos que representan la estatura de los estudiantes en dos aulas diferentes. Queremos obtener información estadística relevante sobre estos datos, como el rango de estaturas, el número de intervalos adecuado para presentarlos en un histograma y las frecuencias relativas. Además, deseamos mostrar gráficamente los resultados mediante histogramas para visualizar de forma clara la distribución de estaturas en cada aula.

**Limitaciones del Código**:
Se interpretó acerca de las limitaciones establecidas lo siguiente:

Claro, aquí tienes una interpretación con palabras diferentes de las limitaciones:

1. **Tamaño fijo de los arreglos**: El programa actual solo puede manejar un número limitado de estudiantes en cada aula. Esto significa que si tenemos más de ese número, el programa no podrá procesarlos correctamente, lo que podría limitar el análisis a un grupo pequeño de datos.

2. **Manejo de errores**: Si el archivo con los datos no se encuentra o tiene un formato inesperado, el programa no sabrá cómo lidiar con esa situación y podría mostrar mensajes de error confusos o dejar de funcionar adecuadamente, lo que dificulta su uso y comprensión.

3. **Cálculos repetidos**: El programa realiza algunos cálculos más de una vez innecesariamente. Esto podría hacer que el programa se ejecute más lentamente de lo necesario y consuma más recursos de la computadora de los que debería, lo que podría afectar su rendimiento general.

4. **División entre cero**: Si por alguna razón el programa intenta dividir un número entre cero, se produce un error. Esto podría suceder si los datos no son suficientes para calcular ciertos valores, y en lugar de manejar esta situación, el programa simplemente falla, lo que puede ser frustrante para el usuario.

**Soluciones Propuestas**:

1. **Tamaño dinámico de los arreglos**: Se recomienda utilizar estructuras de datos dinámicas, como vectores o listas, en lugar de arreglos estáticos, para poder manejar conjuntos de datos de diferentes tamaños y evitar el límite de 20 estudiantes.

2. **Manejo de excepciones**: Implementar un manejo adecuado de excepciones al leer el archivo CSV, de modo que el programa pueda proporcionar mensajes de error apropiados al usuario si el archivo no existe o tiene un formato incorrecto, en lugar de generar errores inesperados.

3. **Optimización de cálculos**: Se sugiere calcular el número de intervalos y el ancho del intervalo una sola vez y luego reutilizar estos valores para ambos conjuntos de datos (Aula 1 y Aula 2), evitando así la redundancia de cálculos innecesarios.

4. **Validación de divisiones**: Antes de realizar divisiones, se debe verificar si el divisor es igual a cero para evitar divisiones entre cero y, en su lugar, proporcionar un mensaje al usuario sobre la imposibilidad de realizar el cálculo correspondiente.

Implementar estas soluciones permitirá que el programa sea más flexible, robusto y eficiente, y mejorará la experiencia del usuario al manejar situaciones inesperadas y evitar errores. Además, eliminará las limitaciones del código actual y permitirá trabajar con conjuntos de datos de diferentes tamaños y formatos de archivo.
