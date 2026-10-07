# Análisis de Consumo y Segmentación de Clientes – ConnectaTel

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1knUfUIZjyyNHkk9gYNSTC3qfoRfDe6e3)

## Objetivo del proyecto

El objetivo de la empresa es identificar patrones de uso, detectar comportamientos atípicos y comprender qué segmentos de clientes muestran necesidades diferenciadas, con el fin de optimizar la oferta comercial y mejorar la experiencia del usuario.

- Identificar segmentos de clientes por edad y por nivel de uso.
- Detectar patrones de consumo extremo (usuarios intensivos o "Heavy Users").
- Encontrar oportunidades comerciales entre los planes Básico y Premium.

## Datasets utilizados

El análisis usa tres tablas:

| Dataset | Filas | Columnas | Descripción |
|---|---|---|---|
| `plans.csv` | 2 | 8 | Condiciones de los planes Básico y Premium (`plan_name`, `messages_included`, `gb_per_month`, `minutes_included`, `usd_monthly_pay`, `usd_per_gb`, `usd_per_message`, `usd_per_minute`) |
| `users_latam.csv` | 4,000 | 8 | Información de cada cliente (`user_id`, `first_name`, `last_name`, `age`, `city`, `reg_date`, `plan`, `churn_date`) |
| `usage.csv` | 40,000 | 6 | Registro de interacciones (`id`, `user_id`, `type`, `date`, `duration`, `length`) |

Entre las tres tablas suman cerca de 44,000 filas.

## Etapas del análisis

1. **Auditoría de calidad de datos:** se detectaron 40 fechas de registro imposibles en `reg_date` (año 2026, fuera del límite de 2024), cerca del 1% de los usuarios, y 50 fechas corruptas en `date`, cerca del 0.1% de los registros de uso. Se eliminaron sin afectar los resultados.
2. **Revisión de valores nulos:** los nulos en `duration` (mensajes de texto), en `length` (llamadas de voz) y en `churn_date` (clientes que siguen activos) son propios del sistema, por lo que se conservaron. Los nulos en `city` (~12%) son datos faltantes y no se usaron en el análisis.
3. **Segmentación por edad:** creación de `grupo_edad` (Jóvenes, Adultos, Adultos Mayores) y comparación con la elección de plan.
4. **Segmentación por nivel de uso:** creación de `grupo_uso` (Bajo, Medio y Alto uso).
5. **Análisis de outliers:** se mantuvieron porque corresponden a consumo real y no a errores.
6. **Conclusiones y recomendaciones de negocio.**

## Hallazgos principales

- La edad no influye en el plan elegido: 65% Básico y 35% Premium en todos los rangos.
- El consumo de los planes Básico y Premium se solapa casi por completo.
- Hay clientes de Alto uso en plan Básico, que son la principal oportunidad de migración.
- Existe un nicho de Heavy Users, con llamadas de hasta 155 minutos.

## Cómo ejecutar el notebook

1. Haz clic en el botón "Abrir en Colab" de arriba.
2. Sube a Colab los tres archivos de datos (`plans.csv`, `users_latam.csv` y `usage.csv`) desde el panel izquierdo (ícono de carpeta).
3. Ejecuta las celdas en orden con `Entorno de ejecución > Ejecutar todo`.

## Guía de reproducción

1. Verifica que los archivos de datos estén en la misma ruta que usa el código del notebook.
2. Asegúrate de tener las librerías necesarias (`pandas`, `seaborn` y `matplotlib`). En Colab ya vienen instaladas.
3. Ejecuta el notebook completo, de arriba hacia abajo, sin saltarte celdas.
4. Los resultados (segmentos, gráficos y estadísticas) deberían coincidir con los del informe.

## Autor

Maria Camila Benavides Valderrama – [GitHub](https://github.com/camy9506-bit)
