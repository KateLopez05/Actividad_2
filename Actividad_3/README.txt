Actividad 3 
Proyecto integrado Big Data


Punto 1 
Transformaciones de fecha 

En este punto derivamos columna a partir de fecha en la tabla de incidentes y creamos anio, mes, dia, dia_semana y nombre_dia
¿Qué aporta cada columna al análisis?

anio: Este nos permite identificar tendencias macro (a largo plazo) para realizar comparativas interanuales. Este es clave para evaluar si el volumen del transito está creciendo estructuralmente o si por el contrario disminuye con el paso del tiempo.
mes: Esencial para detectar la estacionalidad anual, ya que nos ayuda a correlacionar la movilidad con los factores cíclicos (meses) como temporadas de vacaciones, regreso de clases, entre otros.
dia: Este aporta granularidad para encontrar patrones dentro del mes, lo que permite analizar por ejemplo los días de pago, los inicios y cierres de mes y como estos eventos afectan al flujo vehicular de la ciudad.
dia_semana y el nombre_dia: Son criticos para distinguir la rutina semanal de los ciudadanos, permitiendo separar el comportamiento de los días laborales en comparación con los fines de semana y entender los perfiles específicos. 


PUNTO 2 
Nueva tabla: resumen por mes

Se crea una tabla agregada por anio y mes 
Y se muestra la siguiente consulta en sql 
SELECT * FROM resumen_mensual LIMIT 10;

PUNTO 3

Normalización de texto (Triming): Este es vital para columnas categóricas como clase (tipo de incidente) o barrio  para evitar inconsistencias de captura, para cuenten como categorías distintas asegurando que los GROUP BY reflejen el volumen real de los eventos de la zona.
Casteo por tipos: Las coordenadas deben ser numéricas para cualquier herramienta de visualización geográfica las pueda interpretar correctamente.
Imputación de nulos: En movilidad, perder un registro por falta de ubicación es costoso porque pierdes la información temporal (fecha/hora). Imputar coordenadas faltantes (o marcar latitud 0 como NULL y rellenarla) nos permite conservar el incidente para análisis de tendencias temporales, aunque la ubicación sea aproximada.
Manejo de OUTLIERS: Los sensores GPS fallan frecuentemente enviando coordenadas (0,0) o puntos fuera de la ciudad. Estos Filtran estos valores extremos evita que tu mapa de calor se distorsione ("zoom out" excesivo) y asegura que el análisis espacial se concentre exclusivamente en el área metropolitana válida.

PUNTO 4

Gráfico 1: Los choques representan la mayoría de los eventos, sugiriendo problemas de congestion en las vías y el riesgo está entre 2 eventos frecuentes (choques) y eventos graves (atropellos) lo cual es vital para salvar las vidas o mejorar el trafico vehicular.

Grafico 2: Un hallazgo en este gráfico es el "efecto fin de semana" ya que típicamente observamos una caída notable el domingo o sea un menor flujo vehicular y un manejo progresivo hacia el viernes, lo cual dicta el cuando se requiere mayor operatividad y control en las calles.





