# Análisis de Ventas y Retención - EcoShop 
Este proyecto presenta un **Análisis Exploratorio de Datos (EDA)** sobre el comportamiento de compra de los usuarios de EcoShop durante el periodo Enero 2025 - Diciembre 2025, con el objetivo de identificar oportunidades para reducir la tasa de abandono. 
[![Python](https://img.shields.io/badge/Python-3.11-blue)](https://img.shields.io/badge/Python-3.11-blue)
[![Estado](https://img.shields.io/badge/Estado-Completado-success)](https://img.shields.io/badge/Estado-Completado-success)
## Índice

- [Resumen Ejecutivo](#resumen-ejecutivo)
- [Tabla de KPIs](#tabla-de-kpis)
- [Metodología](#metodología)
- [Código Destacado](#código-destacado)

  ## Resumen Ejecutivo
  > **Insight principal:** Los clientes que realizan una segunda compra dentro de los primeros 30 días tienen un LTV (*Lifetime Value*) **3 veces superior** al resto. *Este es el dato más relevante del análisis y confirma la importancia de las estrategias de reactivación temprana.*
  >
  
  - **Estacionalidad marcada:** El pico de ventas ocurre en noviembre (+42% 
respecto a la media anual) impulsado por el Black Friday.

 - **Fricción en móviles:** La columna device_type reveló que el 70% del tráfico 
viene de mobile, pero la conversión es un 1.8% menor que en desktop.

 - **Categoría estrella:** Los productos de la categoría Hogar_Sostenible 
concentran el mayor margen de beneficio neto.

## Tabla de KPIs 


| Métrica | 2024 | 2025 | Variación |
|:---|---:|---:|---:|
| Ingresos totales | 1.250.000 € | 1.580.000 € | +26,4% |
| Ticket promedio | 48,20 € | 52,10 € | +8,1% |
| Tasa de retención a 90 días | 31,5% | 38,7% | +22,9% |
| Tasa de abandono | 24,8% | 19,3% | -22,2% |
| LTV promedio | 186,40 € | 254,80 € | +36,7% |

## Metodologia
1. Extracción: Conexión a base de datos PostgreSQL mediante SQLAlchemy. 
2. Limpieza: Tratamiento de valores nulos en fecha_entrega y 
estandarización de categorías. 
3. Análisis: Segmentación de clientes mediante análisis RFM (Recencia, 
Frecuencia, Valor Monetario). 
4. Visualización: Creación de dashboard interactivo en Power BI y gráficos 
estáticos con Seaborn.

## Estado del proyecto

- [x] Limpieza y validación del dataset
- [x] Análisis exploratorio y pruebas de hipótesis
- [ ] Automatización del pipeline semanal con Airflow
- [ ] Modelo predictivo de *churn*

## Código Destacado

Consulta SQL utilizada para calcular el ticket promedio por categoría:

```sql
SELECT
    categoria,
    COUNT(DISTINCT order_id) AS total_pedidos,
    ROUND(AVG(total_venta), 2) AS ticket_promedio
FROM ventas_2025
WHERE estado_pedido = 'Completado'
GROUP BY categoria
ORDER BY ticket_promedio DESC;
```
