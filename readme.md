# Proyecto: Clasificación de Notas de Estudiantes Usando Redes Neuronales Artificiales

## Integrantes

Brandon Trigueros - C17899
Milton Sojo - C17546

## Ejecutar el código

Comando para instalar dependencias:

- Crear un entorno virtual con virtualenv -p python3 venv

pip install -r requirements.txt

## Descripción del Proyecto

Este proyecto implementa una red neuronal feedforward para predecir las notas de los estudiantes basado en un conjunto de características relacionadas con factores académicos, sociales y personales. El objetivo principal es mejorar la precisión en la clasificación de las notas, identificando patrones significativos en los datos.

---

## Dataset

- **Nombre**: Factors Affecting University Student Grades
- **Características**:
  - Variables académicas como `Attendance`, `Previous_Grades`, `Study_Hours`.
  - Factores sociales como `Parental_Involvement`, `Sports_Participation`.
  - Factores personales como `Self_Esteem`, `Motivation`.

### Preprocesamiento

1. **Imputación de Valores Faltantes**:

   - Valores numéricos imputados con la mediana.
   - Valores categóricos imputados con "Unknown".

2. **Codificación**:

   - Variables categóricas codificadas numéricamente.
   - Codificación del objetivo (`Grades`) usando `LabelEncoder`.

3. **Ingeniería de Características**:

   - Creación de interacciones como `Effective_Study_Time = Attendance * Study_Hours`.
   - Generación de características polinomiales (grado 2).

4. **Reducción de Dimensionalidad**:

   - PCA (Análisis de Componentes Principales) para seleccionar las 15 principales componentes.

5. **Balanceo de Clases**:
   - Aplicación de Borderline SMOTE para mejorar la distribución de clases.

---

## Tipo de Red Utilizada

- **Tipo**: Feedforward Neural Network (FFNN)
- **Diseño Final**:
  - Capa de entrada: 256 neuronas, función de activación `swish`.
  - Capas ocultas:
    - Primera capa: 128 neuronas, activación `swish`, regularización L2 (0.01), y dropout (0.4).
    - Segunda capa: 64 neuronas, activación `swish` y dropout (0.3).
  - Capa de salida: Softmax para la clasificación multiclase.
  - Optimizador: Adam (`learning_rate=0.0001`).
  - Pérdida: `sparse_categorical_crossentropy`.

---

## Entrenamiento del Modelo

1. **Configuración**:

   - Dividido en 80% entrenamiento y 20% prueba.
   - Validación interna: 20% del conjunto de entrenamiento.
   - Uso de `EarlyStopping` para prevenir sobreajuste.

2. **Hiperparámetros**:

   - Épocas: 400 (con parada anticipada).
   - Tamaño del batch: 64.
   - Peso de clases: Generado automáticamente para manejar desbalance.

3. **Resultados del Entrenamiento**:
   - `accuracy` de entrenamiento: 55%
   - `val_accuracy`: 40%

---

## Pruebas Realizadas

### Configuración

- **Métricas de Evaluación**:
  - Precisión (`precision`).
  - Recall (`recall`).
  - F1-Score.
  - Matriz de Confusión.

### Resultados Finales

- **Test Accuracy**: 40%
- **Classification Report**:

| Clase | Precisión | Recall | F1-Score | Soporte |
| ----- | --------- | ------ | -------- | ------- |
| A     | 0.45      | 0.38   | 0.41     | 500     |
| B     | 0.40      | 0.45   | 0.42     | 500     |
| C     | 0.35      | 0.37   | 0.36     | 500     |

- **Matriz de Confusión**:
  ```
  [[190  160  150]
   [140  225  135]
   [160  170  170]]
  ```

---

## Conclusión

El modelo logró un `accuracy` final de **40%**, mejorando significativamente respecto a intentos iniciales (30-33%). Este resultado se atribuye a:

1. Mejor representación de características (uso de PCA y SMOTE).
2. Arquitectura optimizada con regularización y funciones de activación avanzadas.
3. Uso de hiperparámetros ajustados como tasas de aprendizaje pequeñas y mayor tamaño de batch.

---

## Archivos Adjuntos

- **Notebook**: Incluye todo el código implementado.
- **Modelo Guardado**: `best_model.keras`.
