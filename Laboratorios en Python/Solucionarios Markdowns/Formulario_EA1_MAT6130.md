# Formulario_EA1_MAT6130

> Copia en Markdown generada desde `Formulario_EA1_MAT6130.ipynb` (se conservan todas las salidas de ejecucion).

# ÁLGEBRA LINEAL (MAT6130)


## EA1: Formulario


#### (1) IMPORTACIÓN DE LIBRERÍAS


```python
import numpy as np
import pandas as pd
```


#### (2) VECTORES: REPRESENTACIÓN Y OPERACIONES


(2.1) Representación de un vector


Un vector de $n$ componentes puede representarse como:

$$\mathbf{v}=(v_1,v_2,\ldots,v_n)$$

o como vector columna:

$$\mathbf{v}=
\begin{pmatrix}
v_1\\
v_2\\
\vdots\\
v_n
\end{pmatrix}$$


En Python:


```python
v = np.array([VALOR_1, VALOR_2, VALOR_3])
```


(2.2) Operaciones componente a componente


Para vectores de igual dimensión:

$$\mathbf{u}+\mathbf{v}
=
(u_1+v_1,\ldots,u_n+v_n)$$

$$\mathbf{u}-\mathbf{v}
=
(u_1-v_1,\ldots,u_n-v_n)$$

$$k\mathbf{u}
=
(ku_1,\ldots,ku_n)$$


En Python:


```python
suma_vectores = v1 + v2
resta_vectores = v1 - v2
producto_escalar = ESCALAR * v
```


(2.3) Índices de máximo y mínimo


```python
# Retorna la posición del valor máximo
indice_mayor = np.argmax(v)

# Retorna la posición del valor mínimo
indice_menor = np.argmin(v)
```


#### (3) NORMA Y DISTANCIA EUCLIDIANA


(3.1) Norma de un vector


$$\|\mathbf{v}\|
=
\sqrt{v_1^2+v_2^2+\cdots+v_n^2}$$


En Python:


```python
norma_v = np.linalg.norm(v)
```


(3.2) Distancia euclidiana entre dos vectores


$$d(\mathbf{u},\mathbf{v})
=
\|\mathbf{u}-\mathbf{v}\|
=
\sqrt{\sum_{i=1}^{n}(u_i-v_i)^2}$$


En Python:


```python
distancia = np.linalg.norm(v1 - v2)
```


#### (4) MATRICES: REPRESENTACIÓN Y ATRIBUTOS


(4.1) Representación de una matriz


```python
M = np.array([[VALOR, VALOR, VALOR],
              [VALOR, VALOR, VALOR]])
```


(4.2) Dimensión y transpuesta


```python
# Retorn dimensión
dimension = M.shape

# Intercambia filas por columnas
M_transpuesta = M.T
```


#### (5) SELECCIÓN EN MATRICES (SLICING)


(5.1) Extraer filas y columnas


```python
fila = M[INDICE_FILA]

# ':' indica todas las filas
columna = M[:, INDICE_COLUMNA]
```


(5.2) Extraer subconjunto


```python
# El límite superior no se incluye
subconjunto = M[INICIO_FILA:FIN_FILA, INICIO_COLUMNA:FIN_COLUMNA]
```


#### (6) OPERACIONES CON MATRICES


Para matrices de igual dimensión:

$$A+B=(a_{ij}+b_{ij})$$

$$A-B=(a_{ij}-b_{ij})$$

$$kA=(ka_{ij})$$


En Python:


(6.1) Suma y promedio por eje (axis)


```python
# Entrega indicador total por cada columna
suma_por_columnas = np.sum(M, axis=0)

# Entrega indicador total por cada fila
suma_por_filas = np.sum(M, axis=1)

promedio_por_columnas = M.mean(axis=0)
promedio_por_filas = M.mean(axis=1)
```


(6.2) Producto matriz-vector y matriz-matriz


```python
# Para que el producto esté definido, las dimensiones interiores deben coincidir:
resultado_producto = M @ MATRIZ_O_VECTOR
```


#### (7) INTEGRACIÓN PANDAS Y NUMPY


(7.1) Carga de datos con etiquetas


```python
# index_col=0 usa la 1° columna como índice de filas
df = pd.read_csv("NOMBRE_DEL_ARCHIVO.csv", index_col=0)
```


(7.2) Extraer matriz numérica cruda para operar


```python
# Alinear el orden de filas de df_2 con el orden de columnas de df_1 antes del producto matricial
df_2 = df_2.loc[df_1.columns]

# Extraer matrices despojadas de etiquetas
M1 = df_1.to_numpy(dtype=float)
M2 = df_2.to_numpy(dtype=float)
```


(7.3) Reconstruir DataFrame a partir de matriz NumPy


```python
df_resultado = pd.DataFrame(MATRIZ_RESULTADO,
                            index=df_ORIGINAL.index,                   # Recupera etiquetas de filas
                            columns=["NOMBRE_COL_1", "NOMBRE_COL_2"])  # Asigna nuevas etiquetas de columnas
```


(7.4) Búsqueda de etiquetas y ordenamiento de tablas


```python
# Retorna el nombre de la fila con el mayor valor en esa columna
etiqueta_maximo = df_resultado["NOMBRE_COLUMNA"].idxmax()


df_ordenado = df_resultado.sort_values(by="NOMBRE_COLUMNA",
                                       ascending=False)       # False para ordenar de mayor a menor
```
