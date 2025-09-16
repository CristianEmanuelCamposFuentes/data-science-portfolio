# ds-ii-logistics · Exploratorio y Predicción de Retrasos en Logística

Análisis exploratorio y primeros modelos para **predecir riesgo de retraso** y **estimar desvío del ETA** a partir de variables operativas (congestión, inventario, clima, costos, etc.).

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1ZBZsqyO3r5jR1gvPrD7CdYM1YD9ArY9f)

---

## 🔍 Highlights en una mirada

<p align="center">
  <img src="./figures/fig_risk_counts.png" alt="Conteo por nivel de riesgo" width="49%" />
  <img src="./fig_violin_delay_by_risk.png" alt="Delay probability por riesgo" width="49%" />
</p>
<p align="center"><em>Izq: dataset desbalanceado hacia High Risk. Der: High Risk concentra mayores probabilidades de retraso.</em></p>

<p align="center">
  <img src="./fig_scatter_congestion_vs_deviation.png" alt="Desvío vs Congestión" width="49%" />
  <img src="./fig_corr_matrix_logistics.png" alt="Matriz de correlación" width="49%" />
</p>
<p align="center"><em>Izq: la congestión se asocia con mayor desvío de ETA. Der: correlaciones entre métricas operativas.</em></p>

---

## 📁 Notebook
- Colab (completo): **[abrir](https://colab.research.google.com/drive/1ZBZsqyO3r5jR1gvPrD7CdYM1YD9ArY9f)**
- Carpeta con notebooks: [`./notebooks/`](./notebooks/)

## Objetivos

- Entender patrones que explican **retrasos** y **desvíos**.
- Construir un **baseline** de clasificación (riesgo) y de regresión (desvío, en horas).
- Dejar un pipeline reproducible para futuras mejoras.

---

## Dataset

- Archivo: `data/dynamic_supply_chain_logistics_dataset.csv`
- Cobertura: Ene-2021 — Ene-2024 (registros **horarios**), 32k filas, 26 columnas.
- Variables clave (ejemplos):  
  `traffic_congestion_level` (0-10), `warehouse_inventory_level`,  
  `route_risk_level` (0-10), `shipping_costs` (USD),  
  `driver_behavior_score` (0-1), `delay_probability` (0-1),  
  `delivery_time_deviation` (h), `risk_classification` (Low/Moderate/High).

> Dataset curado para uso educativo.

---

## Hallazgos del EDA (resumen)

- **Congestión** > 7 eleva fuertemente retrasos y desvíos.
- **Inventarios bajos** (<100 u) → mayor variabilidad del ETA.
- **Clases desbalanceadas** (High ≫ Moderate > Low): se aplican `class_weight`/estrategias de balanceo.
- `driver_behavior_score` muestra distribución bimodal: segmentar o usarlo como feature importante.
- Correlaciones razonables entre costos/tiempos/condiciones externas.

---

## 🧠 Modelado (baseline rápido)

**Clasificación** (riesgo / delay alto):
- Modelos: `LogisticRegression(balanced)`, `RandomForest`, `XGBClassifier`.
- Validación: **split temporal** (train 2021-2023, test 2024) y/o `TimeSeriesSplit`.
- Métricas: **PR-AUC**, F1-macro, matriz de confusión.

**Regresión** (desvío ETA):
- Modelos: `LinearRegression`, `RandomForestRegressor`, `XGBRegressor`.
- Métricas: **MAE** (principal) + RMSE.  
- Gráficos: Real vs. Predicho y distribución de errores.

**Pipeline**:
- `ColumnTransformer` con `OneHotEncoder` (categorías) + imputación/scaler según modelo.
- Importancias (permutation) y explicación básica (SHAP) para árboles.

---

## Cómo ejecutar

```bash
pip install -U pandas numpy scikit-learn matplotlib seaborn xgboost
```

## Estructura
```
ds-ii-logistics/
├─ data/
│  └─ dynamic_supply_chain_logistics_dataset.csv
├─ figures/
│  ├─ fig_risk_counts.png
│  ├─ fig_violin_delay_by_risk.png
│  ├─ fig_scatter_congestion_vs_deviation.png
│  └─ fig_corr_matrix_logistics.png
├─ notebooks/
│  └─ ProyectoDSIIParteII....ipynb
└─ README.md
```


**Próximos pasos**:

- Features de tiempo (hour/dayofweek/season) y lags de congestión/ETA.

- Calibración de probabilidades y threshold tuning para alertas.

- Monitoreo: data drift y reentrenamiento mensual.

---

## Licencia

MIT – uso libre con atribución.

## Contacto

Cristian Emanuel Campos Fuentes – cristianemanuelcamposfuentes@hotmail.com
 – [LinkedIn](https://www.linkedin.com/in/cristian-emanuel-campos-fuentes/)