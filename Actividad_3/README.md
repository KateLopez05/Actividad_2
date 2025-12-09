# 📌 Actividad 3  Proyecto Integrado
**Autores:**  
Katerin Vanesa Lopez Moros  
Bayron Meza Guzman  
Grupo 15  
**Docente:** Andres Felipe Callejas  
**Materia:** Big Data Grupo 61

## 🚀**Descripción:**
A partir del dataset usado en la Actividad 2, transformar y visualizar los datos en Databricks CE, generando columnas derivadas de fecha, un resumen mensual, un proceso de limpieza con evidencia antes/después y visualizaciones categóricas. Finalmente, elaborar un video explicativo (≤ 3 minutos, ≤ 50 MB).

## ✏️ Transformaciones de fecha 

En este punto derivamos columna a partir de fecha en la tabla de incidentes y creamos anio, mes, dia, dia_semana y nombre_dia  

**¿Qué aporta cada columna al análisis?**   

➡️ **anio:** Este nos permite identificar tendencias macro (a largo plazo) para realizar comparativas interanuales. Este es clave para evaluar si el volumen del transito está creciendo estructuralmente o si por el contrario disminuye con el paso del tiempo.  

➡️ **mes:** Esencial para detectar la estacionalidad anual, ya que nos ayuda a correlacionar la movilidad con los factores cíclicos (meses) como temporadas de vacaciones, regreso de clases, entre otros.  

➡️ **dia:** Este aporta granularidad para encontrar patrones dentro del mes, lo que permite analizar por ejemplo los días de pago, los inicios y cierres de mes y como estos eventos afectan al flujo vehicular de la ciudad.  

➡️ **dia_semana y el nombre_dia:** Son criticos para distinguir la rutina semanal de los ciudadanos, permitiendo separar el comportamiento de los días laborales en comparación con los fines de semana y entender los perfiles específicos.  

## ✏️ Nueva tabla: resumen por mes

Se crea una tabla agregada por anio y mes  
Y se muestra la siguiente consulta en sql  
SELECT * FROM resumen_mensual LIMIT 10;  
Se observa dentro del notebook.  

## ✏️ Limpieza antes y después
**¿Por qué cada limpieza es pertinente?**

➡️ **Normalización de texto (Triming):** Este es vital para columnas categóricas como clase (tipo de incidente) o barrio  para evitar inconsistencias de captura, para cuenten como categorías distintas asegurando que los GROUP BY reflejen el volumen real de los eventos de la zona.  

➡️ **Casteo por tipos:** Las coordenadas deben ser numéricas para cualquier herramienta de visualización geográfica las pueda interpretar correctamente.  

➡️ **Imputación de nulos:** En movilidad, perder un registro por falta de ubicación es costoso porque pierdes la información temporal (fecha/hora). Imputar coordenadas faltantes (o marcar latitud 0 como NULL y rellenarla) nos permite conservar el incidente para análisis de tendencias temporales, aunque la ubicación sea aproximada.  

➡️ **Manejo de OUTLIERS:** Los sensores GPS fallan frecuentemente enviando coordenadas (0,0) o puntos fuera de la ciudad. Estos Filtran estos valores extremos evita que tu mapa de calor se distorsione ("zoom out" excesivo) y asegura que el análisis espacial se concentre exclusivamente en el área metropolitana válida.  

## ✏️ Visualizaciones con librería

**Interpretación de cada visualización**

<img width="1248" height="626" alt="image" src="https://github.com/user-attachments/assets/9ddd18b0-c00c-4020-a3b5-4555597405ff" />

➡️ **Gráfico 1:** Los choques representan la mayoría de los eventos, sugiriendo problemas de congestion en las vías y el riesgo está entre 2 eventos frecuentes (choques) y eventos graves (atropellos) lo cual es vital para salvar las vidas o mejorar el trafico vehicular. 

<img width="1246" height="732" alt="image" src="https://github.com/user-attachments/assets/d81de1e9-01c4-40ae-b258-26eb9859e288" />

➡️ **Grafico 2:** Un hallazgo en este gráfico es el "efecto fin de semana" ya que típicamente observamos una caída notable el domingo o sea un menor flujo vehicular y un manejo progresivo hacia el viernes, lo cual dicta el cuando se requiere mayor operatividad y control en las calles.

## 🔗 **Video explicativo:**
- **El Desafío de los Datos Crudos:** Iniciamos con un dataset que presentaba inconsistencias críticas: coordenadas GPS en cero, nulos y textos sin estandarizar, lo cual impedía cualquier análisis espacial fiable.
- **Ingeniería y Limpieza (SQL):** Mediante consultas SQL avanzadas, normalizamos las categorías y aplicamos filtros estadísticos (IQR) para descartar ubicaciones erróneas, recuperando la calidad del dato geográfico.
- **La Realidad del Volumen (Pareto):** Al visualizar los tipos de incidentes, confirmamos la Ley de Pareto: los 'Choques' (solo daños materiales) representan la gran mayoría de los casos, indicando un problema estructural de congestión.
- **Patrones Temporales de Riesgo:** El análisis por día de la semana reveló ciclos claros de siniestralidad (ej. picos en viernes/sábado), permitiéndonos diferenciar entre el tráfico rutinario laboral y el riesgo social de fin de semana.
- **Impacto en la Toma de Decisiones:** Esta transformación de datos permite a la Secretaría de Movilidad pasar de la reacción a la prevención, asignando agentes y recursos en los días y zonas exactas donde la evidencia muestra mayor riesgo.
  
**Enlace al video:** https://drive.google.com/file/d/1wDCdLknGPbSvLdqhLc6F98YmnBlZJE-M/view?usp=sharing 

