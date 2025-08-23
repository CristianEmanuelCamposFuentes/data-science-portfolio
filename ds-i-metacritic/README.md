# ds-i-metacritic · EDA de Videojuegos (Metacritic)

Análisis exploratorio para entender cómo varían las puntuaciones de **usuarios** y **críticos**, y qué patrones aparecen por plataforma, género y año.

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1G7AOSqC__0ZdLgQukFz7aPO9bBeicFIV)

---


## 🔍 Highlights en una mirada

<p align="center">
  <img src="./figures/fig_corr_matrix.PNG" alt="Matriz de correlación de variables" width="45%" />
  <img src="./figures/fig_distribution_userscore.PNG" alt="Distribución de userScore" width="49%" />
</p>
<p align="center">
  <em>Izq: correlaciones entre variables clave. Der: distribución de userScore.</em>
</p>

<p align="center">
  <img src="./figures/fig_platform_counts.PNG" alt="Cantidad de juegos por plataforma" width="49%" />
  <img src="./figures/fig_boxplot_userscore_by_platform.PNG" alt="userScore por plataforma (boxplot)" width="49%" />
</p>
<p align="center">
  <em>Izq: representación por plataforma. Der: diferencias de userScore por plataforma.</em>
</p>

---

## 📁 Notebook
- Colab (completo): **[abrir](https://colab.research.google.com/drive/1G7AOSqC__0ZdLgQukFz7aPO9bBeicFIV)**
- Carpeta con notebooks: [`./notebooks/`](./notebooks/)

## Objetivos

- Explorar la distribución de **userScore** y **metascore**.  
- Detectar correlaciones entre métricas de reseñas.  
- Observar diferencias por **plataforma/género** y su posible impacto.  
- Dejar bases para un futuro modelo (clasificación/regresión simple).

---

## Dataset

- Archivo: `data/dataset_metacritic_2025.csv`  
- Fuente: compendio público (curado para el curso).  
- Principales campos: `title`, `platform`, `genres`, `metascore`, `userScore`, recuentos de reseñas por tipo, año de lanzamiento.

> El dataset fue limpiado para uso educativo.

---

## Highlights del EDA

- **Distribuciones**: userScore muestra picos cercanos a 7–8 (tendencia a calificaciones positivas).  
- **Correlación**: fuertes relaciones entre recuentos de reseñas positivas/negativas/neutral (tienen sentido operacional).  
- **Diferencias por plataforma/género**: algunas plataformas concentran más títulos con puntajes altos (indicio de sesgo de catálogo y preferencia de audiencia).  
- **Parejas clave**: `metascore` vs `userScore` exhibe correlación moderada – públicos y críticos no siempre coinciden.

---

## Cómo ejecutar

```bash
pip install -U pandas numpy matplotlib seaborn
# abrir notebooks/ProyectoDS1ParteIII...ipynb
o Colab desde el badge de arriba.
```

## Próximos pasos

- Feature engineering (año → década, géneros one-hot, bins de metascore).

- Baselines de ML (regresión para metascore, clasificación para “top tier”).

- Control de fuga de datos y validación temporal.