# Dashboard de Producción Industrial - Power BI

## Tabla de Contenido

- [Resumen General](#resumen-general)
- [Descripción del Dataset](#descripción-del-dataset)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)
- [Vistas del Dashboard](#vistas-del-dashboard)
- [Modelo de Datos](#modelo-de-datos)
- [Lógica DAX](#lógica-dax)
- [Cómo Usarlo](#cómo-usarlo)
- [Publicación del Dashboard](#publicación-del-dashboard)
- [Aviso Legal](#aviso-legal)
- [Autor](#autor)

---

## Resumen General

Este proyecto presenta un dashboard de control de producción desarrollado con Power BI, utilizando datos reales anonimizados de una planta industrial bajo sistema Make to Order.  
El objetivo es monitorear la eficiencia operativa, la utilización de la capacidad instalada y las causas de ineficiencia por área de trabajo.

El dashboard está orientado a la mejora continua, permitiendo identificar cuellos de botella, operadores con baja productividad y brechas frente a metas históricas.

---

## Descripción del Dataset

El conjunto de datos ha sido modificado para proteger la confidencialidad, pero mantiene su estructura operativa original.

| Tabla | Descripción |
| --- | --- |
| `proceso_a`, `proceso_b`, ... | Datos por proceso productivo con eficiencia, horarios y operadores |
| `capacidad_*` | Capacidad instalada diaria por línea |
| `Calendar` | Tabla de fechas estándar para visualizaciones temporales |
| `BD_Paretto` | Base de causas de ineficiencia por área |
| `Medidas` | Métricas calculadas mediante DAX |
| `Tipos_*` | Clasificación adicional según tipo de proceso |

---

## Tecnologías Utilizadas

- Power BI Desktop
- DAX para medidas personalizadas
- Modelo de datos relacional
- Excel (como fuente de datos)
- GitHub para versionamiento y publicación

---

## Vistas del Dashboard

### Indicador Semanal de Producción

![Indicador de producción](screenshots/indicador_produccion.png)

- Comparación de producción vs capacidad instalada  
- Seguimiento de eficiencia diaria por operador  
- Causas de ineficiencia (Pareto)

### Tablero de Control General

![Tablero de control](screenshots/tablero_control.png)

- Cumplimiento diario y mensual de metas  
- Estado de liquidados, en proceso y retrasados  
- Distribución por tipo de cliente

---

## Modelo de Datos

<img src="screenshots/modelo_datos.png" alt="Modelo de datos" width="800"/>

Modelo en estrella centrado en la tabla calendario y procesos individuales relacionados por fecha y código de operador.

---

## Lógica DAX

Consulta el detalle de las fórmulas DAX empleadas en el archivo [`DAX_Medidas.md`](DAX_Medidas.md).

Incluye medidas como:

- % Ef proceso  
- Capacidad instalada por proceso  
- % Frecuencia acumulada (Pareto)  
- Utilización de capacidad diaria

---

## Cómo Usarlo

1. Descarga el archivo `.pbix`
2. Asegúrate de mantener la carpeta `data_produccion/` en el mismo nivel
3. Abre el `.pbix` con Power BI Desktop
4. Visualiza sin conexión, ya que los datos están incrustados

---

## Publicación del Dashboard

Si deseas ver una vista pública interactiva, consulta el siguiente archivo:

[`link_dashboard_public.txt`](link_dashboard_public.txt)

Nota: Esta funcionalidad depende de la activación del modo público por parte del administrador de Power BI. Si no se encuentra disponible, se recomienda visualizar el `.pbix` directamente.

---

## Aviso Legal

Los datos utilizados en este proyecto han sido anonimizados completamente para proteger la confidencialidad de la empresa original.  
Se han reemplazado nombres de clientes, procesos y operadores por alias irreversibles.

Este repositorio tiene fines demostrativos y educativos.

---

## Autor

Renzo Gabriel Sánchez Quispe  
Lima, Perú  
renzosanchez201@gmail.com  
+51 937 200 263  
GitHub: [github.com/renzosan25](https://github.com/renzosan25)
