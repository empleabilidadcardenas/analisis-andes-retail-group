# 📊 Dashboard de Desempeño Comercial (2024–2025) | Andes Retail Group

## 📌 Descripción del Proyecto
Este proyecto consiste en el diseño y desarrollo de un dashboard interactivo en **Microsoft Power BI** para evaluar el desempeño comercial, la rentabilidad y los patrones estacionales de **Andes Retail Group** durante el periodo 2024–2025. 

El objetivo principal es transformar los datos transaccionales en información accionable mediante dos vistas estratégicas (**Overview Ejecutivo** y **Vista Detalle**) y comunicar los hallazgos de negocio bajo el marco narrativo **SCQA** (*Situación, Complicación, Pregunta, Respuesta*).

---

## 🛠️ Preparación de Datos y Modelado (ETL)
Antes de la construcción visual, se realizó la limpieza y transformación del dataset en Power Query:
* **Estandarización de formatos:** Ajuste regional de `Fecha_pedido` a formato Español (Latinoamérica) y validación de tipos de datos numéricos/monetarios.
* **Ingeniería de características (Columna Condicional):** Creación de la variable `Nivel_Venta` en función del monto de ingresos por registro:
  * `Ingresos >= 1000` ➔ **"Venta Alta"**
  * `Ingresos < 1000` ➔ **"Venta Baja"**
* **Control de calidad:** Verificación de integridad mediante las herramientas de *Perfil de columna* en Power BI.

---

## 📐 Arquitectura y Planificación del Dashboard

El reporte sigue un patrón de lectura en **"Z"** (de arriba hacia abajo y de izquierda a derecha), dividiendo el análisis en dos niveles de profundidad:

### 1. 🖥️ Vista Overview: *¿Cómo ha evolucionado el ingreso total y qué lo impulsa?*
Diseñada para ofrecer un diagnóstico inmediato del estado general del negocio.

* **Tarjetas de KPIs Principales (Parte superior):**
  * **Ingresos Totales:** `Suma de Ingresos` (~$6.00 M) — Métrica principal de entrada de capital.
  * **Beneficio Total:** `Suma de Ingresos - Costo` ($1.94 M) — Utilidad neta real generada.
  * **Unidades Vendidas Totales:** `Suma de Unidades_Vendidas` (58 mil unidades) — Volumen de salida de inventario.
  * **Ticket Promedio por Pedido:** `Ingresos Totales / Recuento de ID_Pedido` ($1.11 mil) — Gasto promedio registrado por cada orden de compra.
* **Visualizaciones de Desglose (Centro e inferior):**
  * **Evolución de Ingresos (2024–2025):** *Gráfico de Líneas* (`Fecha_Pedido` por Mes/Año vs. `Ingresos`) que ocupa el ancho central para identificar tendencias, picos y caídas temporales.
  * **Desempeño Geográfico:** *Gráfico de Barras Agrupadas* (`País` y `Región` vs. `Ingresos`) para comparar el liderazgo entre **Perú, Chile y Colombia** en sus regiones Norte, Centro y Sur.
  * **Participación por Categoría:** *Gráfico de Anillos (Donut Chart)* (`Categoría_Producto` vs. `Ingresos`) que muestra la proporción de ventas entre **Deportes, Electrónica, Hogar y Ropa**.
* **Segmentadores Interactivos (Parte inferior derecha):**
  * Filtro desplegable por `Año` (2024, 2025) y botones de selección rápida por `Segmento_Cliente` (*Premium, Estándar, Económico*).

---

### 2. 🔎 Vista Detalle: *¿Por qué varían los ingresos y dónde hay oportunidades de mejora?*
Enfocada en la rentabilidad marginal, estacionalidad y exploración granular.

* **Visualizaciones Analíticas:**
  * **Patrones Estacionales:** *Gráfico de Columnas Agrupadas* (`Estación` [Verano, Otoño, Invierno, Primavera] vs. `Ingresos`) para comparar el rendimiento comercial según la época del año.
  * **Rentabilidad por Segmento de Cliente:** *Gráfico Combinado de Columnas y Línea* (`Segmento_Cliente` vs. `Ingresos` y `Beneficio`) para contrastar el volumen de facturación frente a la ganancia real.
  * **Matriz de Oportunidades Comerciales:** *Matriz dinámica* (`País > Categoría_Producto`, valores: `Margen %` y `Beneficio`) con formato condicional tipo semáforo para detectar combinaciones con baja rentabilidad.
  * **Detalle Granular de Pedidos (Tabla):** Resumen operativo con `Conteo de Pedidos`, `Clientes Únicos` (recuento distinto de `ID_Cliente`), `Ingresos Totales`, `Costo Total` y `Beneficio Total`.
* **Filtros de Exploración:**
  * Deslizador temporal (*slider*) de `Fecha_Pedido`, y menús desplegables de `País` y `Categoría_Producto`.

---

## 💡 Hallazgos y Narrativa Ejecutiva (Modelo SCQA)

### Vista General (Overview)
* **S (Situación):** Durante el periodo 2024–2025, Andes Retail Group registró aproximadamente **$6 millones en ingresos totales** y **$1.94 millones en beneficio neto**, movilizando **58 mil unidades** con un ticket promedio por pedido de **$1.11 mil**. A nivel regional, Perú y Chile lideran ligeramente la facturación, mientras que las categorías de *Deportes* y *Electrónica* destacan como motores clave del portafolio.
* **C (Complicación):** El análisis evolutivo revela fluctuaciones importantes con caídas pronunciadas hacia mediados de año. Asimismo, la categoría de *Ropa* presenta un rezago comercial respecto al resto de las líneas de producto.
* **Q (Pregunta):** ¿Cómo podemos estabilizar el flujo de ingresos a lo largo del año e impulsar las categorías y regiones de menor desempeño?
* **A (Respuesta):** Replicar las tácticas promocionales y de surtido exitosas de *Deportes* y *Electrónica* hacia la línea de *Ropa*, y desplegar campañas preventivas antes de mitad de año para amortiguar la caída cíclica de ingresos.

### Vista Detalle
* **S (Situación):** El desglose estacional confirma que el **Verano** es el periodo de mayor facturación para la empresa. Por su parte, los segmentos de clientes **Premium** y **Estándar** sostienen la rentabilidad del negocio al aportar el mayor volumen de beneficio neto.
* **C (Complicación):** Se identifican dos focos críticos: primero, las ventas sufren una contracción severa durante el **Invierno**; segundo, el segmento **Económico** genera un beneficio total considerablemente menor en relación con sus costos operativos y volumen de ventas.
* **Q (Pregunta):** ¿Cómo podemos mitigar el desplome estacional de invierno y optimizar la rentabilidad del segmento *Económico*?
* **A (Respuesta):** Auditar la estructura de precios, descuentos y costos logísticos asociados al segmento *Económico* para proteger el margen de ganancia, y lanzar paquetes promocionales de *Invierno* enfocados en la retención y recurrencia de los clientes *Premium* y *Estándar*.

---

## 💬 Resumen Ejecutivo para Stakeholders (Formato Slack)

> **📊 Actualización de Desempeño Comercial (2024–2025)**
> 
> Equipo, les comparto los hallazgos principales de nuestro último análisis en Power BI:
> * **Contexto (Situación):** Cerramos el periodo con **~$6M en ingresos totales** y **$1.94M de beneficio neto** (58k unidades vendidas y un ticket promedio de $1.11k por pedido), manteniendo una presencia sólida en Chile, Perú y Colombia.
> * **El problema (Complicación):** Detectamos dos riesgos clave para el crecimiento:
>   1. *Caída estacional:* Nuestras ventas se contraen drásticamente durante el invierno y hacia mediados de año.
>   2. *Brecha de rentabilidad:* El segmento de clientes *Económico* aporta menor utilidad neta frente a los segmentos *Premium* y *Estándar*.
> * **Nuestra prioridad (Pregunta):** ¿Cómo estabilizamos la facturación anual y fortalecemos nuestros márgenes operativos?
> * **Plan de acción sugerido (Respuesta):**
>   * 👉 **Foco en alto valor:** Priorizar la pauta digital y estrategias de fidelización en los segmentos *Premium* y *Estándar*, que son el motor principal de nuestras utilidades.
>   * 👉 **Plan de choque estacional:** Diseñar con Marketing y Ventas campañas específicas de activación para la temporada de invierno e impulsar el catálogo de *Ropa*.

---

## 🚀 Cómo visualizar este proyecto
1. Clona este repositorio o descarga directamente el archivo `proyecto triple ten.pbix`.
2. Abre el archivo utilizando **Microsoft Power BI Desktop**.
