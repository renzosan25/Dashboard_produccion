# Medidas DAX Personalizadas

Este repositorio contiene un conjunto de medidas DAX desarrolladas para analizar eficiencia, capacidad, utilización y frecuencia acumulada en distintos procesos productivos. Cada medida está documentada con su objetivo, lógica y fórmula.

---

## 1. % Eficiencia Proceso A

** Objetivo:**  
Calcular la eficiencia del proceso A comparando el tiempo productivo frente al tiempo disponible por día y turno.

** Fórmula:**
```dax
% Ef proceso_a = 
VAR TiempoProductivo =
    SUMX(
        SUMMARIZE('proceso_a', 'proceso_a'[FECHA], 'proceso_a'[turno], 
            "TiempoProd", MAX('proceso_a'[TIEMPO PRODUCTIVO])
        ),
        [TiempoProd]
    )
VAR TiempoDisponible =
    SUMX(
        SUMMARIZE('proceso_a', 'proceso_a'[FECHA], 'proceso_a'[turno], 
            "TiempoProd", MAX('proceso_a'[TIEMPO DISPONIBLE])
        ),
        [TiempoProd]
    )
RETURN
    DIVIDE(TiempoProductivo, TiempoDisponible, 0)
```

## 2. Capacidad_proceso_b

** Objetivo:**  
Estimar la capacidad diaria del proceso B a partir del minutaje promedio por ciclo.

** Fórmula:**
```dax
Capacidad proceso_b = 
VAR PromedioMinutaje = 
    CALCULATE(
        AVERAGE('proceso_b'[MINUTAJE]), 
        REMOVEFILTERS('proceso_b'[FECHA])
    )
RETURN 
    IF(PromedioMinutaje <= 0, 0, (60 / PromedioMinutaje) * 8 * 10)
```

## 3. Frecuencia Acumulada %

** Objetivo:**  
Determinar la frecuencia acumulada porcentual por motivo dentro de cada área, útil para análisis de Pareto.

** Fórmula:**
```dax
Frecuencia Acumulada % = 
VAR AreaActual = SELECTEDVALUE(BD_Paretto[AREA])
VAR MotivoActual = SELECTEDVALUE(BD_Paretto[MOTIVO])
VAR FrecuenciaActual = CALCULATE(SUM(BD_Paretto[FRECUENCIA]), ALLEXCEPT(BD_Paretto, BD_Paretto[MOTIVO], BD_Paretto[AREA]))

VAR TotalFrecuenciaArea = 
    CALCULATE(
        SUM(BD_Paretto[FRECUENCIA]),
        ALLEXCEPT(BD_Paretto, BD_Paretto[AREA])
    )

VAR FrecuenciaAcumulada = 
    SUMX(
        FILTER(
            ALL(BD_Paretto),
            BD_Paretto[AREA] = AreaActual &&
            (
                BD_Paretto[FRECUENCIA] > FrecuenciaActual
                || 
                (BD_Paretto[FRECUENCIA] = FrecuenciaActual && BD_Paretto[MOTIVO] <= MotivoActual)
            )
        ),
        BD_Paretto[FRECUENCIA]
    )

RETURN 
DIVIDE(FrecuenciaAcumulada, TotalFrecuenciaArea, 0)
```

## 4. Utilización de Capacidad - Proceso c

** Objetivo:**  
Calcular la utilización promedio de la capacidad diaria del proceso C.

** Fórmula:**
```dax
Utilización Capacidad proceso c = 
VAR TablaFiltrada = 
    ADDCOLUMNS(
        VALUES('Calendar'[Date]), 
        "MaxCapacidadDia", CALCULATE(MAX(capacidad_c[CAPACIDAD LAV.C])),
        "ProduccionDia", CALCULATE(SUM(proceso_c[KG]))
    )

VAR UtilizacionDiaria = 
    ADDCOLUMNS(
        TablaFiltrada,
        "Utilizacion", DIVIDE([ProduccionDia], [MaxCapacidadDia], 0)
    )

RETURN 
    AVERAGEX(UtilizacionDiaria, [Utilizacion])
```

