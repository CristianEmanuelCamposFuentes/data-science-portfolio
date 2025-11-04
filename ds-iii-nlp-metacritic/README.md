# DS III — NLP + Clasificación (Metacritic)

**Problema.** Clasificar reseñas de videojuegos en **Buenas (1)** vs **Malas (0)** para identificar temas que explican cada clase y recomendar acciones de marketing/producto.

**Dataset.** Metacritic (2021–2024). Texto: `summary`/reseñas. Metadatos: género, plataforma, publisher, etc.  
**Notebook:** [Abrir en Colab](https://colab.research.google.com/drive/10EFJuwidO54S-3NGYneihxYFEJeVzJr7?usp=drive_link) • **Figures:** carpeta `/figures`.

## Pipeline
1. Limpieza y EDA (equilibrio de clases, nubes de palabras).
2. TF-IDF + Regresión Logística (baseline reproducible).
3. CNN con `TextVectorization` (comparación).
4. (Opcional) Híbrido texto + metadatos (ColumnTransformer).

## Resultados (test)
- **F1 (TF-IDF + LogReg):** 0.82  
- **F1 (CNN):** 0.79  
- **F1 (Híbrido):** 0.84

## Conclusiones
- Los términos positivos refuerzan jugabilidad/performance; los negativos se asocian a bugs y balance → priorizar parches/notas.


## Próximos pasos
- Probar focal loss / calibración de probabilidades.
- Data augmentation ligero para la clase minoritaria.
- Explicabilidad local (LIME/SHAP) en casos representativos.
