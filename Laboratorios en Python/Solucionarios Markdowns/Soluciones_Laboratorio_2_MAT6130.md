# Soluciones_Laboratorio_2_MAT6130

> Copia en Markdown generada desde `Soluciones_Laboratorio_2_MAT6130.ipynb` (se conservan todas las salidas de ejecucion).

<img src="https://i.ibb.co/93sNcdhp/Logo-pmat-color.png" align="right" width="250">

<br>

# **Matrices como organización y operación de datos**


## **Introducción contextual**

En el laboratorio anterior representamos registros individuales mediante vectores. En este laboratorio organizaremos varios registros con las mismas variables mediante matrices, para interpretar y reorganizar información, realizar operaciones y construir indicadores con apoyo de Python.


## Resultado de aprendizaje asociado

RA1: Representa información mediante vectores y matrices, realizando operaciones básicas e interpretando sus resultados en contextos de ciencia de datos e inteligencia artificial, con apoyo de Python.

## Indicadores de logro trabajados

IL1.4: Organiza datos multivariables en matrices, interpretando filas, columnas y entradas según el contexto.

IL1.5: Aplica operaciones matriciales para combinar, reorganizar o resumir información en contextos de datos, con apoyo de Python cuando corresponda.


```python
# @title
%%html
<div style="border: 4px solid #006d77; border-radius: 0px; overflow: hidden; font-family: sans-serif; max-width: 800px; margin-bottom: 20px;">

  <div style="background-color: #000000; color: #ffc107; padding: 10px 15px; font-weight: bold; font-size: 16px; display: flex; align-items: center;">
    <span style="margin-right: 10px; font-size: 18px;">💡</span>
    <span>Matrices como registros tabulares de información</span>
  </div>

  <div style="background-color: #ffffff; padding: 20px; display: flex; align-items: center; justify-content: space-between;">

    <div style="color: #000000; flex: 1; padding-right: 30px; font-size: 14px; line-height: 1.5;">
      Antes de comenzar las actividades, revisa este recurso para comprender cómo una matriz organiza varios registros y
      cómo interpretar sus filas, columnas, entradas y dimensión.
      <b>Escanea o haz clic en el código QR</b> para aprender también a transponer matrices y a seleccionar o
      resumir información por filas y columnas con NumPy.
    </div>

    <div style="flex-shrink: 0;">
      <a href="https://duoc.h5p.com/content/1292920545769139118" target="_blank">
        <img src="https://i.ibb.co/DD20bqQz/L2-H5P1.png"
             alt="QR Code"
             style="width: 100px; height: 100px; border: none;">
      </a>
    </div>

  </div>

  <div style="background-color: #000000; color: #ffc107; padding: 8px 15px; font-weight: bold; font-size: 16px;">
    Presentación interactiva H5P
  </div>

</div>
```

**Salida:**


<div style="border: 4px solid #006d77; border-radius: 0px; overflow: hidden; font-family: sans-serif; max-width: 800px; margin-bottom: 20px;">

  <div style="background-color: #000000; color: #ffc107; padding: 10px 15px; font-weight: bold; font-size: 16px; display: flex; align-items: center;">
    <span style="margin-right: 10px; font-size: 18px;">💡</span>
    <span>Matrices como registros tabulares de información</span>
  </div>

  <div style="background-color: #ffffff; padding: 20px; display: flex; align-items: center; justify-content: space-between;">

    <div style="color: #000000; flex: 1; padding-right: 30px; font-size: 14px; line-height: 1.5;">
      Antes de comenzar las actividades, revisa este recurso para comprender cómo una matriz organiza varios registros y 
      cómo interpretar sus filas, columnas, entradas y dimensión. 
      <b>Escanea o haz clic en el código QR</b> para aprender también a transponer matrices y a seleccionar o 
      resumir información por filas y columnas con NumPy.
    </div>

    <div style="flex-shrink: 0;">
      <a href="https://duoc.h5p.com/content/1292920545769139118" target="_blank">
        <img src="https://i.ibb.co/DD20bqQz/L2-H5P1.png"
             alt="QR Code"
             style="width: 100px; height: 100px; border: none;">
      </a>
    </div>

  </div>

  <div style="background-color: #000000; color: #ffc107; padding: 8px 15px; font-weight: bold; font-size: 16px;">
    Presentación interactiva H5P
  </div>

</div>


#📌 Consulta rápida: lectura de matrices

Para una matriz $A_{m\times n}$:

* $m$ indica la cantidad de filas y $n$ la cantidad de columnas.
* $a_{ij}$ corresponde a la entrada ubicada en la fila $i$ y columna $j$.
* $A^T$ intercambia las filas y las columnas.


###**Nota**: Matrices especiales

En los próximos laboratorios se utilizarán matrices con algunas estructuras particulares:

* **Matriz diagonal**: matriz cuadrada cuyos valores fuera de la diagonal principal son cero.
* **Matriz identidad**: matriz diagonal cuyos elementos de la diagonal principal son iguales a 1.

<br>

$$
D=
\begin{pmatrix}
d_1 & 0 & \cdots & 0 \\
0 & d_2 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & d_n
\end{pmatrix}
\qquad
I_n=
\begin{pmatrix}
1 & 0 & \cdots & 0 \\
0 & 1 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & 1
\end{pmatrix}
$$

<br>

**Recuerda**: ambas son matrices cuadradas y la matriz identidad es un caso particular de matriz diagonal.


# Instrucciones

Este laboratorio contiene problemas que deben resolverse tanto de forma analítica como de forma computacional.

Los problemas marcados con 📝 se deben resolver con lápiz y papel en tu cuaderno, mientras que aquellos marcados con 💻/🐍 se deben resolver usando Python.


# **Actividad 1 - Matriz de usuarios en una aplicación móvil 📝**


Una aplicación móvil analiza la actividad semanal de cinco usuarios. Para ello, organiza los datos en una matriz donde cada fila representa un usuario y cada columna una variable observada.

$$A = \begin{pmatrix}
10 & 4 & 2 & 1 \\
15 & 6 & 1 & 0 \\
8 & 3 & 0 & 2 \\
12 & 5 & 2 & 1 \\
18 & 7 & 3 & 0
\end{pmatrix}$$

Las columnas representan, respectivamente:

* horas de uso semanal;
* compras realizadas;
* reclamos enviados;
* tickets resueltos por autoservicio.

El equipo de análisis desea comprender el comportamiento de los usuarios y detectar registros destacados.


a) ¿Cuál es la dimensión de la matriz $A$?


La matriz tiene 5 filas y 4 columnas.
$$\dim(A) = 5\times 4$$


b) ¿Qué representa la fila 5?


La fila 5 es: $(18,7,3,0)$

Representa al usuario 5, quien registra 18 horas de uso semanal, 7 compras, 3 reclamos y 0 tickets resueltos por autoservicio.


c) ¿Qué representa la columna 2?


La columna 2 es:

 \begin{pmatrix}
4 \\
6 \\
3 \\
5 \\
7
\end{pmatrix}

Representa la cantidad de compras realizadas por cada usuario, estructurada como un vector columna.


d) Interprete el valor $a_{3,4}$.


El valor $a_{3,4}$ corresponde a la fila 3 y columna 4, $a_{3,4} = 2$. Esto significa que el usuario 3 resolvió 2 tickets mediante autoservicio.


e) ¿Qué usuario presenta mayor cantidad de horas de uso?


Las horas de uso están en la columna 1: $10, 15, 8, 12, 18$. El mayor valor es 18, por lo tanto el usuario 5 presenta mayor cantidad de horas de uso.


f) ¿Qué usuario presenta mayor interacción total si se suman todas sus componentes?


Se calcula la suma total por fila:

Usuario 1: $10 + 4 + 2 + 1 = 17$

Usuario 2: $15 + 6 + 1 + 0 = 22$

Usuario 3: $8 + 3 + 0 + 2 = 13$

Usuario 4: $12 + 5 + 2 + 1 = 20$

Usuario 5: $18 + 7 + 3 + 0 = 28$

El usuario 5 presenta mayor interacción total.

**Nota:** Aquí sumamos directamente para entender la mecánica de la matriz, pero en el abordaje real de este tipo de situaciones, antes de sumar variables distintas (como horas y compras), tendríamos que normalizarlas y/o ponderarlas.


# **Actividad 2 - Matriz de indicadores académicos 📝**


Una carrera desea analizar el desempeño de cuatro secciones en una asignatura. Para ello, construye una matriz donde cada fila representa una sección y cada columna un indicador académico.

$$B = \begin{pmatrix}
82 & 5,6 & 75 & 68 \\
76 & 5,2 & 68 & 60 \\
90 & 6,0 & 80 & 72 \\
70 & 4,9 & 62 & 55
\end{pmatrix}$$

Las columnas representan, respectivamente:

* tasa de asistencia, medida en porcentaje (%);
* promedio de notas, medido en escala de 1,0 a 7,0;
* tasa de aprobación, medida en porcentaje (%);
* tasa de participación en actividades, medida en porcentaje (%).

El equipo académico desea identificar fortalezas y posibles alertas.


a) Indique la dimensión de la matriz $B$.


La matriz tiene 4 filas y 4 columnas: $\dim (B) = 4 \times 4$


b) Interprete la fila 3.


La fila 3 es: $(90; 6,0 ;80; 72)$
Representa que la sección 3 tiene 90% de asistencia, promedio de notas 6,0, tasa de aprobación 80% y participación en actividades de 72%.


c) Interprete la entrada $b_{4,2}$


La entrada $b_{4,2}$ es $4,9$

Esto significa que la sección 4 tiene promedio de notas 4,9.


d) ¿Qué sección presenta mayor promedio de notas?


Los promedios de notas están en la columna 2:
$\begin{pmatrix}5,6\\
5,2\\
6,0\\
4,9\end{pmatrix}$

El mayor promedio corresponde a la sección 3.


e) ¿Qué sección presenta menor tasa de aprobación?


Las tasas de aprobación están en la columna 3:
$\begin{pmatrix}
75\\ 68\\ 80\\ 62\end{pmatrix}$

La menor tasa de aprobación corresponde a la sección 4, con 62%


f) Si se considera como alerta una aprobación menor a 65%, ¿qué secciones deberían revisarse?


Se consideran en alerta las secciones con aprobación menor a 65%.

* Sección 1: 75%, no está en alerta.
* Sección 2: 68%, no está en alerta.
* Sección 3: 80%, no está en alerta.
* Sección 4: 62%, sí está en alerta.

Por lo tanto, debería revisarse la sección 4.


# **Actividad 3 - Construcción de una matriz desde una tabla logística 📝**


Una empresa logística registra información de cuatro centros de distribución. La siguiente tabla resume pedidos procesados, entregas exitosas, reclamos y entregas fuera de plazo durante una jornada.

| Centro   | Pedidos procesados | Entregas exitosas | Reclamos | Entregas fuera de plazo |
| -------- | -----------------: | ----------------: | -------: | ----------------------: |
| Centro 1 |                240 |               220 |        8 |                      12 |
| Centro 2 |                300 |               285 |       12 |                      10 |
| Centro 3 |                180 |               170 |        5 |                       8 |
| Centro 4 |                260 |               230 |       15 |                      20 |


a) Construya la matriz $L$ asociada a la tabla, considerando que las filas representan centros y las columnas representan variables.


La matriz asociada es:

$$L = \begin{pmatrix}
240 & 220 & 8 & 12 \\
300 & 285 & 15 & 10 \\
180 & 170 & 5 & 8 \\
260 & 230 & 15 & 20
\end{pmatrix}$$


b) Indique la dimensión de $L$.


La matriz tiene 4 filas y 4 columnas.

$$\dim(L) = 4 \times 4$$


c) Interprete la entrada $l_{4,3}$


La entrada $l_{4,3}$ corresponde a la fila 4, columna 3.

$$l_{4,3} = 15$$

Esto significa que el centro 4 recibió 15 reclamos.


d) ¿Qué centro presenta mayor cantidad de entregas exitosas?


Las entregas exitosas corresponden a la columna 2:
$$\begin{pmatrix}220\\ 285\\ 170\\ 230\end{pmatrix}$$

El mayor valor es 285, por lo tanto el centro 2 presenta la mayor cantidad de entregas exitosas.


e) Calcule, para cada centro, la diferencia entre pedidos procesados y entregas exitosas.


Se calcula la diferencia entre pedidos procesados y entregas exitosas:

Centro 1:

$$240-220=20$$

Centro 2:

$$300-285=15$$

Centro 3:

$$180-170=10$$

Centro 4:

$$260-230=30$$

**Nota:** Si agrupáramos estos resultados, formarían un nuevo vector columna de brechas que podríamos añadir a nuestra matriz original


f) ¿Qué centro presenta mayor brecha entre pedidos procesados y entregas exitosas?


La mayor brecha corresponde al centro 4, con 30 pedidos no reflejados como entregas exitosas.


# **Actividad 4 - Transpuesta y reorganización de mediciones 📝**


Una empresa de sensores registra tres variables ambientales: temperatura, humedad y concentración de partículas, en cuatro zonas de una ciudad. La matriz de datos es:

$$S = \begin{pmatrix}
22 & 65 & 35 \\
25 & 60 & 50 \\
20 & 70 & 30 \\
27 & 58 & 55
\end{pmatrix}$$

Cada fila representa una zona y las columnas representan temperatura, humedad y partículas, respectivamente.


a) Indique la dimensión de S.


La matriz $S$ tiene 4 filas y 3 columnas.

$$\dim(S)=4 \times 3$$


b) Calcule la transpuesta $S^T$


La transpuesta es:

$$S^T = \begin{pmatrix}
22 & 25 & 20 & 27\\
65 & 60 & 70 & 58 \\
35 & 50 & 30 & 55
\end{pmatrix}$$


c) Indique la dimensión de $S^T$


La matriz $S^T$ tiene 3 filas y 4 columnas.

$$\dim(S^T)=3 \times 4$$


d) Interprete qué ocurre con filas y columnas al calcular la transpuesta.


Al calcular la transpuesta, las filas pasan a ser columnas y las columnas pasan a ser filas. En este caso, originalmente las filas eran zonas y las columnas eran variables. Después de transponer, las filas representan variables y las columnas representan zonas.

La transpuesta no modifica los valores registrados; solo reorganiza la matriz para analizar la información desde otra perspectiva.


e) En $S^T$, ¿qué representa la fila 3?


En $S^T$, la fila 3 es: $(35, 50, 30, 55)$

Representa la concentración de partículas en las cuatro zonas.


f) ¿En qué zona se registra la mayor concentración de partículas?


La concentración de partículas corresponde a la columna 3 de S, o fila 3 de $S^T$:

$$(35; 50; 30; 55)$$

El mayor valor es 55, correspondiente a la zona 4.


# 💡 Reflexión:

Responde brevemente:

a) ¿Qué representa una fila en una matriz de datos?

b) ¿Qué representa una columna?

c) ¿Por qué es importante conocer la dimensión de una matriz?

d) ¿Qué ocurre al calcular la transpuesta de una matriz?

e) ¿Por qué una tabla de datos puede interpretarse como una matriz?


# 🐍 Recordatorio Python

Para trabajar con matrices en NumPy:


```python
import numpy as np
```


Crear una matriz:


```python
A = np.array([
    [1, 2, 3],
    [4, 5, 6]
])
```


Consultar su dimensión:


```python
A.shape
```

**Salida:**


```
(2, 3)
```


Seleccionar una fila:


```python
A[0]
# En este caso estamos trayendo la primera fila de la matriz.
# (Recuerda que en Python los índices siempre comienzan a contar desde el 0)
# Nota: Al dar un solo número, Python asume automáticamente que pedimos la fila entera.
# Es exactamente equivalente a escribir A[0, :]
```

**Salida:**


```
array([1, 2, 3])
```


Seleccionar una columna:


```python
A[:,1]
# El símbolo ':' en la primera posición significa "selecciona TODAS las filas".
# El número '1' indica que queremos la segunda columna.
# IMPORTANTE: A diferencia de las filas, para extraer una columna NO podemos
# saltarnos la primera posición. El ':' es obligatorio para indicarle a Python
# que cruce todas las filas y nos traiga la variable completa.
```

**Salida:**


```
array([2, 5])
```


Seleccionar un subconjunto:


```python
A[0:2, 1:3]
# '0:2' extrae las filas: desde el índice 0 hasta el 1.
# '1:3' extrae las columnas: desde el índice 1 hasta el 2.
#
# REGLA CLAVE DE PYTHON: En un rango 'inicio:fin', el número de 'fin' NUNCA se incluye.
# Por lo tanto, 0:2 trae los índices 0 y 1 (primera y segunda fila de la matriz original).
# Y 1:3 trae los índices 1 y 2 (segunda y tercera columna de la matriz original).
```

**Salida:**


```
array([[2, 3],
       [5, 6]])
```


Cuando queremos calcular resúmenes de una matriz (como sumas o promedios), debemos indicarle a Python si queremos el cálculo para toda la matriz, por variables (columnas) o por registros (filas). Esto lo controlamos con el parámetro `axis` dentro de las funciones de NumPy.

`axis = 0` (Eje de las filas): Le dice a Python: "opera las filas entregando un indicador para cada columna (suma para cada columna, promedio para cada columna, etc".

`axis = 1` (Eje de las columnas): Le dice a Python: "opera las columnas entregando un indicador para cada fila (suma para cada fila, promedio para cada fila".


Calcular suma por filas:


```python
A.sum(axis=1)
# 'axis=1' indica que se operan las columnas.
# Al operar las columnas, el resultado es la suma total para CADA FILA.
```

**Salida:**


```
array([ 6, 15])
```


Calcular promedio por columnas:


```python
A.mean(axis=0)
# 'axis=0' indica que se operan las filas.
# Al operar las filas, el resultado es el promedio para CADA COLUMNA.
```

**Salida:**


```
array([2.5, 3.5, 4.5])
```


# **Actividad 5 - Matriz de monitoreo ambiental urbano 💻/🐍**


Una municipalidad registra cuatro variables ambientales en cinco sectores de la ciudad: nivel de ruido, temperatura, concentración de partículas y flujo vehicular estimado. Cada fila representa un sector y cada columna una variable ambiental.

$$M = \begin{pmatrix}
70 & 22 & 35 & 120\\
80 & 25 & 50 & 180 \\
65 & 21 & 30 & 100 \\
90 & 27 & 60 & 220\\
75 & 24 & 45 & 160
\end{pmatrix}$$

Las columnas de la matriz siguen el mismo orden en que se mencionan las variables.


a) Cree la matriz en Python.


```python
import numpy as np

# Matriz de monitoreo ambiental:
# Filas: sectores
# Columnas: [ruido, temperatura, partículas, flujo vehicular]
M = np.array([
    [70, 22, 35, 120],
    [80, 25, 50, 180],
    [65, 21, 30, 100],
    [90, 27, 60, 220],
    [75, 24, 45, 160]
])

print("Matriz M:")
print(M)
```

**Salida:**


```
Matriz M:
[[ 70  22  35 120]
 [ 80  25  50 180]
 [ 65  21  30 100]
 [ 90  27  60 220]
 [ 75  24  45 160]]
```


b) Muestre su dimensión.


```python
print("\nDimensión de M:")
print(M.shape)
```

**Salida:**


```

Dimensión de M:
(5, 4)
```


c) Extraiga la fila correspondiente al sector 4.


```python
# Fila del sector 4
sector_4 = M[3]
print("\nDatos del sector 4:")
print(sector_4)
```

**Salida:**


```

Datos del sector 4:
[ 90  27  60 220]
```


d) Extraiga la columna correspondiente a concentración de partículas.


```python
# Columna de partículas
particulas = M[:, 2]
print("\nConcentración de partículas por sector:")
print(particulas)
```

**Salida:**


```

Concentración de partículas por sector:
[35 50 30 60 45]
```


e) Calcule el promedio de cada variable ambiental.


```python
# Promedio por variable
promedios = M.mean(axis=0)
print("\nPromedio por variable:")
print(promedios)
```

**Salida:**


```

Promedio por variable:
[ 76.   23.8  44.  156. ]
```


f) Identifique el sector con mayor flujo vehicular.


```python
# Sector con mayor flujo vehicular
flujo = M[:, 3]
indice_mayor_flujo = np.argmax(flujo)

print("\nSector con mayor flujo vehicular:")
print("Sector", indice_mayor_flujo + 1, "con", flujo[indice_mayor_flujo])
```

**Salida:**


```

Sector con mayor flujo vehicular:
Sector 4 con 220
```


g) A partir de los cálculos realizados, ¿qué sector podría priorizarse para un análisis ambiental más detallado? Justifique su respuesta integrando los resultados obtenidos en los incisos anteriores.


El sector 4 podría priorizarse para un análisis ambiental más detallado, ya que presenta el mayor flujo vehicular y, al revisar sus datos, también muestra valores elevados en ruido y concentración de partículas. Además, sus valores se encuentran por sobre los promedios de las variables ambientales calculados para la ciudad, lo que sugiere que concentra condiciones más críticas que otros sectores.


# **Actividad 6 - Matriz de desempeño académico 💻/🐍**


Una coordinación académica analiza los resultados de seis estudiantes en una actividad práctica de ciencia de datos. Para cada estudiante se registran cuatro dimensiones de desempeño:

1.	Lectura e interpretación de datos,
2.	Representación matricial,
3.	Uso de Python,
4.	Interpretación de resultados.

Cada fila de la matriz representa el perfil de desempeño de un estudiante y cada columna representa una dimensión evaluada.

$$E =
\begin{pmatrix}
5,5 & 6,0 & 5,8 & 6,2 \\
4,8 & 5,2 & 5,0 & 5,4 \\
6,2 & 6,5 & 6,3 & 6,6 \\
5,0 & 5,4 & 5,1 & 5,6 \\
4,5 & 4,9 & 5,2 & 5,0 \\
6,0 & 5,8 & 6,1 & 6,4
\end{pmatrix}$$


a) Cree la matriz en Python.


```python
import numpy as np

# Matriz de notas:
# Filas: estudiantes
# Columnas: evaluaciones
E = np.array([
    [5.5, 6.0, 5.8, 6.2],
    [4.8, 5.2, 5.0, 5.4],
    [6.2, 6.5, 6.3, 6.6],
    [5.0, 5.4, 5.1, 5.6],
    [4.5, 4.9, 5.2, 5.0],
    [6.0, 5.8, 6.1, 6.4]
])

print("Matriz de notas:")
print(E)
```

**Salida:**


```
Matriz de notas:
[[5.5 6.  5.8 6.2]
 [4.8 5.2 5.  5.4]
 [6.2 6.5 6.3 6.6]
 [5.  5.4 5.1 5.6]
 [4.5 4.9 5.2 5. ]
 [6.  5.8 6.1 6.4]]
```


b) Extraiga el perfil de desempeño del estudiante 3 utilizando Python.


```python
# Estudiante 3
estudiante_3 = E[2]
print("\nNotas del estudiante 3:")
print(estudiante_3)
```

**Salida:**


```

Notas del estudiante 3:
[6.2 6.5 6.3 6.6]
```


c) Extraiga los resultados asociados a la dimensión “Interpretación de resultados” utilizando Python.


```python
# Evaluación 4
evaluacion_4 = E[:, 3]
print("\nNotas de la evaluación 4:")
print(evaluacion_4)
```

**Salida:**


```

Notas de la evaluación 4:
[6.2 5.4 6.6 5.6 5.  6.4]
```


d) Calcule el promedio de desempeño por estudiante.


```python
# Promedio por estudiante
promedio_estudiante = np.round(E.mean(axis=1),2)
print("\nPromedio por estudiante:")
print(promedio_estudiante)
```

**Salida:**


```

Promedio por estudiante:
[5.88 5.1  6.4  5.28 4.9  6.07]
```


e) Calcule el promedio de desempeño por dimensión.


```python
# Promedio por evaluación
promedio_evaluacion = np.round(E.mean(axis=0),2)
print("\nPromedio por evaluación:")
print(promedio_evaluacion)
```

**Salida:**


```

Promedio por evaluación:
[5.33 5.63 5.58 5.87]
```


f) Identifique, utilizando Python, al estudiante con mayor desempeño global.


```python
# Estudiante con mayor promedio
indice_mejor_estudiante = np.argmax(promedio_estudiante)
print("\nEstudiante con mayor promedio:")
print("Estudiante", indice_mejor_estudiante + 1, "con promedio", promedio_estudiante[indice_mejor_estudiante])
```

**Salida:**


```

Estudiante con mayor promedio:
Estudiante 3 con promedio 6.4
```


g) Identifique, utilizando Python, la dimensión con menor promedio general.


```python
# Evaluación con menor promedio
indice_eval_menor = np.argmin(promedio_evaluacion)
print("\nEvaluación con menor promedio:")
print("Evaluación", indice_eval_menor + 1, "con promedio", promedio_evaluacion[indice_eval_menor])
```

**Salida:**


```

Evaluación con menor promedio:
Evaluación 1 con promedio 5.333333333333333
```


h) Suponga que fue solicitado por la coordinación académica para elaborar un diagnóstico breve del grupo. Considerando los resultados anteriores, redacte una síntesis diagnóstica dirigida a coordinación académica.


El cálculo del promedio por estudiante permite identificar rendimientos individuales. El promedio por evaluación permite analizar si alguna evaluación presentó mayor dificultad general.

El estudiante 3 presenta el mayor promedio, por lo que muestra el mejor rendimiento global. La evaluación con menor promedio podría ser revisada por el equipo docente para identificar contenidos que requieran refuerzo.


# **Actividad 7 - Transpuesta y comparación de rutas 💻/🐍**


Una empresa de transporte registra la cantidad de pasajeros en cuatro rutas durante cinco horarios del día. Cada fila representa una ruta y cada columna un horario.

$$P = \begin{pmatrix}
30 & 45 & 50 & 40 & 35\\
25 & 35 & 55 & 45 & 50\\
40 & 50 & 60 & 55 & 65\\
20 & 30 & 35 & 25 & 40
\end{pmatrix}$$


a) Utilizando una misma función de NumPy aplicada directamente sobre la matriz $P$, obtenga un vector con el total de pasajeros de cada ruta y otro vector con el total de pasajeros de cada horario.


```python
import numpy as np

# Matriz de pasajeros
# Filas: rutas
# Columnas: horarios
P = np.array([
    [30, 45, 50, 40, 35],
    [25, 35, 55, 45, 50],
    [40, 50, 60, 55, 65],
    [20, 30, 35, 25, 40]
])

print("Matriz original:")
print(P)

# Total de pasajeros por ruta
# Se suman las columnas de cada fila
total_ruta = np.sum(P, axis=1)

print("\nTotal de pasajeros por ruta:")
print(total_ruta)

# Total de pasajeros por horario
# Se suman las filas de cada columna
total_horario = np.sum(P, axis=0)

print("\nTotal de pasajeros por horario:")
print(total_horario)
```

**Salida:**


```
Matriz original:
[[30 45 50 40 35]
 [25 35 55 45 50]
 [40 50 60 55 65]
 [20 30 35 25 40]]

Total de pasajeros por ruta:
[200 210 270 150]

Total de pasajeros por horario:
[115 160 200 165 190]
```


b) Explique qué representa cada componente de los vectores obtenidos en el inciso anterior.


En el inciso anterior se obtuvieron dos vectores:

`total_ruta: [200  210  270  150]`

Cada componente representa el total de pasajeros de una ruta, sumando todos los horarios registrados.

* La primera componente, 200, corresponde al total de pasajeros de la Ruta 1.
* La segunda componente, 210, corresponde al total de pasajeros de la Ruta 2.
* La tercera componente, 270, corresponde al total de pasajeros de la Ruta 3.
* La cuarta componente, 150, corresponde al total de pasajeros de la Ruta 4.

También se obtuvo:

`total_horario = [115 160 200 165 190]`

Cada componente representa el total de pasajeros de un horario, sumando las cuatro rutas.

* La primera componente, 115, corresponde al total de pasajeros del Horario 1.
* La segunda componente, 160, corresponde al total de pasajeros del Horario 2.
* La tercera componente, 200, corresponde al total de pasajeros del Horario 3.
* La cuarta componente, 165, corresponde al total de pasajeros del Horario 4.
* La quinta componente, 190, corresponde al total de pasajeros del Horario 5.


c) El equipo de planificación desea analizar cada horario como un registro formado por la cantidad de pasajeros de las cuatro rutas. Utilizando Python y sin volver a ingresar los datos, reorganice la matriz $P$ de modo que cada fila represente un horario y cada columna una ruta. Muestre la nueva matriz e indique su dimensión


```python
# Transpuesta de la matriz P
P_transpuesta = P.T

print("Matriz reorganizada:")
print(P_transpuesta)

print("\nDimensión de la nueva matriz:")
print(P_transpuesta.shape)
```

**Salida:**


```
Matriz reorganizada:
[[30 25 40 20]
 [45 35 50 30]
 [50 55 60 35]
 [40 45 55 25]
 [35 50 65 40]]

Dimensión de la nueva matriz:
(5, 4)
```


d) Interprete qué representa la transpuesta en este contexto.


La matriz original $P$ organiza la información por rutas, ya que cada fila representa una ruta y cada columna representa un horario del día. Al calcular la transpuesta $P^T$, las filas y columnas se intercambian: ahora cada fila representa un horario y cada columna representa una ruta.

Por lo tanto, la transpuesta permite reorganizar la información para analizar los datos desde otra perspectiva. En lugar de observar cuántos pasajeros tuvo cada ruta durante los distintos horarios, ahora se puede observar cuántos pasajeros hubo en cada horario comparando simultáneamente las cuatro rutas.

En este contexto, la transpuesta facilita responder preguntas como: ¿en qué horario se concentra mayor demanda entre todas las rutas? o ¿cómo se comparan las rutas dentro de un mismo horario?


# 💡 Reflexión:

Responde brevemente:

a) ¿Qué comando permite conocer la dimensión de una matriz en NumPy?

b) ¿Qué significa seleccionar una fila de una matriz de datos?

c) ¿Qué significa seleccionar una columna?

d) ¿Qué ventaja tiene seleccionar subconjuntos de una matriz?

e) ¿Qué diferencia hay entre `axis = 0` y `axis = 1` al calcular sumas o promedios?

f) ¿Cómo se calcula la transpuesta en NumPy?


```python
# @title
%%html
<div style="border: 4px solid #006d77; border-radius: 0px; overflow: hidden; font-family: sans-serif; max-width: 800px; margin-bottom: 20px;">

  <div style="background-color: #000000; color: #ffc107; padding: 10px 15px; font-weight: bold; font-size: 16px; display: flex; align-items: center;">
    <span style="margin-right: 10px; font-size: 18px;">💡</span>
    <span>Operaciones matriciales para comparar, ajustar y ponderar datos</span>
  </div>

  <div style="background-color: #ffffff; padding: 20px; display: flex; align-items: center; justify-content: space-between;">

    <div style="color: #000000; flex: 1; padding-right: 30px; font-size: 14px; line-height: 1.5;">
      Antes de continuar, revisa este recurso para aprender cómo combinar, comparar y ajustar matrices, y cómo construir
      uno o varios indicadores mediante productos matriciales.
      <b>Escanea o haz clic en el código QR</b> para revisar las condiciones de compatibilidad y su implementación en Python.
    </div>

    <div style="flex-shrink: 0;">
      <a href="https://duoc.h5p.com/content/1292920546762324738" target="_blank">
        <img src="https://i.ibb.co/WNcjqHJ7/L2-H5P2.png"
             alt="QR Code"
             style="width: 100px; height: 100px; border: none;">
      </a>
    </div>

  </div>

  <div style="background-color: #000000; color: #ffc107; padding: 8px 15px; font-weight: bold; font-size: 16px;">
    Presentación interactiva H5P
  </div>

</div>
```

**Salida:**


<div style="border: 4px solid #006d77; border-radius: 0px; overflow: hidden; font-family: sans-serif; max-width: 800px; margin-bottom: 20px;">

  <div style="background-color: #000000; color: #ffc107; padding: 10px 15px; font-weight: bold; font-size: 16px; display: flex; align-items: center;">
    <span style="margin-right: 10px; font-size: 18px;">💡</span>
    <span>Operaciones matriciales para comparar, ajustar y ponderar datos</span>
  </div>

  <div style="background-color: #ffffff; padding: 20px; display: flex; align-items: center; justify-content: space-between;">

    <div style="color: #000000; flex: 1; padding-right: 30px; font-size: 14px; line-height: 1.5;">
      Antes de continuar, revisa este recurso para aprender cómo combinar, comparar y ajustar matrices, y cómo construir 
      uno o varios indicadores mediante productos matriciales.
      <b>Escanea o haz clic en el código QR</b> para revisar las condiciones de compatibilidad y su implementación en Python.
    </div>

    <div style="flex-shrink: 0;">
      <a href="https://duoc.h5p.com/content/1292920546762324738" target="_blank">
        <img src="https://i.ibb.co/WNcjqHJ7/L2-H5P2.png"
             alt="QR Code"
             style="width: 100px; height: 100px; border: none;">
      </a>
    </div>

  </div>

  <div style="background-color: #000000; color: #ffc107; padding: 8px 15px; font-weight: bold; font-size: 16px;">
    Presentación interactiva H5P
  </div>

</div>


#📌 Consulta rápida: operaciones matriciales

La suma y la resta requieren matrices con la misma dimensión:

$$A+B,\ \ A-B,\ \  k\cdot A$$

Para el producto matricial:

$$A_{m\times n} \cdot B_{n\times r}= C_{m\times r}$$

Las dimensiones internas deben coincidir.

---

<br>

Si $X_{m\times n}$ contiene $m$ registros y $n$ variables:

#### Un indicador

$$X_{m\times n} \cdot w_{n\times 1}= r_{m\times 1}$$

#### Varios indicadores

$$X_{m\times n} \cdot W_{n\times k}= R_{m\times k}$$

**Recuerda**: las dimensiones internas deben coincidir.


# 🐍 Recordatorio Python

Producto matricial en Python

En NumPy, el operador `@` permite calcular productos matriciales, siempre que las dimensiones sean compatibles.


```python
import numpy as np

X = np.array([
    [10, 4, 1],
    [8, 6, 2]
])

p = np.array([[0.5],
              [1.0],
              [-2]])

resultado_vector = X @ p

print("Resultado:")
print(resultado_vector)
```

**Salida:**


```
Producto matriz-vector:
[[7.]
 [6.]]
```


El operador `@` se utiliza de la misma manera para calcular un producto matriz-vector. La diferencia se encuentra en las dimensiones del segundo factor y en la forma del resultado.

También es posible utilizar `np.dot(A, B)` o `A.dot(B)`. En esta guía se utilizará `@`, porque permite reconocer con mayor claridad que se está realizando un producto matricial.


# **Actividad 8 - Comparación de ventas entre dos semanas 💻/🐍**


Una tienda registra las ventas de cuatro productos en tres canales: online, presencial y marketplace. La matriz $A$ corresponde a la semana 1 y la matriz $B$ a la semana 2.

$$A =
\begin{pmatrix}
120 & 80 & 40 \\
90 & 60 & 30 \\
150 & 100 & 50 \\
70 & 45 & 20
\end{pmatrix}$$
<br>

$$B =
\begin{pmatrix}
130 & 85 & 50 \\
100 & 70 & 45 \\
160 & 95 & 65 \\
80 & 55 & 25
\end{pmatrix}$$

Las filas representan productos y las columnas representan canales de venta, en el siguiente orden:

$$\text{online, presencial, marketplace}$$

Además, la tienda asigna un peso estratégico a cada canal según su importancia comercial:

$$p = \begin{pmatrix}
0,5\\
0,3\\
0,2
\end{pmatrix}$$

donde:

* online tiene peso 0,5;
* presencial tiene peso 0,3;
* marketplace tiene peso 0,2.

El equipo comercial desea comparar la evolución de los productos considerando que los canales tienen distinta importancia estratégica.


a) Indique la dimensión de las matrices $A$ y $B$.


```python
import numpy as np

# Matriz A: ventas semana 1
# Filas: productos
# Columnas: canales [online, presencial, marketplace]
A = np.array([
    [120, 80, 40],
    [90, 60, 30],
    [150, 100, 50],
    [70, 45, 20]
])

# Matriz B: ventas semana 2
B = np.array([
    [130, 85, 50],
    [100, 70, 45],
    [160, 95, 65],
    [80, 55, 25]
])

# Vector de ponderaciones por canal
# [online, presencial, marketplace]
p = np.array([
    [0.5],
    [0.3],
    [0.2]
])


print("Dimensión de A:", A.shape)
print("Dimensión de B:", B.shape)
```

**Salida:**


```
Dimensión de A: (4, 3)
Dimensión de B: (4, 3)
```


b) Interprete la entrada $b_{3,2}$.


```python
entrada_b32 = B[2, 1]

print("Entrada b_3,2:", entrada_b32)
```

**Salida:**


```
Entrada b_3,2: 95
```


La entrada $b_{3,2} = 95$ significa que el Producto 3 vendió 95 unidades en el canal presencial durante la semana 2.


c) Verifique si se puede calcular la matriz de incremento: $B -A$


```python
print("Dimensión de A:", A.shape)
print("Dimensión de B:", B.shape)

if A.shape == B.shape:
    print("Sí se puede calcular B - A, porque ambas matrices tienen la misma dimensión.")
else:
    print("No se puede calcular B - A, porque las matrices tienen distinta dimensión.")
```

**Salida:**


```
Dimensión de A: (4, 3)
Dimensión de B: (4, 3)
Sí se puede calcular B - A, porque ambas matrices tienen la misma dimensión.
```


d) Calcule la matriz incremento: $B - A$


```python
incremento = B - A

print("Matriz incremento B - A:")
print(incremento)
```

**Salida:**


```
Matriz incremento B - A:
[[10  5 10]
 [10 10 15]
 [10 -5 15]
 [10 10  5]]
```


e) Interprete el resultado para el producto 3.


```python
incremento_producto_3 = incremento[2]

print("Incremento del producto 3:")
print(incremento_producto_3)
```

**Salida:**


```
Incremento del producto 3:
[10 -5 15]
```


Para el Producto 3, el vector de incremento es: $(10,\ -5,\ 15)$

Esto significa que, entre la semana 1 y la semana 2:

* en el canal online, las ventas aumentaron en 10 unidades;
* en el canal presencial, las ventas disminuyeron en 5 unidades;
* en el canal marketplace, las ventas aumentaron en 15 unidades.

Por lo tanto, el Producto 3 tuvo una mejora en dos canales, aunque presentó una disminución en el canal presencial.


f) Calcule el puntaje de desempeño comercial de cada producto en la semana 1 y en la semana 2 mediante los productos $A \cdot p$ y $B \cdot p$.


```python
puntaje_A = A @ p
puntaje_B = B @ p

print("Puntaje de desempeño comercial semana 1:")
print(puntaje_A)

print("\nPuntaje de desempeño comercial semana 2:")
print(puntaje_B)
```

**Salida:**


```
Puntaje de desempeño comercial semana 1:
[[ 92. ]
 [ 69. ]
 [115. ]
 [ 52.5]]

Puntaje de desempeño comercial semana 2:
[[100.5]
 [ 80. ]
 [121.5]
 [ 61.5]]
```


g) Interprete qué representa cada componente de los vectores $A \cdot p$ y $B \cdot p$.


Para la semana 1:

$$
A \cdot p =
\begin{pmatrix}
92 \\
69 \\
115 \\
52,5
\end{pmatrix}
$$

Cada componente representa el puntaje de desempeño comercial ponderado de un producto en la semana 1.

* 92 corresponde al puntaje ponderado del Producto 1.
* 69 corresponde al puntaje ponderado del Producto 2.
* 115 corresponde al puntaje ponderado del Producto 3.
* 52,5 corresponde al puntaje ponderado del Producto 4.
<br>

Para la semana 2:

$$
B \cdot p =
\begin{pmatrix}
100,5 \\
80 \\
121,5 \\
61,5
\end{pmatrix}
$$

Cada componente representa el puntaje de desempeño comercial ponderado de un producto en la semana 2.

* 100,5 corresponde al puntaje ponderado del Producto 1.
* 80 corresponde al puntaje ponderado del Producto 2.
* 121,5 corresponde al puntaje ponderado del Producto 3.
* 61,5 corresponde al puntaje ponderado del Producto 4.


h) Calcule la variación del puntaje de desempeño de cada producto entre ambas semanas.


```python
variacion_puntaje = puntaje_B - puntaje_A

print("Variación del puntaje de desempeño comercial:")
print(variacion_puntaje)
```

**Salida:**


```
Variación del puntaje de desempeño comercial:
[[ 8.5]
 [11. ]
 [ 6.5]
 [ 9. ]]
```


La variación del puntaje indica cuánto aumentó el desempeño comercial ponderado de cada producto entre la semana 1 y la semana 2.

* Producto 1: aumentó 8,5 puntos.
* Producto 2: aumentó 11 puntos.
* Producto 3: aumentó 6,5 puntos.
* Producto 4: aumentó 9 puntos.


i) A partir de los resultados obtenidos, determine qué producto presentó la mayor mejora en su desempeño comercial, considerando la importancia asignada a los canales. Justifique su respuesta.


```python
producto_mayor_mejora = np.argmax(variacion_puntaje) + 1
mayor_mejora = np.max(variacion_puntaje)

print("Producto con mayor mejora:", producto_mayor_mejora)
print("Mayor mejora en puntaje:", mayor_mejora)
```

**Salida:**


```
Producto con mayor mejora: 2
Mayor mejora en puntaje: 11.0
```


El producto que presentó la mayor mejora en su desempeño comercial ponderado fue el Producto 2, con un aumento de: 11 puntos entre la semana 1 y la semana 2.

Aunque otros productos también aumentaron sus ventas, el Producto 2 tuvo la mayor mejora al considerar la importancia estratégica asignada a cada canal. Esto significa que su crecimiento fue especialmente relevante en los canales con mayor ponderación dentro del análisis comercial.


# **Actividad 9 - Ajuste diferenciado de presupuesto por área 📝**


Una institución distribuye presupuesto en cuatro áreas durante tres periodos. La matriz $P$, en millones de pesos, representa el presupuesto asignado inicialmente:

$$P =
\begin{pmatrix}
50 & 55 & 60 \\
25 & 45 & 80 \\
25 & 35 & 45 \\
20 & 30 & 42
\end{pmatrix}$$

Las filas representan áreas institucionales, en el siguiente orden:

* docencia;
* investigación;
* vinculación;
* innovación.

Las columnas representan periodos 1, 2 y 3.

La institución analiza dos escenarios:

* Escenario A: aumento general de 10%.
* Escenario B: aumento general de 10% y refuerzo adicional de 5 millones para innovación en cada periodo.

Además, para comparar las áreas considerando la importancia estratégica de cada periodo, se define el vector de ponderaciones:

$$q = \begin{pmatrix}
0,2\\
0,3\\
0,5\end{pmatrix}$$

Esto significa que el periodo 1 tiene peso 0,2, el periodo 2 tiene peso 0,3 y el periodo 3 tiene peso 0,5.


a) Calcule la matriz ajustada del Escenario A: $P_A$


El Escenario A aplica un aumento general de 10%, por lo tanto:

$$P_A = 1,1 \cdot P $$

$$P_A =
1,1 \cdot
\begin{pmatrix}
50 & 55 & 60\\
25 & 45 & 80\\
25 & 35 & 45\\
20 & 30 & 42
\end{pmatrix}$$
<br>

$$P_A =
\begin{pmatrix}
55 & 60,5 & 66\\
27,5 & 49,5 & 88\\
27,5 & 38,5 & 49,5\\
22 & 33 & 46,2
\end{pmatrix}$$


b) Construya la matriz de refuerzo $R$ para el Escenario B.


El refuerzo adicional se aplica solo al área de innovación, que corresponde a la fila 4. Por lo tanto:

$$\begin{pmatrix}
0 & 0 & 0\\
0 & 0 & 0\\
0 & 0 & 0\\
5 & 5 & 5\end{pmatrix}$$


c) Calcule la matriz final del Escenario B e interprete cómo cambia el presupuesto del área de innovación respecto del Escenario A.


En el Escenario B, se aplica primero el aumento general de 10% y luego se agrega el refuerzo adicional para innovación:

$$P_B = P_A + R$$

$$P_B =
\begin{pmatrix}
55 & 60,5 & 66\\
27,5 & 49,5 & 88\\
27,5 & 38,5 & 49,5\\
22 & 33 & 46,2
\end{pmatrix}
+
\begin{pmatrix}
0 & 0 & 0\\
0 & 0 & 0\\
0 & 0 & 0\\
5 & 5 & 5
\end{pmatrix}$$
<br>

$$
P_B =
\begin{pmatrix}
55 & 60,5 & 66\\
27,5 & 49,5 & 88\\
27,5 & 38,5 & 49,5\\
27 & 38 & 51,2
\end{pmatrix}
$$
<br>

La fila correspondiente al área de innovación en el Escenario A es:

$$(22,\;33,\;46,2)$$

Mientras que en el Escenario B es:

$$(27,\;38,\;51,2)$$

Por lo tanto, respecto del Escenario A, el presupuesto de innovación aumenta en:

$$(27,\;38,\;51,2) - (22,\;33,\;46,2) = (5,\;5,\;5)$$

Esto significa que, en el Escenario B, el área de innovación recibe 5 millones de pesos adicionales en cada período respecto del Escenario A. Las demás áreas no cambian entre el Escenario A y el Escenario B.


d) Calcule el presupuesto total por área en el Escenario B. Exprese el resultado en un vector columna e identifique el área con mayor presupuesto total.


A partir de:

$$P_B =
\begin{pmatrix}
55 & 60,5 & 66\\
27,5 & 49,5 & 88\\
27,5 & 38,5 & 49,5\\
27 & 38 & 51,2
\end{pmatrix}$$

se suman los valores de cada fila.

Docencia:

$$55 + 60,5 + 66 = 181,5$$

Investigación:

$$27,5 + 49,5 + 88 = 165$$

Vinculación:

$$27,5 + 38,5 + 49,5 = 115,5$$

Innovación:

$$27 + 38 + 51,2 = 116,2$$

Por lo tanto, el vector columna con los presupuestos totales por área es:

$$\begin{pmatrix}
181,5\\
165\\
115,5\\
116,2
\end{pmatrix}$$

En el orden dado, este vector representa:

$$\begin{pmatrix}
\text{Docencia}\\
\text{Investigación}\\
\text{Vinculación}\\
\text{Innovación}
\end{pmatrix}$$

Por lo tanto, el área con mayor presupuesto total en el Escenario B es Docencia, con 181,5 millones de pesos.


e) Calcule el indicador ponderado por área usando: $P_B \cdot q$


El vector de ponderaciones es:

$$q =
\begin{pmatrix}
0,2\\
0,3\\
0,5
\end{pmatrix}$$

Entonces:

$$P_B \cdot q =
\begin{pmatrix}
55 & 60,5 & 66\\
27,5 & 49,5 & 88\\
27,5 & 38,5 & 49,5\\
27 & 38 & 51,2
\end{pmatrix}
\cdot
\begin{pmatrix}
0,2\\
0,3\\
0,5
\end{pmatrix}$$
<br>

Docencia:

$$55 \cdot(0,2) + 60,5 \cdot(0,3) + 66 \cdot(0,5) = 11 + 18,15 + 33 = 62,15$$

Investigación:

$$27,5 \cdot(0,2) + 49,5 \cdot(0,3) + 88 \cdot(0,5) = 5,5 + 14,85 + 44 = 64,35$$

Vinculación:

$$27,5 \cdot(0,2) + 38,5 \cdot(0,3) + 49,5 \cdot(0,5) = 5,5 + 11,55 + 24,75 = 41,8$$

Innovación:

$$27 \cdot(0,2) + 38 \cdot(0,3) + 51,2 \cdot(0,5) = 5,4 + 11,4 + 25,6 = 42,4$$

Por lo tanto:

$$P_B \cdot q =
\begin{pmatrix}
62,15\\
64,35\\
41,8\\
42,4
\end{pmatrix}
$$


f) Compare los resultados obtenidos mediante el presupuesto total y el indicador ponderado. Explique qué información aporta cada criterio y qué área debería priorizarse de acuerdo con la importancia asignada a los periodos.


Según el presupuesto total, el área con mayor asignación acumulada en el Escenario B es docencia, con: 181,5 millones de pesos.

Sin embargo, según el indicador ponderado, el área con mayor valor es investigación, con: 64,35

Esto ocurre porque el indicador ponderado no solo considera cuánto presupuesto recibe cada área en total, sino también en qué periodo se concentra ese presupuesto. Como el periodo 3 tiene el mayor peso estratégico (0,5), las áreas con mayor presupuesto en ese periodo aumentan su indicador ponderado.

En este caso, investigación recibe 88 millones en el periodo 3, por lo que supera a docencia en el indicador ponderado, aunque docencia tenga mayor presupuesto total acumulado.

Por lo tanto, si la decisión se basa en el presupuesto total, el área destacada es docencia. En cambio, si la decisión considera la importancia estratégica de los periodos, el área que debería priorizarse es investigación.


# 🐍 Recordatorio Python

Producto matricial en Python

En NumPy, el operador `@` permite calcular productos matriciales, siempre que las dimensiones sean compatibles.


```python
import numpy as np

X = np.array([
    [10, 4, 1],
    [8, 6, 2]
])

p = np.array([[0.5],
              [1.0],
              [-2]])

resultado_vector = X @ p

print("Resultado:")
print(resultado_vector)
```

**Salida:**


```
Producto matriz-vector:
[[7.]
 [6.]]
```


El operador `@` se utiliza de la misma manera para calcular un producto matriz-vector. La diferencia se encuentra en las dimensiones del segundo factor y en la forma del resultado.

También es posible utilizar `np.dot(A, B)` o `A.dot(B)`. En esta guía se utilizará `@`, porque permite reconocer con mayor claridad que se está realizando un producto matricial.


# **Actividad 10 - Selección de subconjuntos en una matriz de ventas 💻/🐍**


Una empresa registra las ventas de cinco productos durante cinco semanas. Cada fila de la matriz representa un producto y cada columna representa una semana.

$$V =
\begin{pmatrix}
120 & 130 & 125 & 140 & 150 \\
80 & 90 & 100 & 95 & 110 \\
200 & 210 & 190 & 220 & 230 \\
60 & 75 & 70 & 85 & 90 \\
150 & 160 & 155 & 170 & 180
\end{pmatrix}$$

El equipo comercial desea analizar específicamente las ventas de los productos 2, 3 y 4 durante las semanas 2, 3 y 4.


a) Utilizando Python, obtenga la submatriz $S$ correspondiente a los productos y semanas indicados. Indique la dimensión de la nueva matriz.


```python
import numpy as np

# Matriz de ventas
# Filas: productos
# Columnas: semanas
V = np.array([
    [120, 130, 125, 140, 150],
    [80,  90,  100, 95,  110],
    [200, 210, 190, 220, 230],
    [60,  75,  70,  85,  90],
    [150, 160, 155, 170, 180]
])

print("Matriz de ventas V:")
print(V)

# Productos 2, 3 y 4 -> filas con índices 1, 2 y 3
# Semanas 2, 3 y 4 -> columnas con índices 1, 2 y 3
S = V[1:4, 1:4]

print("\nSubmatriz S: productos 2, 3 y 4 durante semanas 2, 3 y 4:")
print(S)

print("\nDimensión de S:")
print(S.shape)
```

**Salida:**


```
Matriz de ventas V:
[[120 130 125 140 150]
 [ 80  90 100  95 110]
 [200 210 190 220 230]
 [ 60  75  70  85  90]
 [150 160 155 170 180]]

Submatriz S: productos 2, 3 y 4 durante semanas 2, 3 y 4:
[[ 90 100  95]
 [210 190 220]
 [ 75  70  85]]

Dimensión de S:
(3, 3)
```


b) Calcule el total de ventas de cada producto dentro del periodo seleccionado. Organice los resultados en un vector columna.


```python
# Total de ventas por producto dentro de la submatriz S
totales_periodo = S.sum(axis=1).reshape(-1, 1)

print("Total de ventas de cada producto en semanas 2, 3 y 4:")
print(totales_periodo)
```

**Salida:**


```
Total de ventas de cada producto en semanas 2, 3 y 4:
[[285]
 [620]
 [230]]
```


c) Considere el vector

$$u = \begin{pmatrix}
1 \\
1 \\
1
\end{pmatrix}$$

Calcule el producto $S\cdot u$ y compare el resultado con el vector obtenido en el inciso anterior. Explique qué ocurre y por qué.


```python
# Vector de unos de dimensión adecuada para multiplicar S
u = np.array([
    [1],
    [1],
    [1]
])

# Producto matriz-vector
resultado = S @ u

print("Resultado de S · u:")
print(resultado)

print("\nVector obtenido en el inciso anterior:")
print(totales_periodo)
```

**Salida:**


```
Resultado de S · u:
[[285]
 [620]
 [230]]

Vector obtenido en el inciso anterior:
[[285]
 [620]
 [230]]
```


El resultado coincide con el vector obtenido en el inciso anterior. Esto ocurre porque cada componente del vector $u$ es igual a $1$. Por lo tanto, al calcular el producto $S\cdot u$, cada elemento de una fila de $S$ se multiplica por 1 y luego los resultados se suman. De esta manera, se obtiene el total de ventas de cada producto.


d) Repita el procedimiento para la matriz completa $V$, utilizando un vector de unos de dimensión adecuada. Compare el producto con mayor venta en la ventana analizada y en el periodo completo. ¿Se mantiene el mismo producto como líder? Fundamente su respuesta.


```python
# Vector de unos para la matriz completa V
u_completo = np.ones((5, 1), dtype=int)

# Total de ventas por producto durante las 5 semanas
totales_completos = V @ u_completo

print("Total de ventas de cada producto durante las 5 semanas:")
print(totales_completos)

# Producto con mayor venta en la ventana seleccionada
indice_lider_periodo = np.argmax(totales_periodo)
producto_lider_periodo = indice_lider_periodo + 2  # porque S comienza en producto 2

# Producto con mayor venta en el periodo completo
indice_lider_completo = np.argmax(totales_completos)
producto_lider_completo = indice_lider_completo + 1  # porque V comienza en producto 1

print("\nProducto líder en semanas 2, 3 y 4:")
print("Producto", producto_lider_periodo)

print("\nProducto líder en el periodo completo:")
print("Producto", producto_lider_completo)
```

**Salida:**


```
Total de ventas de cada producto durante las 5 semanas:
[[ 665]
 [ 475]
 [1050]
 [ 380]
 [ 815]]

Producto líder en semanas 2, 3 y 4:
Producto 3

Producto líder en el periodo completo:
Producto 3
```


En la ventana seleccionada, correspondiente a los productos 2, 3 y 4 durante las semanas 2, 3 y 4, el producto con mayor venta es el Producto 3, con 620 unidades.

Al repetir el procedimiento para la matriz completa V, el producto con mayor venta total durante las cinco semanas también es el Producto 3, con 1.050 unidades.

Por lo tanto, sí se mantiene el mismo producto como líder tanto en la ventana analizada como en el periodo completo.


# **Actividad 11 - Aplicación de dos criterios mediante un producto matriz - matriz 📝**


Una empresa representa el comportamiento de tres usuarios mediante tres variables, previamente expresadas en una escala común:
1. compras realizadas;
2. interacciones con la plataforma;
3. solicitudes de soporte.

La matriz de registros es:

$$
X=
\begin{pmatrix}
6 & 2 & 1\\
3 & 5 & 2\\
7 & 3 & 5
\end{pmatrix}
$$

Donde, cada fila representa un usuario y cada columna una de las variables indicadas en el orden respectivo.
El equipo desea evaluar a los usuarios mediante dos criterios. Para ello, utiliza la siguiente matriz de ponderaciones:

$$
W=
\begin{pmatrix}
2 & 0\\
1 & 1\\
0 & 2
\end{pmatrix}
$$

La primera columna de $W$ corresponde a un puntaje de actividad comercial y la segunda a un puntaje de prioridad de atención.


a)	Verifique que el producto $X\cdot W$ está definido. Indique la dimensión de la matriz resultante y explique qué representarán sus filas y columnas.


La matriz $X$ tiene dimensión $3 \times 3$ porque tiene 3 filas y 3 columnas.

La matriz $W$ tiene dimensión $3 \times 2$ porque tiene 3 filas y 2 columnas.

El producto $X \cdot W$ está definido porque el número de columnas de $X$ coincide con el número de filas de $W$:

$$(3 \times 3)(3 \times 2)$$


Por lo tanto, la matriz resultante tendrá dimensión: $3 \times 2$

Esto significa que el resultado tendrá 3 filas y 2 columnas.

Las filas representarán a los tres usuarios y las columnas representarán los dos puntajes calculados:


b)	Calcule el producto $X\cdot W$.


$$
X \cdot W =
\begin{pmatrix}
6 & 2 & 1\\
3 & 5 & 2\\
7 & 3 & 5
\end{pmatrix}
\cdot
\begin{pmatrix}
2 & 0\\
1 & 1\\
0 & 2
\end{pmatrix}$$

Calculamos cada entrada de la matriz resultante.

Para el usuario 1:

$$(6,\ 2,\ 1)\cdot(2,\ 1,\ 0)=6\cdot(2) + 2\cdot(1) + 1\cdot(0) = 12 + 2 + 0 = 14$$

$$(6,\ 2,\ 1)\cdot(0,\ 1,\ 2)=6\cdot(0) + 2\cdot(1) + 1\cdot(2) = 0 + 2 + 2 = 4$$

Para el usuario 2:

$$(3,\ 5,\ 2)\cdot(2,\ 1,\ 0)=3\cdot(2) + 5\cdot(1) + 2\cdot(0)=6+5+0=11$$

$$(3,\ 5,\ 2)\cdot(0,\ 1,\ 2)=3\cdot(0) + 5\cdot(1) + 2\cdot(2)=0+5+4=9$$

Para el usuario 3:

$$(7,\ 3,\ 5)\cdot(2,\ 1,\ 0)=7\cdot(2) + 3\cdot(1) + 5\cdot(0) = 14 + 3 + 0 = 17$$

$$(7,\ 3,\ 5)\cdot(0,\ 1,\ 2)=7\cdot(0) + 3\cdot(1) + 5\cdot(2) = 0 + 3 + 10 = 13$$

Por lo tanto:

$$X \cdot W =
\begin{pmatrix}
14 & 4\\
11 & 9\\
17 & 13
\end{pmatrix}$$


c)	A partir del resultado obtenido, identifique qué usuario presenta el mayor puntaje de actividad comercial y cuál presenta la mayor prioridad de atención.


El vector correspondiente al puntaje de actividad comercial es la primera columna de $X \cdot W$:

$$\begin{pmatrix}
14\\
11\\
17
\end{pmatrix}$$

Por lo tanto:

* Usuario 1: 14 puntos;
* Usuario 2: 11 puntos;
* Usuario 3: 17 puntos.

El mayor puntaje de actividad comercial corresponde al usuario 3, con 17 puntos.

El vector correspondiente al puntaje de prioridad de atención es la segunda columna de $X \cdot W$:

$$\begin{pmatrix}
4\\
9\\
13
\end{pmatrix}$$

Por lo tanto:

* Usuario 1: 4 puntos;
* Usuario 2: 9 puntos;
* Usuario 3: 13 puntos.

El mayor puntaje de prioridad de atención corresponde también al usuario 3, con 13 puntos.

En consecuencia, con la matriz de ponderaciones original, el usuario 3 presenta tanto el mayor puntaje de actividad comercial como la mayor prioridad de atención.


d)	Posteriormente, el equipo decide penalizar las solicitudes de soporte en el puntaje de actividad comercial. Para analizar este cambio se ejecuta el siguiente código:

![image.png](data:image/png;base64,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)


Utilice la salida para explicar cómo cambió la clasificación de los usuarios según el puntaje de actividad comercial.


Con la matriz original, los puntajes de actividad comercial eran:

$$\begin{pmatrix}
14\\
11\\
17
\end{pmatrix}$$

Por lo tanto, el orden era:

$$\text{Usuario 3} > \text{Usuario 1} > \text{Usuario 2}$$

Después de penalizar las solicitudes de soporte, la salida ajustada fue:

$$\begin{pmatrix}
12 & 4\\
7 & 9\\
7 & 13
\end{pmatrix}$$

La primera columna corresponde al nuevo puntaje de actividad comercial:

$$\begin{pmatrix}
12\\
7\\
7
\end{pmatrix}$$

Por lo tanto, la nueva clasificación es:

$$\text{Usuario 1} > \text{Usuario 2} = \text{Usuario 3}$$

Esto ocurre porque las solicitudes de soporte ahora descuentan puntaje en la actividad comercial. El Usuario 3, aunque tenía más compras, también tenía más solicitudes de soporte, por eso baja su puntaje. En cambio, el Usuario 1 queda con el mayor puntaje comercial ajustado.


# **Actividad 12 - Cálculo de resultados comerciales mediante productos matriciales 📝**


Una empresa vende tres productos en tres tiendas. La matriz $Q$ representa la cantidad vendida de cada producto en cada tienda:

$$Q =
\begin{pmatrix}
10 & 5 & 8\\
8 & 7 & 6\\
12 & 4 & 10
\end{pmatrix}$$

Las filas representan las tiendas y las columnas representan los productos.

La matriz $R$ contiene, para cada producto, su ingreso unitario y su costo unitario:

$$R =
\begin{pmatrix}
20 & 12\\
30 & 18\\
25 & 15
\end{pmatrix}$$

Las filas representan los productos. La primera columna corresponde al ingreso unitario y la segunda al costo unitario.


a) Verifique que el producto $Q\cdot R$ está definido. Indique la dimensión del resultado y explique qué representarán sus filas y columnas.


La matriz Q tiene dimensión: $3 \times 3$

La matriz R tiene dimensión: $3 \times 2$

Como el número de columnas de $Q$ coincide con el número de filas de $R$, el producto es compatible.

El resultado tendrá dimensión: $3 \times 2$


b) Calcule el producto $Q \times R$.


$$Q \cdot R =
\begin{pmatrix}
10 & 5 & 8\\
8 & 7 & 6\\
12 & 4 & 10
\end{pmatrix}
\cdot
\begin{pmatrix}
20 & 12\\
30 & 18\\
25 & 15
\end{pmatrix}$$

Para la tienda 1:

$$10\cdot(20) + 5\cdot(30) + 8\cdot(25) = 200 + 150 + 200 = 550$$

$$10\cdot(12) + 5\cdot(18) + 8\cdot(15) = 120 + 90 + 120 = 330$$

Para la tienda 2:

$$8\cdot(20) + 7\cdot(30) + 6\cdot(25) = 160 + 210 + 150 = 520$$

$$8\cdot(12) + 7\cdot(18) + 6\cdot(15) = 96 + 126 + 90=312$$


Para la tienda 3:

$$12\cdot(20) + 4\cdot(30) + 10\cdot(25) = 240 + 120 + 250 = 610$$

$$12\cdot(12) + 4\cdot(18) + 10\cdot(15) = 144 + 72 + 150 = 366$$

Por lo tanto:

$$Q \cdot R =
\begin{pmatrix}
550 & 330\\
520 & 312\\
610 & 366
\end{pmatrix}$$

La primera columna representa el ingreso total de cada tienda y la segunda columna representa el costo total de cada tienda.


c) Para obtener la utilidad de cada tienda, se utiliza el vector:

$$u =
\begin{pmatrix}
1\\
-1
\end{pmatrix}$$

Calcule $(Q\cdot R)\cdot u$ e interprete qué representa cada componente del vector resultante.


Para obtener la utilidad de cada tienda, se utiliza el vector:

$$u=
\begin{pmatrix}
1\\
-1
\end{pmatrix}$$

Este vector permite calcular:

$$\text{utilidad}=\text{ingreso total}-\text{costo total}$$

Entonces:

$$
(Q\cdot R)\cdot u =
\begin{pmatrix}
550 & 330\\
520 & 312\\
610 & 366
\end{pmatrix}
\cdot
\begin{pmatrix}
1\\
-1
\end{pmatrix}$$

Calculamos cada componente:

$$550\cdot(1) + 330\cdot(-1) = 550 - 330 = 220$$

$$520\cdot(1) + 312\cdot(-1) = 520 - 312 = 208$$

$$610\cdot(1) + 366\cdot(-1) = 610 - 366 = 244$$

Por lo tanto:

$$(Q\cdot R)\cdot u =
\begin{pmatrix}
220\\
208\\
244
\end{pmatrix}$$

Cada componente representa la utilidad de una tienda:

$$\begin{pmatrix}
220\\
208\\
244
\end{pmatrix}
=
\begin{pmatrix}
\text{utilidad tienda 1}\\
\text{utilidad tienda 2}\\
\text{utilidad tienda 3}
\end{pmatrix}$$

Por lo tanto, la tienda con mayor utilidad en el escenario original es la tienda 3, con una utilidad de $244$.


```python
import numpy as np
Q = np.array([[10, 5, 8],
              [8,  7, 6],
              [12, 4, 10]])

u = ([[1],
      [-1]])
```


```python
import numpy as np

R_ajustada = np.array([[20, 14.4],
                       [30, 21.6],
                       [25, 18.0]])

r_ajustados = Q @ R_ajustada
utilidad_ajustada = r_ajustados @ u

print(utilidad_ajustada)
```

**Salida:**


```
[[154. ]
 [145.6]
 [170.8]]
```


d) Debido a un aumento del 20% en los costos de producción, la empresa actualiza la segunda columna de la matriz $R$, manteniendo sin cambios los ingresos unitarios. Un analista ejecuta el siguiente código:


![imagen.png](data:image/png;base64,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)


Interprete la salida y compárela con las utilidades obtenidas en el inciso anterior. ¿Qué tienda mantiene la mayor utilidad y cuál presenta la mayor disminución respecto del escenario original?


Cada componente representa la utilidad de una tienda después del aumento de costos:

$$\begin{pmatrix}
154\\
145,6\\
170,8
\end{pmatrix}
=
\begin{pmatrix}
\text{utilidad ajustada tienda 1}\\
\text{utilidad ajustada tienda 2}\\
\text{utilidad ajustada tienda 3}
\end{pmatrix}$$

Comparando con las utilidades originales:

$$\begin{pmatrix}
220\\
208\\
244
\end{pmatrix}$$

se observa que todas las utilidades disminuyen.

La disminución de utilidad por tienda es:

$$\begin{pmatrix}
220\\
208\\
244
\end{pmatrix}
-
\begin{pmatrix}
154\\
145,6\\
170,8
\end{pmatrix}
=
\begin{pmatrix}
66\\
62,4\\
73,2
\end{pmatrix}$$

Esto significa que:

- la tienda 1 disminuye su utilidad en 66;
- la tienda 2 disminuye su utilidad en 62,4;
- la tienda 3 disminuye su utilidad en 73,2.

Por lo tanto, después del aumento de costos, la tienda que mantiene la mayor utilidad es la tienda 3, con 170,8.

Además, la tienda que presenta la mayor disminución respecto del escenario original también es la tienda 3, ya que su utilidad baja en 73,2.


# 💡Reflexión:

Responde brevemente:

a) ¿Cuándo se pueden sumar o restar matrices?

b) ¿Qué efecto tiene multiplicar una matriz por un escalar?

c) ¿Qué representa un producto matriz-vector en un contexto de datos?

d) ¿Qué condición debe cumplirse para multiplicar una matriz por un vector?

e) ¿Qué representa un producto matriz-matriz en un contexto aplicado?

f) ¿Por qué el producto matriz-vector permite calcular indicadores para varios registros al mismo tiempo?


# **Actividad 13 - Puntajes de priorización preventiva 💻/🐍**


Un centro de salud organiza el seguimiento preventivo de seis pacientes. Cada paciente se representa mediante cuatro variables:

1. edad;
2. número de controles atrasados;
3. nivel de sedentarismo;
4. cantidad de alertas registradas.

La información se organiza en la matriz:

$$H=
\begin{pmatrix}
68 & 0 & 5 & 0\\
45 & 3 & 2 & 1\\
35 & 1 & 4 & 2\\
60 & 2 & 3 & 0\\
50 & 0 & 5 & 1\\
55 & 3 & 1 & 0
\end{pmatrix}$$

Cada fila representa un paciente y las columnas mantienen el orden de las variables indicadas.

Para apoyar la organización de las acciones del centro, se definen dos criterios:

- **seguimiento preventivo general**, que asigna mayor importancia a la edad y al nivel de sedentarismo;
- **prioridad de contacto**, que asigna mayor importancia a los controles atrasados y a las alertas registradas.

Las ponderaciones de ambos criterios se organizan, en el orden mencionado, en la matriz:

$$W=
\begin{pmatrix}
0,2 & 0,05\\
2 & 4\\
3 & 1\\
1 & 6
\end{pmatrix}$$


a) Utilizando Python, obtenga los puntajes de los seis pacientes para ambos criterios mediante un producto matricial.


```python
import numpy as np

# Matriz de pacientes
# Columnas: [edad, controles atrasados, nivel de sedentarismo, alertas registradas]
H = np.array([
    [68, 0, 5, 0],
    [45, 3, 2, 1],
    [35, 1, 4, 2],
    [60, 2, 3, 0],
    [50, 0, 5, 1],
    [55, 3, 1, 0]
])

# Matriz de ponderaciones
# Columna 1: seguimiento preventivo general
# Columna 2: prioridad de contacto
W = np.array([
    [0.2, 0.05],
    [2,   4],
    [3,   1],
    [1,   6]
])

# Producto matricial
puntajes = H @ W

print("Matriz de puntajes:")
print(puntajes)

print("\nDimensión de la matriz de puntajes:")
print(puntajes.shape)
```

**Salida:**


```
Matriz de puntajes:
[[28.6   8.4 ]
 [22.   22.25]
 [23.   21.75]
 [25.   14.  ]
 [26.   13.5 ]
 [20.   15.75]]

Dimensión de la matriz de puntajes:
(6, 2)
```


b) Identifique qué paciente obtiene el mayor puntaje en cada criterio. Justifique su respuesta relacionando los datos del paciente con las ponderaciones correspondientes.


```python
# Separar columnas de la matriz de puntajes
seguimiento_general = puntajes[:, 0]
prioridad_contacto = puntajes[:, 1]

# Identificar el paciente con mayor puntaje en cada criterio
paciente_mayor_seguimiento = np.argmax(seguimiento_general) + 1
paciente_mayor_contacto = np.argmax(prioridad_contacto) + 1

print("Puntajes de seguimiento preventivo general:")
print(seguimiento_general)

print("\nPuntajes de prioridad de contacto:")
print(prioridad_contacto)

print("\nPaciente con mayor seguimiento preventivo general:")
print("Paciente", paciente_mayor_seguimiento)

print("\nPaciente con mayor prioridad de contacto:")
print("Paciente", paciente_mayor_contacto)
```

**Salida:**


```
Puntajes de seguimiento preventivo general:
[28.6 22.  23.  25.  26.  20. ]

Puntajes de prioridad de contacto:
[ 8.4  22.25 21.75 14.   13.5  15.75]

Paciente con mayor seguimiento preventivo general:
Paciente 1

Paciente con mayor prioridad de contacto:
Paciente 2
```


El paciente 1 obtiene el mayor puntaje de seguimiento preventivo general, con 28,6, porque presenta la mayor edad y un nivel alto de sedentarismo, variables que tienen mayor peso en este criterio.
El paciente 2 obtiene el mayor puntaje de prioridad de contacto, con 22,25, porque registra tres controles atrasados y una alerta, variables que reciben las ponderaciones más altas en este segundo criterio.


c) Explique qué representa cada columna de la matriz de puntajes obtenida y cómo se relaciona con las columnas de la matriz de ponderaciones $W$.


La primera columna de $H \cdot W$ contiene los puntajes de seguimiento preventivo general y se obtiene utilizando la primera columna de $W$. La segunda columna contiene los puntajes de prioridad de contacto y se obtiene utilizando la segunda columna de "W$.
De esta forma, el producto matricial permite aplicar simultáneamente dos criterios de ponderación a todos los pacientes


# **Actividad 14 - Puntaje de prioridad en soporte técnico 💻/🐍**


Una empresa tecnológica registra cuatro variables para siete tickets de soporte:

1. tiempo de espera;
2. número de intentos de contacto;
3. nivel de impacto;
4. cantidad de usuarios afectados.

La información se organiza en la matriz:

$$
T=
\begin{pmatrix}
12 & 4 & 3 & 15\\
5 & 2 & 5 & 80\\
9 & 5 & 2 & 20\\
3 & 1 & 5 & 120\\
8 & 3 & 4 & 50\\
14 & 2 & 2 & 10\\
6 & 4 & 4 & 70
\end{pmatrix}
$$

Cada fila representa un ticket y las columnas mantienen el orden de las variables indicadas.

El equipo utiliza dos criterios para organizar la atención:

- **urgencia de atención**, que asigna mayor importancia al tiempo de espera, los intentos de contacto y el nivel de impacto;
- **alcance del incidente**, que asigna mayor importancia al nivel de impacto y a la cantidad de usuarios afectados.

Los vectores de ponderaciones son:

$$
p=
\begin{pmatrix}
1,5\\
2\\
4\\
0,05
\end{pmatrix},
\qquad
q=
\begin{pmatrix}
0,2\\
0,5\\
3\\
0,2
\end{pmatrix}
$$


a) Organice los vectores de ponderaciones en una matriz $W$ y utilice Python para obtener simultáneamente los puntajes de los siete tickets según ambos criterios.


```python
import numpy as np

# Matriz de tickets
# Columnas: [tiempo de espera, intentos de contacto, nivel de impacto, usuarios afectados]
T = np.array([
    [12, 4, 3, 15],
    [5,  2, 5, 80],
    [9,  5, 2, 20],
    [3,  1, 5, 120],
    [8,  3, 4, 50],
    [14, 2, 2, 10],
    [6,  4, 4, 70]])

# Vectores de ponderación
p = np.array([
    [1.5],
    [2],
    [4],
    [0.05]])

q = np.array([
    [0.2],
    [0.5],
    [3],
    [0.2]])

# Matriz de ponderaciones
# Columna 1: urgencia de atención
# Columna 2: alcance del incidente
W = np.hstack((p, q))

print("Matriz de ponderaciones W:")
print(W)

# Producto matricial
puntajes = T @ W

print("\nMatriz de puntajes:")
print(puntajes)
```

**Salida:**


```
Matriz de ponderaciones W:
[[1.5  0.2 ]
 [2.   0.5 ]
 [4.   3.  ]
 [0.05 0.2 ]]

Matriz de puntajes:
[[38.75 16.4 ]
 [35.5  33.  ]
 [32.5  14.3 ]
 [32.5  40.1 ]
 [36.5  25.1 ]
 [33.5  11.8 ]
 [36.5  29.2 ]]
```


b) A partir de los resultados, identifique qué ticket obtiene el mayor puntaje en cada criterio. Justifique su respuesta relacionando los registros del ticket con las ponderaciones utilizadas.


```python
# Separar los puntajes por criterio
urgencia_atencion = puntajes[:, 0]
alcance_incidente = puntajes[:, 1]

# Identificar máximos
ticket_mayor_urgencia = np.argmax(urgencia_atencion) + 1
ticket_mayor_alcance = np.argmax(alcance_incidente) + 1

print("Puntajes de urgencia de atención:")
print(urgencia_atencion)

print("\nPuntajes de alcance del incidente:")
print(alcance_incidente)

print("\nTicket con mayor urgencia de atención:")
print("Ticket", ticket_mayor_urgencia)

print("\nTicket con mayor alcance del incidente:")
print("Ticket", ticket_mayor_alcance)
```

**Salida:**


```
Puntajes de urgencia de atención:
[38.75 35.5  32.5  32.5  36.5  33.5  36.5 ]

Puntajes de alcance del incidente:
[16.4 33.  14.3 40.1 25.1 11.8 29.2]

Ticket con mayor urgencia de atención:
Ticket 1

Ticket con mayor alcance del incidente:
Ticket 4
```


El ticket 1 obtiene el mayor puntaje de urgencia de atención, con 38,75, principalmente por su tiempo de espera y su cantidad de intentos de contacto.
El ticket 4 obtiene el mayor puntaje de alcance del incidente, con 40,10, porque presenta el nivel máximo de impacto y la mayor cantidad de usuarios afectados.


c) Para establecer una prioridad final, el equipo asigna un 60% de importancia a la urgencia de atención y un 40% al alcance del incidente. Calcule mediante un producto matriz-vector el puntaje final de cada ticket e identifique cuál debería atenderse primero. Interprete qué representa cada componente del vector obtenido.


```python
# Vector de ponderación final
# 60% urgencia de atención, 40% alcance del incidente
r = np.array([
    [0.6],
    [0.4]])

# Puntaje final de cada ticket
puntaje_final = puntajes @ r

print("Puntaje final de cada ticket:")
print(puntaje_final)

# Identificar ticket que debe atenderse primero
ticket_prioritario = np.argmax(puntaje_final) + 1

print("\nTicket que debería atenderse primero:")
print("Ticket", ticket_prioritario)
```

**Salida:**


```
Puntaje final de cada ticket:
[[29.81]
 [34.5 ]
 [25.22]
 [35.54]
 [31.94]
 [24.82]
 [33.58]]

Ticket que debería atenderse primero:
Ticket 4
```


Cada componente del vector representa el puntaje final de un ticket, considerando ambos criterios. El ticket 4 debería atenderse primero, ya que obtiene el mayor puntaje final, con 35,54.


# Preparación de datos externos para trabajar con matrices


En algunas situaciones, los datos se encuentran almacenados en archivos externos, como archivos CSV o Excel. Antes de realizar operaciones matriciales, es necesario cargar las tablas, conservar sus etiquetas y verificar que los datos estén correctamente organizados.


### Cargar archivos y conservar las etiquetas


Pandas permite cargar archivos CSV mediante `pd.read_csv()` y archivos Excel mediante `pd.read_excel()`:




Las etiquetas de las filas y columnas pueden consultarse mediante:
tabla.index
tabla.columns


```python
tabla = pd.read_csv("archivo.csv", index_col = 0)
tabla = pd.read_excel("archivo.xlsx", index_col = 0)
```


En ambos casos, el argumento `index_col = 0` indica que la primera columna del archivo se utilizará como etiqueta de las filas, en lugar de incorporarla como una variable de la tabla.

Las etiquetas de las filas y columnas pueden consultarse mediante:


```python
tabla.index
tabla.columns
```


### Organizar datos mediante sus etiquetas


Cuando se combinan datos provenientes de dos tablas, no basta con que sus dimensiones sean compatibles. También es necesario que las variables relacionadas coincidan en significado y orden.
Por ejemplo:


```python
 tabla_B = tabla_B.loc[tabla_A.columns]
```


La instrucción anterior reorganiza las filas de `tabla_B` siguiendo el orden de las etiquetas presentes en las columnas de `tabla_A`.

De esta manera, la primera columna de `tabla_A` se relaciona con la primera fila de `tabla_B`, la segunda columna con la segunda fila, y así sucesivamente.


### Convertir una tabla en una matriz


Para realizar operaciones matriciales con NumPy, los datos numéricos de un DataFrame pueden convertirse en una matriz mediante:


```python
A = tabla_A.to_numpy()
B = tabla_B.to_numpy()
```


Las etiquetas de las filas y columnas no forman parte de las matrices obtenidas. Por esta razón, deben conservarse los DataFrames originales para interpretar posteriormente los resultados.


### Verificar la compatibilidad de las dimensiones


La propiedad `.shape` entrega la cantidad de filas y columnas de una matriz:


```python
A.shape
```


`(filas, columnas)`

Por esta razón:


```python
A.shape[0]  # cantidad de filas
A.shape[1]  # cantidad de columnas
```


Para verificar mediante Python si el producto $A \cdot b$ está definido, se puede comprobar:


```python
A.shape[1] == B.shape[0]
```


Esto compara la cantidad de columnas de la primera matriz con la cantidad de filas de la segunda.


# **Actividad 15 - Producto matriz-matriz en ventas multicanal con dataset 💻/🐍**


Una empresa registra las unidades vendidas de ocho productos en doce tiendas. La información está disponible en el archivo: **<a href="https://drive.google.com/uc?export=download&id=1kdBqYaxMQAilHV5H3juep6_O-oGgfjza">set de datos</a>**

Donde cada fila representa una tienda y cada columna representa un producto.
La empresa también dispone del archivo: **<a href="https://drive.google.com/uc?export=download&id=13npFlJLy3gYDEA05pol-F4jg9ZaWz2QK">set de datos</a>**

Donde cada fila representa un producto y sus columnas contienen las siguientes características:

*	ingreso unitario, medido en pesos;
*	costo unitario, medido en pesos;
*	tiempo de preparación, medido en minutos por unidad;
*	emisión logística, medida en kg de CO₂ equivalente por unidad.

El equipo desea utilizar estas tablas para obtener simultáneamente indicadores comerciales y operativos para cada tienda.


a) Cargue ambos archivos, organice los datos para que los productos coincidan en cantidad y orden, y convierta las tablas en las matrices numéricas $U$ y $G$.

**Nota:** Utilice el argumento `index_col = 0` de la función `pd.read_csv()` y la instrucción `.loc[]` para seleccionar y ordenar las filas del DataFrame.


```python
import pandas as pd
import numpy as np

# Cargar archivos
ventas = pd.read_csv("L2_A15_ventas_tiendas_productos.csv", index_col=0)
caracteristicas = pd.read_csv("L2_A15_caracteristicas_productos.csv", index_col=0)

# Limpiar posibles espacios en nombres de filas y columnas
ventas.columns = ventas.columns.str.strip()
ventas.index = ventas.index.str.strip()

caracteristicas.columns = caracteristicas.columns.str.strip()
caracteristicas.index = caracteristicas.index.str.strip()

# Mostrar tablas originales
print("Tabla de ventas:")
display(ventas)

print("Tabla de características:")
display(caracteristicas)
```

**Salida:**


```
Tabla de ventas:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Producto_1</th>
      <th>Producto_2</th>
      <th>Producto_3</th>
      <th>Producto_4</th>
      <th>Producto_5</th>
      <th>Producto_6</th>
      <th>Producto_7</th>
      <th>Producto_8</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda_1</th>
      <td>122</td>
      <td>112</td>
      <td>34</td>
      <td>126</td>
      <td>91</td>
      <td>40</td>
      <td>122</td>
      <td>141</td>
    </tr>
    <tr>
      <th>Tienda_2</th>
      <td>94</td>
      <td>180</td>
      <td>180</td>
      <td>40</td>
      <td>80</td>
      <td>70</td>
      <td>50</td>
      <td>180</td>
    </tr>
    <tr>
      <th>Tienda_3</th>
      <td>72</td>
      <td>21</td>
      <td>107</td>
      <td>177</td>
      <td>57</td>
      <td>149</td>
      <td>40</td>
      <td>77</td>
    </tr>
    <tr>
      <th>Tienda_4</th>
      <td>41</td>
      <td>108</td>
      <td>68</td>
      <td>78</td>
      <td>34</td>
      <td>70</td>
      <td>127</td>
      <td>74</td>
    </tr>
    <tr>
      <th>Tienda_5</th>
      <td>83</td>
      <td>150</td>
      <td>70</td>
      <td>154</td>
      <td>40</td>
      <td>92</td>
      <td>37</td>
      <td>151</td>
    </tr>
    <tr>
      <th>Tienda_6</th>
      <td>108</td>
      <td>79</td>
      <td>33</td>
      <td>28</td>
      <td>109</td>
      <td>72</td>
      <td>149</td>
      <td>103</td>
    </tr>
    <tr>
      <th>Tienda_7</th>
      <td>111</td>
      <td>130</td>
      <td>27</td>
      <td>54</td>
      <td>100</td>
      <td>69</td>
      <td>123</td>
      <td>151</td>
    </tr>
    <tr>
      <th>Tienda_8</th>
      <td>21</td>
      <td>153</td>
      <td>73</td>
      <td>125</td>
      <td>23</td>
      <td>73</td>
      <td>165</td>
      <td>63</td>
    </tr>
    <tr>
      <th>Tienda_9</th>
      <td>33</td>
      <td>114</td>
      <td>67</td>
      <td>34</td>
      <td>59</td>
      <td>101</td>
      <td>130</td>
      <td>72</td>
    </tr>
    <tr>
      <th>Tienda_10</th>
      <td>43</td>
      <td>173</td>
      <td>143</td>
      <td>60</td>
      <td>176</td>
      <td>34</td>
      <td>64</td>
      <td>84</td>
    </tr>
    <tr>
      <th>Tienda_11</th>
      <td>108</td>
      <td>90</td>
      <td>28</td>
      <td>107</td>
      <td>148</td>
      <td>155</td>
      <td>82</td>
      <td>158</td>
    </tr>
    <tr>
      <th>Tienda_12</th>
      <td>100</td>
      <td>155</td>
      <td>52</td>
      <td>142</td>
      <td>24</td>
      <td>60</td>
      <td>47</td>
      <td>154</td>
    </tr>
  </tbody>
</table>


```
Tabla de características:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ingreso_unitario</th>
      <th>costo_unitario</th>
      <th>tiempo_preparacion</th>
      <th>emision_logistica</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Producto_1</th>
      <td>20392.0</td>
      <td>19183.0</td>
      <td>4.0</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>Producto_2</th>
      <td>25067.0</td>
      <td>15965.0</td>
      <td>2.0</td>
      <td>0.93</td>
    </tr>
    <tr>
      <th>Producto_3</th>
      <td>27265.0</td>
      <td>13154.0</td>
      <td>6.0</td>
      <td>0.63</td>
    </tr>
    <tr>
      <th>Producto_4</th>
      <td>31488.0</td>
      <td>14762.0</td>
      <td>11.0</td>
      <td>3.05</td>
    </tr>
    <tr>
      <th>Producto_5</th>
      <td>14454.0</td>
      <td>10056.0</td>
      <td>8.0</td>
      <td>1.76</td>
    </tr>
    <tr>
      <th>Producto_6</th>
      <td>23837.0</td>
      <td>19948.0</td>
      <td>8.0</td>
      <td>2.53</td>
    </tr>
    <tr>
      <th>Producto_7</th>
      <td>26039.0</td>
      <td>13110.0</td>
      <td>10.0</td>
      <td>4.13</td>
    </tr>
    <tr>
      <th>Producto_8</th>
      <td>31115.0</td>
      <td>18773.0</td>
      <td>11.0</td>
      <td>1.50</td>
    </tr>
  </tbody>
</table>


```python
# Orden de productos según la matriz de ventas
productos = ventas.columns

# Reordenar características para que coincidan con el orden de productos de ventas
caracteristicas_ordenadas = caracteristicas.loc[productos]

print("Características ordenadas según los productos de la matriz de ventas:")
display(caracteristicas_ordenadas)
```

**Salida:**


```
Características ordenadas según los productos de la matriz de ventas:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ingreso_unitario</th>
      <th>costo_unitario</th>
      <th>tiempo_preparacion</th>
      <th>emision_logistica</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Producto_1</th>
      <td>20392.0</td>
      <td>19183.0</td>
      <td>4.0</td>
      <td>0.60</td>
    </tr>
    <tr>
      <th>Producto_2</th>
      <td>25067.0</td>
      <td>15965.0</td>
      <td>2.0</td>
      <td>0.93</td>
    </tr>
    <tr>
      <th>Producto_3</th>
      <td>27265.0</td>
      <td>13154.0</td>
      <td>6.0</td>
      <td>0.63</td>
    </tr>
    <tr>
      <th>Producto_4</th>
      <td>31488.0</td>
      <td>14762.0</td>
      <td>11.0</td>
      <td>3.05</td>
    </tr>
    <tr>
      <th>Producto_5</th>
      <td>14454.0</td>
      <td>10056.0</td>
      <td>8.0</td>
      <td>1.76</td>
    </tr>
    <tr>
      <th>Producto_6</th>
      <td>23837.0</td>
      <td>19948.0</td>
      <td>8.0</td>
      <td>2.53</td>
    </tr>
    <tr>
      <th>Producto_7</th>
      <td>26039.0</td>
      <td>13110.0</td>
      <td>10.0</td>
      <td>4.13</td>
    </tr>
    <tr>
      <th>Producto_8</th>
      <td>31115.0</td>
      <td>18773.0</td>
      <td>11.0</td>
      <td>1.50</td>
    </tr>
  </tbody>
</table>


b) Verifique que el producto $U \cdot G$ esté definido e indique la dimensión de cada matriz, la dimensión esperada del resultado, y qué representan las filas y columnas de la matriz resultante.


```python
# Convertir a matrices numéricas
U = ventas.to_numpy(dtype=float)
G = caracteristicas_ordenadas.to_numpy(dtype=float)

print("Dimensión de U:", U.shape)
print("Dimensión de G:", G.shape)

if U.shape[1] == G.shape[0]:
    print("El producto U · G está definido.")
    print("Dimensión esperada del resultado:", (U.shape[0], G.shape[1]))
else:
    print("El producto U · G no está definido.")
```

**Salida:**


```
Dimensión de U: (12, 8)
Dimensión de G: (8, 4)
El producto U · G está definido.
Dimensión esperada del resultado: (12, 4)
```


c) Calcule el producto matricial $Y= U \cdot G$.


```python
# Producto matricial
Y = U @ G

# Crear DataFrame para interpretar mejor el resultado
Y_df = pd.DataFrame(
    Y,
    index=ventas.index,
    columns=[
        "ingreso_total",
        "costo_total",
        "tiempo_total_preparacion",
        "emision_total_logistica"
    ]
)

print("Matriz de indicadores Y = U · G:")
display(Y_df.round(2))
```

**Salida:**


```
Matriz de indicadores Y = U · G:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ingreso_total</th>
      <th>costo_total</th>
      <th>tiempo_total_preparacion</th>
      <th>emision_total_logistica</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda_1</th>
      <td>20022593.0</td>
      <td>12395083.0</td>
      <td>6121.0</td>
      <td>1559.80</td>
    </tr>
    <tr>
      <th>Tienda_2</th>
      <td>22323688.0</td>
      <td>13870582.0</td>
      <td>5936.0</td>
      <td>1253.60</td>
    </tr>
    <tr>
      <th>Tienda_3</th>
      <td>18298368.0</td>
      <td>11252158.0</td>
      <td>5814.0</td>
      <td>1427.98</td>
    </tr>
    <tr>
      <th>Tienda_4</th>
      <td>15622881.0</td>
      <td>9349067.0</td>
      <td>4562.0</td>
      <td>1278.23</td>
    </tr>
    <tr>
      <th>Tienda_5</th>
      <td>20643260.0</td>
      <td>12738316.0</td>
      <td>5833.0</td>
      <td>1385.57</td>
    </tr>
    <tr>
      <th>Tienda_6</th>
      <td>16340444.0</td>
      <td>10599786.0</td>
      <td>5167.0</td>
      <td>1388.33</td>
    </tr>
    <tr>
      <th>Tienda_7</th>
      <td>18950044.0</td>
      <td>12186334.0</td>
      <td>5703.0</td>
      <td>1454.27</td>
    </tr>
    <tr>
      <th>Tienda_8</th>
      <td>18519051.0</td>
      <td>10684321.0</td>
      <td>5314.0</td>
      <td>1583.25</td>
    </tr>
    <tr>
      <th>Tienda_9</th>
      <td>15313594.0</td>
      <td>9500283.0</td>
      <td>4508.0</td>
      <td>1276.00</td>
    </tr>
    <tr>
      <th>Tienda_10</th>
      <td>18636140.0</td>
      <td>11217616.0</td>
      <td>5280.0</td>
      <td>1245.88</td>
    </tr>
    <tr>
      <th>Tienda_11</th>
      <td>21476297.0</td>
      <td>14077842.0</td>
      <td>6939.0</td>
      <td>1720.78</td>
    </tr>
    <tr>
      <th>Tienda_12</th>
      <td>19606320.0</td>
      <td>12118523.0</td>
      <td>5420.0</td>
      <td>1289.16</td>
    </tr>
  </tbody>
</table>


d) Para obtener la utilidad aproximada de cada tienda, utilice el vector:

$$v = \begin{pmatrix}
1\\
-1\\
0\\
0
\end{pmatrix}$$

Calcule el producto entre la matriz $Y$ y el vector $v$, e identifique la tienda con mayor utilidad aproximada. Explique por qué el producto con el vector v permite obtener la diferencia entre el ingreso total y el costo total.


```python
# Vector para calcular utilidad aproximada
v = np.array([
    [1],
    [-1],
    [0],
    [0]])

# Producto entre Y y v
utilidad = Y @ v

# Crear DataFrame con la utilidad
utilidad_df = pd.DataFrame(
    utilidad,
    index=ventas.index,
    columns=["utilidad_aproximada"])

print("Utilidad aproximada por tienda:")
display(utilidad_df.round(2))

# Identificar tienda con mayor utilidad
tienda_mayor_utilidad = utilidad_df["utilidad_aproximada"].idxmax()
mayor_utilidad = utilidad_df["utilidad_aproximada"].max()

print("Tienda con mayor utilidad aproximada:", tienda_mayor_utilidad)
print("Mayor utilidad aproximada:", mayor_utilidad)
```

**Salida:**


```
Utilidad aproximada por tienda:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>utilidad_aproximada</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda_1</th>
      <td>7627510.0</td>
    </tr>
    <tr>
      <th>Tienda_2</th>
      <td>8453106.0</td>
    </tr>
    <tr>
      <th>Tienda_3</th>
      <td>7046210.0</td>
    </tr>
    <tr>
      <th>Tienda_4</th>
      <td>6273814.0</td>
    </tr>
    <tr>
      <th>Tienda_5</th>
      <td>7904944.0</td>
    </tr>
    <tr>
      <th>Tienda_6</th>
      <td>5740658.0</td>
    </tr>
    <tr>
      <th>Tienda_7</th>
      <td>6763710.0</td>
    </tr>
    <tr>
      <th>Tienda_8</th>
      <td>7834730.0</td>
    </tr>
    <tr>
      <th>Tienda_9</th>
      <td>5813311.0</td>
    </tr>
    <tr>
      <th>Tienda_10</th>
      <td>7418524.0</td>
    </tr>
    <tr>
      <th>Tienda_11</th>
      <td>7398455.0</td>
    </tr>
    <tr>
      <th>Tienda_12</th>
      <td>7487797.0</td>
    </tr>
  </tbody>
</table>


```
Tienda con mayor utilidad aproximada: Tienda_2
Mayor utilidad aproximada: 8453106.0
```


e)	A partir del reporte obtenido, recomiende:

*	una tienda que podría priorizarse para una estrategia de expansión comercial;
*	una tienda que debería ser revisada desde el punto de vista operativo o logístico.

Justifique ambas decisiones utilizando al menos dos indicadores calculados.


```python
# Reporte completo
reporte = Y_df.copy()
reporte["utilidad_aproximada"] = utilidad_df["utilidad_aproximada"]

print("Reporte completo por tienda:")
display(reporte.round(2))
```

**Salida:**


```
Reporte completo por tienda:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ingreso_total</th>
      <th>costo_total</th>
      <th>tiempo_total_preparacion</th>
      <th>emision_total_logistica</th>
      <th>utilidad_aproximada</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda_1</th>
      <td>20022593.0</td>
      <td>12395083.0</td>
      <td>6121.0</td>
      <td>1559.80</td>
      <td>7627510.0</td>
    </tr>
    <tr>
      <th>Tienda_2</th>
      <td>22323688.0</td>
      <td>13870582.0</td>
      <td>5936.0</td>
      <td>1253.60</td>
      <td>8453106.0</td>
    </tr>
    <tr>
      <th>Tienda_3</th>
      <td>18298368.0</td>
      <td>11252158.0</td>
      <td>5814.0</td>
      <td>1427.98</td>
      <td>7046210.0</td>
    </tr>
    <tr>
      <th>Tienda_4</th>
      <td>15622881.0</td>
      <td>9349067.0</td>
      <td>4562.0</td>
      <td>1278.23</td>
      <td>6273814.0</td>
    </tr>
    <tr>
      <th>Tienda_5</th>
      <td>20643260.0</td>
      <td>12738316.0</td>
      <td>5833.0</td>
      <td>1385.57</td>
      <td>7904944.0</td>
    </tr>
    <tr>
      <th>Tienda_6</th>
      <td>16340444.0</td>
      <td>10599786.0</td>
      <td>5167.0</td>
      <td>1388.33</td>
      <td>5740658.0</td>
    </tr>
    <tr>
      <th>Tienda_7</th>
      <td>18950044.0</td>
      <td>12186334.0</td>
      <td>5703.0</td>
      <td>1454.27</td>
      <td>6763710.0</td>
    </tr>
    <tr>
      <th>Tienda_8</th>
      <td>18519051.0</td>
      <td>10684321.0</td>
      <td>5314.0</td>
      <td>1583.25</td>
      <td>7834730.0</td>
    </tr>
    <tr>
      <th>Tienda_9</th>
      <td>15313594.0</td>
      <td>9500283.0</td>
      <td>4508.0</td>
      <td>1276.00</td>
      <td>5813311.0</td>
    </tr>
    <tr>
      <th>Tienda_10</th>
      <td>18636140.0</td>
      <td>11217616.0</td>
      <td>5280.0</td>
      <td>1245.88</td>
      <td>7418524.0</td>
    </tr>
    <tr>
      <th>Tienda_11</th>
      <td>21476297.0</td>
      <td>14077842.0</td>
      <td>6939.0</td>
      <td>1720.78</td>
      <td>7398455.0</td>
    </tr>
    <tr>
      <th>Tienda_12</th>
      <td>19606320.0</td>
      <td>12118523.0</td>
      <td>5420.0</td>
      <td>1289.16</td>
      <td>7487797.0</td>
    </tr>
  </tbody>
</table>


```python
print("Tiendas ordenadas por utilidad aproximada:")
display(reporte.sort_values("utilidad_aproximada", ascending=False).round(2))
```

**Salida:**


```
Tiendas ordenadas por utilidad aproximada:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ingreso_total</th>
      <th>costo_total</th>
      <th>tiempo_total_preparacion</th>
      <th>emision_total_logistica</th>
      <th>utilidad_aproximada</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda_2</th>
      <td>22323688.0</td>
      <td>13870582.0</td>
      <td>5936.0</td>
      <td>1253.60</td>
      <td>8453106.0</td>
    </tr>
    <tr>
      <th>Tienda_5</th>
      <td>20643260.0</td>
      <td>12738316.0</td>
      <td>5833.0</td>
      <td>1385.57</td>
      <td>7904944.0</td>
    </tr>
    <tr>
      <th>Tienda_8</th>
      <td>18519051.0</td>
      <td>10684321.0</td>
      <td>5314.0</td>
      <td>1583.25</td>
      <td>7834730.0</td>
    </tr>
    <tr>
      <th>Tienda_1</th>
      <td>20022593.0</td>
      <td>12395083.0</td>
      <td>6121.0</td>
      <td>1559.80</td>
      <td>7627510.0</td>
    </tr>
    <tr>
      <th>Tienda_12</th>
      <td>19606320.0</td>
      <td>12118523.0</td>
      <td>5420.0</td>
      <td>1289.16</td>
      <td>7487797.0</td>
    </tr>
    <tr>
      <th>Tienda_10</th>
      <td>18636140.0</td>
      <td>11217616.0</td>
      <td>5280.0</td>
      <td>1245.88</td>
      <td>7418524.0</td>
    </tr>
    <tr>
      <th>Tienda_11</th>
      <td>21476297.0</td>
      <td>14077842.0</td>
      <td>6939.0</td>
      <td>1720.78</td>
      <td>7398455.0</td>
    </tr>
    <tr>
      <th>Tienda_3</th>
      <td>18298368.0</td>
      <td>11252158.0</td>
      <td>5814.0</td>
      <td>1427.98</td>
      <td>7046210.0</td>
    </tr>
    <tr>
      <th>Tienda_7</th>
      <td>18950044.0</td>
      <td>12186334.0</td>
      <td>5703.0</td>
      <td>1454.27</td>
      <td>6763710.0</td>
    </tr>
    <tr>
      <th>Tienda_4</th>
      <td>15622881.0</td>
      <td>9349067.0</td>
      <td>4562.0</td>
      <td>1278.23</td>
      <td>6273814.0</td>
    </tr>
    <tr>
      <th>Tienda_9</th>
      <td>15313594.0</td>
      <td>9500283.0</td>
      <td>4508.0</td>
      <td>1276.00</td>
      <td>5813311.0</td>
    </tr>
    <tr>
      <th>Tienda_6</th>
      <td>16340444.0</td>
      <td>10599786.0</td>
      <td>5167.0</td>
      <td>1388.33</td>
      <td>5740658.0</td>
    </tr>
  </tbody>
</table>


```python
print("Tiendas con mayor tiempo total de preparación:")
display(reporte.sort_values("tiempo_total_preparacion", ascending=False).round(2))
```

**Salida:**


```
Tiendas con mayor tiempo total de preparación:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ingreso_total</th>
      <th>costo_total</th>
      <th>tiempo_total_preparacion</th>
      <th>emision_total_logistica</th>
      <th>utilidad_aproximada</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda_11</th>
      <td>21476297.0</td>
      <td>14077842.0</td>
      <td>6939.0</td>
      <td>1720.78</td>
      <td>7398455.0</td>
    </tr>
    <tr>
      <th>Tienda_1</th>
      <td>20022593.0</td>
      <td>12395083.0</td>
      <td>6121.0</td>
      <td>1559.80</td>
      <td>7627510.0</td>
    </tr>
    <tr>
      <th>Tienda_2</th>
      <td>22323688.0</td>
      <td>13870582.0</td>
      <td>5936.0</td>
      <td>1253.60</td>
      <td>8453106.0</td>
    </tr>
    <tr>
      <th>Tienda_5</th>
      <td>20643260.0</td>
      <td>12738316.0</td>
      <td>5833.0</td>
      <td>1385.57</td>
      <td>7904944.0</td>
    </tr>
    <tr>
      <th>Tienda_3</th>
      <td>18298368.0</td>
      <td>11252158.0</td>
      <td>5814.0</td>
      <td>1427.98</td>
      <td>7046210.0</td>
    </tr>
    <tr>
      <th>Tienda_7</th>
      <td>18950044.0</td>
      <td>12186334.0</td>
      <td>5703.0</td>
      <td>1454.27</td>
      <td>6763710.0</td>
    </tr>
    <tr>
      <th>Tienda_12</th>
      <td>19606320.0</td>
      <td>12118523.0</td>
      <td>5420.0</td>
      <td>1289.16</td>
      <td>7487797.0</td>
    </tr>
    <tr>
      <th>Tienda_8</th>
      <td>18519051.0</td>
      <td>10684321.0</td>
      <td>5314.0</td>
      <td>1583.25</td>
      <td>7834730.0</td>
    </tr>
    <tr>
      <th>Tienda_10</th>
      <td>18636140.0</td>
      <td>11217616.0</td>
      <td>5280.0</td>
      <td>1245.88</td>
      <td>7418524.0</td>
    </tr>
    <tr>
      <th>Tienda_6</th>
      <td>16340444.0</td>
      <td>10599786.0</td>
      <td>5167.0</td>
      <td>1388.33</td>
      <td>5740658.0</td>
    </tr>
    <tr>
      <th>Tienda_4</th>
      <td>15622881.0</td>
      <td>9349067.0</td>
      <td>4562.0</td>
      <td>1278.23</td>
      <td>6273814.0</td>
    </tr>
    <tr>
      <th>Tienda_9</th>
      <td>15313594.0</td>
      <td>9500283.0</td>
      <td>4508.0</td>
      <td>1276.00</td>
      <td>5813311.0</td>
    </tr>
  </tbody>
</table>


```python
print("Tiendas con mayor emisión logística total:")
display(reporte.sort_values("emision_total_logistica", ascending=False).round(2))
```

**Salida:**


```
Tiendas con mayor emisión logística total:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ingreso_total</th>
      <th>costo_total</th>
      <th>tiempo_total_preparacion</th>
      <th>emision_total_logistica</th>
      <th>utilidad_aproximada</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda_11</th>
      <td>21476297.0</td>
      <td>14077842.0</td>
      <td>6939.0</td>
      <td>1720.78</td>
      <td>7398455.0</td>
    </tr>
    <tr>
      <th>Tienda_8</th>
      <td>18519051.0</td>
      <td>10684321.0</td>
      <td>5314.0</td>
      <td>1583.25</td>
      <td>7834730.0</td>
    </tr>
    <tr>
      <th>Tienda_1</th>
      <td>20022593.0</td>
      <td>12395083.0</td>
      <td>6121.0</td>
      <td>1559.80</td>
      <td>7627510.0</td>
    </tr>
    <tr>
      <th>Tienda_7</th>
      <td>18950044.0</td>
      <td>12186334.0</td>
      <td>5703.0</td>
      <td>1454.27</td>
      <td>6763710.0</td>
    </tr>
    <tr>
      <th>Tienda_3</th>
      <td>18298368.0</td>
      <td>11252158.0</td>
      <td>5814.0</td>
      <td>1427.98</td>
      <td>7046210.0</td>
    </tr>
    <tr>
      <th>Tienda_6</th>
      <td>16340444.0</td>
      <td>10599786.0</td>
      <td>5167.0</td>
      <td>1388.33</td>
      <td>5740658.0</td>
    </tr>
    <tr>
      <th>Tienda_5</th>
      <td>20643260.0</td>
      <td>12738316.0</td>
      <td>5833.0</td>
      <td>1385.57</td>
      <td>7904944.0</td>
    </tr>
    <tr>
      <th>Tienda_12</th>
      <td>19606320.0</td>
      <td>12118523.0</td>
      <td>5420.0</td>
      <td>1289.16</td>
      <td>7487797.0</td>
    </tr>
    <tr>
      <th>Tienda_4</th>
      <td>15622881.0</td>
      <td>9349067.0</td>
      <td>4562.0</td>
      <td>1278.23</td>
      <td>6273814.0</td>
    </tr>
    <tr>
      <th>Tienda_9</th>
      <td>15313594.0</td>
      <td>9500283.0</td>
      <td>4508.0</td>
      <td>1276.00</td>
      <td>5813311.0</td>
    </tr>
    <tr>
      <th>Tienda_2</th>
      <td>22323688.0</td>
      <td>13870582.0</td>
      <td>5936.0</td>
      <td>1253.60</td>
      <td>8453106.0</td>
    </tr>
    <tr>
      <th>Tienda_10</th>
      <td>18636140.0</td>
      <td>11217616.0</td>
      <td>5280.0</td>
      <td>1245.88</td>
      <td>7418524.0</td>
    </tr>
  </tbody>
</table>


La Tienda 2 podría priorizarse para una estrategia de expansión comercial, porque presenta el mayor ingreso total, con \$22.323.688 pesos, y la mayor utilidad aproximada, con \$8.453.106 pesos.

La Tienda 11 debería revisarse desde el punto de vista operativo y logístico, porque presenta el mayor tiempo total de preparación, con 6.939 minutos, y la mayor emisión logística, con 1.720,78 kg de CO₂ equivalente. Además, concentra el mayor costo total.

Por lo tanto, la tienda con mejor resultado comercial no es necesariamente la que presenta la mayor carga operativa.


# **Actividad 16 - Afinidad entre usuarios y perfiles de recomendación 💻/🐍**


Una plataforma de streaming registra valoraciones de usuarios sobre distintas categorías de contenido. Las valoraciones se expresan en una escala de 1 a 5 y se encuentran disponibles en el archivo:

**<a href="https://drive.google.com/uc?export=download&id=1oWf0bII_JRRn8i4xMjS0ByRaIUTMjvej">set de datos</a>**

En esta tabla:

* cada fila representa un usuario;
* cada columna representa una categoría de contenido;
* cada entrada corresponde a la valoración asignada por un usuario a una categoría.

La plataforma también dispone del archivo:

**<a href="https://drive.google.com/uc?export=download&id=1gyWfyjb99ZmYNrtGuAIrI5u7dKt6IgJ7">set de datos</a>**

En esta tabla:

* cada fila representa una categoría de contenido;
* cada columna representa un perfil de recomendación;
* cada entrada corresponde a la ponderación asignada a una categoría dentro del perfil.

Las ponderaciones de cada perfil son positivas y suman 1. Por lo tanto, los puntajes obtenidos pueden interpretarse en la misma escala de 1 a 5 utilizada en las valoraciones.

El equipo desea utilizar ambos archivos para determinar qué perfil representa mejor las preferencias de cada usuario, para esto realice las siguientes acciones:


a) Cargue ambos archivos, organice los datos para que las categorías coincidan en cantidad y orden, y convierta las tablas en las matrices numéricas $R$ y $Q$.


```python
import pandas as pd
import numpy as np

# Cargar archivos
valoraciones = pd.read_csv("L2_A16_valoraciones_usuarios.csv", index_col=0)
perfiles = pd.read_csv("L2_A16_perfiles_recomendacion.csv", index_col=0)

# Revisar las tablas
print("Tabla de valoraciones de usuarios:")
display(valoraciones.head())

print("Tabla de perfiles de recomendación:")
display(perfiles.head())
```

**Salida:**


```
Tabla de valoraciones de usuarios:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>accion</th>
      <th>comedia</th>
      <th>documental</th>
      <th>ciencia_ficcion</th>
      <th>drama</th>
      <th>terror</th>
      <th>animacion</th>
      <th>romance</th>
      <th>aventura</th>
      <th>policial</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Usuario_1</th>
      <td>3</td>
      <td>5</td>
      <td>3</td>
      <td>2</td>
      <td>4</td>
      <td>3</td>
      <td>4</td>
      <td>2</td>
      <td>2</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Usuario_2</th>
      <td>2</td>
      <td>2</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>4</td>
      <td>5</td>
      <td>1</td>
      <td>1</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Usuario_3</th>
      <td>2</td>
      <td>4</td>
      <td>3</td>
      <td>5</td>
      <td>3</td>
      <td>5</td>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>4</td>
    </tr>
    <tr>
      <th>Usuario_4</th>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>2</td>
      <td>4</td>
      <td>3</td>
      <td>2</td>
      <td>5</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>Usuario_5</th>
      <td>3</td>
      <td>1</td>
      <td>4</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>5</td>
      <td>4</td>
      <td>4</td>
    </tr>
  </tbody>
</table>


```
Tabla de perfiles de recomendación:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>perfil_accion_aventura</th>
      <th>perfil_documental_cultural</th>
      <th>perfil_familiar_animacion</th>
      <th>perfil_suspenso_policial</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>accion</th>
      <td>0.25</td>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.10</td>
    </tr>
    <tr>
      <th>comedia</th>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.15</td>
      <td>0.05</td>
    </tr>
    <tr>
      <th>documental</th>
      <td>0.05</td>
      <td>0.35</td>
      <td>0.10</td>
      <td>0.05</td>
    </tr>
    <tr>
      <th>ciencia_ficcion</th>
      <td>0.20</td>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.05</td>
    </tr>
    <tr>
      <th>drama</th>
      <td>0.05</td>
      <td>0.15</td>
      <td>0.10</td>
      <td>0.10</td>
    </tr>
  </tbody>
</table>


```python
# Categorías según el orden de la tabla de valoraciones
categorias = valoraciones.columns

# Reordenar las filas de perfiles según el orden de las columnas de valoraciones
perfiles_ordenados = perfiles.loc[categorias]

print("Perfiles ordenados según las categorías de valoración:")
display(perfiles_ordenados)
```

**Salida:**


```
Perfiles ordenados según las categorías de valoración:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>perfil_accion_aventura</th>
      <th>perfil_documental_cultural</th>
      <th>perfil_familiar_animacion</th>
      <th>perfil_suspenso_policial</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>accion</th>
      <td>0.25</td>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.10</td>
    </tr>
    <tr>
      <th>comedia</th>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.15</td>
      <td>0.05</td>
    </tr>
    <tr>
      <th>documental</th>
      <td>0.05</td>
      <td>0.35</td>
      <td>0.10</td>
      <td>0.05</td>
    </tr>
    <tr>
      <th>ciencia_ficcion</th>
      <td>0.20</td>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.05</td>
    </tr>
    <tr>
      <th>drama</th>
      <td>0.05</td>
      <td>0.15</td>
      <td>0.10</td>
      <td>0.10</td>
    </tr>
    <tr>
      <th>terror</th>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.20</td>
    </tr>
    <tr>
      <th>animacion</th>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.30</td>
      <td>0.05</td>
    </tr>
    <tr>
      <th>romance</th>
      <td>0.05</td>
      <td>0.10</td>
      <td>0.15</td>
      <td>0.05</td>
    </tr>
    <tr>
      <th>aventura</th>
      <td>0.20</td>
      <td>0.10</td>
      <td>0.05</td>
      <td>0.10</td>
    </tr>
    <tr>
      <th>policial</th>
      <td>0.05</td>
      <td>0.05</td>
      <td>0.00</td>
      <td>0.25</td>
    </tr>
  </tbody>
</table>


```python
# Convertir a matrices numéricas
R = valoraciones.to_numpy(dtype=float)
Q = perfiles_ordenados.to_numpy(dtype=float)
```


b) Verifique que el producto $R \cdot Q$ esté definido e indique la dimensión esperada de la matriz resultante.


```python
print("Dimensión de R:", R.shape)
print("Dimensión de Q:", Q.shape)

if R.shape[1] == Q.shape[0]:
    print("El producto R · Q está definido.")
    print("Dimensión esperada del resultado:", (R.shape[0], Q.shape[1]))
else:
    print("El producto R · Q no está definido.")
```

**Salida:**


```
Dimensión de R: (20, 10)
Dimensión de Q: (10, 4)
El producto R · Q está definido.
Dimensión esperada del resultado: (20, 4)
```


c) Calcule la matriz de afinidades $A = R \cdot Q$ y determine para cada usuario el perfil con el que presenta mayor afinidad.


```python
# Producto matricial
A = R @ Q

# Convertir resultado a DataFrame para interpretarlo mejor
A_df = pd.DataFrame(
    A,
    index=valoraciones.index,
    columns=perfiles_ordenados.columns
)

print("Matriz de afinidades A = R · Q:")
display(A_df.round(2))
```

**Salida:**


```
Matriz de afinidades A = R · Q:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>perfil_accion_aventura</th>
      <th>perfil_documental_cultural</th>
      <th>perfil_familiar_animacion</th>
      <th>perfil_suspenso_policial</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Usuario_1</th>
      <td>2.65</td>
      <td>2.95</td>
      <td>3.45</td>
      <td>2.55</td>
    </tr>
    <tr>
      <th>Usuario_2</th>
      <td>1.90</td>
      <td>1.80</td>
      <td>2.65</td>
      <td>3.05</td>
    </tr>
    <tr>
      <th>Usuario_3</th>
      <td>2.95</td>
      <td>2.85</td>
      <td>2.35</td>
      <td>3.40</td>
    </tr>
    <tr>
      <th>Usuario_4</th>
      <td>3.25</td>
      <td>4.00</td>
      <td>3.55</td>
      <td>3.55</td>
    </tr>
    <tr>
      <th>Usuario_5</th>
      <td>3.30</td>
      <td>3.60</td>
      <td>3.15</td>
      <td>3.40</td>
    </tr>
    <tr>
      <th>Usuario_6</th>
      <td>3.85</td>
      <td>3.40</td>
      <td>3.60</td>
      <td>3.65</td>
    </tr>
    <tr>
      <th>Usuario_7</th>
      <td>2.30</td>
      <td>3.35</td>
      <td>2.85</td>
      <td>3.30</td>
    </tr>
    <tr>
      <th>Usuario_8</th>
      <td>3.15</td>
      <td>2.50</td>
      <td>2.90</td>
      <td>2.75</td>
    </tr>
    <tr>
      <th>Usuario_9</th>
      <td>3.10</td>
      <td>3.40</td>
      <td>2.55</td>
      <td>3.00</td>
    </tr>
    <tr>
      <th>Usuario_10</th>
      <td>3.15</td>
      <td>2.70</td>
      <td>3.40</td>
      <td>3.00</td>
    </tr>
    <tr>
      <th>Usuario_11</th>
      <td>3.35</td>
      <td>2.65</td>
      <td>2.40</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>Usuario_12</th>
      <td>3.80</td>
      <td>4.55</td>
      <td>3.55</td>
      <td>4.25</td>
    </tr>
    <tr>
      <th>Usuario_13</th>
      <td>2.90</td>
      <td>1.85</td>
      <td>2.85</td>
      <td>1.95</td>
    </tr>
    <tr>
      <th>Usuario_14</th>
      <td>3.05</td>
      <td>3.30</td>
      <td>3.00</td>
      <td>3.35</td>
    </tr>
    <tr>
      <th>Usuario_15</th>
      <td>2.40</td>
      <td>2.10</td>
      <td>2.00</td>
      <td>2.75</td>
    </tr>
    <tr>
      <th>Usuario_16</th>
      <td>3.35</td>
      <td>2.75</td>
      <td>2.60</td>
      <td>3.45</td>
    </tr>
    <tr>
      <th>Usuario_17</th>
      <td>3.40</td>
      <td>2.55</td>
      <td>3.25</td>
      <td>3.10</td>
    </tr>
    <tr>
      <th>Usuario_18</th>
      <td>3.85</td>
      <td>3.60</td>
      <td>2.40</td>
      <td>3.95</td>
    </tr>
    <tr>
      <th>Usuario_19</th>
      <td>2.60</td>
      <td>3.60</td>
      <td>3.20</td>
      <td>3.20</td>
    </tr>
    <tr>
      <th>Usuario_20</th>
      <td>3.05</td>
      <td>3.40</td>
      <td>3.35</td>
      <td>2.85</td>
    </tr>
  </tbody>
</table>


```python
# Perfil de mayor afinidad por usuario
perfil_mayor_afinidad = A_df.idxmax(axis=1)

# Puntaje máximo de afinidad por usuario
puntaje_mayor_afinidad = A_df.max(axis=1)

# Resumen
resumen_afinidad = pd.DataFrame({
    "perfil_mayor_afinidad": perfil_mayor_afinidad,
    "puntaje": puntaje_mayor_afinidad
})

print("Perfil de mayor afinidad por usuario:")
display(resumen_afinidad.round(2))
```

**Salida:**


```
Perfil de mayor afinidad por usuario:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>perfil_mayor_afinidad</th>
      <th>puntaje</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Usuario_1</th>
      <td>perfil_familiar_animacion</td>
      <td>3.45</td>
    </tr>
    <tr>
      <th>Usuario_2</th>
      <td>perfil_suspenso_policial</td>
      <td>3.05</td>
    </tr>
    <tr>
      <th>Usuario_3</th>
      <td>perfil_suspenso_policial</td>
      <td>3.40</td>
    </tr>
    <tr>
      <th>Usuario_4</th>
      <td>perfil_documental_cultural</td>
      <td>4.00</td>
    </tr>
    <tr>
      <th>Usuario_5</th>
      <td>perfil_documental_cultural</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>Usuario_6</th>
      <td>perfil_accion_aventura</td>
      <td>3.85</td>
    </tr>
    <tr>
      <th>Usuario_7</th>
      <td>perfil_documental_cultural</td>
      <td>3.35</td>
    </tr>
    <tr>
      <th>Usuario_8</th>
      <td>perfil_accion_aventura</td>
      <td>3.15</td>
    </tr>
    <tr>
      <th>Usuario_9</th>
      <td>perfil_documental_cultural</td>
      <td>3.40</td>
    </tr>
    <tr>
      <th>Usuario_10</th>
      <td>perfil_familiar_animacion</td>
      <td>3.40</td>
    </tr>
    <tr>
      <th>Usuario_11</th>
      <td>perfil_suspenso_policial</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>Usuario_12</th>
      <td>perfil_documental_cultural</td>
      <td>4.55</td>
    </tr>
    <tr>
      <th>Usuario_13</th>
      <td>perfil_accion_aventura</td>
      <td>2.90</td>
    </tr>
    <tr>
      <th>Usuario_14</th>
      <td>perfil_suspenso_policial</td>
      <td>3.35</td>
    </tr>
    <tr>
      <th>Usuario_15</th>
      <td>perfil_suspenso_policial</td>
      <td>2.75</td>
    </tr>
    <tr>
      <th>Usuario_16</th>
      <td>perfil_suspenso_policial</td>
      <td>3.45</td>
    </tr>
    <tr>
      <th>Usuario_17</th>
      <td>perfil_accion_aventura</td>
      <td>3.40</td>
    </tr>
    <tr>
      <th>Usuario_18</th>
      <td>perfil_suspenso_policial</td>
      <td>3.95</td>
    </tr>
    <tr>
      <th>Usuario_19</th>
      <td>perfil_documental_cultural</td>
      <td>3.60</td>
    </tr>
    <tr>
      <th>Usuario_20</th>
      <td>perfil_documental_cultural</td>
      <td>3.40</td>
    </tr>
  </tbody>
</table>


d) El equipo desea comparar específicamente la afinidad de los usuarios con los perfiles `perfil_accion_aventura` y `perfil_documental_cultural`. Para ello, considere el vector:

$$c = \begin{pmatrix}
1\\
-1\\
0\\
0
\end{pmatrix}$$

Calcule:

$$d = A \cdot c$$

Explique qué significa que una componente del vector $d$ sea positiva, negativa o igual a cero. Luego, identifique el usuario con mayor inclinación relativa hacia acción y aventura y el usuario con mayor inclinación relativa hacia documental y cultural.


```python
# Vector de comparación
# Compara perfil_accion_aventura - perfil_documental_cultural
c = np.array([
    [1],
    [-1],
    [0],
    [0]
])

# Calcular diferencia de afinidad
d = A @ c

# Crear DataFrame con el resultado
d_df = pd.DataFrame(
    d,
    index=valoraciones.index,
    columns=["diferencia_accion_vs_documental"]
)

print("Diferencia entre perfil acción-aventura y documental-cultural:")
display(d_df.round(2))
```

**Salida:**


```
Diferencia entre perfil acción-aventura y documental-cultural:
```


<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>diferencia_accion_vs_documental</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Usuario_1</th>
      <td>-0.30</td>
    </tr>
    <tr>
      <th>Usuario_2</th>
      <td>0.10</td>
    </tr>
    <tr>
      <th>Usuario_3</th>
      <td>0.10</td>
    </tr>
    <tr>
      <th>Usuario_4</th>
      <td>-0.75</td>
    </tr>
    <tr>
      <th>Usuario_5</th>
      <td>-0.30</td>
    </tr>
    <tr>
      <th>Usuario_6</th>
      <td>0.45</td>
    </tr>
    <tr>
      <th>Usuario_7</th>
      <td>-1.05</td>
    </tr>
    <tr>
      <th>Usuario_8</th>
      <td>0.65</td>
    </tr>
    <tr>
      <th>Usuario_9</th>
      <td>-0.30</td>
    </tr>
    <tr>
      <th>Usuario_10</th>
      <td>0.45</td>
    </tr>
    <tr>
      <th>Usuario_11</th>
      <td>0.70</td>
    </tr>
    <tr>
      <th>Usuario_12</th>
      <td>-0.75</td>
    </tr>
    <tr>
      <th>Usuario_13</th>
      <td>1.05</td>
    </tr>
    <tr>
      <th>Usuario_14</th>
      <td>-0.25</td>
    </tr>
    <tr>
      <th>Usuario_15</th>
      <td>0.30</td>
    </tr>
    <tr>
      <th>Usuario_16</th>
      <td>0.60</td>
    </tr>
    <tr>
      <th>Usuario_17</th>
      <td>0.85</td>
    </tr>
    <tr>
      <th>Usuario_18</th>
      <td>0.25</td>
    </tr>
    <tr>
      <th>Usuario_19</th>
      <td>-1.00</td>
    </tr>
    <tr>
      <th>Usuario_20</th>
      <td>-0.35</td>
    </tr>
  </tbody>
</table>


```python
# Usuario con mayor inclinación relativa hacia acción-aventura
usuario_mayor_accion = d_df["diferencia_accion_vs_documental"].idxmax()
valor_mayor_accion = d_df["diferencia_accion_vs_documental"].max()

# Usuario con mayor inclinación relativa hacia documental-cultural
usuario_mayor_documental = d_df["diferencia_accion_vs_documental"].idxmin()
valor_mayor_documental = d_df["diferencia_accion_vs_documental"].min()

print("Usuario con mayor inclinación relativa hacia acción-aventura:")
print(usuario_mayor_accion, "con diferencia", round(valor_mayor_accion, 2))

print("\nUsuario con mayor inclinación relativa hacia documental-cultural:")
print(usuario_mayor_documental, "con diferencia", round(valor_mayor_documental, 2))
```

**Salida:**


```
Usuario con mayor inclinación relativa hacia acción-aventura:
Usuario_13 con diferencia 1.05

Usuario con mayor inclinación relativa hacia documental-cultural:
Usuario_7 con diferencia -1.05
```


El Usuario_13 presenta la mayor inclinación relativa hacia el perfil `perfil_accion_aventura`, porque su diferencia entre acción-aventura y documental-cultural es la más alta y positiva.

El Usuario_7 presenta la mayor inclinación relativa hacia el perfil `perfil_documental_cultural`, porque su diferencia es la más baja y negativa.


#💡Cierre y reflexión

Las matrices permiten organizar múltiples registros y variables en una misma estructura matemática. En este laboratorio, las filas y columnas representaron elementos como usuarios, productos, tiendas, categorías e indicadores, lo que permitió analizar conjuntos completos de datos y no solo registros aislados.

Las operaciones matriciales permitieron comparar y transformar información. En particular, los productos matriz-vector y matriz-matriz permitieron calcular totales, puntajes ponderados, indicadores y afinidades para varios registros de manera simultánea. Para que estos productos tengan sentido, no solo fue necesario verificar la compatibilidad de las dimensiones, sino también que las variables relacionadas coincidieran en significado y orden.

Esta forma de representar relaciones será fundamental para avanzar hacia situaciones en las que algunas cantidades sean desconocidas. Más adelante, las matrices permitirán organizar condiciones simultáneas y analizar si existen valores que las satisfagan, ampliando su uso desde la transformación de datos hacia la resolución de problemas mediante sistemas lineales.


#🏅 En este laboratorio aprendiste a:

*	Representar e interpretar información tabular mediante matrices, identificando sus filas, columnas, entradas y dimensiones.
*	Construir y preparar matrices a partir de datos ingresados directamente o almacenados en archivos externos.
*	Seleccionar filas, columnas y submatrices, y calcular e interpretar la transpuesta.
*	Realizar operaciones básicas con matrices: suma, resta y multiplicación por escalar.
*	Obtener e interpretar totales y promedios por filas o columnas.
*	Verificar la compatibilidad de dimensiones y calcular productos matriz-vector y matriz-matriz.
*	Interpretar los productos matriciales como combinaciones ponderadas y transformaciones de información.
*	Utilizar Pandas y NumPy para preparar, explorar y operar matrices en problemas aplicados.
