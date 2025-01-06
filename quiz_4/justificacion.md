# Respuesta a las preguntas

## 1. Selección del dataset y su justificación

El dataset elegido analiza los **factores que afectan las calificaciones de estudiantes universitarios**. Este conjunto de datos incluye variables demográficas, socioeconómicas, académicas, y relacionadas con hábitos personales, tales como:

- **Demográficas**: Edad, género.
- **Socioeconómicas**: Nivel educativo de los padres, ingresos familiares.
- **Académicas**: Asistencia, participación en clase, horas de estudio, estilo de aprendizaje.
- **Personales**: Uso de redes sociales, participación deportiva, tutorías y mentorías.

### Justificación teórica

El rendimiento académico es una métrica clave para evaluar el éxito educativo, influenciado por factores personales, familiares y escolares. Según la teoría de la integración ecológica de Bronfenbrenner, múltiples sistemas interactúan en el desarrollo del estudiante, como el contexto familiar (ingreso, educación de los padres) y escolar (tipo de escuela, tutorías). Este dataset es adecuado para modelar esta interacción porque incluye una combinación rica de variables cuantitativas y cualitativas que permiten analizar los factores determinantes del éxito estudiantil.

### Exploración inicial

El dataset contiene:

- **35 columnas**, mezclando variables categóricas y numéricas.
- **Valores faltantes** en columnas clave como calificaciones anteriores y participación en clase.
- **Problemas de calidad de datos**, como categorías no uniformes y valores nulos.

Estas características hacen que este dataset sea un reto interesante para el análisis y la aplicación de modelos de aprendizaje profundo.

---

## 2. Problema a resolver

### Definición del problema

Se busca predecir la **categoría final de la calificación del estudiante** (A, B, C, D, F), utilizando los factores proporcionados en el dataset. Este problema pertenece a la **clasificación supervisada**.

### Relevancia

La predicción de calificaciones permite identificar estudiantes en riesgo y desarrollar estrategias personalizadas para mejorar su desempeño, alineándose con principios de educación inclusiva y equitativa.

---

## 3. Tipo de red neuronal seleccionada

### Red neuronal seleccionada

Para resolver este problema, se utilizará una **Multilayer Perceptron (MLP)**. Esta red es adecuada porque:

- Maneja datos tabulares con variables categóricas y numéricas.
- Permite capturar interacciones no lineales entre los factores que afectan las calificaciones.
- Es eficaz para tareas de clasificación supervisada.

### Descripción del modelo

1. **Entrada**:

   - Se normalizan las variables numéricas.
   - Las variables categóricas se codifican utilizando embeddings o one-hot encoding.

2. **Arquitectura**:

   - **Capas ocultas**: Dos o tres capas densas con funciones de activación ReLU para capturar interacciones complejas.
   - **Capas de dropout** para evitar el sobreajuste.

3. **Salida**:

   - Una capa densa con activación softmax que produce probabilidades para cada categoría (A, B, C, D, F).

4. **Optimización**:
   - Se utiliza la entropía cruzada categórica como función de pérdida.
   - Optimizador Adam para una convergencia rápida y estable.

### Resolución del problema

La red aprenderá patrones complejos en los datos, como:

- **Relaciones no lineales**: Por ejemplo, cómo la combinación de asistencia alta y horas de estudio bajas afecta las calificaciones.
- **Interacciones categóricas**: Cómo el tipo de escuela interactúa con el nivel de ingresos familiares.

La implementación del modelo permitirá no solo predecir calificaciones, sino también interpretar qué factores tienen mayor peso en el rendimiento académico, brindando insights para intervenciones educativas.

---
