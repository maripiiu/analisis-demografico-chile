# Análisis de la Relación entre Vulnerabilidad Socioeconómica, Educación y Natalidad en Chile
## Proyecto IMT-2200: Análisis de Datos Demográficos de Chile

##  Descripción del Proyecto

Este proyecto analiza tendencias demográficas en Chile, enfocándose en:
- **Nacimientos** (1992-2022): Análisis de series temporales de nacimientos por región, edad de progenitores y educación
- **Censo 2024**: Datos de población, educación y fecundidad a nivel comunal
- **Índice de Vulnerabilidad Social (RSH)**: Distribución de vulnerabilidad por quintiles (0-40%, 41-50%, etc.) a nivel nacional, regional y comunal

**Audiencia objetivo**: Ministerio de Desarrollo Social y Familia

---

##  Estructura del Repositorio

```
.
├── README.md                          # Este archivo
├── requirements.txt                   # Dependencias del proyecto
|
│
├── notebooks/                         # Jupyter Notebooks con análisis
│   ├── analisis_final.ipynb          #  NOTEBOOK PRINCIPAL - Análisis completo
│   ├── orden_series_nacimiento.ipynb # Limpieza y procesamiento de datos de nacimientos
│   ├── rsh_unir_limpiar.ipynb        # Unificación y limpieza de datos RSH
│   ├── info_IV.ipynb                 # Procesamiento de índice de vulnerabilidad
│   └── censo_limpiar_.ipynb          # Limpieza de datos del censo 2024
│
├── Data/                              # Datos del proyecto
│   ├── clean data/                   # Datos procesados y limpios
│   │   ├── censo/
│   │   │   ├── 2017/                 # Censo 2017
│   │   │   │   ├── README.md
│   │   │   │   └── microdato2017.csv
│   │   │   └── 2024/                 # Censo 2024
│   │   │       ├── censo_2024_educacion.csv
│   │   │       ├── censo_2024_fecundidad.csv
│   │   │       └── censo_2024_poblacion.csv
│   │   ├── nacimientos/
│   │   │   └── Serie_nacimientos_1992-2022.parquet
│   │   └── RSH/
│   │       └── Tramos_RSH_2019-2025.csv
│   │
│   ├── dirty data/                   # Datos crudos sin procesar
│   │   ├── censo/
│   │   │   ├── 2017/
│   │   │   │   ├── README.md
│   │   │   │   └── csv-personas-censo-2017/
│   │   │   └── 2024/
│   │   ├── Datos_nacimientos/
│   │   │   └── README.md
│   │   ├── Nacimientos_1992-2022/
│   │   └── Set_de_Datos_RSH/
│   │
│   └── mapas vectoriales/
│       └── Comunas/
│
├── docs/                              # Documentación adicional
│   └── index.html
│
├── graficos/                          # Gráficos generados
│
|
│
└── web/                               # Sitio web del proyecto
    ├── index.html
    └── styles.css
```

---

##  Cómo Usar Este Repositorio

### Requisitos Previos
- Python 3.12.0+
- Pandas, NumPy, Matplotlib, Seaborn, scikit-learn

### Ejecución del Proyecto

1. **Para análisis completo** (punto de entrada principal):
   ```bash
   jupyter notebook notebooks/analisis_final.ipynb
   ```

2. **Para procesar datos por primera vez**:
   - Ejecutar `notebooks/censo_limpiar_.ipynb` para procesar censo
   - Ejecutar `notebooks/orden_series_nacimiento.ipynb` para procesar nacimientos
   - Ejecutar `notebooks/rsh_unir_limpiar.ipynb` para procesar RSH

---

##  Descripción de Notebooks

| Notebook | Descripción | Entrada | Salida |
|----------|-------------|---------|--------|
| **analisis_final.ipynb** | Análisis completo con visualizaciones principales | Datos limpios | Gráficos y conclusiones |
| **orden_series_nacimiento.ipynb** | Limpieza y renombrado de datos de nacimientos | CSV bruto | `Serie_nacimientos_1992-2022.parquet` |
| **rsh_unir_limpiar.ipynb** | Unificación de 47 archivos RSH CSV | 47 archivos RSH | `DATOS_CONSOLIDADOS_RSH.csv` |
| **info_IV.ipynb** | Agregación de RSH por quintiles por comuna | RSH consolidado | Datos agregados por comuna |
| **censo_limpiar_.ipynb** | Extracción de datos de censo 2024 | Excel/CSV | CSV procesados por tema |

---

##  Hallazgos Principales

- **Tendencia de natalidad**: Tendencia decreciente en nacimientos desde 1992
- **Vulnerabilidad social**: Concentración de vulnerabilidad en comunas específicas
- **Datos demográficos**: Cambios significativos en estructura de edad y educación
---
## Preguntas de Investigación
Este proyecto busca responder las siguientes interrogantes mediante el análisis de datos:

1.  **Relación Educación-Maternidad:** ¿Existe una correlación entre el nivel educativo de la madre y la edad a la que tienen su primer hijo?
2.  **Evolución de la Vulnerabilidad:** ¿Cómo ha variado el porcentaje de hogares vulnerables en Chile (según el RSH) a lo largo del tiempo analizado?
3.  **Distribución Regional:** ¿Cómo se distribuyen los nacimientos y la vulnerabilidad a nivel regional? (Con énfasis en el análisis comparativo de regiones, como la IV Región).
4.  **Factores Demográficos:** ¿Qué grupos etarios concentran la mayor cantidad de nacimientos y cómo se relaciona esto con la vulnerabilidad socioeconómica?
---
## Datos Utilizados:
El análisis integra tres fuentes de datos principales:
- Registro Social de Hogares (RSH): Datos del Ministerio de Desarrollo Social que indican el tramo de vulnerabilidad de los hogares.
- Estadísticas Vitales (Nacimientos): Datos del DEIS/INE sobre nacimientos, incluyendo edad de la madre y región.
- Censo: Información demográfica base para normalizar datos poblacionales.
---
##  Fuentes de Datos

- [INE - Censos de Población](https://www.ine.gob.cl/estadisticas/sociales/censos-de-poblacion-y-vivienda/censo-de-poblacion-y-vivienda)
- [Ministerio de Desarrollo Social - Índice de Vulnerabilidad Social](https://www.desarrollosocialyfamilia.gob.cl/)
- BIDAT - Banco Integrado de Datos del Ministerio de Desarrollo Social y Familia (https://bidat.gob.cl/search?_token=IkVz0DXMD3zHxS6CXJfFNUHerAtfmLz0kZcDPj3g&search=Personas+en+RSH&selectedFormat=)
- Series de nacimientos 1992-2022
---
## Ejecución
- Para replicar los resultados, se recomienda ejecutar el notebook principal: jupyter notebook notebooks/analisis_final.ipynb
**Si se desea replicar el proceso de limpieza desde cero, ejecutar los notebooks de la carpeta notebooks/ en el orden descrito en la tabla anterior.**
## Autores:
- Boris Tomas Antillanca Salinas
- Esteban Rodrigo Arias Serra
- Gaspar Alejandro Yáñez Flores
- María Paz Allendes Álvarez

## Declaración de Uso de IA
Siguiendo las políticas de integridad del curso, declaramos el uso de Inteligencia Artificial Generativa (Google Gemini) como herramienta de apoyo en las siguientes tareas:

1.  **Visualización:** Se utilizaron consultas para ajustar detalles estéticos de los gráficos en `matplotlib` y `seaborn` (ej: rotación de etiquetas, paletas de colores).
2.  **Limpieza de Datos:** Se solicitaron sugerencias de métodos eficientes en `pandas` para el manejo de valores nulos y estandarización de columnas.
3.  **Documentación:** Se utilizó IA para generar la estructura base y mejorar la redacción técnica de este archivo `README.md`.

*Nota: Todo el código y texto generado fue revisado, adaptado y verificado por el equipo.*
