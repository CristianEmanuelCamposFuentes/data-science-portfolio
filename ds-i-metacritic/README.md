# ds-i-metacritic · EDA de Videojuegos (Metacritic)

Análisis exploratorio para entender cómo varían las puntuaciones de **usuarios** y **críticos**, y qué patrones aparecen por plataforma, género y año.

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1G7AOSqC__0ZdLgQukFz7aPO9bBeicFIV)

---

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

## Figuras (sugeridas)

Guárdalas en `figures/`:

- `fig_distribution_userscore.png`
- `fig_platform_counts.png`
- `fig_boxplot_userscore_by_platform.png`
- `fig_scatter_metascore_userscore.png`
- `fig_corr_matrix.png`

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