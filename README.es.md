# Restaurant Demand Optimization (Forecasting + KPIs)

Proyecto de Data Science end-to-end para **predecir demanda** y **optimizar rentabilidad** en un restaurante, combinando:
- análisis exploratorio (EDA),
- KPIs operativos/financieros,
- ingeniería de menú,
- modelos predictivos (baseline + ML + series de tiempo),
- evaluación y recomendaciones de negocio.

> Diseñado como proyecto de portafolio (GitHub/LinkedIn): código modular, reproducible y adaptable a distintos restaurantes y entornos.

---

## Business Goal

Optimizar:
- **Rentabilidad** (margen y utilidad estimada)
- **Desperdicio** (mejor planificación de compras e inventario)
- **Operación** (dotación por turno, planificación de producción)
- **Demanda**: forecast **diario**, **semanal** y **30 días**

---

## Config & Assumptions (adaptable)

Estos parámetros se definen como configuración (para reutilizar el proyecto en distintos restaurantes):

- **Moneda base**: CLP (configurable)
- **Impuesto**: IVA 19% (configurable)
- **Propina**: 10% opcional (por defecto **no** incluida en revenue)
- **Canales**: `dine_in`, `takeaway`, `delivery`
- **Catálogo (SKUs)**: típico 40–80 (configurable)
- **Horario típico**: 11:00–00:00, 6 días/semana (configurable)

---

## Data (POS & Operaciones)

Estructura esperada (real o sintética):
- Fecha/hora, ticket/boleta, productos, cantidades, precios
- Costos por ingrediente / receta (para food cost)
- Inventario y rotación
- Personal por turno y costos (para productividad)
- Costos fijos mensuales (para utilidad estimada)

> Por práctica profesional, `data/raw/` y `data/processed/` no se versionan en Git.

---

## Project Structure

```text
restaurant-demand-optimization/
├── data/
│   ├── raw/              # ignorado por git
│   └── processed/        # ignorado por git
├── notebooks/
├── src/
│   ├── forecasting/
│   ├── kpis/
│   └── main.py
├── reports/
├── README.md
├── requirements.txt
├── .gitignore
└── .gitattributes