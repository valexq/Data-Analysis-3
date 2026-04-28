# Resumen ejecutivo

El proyecto analiza la rotacion de empleados a partir del dataset HR Analytics. La base original tiene 14999 registros y el dataset limpio conserva 14999 empleados para analisis. Se detectaron 3008 filas repetidas posteriores al primer registro y 5346 filas involucradas en grupos duplicados. Se conservaron porque no existe un identificador unico de empleado y cada fila puede representar una persona distinta con los mismos atributos.

## KPIs principales
- Tasa de rotacion general: 23.81 %.
- Satisfaccion promedio: 0.613 indice 0-1.
- Horas mensuales promedio: 201.1 horas.
- Rotacion con satisfaccion baja: 35.61 %.
- Brecha de rotacion por satisfaccion: 23.1 puntos porcentuales.
- Rotacion con salario bajo: 29.69 %.
- Brecha salario bajo vs alto: 23.06 puntos porcentuales.
- Rotacion en alta carga laboral: 37.31 %.

## Hipotesis formales
- H1. H0: no existe relacion lineal significativa entre horas mensuales y satisfaccion. H1: existe una relacion lineal negativa significativa entre horas mensuales y satisfaccion.
- H2. H0: la rotacion es independiente de la categoria de satisfaccion. H1: la rotacion depende de la categoria de satisfaccion y aumenta en satisfaccion baja.
- H3. H0: la rotacion es independiente del nivel salarial. H1: la rotacion depende del nivel salarial y aumenta en salario bajo.
- H4. H0: no existe relacion monotona significativa entre horas promedio departamentales y rotacion departamental. H1: existe una relacion monotona positiva significativa entre ambas variables.

## Validacion estadistica
- H1: Correlacion de Pearson, estadistico=-0.02, p=0.014075, Rechazar H0.
- H2: Chi-cuadrado de independencia, estadistico=1101.5652, p=0.0, Rechazar H0.
- H3: Chi-cuadrado de independencia, estadistico=381.225, p=0.0, Rechazar H0.
- H4: Correlacion de Spearman, estadistico=-0.1515, p=0.676065, No rechazar H0.

## Lectura de negocio
La evidencia mas fuerte apunta a dos factores de riesgo: baja satisfaccion y salario bajo. Las horas mensuales tienen una relacion lineal muy debil con la satisfaccion, por lo que deben leerse como contexto de carga laboral, no como causa directa de la rotacion.

## Dashboard Power BI
El dashboard principal debe entregarse como `dashboard/hr_dashboard.pbix`. Las tarjetas y visuales trazan los KPIs del catalogo `data/kpi_definitions.csv` y se conectan con las hipotesis del analisis.
