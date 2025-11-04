
## Conclusiones

**Baseline TF-IDF + Regresión Logística**
F1≈1.41 (aprox.); ROC-AUC=0.745.
**Términos positivos** (peso alto): new, mario, expansion, ea, story, about, sims, returns.
**Términos negativos** (peso alto): movie, different, interactive, film, action, the player, horror, games.
**Clases**: {1: 5587, 0: 2586}.

## Próximos pasos
1. Comparar con `TextVectorization + CNN` (Keras).
2. Incluir metadatos (género, plataforma, año) en un modelo híbrido texto+estructura.
3. Explicar decisiones del modelo en muestras con LIME/SHAP.
