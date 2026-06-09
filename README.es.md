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

<!--
  Sección "Resultados y Conclusiones" para pegar en el README del repo
  restaurant-demand-optimization (versión ES + EN).

  Las imágenes deben estar subidas a la RAÍZ del repo con estos nombres:
    heatmap_demanda.jpg
    pareto_ventas.jpg
    menu_engineering.jpg
-->

## 📊 Resultados y conclusiones (ES)

> Hallazgos obtenidos sobre un dataset tipo POS (datos sintéticos reproducibles, 60 productos).

### Patrón de demanda
![Heatmap de demanda por día y hora](heatmap_demanda.jpg)

Se identifican **dos peaks claros**: almuerzo (13:00–15:00) y cena (20:00–22:00), con el máximo el **sábado ~21:00**. Este patrón permite planificar turnos, ajustar la *mise en place* / inventario y reducir quiebres en horas punta.

### Concentración de ventas (Pareto 80/20)
![Pareto de ventas por producto](pareto_ventas.jpg)

**23 de 60 productos (≈38%) explican cerca del 80% de las ventas.** Foco operativo: asegurar disponibilidad de esos *top sellers*, optimizar su compra e inventario, y simplificar la cola larga del menú.

### Menu Engineering
![Matriz de Menu Engineering](menu_engineering.jpg)

Cruzando **popularidad (unidades vendidas) vs. margen por unidad**, cada producto cae en uno de cuatro cuadrantes:

- **Estrellas** — alta venta y alto margen → proteger y destacar.
- **Caballos de batalla** — alta venta, menor margen → optimizar costo o subir precio con cuidado.
- **Puzzles** — alto margen, baja venta → promocionar o reubicar en la carta.
- **Perros** — baja venta y bajo margen → candidatos a eliminar.

### KPIs calculados
Ventas netas/brutas, ticket promedio, *food cost %* y margen por producto, además de KPIs operativos por turno.

### Próximos pasos
Forecasting de demanda con *backtesting* (horizontes diario, semanal y a 30 días) e incorporación de modelos de ML para apoyar compras y planificación de turnos.

---

## 📊 Results & Conclusions (EN)

> Findings on a POS-like dataset (reproducible synthetic data, 60 products).

### Demand pattern
![Demand heatmap by day and hour](heatmap_demanda.jpg)

Two clear peaks: lunch (1–3 PM) and dinner (8–10 PM), peaking on **Saturday ~9 PM**. Useful for shift planning, mise en place / inventory, and reducing stockouts at peak hours.

### Sales concentration (80/20 Pareto)
![Sales Pareto by product](pareto_ventas.jpg)

**23 of 60 products (~38%) drive ~80% of sales.** Focus on keeping top sellers in stock, optimizing their purchasing, and simplifying the menu's long tail.

### Menu Engineering
![Menu Engineering matrix](menu_engineering.jpg)

Crossing **popularity (units) vs. margin per unit**, each item falls into Stars, Workhorses, Puzzles, or Dogs — guiding pricing, promotion, and simplification.

### KPIs
Net/gross revenue, average ticket, food cost %, per-product margin, and operational KPIs per shift.

### Next steps
Backtested demand forecasting (daily, weekly, 30-day) and ML models to support purchasing and staffing.
