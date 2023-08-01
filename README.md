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
Para mejorar el programa y superar sus limitaciones, se proponen las siguientes soluciones:

En primer lugar, se sugiere utilizar estructuras de datos dinámicas, como vectores o listas, en lugar de arreglos estáticos con tamaño fijo. Esto permitirá adaptarse a diferentes cantidades de estudiantes en cada aula y eliminar la restricción de trabajar con un número limitado de datos. Con esta mejora, el programa podrá manejar conjuntos de datos más grandes y ser más flexible en su capacidad para analizar diversas cantidades de estudiantes.

Además, se propone implementar un manejo adecuado de excepciones al leer el archivo CSV con los datos de estatura. Esto garantizará que el programa pueda lidiar de manera controlada con situaciones en las que el archivo no exista o tenga un formato incorrecto. En lugar de mostrar mensajes de error confusos o dejar de funcionar abruptamente, el programa proporcionará mensajes claros y amigables para guiar al usuario en la solución de problemas con el archivo de datos.

Otra solución propuesta es optimizar los cálculos realizados en el programa. Actualmente, se calculan repetidamente algunos valores, como el número de intervalos y el ancho del intervalo, para ambos conjuntos de datos. Para mejorar la eficiencia del programa, se puede calcular estos valores una sola vez y luego reutilizarlos para ambas aulas, evitando repeticiones innecesarias y acelerando el proceso de análisis.

Por último, se sugiere realizar una validación para evitar divisiones por cero durante los cálculos. Si el número de intervalos calculado es cero, esto podría causar errores en tiempo de ejecución. Para evitar esta situación, el programa verificará previamente si el divisor es igual a cero antes de realizar la división. Si el divisor es cero, se mostrará un mensaje explicativo al usuario, evitando problemas inesperados y brindando una experiencia más segura y comprensible, de igual manera se implemento dentro de otras funciones para que detecte por ejemplo si no hay datos, o cosas así por el estilo, mostrando mediante la salida estandar de errores "cerr".
