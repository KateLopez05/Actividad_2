# 📌 Actividad 2 

Katerin Vanesa Lopez Moros

Bayron Meza Guzman 

Grupo de canvas #15

Andres Felipe Callejas

Big Data Grupo 61

## 🚀**Descripción:**
En esta actividad se desarrolla una serie de puntos que tienen como objetivo principal recolectar un conjunto de datos y así desplegarlo sobre una infraestructura virtual, que en este caso en especial será Datadricks Community Edition, diseñando el esquema de almacenamiento, configurando la arquitectura básica, cargando datos desde un dataset y validando todo el procesamiento con Spark y SQL.

## 1️⃣ **Esquema** 
Las entidades clave de este dataset son:
Ubicación, Tiempo, Tipo de incidente e Incidente

Los campos claves son: 
Los *Categóricos* como clase, dia_nombre, barrio, comuna, diseno. Los *Numéricos* como Coordenadas (longitud, latitud). y *Fecha y hora* fecha, hora.

Y como llaves encontramos:
cbml como llave primaria en ubicación y como llave foranea en incidente, fecha y hora como llaves primarias en tiempo y llaves foraneas en incidente y clase como llave primaria en tipo de incidente y como llave foranea en indicente. 


Propón un DDL (Spark SQL) o una StructType (PySpark) que represente el esquema.

Incluye un diagrama simple (Mermaid/draw.io) o tabla de diccionario de datos en una celda Markdown.

## 2️⃣ **Configuración de Databricks**
Debes mostrar paso a paso (con capturas y/o salidas de celdas) la configuración del entorno:

Versión de Databricks Runtime, tipo de clúster, núcleos/RAM, autoscaling.

Versiones de Python/Spark: spark.version, spark.sparkContext.getConf().getAll().

Estructura de almacenamiento (DBFS o Volumes) que utilizarás.

Sugerencia: usa celdas Python para imprimir la configuración y celdas %md para documentar.

## 3️⃣ **Ingesta desde Kaglee + creación de tabla**
Obtención del dataset:

Opción A (API Kaggle): instala kaggle, configura el token y descarga al workspace/DBFS.

Opción B (Manual/URL): descarga local y carga el archivo a DBFS (UI: Upload a /FileStore o Volumes).

Carga en Spark: lee el archivo (CSV/JSON/Parquet) con spark.read aplicando el esquema diseñado.

Persistencia: crea una tabla (saveAsTable o CREATE TABLE USING) y muestra %sql DESCRIBE TABLE.

Incluye capturas/salidas de lectura, recuentos y confirmación de la ruta/tabla creada.

## 4️⃣ **Validaciones**
Realiza validaciones en Spark (PySpark) y en SQL con salidas visibles:

Metadatos: %sql DESCRIBE TABLE, SHOW CREATE TABLE; en Spark: df.printSchema().

Descripción de datos: df.describe().show() y/o %sql con funciones agregadas.

Consultas SELECT y GROUP BY: equivalentes en Spark y SQL comparando resultados.

Conteos y muestras: COUNT(*), LIMIT, filtros por campo.

Explica brevemente cada resultado y su propósito de validación.

## 5️⃣ **Ventajas y Desventajas entre Spark y SQL**
