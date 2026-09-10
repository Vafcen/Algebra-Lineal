# Álgebra Lineal

Conjunto de guías y laboratorios en Jupyter Notebook sobre álgebra lineal con Python, orientados a ciencia de datos e inteligencia artificial.

## Contenido

- Vectores como representación de información
- Matrices como organización y operación de datos
- Laboratorios 3 a 6: contenido próximamente disponible (se actualizará durante el semestre)

Cada laboratorio cuenta con:
- Una **guía teórica en PDF** (`G1`–`G6`) con el objetivo y contexto del laboratorio.
- Un **notebook de laboratorio** (`Lab1`–`Lab6`) con los problemas a resolver.
- Notebooks de **soluciones** (por ahora solo disponible para el Laboratorio 1).

## Instalación

Clona el repositorio:
```bash
git clone https://github.com/Vafcen/Algebra-Lineal.git
cd Algebra-Lineal
```

Instala las dependencias en un entorno virtual (Para no romper otros paquetes nativos del sistema):

*Nota: Si utilizas Google Colab no es necesario instalar las dependencias ya que vienen pre-instaladas en la instancia por defecto.*

Linux/MacOS
```bash
python3 -m venv ~/venvs/data && ~/venvs/data/bin/pip install --upgrade pip && ~/venvs/data/bin/pip install numpy jupyter
```
Windows (PowerShell)
```bash
python -m venv $HOME\venvs\data ; & "$HOME\venvs\data\Scripts\pip" install --upgrade pip ; & "$HOME\venvs\data\Scripts\pip" install numpy jupyter
```

## Paso a paso

Para cada laboratorio (`N` = 1, 2, 3...):

1. **Lee la guía teórica**: abre `GN_MAT6130.pdf` para revisar el objetivo, el contexto y los conceptos que se trabajarán.
2. **Abre el laboratorio**: abre `LabN_MAT6130.ipynb` en VS Code o Google Colab.
3. **Resuelve los problemas**, distinguiendo el tipo de resolución pedida:
   - 📝 Problemas que se resuelven a mano, con lápiz y papel.
   - 💻/🐍 Problemas que se resuelven de forma computacional, ejecutando las celdas de Python.
4. **Verifica tus respuestas**: si existe `Soluciones_Laboratorio_N_MAT6130.ipynb`, compáralo con tu propia resolución (actualmente disponible solo para el Laboratorio 1).

## Librerías utilizadas

- NumPy
