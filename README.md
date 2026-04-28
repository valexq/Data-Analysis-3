# Proyecto: Business Intelligence para rotacion de empleados

## Objetivo

Analizar la rotacion de empleados del dataset **HR Analytics** para identificar factores asociados a la salida del personal y apoyar decisiones de retencion en Recursos Humanos.

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
│  ├─ capturas/
│  └─ visualizaciones/
├─ reports/
│  ├─ auditoria_limpieza.csv
│  ├─ resultados_hipotesis.csv
│  └─ resumen_ejecutivo.md
├─ README.md
└─ requirements.txt
```

## Contexto del dataset

El proyecto utiliza un conjunto de datos de analitica de Recursos Humanos que contiene informacion sobre satisfaccion laboral, ultima evaluacion, numero de proyectos, horas promedio trabajadas al mes, antiguedad en la empresa, accidentes laborales, promociones, departamento, salario y rotacion. Cada fila representa un registro de empleado y permite analizar como diferentes condiciones laborales y organizacionales se relacionan con la permanencia o la salida del personal.

## Problema de analisis

La empresa enfrenta un nivel importante de rotacion y necesita identificar factores que permitan detectar grupos con mayor riesgo de salida. Se sospecha que la carga laboral, la satisfaccion y el salario pueden estar influyendo en la decision de abandonar la empresa. Este problema afecta la continuidad operativa, incrementa los costos de reemplazo y puede deteriorar el clima laboral de los equipos que permanecen.

## Metodologia

1. Se definio el problema de negocio y se formularon preguntas clave sobre rotacion, satisfaccion, salario y carga laboral.
2. Se plantearon 4 hipotesis con formulacion explicita de `H0` y `H1`, justificadas desde negocio y validadas con pruebas de Pearson, chi-cuadrado y Spearman con `alpha = 0.05`.
3. Se limpio y transformo la base original sin cambiar el numero de registros. No se detectaron valores faltantes. Los duplicados exactos se conservaron y se marcaron en `duplicate_exact_record` por falta de identificador unico.
4. Se construyeron tablas agregadas, KPIs y un dashboard ejecutivo en Power BI con el archivo principal `dashboard/hr_dashboard.pbix`.
5. Los entregables se regeneran desde estos notebooks: `01_eda_preparacion.ipynb`, `02_hipotesis_pruebas.ipynb` y `03_kpis_export_dashboard.ipynb`.

Preguntas clave:

1. Existe relacion entre horas mensuales y satisfaccion?
2. La satisfaccion baja se relaciona con mayor rotacion?
3. El salario se relaciona con la rotacion?
4. Los departamentos con mas horas promedio tienen mayor rotacion?

Hipotesis formales:

| Hipotesis | H0 | H1 | Justificacion de negocio |
| --- | --- | --- | --- |
| H1: horas mensuales vs satisfaccion | No existe relacion lineal estadisticamente significativa entre `average_monthly_hours` y `satisfaction_level`. | Existe una relacion lineal negativa estadisticamente significativa entre `average_monthly_hours` y `satisfaction_level`. | Permite evaluar si la carga de trabajo debe monitorearse como factor de desgaste y retencion. |
| H2: satisfaccion baja vs rotacion | La rotacion es independiente de la categoria de satisfaccion del empleado. | La rotacion depende de la categoria de satisfaccion y la salida es mayor en empleados con satisfaccion baja. | Ayuda a priorizar programas de clima laboral para grupos con mayor riesgo de salida. |
| H3: salario vs rotacion | La rotacion es independiente del nivel salarial. | La rotacion depende del nivel salarial y es mayor en empleados con salario bajo. | Orienta decisiones de compensacion y revisiones salariales para disminuir salida de talento. |
| H4: horas promedio departamentales vs rotacion | No existe una relacion monotona estadisticamente significativa entre horas promedio departamentales y rotacion departamental. | Existe una relacion monotona positiva estadisticamente significativa entre horas promedio departamentales y rotacion departamental. | Permite validar si la sobrecarga operativa por area explica la salida y si conviene intervenir departamentos especificos. |

Trazabilidad de entregables:

| Entregable | Archivo base | Como se obtiene |
| --- | --- | --- |
| Dataset limpio | `data/clean_hr_analytics.csv` | Se genera desde `data/raw_hr_analytics.csv` en `01_eda_preparacion.ipynb`. |
| Resultados estadisticos | `reports/resultados_hipotesis.csv` | Se generan en `02_hipotesis_pruebas.ipynb`. H4 se calcula con promedios exactos por departamento antes del redondeo. |
| KPIs de negocio | `data/kpi_definitions.csv` | Se generan en `03_kpis_export_dashboard.ipynb` con justificacion de negocio, relacion con hipotesis e indicador de soporte en el dashboard. |
| Dashboard ejecutivo | `dashboard/hr_dashboard.pbix` | Se construye en Power BI con `data/clean_hr_analytics.csv`, sin cambiar nombres de variables ya usadas. |

## Resultados

Hipotesis validadas:

| Hipotesis | Prueba | Resultado | Decision |
| --- | --- | --- | --- |
| H1: A mas horas mensuales, menor satisfaccion | Pearson | `r = -0.0200`, `p = 0.0141` | Rechazar H0 |
| H2: Baja satisfaccion aumenta la rotacion | Chi-cuadrado | `chi2 = 1101.5652`, `p < 0.05` | Rechazar H0 |
| H3: Salario bajo aumenta la rotacion | Chi-cuadrado | `chi2 = 381.2250`, `p < 0.05` | Rechazar H0 |
| H4: Departamentos con mas horas tienen mayor rotacion | Spearman | `rho = -0.1515`, `p = 0.6761` | No rechazar H0 |

KPIs principales:

| KPI | Valor | Relacion con hipotesis | Interpretacion |
| --- | ---: | --- | --- |
| Tasa de rotacion general | 23.81% | H2, H3 y H4 | Resume el nivel total de salida y sirve como indicador ejecutivo principal. |
| Satisfaccion promedio | 0.613 | H1 y H2 | El nivel medio de satisfaccion es moderado y debe vigilarse junto con la rotacion. |
| Horas mensuales promedio | 201.1 horas | H1 y H4 | Monitorea la carga laboral agregada como variable operativa de contexto. |
| Rotacion con satisfaccion baja | 35.61% | H2 | Identifica el segmento prioritario para acciones de clima y retencion. |
| Brecha de rotacion por satisfaccion | 23.10 p.p. | H2 | Cuantifica el impacto de la satisfaccion en la salida y facilita priorizar intervenciones. |
| Rotacion con salario bajo | 29.69% | H3 | Mide el riesgo de fuga en el segmento mas sensible a compensacion. |
| Brecha salario bajo vs alto | 23.06 p.p. | H3 | Evidencia una brecha fuerte de retencion asociada al nivel salarial. |
| Rotacion en alta carga laboral | 37.31% | H1 y H4 | Activa una alerta operativa sobre equipos con exigencia alta. |

Visualizaciones centrales del dashboard:

- Rotacion por departamento.
- Rotacion por satisfaccion.
- Rotacion por salario.
- Horas mensuales vs satisfaccion.
- Rotacion por carga laboral.
- Matriz ejecutiva por departamento.

Hallazgos principales:
- Los empleados con satisfacción por debajo de la mediana tienen aproximadamente el triple de probabilidad de abandonar la empresa 
en comparación con quienes tienen satisfacción alta, lo que sugiere que intervenir el clima laboral podría reducir 
significativamente la rotación.
- Los empleados con salario bajo tienen aproximadamente 4.5 veces más probabilidad de abandonar la empresa que los de salario alto, 
lo que sugiere que una política de revisión salarial podría reducir significativamente la rotación en este segmento.
- 
La relacion entre horas y satisfaccion existe, pero es muy debil en terminos practicos.

- No hay evidencia estadistica para afirmar que los departamentos con mas horas promedio sean los de mayor rotacion.

## Conclusiones

- Los factores mas utiles para priorizar acciones de retencion son la satisfaccion baja y el salario bajo.
- Las horas mensuales deben leerse como variable de contexto y no como causa directa de la rotacion.
- El dashboard ejecutivo permite seguir el riesgo de salida con trazabilidad directa entre hipotesis, KPIs y visualizaciones.
- El analisis tiene limitaciones: no hay identificador unico de empleado, no hay fechas y no se puede afirmar causalidad.
