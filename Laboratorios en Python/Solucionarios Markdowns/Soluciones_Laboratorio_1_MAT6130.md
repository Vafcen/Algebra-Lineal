# Soluciones_Laboratorio_1_MAT6130

> Copia en Markdown generada desde `Soluciones_Laboratorio_1_MAT6130.ipynb` (se conservan todas las salidas de ejecucion).

<img src="https://i.ibb.co/93sNcdhp/Logo-pmat-color.png" align="right" width="250">

<br>

# **Vectores como representación de información**


## **Introducción contextual**

En ciencia de datos e inteligencia artificial, distintos objetos y situaciones pueden representarse mediante vectores que organizan varias características numéricas. En este laboratorio utilizarás esta representación para interpretar registros, realizar operaciones y comparar datos mediante cálculo analítico y Python.


## Resultado de aprendizaje asociado

RA1: Representa información mediante vectores y matrices, realizando operaciones básicas e interpretando sus resultados en contextos de ciencia de datos e inteligencia artificial, con apoyo de Python.

## Indicadores de logro trabajados

IL1.1: Interpreta componentes de vectores contextualizados, considerando el significado y el orden de sus variables.

IL1.2: Opera vectores contextualizados mediante suma, resta y multiplicación por escalar, con apoyo de Python cuando corresponda, interpretando los resultados en contexto.

IL1.3: Determina magnitud y diferencia global entre registros vectoriales mediante norma y distancia euclidiana, con apoyo de Python cuando corresponda.


# Instrucciones

Este laboratorio contiene problemas que deben resolverse tanto de forma analítica como de forma computacional.

Los problemas marcados con 📝 se deben resolver con lápiz y papel en tu cuaderno, mientras que aquellos marcados con 💻/🐍 se deben resolver usando Python.


```python
# @title
%%html
<div style="border: 4px solid #006d77; border-radius: 0px; overflow: hidden; font-family: sans-serif; max-width: 800px; margin-bottom: 20px;">

  <div style="background-color: #000000; color: #ffc107; padding: 10px 15px; font-weight: bold; font-size: 16px; display: flex; align-items: center;">
    <span style="margin-right: 10px; font-size: 18px;">💡</span>
    <span>Leer y operar registros vectoriales</span>
  </div>

  <div style="background-color: #ffffff; padding: 20px; display: flex; align-items: center; justify-content: space-between;">

    <div style="color: #000000; flex: 1; padding-right: 30px; font-size: 14px; line-height: 1.5;">
      Antes de comenzar las primeras actividades, revisa este recurso para comprender cómo un vector organiza información,
      cómo interpretar el significado y el orden de sus componentes y cómo realizar operaciones entre registros manteniendo
      su sentido en contexto. <b>Escanea o haz clic en el código QR</b> para acceder al contenido.
    </div>

    <div style="flex-shrink: 0;">
      <a href="https://duoc.h5p.com/content/1292919584491779108" target="_blank">
        <img src="https://i.ibb.co/KpqPsmxR/L1-H5P1.png"
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
    <span>Leer y operar registros vectoriales</span>
  </div>

  <div style="background-color: #ffffff; padding: 20px; display: flex; align-items: center; justify-content: space-between;">

    <div style="color: #000000; flex: 1; padding-right: 30px; font-size: 14px; line-height: 1.5;">
      Antes de comenzar las primeras actividades, revisa este recurso para comprender cómo un vector organiza información,
      cómo interpretar el significado y el orden de sus componentes y cómo realizar operaciones entre registros manteniendo
      su sentido en contexto. <b>Escanea o haz clic en el código QR</b> para acceder al contenido.
    </div>

    <div style="flex-shrink: 0;">
      <a href="https://duoc.h5p.com/content/1292919584491779108" target="_blank">
        <img src="https://i.ibb.co/KpqPsmxR/L1-H5P1.png"
             alt="QR Code"
             style="width: 100px; height: 100px; border: none;">
      </a>
    </div>

  </div>

  <div style="background-color: #000000; color: #ffc107; padding: 8px 15px; font-weight: bold; font-size: 16px;">
    Presentación interactiva H5P
  </div>

</div>


# 📌 Consulta rápida: operaciones y medidas vectoriales

Para operar vectores, estos deben tener la misma dimensión y representar las variables en el mismo orden.

$$u + v=(u_1 + v_1, u_2 + v_2, ... ,u_n + v_n)$$
$$u - v=(u_1 - v_1, u_2 - v_2, ... ,u_n - v_n)$$
$$k \cdot u=(k\cdot u_1, k \cdot u_2, ... , k \cdot u_n)$$

**Recuerda**: en la resta, el signo indica la dirección del cambio y el valor absoluto permite comparar el tamaño de las diferencias.


### **Nota**: Vector fila y vector columna

Un mismo vector puede escribirse como vector fila:

$$u=(x_1, x_2, x_3, …,x_n)$$

o como vector columna:

$$u = \begin{pmatrix}
x_1 \\
x_2\\
...\\
x_n\\
\end{pmatrix}$$


# **Actividad 1 - Perfil de usuarios en una plataforma digital 📝**


Una plataforma de streaming está desarrollando un sistema de recomendación basado en el comportamiento de sus usuarios. Para analizar patrones de actividad, cada usuario se representa mediante un vector de características que resume distintas métricas registradas durante una semana.

Los perfiles de dos usuarios son:

$$u=(12,5,8,3)$$

$$v=(9,7,6,1)$$

donde cada componente representa, respectivamente:

* horas de uso semanales,
* películas visualizadas,
* búsquedas realizadas,
* reclamos enviados a soporte.

El equipo de análisis desea comparar ambos perfiles para identificar diferencias en sus comportamientos digitales.


a) ¿Qué representa la tercera componente de ambos vectores?


La tercera componente representa la cantidad de búsquedas realizadas en la plataforma.


b) Determine el vector diferencia: $u−v$


$$u-v=(12,5,8,3)-(9,7,6,1)$$

$$u-v=(12 - 9, 5 - 7, 8 - 6 , 3 -1)$$

$$=(3,-2,2,2)$$


c) ¿Qué variable presenta mayor diferencia entre ambos usuarios?


Se comparan las diferencias absolutas:

$\left |3 \right |= 3$, $\left |-2 \right |= 2$, $\left |2 \right |= 2$, $\left |2 \right |=2$

La mayor diferencia se presenta en la primera componente, correspondiente a las horas de uso semanales.


d) Interprete el significado del vector diferencia en el contexto del problema.


El vector diferencia: $(3,-2,2,2)$

indica que el usuario $u$ usa la plataforma 3 horas más que el usuario $v$, ve 2 películas menos, realiza 2 búsquedas más y envía 2 reclamos más. En términos generales, el usuario $u$ parece tener mayor interacción con la plataforma, aunque no necesariamente consume más películas.


# **Actividad 2 - Monitoreo de máquinas en una planta industrial 📝**


Una empresa manufacturera monitorea el funcionamiento de dos máquinas mediante sensores instalados en tiempo real. Cada máquina se representa mediante un vector que resume cuatro indicadores técnicos entregados por sensores, expresados en una escala común de monitoreo.
Los registros son:

$$m_1 = (80,\ 45,\ 120,\ 30)$$

$$m_2 = (75,\ 50,\ 100,\ 25)$$

donde las componentes representan, respectivamente, indicadores asociados a:

*	temperatura de operación,
*	nivel de vibración,
*	presión interna,
*	humedad del sistema.


El área de mantenimiento desea comparar ambas máquinas para identificar posibles diferencias operativas.


a) Determine el vector diferencia: $m_1 - m_2$


$$m_1 - m_2 = (80, 45, 120, 30) - (75, 50, 100, 25)$$

$$m_1 - m_2 = (80-75, 45-50, 120-100, 30-25)$$

$$m_1 - m_2 =(5, -5, 20, 5)$$


b) Determine la magnitud de la diferencia entre ambas máquinas para cada variable. ¿En cuál variable se observa la mayor discrepancia?


La diferencia se obtiene mediante el valor absoluto de las componentes del vector diferencia:

$\left |5 \right |= 5$, $\left |-5 \right |= 5$, $\left |20 \right |= 20$, $\left |5 \right |= 5$

La mayor discrepancia corresponde al indicador asociado a la presión interna, porque presenta la diferencia absoluta más alta.


c) Interprete el vector diferencia en el contexto del problema.


El vector diferencia indica que la máquina 1 presenta 5 unidades más en el indicador asociado a temperatura, 5 unidades menos en el indicador asociado a la vibración, 20 unidades más que el indicador asociado a la presión interna y 5 unidades más que el indicador asociado a la humedad que la máquina 2. La mayor diferencia absoluta se encuentra en el indicador asociado a la presión interna.


# **Actividad 3 - Evolución semanal de una tienda online 📝**


Una tienda online analiza su actividad comercial durante dos semanas consecutivas. Para ello, resume la información semanal mediante vectores que contienen tres indicadores clave del negocio.

Los registros son:

$$s_1 = (120,\ 45,\ 30)$$

$$s_2 = (150,\ 60,\ 50)$$

donde las componentes representan, respectivamente:

* visitas al sitio web,
* compras realizadas,
* tickets de soporte recibidos.

El equipo comercial desea estudiar cómo cambió la actividad de la tienda entre una semana y otra.


a) Determine el vector incremento: $s_2 - s_1$


$$s_2 - s_1 = (150, 60, 50) - (120, 45, 30)$$

$$s_2 - s_1= (30, 15, 20)$$


b) Determine el vector promedio semanal:
$$\frac{s_1 + s_2}{2}$$


$$\frac{s_1 + s_2}{2}=\frac{(120,\ 45,\ 30)+(150,\ 60,\ 50)}{2}$$

$$= \frac{(270,\ 105,\ 80)}{2}$$

$$= (135,\ 52,5,\ 40)$$


c) En términos absolutos, ¿se generaron más compras nuevas o más tickets de soportes nuevos de una semana a otra?


Las compras aumentaron en 15 unidades, mientras que los tickets de soporte aumentaron en 20 unidades. El aumento de tickets fue mayor que el aumento de compras, por lo que no parece ser completamente proporcional. Esto podría indicar que el incremento de actividad generó más consultas o problemas operativos.


d) Interprete ambos resultados en el contexto del problema.


El vector incremento indica que, de una semana a otra, la tienda aumentó en 30 visitas, 15 compras y 20 tickets de soporte. El vector promedio muestra que, considerando ambas semanas, la tienda tuvo en promedio 135 visitas, 52,5 compras y 40 tickets de soporte por semana.


# **Actividad 4 - Ajuste de señales en un sistema de monitoreo 📝**


Un sistema de monitoreo recibe señales desde cuatro sensores instalados en una infraestructura crítica. Para mejorar la detección de eventos, el sistema aplica una transformación simple: primero duplica la intensidad de las señales y luego agrega un refuerzo adicional en algunos sensores.

El vector original de señales es:

$$v=(3,5,2,4)$$

Donde cada componente del vector representa la intensidad de la señal recibida desde los sensores 1, 2, 3 y 4, respectivamente.

El refuerzo adicional aplicado por el sistema es:

$$r=(1,1,0,2)$$


a) Determine el vector resultante $2v$ después de duplicar la señal original.


$$2v=2(3,5,2,4)$$

$$2v=(6,10,4,8)$$


b) Determine el vector final $2v+r$ después de agregar el refuerzo.


$$2v+r=(6,10,4,8)+(1,1,0,2)$$

$$2v+r=(7,11,4,10)$$


c)  ¿Qué sensor no recibió refuerzo adicional?


El sensor 3 no recibió refuerzo adicional, porque la tercera componente del vector $r$ es 0.


d) Interprete el resultado final en el contexto del sistema de monitoreo.


El vector final $(7, 11, 4, 10)$ indica que después de duplicar las señales originales y agregar el refuerzo adicional, las intensidades finales de los sensores 1, 2, 3 y 4 son 7, 11, 4 y 10, respectivamente. Los sensores 1, 2 y 4 recibieron refuerzo adicional, mientras que el sensor 3 solo fue duplicado.


# 💡Reflexión

Responde brevemente:

a) ¿Por qué es importante respetar el orden de las componentes de un vector?

b) ¿Qué operación permite comparar dos registros componente a componente?

c) ¿Qué efecto tiene multiplicar un vector por un escalar?

d) ¿Por qué estas operaciones pueden representar cambios en datos reales?


# 🐍 Recordatorio Python

En las actividades anteriores se trabajaron operaciones básicas con vectores de forma manual. Ahora se implementarán estas mismas ideas en Python usando NumPy.


```python
import numpy as np
```


Para crear un vector


```python
v = np.array([1, 2, 3])
print(v)
```

**Salida:**


```
[1 2 3]
```


En NumPy, las operaciones entre vectores se realizan componente a componente, siempre que los vectores tengan la misma dimensión.


# **Actividad 5 - Agricultura inteligente 💻/🐍**


Una empresa agrícola utiliza sensores para monitorear un cultivo. Durante una jornada, registra un vector con cuatro variables ambientales: temperatura, humedad del suelo, radiación solar y velocidad del viento.
El registro del cultivo es:

$$c=(24,68,850,12)$$

donde las componentes representan, respectivamente:

*	temperatura, medida en grados Celsius (°C);
*	humedad del suelo, medida en porcentaje (%);
*	radiación solar, medida en watts por metro cuadrado (W/$m^2$);
* velocidad del viento, medida en kilómetros por hora (km/h).


a) Represente el vector en Python e imprima cada componente con su significado y unidad de medida.


```python
import numpy as np

# Vector del cultivo:
# [temperatura, humedad del suelo, radiación solar, velocidad del viento]
cultivo = np.array([24, 68, 850, 12])

print("Vector del cultivo:")
print(cultivo)

print("\nInterpretación de componentes:")
print("Temperatura:", cultivo[0],"°C")
print("Humedad del suelo:", cultivo[1],"%")
print("Radiación solar:", cultivo[2],"W/m2")
print("Velocidad del viento:", cultivo[3],"km/h")
```

**Salida:**


```
Vector del cultivo:
[ 24  68 850  12]

Interpretación de componentes:
Temperatura: 24 °C
Humedad del suelo: 68 %
Radiación solar: 850 W/m2
Velocidad del viento: 12 km/h
```


b) Explique por qué es importante respetar el orden de las componentes del vector.


El vector permite representar distintas mediciones ambientales en una sola estructura ordenada. Cada posición del vector tiene un significado específico, por lo que cambiar el orden modificaría la interpretación de los datos.


# **Actividad 6 - Registro de tráfico urbano 💻/🐍**


Una municipalidad registra el flujo vehicular en dos horarios distintos del día. Cada vector resume el número de vehículos observados en tres zonas de la ciudad: norte, centro y sur.

Los registros son:

$$m=(120,\ 90,\ 150)$$

$$t=(180,\ 110,\ 170)$$

donde $m$ representa la mañana y $t$ representa la tarde.


a) Calcule el total de vehículos registrados por zona durante ambos horarios.


```python
import numpy as np

# Vectores de flujo vehicular:
# [zona norte, zona centro, zona sur]
manana = np.array([120, 90, 150])
tarde = np.array([180, 110, 170])

# Suma componente a componente
total = manana + tarde

print("Total de vehículos por zona:")
print(total)
```

**Salida:**


```
Total de vehículos por zona:
[300 200 320]
```


b) Según el vector total obtenido, ¿qué zona concentra mayor flujo vehicular acumulado?


```python
# Encabezado de la impresión
print("\nZona con mayor flujo acumulado:")

# Creamos un arreglo con las zonas asociadas a los vectores
zonas = np.array(["Norte", "Centro", "Sur"])

# Mediante np.argmax buscamos en el arreglo "total" la posición donde se encuentra el mayor valor dentro del arreglo
indice_mayor = np.argmax(total)

# Se extrae el contenido, en ambos vectores, asociado al índice que contiene el mayor valor en el arreglo "total"
print(zonas[indice_mayor], "con", total[indice_mayor], "vehículos")
```

**Salida:**


```

Zona con mayor flujo acumulado:
Sur con 320 vehículos
```


c) ¿Qué decisión podría tomar la municipalidad con esta información?


El vector total es: $(300,\ 200,\ 320)$

Esto indica que la zona sur concentra el mayor flujo vehicular acumulado, con 320 vehículos. La municipalidad podría priorizar esa zona para estudiar congestión, revisar la configuración de semáforos o reforzar medidas de gestión vial.


# **Actividad 7 - Indicadores de rendimiento académico 💻/🐍**


Para analizar el desempeño general de una sección a partir de dos evaluaciones, se utilizan vectores que representan el promedio obtenido en tres áreas: teoría, aplicación y resolución de problemas.

Los registros se presentan a continuación en el orden mencionado:

$$e_1 = (5,2;\ 4,8;\ 5,5)$$

$$e_2 = (5,6;\ 5,1;\ 5,8)$$


a) Calcule el promedio vectorial entre ambas evaluaciones.


```python
import numpy as np

# Vectores de desempeño:
# [teoría, aplicación, resolución de problemas]
evaluacion_1 = np.array([5.2, 4.8, 5.5])
evaluacion_2 = np.array([5.6, 5.1, 5.8])

# Promedio componente a componente
promedio = (evaluacion_1 + evaluacion_2) / 2

print("Promedio por área:")
print(promedio)
```

**Salida:**


```
Promedio por área:
[5.4  4.95 5.65]
```


b) ¿En qué área se observa el mayor promedio?


```python
areas = np.array(["Teoría", "Aplicación", "Resolución de problemas"])
indice_mayor = np.argmax(promedio)

print("\nÁrea con mayor promedio:")
print(areas[indice_mayor], "con promedio", promedio[indice_mayor])
```

**Salida:**


```

Área con mayor promedio:
Resolución de problemas con promedio 5.65
```


c) ¿Qué podría concluir el equipo docente a partir de estos resultados?


El vector promedio es $(5,4;\ 4,95;\ 5,65)$. El área con mayor promedio es resolución de problemas, mientras que aplicación presenta el promedio más bajo. A partir de estos resultados, el equipo docente podría concluir que la sección muestra un mejor desempeño promedio en resolución de problemas y que el área de aplicación podría requerir mayor refuerzo.


# **Actividad 8 - Consumo energético en edificios 💻/🐍**


Una empresa de eficiencia energética registra el consumo de un edificio en cuatro franjas horarias, donde las componentes representan el consumo energético, medido en kilowatt-hora, durante la mañana, mediodía, tarde y noche, respectivamente:

$$e=(40,\ 55,\ 70,\ 60)$$

Debido a una alerta de alta demanda, se simula un escenario en el que el consumo aumenta en un 20%.


a) Calcule el nuevo vector de consumo si todos los valores aumentan en un 20%.


```python
import numpy as np

# Vector de consumo energético:
# [mañana, mediodía, tarde, noche]
consumo = np.array([40, 55, 70, 60])

# Aumento del 20%, equivalente a multiplicar por 1.2
nuevo_consumo = 1.2 * consumo

print("Consumo original:")
print(consumo)

print("\nConsumo con aumento del 20%:")
print(nuevo_consumo)
```

**Salida:**


```
Consumo original:
[40 55 70 60]

Consumo con aumento del 20%:
[48. 66. 84. 72.]
```


b) Utilice Python para mostrar en consola cuál es la componente de mayor valor y a qué categoría corresponde


```python
franjas = np.array(["Mañana", "Mediodía", "Tarde", "Noche"])
indice_mayor = np.argmax(nuevo_consumo)

print("\nFranja con mayor consumo después del aumento:")
print(franjas[indice_mayor], "con", nuevo_consumo[indice_mayor])
```

**Salida:**


```

Franja con mayor consumo después del aumento:
Tarde con 84.0
```


c) ¿El aumento porcentual cambia la relación entre las franjas horarias? Explique.


El nuevo vector de consumo es: $(48,\ 66,\ 84,\ 72)$

La franja con mayor consumo sigue siendo la tarde. Como todos los valores aumentaron en la misma proporción, la relación entre las franjas horarias no cambia: la tarde sigue siendo la franja de mayor consumo, y la mañana la de menor consumo.


#💡Reflexión

Responde brevemente:

a) ¿Qué ventaja tiene representar datos como vectores en Python?

b) ¿Qué operación manual se vuelve más simple al usar NumPy?

c) ¿Por qué es importante interpretar los resultados y no solo ejecutar el código?

d) ¿Qué significa que NumPy opere los vectores componente a componente?


```python
# @title
%%html
<div style="border: 4px solid #006d77; border-radius: 0px; overflow: hidden; font-family: sans-serif; max-width: 800px; margin-bottom: 20px;">

  <div style="background-color: #000000; color: #ffc107; padding: 10px 15px; font-weight: bold; font-size: 16px; display: flex; align-items: center;">
    <span style="margin-right: 10px; font-size: 18px;">💡</span>
    <span>Magnitud y similitud entre registros vectoriales</span>
  </div>

  <div style="background-color: #ffffff; padding: 20px; display: flex; align-items: center; justify-content: space-between;">

    <div style="color: #000000; flex: 1; padding-right: 30px; font-size: 14px; line-height: 1.5;">
      Antes de continuar con la comparación de registros, revisa este recurso para distinguir entre
      la magnitud de un vector y la similitud entre dos registros. <b>Escanea o haz clic en el código QR</b>
      para aprender cómo calcular e interpretar la norma y la distancia euclidiana, considerando también el
      efecto de la escala de las variables.
    </div>

    <div style="flex-shrink: 0;">
      <a href="https://duoc.h5p.com/content/1292920545337914768" target="_blank">
        <img src="https://i.ibb.co/GfQv6TXn/L1-H5P2.png"
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
    <span>Magnitud y similitud entre registros vectoriales</span>
  </div>

  <div style="background-color: #ffffff; padding: 20px; display: flex; align-items: center; justify-content: space-between;">

    <div style="color: #000000; flex: 1; padding-right: 30px; font-size: 14px; line-height: 1.5;">
      Antes de continuar con la comparación de registros, revisa este recurso para distinguir entre 
      la magnitud de un vector y la similitud entre dos registros. <b>Escanea o haz clic en el código QR</b> 
      para aprender cómo calcular e interpretar la norma y la distancia euclidiana, considerando también el 
      efecto de la escala de las variables.
    </div>

    <div style="flex-shrink: 0;">
      <a href="https://duoc.h5p.com/content/1292920545337914768" target="_blank">
        <img src="https://i.ibb.co/GfQv6TXn/L1-H5P2.png"
             alt="QR Code"
             style="width: 100px; height: 100px; border: none;">
      </a>
    </div>

  </div>

  <div style="background-color: #000000; color: #ffc107; padding: 8px 15px; font-weight: bold; font-size: 16px;">
    Presentación interactiva H5P
  </div>

</div>


# 📌 Consulta rápida: norma y distancia euclidiana

La norma representa la magnitud global del vector:

$$\left\| u\right\|=\sqrt{x_{1}^{2}+x_{2}^{2}+ ... +x_{n}^{2}}$$

La distancia euclidiana representa la diferencia global entre dos registros. Una menor distancia indica mayor similitud:

$$d(u,v)=\left\| u-v\right\|$$

**Recuerda**: la escala de las variables puede influir en la comparación.


# **Actividad 9 - Indicadores fisiológicos en pacientes hospitalarios 📝**


Un hospital monitorea a dos pacientes mediante un conjunto reducido de indicadores fisiológicos. Cada paciente se representa mediante un vector que resume mediciones clínicas tomadas en un mismo periodo.

Los registros son:

$$p_1 = (120, 80, 95, 18)$$

$$p_2 = (110, 75, 90, 20)$$

donde las componentes representan, respectivamente:

* presión sistólica,
* frecuencia cardíaca,
* saturación de oxígeno,
* frecuencia respiratoria.

El equipo de análisis desea comparar la magnitud numérica de ambos registros mediante la norma euclidiana y discutir qué información entrega esta medida.


a) Calcule la norma de ambos vectores.


Para el paciente 1:
$$\|p_1\| = \sqrt{120^2 + 80^2 + 95^2 + 18^2}$$

$$\|p_1\| = \sqrt{14400 + 6400 + 9025 + 324}$$

$$\|p_1\| = \sqrt{30149} \approx 173,63$$


Para el paciente 2:
$$\|p_2\| = \sqrt{110^2 + 75^2 + 90^2 + 20^2}$$

$$\|p_2\| = \sqrt{12100 + 5625 + 8100 + 400}$$

$$\|p_2\| = \sqrt{26225} \approx 161,94$$


b) Determine cuál paciente presenta mayor norma del vector de registros. ¿Qué precaución debe tenerse al interpretar este resultado?


El paciente 1 presenta mayor norma del vector de registros, ya que.

$$173,63 > 161,94$$

Sin embargo, esta medida no permite concluir por sí sola que su condición sea más grave, ya que cada variable clínica debe interpretarse según criterios médicos y escalas específicas.


c) ¿La norma permite identificar exactamente qué variable explica la diferencia entre ambos pacientes? Justifique.


No. La norma resume todos los valores en una sola medida global, pero no indica por sí sola qué componente específica explica la diferencia. Para identificar la variable más influyente, se debe revisar la comparación componente a componente.


d)	¿Qué precaución debe tenerse al comparar las normas de estos vectores, considerando que las componentes corresponden a indicadores fisiológicos distintos?


Se debe tener precaución porque las componentes representan variables clínicas distintas y no necesariamente están en la misma escala ni tienen el mismo rango de valores. Por ejemplo, la presión sistólica, la frecuencia cardíaca y la saturación de oxígeno tienen valores numéricamente mayores que la frecuencia respiratoria, por lo que pueden influir más en la norma.


# **Actividad 10 - Comparación de perfiles de clientes tecnológicos 📝**


Una empresa tecnológica analiza el comportamiento de sus clientes en una aplicación. Cada cliente se representa mediante un vector de características que resume su interacción con el servicio durante un mes.

Los perfiles son:

$$u_1 = (15, 7, 10, 4)$$

$$u_2 = (14, 6, 9, 5)$$

$$u_3 = (25, 15, 18, 9)$$

donde las componentes representan, respectivamente:

* horas de uso,
* compras realizadas,
* funcionalidades utilizadas,
* solicitudes de soporte.

El equipo de análisis desea determinar cuál cliente tiene un comportamiento más parecido al cliente $u_1$.


a) Calcule la distancia euclidiana entre $u_1$ y $u_2$.


$$u_1 - u_2 = (15, 7, 10, 4) - (14, 6, 9, 5)$$

$$u_1 - u_2 = (1, 1, 1, -1)$$

$$d(u_1, u_2) = \sqrt{1^2 + 1^2 + 1^2 + (-1)^2}$$

$$d(u_1, u_2) = \sqrt{4} = 2$$


b) Calcule la distancia euclidiana entre $u_1$ y $u_3$.


$$u_1 - u_3 = (15, 7, 10, 4) - (25, 15, 18, 9)$$

$$u_1 - u_3 = (-10, -8, -8, -5)$$

$$d(u_1, u_3) = \sqrt{(-10)^2 + (-8)^2 + (-8)^2 + (-5)^2}$$

$$d(u_1, u_3) = \sqrt{100 + 64 + 64 + 25}$$

$$d(u_1, u_3) = \sqrt{253} \approx 15,91$$


c) ¿Qué cliente posee un comportamiento más similar a $u_1$? Justifique.


Según la distancia euclidiana calculada, el cliente $u_2$ posee un comportamiento más similar a $u_1$, porque su distancia respecto de $u_1$ es menor:

$$2 < 15,91$$

Esto significa que, bajo esta medida de comparación, las diferencias globales entre $u_1$ y $u_2$ son menores que entre $u_1$ y $u_3$.


d) ¿Qué precaución debe considerarse al usar la distancia euclidiana para comparar perfiles de clientes con variables como horas de uso, compras realizadas, funcionalidades utilizadas y solicitudes de soporte?


Se debe considerar que las variables pueden tener escalas distintas. Si una variable toma valores mucho más grandes que las demás, puede influir más en la distancia euclidiana y aportar más al resultado final. Por lo tanto, la distancia euclidiana permite comparar los perfiles según los datos entregados, pero su interpretación debe considerar que algunas componentes podrían tener mayor peso por su escala numérica.


# **Actividad 11 - Actividad de usuarios en una red social 📝**


Una red social analiza el comportamiento de tres usuarios durante una semana. Para ello, representa a cada usuario mediante un vector de actividad digital formado por indicadores comparables entre sí.

Los perfiles son:

$$a=(20,10,8,5)$$

$$b=(18,12,7,6)$$

$$c=(35,20,15,10)$$

donde las componentes representan, respectivamente indicadores asociados a:

* horas de uso,
* publicaciones realizadas,
* interacciones recibidas,
* mensajes enviados.

El equipo de análisis desea distinguir entre actividad general y similitud de comportamiento respecto del usuario $a$.


a) Calcule la norma de cada usuario.


Norma del usuario $a$:

\begin{align*}
\|a\| &= \sqrt{20^2 + 10^2 + 8^2 + 5^2} \\
\|a\| &= \sqrt{400 + 100 + 64 + 25} \\
\|a\| &= \sqrt{589} \approx 24,27
\end{align*}

Norma del usuario $b$:

\begin{align*}
\|b\| &= \sqrt{18^2 + 12^2 + 7^2 + 6^2} \\
\|b\| &= \sqrt{324 + 144 + 49 + 36} \\
\|b\| &= \sqrt{553} \approx 23,52
\end{align*}

Norma del usuario $c$:

\begin{align*}
\|c\| &= \sqrt{35^2 + 20^2 + 15^2 + 10^2} \\
\|c\| &= \sqrt{1225 + 400 + 225 + 100} \\
\|c\| &= \sqrt{1950} \approx 44,16
\end{align*}


b) Determine cuál usuario presenta mayor actividad general.


El usuario $c$ presenta mayor actividad general, porque tiene la norma más alta.


c) Calcule las distancias: $d(a,b)$ y $d(a,c)$


Distancia entre $a$ y $b$:

\begin{align*}
a - b &= (20, 10, 8, 5) - (18, 12, 7, 6) \\
a - b &= (2, -2, 1, -1) \\
d(a,b) &= \sqrt{2^2 + (-2)^2 + 1^2 + (-1)^2} \\
d(a,b) &= \sqrt{4 + 4 + 1 + 1} \\
d(a,b) &= \sqrt{10} \approx 3,16
\end{align*}

Distancia entre $a$ y $c$:

\begin{align*}
a - c &= (20, 10, 8, 5) - (35, 20, 15, 10) \\
a - c &= (-15, -10, -7, -5) \\
d(a,c) &= \sqrt{(-15)^2 + (-10)^2 + (-7)^2 + (-5)^2} \\
d(a,c) &= \sqrt{225 + 100 + 49 + 25} \\
d(a,c) &= \sqrt{399} \approx 19,97
\end{align*}


d) ¿El usuario con mayor actividad general es necesariamente el más parecido al usuario $a$? Justifique.


No. El usuario $c$ tiene mayor actividad general, pero no es el más parecido al usuario $a$. El usuario más parecido a $a$ es $b$, porque la distancia entre ambos es menor. Esto muestra que una norma alta indica mayor magnitud global, mientras que la distancia permite comparar similitud entre registros.


# **Actividad 12 - Comparación de dispositivos IoT en monitoreo ambiental 📝**


Una empresa utiliza dispositivos IoT para monitorear condiciones ambientales en distintas zonas de una ciudad. Cada dispositivo genera un vector con cuatro mediciones tomadas durante una jornada.

Los registros son:

$$s_1 = (50,70,30,90)$$

$$s_2 = (48,65,35,85)$$

$$s_3 = (90,120,80,150)$$

donde las componentes representan, respectivamente:

* nivel de ruido,
* concentración de partículas,
* temperatura superficial,
* flujo vehicular estimado.

El equipo técnico desea identificar cuál dispositivo registra condiciones más parecidas a las del dispositivo $s_1$, considerando la cercanía global entre los registros a partir de sus componentes.


a)	Determine qué dispositivo registra condiciones más similares a las de $s_1$. Justifique matemáticamente su respuesta.


Calculamos la distancia euclidiana entre $s_1$ y $s_2$.


$$s_1 - s_2 =(50,70,30,90)-(48,65,35,85)$$

$$s_1 - s_2 =(2,5,-5,5)$$


\begin{align*}
d(s_1, s_2) &= \sqrt{2^2 + 5^2 + (-5)^2 + 5^2} \\
d(s_1, s_2) &= \sqrt{4 + 25 + 25 + 25} \\
d(s_1, s_2) &= \sqrt{79} \approx 8,89
\end{align*}


Calculamos la distancia euclidiana entre $s_1$ y $s_3$.


\begin{align*}
s_1 - s_3 &= (50, 70, 30, 90) - (90, 120, 80, 150) \\
s_1 - s_3 &= (-40, -50, -50, -60) \\
d(s_1, s_3) &= \sqrt{(-40)^2 + (-50)^2 + (-50)^2 + (-60)^2} \\
d(s_1, s_3) &= \sqrt{1600 + 2500 + 2500 + 3600} \\
d(s_1, s_3) &= \sqrt{10200} \approx 100,99
\end{align*}


El dispositivo $s_2$ registra condiciones más similares a las de $s_1$, porque al comparar las distancias entre $s_1$ y los otros dispositivos, la menor distancia corresponde a $s_2$. Esto indica que sus diferencias globales respecto de $s_1$ son menores que las observadas con $s_3$.


b)	Considerando el desarrollo realizado en el inciso anterior, identifique qué variables explican principalmente la mayor lejanía respecto de $s_1$. Justifique su respuesta.


La mayor lejanía respecto de $s_1$ se observa al comparar con $s_3$. Al revisar las diferencias componente a componente, las variables que más aportan a esa lejanía son el flujo vehicular estimado, la concentración de partículas y la temperatura superficial, ya que presentan las mayores diferencias absolutas respecto de $s_1$.


#💡Reflexión

Responde brevemente:

a) ¿Qué mide la norma de un vector?

b) ¿Qué mide la distancia euclidiana entre dos vectores?

c) ¿Un vector con mayor norma es necesariamente el más parecido a otro?

d) ¿Por qué la escala de las variables puede afectar la distancia euclidiana?


# 🐍Recordatorio Python

Para calcular la norma de un vector se utiliza:


```python
np.linalg.norm(vector)
```


Para calcular la distancia euclidiana entre dos vectores se puede usar:


```python
np.linalg.norm(vector1 - vector2)
```


# **Actividad 13 - Rendimiento físico de deportistas 💻/🐍**


Un centro deportivo evalúa a dos deportistas mediante cuatro indicadores físicos: velocidad, resistencia, fuerza y flexibilidad. Cada deportista se representa mediante un vector de resultados.

Los registros son:

$$d_1 = (8,\ 7,\ 9,\ 6)$$

$$d_2 = (6,\ 8,\ 7,\ 7)$$

**Nota**: Los indicadores están expresados como puntajes en una escala común de 1 a 10, donde un mayor puntaje representa mejor desempeño.


a) Calcule la norma de cada vector.


```python
import numpy as np

# Vectores de rendimiento:
# [velocidad, resistencia, fuerza, flexibilidad]
deportista_1 = np.array([8, 7, 9, 6])
deportista_2 = np.array([6, 8, 7, 7])
```


```python
# Cálculo de normas
norma_1 = np.linalg.norm(deportista_1)
norma_2 = np.linalg.norm(deportista_2)

print("Norma deportista 1:", round(norma_1, 2))
print("Norma deportista 2:", round(norma_2, 2))
```

**Salida:**


```
Norma deportista 1: 15.17
Norma deportista 2: 14.07
```


b) Determine qué deportista presenta mayor magnitud global de rendimiento.


```python
if norma_1 > norma_2:
    print("El deportista 1 presenta mayor magnitud global de rendimiento.")
elif norma_1 == norma_2:
    print("Ambos deportistas presentan la misma magnitud global de rendimiento.")
else:
    print("El deportista 2 presenta mayor magnitud global de rendimiento.")
```

**Salida:**


```
El deportista 1 presenta mayor magnitud global de rendimiento.
```


c) Calcule la diferencia componente a componente entre ambos deportistas.


```python
# Cálculo de diferencia
diferencia = deportista_1 - deportista_2
print("Diferencia componente a componente:", diferencia)
```

**Salida:**


```
Diferencia componente a componente: [ 2 -1  2 -1]
```


d) ¿En qué indicador destaca cada deportista?


La diferencia componente a componente permite observar en qué indicadores destaca cada deportista. El deportista 1 supera al deportista 2 en velocidad y fuerza, mientras que el deportista 2 supera al deportista 1 en resistencia y flexibilidad.

La norma resume la magnitud global del vector de rendimiento, pero no reemplaza la revisión componente a componente.


# **Actividad 14 - Comparación de sucursales bancarias 💻/🐍**


Un banco compara dos sucursales a partir de cuatro indicadores mensuales: nuevos clientes, créditos otorgados, reclamos recibidos y atenciones realizadas.

Los registros son:

$$b_1 = (80,35,12,400)$$

$$b_2 = (75,40,15,380)$$

Considere que los componentes de cada vector corresponden, en el mismo orden, a los indicadores mencionados.


a) Calcule el vector diferencia $b_1-b_2$ e interprete sus componentes en el contexto del problema.


```python
import numpy as np

# Vectores de sucursales:
# [nuevos clientes, créditos otorgados, reclamos, atenciones]
sucursal_1 = np.array([80, 35, 12, 400])
sucursal_2 = np.array([75, 40, 15, 380])

diferencia = sucursal_1 - sucursal_2
print(diferencia)
```

**Salida:**


```
[ 5 -5 -3 20]
```


 En el vector diferencia $(5, -5, -3, 20)$, observamos que la sucursal 1 tiene tiene 5 nuevos clientes más, 5 créditos menos, 3 reclamos menos y 20 atenciones más que la sucursal 2.


b) Calcule la distancia euclidiana entre ambas sucursales e interprete el resultado


```python
import numpy as np

# Distancia euclidiana
distancia = np.linalg.norm(sucursal_1 - sucursal_2)

print("Distancia euclidiana entre sucursales:", distancia)
```

**Salida:**


```
Distancia euclidiana entre sucursales: 21.42428528562855
```


La distancia euclidiana de 21,42 representa la norma del vector diferencia, entregando una medida de la magnitud global de la discrepancia entre ambas sucursales. Al abrir este resultado e interpretar


c) ¿Por qué se debe tener cuidado al interpretar esta distancia?


La distancia euclidiana resume la diferencia global entre ambas sucursales. Sin embargo, debe interpretarse con cuidado, porque la variable “atenciones realizadas” tiene valores mucho mayores que “reclamos” o “créditos otorgados”. Por eso, esta variable puede dominar el cálculo de la distancia. En análisis de datos reales, esto suele corregirse mediante estandarización.


# **Actividad 15 - Comparación de canciones en una aplicación musical 💻/🐍**


Una aplicación musical representa canciones mediante vectores de características. Cada canción se describe mediante cuatro variables: energía, bailabilidad, duración normalizada y popularidad. Para este análisis, las características se expresan como puntajes en una escala común.

Los registros son:

$$c_1 = (8,7,5,9)$$

$$c_2 = (7,8,5,8)$$

$$c_3 = (3,4,9,5)$$

La plataforma desea identificar qué canción se parece más a la canción $c_1$ según distancia euclidiana.


a) Calcule las distancias desde $c_1$ hacia las otras canciones.


```python
import numpy as np

# Vectores de canciones:
# [energía, bailabilidad, duración normalizada, popularidad]
cancion_1 = np.array([8, 7, 5, 9])
cancion_2 = np.array([7, 8, 5, 8])
cancion_3 = np.array([3, 4, 9, 5])

# Diferencias componente a componente
dif_12 = cancion_1 - cancion_2
dif_13 = cancion_1 - cancion_3

# Cálculo de distancias respecto a canción 1
distancia_12 = np.linalg.norm(dif_12)
distancia_13 = np.linalg.norm(dif_13)

print("Diferencia canción 1 - canción 2:")
print(dif_12)

print("\nDiferencia canción 1 - canción 3:")
print(dif_13)

print("\nDistancia entre canción 1 y canción 2:", distancia_12)
print("Distancia entre canción 1 y canción 3:", distancia_13)
```

**Salida:**


```
Diferencia canción 1 - canción 2:
[ 1 -1  0  1]

Diferencia canción 1 - canción 3:
[ 5  3 -4  4]

Distancia entre canción 1 y canción 2: 1.7320508075688772
Distancia entre canción 1 y canción 3: 8.12403840463596
```


b) Identifique la canción más similar a $c_1$.


```python

if distancia_12 < distancia_13:
    print("\nLa canción 2 es más similar a la canción 1.")
elif distancia_12 > distancia_13:
    print("\nLa canción 3 es más similar a la canción 1.")
else:
    print("\nLas canciones 2 y 3 son igualmente similares a la canción 1.")
```

**Salida:**


```

La canción 2 es más similar a la canción 1.
```


La canción con menor distancia respecto de $c_1$ es la más parecida según las variables consideradas. En este caso, la canción 2 es más similar a la canción 1.


c) ¿Qué variable aporta más a la distancia entre $c_1$ y $c_3$? Justifique su respuesta.


La diferencia entre $c_1$ y $c_3$ es: $(5,3,-4,4)$

La mayor diferencia absoluta corresponde a energía, con una diferencia de 5 unidades. Por lo tanto, esa variable aporta fuertemente a la distancia entre ambas canciones.

Este tipo de comparación es una primera aproximación a sistemas de recomendación basados en características.


# **Actividad 16 - Priorización de mantenimiento en buses eléctricos 💻/🐍**


Una empresa de transporte monitorea tres buses eléctricos mediante cuatro indicadores técnicos: temperatura de batería, ciclos de carga, consumo energético y eventos de alerta. Cada bus se representa mediante un vector cuyas componentes siguen el orden de las variables mencionadas.
Los registros son:

$$b_1 = (35,120,80,2)$$

$$b_2 = (37,125,85,3)$$

$$b_3 = (50,180,120,8)$$

El bus $b_1$ se considera como referencia de funcionamiento esperado. El equipo técnico desea identificar cuál de los otros buses presenta un funcionamiento más similar a esa referencia y qué aspectos explican la diferencia observada.


a)	Determine cuál bus se encuentra más cerca del funcionamiento esperado. Justifique matemáticamente su respuesta


```python
import numpy as np

# Vectores de buses:
# [temperatura batería, ciclos de carga, consumo energético, eventos de alerta]
bus_1 = np.array([35, 120, 80, 2])
bus_2 = np.array([37, 125, 85, 3])
bus_3 = np.array([50, 180, 120, 8])

# Cálculo de normas
norma_1 = np.linalg.norm(bus_1)
norma_2 = np.linalg.norm(bus_2)
norma_3 = np.linalg.norm(bus_3)

print("Normas de los buses:")
print("Bus 1:", round(norma_1, 1))
print("Bus 2:", round(norma_2, 1))
print("Bus 3:", round(norma_3, 1))
```

**Salida:**


```
Normas de los buses:
Bus 1: 148.4
Bus 2: 155.7
Bus 3: 222.2
```


El bus $b_2$ presenta un funcionamiento técnico más similar al bus $b_1$, porque su distancia respecto del bus de referencia es menor que la distancia entre $b_1$ y $b_3$. Esto indica que considerando conjuntamente los indicadores técnicos, $b_2$ se encuentra más cerca del funcionamiento esperado.


b)	Considerando el desarrollo realizado en el inciso anterior, identifique qué variables explican principalmente la mayor lejanía respecto del funcionamiento esperado. Justifique su respuesta.


```python
# Vector ideal definido por el fabricante
vector_ideal = np.array([35, 120, 80, 2])

# Diferencias respecto al vector ideal
dif_1 = bus_1 - vector_ideal
dif_2 = bus_2 - vector_ideal
dif_3 = bus_3 - vector_ideal

# Distancias respecto al vector ideal
distancia_1 = np.linalg.norm(dif_1)
distancia_2 = np.linalg.norm(dif_2)
distancia_3 = np.linalg.norm(dif_3)

print("Diferencias respecto al vector ideal:")
print("Bus 1 - Vector ideal:", dif_1)
print("Bus 2 - Vector ideal:", dif_2)
print("Bus 3 - Vector ideal:", dif_3)

print("\nDistancias respecto al vector ideal:")
print("Distancia Bus 1:", round(distancia_1,1))
print("Distancia Bus 2:", round(distancia_2,1))
print("Distancia Bus 3:", round(distancia_3,1))
```

**Salida:**


```
Diferencias respecto al vector ideal:
Bus 1 - Vector ideal: [0 0 0 0]
Bus 2 - Vector ideal: [2 5 5 1]
Bus 3 - Vector ideal: [15 60 40  6]

Distancias respecto al vector ideal:
Distancia Bus 1: 0.0
Distancia Bus 2: 7.4
Distancia Bus 3: 73.9
```


```python
# Guardar distancias en una lista
distancias = [distancia_1, distancia_2, distancia_3]

# Identificar el bus más cercano al vector ideal
bus_mas_cercano = np.argmin(distancias) + 1

print("El bus más cercano al vector ideal es el Bus", bus_mas_cercano)
```

**Salida:**


```
El bus más cercano al vector ideal es el Bus 1
```


La mayor lejanía respecto del funcionamiento esperado se observa al comparar con $b_1$ con $b_3$. Al revisar las diferencias componente a componente, las variables que explican principalmente esa lejanía son los ciclos de carga y el consumo energético, ya que presentan diferencias mayores que las demás componentes.


c)	¿Qué precaución debe tenerse al interpretar la comparación realizada, considerando la escala de las variables?


Se debe tener precaución porque las variables tienen escalas distintas. Indicadores como ciclos de carga o consumo energético tienen valores numéricamente mayores que eventos de alerta, por lo que pueden influir más en la distancia euclidiana. Por eso, la comparación permite una primera aproximación, pero no reemplaza un análisis técnico más detallado ni considera una posible estandarización de variables.


# **Actividad 17 - Perfiles de clientes en comercio electrónico 💻/🐍**


Una empresa de comercio electrónico representa a sus clientes mediante registros vectoriales de comportamiento mensual. Cada registro considera cuatro variables relevantes para el análisis comercial: visitas al sitio, compras realizadas, productos revisados y solicitudes de soporte. Las componentes de cada vector siguen el orden de las variables mencionadas.
Los clientes presentan los siguientes perfiles:

$$c_1 = (25,8,15,3)$$

$$c_2 = (20,6,12,2)$$

$$c_3 = (40,18,30,10)$$

El equipo de análisis desea comparar el comportamiento de los clientes para distinguir entre nivel general de actividad y similitud respecto del cliente $c_1$.


a)	Realice un análisis con Python que permita determinar qué cliente presenta mayor nivel general de actividad y qué cliente presenta un comportamiento más similar a $c_1$. Justifique matemáticamente su respuesta.


```python
import numpy as np

# Vectores de clientes:
# [visitas al sitio, compras, productos revisados, solicitudes de soporte]
c1 = np.array([25, 8, 15, 3])
c2 = np.array([20, 6, 12, 2])
c3 = np.array([40, 18, 30, 10])

# Vectores diferencia respecto de c1
diferencia_12 = c1 - c2
diferencia_13 = c1 - c3

print("Vector diferencia c1 - c2:")
print(diferencia_12)

print("\nVector diferencia c1 - c3:")
print(diferencia_13)

# Normas
norma_c1 = np.linalg.norm(c1)
norma_c2 = np.linalg.norm(c2)
norma_c3 = np.linalg.norm(c3)

print("\nNormas:")
print("Norma c1:", round(norma_c1, 2))
print("Norma c2:", round(norma_c2, 2))
print("Norma c3:", round(norma_c3, 2))

# Distancias respecto de c1
distancia_12 = np.linalg.norm(c1 - c2)
distancia_13 = np.linalg.norm(c1 - c3)

print("\nDistancias respecto de c1:")
print("Distancia c1-c2:", round(distancia_12, 2))
print("Distancia c1-c3:", round(distancia_13, 2))

# Cliente más cercano a c1
if distancia_12 < distancia_13:
    print("\nEl cliente c2 es más cercano a c1 en valores absolutos.")
else:
    print("\nEl cliente c3 es más cercano a c1 en valores absolutos.")
```

**Salida:**


```
Vector diferencia c1 - c2:
[5 2 3 1]

Vector diferencia c1 - c3:
[-15 -10 -15  -7]

Normas:
Norma c1: 30.38
Norma c2: 24.17
Norma c3: 54.07

Distancias respecto de c1:
Distancia c1-c2: 6.24
Distancia c1-c3: 24.47

El cliente c2 es más cercano a c1 en valores absolutos.
```


El cliente $c_3$ presenta mayor nivel general de actividad, ya que tiene la mayor norma del vector de comportamiento. Sin embargo, el cliente más similar a $c_1$ es $c_2$, porque la distancia euclidiana entre $c_1$ y $c_2$ es menor que la distancia entre $c_1$ y $c_3$.


b)	Explique si el cliente con mayor nivel general de actividad es necesariamente el más similar a $c_1$. Fundamente su respuesta a partir de los resultados obtenidos.


No. Una mayor norma indica mayor magnitud global de actividad, pero no necesariamente mayor similitud respecto de un cliente de referencia. En este caso, $c_3$ tiene mayor actividad general, pero está más alejado de $c_1$. La similitud respecto de $c_1$ se analiza mejor mediante la distancia euclidiana entre registros.


c)	Redacte una breve conclusión para el equipo de análisis comercial, indicando qué cliente se parece más a $c_1$ y qué precaución debe tenerse al interpretar estos resultados.


El cliente $c_2$ presenta un comportamiento más parecido al cliente $c_1$, por lo que podría considerarse más cercano a su perfil de interacción mensual. Sin embargo, la interpretación debe considerar que las variables pueden tener escalas distintas y que la distancia euclidiana entrega una medida global de comparación, no una explicación completa del comportamiento comercial.


# 💡Cierre y reflexión

Los vectores permiten transformar información del mundo real en estructuras matemáticas que pueden compararse, analizarse y procesarse computacionalmente. En este laboratorio, cada vector representó un registro: usuarios, máquinas, pacientes, sensores, canciones, buses, clientes o indicadores de rendimiento.

La suma permitió acumular información; la resta permitió comparar registros; la multiplicación por escalar permitió modificar la intensidad de las componentes; la norma entregó una medida de magnitud general; y la distancia euclidiana permitió medir diferencia global entre registros.

Esta forma de representar información será fundamental para avanzar hacia matrices. En el siguiente laboratorio, la idea de vector se ampliará hacia matrices, donde varios vectores podrán organizarse simultáneamente como filas o columnas de una tabla de datos. Comprender los vectores es, por tanto, el primer paso para analizar datasets completos.


# 🏅 En este laboratorio aprendiste a…

* Representar información mediante vectores.
* Interpretar el significado y el orden de las componentes.
* Sumar y restar vectores en contexto.
* Multiplicar vectores por escalares.
* Calcular la norma como magnitud global.
* Calcular la distancia euclidiana como diferencia global entre registros.
* Distinguir entre magnitud y similitud.
* Usar Python y NumPy para operar vectores.
* Interpretar resultados matemáticos en problemas aplicados.
* Reconocer que la escala de las variables puede afectar la interpretación de las distancias.
