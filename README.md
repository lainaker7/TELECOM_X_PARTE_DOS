🚀 README del Análisis de Predicción de Deserción de Clientes

Este cuaderno documenta un proceso completo de análisis de datos y modelado predictivo para identificar los factores que influyen en la deserción de clientes (churn).

📌 **1. Extracción y Carga del Archivo Tratado**
Comenzamos cargando un archivo CSV que contiene datos de clientes ya preprocesados. Este archivo es la base para nuestro análisis.

🔍**2. Análisis de la Utilidad de la Información**
Se realizó un análisis inicial para comprender la estructura de los datos, incluyendo tipos de datos y la cantidad de valores únicos por columna. Se identificó la columna ID_cliente como no útil para los modelos predictivos debido a sus valores únicos y se procedió a eliminarla.

✏️**3. Transformación de Variables con ONE-HOT-ENCODING**
Las variables categóricas fueron transformadas utilizando One-Hot Encoding para convertirlas en un formato numérico que los modelos de Machine Learning puedan procesar. Esto crea nuevas columnas binarias para cada categoría única.

⚖️** 4. Balanceo de Clases: Detección y Tratamiento**
Se analizó la proporción de clientes con y sin deserción. Se encontró un desbalance significativo (26.58% deserción vs 73.42% no deserción). Para mitigar este problema y asegurar que los modelos no se sesguen hacia la clase mayoritaria, se aplicó la técnica SMOTE (Synthetic Minority Over-sampling Technique) para igualar el número de muestras en ambas clases.

📊 **5. Estandarización de Características Numéricas**
Las características numéricas (Antiguedad, Cargos_mensuales, Cargos_totales) fueron estandarizadas utilizando StandardScaler. Esto asegura que todas las características tengan una escala similar (media de 0 y desviación estándar de 1), lo cual es crucial para modelos sensibles a la escala como la Regresión Logística y SVM.

🎯 **6. Correlación y Selección de Variables**
Se calculó y visualizó una matriz de correlación para entender las relaciones entre todas las variables. Luego, se examinaron específicamente las correlaciones de cada característica con la variable objetivo Deserción_Sí para identificar los predictores más fuertes. Se realizaron visualizaciones (boxplots) para entender la relación entre Antiguedad, Cargos_totales y la deserción.

🤖 **7. Modelado Predictivo**
*7.1. Separación de Datos*
Los datos balanceados y estandarizados (X_res_scaled, y_res) se dividieron en conjuntos de entrenamiento (70%) y prueba (30%) utilizando train_test_split, manteniendo la estratificación de clases.

*7.2. Entrenamiento y Evaluación de Modelos*
Se entrenaron y evaluaron dos modelos de clasificación:

Regresión Logística: Modelo lineal que se beneficia de la estandarización. Logró un rendimiento robusto con un Accuracy de 0.8551 y F1-Score de 0.8539.
Árbol de Decisión: Modelo basado en reglas. Inicialmente, se entrenó y luego se ajustó con max_depth=5 para controlar el sobreajuste. El modelo ajustado mostró un Accuracy de 0.8031 y F1-Score de 0.7995.
*7.3. Matrices de Confusión*
Se visualizaron las matrices de confusión para ambos modelos, permitiendo una comprensión detallada de los verdaderos positivos, verdaderos negativos, falsos positivos y falsos negativos.

✨ **8. Conclusión y Próximos Pasos**
El análisis identificó variables clave que impactan la deserción de clientes. Ambos modelos coincidieron en la importancia del Metodo_de_pago_Cheque electrónico y Antiguedad. Sin embargo, el Contrato_Mensual fue abrumadoramente dominante para el Árbol de Decisión, mientras que Cuentas_Diarias y Cargos_mensuales lo fueron para la Regresión Logística.

**Ideas o Próximos Pasos:**
Intervenciones por Método de Pago: Dada la fuerte influencia del Metodo_de_pago_Cheque electrónico, se recomienda diseñar estrategias específicas o incentivos para clientes que usan este método, buscando reducir la deserción.
Estrategias de Contrato: Se sugiere investigar a fondo por qué los Contrato_Mensual tienen una tasa de deserción tan alta y explorar ofertas para que estos clientes transicionen a contratos a más largo plazo.