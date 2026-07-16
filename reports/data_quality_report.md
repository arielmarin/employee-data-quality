# Employee Data Quality Assessment Report
## 1. Introducción

Este informe documenta el proceso de evaluación, limpieza y validación realizado sobre el **Messy Employee Dataset**, un conjunto de datos compuesto por información de empleados que presenta diversos problemas de calidad distribuidos entre sus variables.

El objetivo del proyecto fue identificar inconsistencias en la estructura y el contenido del dataset, definir una estrategia de limpieza para cada problema detectado y generar una versión preparada para su utilización en análisis exploratorios y dashboards.

Durante el proceso se analizaron aspectos como la presencia de valores faltantes, tipos de datos incorrectos, formatos inconsistentes y variables que contenían más de un atributo. Cada decisión de limpieza fue tomada a partir del análisis de las características propias del dataset, procurando preservar la información original y minimizar el impacto sobre los datos.

El resultado obtenido fue un conjunto de datos consistente, correctamente estructurado y listo para ser utilizado en las siguientes etapas del proyecto.

## 2. Objetivos

El objetivo principal de este proyecto fue preparar el dataset para su utilización en etapas posteriores de análisis, garantizando que la información fuera consistente y confiable.

Para alcanzar este objetivo se plantearon las siguientes tareas:

- Analizar la estructura general del dataset.
- Detectar problemas de calidad en cada variable.
- Definir una estrategia de limpieza para cada hallazgo.
- Aplicar las transformaciones necesarias.
- Validar que el dataset resultante fuera consistente y estuviera listo para el análisis exploratorio.

## 3. Descripción del Dataset

El proyecto se desarrolló utilizando el **Messy Employee Dataset**, un conjunto de datos diseñado para contener problemas habituales de calidad que pueden encontrarse durante la preparación de información para análisis.

El dataset está compuesto por **1020 registros** y **12 columnas**, que incluyen información relacionada con la identificación de empleados, departamento, región, salario, desempeño, modalidad de trabajo y fecha de ingreso.

Durante la inspección inicial se identificaron distintos problemas de calidad distribuidos entre varias columnas. Entre ellos se encontraron valores faltantes, tipos de datos incorrectos, formatos inconsistentes y variables que almacenaban múltiples atributos dentro de una misma columna.

Estas características hicieron del dataset un caso adecuado para desarrollar un proceso completo de evaluación, limpieza y validación de datos.

### Características Generales del Dataset

| Característica             | Valor                                        |
|----------------------------|----------------------------------------------|
| Nombre del dataset         | Messy Employee Dataset                       |
| Registros                  | 1020                                         |
| Columnas originales        | 12                                           |
| Variables numéricas        | Age, Salary                                  |
| Variables categóricas      | Department_Region, Status, Performance_Score |
| Variables de identificación| Employee_ID, Email, Phone                    |
| Variable temporal          | Join_Date                                    |
| Variable booleana          | Remote_Work                                  |

## 4. Metodología

El desarrollo del proyecto se dividió en cuatro etapas principales.

### 1. Data Profiling

Se realizó una exploración inicial del dataset para conocer su estructura, identificar valores faltantes, revisar los tipos de datos y detectar posibles inconsistencias.

### 2. Data Quality Assessment

Se analizó cada variable de forma individual para identificar problemas de calidad y definir la estrategia de limpieza más adecuada.

### 3. Data Cleaning

Se aplicaron las transformaciones necesarias para corregir los problemas detectados, incluyendo la conversión de tipos de datos, normalización de columnas y tratamiento de valores faltantes.

### 4. Data Validation

Finalmente se verificó que todas las transformaciones se hubieran aplicado correctamente y que el dataset estuviera preparado para las siguientes etapas del proyecto.

## 5. Evaluación Inicial de la Calidad de los Datos

Antes de realizar cualquier transformación, se llevó a cabo un proceso de Data Profiling con el objetivo de conocer el estado inicial del Messy Employee Dataset e identificar los problemas que debían resolverse antes de iniciar el análisis exploratorio.

La evaluación se realizó utilizando Pandas para inspeccionar la estructura del dataset y Missingno para visualizar la distribución de los valores faltantes. Durante esta etapa se analizaron la cantidad de registros y columnas, los tipos de datos, las estadísticas descriptivas, la presencia de valores nulos, la existencia de registros duplicados y la consistencia de las variables.

Este análisis permitió elaborar un diagnóstico inicial y definir las acciones de limpieza que se aplicarían posteriormente.

### 5.1 Estructura General del Dataset

La inspección inicial mostró que el dataset estaba compuesto por **1020** registros y **12** columnas, que incluían variables numéricas, categóricas, booleanas y de identificación.

Si bien la estructura general era consistente, se detectaron algunas columnas con tipos de datos inadecuados para el tipo de información que almacenaban. Entre ellas se encontraban **Join_Date**, cargada como texto, y Phone, almacenada como un valor numérico a pesar de representar un identificador.

### 5.2 Estadísticas Descriptivas

Se analizaron las variables **Age** y **Salary** mediante estadísticas descriptivas para comprender su distribución y evaluar la presencia de posibles anomalías.

Este análisis fue determinante para seleccionar la estrategia de imputación de los valores faltantes. En particular, permitió observar que Salary presentaba una distribución relativamente equilibrada, mientras que Age estaba compuesta por un conjunto reducido de valores discretos, lo que justificó utilizar criterios diferentes para cada variable.

### 5.3 Análisis de Valores Faltantes

Uno de los aspectos más importantes de la evaluación consistió en identificar la presencia de valores faltantes dentro del conjunto de datos.

Para ello se calculó la cantidad de registros incompletos por columna y posteriormente se realizó una visualización gráfica de la distribución de dichos valores utilizando la biblioteca **Missingno**.

El análisis mostró que las columnas **Age** y **Salary** presentaban información incompleta, aunque con una magnitud diferente.

En el caso de **Salary**, la cantidad de valores faltantes era reducida y la distribución de la variable permitía considerar técnicas de imputación basadas en medidas estadísticas.

Por otro lado, la columna **Age** presentaba una proporción considerablemente mayor de valores faltantes, por lo que la estrategia de tratamiento debía contemplar la naturaleza discreta de la variable y minimizar el impacto sobre su distribución original.

La visualización de los valores faltantes permitió confirmar que el problema se encontraba concentrado únicamente en determinadas columnas y no representaba una pérdida generalizada de información dentro del dataset.

### 5.4 Detección de Registros Duplicados

También se verificó la existencia de registros duplicados mediante la función duplicated() de Pandas.

La inspección confirmó que el dataset no presentaba filas duplicadas, por lo que no fue necesario aplicar procesos de eliminación ni consolidación de registros.

### 5.5 Evaluación General

La evaluación inicial permitió identificar los principales problemas de calidad presentes en el dataset y establecer el plan de trabajo para la etapa de limpieza.

Los hallazgos más relevantes fueron:

- Valores faltantes en las columnas Age y Salary.
- Tipos de datos inadecuados en Join_Date y Phone.
- Una columna compuesta (Department_Region) que almacenaba dos atributos diferentes.
- Un formato inconsistente en la columna Phone, donde todos los registros incluían un signo negativo.

Con este diagnóstico fue posible definir una estrategia de limpieza específica para cada problema, asegurando que las transformaciones realizadas respondieran a las características del dataset y no a decisiones arbitrarias.

## 6. Hallazgos de Calidad de Datos

Como resultado del proceso de evaluación inicial se identificaron distintos problemas que afectaban la calidad general del conjunto de datos. Los hallazgos detectados no comprometían la totalidad del dataset, pero sí podían influir en la precisión de futuros análisis, dificultar el tratamiento de determinadas variables o limitar la capacidad de obtener información confiable.

Cada uno de los problemas fue analizado de manera individual con el objetivo de seleccionar la estrategia de corrección más adecuada, procurando preservar la integridad de la información y evitando introducir modificaciones innecesarias.

A continuación, se describen los principales hallazgos identificados durante la evaluación.

### 6.1 Columna Join_Date

Durante la inspección inicial se observó que la variable **Join_Date**, correspondiente a la fecha de ingreso de cada empleado, se encontraba almacenada como una cadena de texto (*string*).

Si bien la información era legible para una persona, este formato impedía aprovechar las funcionalidades de análisis temporal disponibles en Pandas, tales como el cálculo de antigüedad, la extracción de componentes de la fecha (año, mes o día) o la realización de análisis cronológicos.

Se determinó que esta situación correspondía a un problema de tipo de dato y no de contenido, por lo que la estrategia definida consistió en convertir la columna al tipo **datetime**, preservando toda la información original.

### 6.2 Columna Department_Region

La variable **Department_Region** almacenaba simultáneamente dos atributos distintos dentro de una única columna: el departamento al que pertenecía el empleado y la región geográfica donde desempeñaba sus funciones.

Desde una perspectiva de modelado de datos, esta estructura no resulta adecuada, ya que cada columna debe representar una única variable.

Mantener ambos atributos combinados dificulta la realización de análisis independientes, como calcular la cantidad de empleados por departamento, comparar salarios entre regiones o construir indicadores específicos para cada dimensión.

Durante la evaluación se verificó que ambos atributos se encontraban separados mediante un guion ("-"), lo que permitió definir una estrategia de normalización consistente basada en la separación de la información en dos nuevas columnas independientes denominadas **Department** y **Region**.

Una vez verificada la correcta separación de los datos, la columna original podría eliminarse sin pérdida de información.

### 6.3 Columna Salary

El análisis de la variable **Salary** permitió identificar la presencia de valores faltantes.

Para definir la estrategia de tratamiento se estudió previamente la distribución de los salarios mediante estadísticas descriptivas, observándose una distribución relativamente equilibrada y un porcentaje reducido de registros incompletos respecto del total del dataset.

Considerando estas características, se concluyó que la imputación mediante la media constituía una alternativa adecuada, ya que permitía conservar la totalidad de los registros sin introducir un sesgo significativo en la distribución de la variable.

### 6.4 Columna Age

La variable **Age** también presentaba valores faltantes, aunque en una proporción considerablemente mayor que la observada en la columna Salary.

Durante el análisis se verificó que las edades disponibles correspondían exclusivamente a valores discretos y que la distribución de la variable hacía desaconsejable utilizar la media como método de imputación, ya que ello habría generado edades con valores decimales poco representativos.

Asimismo, eliminar los registros incompletos habría implicado descartar aproximadamente una quinta parte del conjunto de datos, reduciendo innecesariamente la información disponible.

Por estos motivos se decidió utilizar la mediana como criterio de imputación, preservando la coherencia de la variable y minimizando el impacto sobre su distribución original.

### 6.5 Columna Phone

Durante la evaluación se observó que la variable **Phone** se encontraba almacenada como un valor numérico entero.

Sin embargo, un número telefónico constituye un identificador y no una magnitud susceptible de operaciones matemáticas. Por este motivo, mantener la variable como un dato numérico podía inducir interpretaciones incorrectas y provocar la pérdida de información relacionada con su formato.

Adicionalmente, se detectó que todos los registros presentaban un signo negativo al inicio del número telefónico.

Debido a que este comportamiento se repetía de forma sistemática en la totalidad del conjunto de datos, se concluyó que correspondía a un error de formato y no a una característica válida de la información.

En consecuencia, se definió convertir la variable al tipo **string** y eliminar únicamente el carácter negativo inicial, conservando el resto del identificador sin modificaciones.

### 6.6 Evaluación General de los Hallazgos

El análisis detallado de las variables permitió comprobar que los problemas detectados respondían principalmente a cuestiones relacionadas con la estructura y el formato de los datos, más que a errores de contenido.

La mayoría de las inconsistencias podían resolverse mediante transformaciones controladas sin necesidad de eliminar registros, lo que permitió conservar la totalidad del conjunto de datos para etapas posteriores del proyecto.

Los hallazgos identificados sirvieron como base para definir el proceso de limpieza descrito en la siguiente sección.

## 7. Proceso de Limpieza de Datos

Una vez finalizada la evaluación inicial, se aplicó un proceso de limpieza para corregir las inconsistencias detectadas en el Messy Employee Dataset. Cada transformación respondió a un problema identificado durante la etapa de Data Profiling y fue implementada procurando preservar la integridad de la información y evitar modificaciones innecesarias.

| Problema                | Solución aplicada               |
| ----------------------- | ------------------------------- |
| Join_Date como texto    | Conversión a datetime           |
| Phone como entero       | Conversión a string             |
| Signo negativo en Phone | Eliminado                       |
| Department_Region       | Separada en Department y Region |
| Salary con 24 nulos     | Imputación por media            |
| Age con 211 nulos       | Imputación por mediana          |

Las acciones realizadas se describen a continuación.

### Conversión de tipos de datos

Se transformó la columna **Join_Date** al tipo de dato **datetime**, permitiendo utilizar herramientas de análisis temporal y garantizando que la información fuera interpretada correctamente por las bibliotecas de análisis de datos.

Asimismo, la columna **Phone** fue convertida al tipo **string**, ya que representa un identificador y no una variable numérica.

### Normalización de la estructura del dataset

La columna **Department_Region** fue dividida en dos nuevas variables independientes: **Department** y **Region**.

Esta transformación permitió mejorar la organización del conjunto de datos y facilitar futuros análisis segmentados por área de trabajo o ubicación geográfica.

Una vez comprobada la correcta separación de la información, la columna original fue eliminada para evitar redundancias.

### Tratamiento de valores faltantes

Los valores faltantes presentes en la columna **Salary** fueron reemplazados utilizando la media de la distribución, considerando que el porcentaje de registros incompletos era reducido y que esta medida representaba adecuadamente el comportamiento general de la variable.

En el caso de la columna **Age**, se utilizó la mediana como criterio de imputación debido a la naturaleza discreta de la variable y a la mayor proporción de valores faltantes observada durante el análisis inicial.

### Corrección de formatos

Finalmente, se eliminó el signo negativo presente al inicio de todos los registros de la columna **Phone**, al identificarse como un error sistemático de formato.

Esta corrección permitió conservar íntegramente los identificadores telefónicos manteniendo un formato consistente para toda la variable.

Al finalizar esta etapa, el conjunto de datos presentaba una estructura más consistente, variables correctamente tipadas y ausencia de valores faltantes en las columnas analizadas, quedando preparado para la fase de validación.

## 8. Validación del Dataset

Finalizado el proceso de limpieza, se realizó una etapa de validación con el objetivo de comprobar que las transformaciones aplicadas hubieran resuelto correctamente los problemas identificados durante la evaluación inicial.

La validación constituye una fase fundamental dentro del proceso de preparación de datos, ya que permite confirmar que las modificaciones realizadas no introdujeron nuevas inconsistencias y que el conjunto de datos se encuentra en condiciones de ser utilizado para análisis posteriores.

Para ello se revisaron nuevamente los principales indicadores de calidad evaluados al inicio del proyecto.

### 8.1 Verificación de Tipos de Datos

En primer lugar, se comprobó que todas las variables presentaran un tipo de dato consistente con la naturaleza de la información almacenada.

Como resultado de esta verificación se confirmó que:

- La columna **Join_Date** fue convertida correctamente al tipo **datetime**, permitiendo realizar análisis temporales.
- La columna **Phone** pasó a almacenarse como **string**, representando adecuadamente un identificador y evitando interpretaciones numéricas incorrectas.
- La columna **Age** quedó almacenada como un valor entero, eliminando la posibilidad de obtener edades con valores decimales.
- Las nuevas columnas **Department** y **Region** fueron creadas correctamente a partir de la variable compuesta original.

Esta validación permitió asegurar que la estructura del dataset respondiera a criterios adecuados de modelado y análisis.

### 8.2 Verificación de Valores Faltantes

Posteriormente se realizó una nueva inspección de los valores faltantes presentes en el conjunto de datos.

La revisión confirmó que todas las columnas del dataset quedaron libres de valores nulos luego del proceso de imputación y transformación.

Este resultado garantiza que futuras consultas, cálculos estadísticos o visualizaciones no se vean afectadas por información incompleta.

### 8.3 Verificación de Registros Duplicados

También se verificó nuevamente la existencia de registros duplicados.

La inspección confirmó que el conjunto de datos continuó sin presentar filas duplicadas luego de las transformaciones realizadas, preservando la integridad de la información original.

### 8.4 Validación de la Estructura

Finalmente se comprobó que la estructura general del dataset fuera consistente con los objetivos planteados al inicio del proyecto.

En esta etapa se verificó que:

- La información originalmente contenida en **Department_Region** hubiera sido preservada correctamente mediante las nuevas columnas **Department** y **Region**.
- Las categorías presentes en las variables categóricas permanecieran consistentes.
- Las transformaciones aplicadas no modificaran la cantidad de registros del conjunto de datos.

Como resultado de esta revisión se concluyó que el proceso de limpieza fue implementado correctamente y que el conjunto de datos se encontraba preparado para ser utilizado en las siguientes etapas del proyecto.

## 9. Resultados Obtenidos

Luego del proceso de evaluación, limpieza y validación, el dataset quedó preparado para su utilización en análisis exploratorios y visualizaciones, manteniendo la totalidad de los registros originales.

Las transformaciones realizadas corrigieron los problemas de calidad detectados durante el diagnóstico inicial y mejoraron la estructura general del conjunto de datos sin alterar el significado de la información.

### Resumen de Resultados

| Aspecto Evaluado     | Estado Inicial                          | Estado Final         |
|----------------------|-----------------------------------------|----------------------|
| Registros            | 1020                                    | 1020                 |
| Columnas             | 12                                      | 13 (Department_Region normalizada en Department y Region) |
| Valores faltantes    | Age (211) y Salary (24)                 | Sin valores faltantes|
| Tipos de datos       | Join_Date y Phone con tipos inadecuados | Tipos corregidos     |
| Columnas compuestas  | Department_Region                       | Separada en Department y Region |
| Formato de Phone     | Entero con signo negativo               | Texto con formato consistente |
| Registros duplicados | No se detectaron                        | Sin modificaciones   |

Como resultado, se obtuvo un dataset consistente, correctamente estructurado y listo para ser utilizado en el análisis exploratorio y la construcción del dashboard.

## 10. Limitaciones del Proyecto

El proyecto se desarrolló sobre un dataset de práctica diseñado para contener problemas de calidad, por lo que no representa todas las situaciones que pueden presentarse en un entorno empresarial.

Las decisiones de limpieza, como la imputación de valores faltantes, se basaron en el análisis estadístico del dataset. En un escenario real, estas transformaciones deberían complementarse con reglas de negocio y conocimiento del dominio.

Además, el alcance del proyecto se limitó a la preparación y validación de los datos. No se abordaron procesos de integración con otras fuentes ni la automatización de la limpieza, aspectos que podrían incorporarse en trabajos futuros.

## 11. Conclusiones

El proyecto permitió desarrollar un proceso completo de evaluación, limpieza y validación sobre el *Messy Employee Dataset*, aplicando una metodología estructurada para mejorar la calidad de la información.

Durante el análisis se identificaron y corrigieron problemas relacionados con valores faltantes, tipos de datos inadecuados, formatos inconsistentes y una columna que combinaba múltiples atributos. Todas las decisiones de limpieza fueron tomadas a partir del análisis del propio dataset, procurando conservar la información original y garantizar su consistencia.

Como resultado, se obtuvo un conjunto de datos preparado para el desarrollo del Análisis Exploratorio de Datos (EDA) y la construcción de un dashboard, cumpliendo con el objetivo principal del proyecto y estableciendo una base confiable para las siguientes etapas del análisis.