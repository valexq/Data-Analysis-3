
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
El presente análisis tiene como objetivo identificar patrones, tendencias y relaciones estadísticas que permitan detectar anticipadamente qué empleados tienen mayor riesgo de irse, reducir la rotación y promover la movilidad promocional, proporcionando al área de Recursos Humanos información basada en evidencia para tomar decisiones estratégicas de retención de sus empleados.
## Contexto del dataset
El proyecto utiliza un conjunto de datos de analítica de Recursos Humanos (HR Analytics) que contiene información de empleados de una empresa, incluyendo su nivel de satisfacción, desempeño en la última evaluación, número de proyectos, horas promedio trabajadas al mes, años en la compañía, departamento, salario, promoción en los últimos cinco años y si han dejado la empresa o no (variable de rotación). Cada fila del dataset representa a un empleado y permite analizar cómo diferentes características laborales y organizacionales se relacionan con la decisión de permanecer en la empresa o abandonarla.

## Problema de análisis 
La empresa está enfrentando una alta rotación de empleados en los últimos meses. Se sospecha que algunos departamentos presentan condiciones de trabajo más exigentes y salarios más bajos, lo que podría estar impulsando la salida de personal. Además, se plantea que el salario, el nivel de satisfacción y la falta de movilidad promocional pueden estar influyendo en la decisión de renunciar. Este fenómeno puede generar una sobrecarga laboral para los empleados que permanecen, aumentando el estrés y el riesgo de insatisfacción, así como retrasos en proyectos, mayores costos de adaptación de nuevos trabajadores y un impacto negativo en la calidad del servicio ofrecido por la organización.

## Preguntas claves
1. ¿Qué departamentos presentan las tasas de rotación más altas y qué variables laborales caracterizan a esos empleados?
2. ¿Cómo se relaciona el nivel de satisfacción laboral con la rotación de empleados?
3. ¿Cómo se relaciona el salario con la rotación de empleados?
4. ¿Existe una mayor rotación entre los empleados que no han sido promovidos en los últimos cinco años frente a quienes sí han sido promovidos?

# Hipótesis 
## **Hipótesis 1**
- **H0:** No existe asociación entre el nivel de satisfacción del empleado y la rotación
- **H1:** Los empleados con un nivel de satisfacción por debajo de la mediana tienen mayor probabilidad de abandonar la empresa
- **Variables:**
-- `satisfaction_level` (según la mediana del dataset)
  - bajo
  - alto 
- `left`
  - 0 = se queda
  - 1 = se va
- **Tipo de variables:** categóricas
- **Prueba estadística:** chi-cuadrado de independencia.
- **Justificación:** Esta hipótesis es relevante porque permite identificar anticipadamente qué empleados tienen baja satisfacción y mayor riesgo de irse, ya que puede costarle a la empresa tiempo de reclutamiento,tiempo de entrenamiento del nuevo empleado y productividad perdida mientras el puesto está vacío. Si se confirma que existe una relación entre satisfacción baja y rotación, el área de Recursos Humanos podría implementar programas de bienestar, bonificaciones y/o reconocimientos con el fin de mejorar la satisfacción del empleado.

## **Hipótesis 2**
- **H0:** No existe asociación entre el salario y la rotación
- **H1:** Los empleados con salario bajo tienen mayor probabilidad de abandonar la empresa que los empleados con salario medio y alto
- **Variables:**
-- `salary`
  - bajo
  - medio
  - alto
- `left`
  - 0 = se queda
  - 1 = se va
- **Tipo de variables:** categóricas
- **Prueba estadística:** chi-cuadrado de independencia.
- **Justificación:** Esta hipótesis es relevante porque permite identificar qué tipo de salario reciben los empleados que se quedan en comparación con los que se van, lo que refleja si la empresa es competitiva en el mercado laboral. Si se confirma que existe una relación entre el salario y rotación, el área de Recursos Humanos podría implementar ajustes de compensación por mercado y política de incrementos salariales periódicos con el fin de reducir la rotación.

## **Hipótesis 3**
- **H0:** No existe asociación entre la promoción en los últimos cinco años y la rotación
- **H1:** Los empleados que no han sido promovidos en los últimos cinco años tienen mayor probabilidad de abandonar la empresa frente a quienes sí han sido promovidos
- **Variables:**
- `promotion_last_5years`
  - 0 = no promovido
  - 1 = promovido
- `left`
  - 0 = se queda
  - 1 = se va
- **Tipo de variables:** categóricas
- **Prueba estadística:** chi-cuadrado de independencia.
- **Justificación:** Esta hipótesis es relevante porque permite identificar si los empleados que se van o se quedan han tenido una promoción, lo que nos muestra un panorama de la política de crecimiento interno de la empresa y el riesgo de perder experiencia y conocimiento acumulado difícil de reemplazar. Si se confirma que existe una relación entre la promoción en los últimos cinco años y la rotación, el área de Recursos Humanos podría implementar cursos de capacitación, programas de desarrollo profesional y mentorías internas con el fin de promover la movilidad promocional.





# Metodología 


# Resultados

# Conclusiones 

