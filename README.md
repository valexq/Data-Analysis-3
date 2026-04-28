# HR Analytics - Análisis de Recursos Humanos

## Objetivo
El presente análisis tiene como objetivo identificar patrones, tendencias y relaciones estadísticas que permitan detectar 
anticipadamente qué empleados tienen mayor riesgo de irse y reducir la rotación, proporcionando al área de Recursos Humanos 
información basada en evidencia para tomar decisiones estratégicas de retención de sus empleados.

## Dataset

- Nombre: `HR Analytics`.
- Fuente: Kaggle.
- Enlace: https://www.kaggle.com/datasets/giripujar/hr-analytics
- Registros: 14999.
- Variables originales: 10.
- Variable objetivo: `left`, donde `1` significa que el empleado se va y `0` que permanece.

## Integrantes

Grupo 5

| Nombre | Fase principal | GitHub |
| --- | --- | --- |
| Vanessa Alfaro | Fases 1 y 2 | `@valexq` |
| Juan Manuel Valencia | Fase 3 | `@Juanchos2905` |
| Ziuvar Ruiz | Fases 4 y 5 | `@ziuvar` |
| Juan Cardona | Fase 6 | `@jcardser` |

## Estructura del repositorio

```text
Data-Analysis-3/
├─ data/
│  ├─ raw_hr_analytics.csv
│  ├─ clean_hr_analytics.csv
│  ├─ department_metrics.csv
│  ├─ salary_metrics.csv
│  ├─ satisfaction_metrics.csv
│  ├─ tenure_metrics.csv
│  ├─ workload_metrics.csv
│  ├─ dashboard_combo_metrics.csv
│  └─ kpi_definitions.csv
├─ notebooks/
│  ├─ 01_eda_preparacion.ipynb
│  ├─ 02_hipotesis_pruebas.ipynb
│  └─ 03_kpis_export_dashboard.ipynb
├─ dashboard/
│  ├─ hr_dashboard.pbix
│  └─ visualizaciones/
├─ reports/
│  ├─ auditoria_limpieza.csv
│  ├─ resultados_hipotesis.csv
│  └─ resumen_ejecutivo.md
├─ README.md
└─ requirements.txt
```

## Contexto del dataset


El proyecto utiliza el conjunto de datos HR Analytics disponible en Kaggle, que contiene información de 14,999 empleados con 
10 variables, incluyendo nivel de satisfacción, desempeño en la última evaluación, número de proyectos, horas promedio trabajadas 
al mes, años en la compañía, departamento, salario, promoción en los últimos cinco años y si han dejado la empresa o no (variable 
de rotación). Cada fila representa a un empleado y permite analizar cómo diferentes características laborales y 
organizacionales se relacionan con la decisión de permanecer en la empresa o abandonarla.

## Problema de análisis

La empresa está enfrentando una alta rotación de empleados en los últimos meses. Se sospecha que algunos departamentos presentan condiciones 
de trabajo más exigentes, lo que podría estar impulsando la salida de personal. Además, se plantea que el salario y el nivel de satisfacción pueden 
estar influyendo en la decisión de renunciar. Este fenómeno puede generar una sobrecarga laboral para los empleados que permanecen, aumentando el estrés 
y el riesgo de insatisfacción, así como retrasos en proyectos, mayores costos de adaptación de nuevos trabajadores y un impacto negativo en la calidad del 
servicio ofrecido por la organización.


## Metodologia

1. Se definió el problema de negocio y se formularon 4 preguntas clave sobre rotación, satisfacción, salario y carga laboral.
2. Se plantearon 4 hipótesis con H0 y H1 explícitas, justificadas desde negocio y validadas con pruebas de Pearson, chi-cuadrado 
y Spearman con α = 0.05.
3. Se limpió y transformó la base original sin cambiar el número de registros. No se detectaron valores faltantes. Los duplicados 
exactos se conservaron y se marcaron en `duplicate_exact_record` por falta de identificador único.
4. Se construyeron tablas agregadas, KPIs y un dashboard ejecutivo en Power BI con el archivo principal `dashboard/hr_dashboard.pbix`.
5. Los entregables se regeneran desde los notebooks: `01_eda_preparacion.ipynb`, `02_hipotesis_pruebas.ipynb` y 
`03_kpis_export_dashboard.ipynb`.

## Preguntas clave:

1. ¿Los departamentos con mayor promedio de horas mensuales trabajadas son más propensos a la baja de sus empleados?
2. ¿Existe una relación entre el promedio de horas mensuales trabajadas y el nivel de satisfacción laboral?
3. ¿Cómo se relaciona el nivel de satisfacción laboral con la rotación de empleados?
4. ¿Cómo se relaciona el salario con la rotación de empleados?



### Hipótesis 1: Horas mensuales vs satisfacción

| Campo | Detalle |
|-------|---------|
| **H0** | No existe relación lineal entre el promedio de horas mensuales trabajadas y el nivel de satisfacción de los empleados |
| **H1** | A más horas mensuales trabajadas, menor es la satisfacción de los empleados |
| **Variables** | `average_monthly_hours` (numérica continua) y `satisfaction_level` (numérica continua) |
| **Tipo de variables** | Numéricas |
| **Prueba estadística** | Correlación de Pearson |

**Justificación:** Esta hipótesis es relevante porque permite identificar si la carga de trabajo excesiva está afectando 
directamente la satisfacción laboral, lo que podría ser una señal temprana de burnout. Si se confirma, el área de Recursos 
Humanos podría proponer a los líderes de cada área redistribuir la carga de trabajo y revisar el número de proyectos asignados 
con el fin de prevenir el burnout y reducir el riesgo de rotación.
> **Nota:** Esta hipótesis actúa como paso previo a la H2: si se confirma que más horas reducen la satisfacción, y la H2 
confirma que baja satisfacción aumenta la rotación, entonces la carga laboral sería un factor indirecto de rotación.

### Hipótesis 2: Satisfacción vs rotación

| Campo | Detalle |
|-------|---------|
| **H0** | No existe asociación entre el nivel de satisfacción del empleado y la rotación |
| **H1** | Los empleados con un nivel de satisfacción por debajo de la mediana tienen mayor probabilidad de abandonar la empresa |
| **Variables** | `satisfaction_level` (discretizada en bajo/alto según mediana = 0.64) y `left` (0 = se queda, 1 = se va) |
| **Tipo de variables** | Categóricas |
| **Prueba estadística** | Chi-cuadrado de independencia |

**Justificación:** Esta hipótesis es relevante porque permite identificar anticipadamente qué empleados tienen baja satisfacción 
y mayor riesgo de irse, ya que puede costarle a la empresa tiempo de reclutamiento, entrenamiento del nuevo empleado y productividad 
perdida mientras el puesto está vacío. Si se confirma, el área de Recursos Humanos podría implementar programas de bienestar, 
bonificaciones y/o reconocimientos con el fin de mejorar la satisfacción del empleado.

### Hipótesis 3: Salario vs rotación

| Campo | Detalle |
|-------|---------|
| **H0** | No existe asociación entre el salario y la rotación |
| **H1** | Los empleados con salario bajo tienen mayor probabilidad de abandonar la empresa que los empleados con salario medio y alto |
| **Variables** | `salary` (bajo/medio/alto) y `left` (0 = se queda, 1 = se va) |
| **Tipo de variables** | Categóricas |
| **Prueba estadística** | Chi-cuadrado de independencia |

**Justificación:** Esta hipótesis es relevante porque permite identificar qué tipo de salario reciben los empleados que se 
quedan en comparación con los que se van, lo que refleja si la empresa es competitiva en el mercado laboral. Si se confirma, 
el área de Recursos Humanos podría implementar ajustes de compensación por mercado y política de incrementos salariales 
periódicos con el fin de reducir la rotación.

### Hipótesis 4: Horas promedio departamentales vs rotación

| Campo | Detalle |
|-------|---------|
| **H0** | No existe una relación monótona estadísticamente significativa entre las horas promedio departamentales y la rotación departamental |
| **H1** | Existe una relación monótona positiva estadísticamente significativa entre las horas promedio departamentales y la rotación departamental |
| **Variables** | `department_label`, `average_monthly_hours` y `left` agregadas por departamento |
| **Tipo de variables** | Numéricas agregadas |
| **Prueba estadística** | Correlación de Spearman |

**Justificación:** Permite validar si la sobrecarga operativa por departamento explica la salida y si conviene intervenir 
equipos específicos. Si se confirma, RRHH podría alertar a los líderes de cada área sobre la distribución de carga de trabajo.



## Trazabilidad de entregables:

| Entregable | Archivo base | Como se obtiene |
| --- | --- | --- |
| Dataset limpio | `data/clean_hr_analytics.csv` | Se genera desde `data/raw_hr_analytics.csv` en `01_eda_preparacion.ipynb`. |
| Resultados estadisticos | `reports/resultados_hipotesis.csv` | Se generan en `02_hipotesis_pruebas.ipynb`. H4 se calcula con promedios exactos por departamento antes del redondeo. |
| KPIs de negocio | `data/kpi_definitions.csv` | Se generan en `03_kpis_export_dashboard.ipynb` con justificacion de negocio, relacion con hipotesis e indicador de soporte en el dashboard. |
| Dashboard ejecutivo | `dashboard/hr_dashboard.pbix` | Se construye en Power BI con `data/clean_hr_analytics.csv`, sin cambiar nombres de variables ya usadas. |

## Resultados

### Hipótesis validadas

| Hipótesis | Prueba | Resultado | Decisión |
|-----------|--------|-----------|----------|
| H1: A más horas mensuales, menor satisfacción | Pearson | r = -0.02, p = 0.014 | Rechazar H0 |
| H2: Baja satisfacción aumenta la rotación | Chi-cuadrado | χ² = 1101.57, gl = 1, p < 0.05 | Rechazar H0 |
| H3: Salario bajo aumenta la rotación | Chi-cuadrado | χ² = 381.22, gl = 2, p < 0.05 | Rechazar H0 |
| H4: Departamentos con más horas tienen mayor rotación | Spearman | rho = -0.15, p = 0.676 | No rechazar H0 |


### KPIs principales:

| KPI | Valor | Relación con hipótesis | Interpretación                                                                             |
| --- | ---: |------------------------|--------------------------------------------------------------------------------------------|
| Tasa de rotacion general | 23.81% | H2, H3 y H4            | Resume el nivel total de salida y sirve como indicador ejecutivo principal.                |
| Satisfaccion promedio | 0.613 | H1 y H2                | El nivel medio de satisfacción es moderado y debe vigilarse junto con la rotacion.         |
| Horas mensuales promedio | 201.1 horas | H1 y H4                | Monitorea la carga laboral agregada como variable operativa de contexto.                   |
| Rotacion con satisfaccion baja | 35.61% | H2                     | Identifica el segmento prioritario para acciones de clima y retención.                     |
| Brecha de rotacion por satisfaccion | 23.10 p.p. | H2                     | Cuantifica el impacto de la satisfaccion en la salida y facilita priorizar intervenciones. |
| Rotacion con salario bajo | 29.69% | H3                     | Mide el riesgo de fuga en el segmento mas sensible a compensación.                         |
| Brecha salario bajo vs alto | 23.06 p.p. | H3                     | Evidencia una brecha fuerte de retención asociada al nivel salarial.                       |
| Rotacion en alta carga laboral | 37.31% | H1 y H4                | Activa una alerta operativa sobre equipos con exigencia alta.                              |

### Visualizaciones centrales del dashboard:

- Rotación por departamento.
- Rotación por satisfaccion.
- Rotación por salario.
- Horas mensuales vs satisfacción.
- Rotación por carga laboral.
- Matriz ejecutiva por departamento.

### Hallazgos principales

- Aunque se esperaba que más horas trabajadas redujeran la satisfacción, la correlación encontrada fue muy débil (r = -0.02), 
lo que sugiere que la carga laboral medida en horas no es el principal driver de insatisfacción en esta empresa.
- Se observa una asociación significativa entre satisfacción y rotación (χ² = 1101.57, p < 0.05). Los empleados con satisfacción 
baja tienen aproximadamente el triple de probabilidad de abandonar la empresa frente a quienes tienen satisfacción alta (35.6% vs 12.5%).
- Se observa una asociación significativa entre salario y rotación (χ² = 381.22, p < 0.05). Los empleados con salario bajo tienen 
aproximadamente 4.5 veces más probabilidad de abandonar la empresa que los de salario alto (29.7% vs 6.6%).
- No hay evidencia estadística para afirmar que los departamentos con más horas promedio sean los de mayor rotación (rho = -0.15, 
p = 0.676).

## Conclusiones

- Los factores más útiles para priorizar acciones de retención son la satisfacción baja y el salario bajo.
- Las horas mensuales deben leerse como variable de contexto y no como causa directa de la rotación.
- El dashboard ejecutivo permite seguir el riesgo de salida con trazabilidad directa entre hipótesis, KPIs y visualizaciones.
- Se recomienda que RRHH priorice intervenciones en empleados con satisfacción baja y salario bajo, ya que estos dos segmentos 
concentran el mayor riesgo de rotación según la evidencia estadística.
- El análisis tiene limitaciones: no hay identificador único de empleado, no hay fechas y no se puede afirmar causalidad, solo 
asociación estadística entre variables.
