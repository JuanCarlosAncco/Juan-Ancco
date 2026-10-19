
# Challenge 1 · Pipeline de Machine Learning

### Caso C — Sueño en los recién nacidos
**Curso:** Machine Learning · UPCH · 2026-II  
**Estudiante:** Juan Carlos Ancco Quispe  
**Modalidad:** Individual

## 1. Presentación del caso y problema — 5 puntos

### ¿De dónde sale la idea?

Para el examen parcial me correspondió el **caso C: sueño en los recién nacidos**. Me interesó trabajar con una pregunta sencilla, que pudiera representarse en un programa y luego en un modelo: **¿cómo estimar la duración de un ciclo de sueño a partir de la edad y algunas características registradas?**

En una exploración anterior del caso se utilizaron tres valores **aproximados de una gráfica didáctica**: a los 3, 6 y 12 meses se asociaron duraciones de 50, 60 y 70 minutos. Estos números **no son mediciones clínicas ni representan una ley sobre el sueño infantil**. Los conservo como referencia del ejercicio previo, porque permiten construir un ejemplo reproducible.

| Edad (meses) | Ciclo de referencia (minutos) |
|:---:|:---:|
| 3 | 50 |
| 6 | 60 |
| 12 | 70 |

El título del caso es «recién nacidos», pero este **prototipo trabaja únicamente con edades de 3 a 12 meses**, porque ese es el intervalo de las referencias disponibles. No pretende cubrir el periodo neonatal.

### Problema que se desea resolver

El desafío es diseñar una pequeña solución que reciba una ficha con estos campos:

- **Edad del bebé:** en meses (3 a 12 para la demostración).
- **Lactancia:** materna, mixta o fórmula.
- **Rutina:** constante o variable, como categoría inventada para practicar.
- **Ambiente:** tranquilo o ruidoso, como categoría inventada para practicar.

A partir de esa ficha se realizarán **dos procesos distintos**: completar y validar los datos mediante una búsqueda en un espacio de estados, y entrenar un modelo de regresión que genere una **estimación simulada** de minutos por ciclo.

### ¿Por qué inteligencia artificial y Machine Learning?

No existe una regla única que permita convertir los cuatro campos en un resultado exacto. Por eso el reto es interesante como ejercicio de IA: primero se puede **representar un problema con estados, operadores y restricciones**; después se puede entrenar una **regresión supervisada** para aproximar una variable numérica a partir de ejemplos.

La elección de una **regresión lineal** es intencional: se puede explicar, inspeccionar sus coeficientes y comparar su error con un modelo que siempre predice el promedio. Para una primera práctica, prefiero comprender qué aprende el modelo antes de usar uno más complicado.

> **Alcance importante:** el conjunto de entrenamiento del segundo notebook es completamente sintético y sus relaciones fueron elegidas para demostrar un pipeline. No valida asociaciones sobre lactancia, rutina o ambiente, y no debe utilizarse para decisiones de salud, diagnóstico o recomendaciones sobre el sueño de bebés reales.

### Qué se espera obtener

1. Una representación formal del problema y sus restricciones.
2. Una búsqueda que construya una ficha válida a partir de datos disponibles.
3. Un experimento de regresión reproducible con entrenamiento, prueba y métricas.
4. Gráficos que permitan interpretar el procedimiento y reconocer sus límites.

---

## 2. Espacio de estados — 5 puntos

El modelo conceptual (estados, operadores, restricciones y representación visual) está explicado en **[02_Espacio_de_Estados.md](02_Espacio_de_Estados.md)**. La primera implementación del recorrido está en el notebook 03.

## 3. Pipeline de razonamiento, exploración y búsqueda — 5 puntos

**[Abrir 03_Pipeline_Busqueda.ipynb](03_Pipeline_Busqueda.ipynb)**  
De una ficha incompleta a una ficha válida: validación, generación de estados, recorrido BFS, búsqueda de una referencia cercana por edad y visualización de resultados.

## 4. Pipeline de regresión y visualización — 5 puntos

**[Abrir 04_Pipeline_Regresion.ipynb]([04_Pipeline_Regresion.ipynb](https://drive.google.com/file/d/1NmdMlFDdci2ZF_DrP-6GzO93GQj4iP4g/view?usp=sharing))**  
Datos simulados, preparación de variables, separación de entrenamiento y prueba, regresión lineal, comparación con un modelo base y gráficos.

### Cómo ejecutarlo en Google Colab

1. Subir estos cuatro archivos al repositorio de GitHub.
2. Entrar en [Google Colab](https://colab.research.google.com/) → **GitHub** → pegar el enlace del repositorio.
3. Abrir `03_Pipeline_Busqueda.ipynb` y ejecutar **Entorno de ejecución → Ejecutar todas**.
4. Hacer lo mismo con `04_Pipeline_Regresion.ipynb`.
5. Cambiar los valores de la ficha y de la consulta final para observar otros resultados.

Los notebooks usan `numpy`, `pandas`, `matplotlib` y `scikit-learn`, bibliotecas disponibles habitualmente en Colab. No se necesitan archivos CSV externos ni claves de acceso.

### Evidencias que mostraría en la exposición

| Parte | Evidencia |
|---|---|
| Caso | Problema, variables y alcance documentados en este README |
| Estados | Diagrama y tabla de transiciones en `02_Espacio_de_Estados.md` |
| Búsqueda | Secuencia de estados visitados, ruta y registro más cercano |
| Predicción | MAE, RMSE, R², comparación con línea base y gráficos |

### Lo que aprendí

Este ejercicio me ayudó a separar dos ideas que suelen confundirse. **Buscar una solución** significa recorrer estados posibles aplicando reglas; **predecir** significa ajustar un modelo a ejemplos. En ambos casos es clave revisar las entradas y no presentar un resultado de prueba como si fuera una conclusión sobre la vida real.

