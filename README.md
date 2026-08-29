# 📊 Informe Rentabilidad Y Desempeño comercial

Dashboard de Business Intelligence construido en Power BI a partir del dataset *Analisis de datos de venta* (Kaggle), con más de 250registros de oredenes de venta entre Noviembre y Diciembre del 2022. El proyecto incluye análisis de los datos de origen, adición de columna costo para mejor analisis, modelado con tabla de calendario, medidas DAX personalizadas y un dashboard interactivo que responde a preguntas clave de negocio: margenes de contribucción, rentabilidad por ciudad, ventas por metodo de pago y tipo de compra.

![Dashboard preview](Dashboard_sales.png)

---

## 🎯 Objetivo

Analizar el comportamiento de ventas de una empresa de retail (Superstore) para identificar patrones estacionales, categorías y regiones más rentables, y perfiles de cliente que aporten más valor — traduciendo los datos en recomendaciones de negocio accionables.

## 🗂️ Fuente de datos

- **Dataset:** [Sales Forecasting — Superstore](https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting) (Kaggle)
- **Registros:** 9.800 filas · 18 columnas
- **Periodo:** enero 2015 – diciembre 2018

## 🛠️ Proceso

**1. Limpieza de datos (Power Query)**
- Corrección de formato regional en la columna `Sales` (el CSV usa separador decimal en formato inglés; se ajustó la configuración regional para evitar que Power BI interpretara `261.96` como `26196`)
- Conversión de `Postal Code` a tipo texto (para evitar agregaciones numéricas sin sentido)
- Verificación de formato de fechas (`Order Date`, `Ship Date`)
- Comprobación de valores nulos y duplicados (dataset limpio en ambos casos)

**2. Modelado de datos**
- Tabla de calendario creada con DAX (`CALENDAR`), con columnas de Año, Mes, Número de Mes y Trimestre
- Relación 1:* entre la tabla de Calendario y la tabla de ventas

**3. Medidas DAX**
| Medida | Descripción |
|---|---|
| `Ventas Totales` | Suma total de ventas |
| `Nº Pedidos` | Conteo de pedidos únicos (`DISTINCTCOUNT`) |
| `Ticket Medio` | Ventas totales / Nº de pedidos |
| `Ventas Año Anterior` | Ventas del mismo periodo del año anterior (`SAMEPERIODLASTYEAR`) |
| `Crecimiento YoY %` | Variación porcentual respecto al año anterior |
| `Nº Clientes` | Conteo de clientes únicos |
| `Ventas por Cliente` | Ventas totales / Nº de clientes |

**4. Dashboard**
Página única con KPIs principales, evolución mensual de ventas, y comparativas por categoría, región y segmento de cliente, con filtro interactivo por año.

## 💡 Insights principales

- **Estacionalidad:** las ventas muestran picos claros en septiembre, noviembre y diciembre, coincidiendo con patrones típicos de retail (vuelta al cole, Black Friday, Navidad). Esto sugiere anticipar la planificación de stock 1-2 meses antes de estos picos.
- **Categoría vs. volumen:** *Technology* lidera en ingresos pese a tener menos pedidos (ticket alto, baja rotación), mientras que *Office Supplies* concentra más pedidos con menor ticket medio (alta rotación, bajo margen unitario).
- **Región y valor de cliente:** *West* y *East* no solo generan más ventas totales, sino también mayor gasto medio por cliente — indicando un mercado de mayor valor, no solo mayor volumen de clientes.
- **Crecimiento:** las ventas de 2018 crecieron un 20,3% respecto a 2017.

## 🧰 Herramientas

- Power BI Desktop (Power Query + DAX)
- Dataset: Kaggle

---
