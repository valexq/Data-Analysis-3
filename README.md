
# Proyecto : Recursos humanos

## Dataset
- **Nombre:** HR Analytics
- **Fuente:** Kaggle
- **Link:** https://www.kaggle.com/datasets/giripujar/hr-analytics
- **Registros:** 15000
- **Variables:** 10


## Integrantes: 
Grupo 5

| Nombre               | Rol                                    | GitHub        |
|----------------------|----------------------------------------|---------------|
| Vanessa Alfaro       | Fase 1 y 2                             | @valexq       |
| Juan Manuel Valencia | Fase                                   | @Juanchos2905 |
| Ziuvar Ruiz          | Fase                                   | @ziuvar       |
| Juan Cardona         | Fase                                   | @jcardser     |

## Estructura del repositorio 
```
Data-Analysis-3/
├─ data/
│  ├─ raw_hr_analytics.csv              # Dataset original de Kaggle 
│  └─ clean_hr_analytics.csv            # CSV limpio listo para BI / pruebas
├─ notebooks/
│  ├─ 01_eda_preparacion.ipynb
│  ├─ 02_hipotesis_pruebas.ipynb
│  └─ 03_kpis_export_dashboard.ipynb
├─ dashboard/
│  ├─ hr_dashboard.pbix # 
│  └─ capturas/         # Screenshots del tablero para el README
├─ README.md
```

## Objetivo
El presente análisis tiene como objetivo identificar patrones, tendencias y relaciones estadísticas que permitan detectar anticipadamente qué empleados tienen mayor riesgo de irse y reducir la rotación, proporcionando al área de Recursos Humanos información basada en evidencia para tomar decisiones estratégicas de retención de sus empleados.
## Contexto del dataset
El proyecto utiliza un conjunto de datos de analítica de Recursos Humanos (HR Analytics) que contiene información de empleados de una empresa, incluyendo su nivel de satisfacción, desempeño en la última evaluación, número de proyectos, horas promedio trabajadas al mes, años en la compañía, departamento, salario, promoción en los últimos cinco años y si han dejado la empresa o no (variable de rotación). Cada fila del dataset representa a un empleado y permite analizar cómo diferentes características laborales y organizacionales se relacionan con la decisión de permanecer en la empresa o abandonarla.

## Problema de análisis 
La empresa está enfrentando una alta rotación de empleados en los últimos meses. Se sospecha que algunos departamentos presentan condiciones de trabajo más exigentes, lo que podría estar impulsando la salida de personal. Además, se plantea que el salario y el nivel de satisfacción pueden estar influyendo en la decisión de renunciar. Este fenómeno puede generar una sobrecarga laboral para los empleados que permanecen, aumentando el estrés y el riesgo de insatisfacción, así como retrasos en proyectos, mayores costos de adaptación de nuevos trabajadores y un impacto negativo en la calidad del servicio ofrecido por la organización.

## Preguntas claves
1. ¿Los departamentos con mayor promedio de horas mensuales trabajadas son más propensos a la baja de sus empleados?
2. ¿Existe una relación entre el promedio de horas mensuales trabajadas y el nivel de satisfacción laboral?
3. ¿Cómo se relaciona el nivel de satisfacción laboral con la rotación de empleados?
4. ¿Cómo se relaciona el salario con la rotación de empleados?

# Hipótesis 
## **Hipótesis 1**
- **H0:** No existe relación entre el promedio de horas mensuales trabajadas y el nivel de satisfacción de los empleados
- **H1:** A más horas mensuales trabajadas, menor es la satisfacción de los empleados
- **Variables:**
  - `average_montly_hours` (numérica continua)
  - `satisfaction_level`   (numérica continua)
- **Tipo de variables:** Númerica
- **Prueba estadística:** Correlación de Pearson
- **Justificación:** Esta hipótesis es relevante porque permite identificar si la carga de trabajo excesiva está afectando directamente la satisfacción laboral de los empleados, lo que podría ser una señal temprana de burnout. Si se confirma que a más horas trabajadas menor es la satisfacción, el área de Recursos Humanos podría proponer a los líderes de cada área redistribuir la carga de trabajo y revisar el número de proyectos asignados con el fin de prevenir el burnout y reducir el riesgo de rotación.
> **Nota:** Esta hipótesis actúa como paso previo a la H2, ya que 
si se confirma que más horas reducen la satisfacción, y la H2 
confirma que baja satisfacción aumenta la rotación, entonces la 
carga laboral sería un factor indirecto de rotación

## **Hipótesis 2**
- **H0:** No existe asociación entre el nivel de satisfacción del empleado y la rotación
- **H1:** Los empleados con un nivel de satisfacción por debajo de la mediana tienen mayor probabilidad de abandonar la empresa
- **Variables:**
  - `satisfaction_level` (según la mediana del dataset)
    - bajo
    - alto 
  - `left`
    - 0 = se queda
    - 1 = se va
- **Tipo de variables:** Categóricas
- **Prueba estadística:** chi-cuadrado de independencia.
- **Justificación:** Esta hipótesis es relevante porque permite identificar anticipadamente qué empleados tienen baja satisfacción y mayor riesgo de irse, ya que puede costarle a la empresa tiempo de reclutamiento,tiempo de entrenamiento del nuevo empleado y productividad perdida mientras el puesto está vacío. Si se confirma que existe una relación entre satisfacción baja y rotación, el área de Recursos Humanos podría implementar programas de bienestar, bonificaciones y/o reconocimientos con el fin de mejorar la satisfacción del empleado.

## **Hipótesis 3**
- **H0:** No existe asociación entre el salario y la rotación
- **H1:** Los empleados con salario bajo tienen mayor probabilidad de abandonar la empresa que los empleados con salario medio y alto
- **Variables:**
  - `salary`
    - bajo
    - medio
    - alto
  - `left`
    - 0 = se queda
    - 1 = se va
- **Tipo de variables:** Categóricas
- **Prueba estadística:** chi-cuadrado de independencia.
- **Justificación:** Esta hipótesis es relevante porque permite identificar qué tipo de salario reciben los empleados que se quedan en comparación con los que se van, lo que refleja si la empresa es competitiva en el mercado laboral. Si se confirma que existe una relación entre el salario y rotación, el área de Recursos Humanos podría implementar ajustes de compensación por mercado y política de incrementos salariales periódicos con el fin de reducir la rotación.



# Metodología 


# Resultados

# Conclusiones 

