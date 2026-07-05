# Modelo de Predicción de Octavos de Final - Mundial 2026

## Integrantes del grupo

- Jheison Wesley Ramos Becerra
- Edgar Heiner Jauregui Epiquien
- Jheremy Jhair Lopez Lopez


--
## Descripción del proyecto

Este proyecto desarrolla un modelo de predicción para los partidos de **octavos de final del Mundial 2026**.

La finalidad del trabajo es utilizar datos históricos, ranking FIFA y un calendario actualizado del Mundial 2026 para estimar los resultados de los partidos pendientes. Los partidos que ya tienen resultado real no son predichos nuevamente, sino que se respetan como información oficial del archivo actualizado.

---

## Objetivo general

Construir un modelo predictivo que permita estimar los resultados de los partidos de octavos de final del Mundial 2026, combinando información histórica, ranking FIFA y resultados reales actualizados.

---

## Objetivos específicos

- Cargar y limpiar las bases de datos utilizadas en el proyecto.
- Entrenar un modelo basado en goles esperados usando distribución de Poisson.
- Incorporar resultados reales de dieciseisavos de final.
- Identificar los cruces reales de octavos de final.
- Predecir únicamente los partidos pendientes.
- Generar una tabla final con resultados reales, predicciones y clasificados a cuartos de final.

---

## Archivos utilizados

Los archivos principales se encuentran en la carpeta `data`:

| Archivo | Descripción |
|---|---|
| `matches_1930_2022.csv` | Base histórica de partidos internacionales usada para entrenar el modelo. |
| `fifa_ranking_2022-10-06.csv` | Ranking FIFA usado como referencia para el Mundial 2022. |
| `fifa_ranking_2026-06-08.csv` | Ranking FIFA actualizado para el Mundial 2026. |
| `schedule_2026_actualizado.csv` | Calendario actualizado del Mundial 2026, con resultados reales y partidos pendientes. |
| `world_cup.csv` | Información histórica de ediciones anteriores de la Copa del Mundo. |

---

## Archivos generados

Los resultados principales se encuentran en la carpeta `resultados`:

| Archivo | Descripción |
|---|---|
| `dieciseisavos_reales_desde_csv_actualizado.csv` | Resultados reales de los dieciseisavos de final obtenidos desde el CSV actualizado. |
| `clasificados_reales_a_octavos_desde_csv.csv` | Selecciones clasificadas a octavos según los resultados reales. |
| `respuesta_3_octavos_resultados_actualizados.csv` | Tabla principal con resultados reales y predicciones de octavos. |



---

## Metodología

El procedimiento seguido fue el siguiente:

1. **Carga de datos**  
   Se cargaron los archivos históricos, rankings FIFA y el calendario actualizado del Mundial 2026.

2. **Limpieza de datos**  
   Se normalizaron nombres de equipos, columnas numéricas y resultados de partidos.

3. **Entrenamiento del modelo**  
   Se entrenó un modelo de Poisson para estimar los goles esperados de cada selección.

4. **Uso de resultados reales**  
   Los partidos de dieciseisavos que ya tenían resultado real fueron tomados directamente del CSV actualizado.

5. **Identificación de octavos de final**  
   Se filtraron los partidos de octavos de final usando el archivo `schedule_2026_actualizado.csv`.

6. **Predicción de partidos pendientes**  
   Solo los partidos sin resultado real fueron estimados mediante el modelo.

7. **Generación de clasificados**  
   Se determinó qué equipos clasifican a cuartos de final según resultados reales o predicciones del modelo.

---

## Modelo utilizado

El modelo principal utilizado fue un **modelo de Poisson**, adecuado para estimar conteos como goles en un partido de fútbol.

La lógica general fue:

```text
Datos históricos + Ranking FIFA + Fixture actualizado
        ↓
Estimación de goles esperados
        ↓
Cálculo de marcador probable
        ↓
Probabilidades de resultado
        ↓
Clasificado a la siguiente fase
```

---

## Resultados esperados

El resultado final del proyecto permite obtener:

- Partido de octavos de final.
- Marcador real o estimado.
- Probabilidad de victoria local.
- Probabilidad de empate.
- Probabilidad de victoria visitante.
- Equipo clasificado a cuartos.
- Criterio de clasificación.

---

## Importante

Este repositorio corresponde únicamente a la fase de:

```text
Octavos de final del Mundial 2026
```

No se debe mezclar con repositorios de otras fases del torneo, como fase de grupos, dieciseisavos, cuartos, semifinales o final.

---

## Estructura recomendada del repositorio

```text
modelo_octavos_final_mundial_2026/
│
├── README.md
├── OCTAVOS_FINAL.ipynb
│
├── data/
│   ├── matches_1930_2022.csv
│   ├── fifa_ranking_2022-10-06.csv
│   ├── fifa_ranking_2026-06-08.csv
│   ├── schedule_2026_actualizado.csv
│   └── world_cup.csv
│
└── resultados/
    ├── dieciseisavos_reales_desde_csv_actualizado.csv
    ├── clasificados_reales_a_octavos_desde_csv.csv
    ├── respuesta_3_octavos_resultados_actualizados.csv
    └── respuesta_4_clasificados_a_cuartos_actualizados.csv
```

---

## Cómo ejecutar el proyecto

1. Abrir el notebook `OCTAVOS_FINAL.ipynb` en Google Colab.
2. Subir los archivos de la carpeta `data`.
3. Ejecutar las celdas de carga, limpieza y entrenamiento del modelo.
4. Ejecutar el bloque de predicción de octavos.
5. Revisar los archivos generados en la carpeta `resultados`.

---

## Conclusión

El modelo permite predecir los partidos pendientes de octavos de final del Mundial 2026 utilizando información histórica, ranking FIFA y datos actualizados del torneo.

La principal mejora del procedimiento es que los partidos ya jugados no se vuelven a predecir. Estos se respetan como resultados reales, mientras que el modelo se aplica únicamente a los partidos pendientes.
