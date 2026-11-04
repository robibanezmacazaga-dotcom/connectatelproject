# 📞 Análisis de Calidad y Segmentación de Clientes — ConnectaTel

## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto fue auditar, limpiar y analizar las bases de datos de consumo de la empresa de telecomunicaciones **ConnectaTel** durante el año 2024. A través de este análisis se identificaron y corrigieron anomalías críticas de calidad en los datos, se exploraron los patrones de consumo por tipo de plan y se construyó una segmentación avanzada de clientes (por uso y edad) para detectar oportunidades comerciales y usuarios de alto valor para el negocio.

---

## 📊 Datasets Utilizados
El análisis se realizó cruzando tres conjuntos de datos principales localizados en el directorio `/datasets/`:
*   **`plans.csv`**: Contiene la oferta comercial y características de los planes vigentes de la compañía (*Basico* y *Premium*).
*   **`users_latam.csv`**: Registro maestro de clientes que incluye identificadores únicos, nombres, edades, ciudades de procedencia, fechas de registro y estado de baja (*churn*).
*   **`usage.csv`**: Detalle histórico de las transacciones de consumo de red, clasificadas por tipo de servicio (llamadas o mensajes de texto), duración en minutos y longitud.

---

## 🛠️ Etapas del Análisis Realizadas

1.  **Carga y Exploración Inicial:** Validación de rutas, inspección de dimensiones con `.shape` y auditoría de tipos de datos mediante `.info()`.
2.  **Identificación de Problemas de Calidad:** 
    *   Detección de valores centinela como `-999` en la edad y `'?'` en las ubicaciones.
    *   Identificación de inconsistencias cronológicas (40 registros con el año imposible 2026).
    *   Comprobación estadística de que los nulos en consumo eran de tipo **MAR (Missing At Random)** dependientes del tipo de servicio.
3.  **Limpieza Básica de Datos:** Imputación de la edad por su mediana real, homologación de texto a `pd.NA` y conversión de fechas futuras anómalas a `pd.NaT`.
4.  **Agregación y Perfilado:** Construcción de una tabla resumen por usuario para consolidar métricas de comportamiento histórico (`cant_mensajes`, `cant_llamadas` y `cant_minutos_llamada`).
5.  **Análisis Estadístico y Visual:** Generación automática de histogramas y diagramas de caja (*Boxplots*) con Seaborn para evaluar sesgamientos y calcular límites superiores mediante el método del **Rango Intercuartílico (IQR)**.
6.  **Segmentación Avanzada:** Clasificación automatizada de usuarios en perfiles lógicos de negocio (`grupo_uso` y `grupo_edad`) utilizando condicionales vectorizados en cascada.

---

## 🚀 Cómo Ejecutar el Notebook

Para revisar, ejecutar o auditar el código de este análisis paso a paso, puedes utilizar un entorno local de Jupyter o Google Colab:

### Opción A: Ejecución en Google Colab
1. Sube el archivo `.ipynb` de este repositorio a tu Google Drive.
2. Abre el archivo con **Google Colaboratory**.
3. Asegúrate de tener los archivos CSV en la carpeta correspondiente de tu entorno de ejecución.

### Opción B: Ejecución Local (Jupyter Notebook)
Asegúrate de contar con Python instalado junto con las dependencias necesarias:

```bash
pip install pandas numpy matplotlib seaborn
jupyter notebook
```
