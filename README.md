# Industrial Production KPIs Dashboard (Power BI)

## Table of Contents

- [Overview](#overview)
- [Dataset Description](#dataset-description)
- [Technologies](#technologies)
- [Dashboard Views](#dashboard-views)
- [Data Modeling](#data-modeling)
- [DAX Logic](#dax-logic)
- [Disclaimer](#disclaimer)
- [Author](#author)
- [Additional Example](#additional-example-daily-control-dashboard)

---

## Overview

This Power BI project presents a complete dashboard system for monitoring key production indicators in an industrial environment using simulated and anonymized data.

The goal is to:
- Track production vs. installed capacity by process
- Monitor operator efficiency over time
- Evaluate process capacity utilization
- Visualize Pareto of inefficiencies
- Control theoretical vs. actual goal achievement

🔗 **Main Dashboard:**  
[▶️ Weekly KPIs – Interactive Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiMzAxMjAyYzctMGM5My00NDk3LTg4NjAtN2I4ZmE4MDgwZjZkIiwidCI6IjdmMDBjMGNjLTE3NzgtNDBlOS1iMTAzLWU2N2Q1MGE0NWMwZSJ9)

---

## Dataset Description

| Table            | Description                                                  |
|------------------|--------------------------------------------------------------|
| proceso_a – f    | Production data for each process (article, client, metrics)  |
| capacidad_*      | Theoretical process capacities by day and group              |
| BD_Paretto       | Inefficiency causes and frequencies                          |
| Calendar         | Standard calendar table with day, month, and year            |
| Turnos           | Shift information                                            |

All data used is simulated and anonymized. See `/data_produccion` for details.

---

## Technologies

- Power BI Desktop
- Power Query (M)
- DAX
- Excel (as data source)
- GitHub (for version control and documentation)

---

## Dashboard Views

### Weekly KPIs – Process B  
[▶️ View Dashboard](https://app.powerbi.com/view?r=eyJrIjoiMzAxMjAyYzctMGM5My00NDk3LTg4NjAtN2I4ZmE4MDgwZjZkIiwidCI6IjdmMDBjMGNjLTE3NzgtNDBlOS1iMTAzLWU2N2Q1MGE0NWMwZSJ9)

![Weekly KPI](./screenshots/dashboard_kpi_semanal.png)

Includes:
- Production vs. Capacity analysis
- Daily efficiency vs. theoretical targets
- Operator-wise performance
- Pareto chart of inefficiency causes

---

## Data Modeling

![Data Model](./screenshots/modelo_relacional_powerbi.png)

- Central `Calendar` table  
- One-to-many relationships across dimensions  
- Centralized `Medidas` table for DAX measures  
- Clean relational integrity and filter context  

---

## DAX Logic

Documented in [`DAX_Medidas.md`](./DAX_Medidas.md), including:

- Efficiency per process
- Capacity estimation based on minutaje
- Pareto accumulation
- Goal vs. actual variance metrics

---

## Disclaimer

All data has been fully anonymized and simulated.  
Client names, operator IDs, and process labels were replaced to protect confidentiality.  
This project is for educational and professional portfolio use only.

---

## Author

**Renzo Gabriel Sánchez Quispe**  
📍 Lima, Perú  
📫 renzosanchez201@gmail.com  
🔗 [GitHub Profile](https://github.com/renzosan25)

---

## Additional Example–Daily Control Dashboard

As a complementary example, the following dashboard illustrates a simplified daily production control panel using flat structured data and simpler DAX logic.

🔗 [▶️ Daily Production Control Dashboard](https://app.powerbi.com/view?r=eyJrIjoiYzlkMmRhNGEtZWUwYy00MWNmLWE5YTItZGFiMjVlMmZlNTNlIiwidCI6IjdmMDBjMGNjLTE3NzgtNDBlOS1iMTAzLWU2N2Q1MGE0NWMwZSJ9)

![Production Control](./screenshots/dashboard_control_salidas.png)

Includes:
- Daily production vs. target tracking
- Output breakdown by client and status
- Monthly distribution by client group
- KPI gauges for progress and goal completion

This report was built to visualize high-level metrics quickly, without applying relational modeling or advanced DAX logic.

---

